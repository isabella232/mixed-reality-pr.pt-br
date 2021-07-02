---
title: Eventos de entrada
description: Documentação de InputEvents no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Eventos,
ms.openlocfilehash: c8871aa575e2aa4507e9dbbdcc8bdf0fc0604633
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176783"
---
# <a name="input-events"></a><span data-ttu-id="a5439-104">Eventos de entrada</span><span class="sxs-lookup"><span data-stu-id="a5439-104">Input events</span></span>

<span data-ttu-id="a5439-105">A lista a seguir descreve todas as interfaces de evento de entrada disponíveis a serem implementadas por um componente MonoBehaviour personalizado.</span><span class="sxs-lookup"><span data-stu-id="a5439-105">The list below outlines all available input event interfaces to be implemented by a custom MonoBehaviour component.</span></span> <span data-ttu-id="a5439-106">Essas interfaces serão chamadas pelo sistema de entrada do MRTK para lidar com a lógica personalizada do aplicativo com base nas interações de entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="a5439-106">These interfaces will be called by the MRTK input system to handle custom app logic based on user input interactions.</span></span> <span data-ttu-id="a5439-107">[Os eventos de entrada de](pointers.md#pointer-event-interfaces) ponteiro são tratados de maneira ligeiramente diferente dos tipos de evento de entrada padrão abaixo.</span><span class="sxs-lookup"><span data-stu-id="a5439-107">[Pointer input events](pointers.md#pointer-event-interfaces) are handled slightly differently than the standard input event types below.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5439-108">Por padrão, um script receberá eventos de entrada somente se for o GameObject em foco por um ponteiro ou pai de um GameObject em foco.</span><span class="sxs-lookup"><span data-stu-id="a5439-108">By default, a script will receive input events only if it is the GameObject in focus by a pointer or parent of a GameObject in focus.</span></span>

| <span data-ttu-id="a5439-109">Manipulador</span><span class="sxs-lookup"><span data-stu-id="a5439-109">Handler</span></span> | <span data-ttu-id="a5439-110">Eventos</span><span class="sxs-lookup"><span data-stu-id="a5439-110">Events</span></span> | <span data-ttu-id="a5439-111">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="a5439-111">Description</span></span> |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | <span data-ttu-id="a5439-112">Origem detectada/perdida</span><span class="sxs-lookup"><span data-stu-id="a5439-112">Source Detected / Lost</span></span> | <span data-ttu-id="a5439-113">Gerado quando uma fonte de entrada é detectada/perdida, como quando uma mão articulada é detectada ou perdida.</span><span class="sxs-lookup"><span data-stu-id="a5439-113">Raised when an input source is detected/lost, like when an articulated hand is detected or lost track of.</span></span> |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | <span data-ttu-id="a5439-114">Pose de origem alterada</span><span class="sxs-lookup"><span data-stu-id="a5439-114">Source Pose Changed</span></span> | <span data-ttu-id="a5439-115">Gerado nas alterações de pose de origem.</span><span class="sxs-lookup"><span data-stu-id="a5439-115">Raised on source pose changes.</span></span> <span data-ttu-id="a5439-116">A pose de origem representa a pose geral da fonte de entrada.</span><span class="sxs-lookup"><span data-stu-id="a5439-116">The source pose represents the general pose of the input source.</span></span> <span data-ttu-id="a5439-117">Poses específicas, como a posição da mão ou do ponteiro em um controlador do DOF de seis, podem ser obtidas por meio de `IMixedRealityInputHandler<MixedRealityPose>` .</span><span class="sxs-lookup"><span data-stu-id="a5439-117">Specific poses, like the grip or pointer pose in a six DOF controller, can be obtained via `IMixedRealityInputHandler<MixedRealityPose>`.</span></span> |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | <span data-ttu-id="a5439-118">Entrada para baixo/para cima</span><span class="sxs-lookup"><span data-stu-id="a5439-118">Input Down / Up</span></span> | <span data-ttu-id="a5439-119">Gerado em alterações em entradas binárias, como botões.</span><span class="sxs-lookup"><span data-stu-id="a5439-119">Raised on changes to binary inputs like buttons.</span></span> |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | <span data-ttu-id="a5439-120">Entrada alterada</span><span class="sxs-lookup"><span data-stu-id="a5439-120">Input Changed</span></span> | <span data-ttu-id="a5439-121">Gerado em alterações em entradas do tipo determinado.</span><span class="sxs-lookup"><span data-stu-id="a5439-121">Raised on changes to inputs of the given type.</span></span> <span data-ttu-id="a5439-122">**T** pode usar os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="a5439-122">**T** can take the following values:</span></span> <br/> <span data-ttu-id="a5439-123">- *float* (por exemplo, retorna gatilho análogo)</span><span class="sxs-lookup"><span data-stu-id="a5439-123">- *float* (e.g returns analog trigger)</span></span><br/> <span data-ttu-id="a5439-124">- *Vector2* (por exemplo, retorna a direção do thumbstick do gamepad)</span><span class="sxs-lookup"><span data-stu-id="a5439-124">- *Vector2* (e.g returns gamepad thumbstick direction)</span></span> <br/> <span data-ttu-id="a5439-125">- *Vector3* (por exemplo, posição de retorno do dispositivo rastreado)</span><span class="sxs-lookup"><span data-stu-id="a5439-125">- *Vector3* (e.g return position of tracked device)</span></span> <br/> <span data-ttu-id="a5439-126">- *Quatternion* (por exemplo, retorna a orientação do dispositivo rastreado)</span><span class="sxs-lookup"><span data-stu-id="a5439-126">- *Quaternion* (e.g returns orientation of tracked device)</span></span><br/> <span data-ttu-id="a5439-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (por exemplo, retorna o dispositivo totalmente rastreado)</span><span class="sxs-lookup"><span data-stu-id="a5439-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (e.g. returns fully tracked device)</span></span> |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | <span data-ttu-id="a5439-128">Palavra-chave speech recognized</span><span class="sxs-lookup"><span data-stu-id="a5439-128">Speech Keyword Recognized</span></span> | <span data-ttu-id="a5439-129">Gerado no reconhecimento de uma das palavras-chave configuradas no Perfil *de Comandos de Fala*.</span><span class="sxs-lookup"><span data-stu-id="a5439-129">Raised on recognition of one of the keywords configured in the *Speech Commands Profile*.</span></span> |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | <span data-ttu-id="a5439-130">Ditado</span><span class="sxs-lookup"><span data-stu-id="a5439-130">Dictation</span></span><br/> <span data-ttu-id="a5439-131">Hipótese</span><span class="sxs-lookup"><span data-stu-id="a5439-131">Hypothesis</span></span> <br/> <span data-ttu-id="a5439-132">Resultado</span><span class="sxs-lookup"><span data-stu-id="a5439-132">Result</span></span> <br/> <span data-ttu-id="a5439-133">Concluir</span><span class="sxs-lookup"><span data-stu-id="a5439-133">Complete</span></span> <br/> <span data-ttu-id="a5439-134">Erro</span><span class="sxs-lookup"><span data-stu-id="a5439-134">Error</span></span> | <span data-ttu-id="a5439-135">Gerado por sistemas de ditado para relatar os resultados de uma sessão de ditado.</span><span class="sxs-lookup"><span data-stu-id="a5439-135">Raised by dictation systems to report the results of a dictation session.</span></span> |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | <span data-ttu-id="a5439-136">Eventos de gesto em:</span><span class="sxs-lookup"><span data-stu-id="a5439-136">Gesture events on:</span></span> <br/> <span data-ttu-id="a5439-137">Iniciado</span><span class="sxs-lookup"><span data-stu-id="a5439-137">Started</span></span> <br/> <span data-ttu-id="a5439-138">Atualizado</span><span class="sxs-lookup"><span data-stu-id="a5439-138">Updated</span></span> <br/> <span data-ttu-id="a5439-139">Concluído</span><span class="sxs-lookup"><span data-stu-id="a5439-139">Completed</span></span> <br/> <span data-ttu-id="a5439-140">Canceled</span><span class="sxs-lookup"><span data-stu-id="a5439-140">Canceled</span></span> | <span data-ttu-id="a5439-141">Gerado na detecção de gestos.</span><span class="sxs-lookup"><span data-stu-id="a5439-141">Raised on gesture detection.</span></span> |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | <span data-ttu-id="a5439-142">Gesto atualizado/concluído</span><span class="sxs-lookup"><span data-stu-id="a5439-142">Gesture Updated / Completed</span></span> | <span data-ttu-id="a5439-143">Gerado na detecção de gestos que contêm dados adicionais do tipo determinado.</span><span class="sxs-lookup"><span data-stu-id="a5439-143">Raised on detection of gestures containing additional data of the given type.</span></span> <span data-ttu-id="a5439-144">Consulte [**eventos de gesto**](gestures.md#gesture-events) para obter detalhes sobre possíveis valores para **T**.</span><span class="sxs-lookup"><span data-stu-id="a5439-144">See [**gesture events**](gestures.md#gesture-events) for details on possible values for **T**.</span></span> |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | <span data-ttu-id="a5439-145">Junções de mão atualizadas</span><span class="sxs-lookup"><span data-stu-id="a5439-145">Hand Joints Updated</span></span> | <span data-ttu-id="a5439-146">Gerado por controladores de mão articulados quando as junções de mão são atualizadas.</span><span class="sxs-lookup"><span data-stu-id="a5439-146">Raised by articulated hand controllers when hand joints are updated.</span></span> |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | <span data-ttu-id="a5439-147">Malha manual atualizada</span><span class="sxs-lookup"><span data-stu-id="a5439-147">Hand Mesh Updated</span></span> | <span data-ttu-id="a5439-148">Gerado por controladores de mão articulados quando uma malha manual é atualizada.</span><span class="sxs-lookup"><span data-stu-id="a5439-148">Raised by articulated hand controllers when a hand mesh is updated.</span></span> |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | <span data-ttu-id="a5439-149">Ação iniciada/encerrada</span><span class="sxs-lookup"><span data-stu-id="a5439-149">Action Started / Ended</span></span> | <span data-ttu-id="a5439-150">Aumente para indicar o início e o término da ação para entradas mapeadas para ações.</span><span class="sxs-lookup"><span data-stu-id="a5439-150">Raise to indicate action start and end for inputs mapped to actions.</span></span> |

## <a name="input-events-in-action"></a><span data-ttu-id="a5439-151">Eventos de entrada em ação</span><span class="sxs-lookup"><span data-stu-id="a5439-151">Input events in action</span></span>

<span data-ttu-id="a5439-152">No nível do script, os eventos de entrada podem ser consumidos implementando uma das interfaces do manipulador de eventos mostradas na tabela acima.</span><span class="sxs-lookup"><span data-stu-id="a5439-152">At the script level, input events can be consumed by implementing one of the event handler interfaces shown in the table above.</span></span> <span data-ttu-id="a5439-153">Quando um evento de entrada é a incêndio por meio de uma interação do usuário, ocorre o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a5439-153">When an input event fires via a user interaction, the following takes place:</span></span>

1. <span data-ttu-id="a5439-154">O sistema de entrada do MRTK reconhece que ocorreu um evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="a5439-154">The MRTK input system recognizes that an input event has occurred.</span></span>
1. <span data-ttu-id="a5439-155">O sistema de entrada do MRTK dispara a função de interface relevante do evento de entrada para todos os [manipuladores de entrada globais registrados](#register-for-global-input-events)</span><span class="sxs-lookup"><span data-stu-id="a5439-155">The MRTK input system fires the relevant interface function of the input event to all [registered global input handlers](#register-for-global-input-events)</span></span>
1. <span data-ttu-id="a5439-156">Para cada ponteiro ativo registrado com o sistema de entrada:</span><span class="sxs-lookup"><span data-stu-id="a5439-156">For every active pointer registered with the input system:</span></span>
    1. <span data-ttu-id="a5439-157">O sistema de entrada determina qual GameObject está em foco para o ponteiro atual.</span><span class="sxs-lookup"><span data-stu-id="a5439-157">The input system determines which GameObject is in focus for the current pointer.</span></span>
    1. <span data-ttu-id="a5439-158">O sistema de entrada utiliza o sistema de eventos do [Unity](https://docs.unity3d.com/Manual/EventSystem.html) para disparar a função de interface relevante para todos os componentes correspondentes no GameObject focado.</span><span class="sxs-lookup"><span data-stu-id="a5439-158">The input system utilizes [Unity's event system](https://docs.unity3d.com/Manual/EventSystem.html) to fire the relevant interface function for all matching components on the focused GameObject.</span></span>
    1. <span data-ttu-id="a5439-159">Se a qualquer momento um evento de entrada tiver sido marcado como [usado,](#how-to-stop-input-events)o processo será final e nenhum GameObjects mais receberá retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="a5439-159">If at any point an input event has been [marked as used](#how-to-stop-input-events), the process will end and no further GameObjects will receive callbacks.</span></span>
        - <span data-ttu-id="a5439-160">Exemplo: os componentes que implementam a interface [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) serão pesquisados quando um comando de fala for reconhecido.</span><span class="sxs-lookup"><span data-stu-id="a5439-160">Example: Components implementing the interface [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) will be searched for when a speech command is recognized.</span></span>
        - <span data-ttu-id="a5439-161">Observação: o sistema de eventos do Unity será bolha para pesquisar o GameObject pai se nenhum componente que corresponde à interface desejada for encontrado no GameObject atual.</span><span class="sxs-lookup"><span data-stu-id="a5439-161">Note: The Unity event system will bubble up to search the parent GameObject if no components matching the desired interface are found on the current GameObject.</span></span>
1. <span data-ttu-id="a5439-162">Se nenhum manipulador de entrada global for registrado e nenhum GameObject for encontrado com um componente/interface correspondente, o sistema de entrada chamará cada manipulador de entrada registrado de fallback</span><span class="sxs-lookup"><span data-stu-id="a5439-162">If no global input handlers are registered and no GameObject is found with a matching component/interface, then the input system will call each fallback registered input handler</span></span>

> [!NOTE]
> <span data-ttu-id="a5439-163">[Eventos de entrada de ponteiro](pointers.md#pointer-event-interfaces) são tratados de maneira ligeiramente diferente das interfaces de evento de entrada listadas acima.</span><span class="sxs-lookup"><span data-stu-id="a5439-163">[Pointer input events](pointers.md#pointer-event-interfaces) are handled in a slightly different manner than the input event interfaces listed above.</span></span> <span data-ttu-id="a5439-164">Em particular, os eventos de entrada de ponteiro são manipulados apenas pelo GameObject em foco pelo ponteiro que disparou o evento de entrada , bem como quaisquer manipuladores de entrada globais.</span><span class="sxs-lookup"><span data-stu-id="a5439-164">In particular, pointer input events are handled only by the GameObject in focus by the pointer that fired the input event - as well as any global input handlers.</span></span> <span data-ttu-id="a5439-165">Eventos de entrada regulares são tratados por GameObjects em foco para todos os ponteiros ativos.</span><span class="sxs-lookup"><span data-stu-id="a5439-165">Regular input events are handled by GameObjects in focus for all active pointers.</span></span>

### <a name="input-event-interface-example"></a><span data-ttu-id="a5439-166">Exemplo de interface de evento de entrada</span><span class="sxs-lookup"><span data-stu-id="a5439-166">Input event interface example</span></span>

<span data-ttu-id="a5439-167">O código a seguir demonstra o uso da [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface .</span><span class="sxs-lookup"><span data-stu-id="a5439-167">The code below demonstrates use of the [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface.</span></span> <span data-ttu-id="a5439-168">Quando o usuário diz as palavras "menor" ou "maior" enquanto se concentra em um GameObject com essa classe, o GameObject se dimensiona pela metade ou duas vezes `ShowHideSpeechHandler` mais.</span><span class="sxs-lookup"><span data-stu-id="a5439-168">When the user says the words "smaller" or "bigger" while focusing on a GameObject with this `ShowHideSpeechHandler` class, the GameObject will scale itself by half or twice as much.</span></span>

```c#
public class ShowHideSpeechHandler : MonoBehaviour, IMixedRealitySpeechHandler
{
    ...

    void IMixedRealitySpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.Command.Keyword == "smaller")
        {
            transform.localScale *= 0.5f;
        }
        else if (eventData.Command.Keyword == "bigger")
        {
            transform.localScale *= 2.0f;
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="a5439-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) Eventos de entrada exigem que as palavras-chave desejadas sejam previamente registradas no Perfil de Comandos [de Fala do MRTK](speech.md).</span><span class="sxs-lookup"><span data-stu-id="a5439-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) input events require that the desired keywords are pre-registered in the [MRTK Speech Commands Profile](speech.md).</span></span>

## <a name="register-for-global-input-events"></a><span data-ttu-id="a5439-170">Registrar-se para eventos de entrada globais</span><span class="sxs-lookup"><span data-stu-id="a5439-170">Register for global input events</span></span>

<span data-ttu-id="a5439-171">Para criar um componente que escuta eventos de entrada globais, desconsiderando qual GameObject pode estar em foco, um componente deve se registrar com o Sistema de Entrada.</span><span class="sxs-lookup"><span data-stu-id="a5439-171">To create a component that listens for global input events, disregarding what GameObject may be in focus, a component must register itself with the Input System.</span></span> <span data-ttu-id="a5439-172">Depois de registradas, todas as instâncias deste MonoBehaviour receberão eventos de entrada junto com qualquer GameObject(s) atualmente em foco e outros ouvintes globais registrados.</span><span class="sxs-lookup"><span data-stu-id="a5439-172">Once registered, any instances of this MonoBehaviour will receive input events along with any GameObject(s) currently in focus and other global registered listeners.</span></span>

<span data-ttu-id="a5439-173">Se um evento de entrada tiver [sido marcado como usado,](#how-to-stop-input-events)os manipuladores registrados globais ainda receberão retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="a5439-173">If an input event has been [marked as used](#how-to-stop-input-events), global registered handlers will still all receive callbacks.</span></span> <span data-ttu-id="a5439-174">No entanto, nenhum GameObjects focado receberá o evento.</span><span class="sxs-lookup"><span data-stu-id="a5439-174">However, no focused GameObjects will receive the event.</span></span>

### <a name="global-input-registration-example"></a><span data-ttu-id="a5439-175">Exemplo de registro de entrada global</span><span class="sxs-lookup"><span data-stu-id="a5439-175">Global input registration example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler, // Handle source detected and lost
    IMixedRealityHandJointHandler // handle joint position updates for hands
{
    private void OnEnable()
    {
        // Instruct Input System that we would like to receive all input events of type
        // IMixedRealitySourceStateHandler and IMixedRealityHandJointHandler
        CoreServices.InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        // This component is being destroyed
        // Instruct the Input System to disregard us for input event handling
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source detected: " + hand.ControllerHandedness);
        }
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source lost: " + hand.ControllerHandedness);
        }
    }

    public void OnHandJointsUpdated(
                InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        MixedRealityPose palmPose;
        if (eventData.InputData.TryGetValue(TrackedHandJoint.Palm, out palmPose))
        {
            Debug.Log("Hand Joint Palm Updated: " + palmPose.Position);
        }
    }
}
```

## <a name="register-for-fallback-input-events"></a><span data-ttu-id="a5439-176">Registrar-se para eventos de entrada de fallback</span><span class="sxs-lookup"><span data-stu-id="a5439-176">Register for fallback input events</span></span>

<span data-ttu-id="a5439-177">Manipuladores de entrada de fallback são semelhantes aos manipuladores de entrada globais registrados, mas são tratados como um último recurso para manipulação de eventos de entrada.</span><span class="sxs-lookup"><span data-stu-id="a5439-177">Fallback input handlers are similar to registered global input handlers but are treated as a last resort for input event handling.</span></span> <span data-ttu-id="a5439-178">Somente se nenhum manipulador de entrada global tiver sido encontrado e nenhum GameObjects estiver em foco, os manipuladores de entrada de fallback serão aproveitados.</span><span class="sxs-lookup"><span data-stu-id="a5439-178">Only if no global input handlers were found and no GameObjects are in focus will fallback input handlers be leveraged.</span></span>

### <a name="fallback-input-handler-example"></a><span data-ttu-id="a5439-179">Exemplo de manipulador de entrada de fallback</span><span class="sxs-lookup"><span data-stu-id="a5439-179">Fallback input handler example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler // Handle source detected and lost
{
    private void OnEnable()
    {
        CoreServices.InputSystem?.PushFallbackInputHandler(this);
    }

    private void OnDisable()
    {
        CoreServices.InputSystem?.PopFallbackInputHandler();
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        ...
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        ...
    }
}
```

## <a name="how-to-stop-input-events"></a><span data-ttu-id="a5439-180">Como interromper eventos de entrada</span><span class="sxs-lookup"><span data-stu-id="a5439-180">How to stop input events</span></span>

<span data-ttu-id="a5439-181">Cada interface de evento de entrada fornece [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) um objeto de dados como um parâmetro para cada função na interface.</span><span class="sxs-lookup"><span data-stu-id="a5439-181">Every input event interface provides a [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) data object as a parameter to each function on the interface.</span></span> <span data-ttu-id="a5439-182">Esse objeto de dados de evento se estende do próprio [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) Unity.</span><span class="sxs-lookup"><span data-stu-id="a5439-182">This event data object extends from Unity's own [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html).</span></span>

<span data-ttu-id="a5439-183">Para impedir que um evento de entrada se propague por meio de sua execução, conforme [descrito,](#input-events-in-action)um componente pode chamar para marcar o [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) evento como usado.</span><span class="sxs-lookup"><span data-stu-id="a5439-183">In order to stop an input event from propagating through its execution [as outlined](#input-events-in-action), a component can call [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) to mark the event as used.</span></span> <span data-ttu-id="a5439-184">Isso impedirá que qualquer outro GameObjects receba o evento de entrada atual, com exceção de manipuladores de entrada globais.</span><span class="sxs-lookup"><span data-stu-id="a5439-184">This will stop any other GameObjects from receiving the current input event, with the exception of global input handlers.</span></span>

> [!NOTE]
> <span data-ttu-id="a5439-185">Um componente que chama o `Use()` método impedirá que outros GameObjects o recebam.</span><span class="sxs-lookup"><span data-stu-id="a5439-185">A component that calls the `Use()` method will stop other GameObjects from receiving it.</span></span> <span data-ttu-id="a5439-186">No entanto, outros componentes no GameObject atual ainda receberão o evento de entrada e dispararão as funções de interface relacionadas.</span><span class="sxs-lookup"><span data-stu-id="a5439-186">However, other components on the current GameObject will still receive the input event and fire any related interface functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5439-187">Confira também</span><span class="sxs-lookup"><span data-stu-id="a5439-187">See also</span></span>

- [<span data-ttu-id="a5439-188">Ponteiros</span><span class="sxs-lookup"><span data-stu-id="a5439-188">Pointers</span></span>](pointers.md)
- [<span data-ttu-id="a5439-189">Fala</span><span class="sxs-lookup"><span data-stu-id="a5439-189">Speech</span></span>](speech.md)
- [<span data-ttu-id="a5439-190">Estado de entrada</span><span class="sxs-lookup"><span data-stu-id="a5439-190">Input State</span></span>](input-state.md)
