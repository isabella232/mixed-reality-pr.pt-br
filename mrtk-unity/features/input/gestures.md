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
# <a name="gestures"></a><span data-ttu-id="c82a6-104">Gestos</span><span class="sxs-lookup"><span data-stu-id="c82a6-104">Gestures</span></span>

<span data-ttu-id="c82a6-105">Os gestos são eventos de entrada com base em mãos humanas.</span><span class="sxs-lookup"><span data-stu-id="c82a6-105">Gestures are input events based on human hands.</span></span> <span data-ttu-id="c82a6-106">Há dois tipos de dispositivos que geram eventos de entrada de gesto em MRTK:</span><span class="sxs-lookup"><span data-stu-id="c82a6-106">There are two types of devices that raise gesture input events in MRTK:</span></span>

- <span data-ttu-id="c82a6-107">Windows Mixed Reality dispositivos como o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c82a6-107">Windows Mixed Reality devices such as HoloLens.</span></span> <span data-ttu-id="c82a6-108">Isso descreve os movimentos de pinçagem ("toque de ar") e gestos de toque e espera.</span><span class="sxs-lookup"><span data-stu-id="c82a6-108">This describes pinching motions ("Air Tap") and tap-and-hold gestures.</span></span>

  <span data-ttu-id="c82a6-109">para obter mais informações sobre gestos de HoloLens, consulte a [documentação de gestos de Windows Mixed Reality](/windows/mixed-reality/gestures).</span><span class="sxs-lookup"><span data-stu-id="c82a6-109">For more information on HoloLens gestures see the [Windows Mixed Reality Gestures documentation](/windows/mixed-reality/gestures).</span></span>

  <span data-ttu-id="c82a6-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)encapsula o [Unity XR. WSA. Input. GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) para consumir eventos de gesto do Unity de dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c82a6-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) wraps the [Unity XR.WSA.Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) to consume Unity's gesture events from HoloLens devices.</span></span>

