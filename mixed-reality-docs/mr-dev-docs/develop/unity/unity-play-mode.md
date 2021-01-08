---
title: Modo de reprodução do Unity
description: Saiba como usar o modo de reprodução no editor do Unity para visualizar as alterações do aplicativo em um dispositivo sem implantar um aplicativo.
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicação remota, Holographic comunicação remota, Holographic de comunicação remota, HoloLens, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, modo de reprodução de Unity
ms.openlocfilehash: 9f6c2cafd08fca8a5d60f3fcf5832ee74762e173
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009836"
---
# <a name="unity-play-mode"></a>Modo de reprodução do Unity

Uma maneira rápida de trabalhar em seu projeto de Unity é usar o "modo de reprodução", que executa seu aplicativo localmente no editor do Unity em seu computador. O Unity usa a comunicação remota do Holographic para fornecer uma maneira rápida de visualizar o conteúdo em um dispositivo de HoloLens real. O modo de reprodução também pode ser usado com um headset de realidade mista do Windows anexado ao seu PC de desenvolvimento.

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de reprodução do Unity com comunicação remota do Holographic

Com a comunicação remota do Holographic, você pode experimentar seu aplicativo no HoloLens enquanto ele é executado no editor do Unity em seu computador. Olhar, gesto, voz e entrada de mapeamento espacial são enviados do seu HoloLens para o seu PC. Os quadros renderizados são enviados de volta ao seu HoloLens. Essa é uma ótima maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo.
1. No seu HoloLens, vá para a **Microsoft Store** e instale o aplicativo de **[player de comunicação remota do Holographic](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
2. No seu HoloLens, inicie o aplicativo do **player de comunicação remota do Holographic** .
3. No Unity, vá para o menu **janela** , expanda o submenu **XR** e selecione **emulação Holographic**.
4. Defina o **modo de emulação** como **remoto para dispositivo**.
5. Para **computador remoto**, insira o endereço IP do seu HoloLens.
6. Selecione **Conectar**. Você deve ver o **status da conexão** alterado para **conectado** e ver a tela ficar em branco no HoloLens.
7. Selecione o botão **reproduzir** para iniciar o modo de reprodução e experimentar o aplicativo em seu HoloLens.

A comunicação remota do Holographic exige um PC rápido e uma conexão Wi-Fi. Você pode encontrar mais detalhes na documentação do [player de comunicação remota do Holographic](../platform-capabilities-and-apis/holographic-remoting-player.md) .

Para obter melhores resultados, verifique se seu aplicativo define corretamente o [ponto de foco](focus-point-in-unity.md). Isso ajuda a Holographic a comunicação remota a melhor adaptação à sua cena com a latência de sua conexão sem fio.

## <a name="see-also"></a>Consulte Também
* [Player de Comunicação Remota Holográfica](../platform-capabilities-and-apis/holographic-remoting-player.md)
