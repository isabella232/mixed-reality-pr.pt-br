---
title: Como adicionar uma interatividade próxima
description: Documentação sobre interação próxima no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Interação Próxima,
ms.openlocfilehash: fc0d6d4013392db74e5c8637574c258bee857865
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144186"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a>Como adicionar interação próxima no MRTK

As interações próximas vêm na forma de toques e capturas. Eventos de toque e captura são gerados como eventos de ponteiro [peloPointer e](pointers.md#pokepointer) [SpherePointer,](pointers.md#spherepointer)respectivamente.

Três etapas principais são necessárias para escutar eventos de toque e/ou de entrada em um GameObject específico.

1. Verifique se o ponteiro relevante está registrado no Perfil de Configuração do [MRTK principal.](../../configuration/mixed-reality-configuration-guide.md)
1. Verifique se o GameObject desejado tem o componente de [script](#add-touch-interactions) [de toque](#add-grab-interactions) ou captura apropriado e [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .
1. Implemente uma interface de manipulador de entrada em um script anexado ao GameObject desejado para escutar os eventos [de captura](#grab-code-example) [ou](#touch-code-example) toque.

## <a name="add-grab-interactions"></a>Adicionar interações de captura

1. Verifique se [um SpherePointer](pointers.md#spherepointer) está registrado no perfil *ponteiro do MRTK*.

    O perfil padrão do MRTK e o perfil padrão do HoloLens 2 já contêm um *SpherePointer.* É possível confirmar que um SpherePointer será criado selecionando o Perfil de Configuração do MRTK e navegando até Opções de  >  **Ponteiros**  >  **de Entrada.** O `GrabPointer` pré-fab padrão (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers)  deve ser listado com um Tipo de Controlador *de Mão Articulada*. Um pré-fab personalizado pode ser utilizado desde que implemente a [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) classe .

    ![Exemplo de perfil de ponteiro de captura](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    O ponteiro de captura padrão consulta objetos próximos em um cone ao redor do ponto de captura para corresponder à interface padrão do Hololens 2.

    ![Ponteiro de captura cônica](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. No GameObject que deve ser acessível, adicione [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) um , bem como um colisor.

    Certifique-se de que a camada do GameObject está em uma camada que pode ser capturada. Por padrão, todas as camadas, exceto *conscientização espacial* e *ignorar Raycasts* , podem ser capturadas. Veja quais camadas podem ser captadas inspecionando as *máscaras de camada de captura* em seu *GrabPointer* pré-fabricado.

1. No gameobject ou em um de seus ancestrais, adicione um componente de script que implementa a [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface. Qualquer ancestral do objeto com o também poderá [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) receber eventos de ponteiro.

### <a name="grab-code-example"></a>Exemplo de captura de código

Abaixo está um script que será impresso se um evento for um toque ou uma captura. Na função de interface *IMixedRealityPointerHandler* relevante, é possível examinar o tipo de ponteiro que dispara esse evento por meio do [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) . Se o ponteiro for um *SpherePointer*, a interação será uma captura.

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

O processo para adicionar interações de toque em elementos UnityUI é diferente do que para a baunilha 3D GameObjects. Você pode pular para a seção a seguir, *interface do usuário do Unity*, para habilitar os componentes da interface do usuário do Unity.

No entanto, para **os dois** tipos de elementos UX, verifique se um [PokePointer](pointers.md#pokepointer) está registrado no *perfil de ponteiro MRTK*.

O perfil MRTK padrão e o perfil do HoloLens 2 padrão já contêm um *PokePointer*. Uma delas pode confirmar se um PokePointer será criado selecionando o perfil de configuração do MRTK e navegando até os  >  **ponteiros** de entrada  >  **Opções de ponteiro**. O padrão `PokePointer` (assets/MRTK/SDK/Features/UX/pré-fabricados/ponteiros) pré-fabricado deve ser listado com um *tipo de controlador* de uma *mão articulada*. Um pré-fabricado personalizado pode ser utilizado contanto que ele implemente a [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) classe.

![Exemplo de Subperfil de ponteiro de arquivo](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>GameObjects 3D

Há duas maneiras diferentes de adicionar interações de toque a GameObjects 3D, dependendo de se o seu objeto 3D deve ter apenas um único plano de toque ou de se deve ser tocável com base em todo o seu colisor.
A primeira maneira é normalmente em objetos com BoxColliders, em que é desejável ter apenas uma única face do colisor reagir a eventos de toque. A outra é para objetos que precisam ser tocamáveis de qualquer direção com base em seu colisor.

### <a name="single-face-touch"></a>Toque de rosto único

Isso é útil para habilitar situações em que apenas um único rosto precisa ser sensível ao toque. Essa opção pressupõe que o objeto do jogo tenha um BoxCollider. É possível usar isso com objetos não BoxCollider, caso em que as propriedades 'Bounds' e 'Local Center' são definidas manualmente para configurar o plano sensível ao toque (ou seja, os limites devem ser definidos como um valor diferente de zero-zero).

1. No GameObject que deve ser sensível ao toque, adicione um componente BoxCollider e um [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable).

    1. Definir **Eventos como** Receber como *Toque* se estiver usando a interface [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) no script de componente abaixo.

    1. Clique **em Corrigir limites e** Centro de **correção**

    ![Instalação nearInteractionTouchable](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. Nesse objeto ou em um de seus ancestrais, adicione um componente de script que implementa o [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   Interface. Qualquer ancestral do objeto com o [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) também poderá receber eventos de ponteiro.

> [!NOTE]
> Na exibição da cena do editor com o GameObject *NearInteractionTouchable* selecionado, observe um quadrado de contorno branco e uma seta. A seta aponta para a "frente" do sensível ao toque. O collidable só poderá ser tocável nessa direção. Para tornar um colisor sensível a todas as direções, consulte a seção sobre o toque [arbitrário do colisor](#arbitrary-collider-touch).
> ![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>Toque de colisor arbitrário

Isso é útil para habilitar situações em que o objeto do jogo precisa ser sensível ao toque em toda a face do colisor. Por exemplo, isso pode ser usado para habilitar interações de toque para um objeto com um SphereCollider, em que todo o colisor precisa ser sensível ao toque.

1. No gameobject que deve ser tocável, adicione um colisor e um `NearInteractionTouchableVolume` componente [] (xref: Microsoft. MixedReality. Toolkit. Input. NearInteractionTouchableVolume).

    1. Defina os **eventos a serem recebidos** para *contato* se usar a `IMixedRealityTouchHandler` interface [] (xref: Microsoft. MixedReality. Toolkit. Input. IMixedRealityTouchHandler) no script do componente abaixo.

1. Nesse objeto ou em um de seus ancestrais, adicione um componente de script que implementa o [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   interface. Qualquer ancestral do objeto com [ `NearInteractionTouchable` ] (xref: Microsoft. MixedReality. Toolkit. Input. NearInteractionTouchable) também poderá receber eventos de ponteiro.

### <a name="unity-ui"></a>Interface do usuário do Unity

1. Adicione/Verifique se há uma [tela UnityUI](https://docs.unity3d.com/Manual/UICanvas.html) na cena.

1. No gameobject que deve ser tocável, adicione um [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) componente.  

    1. Defina os **eventos a serem recebidos** para *toque* se usar a [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface no script do componente abaixo.

1. Nesse objeto ou em um de seus ancestrais, adicione um componente de script que implementa a [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface. Qualquer ancestral do objeto com o também poderá [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) receber eventos de ponteiro.

> [!IMPORTANT]
> Os objetos podem não se comportar conforme o esperado se estiverem localizados em objetos Canvas sobrepostos. Para garantir um comportamento consistente, nunca sobreponha objetos Canvas em sua cena.

> [!IMPORTANT]
> No `NearInteractionTouchable` componente Script, para que os eventos de propriedade *recebam* duas opções: *ponteiro* e *toque*. Defina os *eventos a serem recebidos* para o *ponteiro* se usar a [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface e defina para *tocar* se usar a [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface no script do componente que responde/manipula os eventos de entrada.

#### <a name="touch-code-example"></a>Exemplo de código de toque

O código a seguir demonstra um monocomportamento que pode ser anexado a um gameobject com um [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) componente variante e responder a eventos de entrada por toque.

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

Este exemplo cria um cubo, o torna tocável e altera a cor de toque.

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

### <a name="grab-events"></a>Capturar eventos

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
