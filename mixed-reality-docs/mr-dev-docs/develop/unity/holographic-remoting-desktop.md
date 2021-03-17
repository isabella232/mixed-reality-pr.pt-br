---
title: Comunicação remota do Holographic no aplicativo de desktop
description: Descubra como usar a comunicação remota do Holographic em um aplicativo de área de trabalho com OpenXR.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução, Holographic comunicação remota, área de trabalho
ms.openlocfilehash: f3cf43d59b74b0f47e701acc1d7312544867b0df
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624312"
---
# <a name="holographic-remoting-in-desktop-app"></a>Comunicação remota do Holographic no aplicativo de desktop

> [!NOTE]
> O suporte remoto do aplicativo Windows autônomo foi adicionado na versão do pacote 0.1.3.
> A partir da versão 0.1.3, esse recurso não oferece suporte a compilações UWP.

1. Siga as etapas na [instalação do Holographic Remoting](openxr-supported-features.md#holographic-remoting-setup)
2. Abra **as configurações do projeto de > de edição**, navegue até o **Gerenciamento de plug-in do XR** e marque a caixa conjunto de recursos da realidade do **Windows Mixed** . Além disso, desmarque **inicializar XR na inicialização**:

    ![Captura de tela do painel de configurações do projeto aberta no editor do Unity com Initialize XR na inicialização desmarcada](images/openxr-features-img-02-app.png)

3. Expanda a seção **recursos** em **OpenXR** e selecione **Mostrar tudo**
4. Marque a caixa de seleção de **comunicação remota do aplicativo Holographic** :

    ![Captura de tela do painel de configurações do projeto aberto no editor do Unity com a comunicação remota do aplicativo habilitada](images/openxr-features-img-03-app.png)

5. Em seguida, escreva algum código para definir a configuração de comunicação remota e disparar a inicialização de XR. O aplicativo de exemplo distribuído com o [plug-in OpenXR de realidade misturada](openxr-getting-started.md#hololens-2-samples) contém AppRemoting.cs, que mostra um cenário de exemplo para se conectar a um endereço IP específico em tempo de execução. A implantação do aplicativo de exemplo em um computador local neste ponto exibirá um campo de entrada de endereço IP com um botão conectar. Digitar um endereço IP e clicar em conectar irá inicializar o XR e tentar se conectar ao dispositivo de destino:

    ![Captura de tela do aplicativo de exemplo exibindo exemplo de IU de comunicação remota](images/openxr-sample-app-remoting.png)

6. Para gravar o código de conexão personalizado, chame `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` com um preenchimento `RemotingConfiguration` . O aplicativo de exemplo expõe isso no Inspetor e mostra como preencher o endereço IP a partir de um campo de texto. Chamar `Connect` irá definir a configuração e inicializar automaticamente a XR, que é o motivo pelo qual ela deve ser chamada como uma corrotina:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. Durante a execução, você pode obter o estado de conexão atual com a `AppRemoting.TryGetConnectionState` API e, opcionalmente, desconectar e desinicializar a XR usando `AppRemoting.Disconnect()` . Isso pode ser usado para desconectar e reconectar-se a um dispositivo diferente na mesma sessão de aplicativo. O aplicativo de exemplo fornece um cubo tappable que desconectará a sessão de comunicação remota, se tocado.

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