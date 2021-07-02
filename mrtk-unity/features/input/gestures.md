---
title: Gestos
description: Docummentation em gestos e seus eventos em MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, gestos,
ms.openlocfilehash: 7bbc97ab5e23a69356d523c463aa37c013d70337
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176884"
---
# <a name="gestures"></a>Gestos

Os gestos são eventos de entrada com base em mãos humanas. Há dois tipos de dispositivos que geram eventos de entrada de gesto em MRTK:

- Windows Mixed Reality dispositivos como o HoloLens. Isso descreve os movimentos de pinçagem ("toque de ar") e gestos de toque e espera.

  para obter mais informações sobre gestos de HoloLens, consulte a [documentação de gestos de Windows Mixed Reality](/windows/mixed-reality/gestures).

  [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)encapsula o [Unity XR. WSA. Input. GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) para consumir eventos de gesto do Unity de dispositivos HoloLens.

- Dispositivos de tela sensível ao toque.

  [`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) encapsula a [classe Unity Touch](https://docs.unity3d.com/ScriptReference/Touch.html) que dá suporte a telas de toque físicas.

ambas as fontes de entrada usam o _Configurações_ perfil de gesto para converter eventos de toque e de gesto do Unity, respectivamente, em [ações de entrada](input-actions.md)do MRTK. esse perfil pode ser encontrado no perfil de _Configurações do sistema de entrada_ .

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a>Eventos de gesto

Eventos de gesto são recebidos pela implementação de uma das interfaces de manipulador de gestos: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) ou [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (consulte a tabela de [manipuladores de eventos](input-events.md)).

Consulte [exemplo de cena](#example-scene) para obter um exemplo de implementação de um manipulador de eventos de gesto.

Ao implementar a versão genérica, os eventos *OnGestureCompleted* e *OnGestureUpdated* podem receber dados digitados dos seguintes tipos:

- `Vector2` -gesto de posição 2D. Produzido por telas de toque para informá-las [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .
- `Vector3` -gesto de posição 3D. produzido por HoloLens para informar:
  - [`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) de um evento de manipulação
  - [`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) de um evento de navegação
- `Quaternion` -gesto de rotação 3D. Disponível para fontes de entrada personalizadas, mas que não são produzidas atualmente por nenhum dos existentes.
- `MixedRealityPose` -Gesto de rotação/posição 3D combinado. Disponível para fontes de entrada personalizadas, mas que não são produzidas atualmente por nenhum dos existentes.

## <a name="order-of-events"></a>Ordem dos eventos

Há duas cadeias de eventos principais, dependendo da entrada do usuário:

- "Reter":
    1. Toque em espera:
        - iniciar _manipulação_
    1. Pressione o toque para além do [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):
        - iniciar _suspensão_
    1. Toque de versão:
        - _suspensão_ completa
        - _manipulação_ completa

- "Mover":
    1. Toque em espera:
        - iniciar _manipulação_
    1. Pressione o toque para além do [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):
        - iniciar _suspensão_
    1. Mover mão para além de [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):
        - cancelar _retenção_
        - iniciar _navegação_
    1. Toque de versão:
        - _manipulação_ completa
        - _navegação_ completa

## <a name="example-scene"></a>Cena de exemplo

A cena **HandInteractionGestureEventsExample** (ativos/MRTK/exemplos/demos/HandTracking/cenas) mostra como usar o resultado do ponteiro para gerar um objeto no local de visita.

O `GestureTester` script (ativos/MRTK/exemplos/demos/HandTracking/script) é uma implementação de exemplo para Visualizar eventos de gestos via Gameobjects. As funções de manipulador alteram a cor dos objetos de indicador e exibem o último evento gravado em objetos de texto na cena.
