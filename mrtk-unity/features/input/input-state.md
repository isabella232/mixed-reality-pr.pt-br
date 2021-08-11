---
title: Estado de entrada
description: Documentação sobre Estados de entrada no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, inputstate,
ms.openlocfilehash: 7d5e008ae3e43d227b90a563dd74e65a89527bd7ddf1720e26577042ce0d545f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228356"
---
# <a name="accessing-input-state-in-mrtk"></a>Acessando o estado de entrada no MRTK

É possível consultar diretamente o estado de todas as entradas em MRTK Iterando sobre os controladores anexados às fontes de entrada. O MRTK também fornece métodos de conveniência para acessar a posição e a rotação dos olhos, das mãos, da cabeça e do controlador de movimento.

Consulte a cena InputDataExample para obter um exemplo de como consultar a entrada por meio da iteração sobre controladores e usando a [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) classe.

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a>Exemplo: posição de acesso, rotação de cabeça, mãos, olhos em MRTK

[`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils)A classe de MRTK fornece métodos de conveniência para acessar o conjunto de raio, Head Ray, olho olhar Ray e raios do controlador de movimento.

```c#
// Get the head ray
var headRay = InputRayUtils.GetHeadGazeRay();

// Get the right hand ray
Ray rightHandRay;
if(InputRayUtils.TryGetHandRay(Handedness.right, rightHandRay))
{
    // Right hand ray is available
}
else
{
    // Right hand ray is not available
}
```

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a>Exemplo: posição de acesso, rotação de todos os controladores 6DOF ativas na cena

```c#
foreach(var controller in CoreServices.InputSystem.DetectedControllers)
{
    // Interactions for a controller is the list of inputs that this controller exposes
    foreach(MixedRealityInteractionMapping inputMapping in controller.Interactions)
    {
        // 6DOF controllers support the "SpatialPointer" type (pointing direction)
        // or "GripPointer" type (direction of the 6DOF controller)
        if (inputMapping.InputType == DeviceInputType.SpatialPointer)
        {
            Debug.Log("spatial pointer PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial pointer RotationData: " + inputMapping.RotationData);
        }

        if (inputMapping.InputType == DeviceInputType.SpatialGrip)
        {
            Debug.Log("spatial grip PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial grip RotationData: " + inputMapping.RotationData);
        }
    }
}
```

## <a name="see-also"></a>Confira também

- [InputEvents](input-events.md)
- [Ponteiros](pointers.md)
- [HandTracking](hand-tracking.md)
