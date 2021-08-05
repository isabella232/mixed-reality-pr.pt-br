---
title: Hotspot de teletransporte
description: Documentação sobre o componente Hotspot Dev No MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, sistema Dev, Hotspot DeTransporte
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 755b0e8f53be2f393b52395309ed9ab0fad96cadc2e4289400cfff45a99aa6a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189446"
---
# <a name="teleport-hotspot"></a>Hotspot de teletransporte

O hotspot de teletransporte é um componente que você pode adicionar ao gameobject para garantir que o usuário está em uma determinada posição e orientação quando ele for para esse local.

## <a name="usage"></a>Uso

### <a name="how-to-create-a-teleport-hotspot"></a>Como criar um hotspot detransporte

Para criar um hotspot de teletransporte, adicione o componenteHotspot a um objeto que também tem um componente colisor. 

![Componente Hotspot Detrans](../images/teleport/TeleportHotspotComponent.png)

Agora, o indicador do ponteiro de teletransporte mudará de cor quando ele for direcionado sobre um Hothotspot. Quando a ação de teletransporte for concluída sobre o ponto de acesso, o usuário será teletransportado para o centro doHotHotspot.

Se o sinalizador de orientação de substituição estiver marcado, a orientação do usuário corresponderá à do hotspot detransporte.

![Exemplo de Hotspot Demão](../images/teleport/TeleportHotspotExample.gif)
