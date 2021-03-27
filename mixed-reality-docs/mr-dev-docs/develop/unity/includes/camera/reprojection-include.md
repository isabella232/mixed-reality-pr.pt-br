---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636248"
---
# <a name="mrtk"></a>[<span data-ttu-id="5b557-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="5b557-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="5b557-102">No momento, o MRTK não tem auxiliares para o modo de Reprojeção.</span><span class="sxs-lookup"><span data-stu-id="5b557-102">MRTK doesn't currently have helpers for the reprojection mode.</span></span> <span data-ttu-id="5b557-103">Consulte uma das outras guias para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="5b557-103">Please see one of the other tabs for more information.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="5b557-104">SDK do XR</span><span class="sxs-lookup"><span data-stu-id="5b557-104">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="5b557-105">O modo de Reprojeção é configurável com a definição de [XRDisplaySubsystem. reprojemode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) para o valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="5b557-105">The reprojection mode is configurable by setting [XRDisplaySubsystem.reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="5b557-106">Por exemplo, se você estiver criando uma [experiência somente de orientação](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) com conteúdo com bloqueio de corpo rígido (por exemplo, conteúdo de vídeo de 360 graus), poderá definir explicitamente o modo de Reprojeção como orientação apenas definindo-o como [reprojemode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span><span class="sxs-lookup"><span data-stu-id="5b557-106">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [ReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="5b557-107">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="5b557-107">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="5b557-108">O modo de Reprojeção é configurável com a definição de [HolographicSettings. reprojemode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) para o valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="5b557-108">The reprojection mode is configurable by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="5b557-109">Por exemplo, se você estiver criando uma [experiência somente de orientação](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) com conteúdo com bloqueio de corpo rígido (por exemplo, conteúdo de vídeo de 360 graus), poderá definir explicitamente o modo de Reprojeção como orientação apenas definindo-o como [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span><span class="sxs-lookup"><span data-stu-id="5b557-109">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>