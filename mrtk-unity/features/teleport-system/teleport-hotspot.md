---
title: Hotspot Demão
description: Documentação sobre o componente Hotspot Dev No MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Sistema Detransporte, Hotspot DeTransporte
ms.openlocfilehash: 0cbdad3c038d457109077b742d3f453d63436ae4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144431"
---
# <a name="teleport-hotspot-experimental"></a><span data-ttu-id="c186e-104">Hotspot Demão [Experimental]</span><span class="sxs-lookup"><span data-stu-id="c186e-104">Teleport Hotspot [Experimental]</span></span>

<span data-ttu-id="c186e-105">O hotspot de teletransporte é um componente que você pode adicionar ao gameobject para garantir que o usuário está em uma determinada posição e orientação quando ele for para esse local.</span><span class="sxs-lookup"><span data-stu-id="c186e-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="c186e-106">Uso</span><span class="sxs-lookup"><span data-stu-id="c186e-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="c186e-107">Como criar um hotspot detransporte</span><span class="sxs-lookup"><span data-stu-id="c186e-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="c186e-108">Para criar um hotspot de teletransporte, adicione o componenteHotspot a um objeto que também tem um componente colisor.</span><span class="sxs-lookup"><span data-stu-id="c186e-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Componente Hotspot Detrans](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="c186e-110">Agora, o indicador do ponteiro de teletransporte mudará de cor quando ele for direcionado sobre um Hothotspot.</span><span class="sxs-lookup"><span data-stu-id="c186e-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="c186e-111">Quando a ação de teletransporte for concluída sobre o ponto de acesso, o usuário será teletransportado para o centro doHotHotspot.</span><span class="sxs-lookup"><span data-stu-id="c186e-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="c186e-112">Se o sinalizador de orientação de substituição estiver marcado, a orientação do usuário corresponderá à do hotspot detransporte.</span><span class="sxs-lookup"><span data-stu-id="c186e-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Exemplo de Hotspot Demão](../images/teleport/TeleportHotspotExample.gif)
