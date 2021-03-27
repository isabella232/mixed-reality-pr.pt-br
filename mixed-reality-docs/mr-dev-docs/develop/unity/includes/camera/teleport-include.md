---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636250"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

O MRTK fornece um [sistema teleport](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) na caixa que funciona automaticamente entre as mãos e os controladores articulados.

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

É recomendável usar a implementação de teleportabilidade do MRTK.
Se você optar por não usar o MRTK, o Unity fornecerá uma implementação de teleportação no [Kit de ferramentas de interação do XR](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).
Se você optar por implementar seu próprio, é bom ter em mente que não é possível mover a câmera diretamente. Devido ao controle do Unity da câmera para acompanhamento de cabeçalho, você precisará dar à câmera um pai na hierarquia e mover esse gameobject em vez disso. Esse é o equivalente do Playspace da MRTK.

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

É recomendável usar a implementação de teleportabilidade do MRTK.
Se você optar por implementar seu próprio, é bom ter em mente que não é possível mover a câmera diretamente. Devido ao controle do Unity da câmera para acompanhamento de cabeçalho, você precisará dar à câmera um pai na hierarquia e mover esse gameobject em vez disso. Esse é o equivalente do Playspace da MRTK.