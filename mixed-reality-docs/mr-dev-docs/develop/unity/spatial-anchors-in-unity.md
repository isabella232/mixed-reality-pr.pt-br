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
# <a name="spatial-anchors-in-unity"></a><span data-ttu-id="489bf-104">Âncoras espaciais no Unity</span><span class="sxs-lookup"><span data-stu-id="489bf-104">Spatial Anchors in Unity</span></span>

<span data-ttu-id="489bf-105">Âncoras espaciais salvam hologramas em espaço real entre as sessões do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="489bf-105">Spatial anchors save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="489bf-106">Depois de salvo no repositório de âncora do HoloLens, eles podem ser encontrados e carregados em diferentes sessões e são um fallback ideal quando não há conectividade com a Internet.</span><span class="sxs-lookup"><span data-stu-id="489bf-106">Once saved in the HoloLens' anchor store, they can be found and loaded in different sessions and are an ideal fallback when there's no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="489bf-107">Elas são armazenadas no dispositivo, enquanto as Âncoras Espaciais do Azure são armazenadas na nuvem.</span><span class="sxs-lookup"><span data-stu-id="489bf-107">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="489bf-108">Se você pretende usar os serviços de nuvem do Azure para armazenar suas âncoras, temos um documento que pode orientar você na integração das [Âncoras Espaciais do Azure](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span><span class="sxs-lookup"><span data-stu-id="489bf-108">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span></span> <span data-ttu-id="489bf-109">Você pode ter âncoras locais e do Azure no mesmo projeto sem conflitos.</span><span class="sxs-lookup"><span data-stu-id="489bf-109">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="understanding-anchors"></a><span data-ttu-id="489bf-110">Noções básicas sobre âncoras</span><span class="sxs-lookup"><span data-stu-id="489bf-110">Understanding Anchors</span></span>

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a><span data-ttu-id="489bf-111">Usando o AnchorStore</span><span class="sxs-lookup"><span data-stu-id="489bf-111">Using the AnchorStore</span></span>

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="489bf-112">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="489bf-112">Next Development Checkpoint</span></span>

<span data-ttu-id="489bf-113">Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos principais blocos de construção da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="489bf-113">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="489bf-114">Deste ponto, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="489bf-114">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="489bf-115">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="489bf-115">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="489bf-116">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="489bf-116">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="489bf-117">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="489bf-117">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="489bf-118">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="489bf-118">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="489bf-119">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="489bf-119">See Also</span></span>
* [<span data-ttu-id="489bf-120">Persistência de ancoragem espacial</span><span class="sxs-lookup"><span data-stu-id="489bf-120">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="489bf-121"><a href="/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a></span><span class="sxs-lookup"><span data-stu-id="489bf-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="489bf-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de âncoras espaciais do Azure para Unity</a></span><span class="sxs-lookup"><span data-stu-id="489bf-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
* [<span data-ttu-id="489bf-123">Escalas de experiência</span><span class="sxs-lookup"><span data-stu-id="489bf-123">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="489bf-124">Estágio espacial</span><span class="sxs-lookup"><span data-stu-id="489bf-124">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="489bf-125">Como controlar a perda no Unity</span><span class="sxs-lookup"><span data-stu-id="489bf-125">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="489bf-126">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="489bf-126">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="489bf-127">Experiências compartilhadas no Unity</span><span class="sxs-lookup"><span data-stu-id="489bf-127">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)