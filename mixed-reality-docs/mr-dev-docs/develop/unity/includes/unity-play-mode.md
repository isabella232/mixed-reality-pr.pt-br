---
ms.openlocfilehash: 17719d2547aa10981e7b8cdf0d2c7d56823e6da5
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345100"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. No HoloLens, acesse o Microsoft Store **e** instale o **[aplicativo Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. No HoloLens, inicie o **aplicativo Holographic Remoting Player.**
1. No Unity, vá para o menu **Editar** e selecione **Configurações do Projeto**.
1. Selecione **Gerenciamento de Plug-in XR.**
1. Verifique se **a guia Autônomo do Windows** está selecionada, encontre **OpenXR** **e Windows Mixed Reality de** recursos definidos na lista e marque suas caixas de seleção.
1. Em seguida, vá para o menu **Janela,** expanda o submenu **XR** e selecione **OpenXR Editor Remoting**.
1. Clique **em Habilitar a Remoting do Editor.**
1. Se o **botão Habilitar Dependências Ausentes** for exibido, clique nessa também. A caixa de erro acima do botão descreve os recursos que ele está habilitando e por quê.
1. Para **Nome do Host Remoto**, insira o endereço IP do HoloLens.
   1. Altere outras configurações conforme necessário.
   1. O editor tentará se conectar depois que o Modo de Reprodução for iniciado.
1. Selecione o **botão Reproduzir** para iniciar o Modo de Reprodução e experimentar o aplicativo no HoloLens.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in do Windows XR](#tab/winxr)

1. No HoloLens, acesse o Microsoft Store **e** instale o **[aplicativo Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. No HoloLens, inicie o **aplicativo Holographic Remoting Player.**
1. No Unity, vá para o menu **Editar** e selecione **Configurações do Projeto**.
1. Selecione **Gerenciamento de Plug-in XR.**
1. Verifique se **a guia Autônomo do Windows** está selecionada, **Windows Mixed Reality** na lista e marque sua caixa de seleção.
1. Em seguida, vá para o menu **Janela,** expanda o submenu **XR** e selecione **Windows XR Plugin Remoting**.
1. De **definir Modo de Emulação** como Remoto para **Dispositivo**.
1. Para **Computador Remoto,** insira o endereço IP do HoloLens.
1. Para se conectar, qualquer um dos dois:
   1. Para se conectar manualmente, **desmarque Conectar na Reprodução** e selecione **Conectar**. Você deve ver **Status da Conexão** mudar para **Conectado** e ver a tela ficar em branco no HoloLens.
   1. Para se conectar automaticamente, **marque Conectar no Play.** O editor tentará se conectar depois que o Modo de Reprodução for iniciado.
1. Selecione o **botão Reproduzir** para iniciar o Modo de Reprodução e experimentar o aplicativo no HoloLens.

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

1. No HoloLens, acesse o Microsoft Store **e** instale o **[aplicativo Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. No HoloLens, inicie o **aplicativo Holographic Remoting Player.**
1. No Unity, acesse o **menu** Janela, expanda o submenu **XR** e selecione **Emulação** Holográfica (marcada como preterida no Unity 2019).
1. De **definir Modo de Emulação** como Remoto para **Dispositivo**.
1. De **definir a Versão** do Dispositivo de acordo com se você estiver usando um HoloLens de primeira geração ou um HoloLens 2.
1. Para **Computador Remoto,** insira o endereço IP do HoloLens.
1. Selecione **Conectar**. Você deve ver **Status da Conexão** mudar para **Conectado** e ver a tela ficar em branco no HoloLens.
1. Selecione o **botão Reproduzir** para iniciar o Modo de Reprodução e experimentar o aplicativo no HoloLens.
