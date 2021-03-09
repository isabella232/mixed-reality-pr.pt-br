---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475066"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**Namespace:** *Microsoft. MixedReality. Toolkit. WindowsMixedReality*<br>
**Tipo:** *WindowsMixedRealityUtilities*

O MRTK fornece tipos já empacotados em ambos os SDKs e do SDK do XR herdados por meio da classe **WindowsMixedRealityUtilities** .

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**Namespace:** *UnityEngine. XR. WindowsMR*<br>
**Tipo:** *WindowsMREnvironment*

A classe estática **WindowsMREnvironment** fornece acesso a vários ponteiros nativos.

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**Namespace:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

O tipo <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> permite que você obtenha acesso a objetos nativos subjacentes usando o método <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> . O que GetNativePtr retorna varia entre diferentes plataformas. No Plataforma Universal do Windows ao direcionar a realidade mista do Windows, XRDevice. GetNativePtr retorna um ponteiro (IntPtr) para a seguinte estrutura:

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

Você pode convertê-lo em HolographicFrameNativeData usando o método Marshal. PtrToStructure:

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr** é uma matriz de IntPtr empacotada como UnmanagedType. ByValArray com um comprimento igual a MaxNumberOfCameras*
