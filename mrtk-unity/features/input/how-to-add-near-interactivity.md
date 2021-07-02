---
title: Como adicionar interatividade próxima
description: Documentação sobre interação próxima no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Interação Próxima,
ms.openlocfilehash: 241425f0c158d684cad6dad8c88c8d692cbec42f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176872"
---
# <a name="how-to-add-near-interactivity"></a>Como adicionar interatividade próxima

As interações próximas vêm na forma de toques e capturas. Eventos de toque e captura são gerados como eventos de ponteiro [peloPointer e](pointers.md#pokepointer) [SpherePointer,](pointers.md#spherepointer)respectivamente.

Três etapas principais são necessárias para escutar eventos de toque e/ou de entrada em um GameObject específico.

1. Verifique se o ponteiro relevante está registrado no Perfil de Configuração do [MRTK principal.](../../configuration/mixed-reality-configuration-guide.md)
1. Verifique se o GameObject desejado tem o componente de [script](#add-touch-interactions) [de toque](#add-grab-interactions) ou captura apropriado e [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .
1. Implemente uma interface de manipulador de entrada em um script anexado ao GameObject desejado para escutar os eventos [de captura](#grab-code-example) [ou](#touch-code-example) toque.

## <a name="add-grab-interactions"></a>Adicionar interações de captura

1. Verifique se [um SpherePointer](pointers.md#spherepointer) está registrado no perfil *ponteiro do MRTK*.

    O perfil padrão do MRTK e o perfil padrão HoloLens 2 já contêm um *SpherePointer.* É possível confirmar que um SpherePointer será criado selecionando o Perfil de Configuração do MRTK e navegando até Opções de  >  **Ponteiros**  >  **de Entrada.** O `GrabPointer` pré-fab padrão (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers)  deve ser listado com um Tipo de Controlador *de Mão Articulada*. Um pré-fab personalizado pode ser utilizado desde que implemente a [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) classe .

    ![Exemplo de perfil de ponteiro de captura](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    O ponteiro de captura padrão consulta objetos próximos em um cone ao redor do ponto de captura para corresponder à interface padrão do Hololens 2.

    ![Ponteiro de captura cônica](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. No GameObject que deve ser acessível, adicione [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) um , bem como um colisor.

    Certifique-se de que a camada do GameObject está em uma camada que pode ser capturada. Por padrão, todas as camadas, exceto Reconhecimento *Espacial* *e Ignorar Raycasts,* são acessíveis. Veja quais camadas podem ser capturadas inspecionando as *Máscaras* de Camada de Captura em seu pré-fab *do GrabPointer.*

1. No GameObject ou em um de seus ancestrais, adicione um componente de script que implementa a [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface . Qualquer ancestral do objeto com o [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) também poderá receber eventos de ponteiro.

### <a name="grab-code-example"></a>Exemplo de código de captura

Abaixo está um script que será impresso se um evento for um toque ou uma captura. Na função de interface *IMixedRealityPointerHandler* relevante, é possível ver o tipo de ponteiro que dispara esse evento por meio do [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) . Se o ponteiro for *um SpherePointer*, a interação será uma captura.

```c#
public class PrintPointerEvents : MonoBehaviour, IMixedRealityPointerHandler
{
    public void OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.Pointer is SpherePointer)
        {
            Debug.Log($"Grab start from {eventData.Pointer.PointerName}");
        }
        if (eventData.Pointer is PokePointer)
        {
            Debug.Log($"Touch start from {eventData.Pointer.PointerName}");
        }
    }

    public void OnPointerClicked(MixedRealityPointerEventData eventData) {}
    public void OnPointerDragged(MixedRealityPointerEventData eventData) {}
    public void OnPointerUp(MixedRealityPointerEventData eventData) {}
}
```

## <a name="add-touch-interactions"></a>Adicionar interações de toque

O processo para adicionar interações de toque em elementos unityUI é diferente do que para GameObjects 3D de vanilla. Você pode pular para a seção a seguir, Interface *do usuário do Unity,* para habilbilenciar componentes de interface do usuário do Unity.

No **entanto,** para ambos os tipos de elementos de UX, verifique se [umPointer está](pointers.md#pokepointer) registrado no perfil *ponteiro do MRTK*.

O perfil padrão do MRTK e o perfil padrão HoloLens 2 já contêm *umPointer*. É possível confirmar que umPointer será criado selecionando o Perfil de Configuração do MRTK e navegue até **Opções de**  >  **Ponteiros de**  >  **Entrada.** O `PokePointer` pré-fab padrão (Ativos/MRTK/SDK/Recursos/UX/Prefabs/Pointers)  deve ser listado com um Tipo de Controlador *de Mão Articulada.* Um pré-fab personalizado pode ser utilizado desde que implemente a [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) classe .

![Exemplo de perfil de ponteiro de ponteiro](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>GameObjects 3D

Há duas maneiras diferentes de adicionar interações de toque a GameObjects 3D, dependendo se o objeto 3d deve ter apenas um plano sensível a toque ou de se ele deve ser tocável com base em todo o colisor.
A primeira maneira normalmente é em objetos com BoxColliders, em que é desejado ter apenas um único rosto do colisor reagir a eventos de toque. A outra é para objetos que precisam ser tocamáveis de qualquer direção com base em seu colisor.

### <a name="single-face-touch"></a>Toque de rosto único

Isso é útil para habilitar situações em que apenas um único rosto precisa ser sensível ao toque. Essa opção pressupõe que o objeto do jogo tenha um BoxCollider. É possível usar isso com objetos não BoxCollider, caso em que as propriedades 'Bounds' e 'Local Center' são definidas manualmente para configurar o plano sensível ao toque (ou seja, os limites devem ser definidos como um valor diferente de zero-zero).

1. No GameObject que deve ser sensível ao toque, adicione um BoxCollider e um [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Componente Input.NearInteractionTouchable).

    1. Definir **Eventos como Receber** como *Toque* se estiver usando o [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit. Interface Input.IMixedRealityTouchHandler) no script de componente abaixo.

    1. Clique **em Corrigir limites e** Centro de **correção**

    ![Instalação nearInteractionTouchable](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. Nesse objeto ou em um de seus ancestrais, adicione um componente de script que implementa o [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   Interface. Qualquer ancestral do objeto com o [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchable) também poderá receber eventos de ponteiro.

> [!NOTE]
> Na exibição da cena do editor com o GameObject *NearInteractionTouchable* selecionado, observe um quadrado de contorno branco e uma seta. A seta aponta para a "frente" do sensível ao toque. O collidable só poderá ser tocável nessa direção. Para tornar um colisor sensível a todas as direções, consulte a seção sobre o toque [arbitrário do colisor](#arbitrary-collider-touch).
> ![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>Toque de colisor arbitrário

Isso é útil para habilitar situações em que o objeto do jogo precisa ser sensível ao toque em toda a face do colisor. Por exemplo, isso pode ser usado para habilitar interações de toque para um objeto com um SphereCollider, em que todo o colisor precisa ser sensível ao toque.

1. No GameObject que deve ser sensível ao toque, adicione um colisor e um [ `NearInteractionTouchableVolume` ] (xref:Microsoft.MixedReality.Toolkit. Componente Input.NearInteractionTouchableVolume).

    1. Definir **Eventos como Receber** como *Toque* se estiver usando o [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit. Interface Input.IMixedRealityTouchHandler) no script de componente abaixo.

1. Nesse objeto ou em um de seus ancestrais, adicione um componente de script que implementa o [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   Interface. Qualquer ancestral do objeto com o [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchable) também poderá receber eventos de ponteiro.

### <a name="unity-ui"></a>Interface do usuário do Unity

1. Adicione/verifique se há uma [tela do UnityUI](https://docs.unity3d.com/Manual/UICanvas.html) na cena.

1. No GameObject que deve ser sensível ao toque, adicione um [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) componente.  

    1. De **definir Eventos como Receber** como *Toque* se estiver usando a interface no script de [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) componente abaixo.

1. Nesse objeto ou em um de seus ancestrais, adicione um componente de script que implementa a [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface . Qualquer ancestral do objeto com o [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) também poderá receber eventos de ponteiro.

> [!IMPORTANT]
> Os objetos poderão não se comportar conforme o esperado se eles estão localizados em objetos de tela sobrepostos. Para garantir um comportamento consistente, nunca sobreponha objetos de tela em sua cena.

> [!IMPORTANT]
> No componente `NearInteractionTouchable` de script, para a propriedade *Eventos a Receber,* há duas opções: *Ponteiro* e *Toque*. Definir *Eventos como Receber* como Ponteiro *se* estiver usando a interface e definido como Toque se estiver usando a interface no script de componente [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) que  [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) responde/trata os eventos de entrada.

#### <a name="touch-code-example"></a>Exemplo de código de toque

O código a seguir demonstra um MonoBehaviour que pode ser anexado a um GameObject com um componente variante e responder a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) eventos de entrada de toque.

```c#
public class TouchEventsExample : MonoBehaviour, IMixedRealityTouchHandler
{
    public void OnTouchStarted(HandTrackingInputEventData eventData)
    {
        string ptrName = eventData.Pointer.PointerName;
        Debug.Log($"Touch started from {ptrName}");
    }
    public void OnTouchCompleted(HandTrackingInputEventData eventData) {}
    public void OnTouchUpdated(HandTrackingInputEventData eventData) { }
}
```

## <a name="near-interaction-script-examples"></a>Exemplos de script de interação próxima

### <a name="touch-events"></a>Eventos de toque

Este exemplo cria um cubo, o torna sensível ao toque e altera a cor ao toque.

```c#
public static void MakeChangeColorOnTouch(GameObject target)
{
    // Add and configure the touchable
    var touchable = target.AddComponent<NearInteractionTouchableVolume>();
    touchable.EventsToReceive = TouchableEventType.Pointer;

    var material = target.GetComponent<Renderer>().material;
    // Change color on pointer down and up
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) => material.color = Color.green);
    pointerHandler.OnPointerUp.AddListener((e) => material.color = Color.magenta);
}
```

### <a name="grab-events"></a>Eventos de captura

O exemplo abaixo mostra como tornar um GameObject draggable. Pressupõe que o objeto do jogo tenha um colisor nele.

```c#
public static void MakeNearDraggable(GameObject target)
{
    // Instantiate and add grabbable
    target.AddComponent<NearInteractionGrabbable>();

    // Add ability to drag by re-parenting to pointer object on pointer down
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = ((SpherePointer)(e.Pointer)).transform;
        }
    });
    pointerHandler.OnPointerUp.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = null;
        }
    });
}
```

## <a name="useful-apis"></a>APIs úteis

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a>Confira também

* [Visão geral da entrada](overview.md)
* [Ponteiros](pointers.md)
* [Eventos de entrada](input-events.md)
