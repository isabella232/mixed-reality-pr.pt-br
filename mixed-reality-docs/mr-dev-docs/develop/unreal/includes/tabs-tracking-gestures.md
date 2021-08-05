---
ms.openlocfilehash: fa21b1a5c3c89cf3c1c63c7ed8ebbdc3d8547661443853987ee3713e50c50e5c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187181"
---
# <a name="426"></a>[4.26](#tab/426)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

![Plano gráfico do evento iniciar reprodução conectado para configurar a função de gestos](../images/unreal-hand-tracking-img-09.png)

Em seguida, você deve adicionar código para assinar os seguintes eventos:

![plano gráfico de Windows contenção de entrada espacial, toque e gestos de manipulação à esquerda ](../images/unreal/key-events.png)
 ![ captura de tela de Windows opções de gesto toque de entrada espacial no painel de detalhes](../images/unreal/key-events2.png)

### <a name="openxr"></a>OpenXR

No OpenXR, os eventos de gesto são controlados por meio do pipeline de entrada. Usando a interação manual, o dispositivo pode reconhecer automaticamente gestos de tocar e segurar, mas não os outros. Eles são nomeados como OpenXRMsftHandInteraction selecionar e segurar mapeamentos. você não precisa habilitar a assinatura, você deve declarar os eventos em Project Configurações/Engine/Input, assim:

![Captura de tela dos mapeamentos de ação OpenXR](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[4.25](#tab/425)

você pode encontrar a função Blueprint em em **Windows Mixed Reality entrada espacial** e a função C++ adicionando o `WindowsMixedRealitySpatialInputFunctionLibrary.h` arquivo de código de chamada.

![Gestos de captura](../images/unreal/capture-gestures.png)

### <a name="enum"></a>Enumeração
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Gráfico

![Tipo de gesto](../images/unreal/gesture-type.png)

C++:
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>Função
Você pode habilitar e desabilitar a captura de gestos com a `CaptureGestures` função. Quando um gesto habilitado aciona eventos de entrada, a função retorna `true` se a captura do gesto foi bem-sucedida e, `false` se houver um erro.

Gráfico

![Gestos de captura BP](../images/unreal/capture-gestures-bp.png)

C++:
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

Veja a seguir os principais eventos, que você pode encontrar em plantas e C++: ![ principais eventos](../images/unreal/key-events.png)

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