- <span data-ttu-id="c82a6-111">Dispositivos de tela sensível ao toque.</span><span class="sxs-lookup"><span data-stu-id="c82a6-111">Touch screen devices.</span></span>

  <span data-ttu-id="c82a6-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) encapsula a [classe Unity Touch](https://docs.unity3d.com/ScriptReference/Touch.html) que dá suporte a telas de toque físicas.</span><span class="sxs-lookup"><span data-stu-id="c82a6-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) wraps the [Unity Touch class](https://docs.unity3d.com/ScriptReference/Touch.html) that supports physical touch screens.</span></span>

<span data-ttu-id="c82a6-113">ambas as fontes de entrada usam o _Configurações_ perfil de gesto para converter eventos de toque e de gesto do Unity, respectivamente, em [ações de entrada](input-actions.md)do MRTK.</span><span class="sxs-lookup"><span data-stu-id="c82a6-113">Both of these input sources use the _Gesture Settings_ profile to translate Unity's Touch and Gesture events respectively into MRTK's [Input Actions](input-actions.md).</span></span> <span data-ttu-id="c82a6-114">esse perfil pode ser encontrado no perfil de _Configurações do sistema de entrada_ .</span><span class="sxs-lookup"><span data-stu-id="c82a6-114">This profile can be found under the _Input System Settings_ profile.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a><span data-ttu-id="c82a6-115">Eventos de gesto</span><span class="sxs-lookup"><span data-stu-id="c82a6-115">Gesture events</span></span>

<span data-ttu-id="c82a6-116">Eventos de gesto são recebidos pela implementação de uma das interfaces de manipulador de gestos: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) ou [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (consulte a tabela de [manipuladores de eventos](input-events.md)).</span><span class="sxs-lookup"><span data-stu-id="c82a6-116">Gesture events are received by implementing one of the gesture handler interfaces: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) or [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (see table of [event handlers](input-events.md)).</span></span>

<span data-ttu-id="c82a6-117">Consulte [exemplo de cena](#example-scene) para obter um exemplo de implementação de um manipulador de eventos de gesto.</span><span class="sxs-lookup"><span data-stu-id="c82a6-117">See [Example Scene](#example-scene) for an example implementation of a gesture event handler.</span></span>

<span data-ttu-id="c82a6-118">Ao implementar a versão genérica, os eventos *OnGestureCompleted* e *OnGestureUpdated* podem receber dados digitados dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="c82a6-118">When implementing the generic version, the *OnGestureCompleted* and *OnGestureUpdated* events can receive typed data of the following types:</span></span>

- <span data-ttu-id="c82a6-119">`Vector2` -gesto de posição 2D.</span><span class="sxs-lookup"><span data-stu-id="c82a6-119">`Vector2` - 2D position gesture.</span></span> <span data-ttu-id="c82a6-120">Produzido por telas de toque para informá-las [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .</span><span class="sxs-lookup"><span data-stu-id="c82a6-120">Produced by touch screens to inform of their [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html).</span></span>
- <span data-ttu-id="c82a6-121">`Vector3` -gesto de posição 3D.</span><span class="sxs-lookup"><span data-stu-id="c82a6-121">`Vector3` - 3D position gesture.</span></span> <span data-ttu-id="c82a6-122">produzido por HoloLens para informar:</span><span class="sxs-lookup"><span data-stu-id="c82a6-122">Produced by HoloLens to inform of:</span></span>
  - <span data-ttu-id="c82a6-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) de um evento de manipulação</span><span class="sxs-lookup"><span data-stu-id="c82a6-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) of a manipulation event</span></span>
  - <span data-ttu-id="c82a6-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) de um evento de navegação</span><span class="sxs-lookup"><span data-stu-id="c82a6-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) of a navigation event</span></span>
- <span data-ttu-id="c82a6-125">`Quaternion` -gesto de rotação 3D.</span><span class="sxs-lookup"><span data-stu-id="c82a6-125">`Quaternion` - 3D rotation gesture.</span></span> <span data-ttu-id="c82a6-126">Disponível para fontes de entrada personalizadas, mas que não são produzidas atualmente por nenhum dos existentes.</span><span class="sxs-lookup"><span data-stu-id="c82a6-126">Available to custom input sources but not currently produced by any of the existing ones.</span></span>
- <span data-ttu-id="c82a6-127">`MixedRealityPose` -Gesto de rotação/posição 3D combinado.</span><span class="sxs-lookup"><span data-stu-id="c82a6-127">`MixedRealityPose` - Combined 3D position/rotation gesture.</span></span> <span data-ttu-id="c82a6-128">Disponível para fontes de entrada personalizadas, mas que não são produzidas atualmente por nenhum dos existentes.</span><span class="sxs-lookup"><span data-stu-id="c82a6-128">Available to custom input sources but not currently produced by any of the existing ones.</span></span>

## <a name="order-of-events"></a><span data-ttu-id="c82a6-129">Ordem dos eventos</span><span class="sxs-lookup"><span data-stu-id="c82a6-129">Order of events</span></span>

<span data-ttu-id="c82a6-130">Há duas cadeias de eventos principais, dependendo da entrada do usuário:</span><span class="sxs-lookup"><span data-stu-id="c82a6-130">There are two principal chains of events, depending on user input:</span></span>

- <span data-ttu-id="c82a6-131">"Reter":</span><span class="sxs-lookup"><span data-stu-id="c82a6-131">"Hold":</span></span>
    1. <span data-ttu-id="c82a6-132">Toque em espera:</span><span class="sxs-lookup"><span data-stu-id="c82a6-132">Hold tap:</span></span>
        - <span data-ttu-id="c82a6-133">iniciar _manipulação_</span><span class="sxs-lookup"><span data-stu-id="c82a6-133">start _Manipulation_</span></span>
    1. <span data-ttu-id="c82a6-134">Pressione o toque para além do [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span><span class="sxs-lookup"><span data-stu-id="c82a6-134">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="c82a6-135">iniciar _suspensão_</span><span class="sxs-lookup"><span data-stu-id="c82a6-135">start _Hold_</span></span>
    1. <span data-ttu-id="c82a6-136">Toque de versão:</span><span class="sxs-lookup"><span data-stu-id="c82a6-136">Release tap:</span></span>
        - <span data-ttu-id="c82a6-137">_suspensão_ completa</span><span class="sxs-lookup"><span data-stu-id="c82a6-137">complete _Hold_</span></span>
        - <span data-ttu-id="c82a6-138">_manipulação_ completa</span><span class="sxs-lookup"><span data-stu-id="c82a6-138">complete _Manipulation_</span></span>

- <span data-ttu-id="c82a6-139">"Mover":</span><span class="sxs-lookup"><span data-stu-id="c82a6-139">"Move":</span></span>
    1. <span data-ttu-id="c82a6-140">Toque em espera:</span><span class="sxs-lookup"><span data-stu-id="c82a6-140">Hold tap:</span></span>
        - <span data-ttu-id="c82a6-141">iniciar _manipulação_</span><span class="sxs-lookup"><span data-stu-id="c82a6-141">start _Manipulation_</span></span>
    1. <span data-ttu-id="c82a6-142">Pressione o toque para além do [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span><span class="sxs-lookup"><span data-stu-id="c82a6-142">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="c82a6-143">iniciar _suspensão_</span><span class="sxs-lookup"><span data-stu-id="c82a6-143">start _Hold_</span></span>
    1. <span data-ttu-id="c82a6-144">Mover mão para além de [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span><span class="sxs-lookup"><span data-stu-id="c82a6-144">Move hand beyond [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span></span>
        - <span data-ttu-id="c82a6-145">cancelar _retenção_</span><span class="sxs-lookup"><span data-stu-id="c82a6-145">cancel _Hold_</span></span>
        - <span data-ttu-id="c82a6-146">iniciar _navegação_</span><span class="sxs-lookup"><span data-stu-id="c82a6-146">start _Navigation_</span></span>
    1. <span data-ttu-id="c82a6-147">Toque de versão:</span><span class="sxs-lookup"><span data-stu-id="c82a6-147">Release tap:</span></span>
        - <span data-ttu-id="c82a6-148">_manipulação_ completa</span><span class="sxs-lookup"><span data-stu-id="c82a6-148">complete _Manipulation_</span></span>
        - <span data-ttu-id="c82a6-149">_navegação_ completa</span><span class="sxs-lookup"><span data-stu-id="c82a6-149">complete _Navigation_</span></span>

## <a name="example-scene"></a><span data-ttu-id="c82a6-150">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="c82a6-150">Example scene</span></span>

<span data-ttu-id="c82a6-151">A cena **HandInteractionGestureEventsExample** (ativos/MRTK/exemplos/demos/HandTracking/cenas) mostra como usar o resultado do ponteiro para gerar um objeto no local de visita.</span><span class="sxs-lookup"><span data-stu-id="c82a6-151">The **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) scene shows how to use the pointer Result to spawn an object at the hit location.</span></span>

<span data-ttu-id="c82a6-152">O `GestureTester` script (ativos/MRTK/exemplos/demos/HandTracking/script) é uma implementação de exemplo para Visualizar eventos de gestos via Gameobjects.</span><span class="sxs-lookup"><span data-stu-id="c82a6-152">The `GestureTester` (Assets/MRTK/Examples/Demos/HandTracking/Script) script is an example implementation to visualize gesture events via GameObjects.</span></span> <span data-ttu-id="c82a6-153">As funções de manipulador alteram a cor dos objetos de indicador e exibem o último evento gravado em objetos de texto na cena.</span><span class="sxs-lookup"><span data-stu-id="c82a6-153">The handler functions change the color of indicator objects and display the last recorded event in text objects in the scene.</span></span>
