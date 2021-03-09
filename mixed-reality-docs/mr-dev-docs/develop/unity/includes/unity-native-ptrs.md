---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475066"
---
# <a name="mrtk"></a>[<span data-ttu-id="438e7-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="438e7-101">MRTK</span></span>](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a><span data-ttu-id="438e7-102">WindowsMixedRealityUtilities</span><span class="sxs-lookup"><span data-stu-id="438e7-102">WindowsMixedRealityUtilities</span></span>

<span data-ttu-id="438e7-103">**Namespace:** *Microsoft. MixedReality. Toolkit. WindowsMixedReality*</span><span class="sxs-lookup"><span data-stu-id="438e7-103">**Namespace:** *Microsoft.MixedReality.Toolkit.WindowsMixedReality*</span></span><br>
<span data-ttu-id="438e7-104">**Tipo:** *WindowsMixedRealityUtilities*</span><span class="sxs-lookup"><span data-stu-id="438e7-104">**Type:** *WindowsMixedRealityUtilities*</span></span>

<span data-ttu-id="438e7-105">O MRTK fornece tipos já empacotados em ambos os SDKs e do SDK do XR herdados por meio da classe **WindowsMixedRealityUtilities** .</span><span class="sxs-lookup"><span data-stu-id="438e7-105">MRTK provides already-marshalled types across both legacy WSA and XR SDK through the **WindowsMixedRealityUtilities** class.</span></span>

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[<span data-ttu-id="438e7-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="438e7-106">XR SDK</span></span>](#tab/xr)

## <a name="windowsmrenvironment"></a><span data-ttu-id="438e7-107">WindowsMREnvironment</span><span class="sxs-lookup"><span data-stu-id="438e7-107">WindowsMREnvironment</span></span>

<span data-ttu-id="438e7-108">**Namespace:** *UnityEngine. XR. WindowsMR*</span><span class="sxs-lookup"><span data-stu-id="438e7-108">**Namespace:** *UnityEngine.XR.WindowsMR*</span></span><br>
<span data-ttu-id="438e7-109">**Tipo:** *WindowsMREnvironment*</span><span class="sxs-lookup"><span data-stu-id="438e7-109">**Type:** *WindowsMREnvironment*</span></span>

<span data-ttu-id="438e7-110">A classe estática **WindowsMREnvironment** fornece acesso a vários ponteiros nativos.</span><span class="sxs-lookup"><span data-stu-id="438e7-110">The static **WindowsMREnvironment** class provides access to several native pointers.</span></span>

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="438e7-111">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="438e7-111">Legacy WSA</span></span>](#tab/wsa)

## <a name="xrdevice"></a><span data-ttu-id="438e7-112">XRDevice</span><span class="sxs-lookup"><span data-stu-id="438e7-112">XRDevice</span></span>

<span data-ttu-id="438e7-113">**Namespace:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="438e7-113">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="438e7-114">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="438e7-114">**Type:** *XRDevice*</span></span>

<span data-ttu-id="438e7-115">O tipo <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> permite que você obtenha acesso a objetos nativos subjacentes usando o método <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> .</span><span class="sxs-lookup"><span data-stu-id="438e7-115">The <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="438e7-116">O que GetNativePtr retorna varia entre diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="438e7-116">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="438e7-117">No Plataforma Universal do Windows ao direcionar a realidade mista do Windows, XRDevice. GetNativePtr retorna um ponteiro (IntPtr) para a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="438e7-117">On the Universal Windows Platform when targeting Windows Mixed Reality, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span>

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame
    public IntPtr IHolographicCameraPtr; // Windows::Graphics::Holographic::IHolographicCamera
}
```

<span data-ttu-id="438e7-118">Você pode convertê-lo em HolographicFrameNativeData usando o método Marshal. PtrToStructure:</span><span class="sxs-lookup"><span data-stu-id="438e7-118">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

<span data-ttu-id="438e7-119">***IHolographicCameraPtr** é uma matriz de IntPtr empacotada como UnmanagedType. ByValArray com um comprimento igual a MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="438e7-119">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span>
