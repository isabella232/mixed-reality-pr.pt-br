---
title: Âncoras espaciais no Unity
description: Saiba como criar, armazenar e buscar âncoras espaciais em aplicativos de realidade misturada no Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity, âncoras espaciais, repositório de ancoragem, HoloLens, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623616"
---
# <a name="spatial-anchors-in-unity"></a>Âncoras espaciais no Unity

Âncoras espaciais salvam hologramas em espaço real entre as sessões do aplicativo. Depois de salvo no repositório de âncora do HoloLens, eles podem ser encontrados e carregados em diferentes sessões e são um fallback ideal quando não há conectividade com a Internet.

> [!IMPORTANT]
> Elas são armazenadas no dispositivo, enquanto as Âncoras Espaciais do Azure são armazenadas na nuvem. Se você pretende usar os serviços de nuvem do Azure para armazenar suas âncoras, temos um documento que pode orientar você na integração das [Âncoras Espaciais do Azure](../mixed-reality-cloud-services.md#azure-spatial-anchors). Você pode ter âncoras locais e do Azure no mesmo projeto sem conflitos.

## <a name="understanding-anchors"></a>Noções básicas sobre âncoras

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a>Usando o AnchorStore

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos principais blocos de construção da realidade misturada. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Mapeamento espacial](spatial-mapping-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Consulte Também
* [Persistência de ancoragem espacial](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de âncoras espaciais do Azure para Unity</a>
* [Escalas de experiência](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Estágio espacial](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Como controlar a perda no Unity](tracking-loss-in-unity.md)
* [Âncoras espaciais](../../design/spatial-anchors.md)
* [Experiências compartilhadas no Unity](shared-experiences-in-unity.md)