---
title: Modo de reprodução do Unity
description: Saiba como usar o modo de reprodução no editor do Unity para visualizar as alterações do aplicativo em um dispositivo sem implantar um aplicativo.
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicação remota, Holographic comunicação remota, Holographic de comunicação remota, HoloLens, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, modo de reprodução de Unity
ms.openlocfilehash: 35f80b0c217adfd5c5d14799dc882d5c504925aa
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333390"
---
# <a name="unity-play-mode"></a>Modo de reprodução do Unity

Uma maneira rápida de trabalhar em seu projeto de Unity é usar o "modo de reprodução", que executa seu aplicativo localmente no editor do Unity em seu computador. O Unity usa a comunicação remota do Holographic para fornecer uma maneira rápida de visualizar o conteúdo em um dispositivo de HoloLens real. O modo de reprodução também pode ser usado com um headset de realidade mista do Windows anexado ao seu PC de desenvolvimento.

## <a name="holographic-remoting-setup"></a>Configuração de comunicação remota do Holographic

1. Primeiro, você precisa [instalar o aplicativo de player de comunicação remota do Holographic](https://www.microsoft.com/store/productId/9NBLGGH4SV40) do Microsoft Store no seu HoloLens 2
2. Execute o aplicativo de player de comunicação remota do Holographic no HoloLens 2 e você verá o número de versão e o endereço IP para se conectar
    * Você precisará do v 2.4 ou posterior para trabalhar com o plug-in OpenXR

    ![Captura de tela do player de comunicação remota do Holographic em execução no HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Holographic comunicação remota no modo de reprodução do editor do Unity

Criar um projeto de Unity do UWP no projeto do Visual Studio e, em seguida, compactá-lo e implantá-lo em um dispositivo HoloLens 2 pode levar algum tempo. Uma solução é habilitar o recurso de comunicação remota do editor do Holographic, que permite que você depure seu script C# usando o modo "Play" diretamente em um dispositivo de HoloLens 2 na rede. Esse cenário evita a sobrecarga de criar e implantar um pacote UWP para um dispositivo remoto.

1. Siga as etapas na [instalação do Holographic Remoting](#holographic-remoting-setup)
2. Abra o **Windows > XR > o editor de OpenXR comunicação remota**:

    ![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](images/openxr-features-img-02.png)

3. Insira o endereço IP obtido do aplicativo de comunicação remota Holographic e selecione **habilitar comunicação remota do editor**

    ![Captura de tela do painel de configurações do projeto aberto no editor do Unity com recursos realçados](images/openxr-features-img-03.png)

Agora você pode clicar no botão "reproduzir" para reproduzir seu aplicativo do Unity no aplicativo de comunicação remota do Holographic em seu HoloLens. Você também pode [anexar Visual Studio ao Unity para](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) depurar scripts C# no modo de reprodução.

> [!NOTE]
> A partir da versão 0.1.0, o runtime de Comunicação Remográfica Holográfica não dá suporte a Âncoras, e as funcionalidades ARAnchorManager não funcionarão por meio da comunicação remot.  Esse recurso será lançado em versões futuras.

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de reprodução do Unity com a Holographic Remoting

Com o Holographic Remoting, você pode experimentar seu aplicativo no HoloLens enquanto ele é executado no editor do Unity em seu computador. O olhar, o gesto, a voz e a entrada de mapeamento espacial são enviados do HoloLens para o computador. Os quadros renderizados são então enviados de volta para o HoloLens. Essa é uma ótima maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo.
1. No HoloLens, acesse o Microsoft Store **e** instale o **[aplicativo Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
2. No HoloLens, inicie o **aplicativo Holographic Remoting Player.**
3. No Unity, vá para o menu **Janela,** expanda o submenu **XR** e selecione **Emulação holográfica**.
4. De **definir Modo de Emulação** como Remoto para **Dispositivo**.
5. Para **Computador Remoto,** insira o endereço IP do HoloLens.
6. Selecione **Conectar**. Você deve ver **Status da Conexão** mudar para **Conectado** e ver a tela ficar em branco no HoloLens.
7. Selecione o **botão Reproduzir** para iniciar o Modo de Reprodução e experimentar o aplicativo no HoloLens.

A remoção holográfica requer um computador rápido e Wi-Fi conexão. Você pode encontrar mais detalhes na [documentação do Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)

Para melhores resultados, certifique-se de que seu aplicativo define corretamente o [ponto de foco](focus-point-in-unity.md). Isso ajuda o Holographic Remoting a adaptar melhor sua cena à latência de sua conexão sem fio.

## <a name="see-also"></a>Consulte Também
* [Player de Comunicação Remota Holográfica](../platform-capabilities-and-apis/holographic-remoting-player.md)
