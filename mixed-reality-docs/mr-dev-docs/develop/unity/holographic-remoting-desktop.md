---
title: Comunicação remota holográfica em um aplicativo da área de trabalho
description: Descubra como usar a Remota Holográfica em um aplicativo da área de trabalho com OpenXR.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realidade misturada, MRTK, Kit de Ferramentas de Realidade Misturada, realidade aumentada, realidade virtual, headsets de realidade misturada, learn, tutorial, introdução, comunicação remota holográfica, área de trabalho
ms.openlocfilehash: 18557af1f08ea05715b92b5072460871bb05a329
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333401"
---
# <a name="holographic-remoting-in-desktop-app"></a>Comunicação remota holográfica em um aplicativo da área de trabalho

> [!NOTE]
> O suporte à remoção de aplicativos autônomos do Windows foi adicionado na versão do pacote 0.1.3.
> A partir da versão 0.1.3, esse recurso não dá suporte a builds UWP.

1. Siga as etapas em [Configuração de Remoção Holográfica](unity-play-mode.md#holographic-remoting-setup)
2. Abra **Editar -> Configurações do** Projeto, navegue até Gerenciamento de **plug-in XR** e marque **a caixa Windows Mixed Reality conjunto de recursos.** Além disso, **desmarque Inicializar XR na Inicialização:**

    ![Captura de tela do painel de configurações do projeto aberto no Editor do Unity com Inicializar XR na Inicialização desmarcada](images/openxr-features-img-02-app.png)

3. Expanda **a seção** Recursos em **OpenXR** e selecione **Mostrar Tudo**
4. Marque a **caixa de seleção Holographic App Remoting:**

    ![Captura de tela do painel de configurações do projeto aberto no Editor do Unity com a opção de remoção de aplicativo habilitada](images/openxr-features-img-03-app.png)

5. Em seguida, escreva um código para definir a configuração de remoting e disparar a inicialização de XR. O aplicativo de exemplo distribuído com o [Plug-in OpenXR](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) de Realidade Misturada contém AppRemoting.cs, que mostra um cenário de exemplo para se conectar a um endereço IP específico em runtime. Implantar o aplicativo de exemplo em um computador local neste ponto exibirá um campo de entrada de endereço IP com um botão conectar. Digitar um endereço IP e clicar em Conectar inicializa o XR e tentar se conectar ao dispositivo de destino:

    ![Captura de tela do aplicativo de exemplo exibindo a interface do usuário de exemplo de remoting do aplicativo](images/openxr-sample-app-remoting.png)

6. Para escrever código de conexão personalizado, `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` chame com um `RemotingConfiguration` preenchido. O aplicativo de exemplo expõe isso no inspetor e mostra como preencher o endereço IP de um campo de texto. Chamar `Connect` definirá a configuração e inicializa automaticamente o XR, por isso ele deve ser chamado como uma coroutina:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. Durante a execução, você pode obter o estado de conexão atual com a API e, opcionalmente, desconectar `AppRemoting.TryGetConnectionState` e des inicializar XR usando `AppRemoting.Disconnect()` . Isso pode ser usado para desconectar e reconectar-se a um dispositivo diferente na mesma sessão de aplicativo. O aplicativo de exemplo fornece um cubo tappable que desconectará a sessão de comunicação remota, se tocado.

### <a name="migration-from-previous-apis"></a>Migração de APIs anteriores

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine. XR. WSA. HolographicRemoting

Do código de exemplo nos [documentos do Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):

| XR. WSA. HolographicRemoting | OpenXR. Remoting. AppRemoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/A: ocorre automaticamente ao chamar `AppRemoting.Connect` ]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine. XR. WindowsMR. WindowsMRRemoting

| XR. WindowsMR.WindowsMRRemoting | OpenXR. Remoting. AppRemoting |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` e `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | Transmitido `AppRemoting.Connect` via `RemotingConfiguration` struct |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`