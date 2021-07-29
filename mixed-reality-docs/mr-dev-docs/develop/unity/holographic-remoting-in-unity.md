---
title: Comunicação remota do Holographic no Unity
description: Descubra como usar a comunicação remota do Holographic em um aplicativo de área de trabalho e modo de reprodução do Unity com o OpenXR.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realidade misturada, MRTK, realidade misturada Toolkit, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução, holographic comunicação remota, área de trabalho
ms.openlocfilehash: 51244a94fb7e54f2eee41d9d1b7f65b0ba373138
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757381"
---
# <a name="holographic-remoting-in-unity"></a>Comunicação remota do Holographic no Unity

> [!NOTE]
> Windows O suporte a comunicação remota do aplicativo autônomo foi adicionado na versão do pacote 0.1.3.
> A partir da versão 0.1.3, esse recurso não oferece suporte a compilações UWP.

[Conheça os fundamentos da comunicação remota do Holographic.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

você pode usar a comunicação remota do Holographic para transmitir conteúdo do Holographic para seu HoloLens 2 em tempo real. Essa é uma ótima maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo. 

Antes de começar, é importante entender suas duas opções principais no Unity:
* **Holographic Remoting no modo de reprodução do Unity**: execute seu aplicativo localmente no editor do unity em seu PC no modo de reprodução para fornecer uma maneira rápida de visualizar o conteúdo em um HoloLens 2. o modo de reprodução também pode ser usado com um Windows Mixed Reality headset conectado ao seu PC de desenvolvimento.
* **Holographic comunicação remota de um arquivo de compilação de unity**: execute seu aplicativo de um aplicativo remoto de comunicação remota do unity Holographic que você exportou para sua área de trabalho para o HoloLens 2. Isso pode ser útil se seu aplicativo tiver ativos ou modelos de alta resolução; sua GPU de desktop lida com a renderização antes de chegar ao HoloLens 2.

## <a name="holographic-remoting-setup"></a>Configuração de comunicação remota do Holographic

seja qual for a rota que você está usando com a comunicação remota do Holographic, você precisa [instalar o aplicativo de Player de comunicação remota do Holographic](https://www.microsoft.com/store/productId/9NBLGGH4SV40) do Microsoft Store no HoloLens 2.

depois de baixado, execute o aplicativo de Player de comunicação remota do Holographic no seu HoloLens 2 e você verá o número de versão e o endereço IP para se conectar. **Você precisará do v 2.4 ou posterior para trabalhar com o plug-in OpenXR**.

![Captura de tela do player de comunicação remota do Holographic em execução no HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de reprodução do Unity com comunicação remota do Holographic

[!INCLUDE[](includes/unity-play-mode.md)]

A comunicação remota do Holographic exige um PC rápido e uma conexão Wi-Fi. Você pode encontrar mais detalhes na documentação do [player de comunicação remota do Holographic](../platform-capabilities-and-apis/holographic-remoting-player.md) .

Para obter melhores resultados, verifique se seu aplicativo define corretamente o [ponto de foco](focus-point-in-unity.md). Isso ajuda a Holographic a comunicação remota para adaptar sua cena à latência de sua conexão sem fio.

## <a name="holographic-remoting-from-a-remote-application"></a>Holographic a comunicação remota de um aplicativo remoto

1. na barra de menus, selecione **editar > Project Configurações**.
1. Na coluna do lado esquerdo, selecione **XR plug-in Management**.
1. na seção **gerenciamento de Plug-in do XR** , selecione **Microsoft HoloLens** grupo de recursos e grupo de **recursos do aplicativo remoto de comunicação remota do Holographic**.
1. Desmarque **inicializar XR na inicialização**:

    ![Captura de tela do painel de configurações do projeto aberta no editor do Unity com Initialize XR na inicialização desmarcada](images/001-openxr-features.png)

1. Escreva algum código para definir a configuração de comunicação remota e disparar a inicialização de XR. O aplicativo de exemplo distribuído com o [plug-in OpenXR de realidade misturada](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) contém AppRemoting. cs, que mostra um cenário de exemplo para se conectar a um endereço IP específico em tempo de execução. A implantação do aplicativo de exemplo em um computador local neste ponto exibirá um campo de entrada de endereço IP com um botão conectar. digitar um endereço IP e clicar em Conexão irá inicializar o XR e tentar se conectar ao dispositivo de destino:

    ![Captura de tela do aplicativo de exemplo exibindo exemplo de IU de comunicação remota](images/openxr-sample-app-remoting.png)

1. Para gravar o código de conexão personalizado, chame `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` com um preenchimento `RemotingConfiguration` . O aplicativo de exemplo expõe isso no Inspetor e mostra como preencher o endereço IP a partir de um campo de texto. Chamar `Connect` irá definir a configuração e inicializar automaticamente a XR, que é o motivo pelo qual ela deve ser chamada como uma corrotina:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. Durante a execução, você pode obter o estado de conexão atual com a `AppRemoting.TryGetConnectionState` API e, opcionalmente, desconectar e desinicializar a XR usando `AppRemoting.Disconnect()` . Isso pode ser usado para desconectar e reconectar-se a um dispositivo diferente na mesma sessão de aplicativo. O aplicativo de exemplo fornece um cubo tappable que desconectará a sessão de comunicação remota, se tocado.

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

## <a name="see-also"></a>Confira também

* [Player de Comunicação Remota Holográfica](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Tutorial: introdução ao PC Holographic de comunicação remota](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Criando um aplicativo de PC de comunicação remota Holographic](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
