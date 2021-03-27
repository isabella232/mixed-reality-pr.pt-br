---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636249"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

O MRTK tratará as configurações específicas da câmera automaticamente, com base na [configuração no perfil do sistema da câmera](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).

**Namespace:** *Microsoft. MixedReality. Toolkit. CameraSystem*<br>
**Tipo:** *MixedRealityCameraSystem*

Para verificar a opaca da câmera, o sistema MixedRealityCamera tem [uma `IsOpaque` Propriedade](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Namespace:** *UnityEngine. XR*<br>
**Tipo:** *XRDisplaySubsystem*

Você pode usar o código de script para determinar em tempo de execução se o headset é imersiva ou Holographic, verificando [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) na [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)em execução ativa.

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Namespace:** *UnityEngine. XR. WSA*<br>
**Tipo:** *HolographicSettings*

Você pode usar o código de script para determinar em tempo de execução se o headset é imersiva ou Holographic verificando [HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).