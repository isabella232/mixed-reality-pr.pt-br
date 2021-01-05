---
ms.openlocfilehash: 6b9223481ed909961dbb88d03e4b55ef68448525
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717414"
---
# <a name="426"></a>[<span data-ttu-id="cc194-101">4.26</span><span class="sxs-lookup"><span data-stu-id="cc194-101">4.26</span></span>](#tab/426)

### <a name="windows-mixed-reality"></a><span data-ttu-id="cc194-102">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="cc194-102">Windows Mixed Reality</span></span>

![Plano gráfico do evento iniciar reprodução conectado para configurar a função de gestos](../images/unreal-hand-tracking-img-09.png)

<span data-ttu-id="cc194-104">Em seguida, você deve adicionar código para assinar os seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="cc194-104">Then you should add code to subscribe to the following events:</span></span>

<span data-ttu-id="cc194-105">![Plano gráfico de espera de entrada espacial do Windows, toque e gestos de manipulação à esquerda ](../images/unreal/key-events.png)
 ![ captura de tela das opções de gesto do toque de entrada espacial do Windows no painel de detalhes](../images/unreal/key-events2.png)</span><span class="sxs-lookup"><span data-stu-id="cc194-105">![Blueprint of Windows spatial input hold, tap, and left manipulation gestures](../images/unreal/key-events.png)
![Screenshot of Windows spatial input tap gesture options in the details panel](../images/unreal/key-events2.png)</span></span>

### <a name="openxr"></a><span data-ttu-id="cc194-106">OpenXR</span><span class="sxs-lookup"><span data-stu-id="cc194-106">OpenXR</span></span>

<span data-ttu-id="cc194-107">No OpenXR, os eventos de gesto são controlados por meio do pipeline de entrada.</span><span class="sxs-lookup"><span data-stu-id="cc194-107">In OpenXR, gesture events are tracked through the input pipeline.</span></span> <span data-ttu-id="cc194-108">Usando a interação manual, o dispositivo pode reconhecer automaticamente gestos de tocar e segurar, mas não os outros.</span><span class="sxs-lookup"><span data-stu-id="cc194-108">Using hand interaction, the device can automatically recognize Tap and Hold gestures, but not the others.</span></span> <span data-ttu-id="cc194-109">Eles são nomeados como OpenXRMsftHandInteraction selecionar e segurar mapeamentos.</span><span class="sxs-lookup"><span data-stu-id="cc194-109">They are named as OpenXRMsftHandInteraction Select and Grip mappings.</span></span> <span data-ttu-id="cc194-110">Você não precisa habilitar a assinatura, deve declarar os eventos em configurações do projeto/mecanismo/entrada, assim como:</span><span class="sxs-lookup"><span data-stu-id="cc194-110">You don’t need to enable subscription, you should declare the events in Project Settings/Engine/Input, just like this:</span></span>

![Captura de tela dos mapeamentos de ação OpenXR](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[<span data-ttu-id="cc194-112">4.25</span><span class="sxs-lookup"><span data-stu-id="cc194-112">4.25</span></span>](#tab/425)

<span data-ttu-id="cc194-113">Você pode encontrar a função Blueprint na **entrada espacial de realidade mista do Windows** e a função C++ adicionando o `WindowsMixedRealitySpatialInputFunctionLibrary.h` arquivo de código de chamada.</span><span class="sxs-lookup"><span data-stu-id="cc194-113">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![Gestos de captura](../images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="cc194-115">Enumeração</span><span class="sxs-lookup"><span data-stu-id="cc194-115">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="cc194-116">Gráfico</span><span class="sxs-lookup"><span data-stu-id="cc194-116">Blueprint:</span></span>

![Tipo de gesto](../images/unreal/gesture-type.png)

<span data-ttu-id="cc194-118">C++:</span><span class="sxs-lookup"><span data-stu-id="cc194-118">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="cc194-119">Função</span><span class="sxs-lookup"><span data-stu-id="cc194-119">Function</span></span>
<span data-ttu-id="cc194-120">Você pode habilitar e desabilitar a captura de gestos com a `CaptureGestures` função.</span><span class="sxs-lookup"><span data-stu-id="cc194-120">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="cc194-121">Quando um gesto habilitado aciona eventos de entrada, a função retorna `true` se a captura do gesto foi bem-sucedida e, `false` se houver um erro.</span><span class="sxs-lookup"><span data-stu-id="cc194-121">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="cc194-122">Gráfico</span><span class="sxs-lookup"><span data-stu-id="cc194-122">Blueprint:</span></span>

![Gestos de captura BP](../images/unreal/capture-gestures-bp.png)

<span data-ttu-id="cc194-124">C++:</span><span class="sxs-lookup"><span data-stu-id="cc194-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

<span data-ttu-id="cc194-125">Veja a seguir os principais eventos, que você pode encontrar em plantas e C++: ![ principais eventos](../images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="cc194-125">The following are key events, which you can find in Blueprints and C++: ![Key Events](../images/unreal/key-events.png)</span></span>

![Principais eventos 2](../images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

