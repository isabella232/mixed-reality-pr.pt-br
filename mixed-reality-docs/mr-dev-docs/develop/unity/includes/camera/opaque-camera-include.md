---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636249"
---
# <a name="mrtk"></a>[<span data-ttu-id="99a96-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="99a96-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="99a96-102">O MRTK tratará as configurações específicas da câmera automaticamente, com base na [configuração no perfil do sistema da câmera](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span><span class="sxs-lookup"><span data-stu-id="99a96-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="99a96-103">**Namespace:** *Microsoft. MixedReality. Toolkit. CameraSystem*</span><span class="sxs-lookup"><span data-stu-id="99a96-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="99a96-104">**Tipo:** *MixedRealityCameraSystem*</span><span class="sxs-lookup"><span data-stu-id="99a96-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="99a96-105">Para verificar a opaca da câmera, o sistema MixedRealityCamera tem [uma `IsOpaque` Propriedade](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span><span class="sxs-lookup"><span data-stu-id="99a96-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="99a96-106">SDK do XR</span><span class="sxs-lookup"><span data-stu-id="99a96-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="99a96-107">**Namespace:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="99a96-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="99a96-108">**Tipo:** *XRDisplaySubsystem*</span><span class="sxs-lookup"><span data-stu-id="99a96-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="99a96-109">Você pode usar o código de script para determinar em tempo de execução se o headset é imersiva ou Holographic, verificando [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) na [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)em execução ativa.</span><span class="sxs-lookup"><span data-stu-id="99a96-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="99a96-110">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="99a96-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="99a96-111">**Namespace:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="99a96-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="99a96-112">**Tipo:** *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="99a96-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="99a96-113">Você pode usar o código de script para determinar em tempo de execução se o headset é imersiva ou Holographic verificando [HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span><span class="sxs-lookup"><span data-stu-id="99a96-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>