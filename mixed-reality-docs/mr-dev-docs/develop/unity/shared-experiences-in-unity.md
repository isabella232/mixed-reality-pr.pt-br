---
title: Experiências compartilhadas no Unity
description: Saiba como compartilhar os mesmos hologramas entre vários usuários em um aplicativo do Unity com âncoras espaciais do Azure.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Compartilhamento, ancoragem, WorldAnchor, Sr Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, âncoras espaciais do Azure, ASA, headset de realidade misturada, headset de realidade misturada do Windows, headset da realidade virtual
ms.openlocfilehash: 7762a76e1eaa944f69153b13fb0f380c7dce643e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583365"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="9eb8c-104">Experiências compartilhadas no Unity</span><span class="sxs-lookup"><span data-stu-id="9eb8c-104">Shared experiences in Unity</span></span>

<span data-ttu-id="9eb8c-105">Uma experiência compartilhada permite que vários usuários, cada um com seu próprio dispositivo de HoloLens, iOS ou Android, exibam e interajam coletivamente com o mesmo holograma.</span><span class="sxs-lookup"><span data-stu-id="9eb8c-105">A shared experience lets multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram.</span></span> <span data-ttu-id="9eb8c-106">Os hologramas são posicionados em um ponto fixo no espaço por meio do compartilhamento de âncora espacial.</span><span class="sxs-lookup"><span data-stu-id="9eb8c-106">Holograms are positioned at a fixed point in space through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="9eb8c-107">Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="9eb8c-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="9eb8c-108">As <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> criam âncoras espaciais duráveis com suporte de nuvem, que seu aplicativo pode localizar em vários dispositivos HoloLens, Ios e Android.</span><span class="sxs-lookup"><span data-stu-id="9eb8c-108"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="9eb8c-109">Ao compartilhar uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="9eb8c-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span> 

<span data-ttu-id="9eb8c-110">Você também pode usar <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para a persistência de holograma assíncrona em dispositivos de HoloLens, Ios e Android.</span><span class="sxs-lookup"><span data-stu-id="9eb8c-110">You can also use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="9eb8c-111">Ao compartilhar uma âncora espacial de nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo que esses dispositivos não estejam presentes juntos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="9eb8c-111">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="9eb8c-112">Para começar a criar experiências compartilhadas no Unity, experimente os guias de início rápido dos separadores <a href="/azure/spatial-anchors/unity-overview" target="_blank">espaciais do Azure</a>de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="9eb8c-112">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="9eb8c-113">Depois que as âncoras espaciais do Azure estiverem configuradas, você poderá <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar âncoras no Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="9eb8c-113">Once Azure Spatial Anchors is set up, you can <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="9eb8c-114">Transferências de âncora local</span><span class="sxs-lookup"><span data-stu-id="9eb8c-114">Local anchor transfers</span></span>

<span data-ttu-id="9eb8c-115">Em situações em que você não pode usar âncoras espaciais do Azure, as [transferências de âncora local](../../out-of-scope/local-anchor-transfers-in-unity.md) permitem que um dispositivo de HoloLens exporte uma âncora para que um segundo HoloLens possa importá-lo.</span><span class="sxs-lookup"><span data-stu-id="9eb8c-115">In situations where you can't use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor so that a second HoloLens can import it.</span></span>  <span data-ttu-id="9eb8c-116">Essa abordagem não tem suporte em dispositivos iOS e Android e fornece uma recall de ancoragem menos robusta do que as âncoras espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="9eb8c-116">This approach is not supported on iOS and Android devices, and provides less robust anchor recall than Azure Spatial Anchors.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="9eb8c-117">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="9eb8c-117">Next Development Checkpoint</span></span>

<span data-ttu-id="9eb8c-118">Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos recursos e APIs da plataforma de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="9eb8c-118">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="9eb8c-119">A partir daqui, você pode continuar para a próxima seção:</span><span class="sxs-lookup"><span data-stu-id="9eb8c-119">From here, you can continue to the next section:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9eb8c-120">Câmera localizável</span><span class="sxs-lookup"><span data-stu-id="9eb8c-120">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="9eb8c-121">Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:</span><span class="sxs-lookup"><span data-stu-id="9eb8c-121">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9eb8c-122">Implantar no HoloLens ou em headsets de imersão de realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="9eb8c-122">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="9eb8c-123">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#3-advanced-features) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="9eb8c-123">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="9eb8c-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="9eb8c-124">See also</span></span>
* [<span data-ttu-id="9eb8c-125">Experiências compartilhadas em realidade misturada</span><span class="sxs-lookup"><span data-stu-id="9eb8c-125">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="9eb8c-126"><a href="/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a></span><span class="sxs-lookup"><span data-stu-id="9eb8c-126"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="9eb8c-127"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de âncoras espaciais do Azure para Unity</a></span><span class="sxs-lookup"><span data-stu-id="9eb8c-127"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>