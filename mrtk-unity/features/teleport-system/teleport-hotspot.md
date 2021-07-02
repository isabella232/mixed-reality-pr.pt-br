---
title: Hotspot Demão
description: Documentação sobre o componente Hotspot Dev No MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, sistema Dev, Hotspot DeTransporte
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 01ae900800c4a13ca7bafc3391ff51b752a95ae0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176205"
---
# <a name="teleport-hotspot"></a>Hotspot Demão

O hotspot de teletransporte é um componente que você pode adicionar ao gameobject para garantir que o usuário está em uma determinada posição e orientação quando ele for para esse local.

## <a name="usage"></a>Uso

### <a name="how-to-create-a-teleport-hotspot"></a>Como criar um hotspot detransporte

Para criar um hotspot de teletransporte, adicione o componenteHotspot a um objeto que também tem um componente colisor. 

![Componente Hotspot Detrans](../images/teleport/TeleportHotspotComponent.png)

Agora, o indicador do ponteiro de teletransporte mudará de cor quando ele for direcionado sobre um Hothotspot. Quando a ação de teletransporte for concluída sobre o ponto de acesso, o usuário será teletransportado para o centro doHotHotspot.

Se o sinalizador de orientação de substituição estiver marcado, a orientação do usuário corresponderá à do hotspot detransporte.

![Exemplo de Hotspot Demão](../images/teleport/TeleportHotspotExample.gif)
