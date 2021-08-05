---
ms.openlocfilehash: 73aba70497323d406b5138eca9c7d2054b8d8b3cea6e82ef67e962a21876c280
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212195"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

O MRTK manipulará configurações específicas da câmera automaticamente, com base na [configuração no perfil do sistema de câmera.](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)

**Namespace:** *Microsoft.MixedReality.Toolkit. CameraSystem*<br>
**Tipo:** *MixedRealityCameraSystem*

Para verificar a opacidade da câmera, o sistema MixedRealityCamera tem [uma `IsOpaque` propriedade](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *XRDisplaySubsystem*

Você pode usar o código de script para determinar em runtime se o headset é imersivo ou holográfico verificando [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) no [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)em execução ativamente.

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipo:** *HolographicSettings*

Você pode usar o código de script para determinar em runtime se o headset é imersivo ou holográfico verificando [HolographicSettings.IsDisplayOpaque.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)