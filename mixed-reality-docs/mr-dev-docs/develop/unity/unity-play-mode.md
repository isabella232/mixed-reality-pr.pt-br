---
title: Modo de reprodução do Unity
description: Saiba como usar o Modo de Reprodução no editor do Unity para visualizar as alterações do aplicativo em um dispositivo sem implantar um aplicativo.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, remoting, holographic remoting, holographic remoting player, HoloLens, mixed reality headset, windows mixed reality headset, virtual reality headset, unity play mode
ms.openlocfilehash: b998233fda34beee0c98795a1efa2c86a53541ba
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392283"
---
# <a name="unity-play-mode"></a>Modo de reprodução do Unity

Uma maneira rápida de trabalhar em seu projeto do Unity é usar o "Modo de Reprodução", que executa seu aplicativo localmente no editor do Unity em seu computador. O Unity usa a Holographic Remoting para fornecer uma maneira rápida de visualizar seu conteúdo em um dispositivo HoloLens real. O Modo de Reprodução também pode ser usado com um Windows Mixed Reality headset anexado ao computador de desenvolvimento.

## <a name="holographic-remoting-setup"></a>Configuração de remoção holográfica

1. Primeiro, você precisa instalar [o aplicativo Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) do Microsoft Store em seu HoloLens 2
2. Execute o aplicativo Holographic Remoting Player no HoloLens 2 e você verá o número de versão e o endereço IP ao que se conectar
    * Você precisará da v2.4 ou posterior para trabalhar com o plug-in OpenXR

    ![Captura de tela do Holographic Remoting Player em execução no HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de reprodução do Unity com a Holographic Remoting

Com o Holographic Remoting, você pode experimentar seu aplicativo no HoloLens enquanto ele é executado no editor do Unity em seu computador. O olhar, o gesto, a voz e a entrada de mapeamento espacial são enviados do HoloLens para o computador. Os quadros renderizados são então enviados de volta para o HoloLens. Essa é uma ótima maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo.

[!INCLUDE[](includes/unity-play-mode.md)]

A remoção holográfica requer um computador rápido e Wi-Fi conexão. Você pode encontrar mais detalhes na [documentação do Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)

Para melhores resultados, certifique-se de que seu aplicativo define corretamente o [ponto de foco](focus-point-in-unity.md). Isso ajuda o Holographic Remoting a adaptar melhor sua cena à latência de sua conexão sem fio.

## <a name="see-also"></a>Consulte Também

* [Player de Comunicação Remota Holográfica](../platform-capabilities-and-apis/holographic-remoting-player.md)
