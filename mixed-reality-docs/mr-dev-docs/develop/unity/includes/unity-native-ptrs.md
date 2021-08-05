---
ms.openlocfilehash: 78296dd4e6667c34926c954774547b21a223c5f4b6635476c51046c7ca22cdc3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208392"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**Namespace:** *Microsoft.MixedReality.Toolkit. WindowsMixedReality*<br>
**Tipo:** *WindowsMixedRealityUtilities*

O MRTK fornece tipos já marshallados no WSA herdado e no SDK do XR por meio da **classe WindowsMixedRealityUtilities.**

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**Namespace:** *UnityEngine.XR.WindowsMR*<br>
**Tipo:** *WindowsMREnvironment*

A classe **estática WindowsMREnvironment** fornece acesso a vários ponteiros nativos.

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

O <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**tipo XRDevice**</a> permite que você tenha acesso a objetos nativos subjacentes usando o <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">método GetNativePtr.</a> O que GetNativePtr retorna varia entre diferentes plataformas. Na Plataforma de Windows Universal ao direcionar Windows Mixed Reality, XRDevice.GetNativePtr retorna um ponteiro (IntPtr) para a seguinte estrutura:

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

Você pode convertê-lo em HolographicFrameNativeData usando o método Marshal.PtrToStructure:

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr** é uma matriz de IntPtr marshaled como UnmanagedType.ByValArray com um comprimento igual a MaxNumberOfCameras*
