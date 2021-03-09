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
# <a name="mixed-reality-native-interop-in-unity"></a>Interoperabilidade nativa de realidade misturada no Unity

Todo aplicativo de realidade misturada [recebe um HolographicSpace antes de começar a](../native/getting-a-holographicspace.md) receber dados da câmera e renderizar quadros. No Unity, o mecanismo cuida dessas etapas para você, manipulando objetos Holographic e atualizando internamente como parte de seu loop de processamento.

No entanto, em cenários avançados, talvez seja necessário obter acesso aos objetos nativos subjacentes, como o <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e o <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>atual.

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a>Desempacotamento de ponteiros nativos

Depois de obter o `IntPtr` de um dos métodos acima (não é necessário para MRTK), use os trechos de código a seguir para empacotá-los para objetos gerenciados.

Se você estiver usando [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), poderá construir um objeto gerenciado a partir de um ponteiro nativo usando o `FromNativePtr()` método:

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

Caso contrário, use `Marshal.GetObjectForIUnknown()` e converta para o tipo desejado:

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a>Convertendo entre sistemas de coordenadas

O Unity usa um sistema de coordenadas à esquerda, enquanto as APIs de percepção do Windows usam sistemas de coordenadas à mão. Para converter entre essas duas convenções, você pode usar os seguintes auxiliares:

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

### <a name="using-holographicframe-native-data"></a>Usando dados nativos do HolographicFrame

> [!NOTE]
> Alterar o estado dos objetos nativos recebidos por meio de HolographicFrameNativeData pode causar comportamento imprevisível e artefatos de renderização, especialmente se o Unity também tiver motivos sobre o mesmo estado.  Por exemplo, você não deve chamar HolographicFrame. UpdateCurrentPrediction ou a previsão de pose que o Unity renderiza com esse quadro estará fora de sincronia com a pose esperada pelo Windows, o que reduzirá a [estabilidade do holograma](../platform-capabilities-and-apis/hologram-stability.md).

Se você precisar de acesso a interfaces nativas para fins de processamento ou depuração, use dados do HolographicFrameNativeData em seus plug-ins nativos ou código C#.

Aqui está um exemplo de como você pode usar o HolographicFrameNativeData para obter a previsão do quadro atual para o tempo de Photon usando as extensões do XR SDK.

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

## <a name="see-also"></a>Consulte Também

* [Como usar o namespace do Windows com aplicativos Unity para HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Como renderizar no DirectX](../native/rendering-in-directx.md)
