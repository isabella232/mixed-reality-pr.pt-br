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
# <a name="teleport-hotspot-experimental"></a><span data-ttu-id="13abb-104">Teleport hotspot [experimental]</span><span class="sxs-lookup"><span data-stu-id="13abb-104">Teleport Hotspot [Experimental]</span></span>

<span data-ttu-id="13abb-105">O HotSpot teleport é um componente que você pode adicionar ao gameobject para garantir que o usuário esteja em uma determinada posição e orientação quando teleport para esse local.</span><span class="sxs-lookup"><span data-stu-id="13abb-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="13abb-106">Uso</span><span class="sxs-lookup"><span data-stu-id="13abb-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="13abb-107">Como criar um hotspot teleport</span><span class="sxs-lookup"><span data-stu-id="13abb-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="13abb-108">Para criar um hotspot teleport, adicione o componente TeleportHotspot a um objeto que também tem um componente colisor.</span><span class="sxs-lookup"><span data-stu-id="13abb-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Componente de HotSpot teleport](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="13abb-110">Agora, o indicador do ponteiro teleport mudará a cor quando for direcionado por um TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="13abb-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="13abb-111">Quando a ação teleport for concluída sobre o HotSpot, o usuário será teleport ao centro do TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="13abb-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="13abb-112">Se o sinalizador de orientação de substituição for marcado como desativado, a orientação do usuário corresponderá à do ponto de interrupção teleport.</span><span class="sxs-lookup"><span data-stu-id="13abb-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Exemplo de HotSpot teleport](../images/teleport/TeleportHotspotExample.gif)
