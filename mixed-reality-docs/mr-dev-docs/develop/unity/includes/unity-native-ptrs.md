---
ms.openlocfilehash: c3775dc73f41b822c233d8fc4ec62459e789b89f
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122263599"
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

# <a name="windows-xr-plugin"></a>[Windows Plug-in XR](#tab/xr)

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

O tipo <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> permite que você obtenha acesso a objetos nativos subjacentes usando o método <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> . O que GetNativePtr retorna varia entre diferentes plataformas. na Plataforma Universal do Windows ao direcionar Windows Mixed Reality, XRDevice. GetNativePtr retorna um ponteiro (IntPtr) para a seguinte estrutura:

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
