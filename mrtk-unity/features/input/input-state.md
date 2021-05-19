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
# <a name="accessing-input-state-in-mrtk"></a><span data-ttu-id="d4d58-104">Acessando o estado de entrada no MRTK</span><span class="sxs-lookup"><span data-stu-id="d4d58-104">Accessing input state in MRTK</span></span>

<span data-ttu-id="d4d58-105">É possível consultar diretamente o estado de todas as entradas no MRTK iterando sobre os controladores anexados às fontes de entrada.</span><span class="sxs-lookup"><span data-stu-id="d4d58-105">It's possible to directly query the state of all inputs in MRTK by iterating over the controllers attached to the input sources.</span></span> <span data-ttu-id="d4d58-106">O MRTK também fornece métodos de conveniência para acessar a posição e a rotação dos olhos, mãos, cabeça e controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="d4d58-106">MRTK also provides convenience methods for accessing the position and rotation of the eyes, hands, head, and motion controller.</span></span>

<span data-ttu-id="d4d58-107">Consulte a cena InputDataExample para ver um exemplo de consulta de entrada por meio da iteração em controladores e usando a [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) classe .</span><span class="sxs-lookup"><span data-stu-id="d4d58-107">See the InputDataExample scene for an example of querying input both via iterating over controllers, and by using the [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) class.</span></span>

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a><span data-ttu-id="d4d58-108">Exemplo: Posição de acesso, rotação de cabeça, mãos, olhos no MRTK</span><span class="sxs-lookup"><span data-stu-id="d4d58-108">Example: Access position, rotation of head, hands, eyes in MRTK</span></span>

<span data-ttu-id="d4d58-109">A classe do MRTK fornece métodos de conveniência para acessar o raio de mão, o raio da cabeça, o raio do olhar e os [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) raios do controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="d4d58-109">MRTK's [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) class provides convenience methods for accessing the hand ray, head ray, eye gaze ray, and motion controller rays.</span></span>

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

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a><span data-ttu-id="d4d58-110">Exemplo: Posição de acesso, rotação de todos os controladores 6DOF ativos na cena</span><span class="sxs-lookup"><span data-stu-id="d4d58-110">Example: Access position, rotation of all 6DOF controllers active in scene</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d4d58-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="d4d58-111">See also</span></span>

- [<span data-ttu-id="d4d58-112">InputEvents</span><span class="sxs-lookup"><span data-stu-id="d4d58-112">InputEvents</span></span>](input-events.md)
- [<span data-ttu-id="d4d58-113">Ponteiros</span><span class="sxs-lookup"><span data-stu-id="d4d58-113">Pointers</span></span>](pointers.md)
- [<span data-ttu-id="d4d58-114">HandTracking</span><span class="sxs-lookup"><span data-stu-id="d4d58-114">HandTracking</span></span>](hand-tracking.md)
