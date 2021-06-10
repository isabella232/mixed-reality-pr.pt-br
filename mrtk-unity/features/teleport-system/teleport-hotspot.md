---
title: Hotspot Demão
description: Documentação sobre o componente Hotspot Dev No MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Sistema Detransporte, Hotspot DeTransporte
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 2d6160570b43ca931d46f4ec04c604b53b18d731
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647037"
---
# <a name="teleport-hotspot"></a><span data-ttu-id="35e9c-104">Hotspot Demão</span><span class="sxs-lookup"><span data-stu-id="35e9c-104">Teleport Hotspot</span></span>

<span data-ttu-id="35e9c-105">O hotspot de teletransporte é um componente que você pode adicionar ao gameobject para garantir que o usuário está em uma determinada posição e orientação quando ele for para esse local.</span><span class="sxs-lookup"><span data-stu-id="35e9c-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="35e9c-106">Uso</span><span class="sxs-lookup"><span data-stu-id="35e9c-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="35e9c-107">Como criar um hotspot detransporte</span><span class="sxs-lookup"><span data-stu-id="35e9c-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="35e9c-108">Para criar um hotspot de teletransporte, adicione o componenteHotspot a um objeto que também tem um componente colisor.</span><span class="sxs-lookup"><span data-stu-id="35e9c-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Componente Hotspot Detrans](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="35e9c-110">Agora, o indicador do ponteiro de teletransporte mudará de cor quando ele for direcionado sobre um Hothotspot.</span><span class="sxs-lookup"><span data-stu-id="35e9c-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="35e9c-111">Quando a ação de teletransporte for concluída sobre o ponto de acesso, o usuário será teletransportado para o centro doHotHotspot.</span><span class="sxs-lookup"><span data-stu-id="35e9c-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="35e9c-112">Se o sinalizador de orientação de substituição estiver marcado, a orientação do usuário corresponderá à do hotspot detransporte.</span><span class="sxs-lookup"><span data-stu-id="35e9c-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Exemplo de Hotspot Demão](../images/teleport/TeleportHotspotExample.gif)
