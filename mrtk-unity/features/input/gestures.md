---
title: Gestos
description: Docummentação em gestos e seus eventos no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Gestos,
ms.openlocfilehash: db6be5845c11efd5bfb199db9c53c867ea315f65bff0a799cd6bf63b9c50a3d1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209156"
---
# <a name="gestures"></a>Gestos

Gestos são eventos de entrada baseados em mãos humanas. Há dois tipos de dispositivos que adem eventos de entrada de gesto no MRTK:

- Windows Mixed Reality dispositivos como HoloLens. Isso descreve movimentos de pinçar ("Toque no Ar") e gestos de toque e segurar.

  Para obter mais informações sobre HoloLens gestos, consulte a [documentação Windows Mixed Reality gestos do .](/windows/mixed-reality/gestures)

  [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)quebra o [XR do Unity. Wsa. Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) para consumir eventos de gesto do Unity de HoloLens dispositivos.

- Dispositivos de tela de toque.

  [`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) envolve a classe [Touch do Unity que](https://docs.unity3d.com/ScriptReference/Touch.html) dá suporte a telas de toque físicas.

Ambas as fontes de entrada usam o perfil _de_ Configurações gesto para converter os eventos de Toque e Gesto do Unity, respectivamente, nas Ações de Entrada [do](input-actions.md)MRTK. Esse perfil pode ser encontrado no perfil sistema _de Configurações_ entrada.

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a>Eventos de gesto

Os eventos de gesto são recebidos pela implementação de uma das interfaces do manipulador de gestos: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) ou (consulte a tabela de [manipuladores de eventos](input-events.md)).

Consulte [Cena de exemplo](#example-scene) para ver um exemplo de implementação de um manipulador de eventos de gestos.

Ao implementar a versão genérica, os *eventos OnGestureCompleted* e *OnGestureUpdated* podem receber dados digitados dos seguintes tipos:

- `Vector2` - Gesto de posição 2D. Produzido por telas de toque para informar sobre seu [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .
- `Vector3` - Gesto de posição 3D. Produzido por HoloLens para informar:
  - [`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) de um evento de manipulação
  - [`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) de um evento de navegação
- `Quaternion` - Gesto de rotação 3D. Disponível para fontes de entrada personalizadas, mas não produzidas atualmente por nenhuma das fontes existentes.
- `MixedRealityPose` – Gesto de posição/rotação 3D combinado. Disponível para fontes de entrada personalizadas, mas não produzidas atualmente por nenhuma das fontes existentes.

## <a name="order-of-events"></a>Ordem dos eventos

Há duas cadeias de eventos principais, dependendo da entrada do usuário:

- "Hold":
    1. Mantenha o toque:
        - Manipulação _de início_
    1. Mantenha o toque [além de HoldStartDuration:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)
        - start _Hold_
    1. Toque de versão:
        - concluir _a espera_
        - manipulação _completa_

- "Mover":
    1. Mantenha o toque:
        - Manipulação _de início_
    1. Mantenha o toque [além de HoldStartDuration:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)
        - start _Hold_
    1. Mova a mão para [além de NavigationStartThreshold:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)
        - cancelar _espera_
        - Iniciar _navegação_
    1. Toque de versão:
        - manipulação _completa_
        - navegação _completa_

## <a name="example-scene"></a>Cena de exemplo

A **cena HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) mostra como usar o ponteiro Result para gerar um objeto no local de ocorrência.

O script (Ativos/MRTK/Exemplos/Demonstrações/HandTracking/Script) é um exemplo de implementação para visualizar eventos de gesto por `GestureTester` meio de GameObjects. As funções de manipulador alteram a cor dos objetos indicadores e exibem o último evento gravado em objetos de texto na cena.
