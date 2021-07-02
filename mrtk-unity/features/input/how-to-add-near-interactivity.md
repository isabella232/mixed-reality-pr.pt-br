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
# <a name="how-to-add-near-interactivity"></a><span data-ttu-id="eec12-104">Como adicionar interatividade próxima</span><span class="sxs-lookup"><span data-stu-id="eec12-104">How to add near interactivity</span></span>

<span data-ttu-id="eec12-105">As interações próximas vêm na forma de toques e capturas.</span><span class="sxs-lookup"><span data-stu-id="eec12-105">Near interactions come in the form of touches and grabs.</span></span> <span data-ttu-id="eec12-106">Eventos de toque e captura são gerados como eventos de ponteiro [peloPointer e](pointers.md#pokepointer) [SpherePointer,](pointers.md#spherepointer)respectivamente.</span><span class="sxs-lookup"><span data-stu-id="eec12-106">Touch and grab events are raised as pointer events by the [PokePointer](pointers.md#pokepointer) and [SpherePointer](pointers.md#spherepointer), respectively.</span></span>

<span data-ttu-id="eec12-107">Três etapas principais são necessárias para escutar eventos de toque e/ou de entrada em um GameObject específico.</span><span class="sxs-lookup"><span data-stu-id="eec12-107">Three key steps are required to listen for touch and/or grab input events on a particular GameObject.</span></span>

1. <span data-ttu-id="eec12-108">Verifique se o ponteiro relevante está registrado no Perfil de Configuração do [MRTK principal.](../../configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="eec12-108">Ensure the relevant pointer is registered in the main [MRTK Configuration Profile](../../configuration/mixed-reality-configuration-guide.md).</span></span>
1. <span data-ttu-id="eec12-109">Verifique se o GameObject desejado tem o componente de [script](#add-touch-interactions) [de toque](#add-grab-interactions) ou captura apropriado e [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .</span><span class="sxs-lookup"><span data-stu-id="eec12-109">Ensure the desired GameObject has the appropriate [grab](#add-grab-interactions) or [touch](#add-touch-interactions) script component and [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html).</span></span>
1. <span data-ttu-id="eec12-110">Implemente uma interface de manipulador de entrada em um script anexado ao GameObject desejado para escutar os eventos [de captura](#grab-code-example) [ou](#touch-code-example) toque.</span><span class="sxs-lookup"><span data-stu-id="eec12-110">Implement an input handler interface on an attached script to the desired GameObject to listen for the [grab](#grab-code-example) or [touch](#touch-code-example) events.</span></span>

## <a name="add-grab-interactions"></a><span data-ttu-id="eec12-111">Adicionar interações de captura</span><span class="sxs-lookup"><span data-stu-id="eec12-111">Add grab interactions</span></span>

1. <span data-ttu-id="eec12-112">Verifique se [um SpherePointer](pointers.md#spherepointer) está registrado no perfil *ponteiro do MRTK*.</span><span class="sxs-lookup"><span data-stu-id="eec12-112">Ensure a [SpherePointer](pointers.md#spherepointer) is registered in the *MRTK Pointer profile*.</span></span>

    <span data-ttu-id="eec12-113">O perfil padrão do MRTK e o perfil padrão HoloLens 2 já contêm um *SpherePointer.*</span><span class="sxs-lookup"><span data-stu-id="eec12-113">The default MRTK profile and the default HoloLens 2 profile already contain a *SpherePointer*.</span></span> <span data-ttu-id="eec12-114">É possível confirmar que um SpherePointer será criado selecionando o Perfil de Configuração do MRTK e navegando até Opções de  >  **Ponteiros**  >  **de Entrada.**</span><span class="sxs-lookup"><span data-stu-id="eec12-114">One can confirm a SpherePointer will be created by selecting the MRTK Configuration Profile and navigating to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="eec12-115">O `GrabPointer` pré-fab padrão (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers)  deve ser listado com um Tipo de Controlador *de Mão Articulada*.</span><span class="sxs-lookup"><span data-stu-id="eec12-115">The default `GrabPointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="eec12-116">Um pré-fab personalizado pode ser utilizado desde que implemente a [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) classe .</span><span class="sxs-lookup"><span data-stu-id="eec12-116">A custom prefab can be utilized as long as it implements the [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) class.</span></span>

    ![Exemplo de perfil de ponteiro de captura](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    <span data-ttu-id="eec12-118">O ponteiro de captura padrão consulta objetos próximos em um cone ao redor do ponto de captura para corresponder à interface padrão do Hololens 2.</span><span class="sxs-lookup"><span data-stu-id="eec12-118">The default grab pointer queries for nearby objects in a cone around the grab point to match the default Hololens 2 interface.</span></span>

    ![Ponteiro de captura cônica](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. <span data-ttu-id="eec12-120">No GameObject que deve ser acessível, adicione [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) um , bem como um colisor.</span><span class="sxs-lookup"><span data-stu-id="eec12-120">On the GameObject that should be grabbable, add a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable), as well as a collider.</span></span>

    <span data-ttu-id="eec12-121">Certifique-se de que a camada do GameObject está em uma camada que pode ser capturada.</span><span class="sxs-lookup"><span data-stu-id="eec12-121">Make sure the layer of the GameObject is on a grabbable layer.</span></span> <span data-ttu-id="eec12-122">Por padrão, todas as camadas, exceto Reconhecimento *Espacial* *e Ignorar Raycasts,* são acessíveis.</span><span class="sxs-lookup"><span data-stu-id="eec12-122">By default, all layers except *Spatial Awareness* and *Ignore Raycasts* are grabbable.</span></span> <span data-ttu-id="eec12-123">Veja quais camadas podem ser capturadas inspecionando as *Máscaras* de Camada de Captura em seu pré-fab *do GrabPointer.*</span><span class="sxs-lookup"><span data-stu-id="eec12-123">See which layers are grabbable by inspecting the *Grab Layer Masks* in your *GrabPointer* prefab.</span></span>

1. <span data-ttu-id="eec12-124">No GameObject ou em um de seus ancestrais, adicione um componente de script que implementa a [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface .</span><span class="sxs-lookup"><span data-stu-id="eec12-124">On the GameObject or one of its ancestors, add a script component that implements the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span></span> <span data-ttu-id="eec12-125">Qualquer ancestral do objeto com o [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) também poderá receber eventos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="eec12-125">Any ancestor of the object with the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) will be able to receive pointer events, as well.</span></span>

### <a name="grab-code-example"></a><span data-ttu-id="eec12-126">Exemplo de código de captura</span><span class="sxs-lookup"><span data-stu-id="eec12-126">Grab code example</span></span>

<span data-ttu-id="eec12-127">Abaixo está um script que será impresso se um evento for um toque ou uma captura.</span><span class="sxs-lookup"><span data-stu-id="eec12-127">Below is a script that will print if an event is a touch or grab.</span></span> <span data-ttu-id="eec12-128">Na função de interface *IMixedRealityPointerHandler* relevante, é possível ver o tipo de ponteiro que dispara esse evento por meio do [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) .</span><span class="sxs-lookup"><span data-stu-id="eec12-128">In the relevant *IMixedRealityPointerHandler* interface function, one can look at the type of pointer that triggers that event via the [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData).</span></span> <span data-ttu-id="eec12-129">Se o ponteiro for *um SpherePointer*, a interação será uma captura.</span><span class="sxs-lookup"><span data-stu-id="eec12-129">If the pointer is a *SpherePointer*, the interaction is a grab.</span></span>

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

## <a name="add-touch-interactions"></a><span data-ttu-id="eec12-130">Adicionar interações de toque</span><span class="sxs-lookup"><span data-stu-id="eec12-130">Add touch interactions</span></span>

<span data-ttu-id="eec12-131">O processo para adicionar interações de toque em elementos unityUI é diferente do que para GameObjects 3D de vanilla.</span><span class="sxs-lookup"><span data-stu-id="eec12-131">The process for adding touch interactions on UnityUI elements is different than for vanilla 3D GameObjects.</span></span> <span data-ttu-id="eec12-132">Você pode pular para a seção a seguir, Interface *do usuário do Unity,* para habilbilenciar componentes de interface do usuário do Unity.</span><span class="sxs-lookup"><span data-stu-id="eec12-132">You can skip to the following section, *Unity UI*, for enabling Unity UI components.</span></span>

<span data-ttu-id="eec12-133">No **entanto,** para ambos os tipos de elementos de UX, verifique se [umPointer está](pointers.md#pokepointer) registrado no perfil *ponteiro do MRTK*.</span><span class="sxs-lookup"><span data-stu-id="eec12-133">For **both** types of UX elements though, ensure a [PokePointer](pointers.md#pokepointer) is registered in the *MRTK Pointer profile*.</span></span>

<span data-ttu-id="eec12-134">O perfil padrão do MRTK e o perfil padrão HoloLens 2 já contêm *umPointer*.</span><span class="sxs-lookup"><span data-stu-id="eec12-134">The default MRTK profile and the default HoloLens 2 profile already contain a *PokePointer*.</span></span> <span data-ttu-id="eec12-135">É possível confirmar que umPointer será criado selecionando o Perfil de Configuração do MRTK e navegue até **Opções de**  >  **Ponteiros de**  >  **Entrada.**</span><span class="sxs-lookup"><span data-stu-id="eec12-135">One can confirm a PokePointer will be created by selecting the MRTK Configuration Profile and navigate to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="eec12-136">O `PokePointer` pré-fab padrão (Ativos/MRTK/SDK/Recursos/UX/Prefabs/Pointers)  deve ser listado com um Tipo de Controlador *de Mão Articulada.*</span><span class="sxs-lookup"><span data-stu-id="eec12-136">The default `PokePointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) prefab should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="eec12-137">Um pré-fab personalizado pode ser utilizado desde que implemente a [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) classe .</span><span class="sxs-lookup"><span data-stu-id="eec12-137">A custom prefab can be utilized as long as it implements the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) class.</span></span>

![Exemplo de perfil de ponteiro de ponteiro](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a><span data-ttu-id="eec12-139">GameObjects 3D</span><span class="sxs-lookup"><span data-stu-id="eec12-139">3D GameObjects</span></span>

<span data-ttu-id="eec12-140">Há duas maneiras diferentes de adicionar interações de toque a GameObjects 3D, dependendo se o objeto 3d deve ter apenas um plano sensível a toque ou de se ele deve ser tocável com base em todo o colisor.</span><span class="sxs-lookup"><span data-stu-id="eec12-140">There are two different ways of adding touch interactions to 3D GameObjects, depending on if your 3d object should only have a single touchable plane, or of if it should be touchable based on its entire collider.</span></span>
<span data-ttu-id="eec12-141">A primeira maneira normalmente é em objetos com BoxColliders, em que é desejado ter apenas um único rosto do colisor reagir a eventos de toque.</span><span class="sxs-lookup"><span data-stu-id="eec12-141">The first way is typically on objects with BoxColliders, where it is desired to only have a single face of the collider react to touch events.</span></span> <span data-ttu-id="eec12-142">A outra é para objetos que precisam ser tocamáveis de qualquer direção com base em seu colisor.</span><span class="sxs-lookup"><span data-stu-id="eec12-142">The other is for objects that need to be touchable from any direction based on their collider.</span></span>

### <a name="single-face-touch"></a><span data-ttu-id="eec12-143">Toque de rosto único</span><span class="sxs-lookup"><span data-stu-id="eec12-143">Single face touch</span></span>

<span data-ttu-id="eec12-144">Isso é útil para habilitar situações em que apenas um único rosto precisa ser sensível ao toque.</span><span class="sxs-lookup"><span data-stu-id="eec12-144">This is useful to enable situations where only a single face needs to be touchable.</span></span> <span data-ttu-id="eec12-145">Essa opção pressupõe que o objeto do jogo tenha um BoxCollider.</span><span class="sxs-lookup"><span data-stu-id="eec12-145">This option assumes that the game object has a BoxCollider.</span></span> <span data-ttu-id="eec12-146">É possível usar isso com objetos não BoxCollider, caso em que as propriedades 'Bounds' e 'Local Center' são definidas manualmente para configurar o plano sensível ao toque (ou seja, os limites devem ser definidos como um valor diferente de zero-zero).</span><span class="sxs-lookup"><span data-stu-id="eec12-146">it's possible to use this with non-BoxCollider objects, in which case the 'Bounds' and 'Local Center' properties much be manually set to configure the touchable plane (i.e. Bounds should be set to a non-zero-zero value).</span></span>

1. <span data-ttu-id="eec12-147">No GameObject que deve ser sensível ao toque, adicione um BoxCollider e um [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Componente Input.NearInteractionTouchable).</span><span class="sxs-lookup"><span data-stu-id="eec12-147">On the GameObject that should be touchable, add a BoxCollider and a [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component.</span></span>

    1. <span data-ttu-id="eec12-148">Definir **Eventos como Receber** como *Toque* se estiver usando o [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit. Interface Input.IMixedRealityTouchHandler) no script de componente abaixo.</span><span class="sxs-lookup"><span data-stu-id="eec12-148">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

    1. <span data-ttu-id="eec12-149">Clique **em Corrigir limites e** Centro de **correção**</span><span class="sxs-lookup"><span data-stu-id="eec12-149">Click **Fix bounds** and **Fix center**</span></span>

    ![Instalação nearInteractionTouchable](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. <span data-ttu-id="eec12-151">Nesse objeto ou em um de seus ancestrais, adicione um componente de script que implementa o [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="eec12-151">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="eec12-152">Interface.</span><span class="sxs-lookup"><span data-stu-id="eec12-152">interface.</span></span> <span data-ttu-id="eec12-153">Qualquer ancestral do objeto com o [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchable) também poderá receber eventos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="eec12-153">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

> [!NOTE]
> <span data-ttu-id="eec12-154">Na exibição da cena do editor com o GameObject *NearInteractionTouchable* selecionado, observe um quadrado de contorno branco e uma seta.</span><span class="sxs-lookup"><span data-stu-id="eec12-154">In the editor scene view with the *NearInteractionTouchable* GameObject selected, notice a white outline square and arrow.</span></span> <span data-ttu-id="eec12-155">A seta aponta para a "frente" do sensível ao toque.</span><span class="sxs-lookup"><span data-stu-id="eec12-155">The arrow points to the "front" of the touchable.</span></span> <span data-ttu-id="eec12-156">O collidable só poderá ser tocável nessa direção.</span><span class="sxs-lookup"><span data-stu-id="eec12-156">The collidable will only be touchable from that direction.</span></span> <span data-ttu-id="eec12-157">Para tornar um colisor sensível a todas as direções, consulte a seção sobre o toque [arbitrário do colisor](#arbitrary-collider-touch).</span><span class="sxs-lookup"><span data-stu-id="eec12-157">To make a collider touchable from all directions, see the section on [arbitrary collider touch](#arbitrary-collider-touch).</span></span>
> <span data-ttu-id="eec12-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span><span class="sxs-lookup"><span data-stu-id="eec12-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span></span>

### <a name="arbitrary-collider-touch"></a><span data-ttu-id="eec12-159">Toque de colisor arbitrário</span><span class="sxs-lookup"><span data-stu-id="eec12-159">Arbitrary collider touch</span></span>

<span data-ttu-id="eec12-160">Isso é útil para habilitar situações em que o objeto do jogo precisa ser sensível ao toque em toda a face do colisor.</span><span class="sxs-lookup"><span data-stu-id="eec12-160">This is useful to enable situations where the game object needs to be touchable along its entire collider face.</span></span> <span data-ttu-id="eec12-161">Por exemplo, isso pode ser usado para habilitar interações de toque para um objeto com um SphereCollider, em que todo o colisor precisa ser sensível ao toque.</span><span class="sxs-lookup"><span data-stu-id="eec12-161">For example, this can be used to enable touch interactions for an object with a SphereCollider, where the entire collider needs to be touchable.</span></span>

1. <span data-ttu-id="eec12-162">No GameObject que deve ser sensível ao toque, adicione um colisor e um [ `NearInteractionTouchableVolume` ] (xref:Microsoft.MixedReality.Toolkit. Componente Input.NearInteractionTouchableVolume).</span><span class="sxs-lookup"><span data-stu-id="eec12-162">On the GameObject that should be touchable, add a collider and a [`NearInteractionTouchableVolume`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume) component.</span></span>

    1. <span data-ttu-id="eec12-163">Definir **Eventos como Receber** como *Toque* se estiver usando o [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit. Interface Input.IMixedRealityTouchHandler) no script de componente abaixo.</span><span class="sxs-lookup"><span data-stu-id="eec12-163">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="eec12-164">Nesse objeto ou em um de seus ancestrais, adicione um componente de script que implementa o [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="eec12-164">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="eec12-165">Interface.</span><span class="sxs-lookup"><span data-stu-id="eec12-165">interface.</span></span> <span data-ttu-id="eec12-166">Qualquer ancestral do objeto com o [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchable) também poderá receber eventos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="eec12-166">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

### <a name="unity-ui"></a><span data-ttu-id="eec12-167">Interface do usuário do Unity</span><span class="sxs-lookup"><span data-stu-id="eec12-167">Unity UI</span></span>

1. <span data-ttu-id="eec12-168">Adicione/verifique se há uma [tela do UnityUI](https://docs.unity3d.com/Manual/UICanvas.html) na cena.</span><span class="sxs-lookup"><span data-stu-id="eec12-168">Add/ensure there is a [UnityUI canvas](https://docs.unity3d.com/Manual/UICanvas.html) in the scene.</span></span>

1. <span data-ttu-id="eec12-169">No GameObject que deve ser sensível ao toque, adicione um [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) componente.</span><span class="sxs-lookup"><span data-stu-id="eec12-169">On the GameObject that should be touchable, add a [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) component.</span></span>  

    1. <span data-ttu-id="eec12-170">De **definir Eventos como Receber** como *Toque* se estiver usando a interface no script de [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) componente abaixo.</span><span class="sxs-lookup"><span data-stu-id="eec12-170">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="eec12-171">Nesse objeto ou em um de seus ancestrais, adicione um componente de script que implementa a [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface .</span><span class="sxs-lookup"><span data-stu-id="eec12-171">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span></span> <span data-ttu-id="eec12-172">Qualquer ancestral do objeto com o [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) também poderá receber eventos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="eec12-172">Any ancestor of the object with the [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) will be able to receive pointer events as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eec12-173">Os objetos poderão não se comportar conforme o esperado se eles estão localizados em objetos de tela sobrepostos.</span><span class="sxs-lookup"><span data-stu-id="eec12-173">Objects may not behave as expected if they are located on overlapping canvas objects.</span></span> <span data-ttu-id="eec12-174">Para garantir um comportamento consistente, nunca sobreponha objetos de tela em sua cena.</span><span class="sxs-lookup"><span data-stu-id="eec12-174">To ensure consistent behavior, never overlap canvas objects in your scene.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eec12-175">No componente `NearInteractionTouchable` de script, para a propriedade *Eventos a Receber,* há duas opções: *Ponteiro* e *Toque*.</span><span class="sxs-lookup"><span data-stu-id="eec12-175">On the `NearInteractionTouchable` script component, for the property *Events to Receive* there are two options: *Pointer* and *Touch*.</span></span> <span data-ttu-id="eec12-176">Definir *Eventos como Receber* como Ponteiro *se* estiver usando a interface e definido como Toque se estiver usando a interface no script de componente [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) que  [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) responde/trata os eventos de entrada.</span><span class="sxs-lookup"><span data-stu-id="eec12-176">Set *Events to Receive* to *Pointer* if using the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface and set to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script that responds/handles the input events.</span></span>

#### <a name="touch-code-example"></a><span data-ttu-id="eec12-177">Exemplo de código de toque</span><span class="sxs-lookup"><span data-stu-id="eec12-177">Touch code example</span></span>

<span data-ttu-id="eec12-178">O código a seguir demonstra um MonoBehaviour que pode ser anexado a um GameObject com um componente variante e responder a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) eventos de entrada de toque.</span><span class="sxs-lookup"><span data-stu-id="eec12-178">The code below demonstrates a MonoBehaviour that can be attached to a GameObject with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) variant component and respond to touch input events.</span></span>

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

## <a name="near-interaction-script-examples"></a><span data-ttu-id="eec12-179">Exemplos de script de interação próxima</span><span class="sxs-lookup"><span data-stu-id="eec12-179">Near interaction script examples</span></span>

### <a name="touch-events"></a><span data-ttu-id="eec12-180">Eventos de toque</span><span class="sxs-lookup"><span data-stu-id="eec12-180">Touch events</span></span>

<span data-ttu-id="eec12-181">Este exemplo cria um cubo, o torna sensível ao toque e altera a cor ao toque.</span><span class="sxs-lookup"><span data-stu-id="eec12-181">This example creates a cube, makes it touchable, and changes color on touch.</span></span>

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

### <a name="grab-events"></a><span data-ttu-id="eec12-182">Eventos de captura</span><span class="sxs-lookup"><span data-stu-id="eec12-182">Grab events</span></span>

<span data-ttu-id="eec12-183">O exemplo abaixo mostra como tornar um GameObject draggable.</span><span class="sxs-lookup"><span data-stu-id="eec12-183">The below example shows how to make a GameObject draggable.</span></span> <span data-ttu-id="eec12-184">Pressupõe que o objeto do jogo tenha um colisor nele.</span><span class="sxs-lookup"><span data-stu-id="eec12-184">Assumes that the game object has a collider on it.</span></span>

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

## <a name="useful-apis"></a><span data-ttu-id="eec12-185">APIs úteis</span><span class="sxs-lookup"><span data-stu-id="eec12-185">Useful APIs</span></span>

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a><span data-ttu-id="eec12-186">Confira também</span><span class="sxs-lookup"><span data-stu-id="eec12-186">See also</span></span>

* [<span data-ttu-id="eec12-187">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="eec12-187">Input Overview</span></span>](overview.md)
* [<span data-ttu-id="eec12-188">Ponteiros</span><span class="sxs-lookup"><span data-stu-id="eec12-188">Pointers</span></span>](pointers.md)
* [<span data-ttu-id="eec12-189">Eventos de entrada</span><span class="sxs-lookup"><span data-stu-id="eec12-189">Input Events</span></span>](input-events.md)
