---
title: HowToAddNearInteractivity
description: Documentação sobre interação próxima no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, interação próxima,
ms.openlocfilehash: fc6fbb33e5a8e9aa6930f56f292f8ded51c53ff0
ms.sourcegitcommit: 0c717ed0043c7a65e2caf1452eb0f49059cdf154
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108644842"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a><span data-ttu-id="4d7cb-104">Como adicionar uma interação próxima no MRTK</span><span class="sxs-lookup"><span data-stu-id="4d7cb-104">How to add near interaction in MRTK</span></span>

<span data-ttu-id="4d7cb-105">As interações próximas vêm na forma de toques e capturas.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-105">Near interactions come in the form of touches and grabs.</span></span> <span data-ttu-id="4d7cb-106">Eventos de toque e captura são gerados como eventos de ponteiro por [PokePointer](pointers.md#pokepointer) e [SpherePointer](pointers.md#spherepointer), respectivamente.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-106">Touch and grab events are raised as pointer events by the [PokePointer](pointers.md#pokepointer) and [SpherePointer](pointers.md#spherepointer), respectively.</span></span>

<span data-ttu-id="4d7cb-107">Três etapas principais são necessárias para ouvir o toque e/ou capturar eventos de entrada em um gameobject específico.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-107">Three key steps are required to listen for touch and/or grab input events on a particular GameObject.</span></span>

1. <span data-ttu-id="4d7cb-108">Verifique se o ponteiro relevante está registrado no [perfil de configuração MRTK](../../configuration/mixed-reality-configuration-guide.md)principal.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-108">Ensure the relevant pointer is registered in the main [MRTK Configuration Profile](../../configuration/mixed-reality-configuration-guide.md).</span></span>
1. <span data-ttu-id="4d7cb-109">Verifique se o gameobject desejado tem o componente de script de [captura](#add-grab-interactions) ou [toque](#add-touch-interactions) apropriado e [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .</span><span class="sxs-lookup"><span data-stu-id="4d7cb-109">Ensure the desired GameObject has the appropriate [grab](#add-grab-interactions) or [touch](#add-touch-interactions) script component and [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html).</span></span>
1. <span data-ttu-id="4d7cb-110">Implemente uma interface de manipulador de entrada em um script anexado para o gameobject desejado para ouvir os eventos de [captura](#grab-code-example) ou [toque](#touch-code-example) .</span><span class="sxs-lookup"><span data-stu-id="4d7cb-110">Implement an input handler interface on an attached script to the desired GameObject to listen for the [grab](#grab-code-example) or [touch](#touch-code-example) events.</span></span>

## <a name="add-grab-interactions"></a><span data-ttu-id="4d7cb-111">Adicionar interações de captura</span><span class="sxs-lookup"><span data-stu-id="4d7cb-111">Add grab interactions</span></span>

1. <span data-ttu-id="4d7cb-112">Verifique se um [SpherePointer](pointers.md#spherepointer) está registrado no *perfil de ponteiro MRTK*.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-112">Ensure a [SpherePointer](pointers.md#spherepointer) is registered in the *MRTK Pointer profile*.</span></span>

    <span data-ttu-id="4d7cb-113">O perfil MRTK padrão e o perfil do HoloLens 2 padrão já contêm um *SpherePointer*.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-113">The default MRTK profile and the default HoloLens 2 profile already contain a *SpherePointer*.</span></span> <span data-ttu-id="4d7cb-114">Uma delas pode confirmar se um SpherePointer será criado selecionando o perfil de configuração do MRTK e navegando até os  >  **ponteiros** de entrada  >  **Opções de ponteiro**.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-114">One can confirm a SpherePointer will be created by selecting the MRTK Configuration Profile and navigating to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="4d7cb-115">O `GrabPointer` pré-fabricado padrão (ativos/MRTK/SDK/Features/UX/pré-fabricados/ponteiros) deve ser listado com um *tipo de controlador* de *mão articulada*.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-115">The default `GrabPointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="4d7cb-116">Um pré-fabricado personalizado pode ser utilizado contanto que ele implemente a [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) classe.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-116">A custom prefab can be utilized as long as it implements the [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) class.</span></span>

    ![Exemplo de perfil de ponteiro de captura](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    <span data-ttu-id="4d7cb-118">O ponteiro de captura padrão consulta objetos próximos em um cone em volta do ponto de captura para corresponder à interface padrão do Hololens 2.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-118">The default grab pointer queries for nearby objects in a cone around the grab point to match the default Hololens 2 interface.</span></span>

    ![Ponteiro de captura cônica](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. <span data-ttu-id="4d7cb-120">No gameobject que deve ser captado, adicione um [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) , bem como um colisor.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-120">On the GameObject that should be grabbable, add a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable), as well as a collider.</span></span>

    <span data-ttu-id="4d7cb-121">Verifique se a camada do gameobject está em uma camada de captura.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-121">Make sure the layer of the GameObject is on a grabbable layer.</span></span> <span data-ttu-id="4d7cb-122">Por padrão, todas as camadas, exceto *conscientização espacial* e *ignorar Raycasts* , podem ser capturadas.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-122">By default, all layers except *Spatial Awareness* and *Ignore Raycasts* are grabbable.</span></span> <span data-ttu-id="4d7cb-123">Veja quais camadas podem ser captadas inspecionando as *máscaras de camada de captura* em seu *GrabPointer* pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-123">See which layers are grabbable by inspecting the *Grab Layer Masks* in your *GrabPointer* prefab.</span></span>

1. <span data-ttu-id="4d7cb-124">No gameobject ou em um de seus ancestrais, adicione um componente de script que implementa a [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-124">On the GameObject or one of its ancestors, add a script component that implements the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span></span> <span data-ttu-id="4d7cb-125">Qualquer ancestral do objeto com o também poderá [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) receber eventos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-125">Any ancestor of the object with the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) will be able to receive pointer events, as well.</span></span>

### <a name="grab-code-example"></a><span data-ttu-id="4d7cb-126">Exemplo de captura de código</span><span class="sxs-lookup"><span data-stu-id="4d7cb-126">Grab code example</span></span>

<span data-ttu-id="4d7cb-127">Abaixo está um script que será impresso se um evento for um toque ou uma captura.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-127">Below is a script that will print if an event is a touch or grab.</span></span> <span data-ttu-id="4d7cb-128">Na função de interface *IMixedRealityPointerHandler* relevante, é possível examinar o tipo de ponteiro que dispara esse evento por meio do [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) .</span><span class="sxs-lookup"><span data-stu-id="4d7cb-128">In the relevant *IMixedRealityPointerHandler* interface function, one can look at the type of pointer that triggers that event via the [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData).</span></span> <span data-ttu-id="4d7cb-129">Se o ponteiro for um *SpherePointer*, a interação será uma captura.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-129">If the pointer is a *SpherePointer*, the interaction is a grab.</span></span>

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

## <a name="add-touch-interactions"></a><span data-ttu-id="4d7cb-130">Adicionar interações de toque</span><span class="sxs-lookup"><span data-stu-id="4d7cb-130">Add touch interactions</span></span>

<span data-ttu-id="4d7cb-131">O processo para adicionar interações de toque em elementos UnityUI é diferente do que para a baunilha 3D GameObjects.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-131">The process for adding touch interactions on UnityUI elements is different than for vanilla 3D GameObjects.</span></span> <span data-ttu-id="4d7cb-132">Você pode pular para a seção a seguir, *interface do usuário do Unity*, para habilitar os componentes da interface do usuário do Unity.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-132">You can skip to the following section, *Unity UI*, for enabling Unity UI components.</span></span>

<span data-ttu-id="4d7cb-133">No entanto, para **os dois** tipos de elementos UX, verifique se um [PokePointer](pointers.md#pokepointer) está registrado no *perfil de ponteiro MRTK*.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-133">For **both** types of UX elements though, ensure a [PokePointer](pointers.md#pokepointer) is registered in the *MRTK Pointer profile*.</span></span>

<span data-ttu-id="4d7cb-134">O perfil MRTK padrão e o perfil do HoloLens 2 padrão já contêm um *PokePointer*.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-134">The default MRTK profile and the default HoloLens 2 profile already contain a *PokePointer*.</span></span> <span data-ttu-id="4d7cb-135">Uma delas pode confirmar se um PokePointer será criado selecionando o perfil de configuração do MRTK e navegando até os  >  **ponteiros** de entrada  >  **Opções de ponteiro**.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-135">One can confirm a PokePointer will be created by selecting the MRTK Configuration Profile and navigate to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="4d7cb-136">O padrão `PokePointer` (assets/MRTK/SDK/Features/UX/pré-fabricados/ponteiros) pré-fabricado deve ser listado com um *tipo de controlador* de uma *mão articulada*.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-136">The default `PokePointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) prefab should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="4d7cb-137">Um pré-fabricado personalizado pode ser utilizado contanto que ele implemente a [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) classe.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-137">A custom prefab can be utilized as long as it implements the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) class.</span></span>

![Exemplo de Subperfil de ponteiro de arquivo](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a><span data-ttu-id="4d7cb-139">GameObjects 3D</span><span class="sxs-lookup"><span data-stu-id="4d7cb-139">3D GameObjects</span></span>

<span data-ttu-id="4d7cb-140">Há duas maneiras diferentes de adicionar interações de toque a GameObjects 3D, dependendo de se o seu objeto 3D deve ter apenas um único plano de toque ou de se deve ser tocável com base em todo o seu colisor.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-140">There are two different ways of adding touch interactions to 3D GameObjects, depending on if your 3d object should only have a single touchable plane, or of if it should be touchable based on its entire collider.</span></span>
<span data-ttu-id="4d7cb-141">A primeira maneira é normalmente em objetos com BoxColliders, em que é desejável ter apenas uma única face do colisor reagir a eventos de toque.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-141">The first way is typically on objects with BoxColliders, where it is desired to only have a single face of the collider react to touch events.</span></span> <span data-ttu-id="4d7cb-142">A outra é para objetos que precisam ser tocáveis de qualquer direção com base em seu colisor.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-142">The other is for objects that need to be touchable from any direction based on their collider.</span></span>

### <a name="single-face-touch"></a><span data-ttu-id="4d7cb-143">Toque único</span><span class="sxs-lookup"><span data-stu-id="4d7cb-143">Single face touch</span></span>

<span data-ttu-id="4d7cb-144">Isso é útil para habilitar situações em que apenas uma única face precisa ser tocável.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-144">This is useful to enable situations where only a single face needs to be touchable.</span></span> <span data-ttu-id="4d7cb-145">Essa opção pressupõe que o objeto de jogo tem um BoxCollider.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-145">This option assumes that the game object has a BoxCollider.</span></span> <span data-ttu-id="4d7cb-146">é possível usar isso com objetos não BoxCollider; nesse caso, as propriedades ' Bounds ' e ' local Center ' são muito definidas manualmente para configurar o plano de toque (ou seja, os limites devem ser definidos como um valor diferente de zero).</span><span class="sxs-lookup"><span data-stu-id="4d7cb-146">it's possible to use this with non-BoxCollider objects, in which case the 'Bounds' and 'Local Center' properties much be manually set to configure the touchable plane (i.e. Bounds should be set to a non-zero-zero value).</span></span>

1. <span data-ttu-id="4d7cb-147">No gameobject que deve ser tocável, adicione um componente BoxCollider e um [ `NearInteractionTouchable` ] (xref: Microsoft. MixedReality. Toolkit. Input. NearInteractionTouchable).</span><span class="sxs-lookup"><span data-stu-id="4d7cb-147">On the GameObject that should be touchable, add a BoxCollider and a [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component.</span></span>

    1. <span data-ttu-id="4d7cb-148">Defina os **eventos a serem recebidos** para *contato* se usar a `IMixedRealityTouchHandler` interface [] (xref: Microsoft. MixedReality. Toolkit. Input. IMixedRealityTouchHandler) no script do componente abaixo.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-148">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

    1. <span data-ttu-id="4d7cb-149">Clique em **corrigir limites** e **centro de correção**</span><span class="sxs-lookup"><span data-stu-id="4d7cb-149">Click **Fix bounds** and **Fix center**</span></span>

    ![Configuração do NearInteractionTouchable](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. <span data-ttu-id="4d7cb-151">Nesse objeto ou em um de seus ancestrais, adicione um componente de script que implementa o [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="4d7cb-151">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="4d7cb-152">interface.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-152">interface.</span></span> <span data-ttu-id="4d7cb-153">Qualquer ancestral do objeto com [ `NearInteractionTouchable` ] (xref: Microsoft. MixedReality. Toolkit. Input. NearInteractionTouchable) também poderá receber eventos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-153">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

> [!NOTE]
> <span data-ttu-id="4d7cb-154">Na exibição de cena do editor com o *NearInteractionTouchable* gameobject selecionado, observe um quadrado de contorno branco e uma seta.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-154">In the editor scene view with the *NearInteractionTouchable* GameObject selected, notice a white outline square and arrow.</span></span> <span data-ttu-id="4d7cb-155">A seta aponta para a "frente" do toque.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-155">The arrow points to the "front" of the touchable.</span></span> <span data-ttu-id="4d7cb-156">O conflito só será sensível a essa direção.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-156">The collidable will only be touchable from that direction.</span></span> <span data-ttu-id="4d7cb-157">Para tornar um colisor tocável de todas as direções, consulte a seção sobre o [toque arbitrário do colisor](#arbitrary-collider-touch).</span><span class="sxs-lookup"><span data-stu-id="4d7cb-157">To make a collider touchable from all directions, see the section on [arbitrary collider touch](#arbitrary-collider-touch).</span></span>
> <span data-ttu-id="4d7cb-158">![NearInteractionTouchable utensílios ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span><span class="sxs-lookup"><span data-stu-id="4d7cb-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span></span>

### <a name="arbitrary-collider-touch"></a><span data-ttu-id="4d7cb-159">Toque de colisor arbitrário</span><span class="sxs-lookup"><span data-stu-id="4d7cb-159">Arbitrary collider touch</span></span>

<span data-ttu-id="4d7cb-160">Isso é útil para habilitar situações em que o objeto do jogo precisa ser tocável ao longo de toda a face do colisor.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-160">This is useful to enable situations where the game object needs to be touchable along its entire collider face.</span></span> <span data-ttu-id="4d7cb-161">Por exemplo, isso pode ser usado para habilitar interações de toque para um objeto com um SphereCollider, onde todo o colisor precisa ser tocável.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-161">For example, this can be used to enable touch interactions for an object with a SphereCollider, where the entire collider needs to be touchable.</span></span>

1. <span data-ttu-id="4d7cb-162">No gameobject que deve ser tocável, adicione um colisor e um `NearInteractionTouchableVolume` componente [] (xref: Microsoft. MixedReality. Toolkit. Input. NearInteractionTouchableVolume).</span><span class="sxs-lookup"><span data-stu-id="4d7cb-162">On the GameObject that should be touchable, add a collider and a [`NearInteractionTouchableVolume`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume) component.</span></span>

    1. <span data-ttu-id="4d7cb-163">Defina os **eventos a serem recebidos** para *contato* se usar a `IMixedRealityTouchHandler` interface [] (xref: Microsoft. MixedReality. Toolkit. Input. IMixedRealityTouchHandler) no script do componente abaixo.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-163">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="4d7cb-164">Nesse objeto ou em um de seus ancestrais, adicione um componente de script que implementa o [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="4d7cb-164">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="4d7cb-165">interface.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-165">interface.</span></span> <span data-ttu-id="4d7cb-166">Qualquer ancestral do objeto com [ `NearInteractionTouchable` ] (xref: Microsoft. MixedReality. Toolkit. Input. NearInteractionTouchable) também poderá receber eventos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-166">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

### <a name="unity-ui"></a><span data-ttu-id="4d7cb-167">Interface do usuário do Unity</span><span class="sxs-lookup"><span data-stu-id="4d7cb-167">Unity UI</span></span>

1. <span data-ttu-id="4d7cb-168">Adicione/Verifique se há uma [tela UnityUI](https://docs.unity3d.com/Manual/UICanvas.html) na cena.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-168">Add/ensure there is a [UnityUI canvas](https://docs.unity3d.com/Manual/UICanvas.html) in the scene.</span></span>

1. <span data-ttu-id="4d7cb-169">No gameobject que deve ser tocável, adicione um [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) componente.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-169">On the GameObject that should be touchable, add a [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) component.</span></span>  

    1. <span data-ttu-id="4d7cb-170">Defina os **eventos a serem recebidos** para *toque* se usar a [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface no script do componente abaixo.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-170">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="4d7cb-171">Nesse objeto ou em um de seus ancestrais, adicione um componente de script que implementa a [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-171">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span></span> <span data-ttu-id="4d7cb-172">Qualquer ancestral do objeto com o também poderá [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) receber eventos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-172">Any ancestor of the object with the [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) will be able to receive pointer events as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d7cb-173">Os objetos podem não se comportar conforme o esperado se estiverem localizados em objetos Canvas sobrepostos.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-173">Objects may not behave as expected if they are located on overlapping canvas objects.</span></span> <span data-ttu-id="4d7cb-174">Para garantir um comportamento consistente, nunca sobreponha objetos Canvas em sua cena.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-174">To ensure consistent behavior, never overlap canvas objects in your scene.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d7cb-175">No `NearInteractionTouchable` componente Script, para que os eventos de propriedade *recebam* duas opções: *ponteiro* e *toque*.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-175">On the `NearInteractionTouchable` script component, for the property *Events to Receive* there are two options: *Pointer* and *Touch*.</span></span> <span data-ttu-id="4d7cb-176">Defina os *eventos a serem recebidos* para o *ponteiro* se usar a [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface e defina para *tocar* se usar a [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface no script do componente que responde/manipula os eventos de entrada.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-176">Set *Events to Receive* to *Pointer* if using the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface and set to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script that responds/handles the input events.</span></span>

#### <a name="touch-code-example"></a><span data-ttu-id="4d7cb-177">Exemplo de código de toque</span><span class="sxs-lookup"><span data-stu-id="4d7cb-177">Touch code example</span></span>

<span data-ttu-id="4d7cb-178">O código a seguir demonstra um monocomportamento que pode ser anexado a um gameobject com um [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) componente variante e responder a eventos de entrada por toque.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-178">The code below demonstrates a MonoBehaviour that can be attached to a GameObject with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) variant component and respond to touch input events.</span></span>

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

## <a name="near-interaction-script-examples"></a><span data-ttu-id="4d7cb-179">Exemplos de script de interação próxima</span><span class="sxs-lookup"><span data-stu-id="4d7cb-179">Near interaction script examples</span></span>

### <a name="touch-events"></a><span data-ttu-id="4d7cb-180">Eventos de toque</span><span class="sxs-lookup"><span data-stu-id="4d7cb-180">Touch events</span></span>

<span data-ttu-id="4d7cb-181">Este exemplo cria um cubo, o torna tocável e altera a cor de toque.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-181">This example creates a cube, makes it touchable, and changes color on touch.</span></span>

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

### <a name="grab-events"></a><span data-ttu-id="4d7cb-182">Capturar eventos</span><span class="sxs-lookup"><span data-stu-id="4d7cb-182">Grab events</span></span>

<span data-ttu-id="4d7cb-183">O exemplo abaixo mostra como tornar um gameobject arrastável.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-183">The below example shows how to make a GameObject draggable.</span></span> <span data-ttu-id="4d7cb-184">Pressupõe que o objeto Game tem um colisor nele.</span><span class="sxs-lookup"><span data-stu-id="4d7cb-184">Assumes that the game object has a collider on it.</span></span>

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

## <a name="useful-apis"></a><span data-ttu-id="4d7cb-185">APIs úteis</span><span class="sxs-lookup"><span data-stu-id="4d7cb-185">Useful APIs</span></span>

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a><span data-ttu-id="4d7cb-186">Confira também</span><span class="sxs-lookup"><span data-stu-id="4d7cb-186">See also</span></span>

* [<span data-ttu-id="4d7cb-187">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="4d7cb-187">Input Overview</span></span>](overview.md)
* [<span data-ttu-id="4d7cb-188">Ponteiros</span><span class="sxs-lookup"><span data-stu-id="4d7cb-188">Pointers</span></span>](pointers.md)
* [<span data-ttu-id="4d7cb-189">Eventos de entrada</span><span class="sxs-lookup"><span data-stu-id="4d7cb-189">Input Events</span></span>](input-events.md)
