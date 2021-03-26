---
title: TeleportHotspot
description: Documentação sobre o componente de HotSpot teleport no MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, teleport System, teleport HotSpot
ms.openlocfilehash: 986105dd771c38b1e26fd9f86df90224110591a4
ms.sourcegitcommit: 4be6f36df9063ccfdce2662e299accc7406b6779
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105582948"
---
# <a name="teleport-hotspot-experimental"></a>Teleport hotspot [experimental]

O HotSpot teleport é um componente que você pode adicionar ao gameobject para garantir que o usuário esteja em uma determinada posição e orientação quando teleport para esse local.

## <a name="usage"></a>Uso

### <a name="how-to-create-a-teleport-hotspot"></a>Como criar um hotspot teleport

Para criar um hotspot teleport, adicione o componente TeleportHotspot a um objeto que também tem um componente colisor. 

![Componente de HotSpot teleport](../images/teleport/TeleportHotspotComponent.png)

Agora, o indicador do ponteiro teleport mudará a cor quando for direcionado por um TeleportHotspot. Quando a ação teleport for concluída sobre o HotSpot, o usuário será teleport ao centro do TeleportHotspot.

Se o sinalizador de orientação de substituição for marcado como desativado, a orientação do usuário corresponderá à do ponto de interrupção teleport.

![Exemplo de HotSpot teleport](../images/teleport/TeleportHotspotExample.gif)
