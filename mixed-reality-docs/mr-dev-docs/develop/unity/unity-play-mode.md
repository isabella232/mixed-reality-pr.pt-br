---
title: Visualizar seu trabalho com a comunicação remota holográfica
description: Use a comunicação remota do Holographic no modo de reprodução para visualizar as alterações do aplicativo em um dispositivo sem implantar um aplicativo.
author: keveleigh
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: Unity, comunicação remota, holographic de comunicação remota, holographic de comunicação remota, HoloLens, headset de realidade mista, headset de realidade mista do windows, headset de realidade virtual, modo de reprodução de unity
ms.openlocfilehash: cd9dca9d1ddf17b78e8c317fa3a58093c9b5837de379510148c6e645b31120ca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226228"
---
# <a name="preview-your-work-with-holographic-remoting"></a>Visualizar seu trabalho com a comunicação remota holográfica

você pode usar a comunicação remota do Holographic para transmitir conteúdo do Holographic para seu HoloLens 2 em tempo real. Essa é uma ótima maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo. 

Uma maneira rápida de trabalhar em seu projeto de Unity é usar o "modo de reprodução", que executa seu aplicativo localmente no editor do Unity em seu computador. o Unity usa a comunicação remota do Holographic para fornecer uma maneira rápida de visualizar o conteúdo em um dispositivo de HoloLens real. o modo de reprodução também pode ser usado com um Windows Mixed Reality headset conectado ao seu PC de desenvolvimento.

## <a name="holographic-remoting-setup"></a>Configuração de comunicação remota do Holographic

1. primeiro, você precisa [instalar o aplicativo de Player de comunicação remota do Holographic](https://www.microsoft.com/store/productId/9NBLGGH4SV40) do Microsoft Store no seu HoloLens 2
2. execute o aplicativo de Player de comunicação remota do Holographic no HoloLens 2 e você verá o número de versão e o endereço IP para se conectar
    * Você precisará do v 2.4 ou posterior para trabalhar com o plug-in OpenXR

    ![Captura de tela do player de comunicação remota do Holographic em execução no HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de reprodução do Unity com comunicação remota do Holographic

com a comunicação remota do Holographic, você pode experimentar seu aplicativo no HoloLens enquanto ele é executado no editor do Unity em seu computador. olhar, gesto, voz e entrada de mapeamento espacial são enviados de seu HoloLens para o seu PC. Os quadros renderizados são enviados de volta para o HoloLens. Essa é uma ótima maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo.

[!INCLUDE[](includes/unity-play-mode.md)]

A comunicação remota do Holographic exige um PC rápido e uma conexão Wi-Fi. Você pode encontrar mais detalhes na documentação do [player de comunicação remota do Holographic](../platform-capabilities-and-apis/holographic-remoting-player.md) .

Para obter melhores resultados, verifique se seu aplicativo define corretamente o [ponto de foco](focus-point-in-unity.md). Isso ajuda a Holographic a comunicação remota a melhor adaptação à sua cena com a latência de sua conexão sem fio.

## <a name="see-also"></a>Consulte Também

* [Player de Comunicação Remota Holográfica](../platform-capabilities-and-apis/holographic-remoting-player.md)
