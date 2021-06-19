---
ms.openlocfilehash: 40d24083ec83b9d6faebc00cf801d1f6f55fddd7
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392284"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. No seu HoloLens, vá para a **Microsoft Store** e instale o aplicativo de **[player de comunicação remota do Holographic](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
1. No seu HoloLens, inicie o aplicativo do **player de comunicação remota do Holographic** .
1. No Unity, vá para o menu **Editar** e selecione **configurações do projeto**.
1. Selecione **Gerenciamento de plug-ins de XR**.
1. Verifique se a guia **autônomo do Windows** está selecionada, encontre o conjunto de recursos do **OpenXR** e do **Windows Mixed Reality** na lista e marque as caixas de seleção.
1. Em seguida, vá para o menu **janela** , expanda o submenu **XR** e selecione **comunicação remota do editor OpenXR**.

    ![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](../images/openxr-features-img-02.png)

1. Clique em **habilitar comunicação remota do editor**.

    ![Captura de tela do painel de configurações do projeto aberto no editor do Unity com recursos realçados](../images/openxr-features-img-03.png)

1. Se o botão **habilitar dependências ausentes** for exibido, clique nele também. A caixa de erro acima do botão descreve os recursos que ele está habilitando e por quê.
1. Para **nome de host remoto**, insira o endereço IP do seu HoloLens.
   1. Altere outras configurações conforme necessário.
   1. O editor tentará se conectar quando o modo de reprodução for iniciado.
1. Selecione o botão **reproduzir** para iniciar o modo de reprodução e experimentar o aplicativo em seu HoloLens. Para depurar scripts C# no modo de reprodução, [anexe o Visual Studio ao Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).

> [!NOTE]
> A partir da versão 0.1.0, o tempo de execução de comunicação remota do Holographic não dá suporte a âncoras, e as funcionalidades de ARAnchorManager não funcionarão por meio de comunicação remota.  Esse recurso estará disponível em versões futuras.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in do Windows XR](#tab/winxr)

1. No seu HoloLens, vá para a **Microsoft Store** e instale o aplicativo de **[player de comunicação remota do Holographic](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
1. No seu HoloLens, inicie o aplicativo do **player de comunicação remota do Holographic** .
1. No Unity, vá para o menu **Editar** e selecione **configurações do projeto**.
1. Selecione **Gerenciamento de plug-ins de XR**.
1. Verifique se a guia **autônomo do Windows** está selecionada, localize **realidade misturada do Windows** na lista e marque a caixa de seleção.
1. Em seguida, vá para o menu **janela** , expanda o submenu **XR** e selecione **comunicação remota do plug-in Windows XR**.
1. Defina o **modo de emulação** como **remoto para dispositivo**.
1. Para **computador remoto**, insira o endereço IP do seu HoloLens.
1. Para se conectar, ou:
   1. Para conectar-se manualmente, desmarque **conectar em Play** e selecione **conectar**. Você deve ver o **status da conexão** alterado para **conectado** e ver a tela ficar em branco no HoloLens.
   1. Para se conectar automaticamente, verifique **conectar na reprodução**. O editor tentará se conectar quando o modo de reprodução for iniciado.
1. Selecione o botão **reproduzir** para iniciar o modo de reprodução e experimentar o aplicativo em seu HoloLens. Para depurar scripts C# no modo de reprodução, [anexe o Visual Studio ao Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

1. No seu HoloLens, vá para a **Microsoft Store** e instale o aplicativo de **[player de comunicação remota do Holographic](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
1. No seu HoloLens, inicie o aplicativo do **player de comunicação remota do Holographic** .
1. No Unity, vá para o menu **janela** , expanda o submenu **XR** e selecione **emulação Holographic** (marcada como preterida no Unity 2019).
1. Defina o **modo de emulação** como **remoto para dispositivo**.
1. Defina a **versão do dispositivo** de acordo com se você estiver usando um hololens de primeira geração ou um hololens 2.
1. Para **computador remoto**, insira o endereço IP do seu HoloLens.
1. Selecione **Conectar**. Você deve ver o **status da conexão** alterado para **conectado** e ver a tela ficar em branco no HoloLens.
1. Selecione o botão **reproduzir** para iniciar o modo de reprodução e experimentar o aplicativo em seu HoloLens. Para depurar scripts C# no modo de reprodução, [anexe o Visual Studio ao Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).
