---
title: Serviço de acompanhamento perdido
description: Visão geral sobre o serviço LostTracking no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 70274639326563b1f3c3a2061dcdbf824fd43709
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176220"
---
# <a name="lost-tracking-service"></a><span data-ttu-id="9bb26-104">Serviço de acompanhamento perdido</span><span class="sxs-lookup"><span data-stu-id="9bb26-104">Lost tracking service</span></span>

![Controle perdido](../images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="9bb26-106">o serviço de extensão de rastreamento perdido fornece HoloLens visual animado de estilo de shell para o estado de rastreamento perdido.</span><span class="sxs-lookup"><span data-stu-id="9bb26-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="9bb26-107">Como usar as extensões de rastreamento perdidas</span><span class="sxs-lookup"><span data-stu-id="9bb26-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="9bb26-108">No perfil do MRTK, adicione o **serviço de rastreamento perdido** às extensões.</span><span class="sxs-lookup"><span data-stu-id="9bb26-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="9bb26-109">Atribua **DefaultLostTrackingServiceProfile** que inclui **LostTrackingVisualPrefab**.</span><span class="sxs-lookup"><span data-stu-id="9bb26-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
