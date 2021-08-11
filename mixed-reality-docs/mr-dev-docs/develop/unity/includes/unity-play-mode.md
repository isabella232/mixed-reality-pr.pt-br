---
ms.openlocfilehash: f579cb73389d23be5959d212d4243361f00a27b8475ce74a16acc2bffa7a192b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192160"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. Na sua HoloLens, acesse o **Microsoft Store** e instale o **[aplicativo Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. Na sua HoloLens, inicie o **aplicativo Holographic Remoting Player.**
1. No Unity, vá para o menu **Editar** e **selecione Project Configurações**.
1. Selecione **Gerenciamento de Plug-in XR.**
1. Verifique se **Windows guia** Autônomo está selecionada, encontre **OpenXR** **e Windows Mixed Reality de** recursos definidos na lista e marque suas caixas de seleção.
1. Em seguida, vá para o menu **Janela,** expanda o submenu **XR** e selecione **OpenXR Editor Remoting**.

    ![Captura de tela do painel de configurações do projeto aberto no Editor do Unity com o gerenciamento de plug-in XR realçada](../images/openxr-features-img-02.png)

1. Clique **em Habilitar a Remoting do Editor.**

    ![Captura de tela do painel de configurações do projeto aberto no Editor do Unity com recursos realçadas](../images/openxr-features-img-03.png)

1. Se o **botão Habilitar Dependências Ausentes** for exibido, clique nessa também. A caixa de erro acima do botão descreve os recursos que ele está habilitando e por quê.
1. Para **Nome do Host Remoto**, insira o endereço IP do seu HoloLens.
   1. Altere outras configurações conforme necessário.
   1. O editor tentará se conectar depois que o Modo de Reprodução for iniciado.
1. Selecione o **botão Reproduzir** para iniciar o Modo de Reprodução e experimente o aplicativo em seu HoloLens. Para depurar scripts C# no modo de reprodução, [anexe Visual Studio ao Unity.](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)

> [!NOTE]
> A partir da versão 0.1.0, o runtime de Comunicação Remográfica Holográfica não dá suporte a Âncoras, e as funcionalidades ARAnchorManager não funcionarão por meio da comunicação remot.  Esse recurso será lançado em versões futuras.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in do Windows XR](#tab/winxr)

1. Na sua HoloLens, acesse o **Microsoft Store** e instale o **[aplicativo Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. Na sua HoloLens, inicie o **aplicativo Holographic Remoting Player.**
1. No Unity, vá para o menu **Editar** e **selecione Project Configurações**.
1. Selecione **Gerenciamento de Plug-in XR.**
1. Verifique se **a guia Pc, Mac & Linux**  Autônomo está selecionada, Windows Mixed Reality na lista e marque sua caixa de seleção.
1. Em seguida, vá para o menu **Janela,** expanda o submenu **XR** e selecione como Windows de **Plug-in XR.**
1. De **definir Modo de Emulação** como Remoto para **Dispositivo**.
1. Para **Computador Remoto,** insira o endereço IP do seu HoloLens.
1. Para se conectar, qualquer um dos dois:
   1. Para se conectar manualmente, **desmarque Conexão no Play** e selecione **Conexão**. Você deve ver **Status da Conexão** mudar para **Conectado** e ver a tela ficar em branco no HoloLens.
   1. Para se conectar automaticamente, **verifique Conexão em Reproduzir**. O editor tentará se conectar depois que o Modo de Reprodução for iniciado.
1. Selecione o **botão Reproduzir** para iniciar o Modo de Reprodução e experimente o aplicativo em seu HoloLens. Para depurar scripts C# no modo de reprodução, [anexe Visual Studio ao Unity.](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

1. Na sua HoloLens, acesse o **Microsoft Store** e instale o **[aplicativo Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. Na sua HoloLens, inicie o **aplicativo Holographic Remoting Player.**
1. No Unity, acesse o **menu** Janela, expanda o submenu **XR** e selecione **Emulação** Holográfica (marcada como preterida no Unity 2019).
1. De **definir Modo de Emulação** como Remoto para **Dispositivo**.
1. De **definir a Versão** do Dispositivo de acordo com se você estiver usando uma versão de HoloLens ou uma HoloLens 2.
1. Para **Computador Remoto,** insira o endereço IP do seu HoloLens.
1. Selecione **Conectar**. Você deve ver **Status da Conexão** mudar para **Conectado** e ver a tela ficar em branco no HoloLens.
1. Selecione o **botão Reproduzir** para iniciar o Modo de Reprodução e experimente o aplicativo em seu HoloLens. Para depurar scripts C# no modo de reprodução, [anexe Visual Studio ao Unity.](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)
