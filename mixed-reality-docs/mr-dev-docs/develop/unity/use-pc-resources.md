---
title: Use os recursos do PC para capacitar seu aplicativo com a comunicação remota do Holographic
description: Use os recursos do PC, em vez de depender do poder de processamento integrado do HoloLens, para capacitar seu aplicativo com a comunicação remota do Holographic
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realidade misturada, MRTK, realidade misturada Toolkit, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução, holographic comunicação remota, área de trabalho, visualização, depuração
ms.openlocfilehash: 634e1a5e92ade79d1d9f0e7bfdd994cfdfb5866b
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203831"
---
# <a name="use-pc-resources-to-power-your-app-with-holographic-remoting"></a>Use os recursos do PC para capacitar seu aplicativo com a comunicação remota do Holographic

Este artigo explica o seguinte caso de uso para a comunicação remota do Holographic:

-  **você deseja que os recursos de um PC liguem seu aplicativo em vez de depender do HoloLens recursos integrados**: você pode criar e compilar um aplicativo que tenha a capacidade de comunicação remota do Holographic. o usuário experimenta o aplicativo no HoloLens, mas o aplicativo realmente é executado em um PC, o que permite que o aplicativo aproveite os recursos mais avançados do PC. Isso pode ser especialmente útil se seu aplicativo tiver ativos ou modelos de alta resolução e se você não quiser que a taxa de quadros seja prejudicada. Chamamos isso de um _aplicativo remoto de comunicação_ remota do Holographic. as entradas do HoloLens--olhar, gesto, voz e mapeamento espacial – são enviadas para o PC, onde o conteúdo é renderizado em uma exibição de imersão virtual. Os quadros renderizados são enviados para a HoloLens.

esse tipo de comunicação remota do Holographic também está disponível para headsets de imersão de Windows Mixed Reality (WMR). Isso pode ser útil se, por exemplo, o fone de ouvido WMR estiver conectado a um PC mochila e você quiser transmitir seu aplicativo de um PC mais potente para o mochila PC.

Para saber mais sobre a comunicação remota do Holographic, consulte [visão geral da comunicação remota do Holographic](../platform-capabilities-and-apis/holographic-remoting-overview.md)

Observe que você também pode usar a comunicação remota [do Holographic se quiser Visualizar e depurar seu aplicativo durante o processo de desenvolvimento](preview-and-debug-your-app.md).

## <a name="set-up-holographic-remoting"></a>Configurar a comunicação remota do Holographic

para usar a comunicação remota do Holographic, você precisa instalar o aplicativo de [Player de comunicação remota do Holographic](../platform-capabilities-and-apis/holographic-remoting-player.md) do Microsoft Store no seu HoloLens 2. Conforme explicado abaixo, depois de baixar e executar o aplicativo, você verá o número de versão e o endereço IP para se conectar. **Você precisará do v 2.4 ou posterior para trabalhar com o plug-in OpenXR**.

A comunicação remota do Holographic exige um PC rápido e uma conexão Wi-Fi. Você pode encontrar mais detalhes no artigo do player de comunicação remota do Holographic vinculado acima.

![Captura de tela do player de comunicação remota do Holographic em execução no HoloLens](images/openxr-features-img-01.png)

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

## <a name="migrate-from-previous-holographic-remoting-apis"></a>Migrar de APIs de comunicação remota Holographic anteriores

Para saber mais sobre a comunicação remota do Holographic, consulte [visão geral da comunicação remota do Holographic](../platform-capabilities-and-apis/holographic-remoting-overview.md)

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

## <a name="see-also"></a>Consulte Também

* [Player de Comunicação Remota Holográfica](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Visualizar e depurar seu aplicativo com o modo de execução e comunicação remota do Holographic](preview-and-debug-your-app.md)
* [Tutorial: introdução ao PC Holographic de comunicação remota](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Criando um aplicativo de PC de comunicação remota Holographic](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
