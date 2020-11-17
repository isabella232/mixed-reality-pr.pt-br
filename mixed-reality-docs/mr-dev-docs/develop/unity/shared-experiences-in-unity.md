---
title: Experiências compartilhadas no Unity
description: Compartilhe os mesmos hologramas entre vários usuários em um aplicativo do Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Compartilhamento, ancoragem, WorldAnchor, Sr Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, âncoras espaciais do Azure, ASA, headset de realidade misturada, headset de realidade misturada do Windows, headset da realidade virtual
ms.openlocfilehash: c9f432a2ef26e28a2329f9fd191f680a4148ca7e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678455"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="bcf65-104">Experiências compartilhadas no Unity</span><span class="sxs-lookup"><span data-stu-id="bcf65-104">Shared experiences in Unity</span></span>

<span data-ttu-id="bcf65-105">Uma experiência compartilhada é aquela em que vários usuários, cada um com seu próprio dispositivo de HoloLens, iOS ou Android, exibem e interagem coletivamente com o mesmo holograma que é posicionado em um ponto fixo no espaço.</span><span class="sxs-lookup"><span data-stu-id="bcf65-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="bcf65-106">Isso é feito por meio do compartilhamento de âncora espacial.</span><span class="sxs-lookup"><span data-stu-id="bcf65-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="bcf65-107">Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="bcf65-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="bcf65-108">Você pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar âncoras espaciais duráveis com suporte de nuvem, que seu aplicativo pode localizar em vários dispositivos HoloLens, Ios e Android.</span><span class="sxs-lookup"><span data-stu-id="bcf65-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="bcf65-109">Ao compartilhar uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="bcf65-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="bcf65-110">Isso permite experiências compartilhadas em tempo real.</span><span class="sxs-lookup"><span data-stu-id="bcf65-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="bcf65-111">Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Âncoras Espaciais do Azure</a> para persistência assíncrona de holograma em dispositivos HoloLens, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="bcf65-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="bcf65-112">Ao compartilhar uma âncora espacial em nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo que os dispositivos não estejam presentes ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="bcf65-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="bcf65-113">Para começar a criar experiências compartilhadas no Unity, experimente os guias de início rápido dos separadores <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">espaciais do Azure</a>de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="bcf65-113">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="bcf65-114">Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar âncoras no Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="bcf65-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="bcf65-115">Transferências de âncora local</span><span class="sxs-lookup"><span data-stu-id="bcf65-115">Local anchor transfers</span></span>

<span data-ttu-id="bcf65-116">Em situações em que você não pode usar âncoras espaciais do Azure, as [transferências de âncora local](../../out-of-scope/local-anchor-transfers-in-unity.md) permitem que um dispositivo de hololens exporte uma âncora a ser importada por um segundo dispositivo hololens.</span><span class="sxs-lookup"><span data-stu-id="bcf65-116">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="bcf65-117">Observe que essa abordagem fornece uma recall de ancoragem menos robusta do que as âncoras espaciais do Azure, e os dispositivos iOS e Android não são compatíveis com essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="bcf65-117">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="bcf65-118">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="bcf65-118">Next Development Checkpoint</span></span>

<span data-ttu-id="bcf65-119">Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos recursos e APIs da plataforma de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="bcf65-119">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="bcf65-120">Daí, você pode prosseguir para o próximo tópico:</span><span class="sxs-lookup"><span data-stu-id="bcf65-120">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bcf65-121">Câmera localizável</span><span class="sxs-lookup"><span data-stu-id="bcf65-121">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="bcf65-122">Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:</span><span class="sxs-lookup"><span data-stu-id="bcf65-122">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bcf65-123">Implantar no HoloLens ou em headsets de imersão de realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="bcf65-123">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="bcf65-124">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#3-platform-capabilities-and-apis) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="bcf65-124">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="bcf65-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="bcf65-125">See also</span></span>
* [<span data-ttu-id="bcf65-126">Experiências compartilhadas em realidade misturada</span><span class="sxs-lookup"><span data-stu-id="bcf65-126">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="bcf65-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a></span><span class="sxs-lookup"><span data-stu-id="bcf65-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="bcf65-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de âncoras espaciais do Azure para Unity</a></span><span class="sxs-lookup"><span data-stu-id="bcf65-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
