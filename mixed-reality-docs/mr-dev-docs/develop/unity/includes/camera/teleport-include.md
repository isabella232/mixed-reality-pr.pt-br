---
ms.openlocfilehash: 879d8083f832e716389e4b4598aa0fffe6930ff1c06d7a07fe9e4dacc98e7937
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212197"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

O MRTK fornece um sistema in-box [que](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) funciona automaticamente entre mãos e controladores articulados.

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

É recomendável usar a implementação de teletransporte do MRTK.
Se você optar por não usar o MRTK, o Unity fornece uma implementação de Toolkit [.](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)
Se você optar por implementar sua própria, é bom ter em mente que não é possível mover a câmera diretamente. Devido ao controle do Unity da câmera para acompanhamento de cabeça, você precisará dar à câmera um pai na hierarquia e mover esse GameObject em vez disso. Esse é o equivalente ao Playspace do MRTK.

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

É recomendável usar a implementação de teletransporte do MRTK.
Se você optar por implementar sua própria, é bom ter em mente que não é possível mover a câmera diretamente. Devido ao controle do Unity da câmera para acompanhamento de cabeça, você precisará dar à câmera um pai na hierarquia e mover esse GameObject em vez disso. Esse é o equivalente ao Playspace do MRTK.