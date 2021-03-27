---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636248"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

No momento, o MRTK não tem auxiliares para o modo de Reprojeção. Consulte uma das outras guias para obter mais informações.

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

O modo de Reprojeção é configurável com a definição de [XRDisplaySubsystem. reprojemode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) para o valor apropriado.

Por exemplo, se você estiver criando uma [experiência somente de orientação](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) com conteúdo com bloqueio de corpo rígido (por exemplo, conteúdo de vídeo de 360 graus), poderá definir explicitamente o modo de Reprojeção como orientação apenas definindo-o como [reprojemode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

O modo de Reprojeção é configurável com a definição de [HolographicSettings. reprojemode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) para o valor apropriado.

Por exemplo, se você estiver criando uma [experiência somente de orientação](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) com conteúdo com bloqueio de corpo rígido (por exemplo, conteúdo de vídeo de 360 graus), poderá definir explicitamente o modo de Reprojeção como orientação apenas definindo-o como [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).