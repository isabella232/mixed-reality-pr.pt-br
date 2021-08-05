---
title: Objetos nativos de realidade misturada no Unity
description: Saiba como obter acesso a objetos nativos holográficos subjacentes no Unity usando o namespace XR.
author: vladkol
ms.author: vladkol
ms.date: 02/25/2021
ms.topic: article
keywords: unity, mixed reality, native, xvice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 63ee9c33a972cb918f141df3b4c1608a561b96dc5c37910deb77b089f7be69b8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208393"
---
# <a name="mixed-reality-native-interop-in-unity"></a>Interoperabilidade nativa da Realidade Misturada no Unity

Cada aplicativo de Realidade [Misturada obtém um HolographicSpace](../native/getting-a-holographicspace.md) antes de começar a receber dados da câmera e renderizar quadros. No Unity, o mecanismo cuida dessas etapas para você, tratando objetos Holographic e atualizando internamente como parte de seu loop de renderização.

No entanto, em cenários avançados, talvez seja necessário obter acesso aos objetos nativos subjacentes, como <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">o HolographicCamera</a> e o <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame atual.</a>

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a>Desmarcar ponteiros nativos

Depois de obter o de um dos métodos acima (não necessário para o MRTK), use os snippets de código a seguir para marshaling deles em `IntPtr` objetos gerenciados.

Se você estiver usando [Microsoft.Windows. MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), você pode construir um objeto gerenciado de um ponteiro nativo usando o `FromNativePtr()` método :

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

Caso contrário, `Marshal.GetObjectForIUnknown()` use e cast para o tipo que você deseja:

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a>Convertendo entre sistemas de coordenadas

O Unity usa um sistema de coordenadas esquerdo, enquanto as APIs Windows Perception usam sistemas de coordenadas à direita. Para converter entre essas duas convenções, você pode usar os seguintes auxiliares:

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
> Alterar o estado dos objetos nativos recebidos por meio de HolographicFrameNativeData pode causar um comportamento imprevisível e renderizar artefatos, especialmente se o Unity também tiver motivos sobre esse mesmo estado.  Por exemplo, você não deve chamar HolographicFrame.UpdateCurrentPrediction ou a previsão de pose que o Unity renderiza com esse quadro estará fora de sincronia com a pose que Windows está esperando, o que reduzirá a estabilidade do [holograma.](../platform-capabilities-and-apis/hologram-stability.md)

Se você precisar de acesso a interfaces nativas para renderização ou depuração, use dados do HolographicFrameNativeData em seus plug-ins nativos ou código C#.

Aqui está um exemplo de como você pode usar HolographicFrameNativeData para obter a previsão do quadro atual para o tempo de foton usando as extensões do SDK do XR.

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
