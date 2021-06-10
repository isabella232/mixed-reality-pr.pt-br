---
ms.openlocfilehash: 0a4f6f1262bcaa69a8755223d738bbd88bd7a6a8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748534"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

O MRTK fornece um [sistema teleport](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) na caixa que funciona automaticamente entre as mãos e os controladores articulados.

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

É recomendável usar a implementação de teleportabilidade do MRTK.
Se você optar por não usar o MRTK, o Unity fornecerá uma implementação de teleportação no [Kit de ferramentas de interação do XR](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).
Se você optar por implementar seu próprio, é bom ter em mente que não é possível mover a câmera diretamente. Devido ao controle do Unity da câmera para acompanhamento de cabeçalho, você precisará dar à câmera um pai na hierarquia e mover esse gameobject em vez disso. Esse é o equivalente do Playspace da MRTK.

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

É recomendável usar a implementação de teleportabilidade do MRTK.
Se você optar por implementar seu próprio, é bom ter em mente que não é possível mover a câmera diretamente. Devido ao controle do Unity da câmera para acompanhamento de cabeçalho, você precisará dar à câmera um pai na hierarquia e mover esse gameobject em vez disso. Esse é o equivalente do Playspace da MRTK.