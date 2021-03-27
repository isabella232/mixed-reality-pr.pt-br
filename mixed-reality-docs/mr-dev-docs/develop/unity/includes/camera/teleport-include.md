---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636250"
---
# <a name="mrtk"></a>[<span data-ttu-id="e53a7-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="e53a7-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="e53a7-102">O MRTK fornece um [sistema teleport](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) na caixa que funciona automaticamente entre as mãos e os controladores articulados.</span><span class="sxs-lookup"><span data-stu-id="e53a7-102">MRTK provides an in-box [teleport system](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) which automatically works across articulated hands and controllers.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="e53a7-103">SDK do XR</span><span class="sxs-lookup"><span data-stu-id="e53a7-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="e53a7-104">É recomendável usar a implementação de teleportabilidade do MRTK.</span><span class="sxs-lookup"><span data-stu-id="e53a7-104">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="e53a7-105">Se você optar por não usar o MRTK, o Unity fornecerá uma implementação de teleportação no [Kit de ferramentas de interação do XR](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span><span class="sxs-lookup"><span data-stu-id="e53a7-105">If you choose not to use MRTK, Unity provides a teleportation implementation in the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span></span>
<span data-ttu-id="e53a7-106">Se você optar por implementar seu próprio, é bom ter em mente que não é possível mover a câmera diretamente.</span><span class="sxs-lookup"><span data-stu-id="e53a7-106">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="e53a7-107">Devido ao controle do Unity da câmera para acompanhamento de cabeçalho, você precisará dar à câmera um pai na hierarquia e mover esse gameobject em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e53a7-107">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="e53a7-108">Esse é o equivalente do Playspace da MRTK.</span><span class="sxs-lookup"><span data-stu-id="e53a7-108">This is the equivalent of MRTK's Playspace.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="e53a7-109">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="e53a7-109">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="e53a7-110">É recomendável usar a implementação de teleportabilidade do MRTK.</span><span class="sxs-lookup"><span data-stu-id="e53a7-110">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="e53a7-111">Se você optar por implementar seu próprio, é bom ter em mente que não é possível mover a câmera diretamente.</span><span class="sxs-lookup"><span data-stu-id="e53a7-111">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="e53a7-112">Devido ao controle do Unity da câmera para acompanhamento de cabeçalho, você precisará dar à câmera um pai na hierarquia e mover esse gameobject em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e53a7-112">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="e53a7-113">Esse é o equivalente do Playspace da MRTK.</span><span class="sxs-lookup"><span data-stu-id="e53a7-113">This is the equivalent of MRTK's Playspace.</span></span>