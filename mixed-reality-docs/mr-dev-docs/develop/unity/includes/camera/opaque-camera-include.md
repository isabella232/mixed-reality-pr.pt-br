---
ms.openlocfilehash: 76f72ac81b677acabf98444f626b7a6b908c29fb
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748445"
---
# <a name="mrtk"></a>[<span data-ttu-id="85395-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="85395-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="85395-102">O MRTK manipulará configurações específicas da câmera automaticamente, com base na [configuração no perfil do sistema de câmera.](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)</span><span class="sxs-lookup"><span data-stu-id="85395-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="85395-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span><span class="sxs-lookup"><span data-stu-id="85395-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="85395-104">**Tipo:** *MixedRealityCameraSystem*</span><span class="sxs-lookup"><span data-stu-id="85395-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="85395-105">Para verificar a opacidade da câmera, o sistema MixedRealityCamera tem [uma `IsOpaque` propriedade](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span><span class="sxs-lookup"><span data-stu-id="85395-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="85395-106">SDK do XR</span><span class="sxs-lookup"><span data-stu-id="85395-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="85395-107">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="85395-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="85395-108">**Tipo:** *XRDisplaySubsystem*</span><span class="sxs-lookup"><span data-stu-id="85395-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="85395-109">Você pode usar o código de script para determinar em runtime se o headset é imersivo ou holográfico verificando [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) no [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)em execução ativamente.</span><span class="sxs-lookup"><span data-stu-id="85395-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="85395-110">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="85395-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="85395-111">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="85395-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="85395-112">**Tipo:** *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="85395-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="85395-113">Você pode usar o código de script para determinar em runtime se o headset é imersivo ou holográfico verificando [HolographicSettings.IsDisplayOpaque.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)</span><span class="sxs-lookup"><span data-stu-id="85395-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>