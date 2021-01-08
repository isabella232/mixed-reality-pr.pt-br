---
title: Objeto interativo
description: Saiba como disparar eventos, fornecer indicações visuais e interagir com objetos em seus aplicativos de realidade misturada.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Realidade misturada, controles, interação, indicações, interface do usuário, UX, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada, áudio
ms.openlocfilehash: d0dc8ce6425d597d04b47a6c8b08f72534488594
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007196"
---
# <a name="interactable-object"></a><span data-ttu-id="bc8f8-104">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="bc8f8-104">Interactable object</span></span>

![Objetos Interactible](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="bc8f8-106">Um botão tem muito tempo uma metáfora usada para disparar um evento no mundo abstrato de 2D.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="bc8f8-107">No mundo de realidade misturada tridimensional, não precisamos mais ser confinado para esse mundo de abstração.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="bc8f8-108">Qualquer coisa pode ser um objeto que possa ser **interagindo** que dispara um evento.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="bc8f8-109">Um objeto de interação pode ser qualquer coisa, desde uma xícara de café em uma tabela até um balão no midair.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="bc8f8-110">Ainda fazemos uso de botões tradicionais em determinadas situações, como na interface do usuário da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="bc8f8-111">A representação visual do botão depende do contexto.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="bc8f8-112">Propriedades importantes do objeto que interage</span><span class="sxs-lookup"><span data-stu-id="bc8f8-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="bc8f8-113">Indicações visuais</span><span class="sxs-lookup"><span data-stu-id="bc8f8-113">Visual cues</span></span>

<span data-ttu-id="bc8f8-114">As indicações visuais são indicações de sensor de luz, recebidas pelo olho e processadas pelo sistema visual durante a percepção visual.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="bc8f8-115">Como o sistema visual é dominante em muitas espécies, especialmente nas pessoas, as indicações visuais são uma grande fonte de informações sobre como o mundo é percebido.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="bc8f8-116">Como os objetos Holographic são mesclados com o ambiente do mundo real em realidade misturada, pode ser difícil entender de quais objetos você pode interagir.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="bc8f8-117">Para qualquer objeto interagindo em sua experiência, é importante fornecer indicações visuais diferenciadas para cada Estado de entrada.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="bc8f8-118">Isso ajuda o usuário a entender qual parte da sua experiência é interagir e torna o usuário confiante usando um método de interação consistente.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="bc8f8-119">Interações distantes</span><span class="sxs-lookup"><span data-stu-id="bc8f8-119">Far interactions</span></span>

<span data-ttu-id="bc8f8-120">Para todos os objetos que o usuário pode interagir com o olhar, o conjunto de raio e o raio do controlador de movimento, é recomendável ter uma indicação visual diferente para esses três Estados de entrada:</span><span class="sxs-lookup"><span data-stu-id="bc8f8-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="bc8f8-121">![interactibleobject-Estados-padrão](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-121">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="bc8f8-122">**Estado padrão (observação)**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="bc8f8-123">Estado ocioso padrão do objeto.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-123">Default idle state of the object.</span></span>
    <span data-ttu-id="bc8f8-124">O cursor não está no objeto.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-124">The cursor isn't on the object.</span></span> <span data-ttu-id="bc8f8-125">A mão não é detectada.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="bc8f8-126">![interactibleobject-Estados de destino](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-126">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="bc8f8-127">**Estado de destino (focalizar)**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="bc8f8-128">Quando o objeto é direcionado com o cursor olhar, a proximidade do dedo ou o ponteiro do controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="bc8f8-129">O cursor está no objeto.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-129">The cursor is on the object.</span></span> <span data-ttu-id="bc8f8-130">A mão foi detectada, pronto.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="bc8f8-131">![interactibleobject-Estados-pressionados](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-131">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="bc8f8-132">**Estado pressionado**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-132">**Pressed state**</span></span><br>
        <span data-ttu-id="bc8f8-133">Quando o objeto for pressionado com um gesto de toque de ar, pressione o botão de seleção de dedo ou controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="bc8f8-134">O cursor está no objeto.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-134">The cursor is on the object.</span></span> <span data-ttu-id="bc8f8-135">A mão é detectada, o ar está tocado.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="bc8f8-136">Você pode usar técnicas como realce ou dimensionamento para fornecer indicações visuais para o estado de entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="bc8f8-137">Em realidade misturada, você pode encontrar exemplos de visualização de diferentes Estados de entrada no menu iniciar e com os botões da barra de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="bc8f8-138">Veja como esses Estados se parecem em um **botão de Holographic**:</span><span class="sxs-lookup"><span data-stu-id="bc8f8-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="bc8f8-139">![interactibleobject-Estados-padrão](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-139">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="bc8f8-140">**Estado padrão (observação)**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="bc8f8-141">![interactibleobject-Estados de destino](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-141">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="bc8f8-142">**Estado de destino (focalizar)**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="bc8f8-143">![interactibleobject-Estados-pressionados](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-143">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="bc8f8-144">**Estado pressionado**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="bc8f8-145">Interações próximas (diretas)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-145">Near interactions (direct)</span></span> 

<span data-ttu-id="bc8f8-146">O HoloLens 2 dá suporte à entrada de acompanhamento de mão articulada, que permite que você interaja com objetos.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="bc8f8-147">Sem comentários haptics e percepção de profundidade perfeita, pode ser difícil dizer por quanto longe sua mão é de um objeto ou se você está tocando.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="bc8f8-148">É importante fornecer indicações visuais suficientes para comunicar o estado do objeto, em particular, o estado de suas mãos com base nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="bc8f8-149">Use comentários visuais para comunicar os seguintes Estados:</span><span class="sxs-lookup"><span data-stu-id="bc8f8-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="bc8f8-150">**Padrão (observação)**: estado ocioso padrão do objeto.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="bc8f8-151">**Focalizar**: quando uma mão está perto de um holograma, alterar elementos visuais para se comunicar que essa mão está direcionando o holograma.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="bc8f8-152">**Distância e ponto de interação**: à medida que a mão se aproxima de um holograma, o design de comentários para comunicar o ponto de interação projetado e a distância do objeto que o dedo é</span><span class="sxs-lookup"><span data-stu-id="bc8f8-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="bc8f8-153">**Contato começa**: alterar visuais (claro, cor) para comunicar que um toque ocorreu</span><span class="sxs-lookup"><span data-stu-id="bc8f8-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="bc8f8-154">**Segure**: alterar visuais (Light, Color) quando o objeto for Segure</span><span class="sxs-lookup"><span data-stu-id="bc8f8-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="bc8f8-155">**Contatos termina**: alterar visuais (claro, cor) quando o toque terminar</span><span class="sxs-lookup"><span data-stu-id="bc8f8-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="bc8f8-156">![Focalizar (longe)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="bc8f8-157">**Focalizar (longe)**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="bc8f8-158">Realce com base na proximidade da mão.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="bc8f8-159">![Focalizar (próximo)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="bc8f8-160">**Focalizar (próximo)**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="bc8f8-161">Realçar alterações de tamanho com base na distância para a mão.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="bc8f8-162">![Toque/pressione](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="bc8f8-163">**Toque/pressione**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-163">**Touch / press**</span></span><br>
        <span data-ttu-id="bc8f8-164">Comentários sobre áudio visual Plus.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="bc8f8-165">![Compreendi](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="bc8f8-166">**Compreendi**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-166">**Grasp**</span></span><br>
        <span data-ttu-id="bc8f8-167">Comentários sobre áudio visual Plus.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="bc8f8-168">Um [botão no HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) é um exemplo de como os diferentes Estados de interação de entrada são visualizados:</span><span class="sxs-lookup"><span data-stu-id="bc8f8-168">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="bc8f8-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="bc8f8-170">**Default**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="bc8f8-171">![Passar o mouse](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="bc8f8-172">**Passar o mouse**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-172">**Hover**</span></span><br>
        <span data-ttu-id="bc8f8-173">Revelar um efeito de iluminação baseada em proximidade.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="bc8f8-174">![Tocar](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="bc8f8-175">**Tocar**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-175">**Touch**</span></span><br>
        <span data-ttu-id="bc8f8-176">Mostrar efeito de ondulação.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="bc8f8-177">![Pressione](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="bc8f8-178">**Pressione**</span><span class="sxs-lookup"><span data-stu-id="bc8f8-178">**Press**</span></span><br>
        <span data-ttu-id="bc8f8-179">Mova a placa frontal.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="bc8f8-180">A indicação visual "anel" no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bc8f8-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="bc8f8-181">No HoloLens 2, há uma indicação visual extra, que pode ajudar a percepção de profundidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="bc8f8-182">Um anel próximo a ele é exibido e escala verticalmente conforme o alcance fica mais próximo do objeto.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="bc8f8-183">O anel, eventualmente, convergi em um ponto quando o estado pressionado é atingido.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="bc8f8-184">Essa unificação Visual ajuda o usuário a entender a distância deles do objeto.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="bc8f8-185">*Loop de vídeo: exemplo de comentários visuais com base na proximidade a uma caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="bc8f8-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="bc8f8-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="bc8f8-187">![Comentário visual sobre a proximidade](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="bc8f8-188">Indicações de áudio</span><span class="sxs-lookup"><span data-stu-id="bc8f8-188">Audio cues</span></span>

<span data-ttu-id="bc8f8-189">Para interações diretas, os comentários de áudio adequados podem melhorar drasticamente a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="bc8f8-190">Use comentários de áudio para comunicar as seguintes indicações:</span><span class="sxs-lookup"><span data-stu-id="bc8f8-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="bc8f8-191">**Contato começa**: Tocar som quando o toque começar</span><span class="sxs-lookup"><span data-stu-id="bc8f8-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="bc8f8-192">**Contatos termina**: Tocar som no ponto de toque</span><span class="sxs-lookup"><span data-stu-id="bc8f8-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="bc8f8-193">**Captura começa**: reproduzir som quando a captura começar</span><span class="sxs-lookup"><span data-stu-id="bc8f8-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="bc8f8-194">**Captações de captura**: Tocar som quando a captura terminar</span><span class="sxs-lookup"><span data-stu-id="bc8f8-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="bc8f8-195">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="bc8f8-195">Voice commanding</span></span><br>
        <span data-ttu-id="bc8f8-196">Para qualquer objeto que interaja, é importante dar suporte a opções de interação alternativas.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="bc8f8-197">Por padrão, recomendamos que os [comandos de voz](../out-of-scope/voice-design.md) tenham suporte para todos os objetos que estiverem interagindo.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="bc8f8-198">Para melhorar a descoberta, você também pode fornecer uma dica de ferramenta durante o estado de foco.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="bc8f8-199">*Imagem: dica de ferramenta para o comando de voz*</span><span class="sxs-lookup"><span data-stu-id="bc8f8-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![comando de voz](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="bc8f8-201">Recomendações de dimensionamento</span><span class="sxs-lookup"><span data-stu-id="bc8f8-201">Sizing recommendations</span></span> 

<span data-ttu-id="bc8f8-202">Para garantir que todos os objetos que podem interagir possam ser facilmente tocadas, é recomendável garantir que os interajam com um tamanho mínimo com base na distância em que são colocados do usuário.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="bc8f8-203">O ângulo visual é geralmente medido em graus de arco Visual. O ângulo visual se baseia na distância entre os olhos do usuário e o objeto e permanece constante, enquanto o tamanho físico do destino pode mudar à medida que a distância do usuário é alterada.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="bc8f8-204">Para determinar o tamanho físico necessário de um objeto com base na distância do usuário, tente usar uma calculadora de ângulo visual como [esta](https://elvers.us/perception/visualAngle/).</span><span class="sxs-lookup"><span data-stu-id="bc8f8-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="bc8f8-205">Abaixo estão as recomendações para tamanhos mínimos de conteúdo de interação.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-205">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="bc8f8-206">Tamanho de destino para interação direta</span><span class="sxs-lookup"><span data-stu-id="bc8f8-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="bc8f8-207">Distância</span><span class="sxs-lookup"><span data-stu-id="bc8f8-207">Distance</span></span> | <span data-ttu-id="bc8f8-208">Ângulo de exibição</span><span class="sxs-lookup"><span data-stu-id="bc8f8-208">Viewing angle</span></span> | <span data-ttu-id="bc8f8-209">Tamanho</span><span class="sxs-lookup"><span data-stu-id="bc8f8-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="bc8f8-210">45 cm</span><span class="sxs-lookup"><span data-stu-id="bc8f8-210">45 cm</span></span>  | <span data-ttu-id="bc8f8-211">Não é menor que 2 °</span><span class="sxs-lookup"><span data-stu-id="bc8f8-211">no smaller than 2°</span></span> | <span data-ttu-id="bc8f8-212">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="bc8f8-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="bc8f8-213">![Tamanho de destino para interação direta](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="bc8f8-214">*Tamanho de destino para interação direta*</span><span class="sxs-lookup"><span data-stu-id="bc8f8-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="bc8f8-215">Tamanho de destino para botões</span><span class="sxs-lookup"><span data-stu-id="bc8f8-215">Target size for buttons</span></span>

<span data-ttu-id="bc8f8-216">Ao criar botões para interação direta, recomendamos um tamanho mínimo maior de 3,2 x 3,2 cm para garantir que haja espaço suficiente para conter um ícone e potencialmente algum texto.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="bc8f8-217">Distância</span><span class="sxs-lookup"><span data-stu-id="bc8f8-217">Distance</span></span> | <span data-ttu-id="bc8f8-218">Tamanho mínimo</span><span class="sxs-lookup"><span data-stu-id="bc8f8-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="bc8f8-219">45 cm</span><span class="sxs-lookup"><span data-stu-id="bc8f8-219">45 cm</span></span>  | <span data-ttu-id="bc8f8-220">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="bc8f8-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="bc8f8-221">![Tamanho do destino dos botões](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="bc8f8-222">*Tamanho do destino dos botões*</span><span class="sxs-lookup"><span data-stu-id="bc8f8-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="bc8f8-223">Tamanho de destino para interação de olhar</span><span class="sxs-lookup"><span data-stu-id="bc8f8-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="bc8f8-224">Distância</span><span class="sxs-lookup"><span data-stu-id="bc8f8-224">Distance</span></span> | <span data-ttu-id="bc8f8-225">Ângulo de exibição</span><span class="sxs-lookup"><span data-stu-id="bc8f8-225">Viewing angle</span></span> | <span data-ttu-id="bc8f8-226">Tamanho</span><span class="sxs-lookup"><span data-stu-id="bc8f8-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="bc8f8-227">2 m</span><span class="sxs-lookup"><span data-stu-id="bc8f8-227">2 m</span></span>  | <span data-ttu-id="bc8f8-228">Não é menor que 1 °</span><span class="sxs-lookup"><span data-stu-id="bc8f8-228">no smaller than 1°</span></span> | <span data-ttu-id="bc8f8-229">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="bc8f8-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="bc8f8-230">![Tamanho de destino para interação de olhar](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc8f8-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="bc8f8-231">*Tamanho de destino para interação de olhar*</span><span class="sxs-lookup"><span data-stu-id="bc8f8-231">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="bc8f8-232">Objeto de interação no MRTK (Kit de ferramentas de realidade misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="bc8f8-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="bc8f8-233">No **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, você pode usar o script de forma a [**interagir**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) para fazer com que os objetos respondam a vários tipos de Estados de interação de entrada.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="bc8f8-234">Ele dá suporte a vários tipos de temas que permitem definir estados visuais controlando Propriedades de objeto, como cor, tamanho, material e sombreador.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="bc8f8-235">Interagir</span><span class="sxs-lookup"><span data-stu-id="bc8f8-235">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="bc8f8-236">Botão</span><span class="sxs-lookup"><span data-stu-id="bc8f8-236">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="bc8f8-237">Exemplos de interação de mão cena</span><span class="sxs-lookup"><span data-stu-id="bc8f8-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="bc8f8-238">O sombreador padrão de MixedRealityToolkit fornece várias opções, como a **luz de proximidade** que ajuda você a criar indicações visuais e de áudio.</span><span class="sxs-lookup"><span data-stu-id="bc8f8-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="bc8f8-239">Sombreador padrão MRTK</span><span class="sxs-lookup"><span data-stu-id="bc8f8-239">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="bc8f8-240">Veja também</span><span class="sxs-lookup"><span data-stu-id="bc8f8-240">See also</span></span>

* [<span data-ttu-id="bc8f8-241">Cursores</span><span class="sxs-lookup"><span data-stu-id="bc8f8-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="bc8f8-242">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="bc8f8-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="bc8f8-243">Botão</span><span class="sxs-lookup"><span data-stu-id="bc8f8-243">Button</span></span>](button.md)
* [<span data-ttu-id="bc8f8-244">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="bc8f8-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="bc8f8-245">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="bc8f8-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="bc8f8-246">Manipulação</span><span class="sxs-lookup"><span data-stu-id="bc8f8-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="bc8f8-247">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="bc8f8-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="bc8f8-248">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="bc8f8-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="bc8f8-249">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="bc8f8-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="bc8f8-250">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="bc8f8-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="bc8f8-251">Teclado</span><span class="sxs-lookup"><span data-stu-id="bc8f8-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="bc8f8-252">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="bc8f8-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="bc8f8-253">Slate</span><span class="sxs-lookup"><span data-stu-id="bc8f8-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="bc8f8-254">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="bc8f8-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="bc8f8-255">Sombreador</span><span class="sxs-lookup"><span data-stu-id="bc8f8-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="bc8f8-256">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="bc8f8-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="bc8f8-257">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="bc8f8-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="bc8f8-258">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="bc8f8-258">Surface magnetism</span></span>](surface-magnetism.md)
