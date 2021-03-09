---
title: Objetos nativos de realidade misturada no Unity
description: Saiba como obter acesso a objetos Holographic nativos subjacentes no Unity usando o namespace XR.
author: vladkol
ms.author: vladkol
ms.date: 02/25/2021
ms.topic: article
keywords: Unity, realidade misturada, nativa, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: c202c698fe55bcd3215850579166ebcb8d4b8910
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475065"
---
# <a name="mixed-reality-native-interop-in-unity"></a><span data-ttu-id="a24a7-104">Interoperabilidade nativa de realidade misturada no Unity</span><span class="sxs-lookup"><span data-stu-id="a24a7-104">Mixed Reality native interop in Unity</span></span>

<span data-ttu-id="a24a7-105">Todo aplicativo de realidade misturada [recebe um HolographicSpace antes de começar a](../native/getting-a-holographicspace.md) receber dados da câmera e renderizar quadros.</span><span class="sxs-lookup"><span data-stu-id="a24a7-105">Every Mixed Reality app [gets a HolographicSpace](../native/getting-a-holographicspace.md) before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="a24a7-106">No Unity, o mecanismo cuida dessas etapas para você, manipulando objetos Holographic e atualizando internamente como parte de seu loop de processamento.</span><span class="sxs-lookup"><span data-stu-id="a24a7-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and internally updating as part of its render loop.</span></span>

<span data-ttu-id="a24a7-107">No entanto, em cenários avançados, talvez seja necessário obter acesso aos objetos nativos subjacentes, como o <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e o <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>atual.</span><span class="sxs-lookup"><span data-stu-id="a24a7-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span>

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="a24a7-108">Desempacotamento de ponteiros nativos</span><span class="sxs-lookup"><span data-stu-id="a24a7-108">Unmarshaling native pointers</span></span>

<span data-ttu-id="a24a7-109">Depois de obter o `IntPtr` de um dos métodos acima (não é necessário para MRTK), use os trechos de código a seguir para empacotá-los para objetos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="a24a7-109">After obtaining the `IntPtr` from one of the methods above (not needed for MRTK), use the following code snippets to marshal them to managed objects.</span></span>

<span data-ttu-id="a24a7-110">Se você estiver usando [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), poderá construir um objeto gerenciado a partir de um ponteiro nativo usando o `FromNativePtr()` método:</span><span class="sxs-lookup"><span data-stu-id="a24a7-110">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

<span data-ttu-id="a24a7-111">Caso contrário, use `Marshal.GetObjectForIUnknown()` e converta para o tipo desejado:</span><span class="sxs-lookup"><span data-stu-id="a24a7-111">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the type you want:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="a24a7-112">Convertendo entre sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="a24a7-112">Converting between coordinate systems</span></span>

<span data-ttu-id="a24a7-113">O Unity usa um sistema de coordenadas à esquerda, enquanto as APIs de percepção do Windows usam sistemas de coordenadas à mão.</span><span class="sxs-lookup"><span data-stu-id="a24a7-113">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="a24a7-114">Para converter entre essas duas convenções, você pode usar os seguintes auxiliares:</span><span class="sxs-lookup"><span data-stu-id="a24a7-114">To convert between these two conventions, you can use the following helpers:</span></span>

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(q.X, q.Y, -q.Z, -q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(q.x, q.y, -q.z, -q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="a24a7-115">Usando dados nativos do HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="a24a7-115">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="a24a7-116">Alterar o estado dos objetos nativos recebidos por meio de HolographicFrameNativeData pode causar comportamento imprevisível e artefatos de renderização, especialmente se o Unity também tiver motivos sobre o mesmo estado.</span><span class="sxs-lookup"><span data-stu-id="a24a7-116">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behavior and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="a24a7-117">Por exemplo, você não deve chamar HolographicFrame. UpdateCurrentPrediction ou a previsão de pose que o Unity renderiza com esse quadro estará fora de sincronia com a pose esperada pelo Windows, o que reduzirá a [estabilidade do holograma](../platform-capabilities-and-apis/hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="a24a7-117">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](../platform-capabilities-and-apis/hologram-stability.md).</span></span>

<span data-ttu-id="a24a7-118">Se você precisar de acesso a interfaces nativas para fins de processamento ou depuração, use dados do HolographicFrameNativeData em seus plug-ins nativos ou código C#.</span><span class="sxs-lookup"><span data-stu-id="a24a7-118">If you need access to native interfaces for rendering or debugging purposes, use data from HolographicFrameNativeData in your native plugins or C# code.</span></span>

<span data-ttu-id="a24a7-119">Aqui está um exemplo de como você pode usar o HolographicFrameNativeData para obter a previsão do quadro atual para o tempo de Photon usando as extensões do XR SDK.</span><span class="sxs-lookup"><span data-stu-id="a24a7-119">Here's an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time using the XR SDK extensions.</span></span>

```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if ENABLE_WINMD_SUPPORT
    IntPtr holographicFramePtr = UnityEngine.XR.WindowsMR.WindowsMREnvironment.CurrentHolographicRenderFrame;

    if (holographicFramePtr != IntPtr.Zero)
    {
        var holographicFrame = Marshal.GetObjectForIUnknown(holographicFramePtr) as Windows.Graphics.Holographic.HolographicFrame;
        frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
        return true;
    }
#endif

    frameDateTime = DateTime.MinValue;
    return false;
}
```

## <a name="see-also"></a><span data-ttu-id="a24a7-120">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="a24a7-120">See Also</span></span>

* [<span data-ttu-id="a24a7-121">Como usar o namespace do Windows com aplicativos Unity para HoloLens</span><span class="sxs-lookup"><span data-stu-id="a24a7-121">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="a24a7-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="a24a7-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="a24a7-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="a24a7-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="a24a7-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="a24a7-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="a24a7-125">Como renderizar no DirectX</span><span class="sxs-lookup"><span data-stu-id="a24a7-125">Rendering in DirectX</span></span>](../native/rendering-in-directx.md)
