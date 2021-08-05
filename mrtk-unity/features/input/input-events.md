---
title: Eventos de entrada
description: Documentação de InputEvents no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Eventos,
ms.openlocfilehash: 25ac5bd4a4f5d5678a80ec362512ce7daac791a17e93944aa4832d9d09c02ee2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208328"
---
# <a name="input-events"></a>Eventos de entrada

A lista a seguir descreve todas as interfaces de evento de entrada disponíveis a serem implementadas por um componente MonoBehaviour personalizado. Essas interfaces serão chamadas pelo sistema de entrada do MRTK para lidar com a lógica personalizada do aplicativo com base nas interações de entrada do usuário. [Os eventos de entrada de](pointers.md#pointer-event-interfaces) ponteiro são tratados de maneira ligeiramente diferente dos tipos de evento de entrada padrão abaixo.

> [!IMPORTANT]
> Por padrão, um script receberá eventos de entrada somente se for o GameObject em foco por um ponteiro ou pai de um GameObject em foco.

| Manipulador | Eventos | DESCRIÇÃO |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | Origem detectada/perdida | Gerado quando uma fonte de entrada é detectada/perdida, como quando uma mão articulada é detectada ou perdida. |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | Pose de origem alterada | Gerado nas alterações de pose de origem. A pose de origem representa a pose geral da fonte de entrada. Poses específicas, como a posição da mão ou do ponteiro em um controlador do DOF de seis, podem ser obtidas por meio de `IMixedRealityInputHandler<MixedRealityPose>` . |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Entrada para baixo/para cima | Gerado em alterações em entradas binárias, como botões. |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Entrada alterada | Gerado em alterações em entradas do tipo determinado. **T** pode usar os seguintes valores: <br/> - *float* (por exemplo, retorna gatilho análogo)<br/> - *Vector2* (por exemplo, retorna a direção do thumbstick do gamepad) <br/> - *Vector3* (por exemplo, posição de retorno do dispositivo rastreado) <br/> - *Quatternion* (por exemplo, retorna a orientação do dispositivo rastreado)<br/> - [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (por exemplo, retorna o dispositivo totalmente rastreado) |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | Palavra-chave speech recognized | Gerado no reconhecimento de uma das palavras-chave configuradas no Perfil *de Comandos de Fala*. |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | Ditado<br/> Hipótese <br/> Result <br/> Concluir <br/> Erro | Gerado por sistemas de ditado para relatar os resultados de uma sessão de ditado. |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Eventos de gesto em: <br/> Iniciado <br/> Atualizado <br/> Concluído <br/> Canceled | Gerado na detecção de gestos. |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Gesto atualizado/concluído | Gerado na detecção de gestos que contêm dados adicionais do tipo determinado. Consulte [**eventos de gesto**](gestures.md#gesture-events) para obter detalhes sobre possíveis valores para **T**. |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | Junções de mão atualizadas | Gerado por controladores de mão articulados quando as junções de mão são atualizadas. |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | Malha manual atualizada | Gerado por controladores de mão articulados quando uma malha manual é atualizada. |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | Ação iniciada/encerrada | Aumente para indicar o início e o término da ação para entradas mapeadas para ações. |

## <a name="input-events-in-action"></a>Eventos de entrada em ação

No nível do script, os eventos de entrada podem ser consumidos implementando uma das interfaces do manipulador de eventos mostradas na tabela acima. Quando um evento de entrada é a incêndio por meio de uma interação do usuário, ocorre o seguinte:

1. O sistema de entrada do MRTK reconhece que ocorreu um evento de entrada.
1. O sistema de entrada do MRTK dispara a função de interface relevante do evento de entrada para todos os [manipuladores de entrada globais registrados](#register-for-global-input-events)
1. Para cada ponteiro ativo registrado com o sistema de entrada:
    1. O sistema de entrada determina qual GameObject está em foco para o ponteiro atual.
    1. O sistema de entrada utiliza o sistema de eventos do [Unity](https://docs.unity3d.com/Manual/EventSystem.html) para disparar a função de interface relevante para todos os componentes correspondentes no GameObject focado.
    1. Se a qualquer momento um evento de entrada tiver sido marcado como [usado,](#how-to-stop-input-events)o processo será final e nenhum GameObjects mais receberá retornos de chamada.
        - Exemplo: os componentes que implementam a interface [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) serão pesquisados quando um comando de fala for reconhecido.
        - Observação: o sistema de eventos do Unity será bolha para pesquisar o GameObject pai se nenhum componente que corresponde à interface desejada for encontrado no GameObject atual.
1. Se nenhum manipulador de entrada global for registrado e nenhum GameObject for encontrado com um componente/interface correspondente, o sistema de entrada chamará cada manipulador de entrada registrado de fallback

> [!NOTE]
> [Eventos de entrada de ponteiro](pointers.md#pointer-event-interfaces) são tratados de maneira ligeiramente diferente das interfaces de evento de entrada listadas acima. Em particular, os eventos de entrada de ponteiro são manipulados apenas pelo GameObject em foco pelo ponteiro que disparou o evento de entrada , bem como quaisquer manipuladores de entrada globais. Eventos de entrada regulares são tratados por GameObjects em foco para todos os ponteiros ativos.

### <a name="input-event-interface-example"></a>Exemplo de interface de evento de entrada

O código a seguir demonstra o uso da [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface . Quando o usuário diz as palavras "menor" ou "maior" enquanto se concentra em um GameObject com essa classe, o GameObject se dimensiona pela metade ou duas vezes `ShowHideSpeechHandler` mais.

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
> [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) Eventos de entrada exigem que as palavras-chave desejadas sejam previamente registradas no Perfil de Comandos [de Fala do MRTK](speech.md).

## <a name="register-for-global-input-events"></a>Registrar-se para eventos de entrada globais

Para criar um componente que escuta eventos de entrada globais, desconsiderando qual GameObject pode estar em foco, um componente deve se registrar com o Sistema de Entrada. Depois de registradas, todas as instâncias deste MonoBehaviour receberão eventos de entrada junto com qualquer GameObject(s) atualmente em foco e outros ouvintes globais registrados.

Se um evento de entrada tiver [sido marcado como usado,](#how-to-stop-input-events)os manipuladores registrados globais ainda receberão retornos de chamada. No entanto, nenhum GameObjects focado receberá o evento.

### <a name="global-input-registration-example"></a>Exemplo de registro de entrada global

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

## <a name="register-for-fallback-input-events"></a>Registrar-se para eventos de entrada de fallback

Manipuladores de entrada de fallback são semelhantes aos manipuladores de entrada globais registrados, mas são tratados como um último recurso para manipulação de eventos de entrada. Somente se nenhum manipulador de entrada global tiver sido encontrado e nenhum GameObjects estiver em foco, os manipuladores de entrada de fallback serão aproveitados.

### <a name="fallback-input-handler-example"></a>Exemplo de manipulador de entrada de fallback

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

## <a name="how-to-stop-input-events"></a>Como interromper eventos de entrada

Cada interface de evento de entrada fornece [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) um objeto de dados como um parâmetro para cada função na interface. Esse objeto de dados de evento se estende do próprio [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) Unity.

Para impedir que um evento de entrada se propague por meio de sua execução, conforme [descrito,](#input-events-in-action)um componente pode chamar para marcar o [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) evento como usado. Isso impedirá que qualquer outro GameObjects receba o evento de entrada atual, com exceção de manipuladores de entrada globais.

> [!NOTE]
> Um componente que chama o `Use()` método impedirá que outros GameObjects o recebam. No entanto, outros componentes no GameObject atual ainda receberão o evento de entrada e dispararão as funções de interface relacionadas.

## <a name="see-also"></a>Confira também

- [Ponteiros](pointers.md)
- [Fala](speech.md)
- [Estado de entrada](input-state.md)
