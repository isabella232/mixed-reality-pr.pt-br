---
title: Estado de entrada
description: Documentação sobre estados de entrada no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, InputState,
ms.openlocfilehash: 4c1bd115c63e25decf73c082546e75b0f276a7ef
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145250"
---
# <a name="accessing-input-state-in-mrtk"></a>Acessando o estado de entrada no MRTK

É possível consultar diretamente o estado de todas as entradas no MRTK iterando sobre os controladores anexados às fontes de entrada. O MRTK também fornece métodos de conveniência para acessar a posição e a rotação dos olhos, mãos, cabeça e controlador de movimento.

Consulte a cena InputDataExample para ver um exemplo de consulta de entrada por meio da iteração em controladores e usando a [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) classe .

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a>Exemplo: Posição de acesso, rotação de cabeça, mãos, olhos no MRTK

A classe do MRTK fornece métodos de conveniência para acessar o raio de mão, o raio da cabeça, o raio do olhar e os [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) raios do controlador de movimento.

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

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a>Exemplo: Posição de acesso, rotação de todos os controladores 6DOF ativos na cena

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
