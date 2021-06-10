---
title: Modo de reprodução do Unity
description: Saiba como usar o Modo de Reprodução no editor do Unity para visualizar as alterações do aplicativo em um dispositivo sem implantar um aplicativo.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, remoting, holographic remoting, holographic remoting player, HoloLens, mixed reality headset, windows mixed reality headset, virtual reality headset, unity play mode
ms.openlocfilehash: caa9d7bf11104ee168fda24fc369de490feb7817
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547096"
---
# <a name="unity-play-mode"></a>Modo de reprodução do Unity

Uma maneira rápida de trabalhar em seu projeto do Unity é usar o "Modo de Reprodução", que executa seu aplicativo localmente no editor do Unity em seu computador. O Unity usa a Holographic Remoting para fornecer uma maneira rápida de visualizar seu conteúdo em um dispositivo HoloLens real. O Modo de Reprodução também pode ser usado com um Windows Mixed Reality headset anexado ao computador de desenvolvimento.

## <a name="holographic-remoting-setup"></a>Configuração de remoção holográfica

1. Primeiro, você precisa instalar [o aplicativo Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) do Microsoft Store em seu HoloLens 2
2. Execute o aplicativo Holographic Remoting Player no HoloLens 2 e você verá o número de versão e o endereço IP ao que se conectar
    * Você precisará da v2.4 ou posterior para trabalhar com o plug-in OpenXR

    ![Captura de tela do Holographic Remoting Player em execução no HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Holographic Remoting no modo de reprodução do Editor do Unity

A criação de um projeto UWP Unity Visual Studio projeto e, em seguida, empacotá-lo e implantá-lo em um dispositivo HoloLens 2 pode levar algum tempo. Uma solução é habilitar o recurso comunicação de comunicação remo do Editor Holográfico, que permite depurar o script C# usando o modo "Reproduzir" diretamente para um dispositivo HoloLens 2 em sua rede. Esse cenário evita a sobrecarga de criação e implantação de um pacote UWP no dispositivo remoto.

1. Siga as etapas em [Configuração de Remoção Holográfica](#holographic-remoting-setup)
2. Abra **a > do Windows XR > De remoção do Editor do OpenXR:**

    ![Captura de tela do painel de configurações do projeto aberto no Editor do Unity com o gerenciamento de plug-in XR realçada](images/openxr-features-img-02.png)

3. Input the IP address you get from the Holographic Remoting app e select **Enable Editor Remoting**

    ![Captura de tela do painel de configurações do projeto aberto no Editor do Unity com recursos realçadas](images/openxr-features-img-03.png)

Agora você pode clicar no botão "Reproduzir" para reproduzir seu aplicativo Unity no aplicativo de Remoção Holográfica em seu HoloLens. Você também pode [anexar Visual Studio ao Unity para](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) depurar scripts C# no modo de reprodução.

> [!NOTE]
> A partir da versão 0.1.0, o runtime de Comunicação Remográfica Holográfica não dá suporte a Âncoras, e as funcionalidades ARAnchorManager não funcionarão por meio da comunicação remot.  Esse recurso será lançado em versões futuras.

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de reprodução do Unity com a Holographic Remoting

Com o Holographic Remoting, você pode experimentar seu aplicativo no HoloLens enquanto ele é executado no editor do Unity em seu computador. O olhar, o gesto, a voz e a entrada de mapeamento espacial são enviados do HoloLens para o computador. Os quadros renderizados são então enviados de volta para o HoloLens. Essa é uma ótima maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo.

[!INCLUDE[](includes/unity-play-mode.md)]

A remoção holográfica requer um computador rápido e Wi-Fi conexão. Você pode encontrar mais detalhes na [documentação do Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)

Para melhores resultados, certifique-se de que seu aplicativo define corretamente o [ponto de foco](focus-point-in-unity.md). Isso ajuda o Holographic Remoting a adaptar melhor sua cena à latência de sua conexão sem fio.

## <a name="see-also"></a>Consulte Também

* [Player de Comunicação Remota Holográfica](../platform-capabilities-and-apis/holographic-remoting-player.md)
