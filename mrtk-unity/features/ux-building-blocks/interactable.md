---
title: Interativo
description: Visão geral sobre o componente de script interagir no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, interagir, eventos,
ms.openlocfilehash: f141a394ec9395e0a27cc964caeb66654fb6fe08
ms.sourcegitcommit: 47c402dc8e588817ce60229bf019170fa36f3045
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107581558"
---
# <a name="interactable"></a><span data-ttu-id="91341-104">Interativo</span><span class="sxs-lookup"><span data-stu-id="91341-104">Interactable</span></span>

![Interativo](../images/interactable/InteractableExamples.png)

<span data-ttu-id="91341-106">O [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) componente é um contêiner All-in-One para tornar qualquer objeto fácil de *interagir* e de responder à entrada.</span><span class="sxs-lookup"><span data-stu-id="91341-106">The [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) component is an all-in-one container to make any object easily *interactable* and responsive to input.</span></span> <span data-ttu-id="91341-107">A interação interage com todos os tipos de entrada, incluindo toque, raios para a mão, fala, etc. e funil dessas interações em [eventos](#events) e respostas de [tema Visual](visual-themes.md) .</span><span class="sxs-lookup"><span data-stu-id="91341-107">Interactable acts as a catch-all for all types of input including touch, hand rays, speech etc and funnel these interactions into [events](#events) and [visual theme](visual-themes.md) responses.</span></span> <span data-ttu-id="91341-108">Esse componente fornece uma maneira fácil de criar botões, alterar a cor em objetos com foco e muito mais.</span><span class="sxs-lookup"><span data-stu-id="91341-108">This component provides an easy way to make buttons, change color on objects with focus, and more.</span></span>

## <a name="how-to-configure-interactable"></a><span data-ttu-id="91341-109">Como configurar o interagir</span><span class="sxs-lookup"><span data-stu-id="91341-109">How to configure Interactable</span></span>

<span data-ttu-id="91341-110">O componente permite três seções principais de configuração:</span><span class="sxs-lookup"><span data-stu-id="91341-110">The component allows for three primary sections of configuration:</span></span>

1) [<span data-ttu-id="91341-111">Configuração de entrada geral</span><span class="sxs-lookup"><span data-stu-id="91341-111">General input configuration</span></span>](#general-input-settings)
1) <span data-ttu-id="91341-112">[Temas visuais](visual-themes.md) direcionados a vários Gameobjects</span><span class="sxs-lookup"><span data-stu-id="91341-112">[Visual Themes](visual-themes.md) targeted against multiple GameObjects</span></span>
1) [<span data-ttu-id="91341-113">Manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="91341-113">Event handlers</span></span>](#events)

### <a name="general-input-settings"></a><span data-ttu-id="91341-114">Configurações de entrada gerais</span><span class="sxs-lookup"><span data-stu-id="91341-114">General input settings</span></span>

![Configurações gerais de interação](../images/interactable/InputFeatures_short.png)

<span data-ttu-id="91341-116">**Estados**</span><span class="sxs-lookup"><span data-stu-id="91341-116">**States**</span></span>

<span data-ttu-id="91341-117">*Estados* é um parâmetro [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) que define as fases de interações, como Press ou Observad, para perfis de [elementos e temas](visual-themes.md)de [interação](#interactable-profiles) .</span><span class="sxs-lookup"><span data-stu-id="91341-117">*States* is a [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) parameter that defines the interactions phases, like press or observed, for [Interactable Profiles](#interactable-profiles) and [Visual Themes](visual-themes.md).</span></span>

<span data-ttu-id="91341-118">O **DefaultInteractableStates** (assets/MRTK/SDK/Features/UX/interagible/States/DefaultInteractableStates. Asset) é fornecido com o MRTK pronto para uso e é o parâmetro padrão para componentes que *interagem* .</span><span class="sxs-lookup"><span data-stu-id="91341-118">The **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) ships with MRTK out-of-box and is the default parameter for *Interactable* components.</span></span>

![Exemplo de Estados ScriptableObject no Inspetor](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="91341-120">O ativo *DefaultInteractableStates* contém quatro Estados e utiliza a [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) implementação do modelo de estado.</span><span class="sxs-lookup"><span data-stu-id="91341-120">The *DefaultInteractableStates* asset contains four states and utilizes the [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) state model implementation.</span></span>

* <span data-ttu-id="91341-121">**Padrão**: nada está acontecendo, esse é o estado base mais isolado.</span><span class="sxs-lookup"><span data-stu-id="91341-121">**Default**: Nothing is happening, this is the most isolated base state.</span></span>

* <span data-ttu-id="91341-122">**Foco**: o objeto está sendo apontado para.</span><span class="sxs-lookup"><span data-stu-id="91341-122">**Focus**: The object is being pointed at.</span></span> <span data-ttu-id="91341-123">Este é um estado único, não há outros Estados atualmente definidos, mas ele deixará o padrão de classificação.</span><span class="sxs-lookup"><span data-stu-id="91341-123">This is a single state, no other states are currently set, but it will out rank Default.</span></span>

* <span data-ttu-id="91341-124">**Pressione**: o objeto está sendo apontado para e um botão ou mão está pressionando.</span><span class="sxs-lookup"><span data-stu-id="91341-124">**Press**: The object is being pointed at and a button or hand is pressing.</span></span> <span data-ttu-id="91341-125">As classificações de estado de saída de pressionamento padrão e foco.</span><span class="sxs-lookup"><span data-stu-id="91341-125">The Press state out ranks Default and Focus.</span></span> <span data-ttu-id="91341-126">Esse estado também será definido como um fallback para a prensa física.</span><span class="sxs-lookup"><span data-stu-id="91341-126">This state will also get set as a fallback to Physical Press.</span></span>

* <span data-ttu-id="91341-127">**Desabilitado**: o botão não deve ser interativo e os comentários visuais permitirão que o usuário saiba se, por algum motivo, esse botão não pode ser usado no momento.</span><span class="sxs-lookup"><span data-stu-id="91341-127">**Disabled**: The button should not be interactive and visual feedback will let the user know if for some reason this button is not usable at this time.</span></span> <span data-ttu-id="91341-128">Teoricamente, o estado desabilitado pode conter todos os outros Estados, mas quando habilitado está desativado, o estado desabilitado supera todos os outros Estados.</span><span class="sxs-lookup"><span data-stu-id="91341-128">In theory, the disabled state could contain all other states, but when Enabled is turned off, the Disabled state trumps all other states.</span></span>

<span data-ttu-id="91341-129">Um valor de bit (#) é atribuído ao estado, dependendo da ordem na lista.</span><span class="sxs-lookup"><span data-stu-id="91341-129">A bit value (#) is assigned to the state depending on the order in the list.</span></span>

> [!NOTE]
> <span data-ttu-id="91341-130">Geralmente, é recomendável utilizar o **DefaultInteractableStates** (assets/MRTK/SDK/Features/UX/interajable/DefaultInteractableStates. Asset) ao criar componentes de *interação* .</span><span class="sxs-lookup"><span data-stu-id="91341-130">It is generally recommended to utilize the **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) when creating *Interactable* components.</span></span>
>
> <span data-ttu-id="91341-131">No entanto, há 17 Estados interagindo disponíveis que podem ser usados para impulsionar temas, embora algumas sejam direcionadas a outros componentes.</span><span class="sxs-lookup"><span data-stu-id="91341-131">However, there are 17 Interactable states available that can be used to drive themes, though some are meant to be driven by other components.</span></span> <span data-ttu-id="91341-132">Aqui está uma lista delas com funcionalidade interna.</span><span class="sxs-lookup"><span data-stu-id="91341-132">Here is a list of those with built-in functionality.</span></span>
>
> * <span data-ttu-id="91341-133">Visitado: o interagir foi clicado.</span><span class="sxs-lookup"><span data-stu-id="91341-133">Visited: the Interactable has been clicked.</span></span>
> * <span data-ttu-id="91341-134">Alternado: o botão está em um estado de alternância ou o índice de dimensão é um número ímpar.</span><span class="sxs-lookup"><span data-stu-id="91341-134">Toggled: The button is in a toggled state or Dimension index is an odd number.</span></span>
> * <span data-ttu-id="91341-135">Gesto: a mão ou o controlador foi pressionado e movido da posição original.</span><span class="sxs-lookup"><span data-stu-id="91341-135">Gesture: The hand or controller was pressed and has moved from the original position.</span></span>
> * <span data-ttu-id="91341-136">VoiceCommand: um comando de fala foi usado para disparar o interagir.</span><span class="sxs-lookup"><span data-stu-id="91341-136">VoiceCommand: A speech command was used to trigger the Interactable.</span></span>
> * <span data-ttu-id="91341-137">PhysicalTouch: uma entrada de toque está detectada no momento; use [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) para habilitar.</span><span class="sxs-lookup"><span data-stu-id="91341-137">PhysicalTouch: A touch input is currently detected, use [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) to enable.</span></span>
> * <span data-ttu-id="91341-138">Captura: uma mão está atualmente captando os limites do objeto, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) para habilitar</span><span class="sxs-lookup"><span data-stu-id="91341-138">Grab: A hand is currently grabbing in the bounds of the object, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) to enable</span></span>

<span data-ttu-id="91341-139">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="91341-139">**Enabled**</span></span>

<span data-ttu-id="91341-140">Alterna se um interagindo será iniciado ou não.</span><span class="sxs-lookup"><span data-stu-id="91341-140">Toggles whether an Interactable will start enabled or not.</span></span> <span data-ttu-id="91341-141">Isso corresponde ao [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) no código.</span><span class="sxs-lookup"><span data-stu-id="91341-141">This corresponds to the [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) in code.</span></span>

<span data-ttu-id="91341-142">Uma propriedade habilitada *de interação* é diferente da Propriedade habilitada configurada por meio de gameobject/componente (ou seja,</span><span class="sxs-lookup"><span data-stu-id="91341-142">An *Interactable's* enabled property is different than the enabled property configured via GameObject/Component (i.e</span></span> <span data-ttu-id="91341-143">SetActive etc.).</span><span class="sxs-lookup"><span data-stu-id="91341-143">SetActive etc).</span></span> <span data-ttu-id="91341-144">A desabilitação do Jogoobject ou do monocomportamento *interagir* desabilitará a execução de tudo na classe, incluindo entrada, temas visuais, eventos, etc. A desabilitação via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) desabilitará a maioria dos tratamentos de entrada, redefinindo os Estados de entrada relacionados.</span><span class="sxs-lookup"><span data-stu-id="91341-144">Disabling the GameObject or *Interactable* MonoBehaviour will disable everything in the class from running including input, visual themes, events, etc. Disabling via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) will disable most input handling, resetting related input states.</span></span> <span data-ttu-id="91341-145">No entanto, a classe ainda executará todos os quadros e receberá eventos de entrada que serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="91341-145">However, the class will still run every frame and receive input events which will be ignored.</span></span> <span data-ttu-id="91341-146">Isso é útil para exibir o interagir em um estado desabilitado que pode ser feito por meio de temas visuais.</span><span class="sxs-lookup"><span data-stu-id="91341-146">This is useful for displaying the Interactable in a disabled state which can be done via Visual Themes.</span></span> <span data-ttu-id="91341-147">Um exemplo típico disso seria um botão enviar aguardando a conclusão de todos os campos de entrada necessários.</span><span class="sxs-lookup"><span data-stu-id="91341-147">A typical example of this would be a submit button waiting for all the required input fields to be completed.</span></span>

<span data-ttu-id="91341-148">**Ações de entrada**</span><span class="sxs-lookup"><span data-stu-id="91341-148">**Input Actions**</span></span>

<span data-ttu-id="91341-149">Selecione a [ação de entrada](../input/input-actions.md) do perfil de configuração de entrada ou de mapeamento do controlador ao qual o componente *interagindo* deve reagir.</span><span class="sxs-lookup"><span data-stu-id="91341-149">Select the [input action](../input/input-actions.md) from the input configuration or controller mapping profile that the *Interactable* component should react to.</span></span>

<span data-ttu-id="91341-150">Essa propriedade pode ser configurada em tempo de execução no código via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .</span><span class="sxs-lookup"><span data-stu-id="91341-150">This property can be configured at runtime in code via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction).</span></span>

<span data-ttu-id="91341-151">**Caso IsGlobal**</span><span class="sxs-lookup"><span data-stu-id="91341-151">**IsGlobal**</span></span>

<span data-ttu-id="91341-152">Se for true, o componente será marcado como um ouvinte de entrada global para a [ação de entrada](../input/input-actions.md)selecionada.</span><span class="sxs-lookup"><span data-stu-id="91341-152">If true, this will mark the component as a global input listener for the selected [input action](../input/input-actions.md).</span></span> <span data-ttu-id="91341-153">O comportamento padrão é false, que restringirá a entrada somente a esse colisor ou gameobject de *interação* .</span><span class="sxs-lookup"><span data-stu-id="91341-153">Default behavior is false which will restrict input to only this *Interactable* collider/GameObject.</span></span>

<span data-ttu-id="91341-154">Essa propriedade pode ser configurada em tempo de execução no código via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) .</span><span class="sxs-lookup"><span data-stu-id="91341-154">This property can be configured at runtime in code via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal).</span></span>

<span data-ttu-id="91341-155">**Comando de fala**</span><span class="sxs-lookup"><span data-stu-id="91341-155">**Speech Command**</span></span>

<span data-ttu-id="91341-156">[Comando de fala](../input/speech.md), do perfil de comandos de fala do MRTK, para disparar um evento OnClick para interação de voz.</span><span class="sxs-lookup"><span data-stu-id="91341-156">[Speech command](../input/speech.md), from the MRTK Speech Commands Profile, to trigger an OnClick event for voice interaction.</span></span>

<span data-ttu-id="91341-157">Essa propriedade pode ser configurada em tempo de execução no código via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) .</span><span class="sxs-lookup"><span data-stu-id="91341-157">This property can be configured at runtime in code via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand).</span></span>

<span data-ttu-id="91341-158">**Requer foco**</span><span class="sxs-lookup"><span data-stu-id="91341-158">**Requires Focus**</span></span>

<span data-ttu-id="91341-159">Se for true, o comando de voz só ativará o *interage* se e somente se ele já tiver o foco de um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="91341-159">If true, the voice command will only activate the *Interactable* if and only if it already has focus from a pointer.</span></span> <span data-ttu-id="91341-160">Se for false, o que poderá ser *interagido* atuará como um ouvinte global para o comando de voz selecionado.</span><span class="sxs-lookup"><span data-stu-id="91341-160">If false, then the *Interactable* will act as a global listener for the selected voice command.</span></span> <span data-ttu-id="91341-161">O comportamento padrão é true, pois vários ouvintes de fala global podem ser difíceis de organizar em uma cena.</span><span class="sxs-lookup"><span data-stu-id="91341-161">The default behavior is true, as multiple global speech listeners can be difficult to organize in a scene.</span></span>

<span data-ttu-id="91341-162">Essa propriedade pode ser configurada em tempo de execução no código via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) .</span><span class="sxs-lookup"><span data-stu-id="91341-162">This property can be configured at runtime in code via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus).</span></span>

<span data-ttu-id="91341-163">**Modo de seleção**</span><span class="sxs-lookup"><span data-stu-id="91341-163">**Selection Mode**</span></span>

<span data-ttu-id="91341-164">Essa propriedade define a lógica de seleção.</span><span class="sxs-lookup"><span data-stu-id="91341-164">This property defines the selection logic.</span></span> <span data-ttu-id="91341-165">Quando um usuário *interage* é clicado, ele faz a iteração em um nível de *dimensão* seguinte.</span><span class="sxs-lookup"><span data-stu-id="91341-165">When an *Interactable* is clicked, it iterates into a next *Dimension* level.</span></span> <span data-ttu-id="91341-166">As *dimensões* são semelhantes à classificação e define um estado fora das entradas (ou seja,</span><span class="sxs-lookup"><span data-stu-id="91341-166">*Dimensions* is similar to rank and defines a state outside of inputs (i.e</span></span> <span data-ttu-id="91341-167">foco, pressione etc.).</span><span class="sxs-lookup"><span data-stu-id="91341-167">focus, press etc).</span></span> <span data-ttu-id="91341-168">Eles são úteis para definir Estados de alternância ou outros Estados de várias classificações associados a um botão.</span><span class="sxs-lookup"><span data-stu-id="91341-168">They are useful for defining Toggle states or other multi-rank states associated with a button.</span></span> <span data-ttu-id="91341-169">O nível de dimensão atual é acompanhado pelo `Interactable.DimensionIndex` .</span><span class="sxs-lookup"><span data-stu-id="91341-169">The current Dimension level is tracked by `Interactable.DimensionIndex`.</span></span>

<span data-ttu-id="91341-170">Os modos de seleção disponíveis são:</span><span class="sxs-lookup"><span data-stu-id="91341-170">The selection modes available are:</span></span>

* <span data-ttu-id="91341-171">**Botão**  -  *Dimensões* = 1, fácil de clicar  simples</span><span class="sxs-lookup"><span data-stu-id="91341-171">**Button** - *Dimensions* = 1, simple clickable *Interactable*</span></span>
* <span data-ttu-id="91341-172">**Alternar**  -  *Dimensões* = *2, alternativas*  / *interligadas* entre o estado desativado</span><span class="sxs-lookup"><span data-stu-id="91341-172">**Toggle** - *Dimensions* = 2, *Interactable* alternates between *on*/*off* state</span></span>
* <span data-ttu-id="91341-173">**Várias dimensões**  -  *Dimensions* >= 3, cada clique aumenta o nível de dimensão atual + 1.</span><span class="sxs-lookup"><span data-stu-id="91341-173">**Multi-dimension** - *Dimensions* >= 3, every click increases the current dimension level + 1.</span></span> <span data-ttu-id="91341-174">Útil para definir um estado de botão para uma lista, etc.</span><span class="sxs-lookup"><span data-stu-id="91341-174">Useful for defining a button state to a list, etc.</span></span>

<span data-ttu-id="91341-175">*Interagir* também permite que vários temas sejam definidos por *dimensão*.</span><span class="sxs-lookup"><span data-stu-id="91341-175">*Interactable* also allows for multiple Themes to be defined per *Dimension*.</span></span> <span data-ttu-id="91341-176">Por exemplo, quando *SelectionMode = Toggle*, um tema pode ser aplicado quando o *interagir* é *desmarcado* e outro tema aplicado quando o componente é *selecionado*.</span><span class="sxs-lookup"><span data-stu-id="91341-176">For example when *SelectionMode=Toggle*, one theme may be applied when the *Interactable* is *deselected* and another theme applied when the component is *selected*.</span></span>

<span data-ttu-id="91341-177">O modo de seleção atual pode ser consultado em tempo de execução via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) .</span><span class="sxs-lookup"><span data-stu-id="91341-177">The current Selection Mode can be queried at runtime via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode).</span></span> <span data-ttu-id="91341-178">A atualização do modo em tempo de execução pode ser obtida definindo a  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) propriedade para corresponder à funcionalidade desejada.</span><span class="sxs-lookup"><span data-stu-id="91341-178">Updating the mode at runtime can be achieved by setting the  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) property to match the desired functionality.</span></span> <span data-ttu-id="91341-179">Além disso, a dimensão atual, útil para *alternar* e modos de *várias dimensões* , pode ser acessada via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) .</span><span class="sxs-lookup"><span data-stu-id="91341-179">Furthermore, the current dimension, useful for *Toggle* and *Multi-Dimension* modes, can be accessed via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension).</span></span>

### <a name="interactable-profiles"></a><span data-ttu-id="91341-180">Perfis de interação</span><span class="sxs-lookup"><span data-stu-id="91341-180">Interactable profiles</span></span>

<span data-ttu-id="91341-181">*Perfis* são itens que criam uma relação entre um gameobject e um [tema Visual](visual-themes.md).</span><span class="sxs-lookup"><span data-stu-id="91341-181">*Profiles* are items that create a relationship between a GameObject and a [Visual Theme](visual-themes.md).</span></span> <span data-ttu-id="91341-182">O perfil define qual conteúdo será manipulado por um tema quando ocorrer uma [alteração de estado](#general-input-settings).</span><span class="sxs-lookup"><span data-stu-id="91341-182">The profile defines what content will be manipulated by a theme when a [state change occurs](#general-input-settings).</span></span>

<span data-ttu-id="91341-183">Os temas funcionam muito parecidos com materiais.</span><span class="sxs-lookup"><span data-stu-id="91341-183">Themes work a lot like materials.</span></span> <span data-ttu-id="91341-184">Eles são objetos programáveis que contêm uma lista de propriedades que serão atribuídas a um objeto com base no estado atual.</span><span class="sxs-lookup"><span data-stu-id="91341-184">They are scriptable objects that contain a list of properties that will be assigned to an object based on the current state.</span></span> <span data-ttu-id="91341-185">Os temas também são reutilizáveis e podem ser atribuídos em vários objetos UX *interagindo* .</span><span class="sxs-lookup"><span data-stu-id="91341-185">Themes are also re-usable and can be assigned across multiple *Interactable* UX objects.</span></span>

<span data-ttu-id="91341-186">**Redefinir em destruir**</span><span class="sxs-lookup"><span data-stu-id="91341-186">**Reset On Destroy**</span></span>

<span data-ttu-id="91341-187">Os temas visuais modificam várias propriedades em um gameobject direcionado, dependendo da classe e do tipo de mecanismo de tema selecionado.</span><span class="sxs-lookup"><span data-stu-id="91341-187">Visual themes modify various properties on a targeted GameObject, dependent on the class and type of theme engine selected.</span></span> <span data-ttu-id="91341-188">Se *Redefinir em Destroy* for verdadeiro quando o componente interagindo for destruído, o componente redefinirá todas as propriedades modificadas de temas ativos para seus valores originais.</span><span class="sxs-lookup"><span data-stu-id="91341-188">If *Reset On Destroy* is true when the Interactable component is destroyed, the component will reset all modified properties from active themes to their original values.</span></span> <span data-ttu-id="91341-189">Caso contrário, quando destruído, o componente que poderá interagir deixará todas as propriedades modificadas como estão.</span><span class="sxs-lookup"><span data-stu-id="91341-189">Otherwise, when destroyed, the Interactable component will leave any modified properties as-is.</span></span> <span data-ttu-id="91341-190">Nesse último caso, o último estado dos valores persistirá, a menos que seja alterado por outro componente externo.</span><span class="sxs-lookup"><span data-stu-id="91341-190">In this latter case, the last state of values will persist unless altered by another external component.</span></span> <span data-ttu-id="91341-191">O padrão é falso.</span><span class="sxs-lookup"><span data-stu-id="91341-191">The default is false.</span></span>

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a><span data-ttu-id="91341-192">Eventos</span><span class="sxs-lookup"><span data-stu-id="91341-192">Events</span></span>

<span data-ttu-id="91341-193">Cada componente que *interage* tem um evento *onclick* que é acionado quando o componente é simplesmente selecionado.</span><span class="sxs-lookup"><span data-stu-id="91341-193">Every *Interactable* component has an *OnClick* event that fires when the component is simply selected.</span></span> <span data-ttu-id="91341-194">No entanto, *interagir* pode ser usado para detectar eventos de entrada que não sejam apenas *onclick*.</span><span class="sxs-lookup"><span data-stu-id="91341-194">However, *Interactable* can be used to detect input events other than just *OnClick*.</span></span>

<span data-ttu-id="91341-195">Clique no botão *Adicionar evento* para adicionar um novo tipo de definição de receptor de evento.</span><span class="sxs-lookup"><span data-stu-id="91341-195">Click the *Add Event* button to add a new type of Event Receiver definition.</span></span> <span data-ttu-id="91341-196">Depois de adicionado, selecione o tipo de evento desejado.</span><span class="sxs-lookup"><span data-stu-id="91341-196">Once added, select the type of Event desired.</span></span>

![Exemplo de eventos](../images/interactable/Events.png)<span data-ttu-id="91341-198">)</span><span class="sxs-lookup"><span data-stu-id="91341-198">)</span></span>

<span data-ttu-id="91341-199">Há diferentes tipos de receptores de eventos para responder a diferentes tipos de entrada.</span><span class="sxs-lookup"><span data-stu-id="91341-199">There are different types of event receivers to respond to different types of input.</span></span> <span data-ttu-id="91341-200">O MRTK é fornecido com o seguinte conjunto de receptores prontos para uso.</span><span class="sxs-lookup"><span data-stu-id="91341-200">MRTK ships with the following set of receivers out-of-box.</span></span>

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

<span data-ttu-id="91341-201">Um receptor personalizado pode ser criado criando-se uma nova classe que se estende [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) .</span><span class="sxs-lookup"><span data-stu-id="91341-201">A custom receiver can be created by making a new class that extends [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase).</span></span>

![Exemplo de receptor de alternância de eventos](../images/interactable/Event_toggle.png)

<span data-ttu-id="91341-203">*Exemplo de um receptor de evento de alternância*</span><span class="sxs-lookup"><span data-stu-id="91341-203">*Example of a Toggle Event Receiver*</span></span>

### <a name="interactable-receivers"></a><span data-ttu-id="91341-204">Receptores interagir</span><span class="sxs-lookup"><span data-stu-id="91341-204">Interactable receivers</span></span>

 <span data-ttu-id="91341-205">O [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) componente permite que os eventos sejam definidos fora do componente de origem *interagir* .</span><span class="sxs-lookup"><span data-stu-id="91341-205">The [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) component allows for events to be defined outside of the source *Interactable* component.</span></span> <span data-ttu-id="91341-206">O *InteractableReceiver* escutará um tipo de evento filtrado disparado por outro *interagir*.</span><span class="sxs-lookup"><span data-stu-id="91341-206">The *InteractableReceiver* will listen for a filtered event type fired by another *Interactable*.</span></span> <span data-ttu-id="91341-207">Se a propriedade *interagir* não for atribuída diretamente, a propriedade *escopo da pesquisa* definirá a direção que o *InteractableReceiver* escutará por eventos que estejam em si, em um pai ou em um gameobject filho.</span><span class="sxs-lookup"><span data-stu-id="91341-207">If the *Interactable* property is not directly assigned, then the *Search Scope* property defines the direction the *InteractableReceiver* listens for events which is either on itself, in a parent, or in a child GameObject.</span></span>

<span data-ttu-id="91341-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) age de maneira semelhante, mas para obter uma lista de eventos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="91341-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) acts in a similar fashion but for a list of matching events.</span></span>

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a><span data-ttu-id="91341-209">Criar eventos personalizados</span><span class="sxs-lookup"><span data-stu-id="91341-209">Create custom events</span></span>

<span data-ttu-id="91341-210">Como os [temas visuais](visual-themes.md#custom-theme-engines), os eventos podem ser estendidos para detectar qualquer padrão de estado ou para expor a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="91341-210">Like [Visual Themes](visual-themes.md#custom-theme-engines), events can be extended to detect any state pattern or to expose functionality.</span></span>

<span data-ttu-id="91341-211">Os eventos personalizados podem ser criados de duas maneiras principais:</span><span class="sxs-lookup"><span data-stu-id="91341-211">Custom events can be created in two main ways:</span></span>

1) <span data-ttu-id="91341-212">Estenda a [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) classe para criar um evento personalizado que aparecerá na lista suspensa de tipos de eventos.</span><span class="sxs-lookup"><span data-stu-id="91341-212">Extend the [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) class to create a custom event that will show up in the dropdown list of event types.</span></span> <span data-ttu-id="91341-213">Um evento do Unity é fornecido por padrão, mas outros eventos do Unity podem ser adicionados ou o evento pode ser definido para ocultar eventos do Unity.</span><span class="sxs-lookup"><span data-stu-id="91341-213">A Unity event is provided by default, but additional Unity events can be added or the event can be set to hide Unity events.</span></span> <span data-ttu-id="91341-214">Essa funcionalidade permite que um designer trabalhe com um engenheiro em um projeto para criar um evento personalizado que o designer pode configurar no editor.</span><span class="sxs-lookup"><span data-stu-id="91341-214">This functionality allows a designer to work with an engineer on a project to create a custom event that the designer can setup in the editor.</span></span>

1) <span data-ttu-id="91341-215">Estenda a [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) classe para criar um componente de evento completamente personalizado que pode residir em um ou outro objeto que possa ser *interagindo* .</span><span class="sxs-lookup"><span data-stu-id="91341-215">Extend the [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) class to create a completely custom event component that can reside on the *Interactable* or another object.</span></span> <span data-ttu-id="91341-216">O [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) fará referência às alterações de estado que são *interagirs* para detectar.</span><span class="sxs-lookup"><span data-stu-id="91341-216">The [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) will reference the *Interactable* to detect state changes.</span></span>

#### <a name="example-of-extending-receiverbase"></a><span data-ttu-id="91341-217">Exemplo de extensão `ReceiverBase`</span><span class="sxs-lookup"><span data-stu-id="91341-217">Example of extending `ReceiverBase`</span></span>

<span data-ttu-id="91341-218">A [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) classe exibe informações de status sobre um *interagindo* e é um exemplo de como criar um receptor de evento personalizado.</span><span class="sxs-lookup"><span data-stu-id="91341-218">The [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) class displays status information about an *Interactable* and is an example of how to create a custom Event Receiver.</span></span>

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

<span data-ttu-id="91341-219">Os métodos a seguir são úteis para substituir/implementar ao criar um receptor de evento personalizado.</span><span class="sxs-lookup"><span data-stu-id="91341-219">The following methods are useful to override/implement when creating a custom Event Receiver.</span></span> <span data-ttu-id="91341-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) é um método abstrato que pode ser usado para detectar padrões/transições de estado.</span><span class="sxs-lookup"><span data-stu-id="91341-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) is an abstract method that can be used to detect state patterns/transitions.</span></span> <span data-ttu-id="91341-221">Além disso, [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) os [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) métodos e são úteis para a criação de lógica de evento Personalizada quando a *interação* é selecionada.</span><span class="sxs-lookup"><span data-stu-id="91341-221">Furthermore, the [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) and [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) methods are useful for creating custom event logic when the *Interactable* is selected.</span></span>

```c#
public override void OnUpdate(InteractableStates state, Interactable source)
{
    if (state.CurrentState() != lastState)
    {
        // the state has changed, do something new
        lastState = state.CurrentState();
        ...
    }
}

public virtual void OnVoiceCommand(InteractableStates state, Interactable source,
                                    string command, int index = 0, int length = 1)
{
    base.OnVoiceCommand(state, source, command, index, length);
    // voice command called, perform some action
}  

public virtual void OnClick(InteractableStates state,
                            Interactable source,
                            IMixedRealityPointer pointer = null)
{
    base.OnClick(state, source);
    // click called, perform some action
}
```

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a><span data-ttu-id="91341-222">Exibindo campos de receptor de eventos personalizados no Inspetor</span><span class="sxs-lookup"><span data-stu-id="91341-222">Displaying custom event receiver fields in the inspector</span></span>

<span data-ttu-id="91341-223">Os scripts *ReceiverBase* usam [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) atributos para expor propriedades personalizadas no Inspetor.</span><span class="sxs-lookup"><span data-stu-id="91341-223">*ReceiverBase* scripts use [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) attributes to expose custom properties in the inspector.</span></span> <span data-ttu-id="91341-224">Aqui está um exemplo de Vector3, uma propriedade personalizada com dica de ferramenta e informações de rótulo.</span><span class="sxs-lookup"><span data-stu-id="91341-224">Here's an example of Vector3, a custom property with tooltip and label information.</span></span> <span data-ttu-id="91341-225">Essa propriedade será exibida como configurável no Inspetor quando um gameobject *interagindo* for selecionado e tiver o tipo de *receptor de evento* associado adicionado.</span><span class="sxs-lookup"><span data-stu-id="91341-225">This property will show up as configurable in the inspector when an *Interactable* GameObject is selected and has the associated *Event Receiver* type added.</span></span>

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a><span data-ttu-id="91341-226">Como usar o interagir</span><span class="sxs-lookup"><span data-stu-id="91341-226">How to use Interactable</span></span>

### <a name="building-a-simple-button"></a><span data-ttu-id="91341-227">Criando um botão simples</span><span class="sxs-lookup"><span data-stu-id="91341-227">Building a simple button</span></span>

<span data-ttu-id="91341-228">É possível criar um botão simples adicionando o componente *interagindo* a um gameobject configurado para receber eventos de entrada.</span><span class="sxs-lookup"><span data-stu-id="91341-228">One can create a simple button by adding the *Interactable* component to a GameObject that is configured to receive input events.</span></span> <span data-ttu-id="91341-229">Ele pode ter um colisor ou um filho para receber a entrada.</span><span class="sxs-lookup"><span data-stu-id="91341-229">It can have a collider on it or on a child to receive input.</span></span> <span data-ttu-id="91341-230">Se você estiver usando *interagir* com uma interface do usuário baseada em Gameobjects, ela deverá estar sob o gameobject do Canvas.</span><span class="sxs-lookup"><span data-stu-id="91341-230">If using *Interactable* with a Unity UI based GameObjects, it should be under the Canvas GameObject.</span></span>

<span data-ttu-id="91341-231">Dê o botão um passo além, criando um novo perfil, atribuindo o próprio gameobject e criando um novo tema.</span><span class="sxs-lookup"><span data-stu-id="91341-231">Take the button one step further, by creating a new profile, assigning the GameObject itself and creating a new theme.</span></span> <span data-ttu-id="91341-232">Além disso, use o evento *onclick* para fazer algo acontecer.</span><span class="sxs-lookup"><span data-stu-id="91341-232">Furthermore, use the *OnClick* event to make something happen.</span></span>

> [!NOTE]
> <span data-ttu-id="91341-233">Tornar um [botão pressionável](button.md) requer o [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) componente.</span><span class="sxs-lookup"><span data-stu-id="91341-233">Making a [button pressable](button.md) requires the [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) component.</span></span> <span data-ttu-id="91341-234">Além disso, o [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) componente é necessário para encaminhada eventos de impressão para o componente *interagindo* .</span><span class="sxs-lookup"><span data-stu-id="91341-234">Additionally, the [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) component is needed to funnel press events to the *Interactable* component.</span></span>

### <a name="creating-toggle-and-multi-dimension-buttons"></a><span data-ttu-id="91341-235">Criando botões de alternância e de várias dimensões</span><span class="sxs-lookup"><span data-stu-id="91341-235">Creating toggle and multi-dimension buttons</span></span>

#### <a name="toggle-button"></a><span data-ttu-id="91341-236">Botão de alternância</span><span class="sxs-lookup"><span data-stu-id="91341-236">Toggle button</span></span>

<span data-ttu-id="91341-237">Para tornar um botão alternado, altere o [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) campo para tipo `Toggle` .</span><span class="sxs-lookup"><span data-stu-id="91341-237">To make a button Toggle-able, change the [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) field to type `Toggle`.</span></span> <span data-ttu-id="91341-238">Na seção de *perfis* , um novo tema alternado é adicionado para cada perfil que é usado quando o *interagir* é alternado.</span><span class="sxs-lookup"><span data-stu-id="91341-238">In the *Profiles* section, a new toggled theme is added for each profile that is used when the *Interactable* is toggled on.</span></span>

<span data-ttu-id="91341-239">Enquanto o [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) é definido como Toggle, a caixa de seleção *isalternated* pode ser usada para definir o valor padrão do controle na inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="91341-239">While the [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) is set to Toggle, the *IsToggled* check box can be used to set the default value of the control at runtime initialization.</span></span>

<span data-ttu-id="91341-240">*CanSelect* significa que o *interagindo* pode ir de *desativado* para *ativado* enquanto o *CanDeselect* significa o inverso.</span><span class="sxs-lookup"><span data-stu-id="91341-240">*CanSelect* means the *Interactable* can go from *off* to *on* while the *CanDeselect* means the inverse.</span></span>

![Exemplo de temas visuais de alternância de perfil](../images/interactable/Profile_toggle.png)

<span data-ttu-id="91341-242">Os desenvolvedores podem utilizar [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) as [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces e para obter/definir o estado de alternância de um *interagindo* por meio de código.</span><span class="sxs-lookup"><span data-stu-id="91341-242">Developers can utilize the [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) and [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces to get/set the toggle state of an *Interactable* via code.</span></span>

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a><span data-ttu-id="91341-243">Alternar coleção de botões</span><span class="sxs-lookup"><span data-stu-id="91341-243">Toggle button collection</span></span>

<span data-ttu-id="91341-244">É comum ter uma lista de botões de alternância em que apenas um pode estar ativo em um determinado momento, também conhecido como um conjunto radial ou botões de opção, etc.</span><span class="sxs-lookup"><span data-stu-id="91341-244">It is common to have a list of toggle buttons where only one can be active at any given time, also known as a radial set or radio buttons etc.</span></span>

<span data-ttu-id="91341-245">Use o [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) componente para habilitar essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="91341-245">Use the [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) component to enable this functionality.</span></span> <span data-ttu-id="91341-246">Esse controle garante que apenas um *interagir* seja alternado em um determinado momento.</span><span class="sxs-lookup"><span data-stu-id="91341-246">This control ensures only one *Interactable* is toggled on at any given time.</span></span> <span data-ttu-id="91341-247">O *radialset* (assets/MRTK/SDK/Features/UX/interajable/pré-fabricados/radialset. pré-fabricado) também é um ótimo ponto de partida pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="91341-247">The *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) is also a great starting point out-of-box.</span></span>

<span data-ttu-id="91341-248">Para criar um grupo de botões radiais personalizado:</span><span class="sxs-lookup"><span data-stu-id="91341-248">To create a custom radial button group:</span></span>

1) <span data-ttu-id="91341-249">Criar vários botões/Gameobjects *interagir*</span><span class="sxs-lookup"><span data-stu-id="91341-249">Create multiple *Interactable* GameObjects/buttons</span></span>
1) <span data-ttu-id="91341-250">Defina cada *interação* com *SelectionMode* = Toggle, *CanSelect* = true e *CanDeselect* = false</span><span class="sxs-lookup"><span data-stu-id="91341-250">Set each *Interactable* with *SelectionMode* = Toggle, *CanSelect* = true, and *CanDeselect* = false</span></span>
1) <span data-ttu-id="91341-251">Criar um gameobject pai vazio em todos os *Interactables* e adicionar o componente *InteractableToggleCollection*</span><span class="sxs-lookup"><span data-stu-id="91341-251">Create an empty parent GameObject over all the *Interactables* and add the *InteractableToggleCollection* component</span></span>
1) <span data-ttu-id="91341-252">Adicionar todos os *Interactables* à barra de *alternância* no *InteractableToggleCollection*</span><span class="sxs-lookup"><span data-stu-id="91341-252">Add all *Interactables* to the *ToggleList* on the *InteractableToggleCollection*</span></span>
1) <span data-ttu-id="91341-253">Defina a propriedade *InteractableToggleCollection. CurrentIndex* para determinar qual botão está selecionado por padrão no início</span><span class="sxs-lookup"><span data-stu-id="91341-253">Set the *InteractableToggleCollection.CurrentIndex* property to determine which button is selected by default at start</span></span>

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a><span data-ttu-id="91341-254">Botão multidimensional</span><span class="sxs-lookup"><span data-stu-id="91341-254">Multi-dimensional button</span></span>

<span data-ttu-id="91341-255">O modo de seleção de várias dimensões é usado para criar botões sequenciais ou um botão que tem mais de duas etapas, como controlar a velocidade com três valores, rápido (1x), mais rápido (2x) ou mais rápido (3x).</span><span class="sxs-lookup"><span data-stu-id="91341-255">Multi-Dimension selection mode is used to create sequential buttons, or a button that has more than two steps, like controlling speed with three values, Fast (1x), Faster (2x) or Fastest (3x).</span></span>

<span data-ttu-id="91341-256">Com as dimensões sendo um valor numérico, podem ser adicionadas até 9 temas para controlar o rótulo de texto ou a textura do botão para cada configuração de velocidade, usando um tema diferente para cada etapa.</span><span class="sxs-lookup"><span data-stu-id="91341-256">With dimensions being a numeric value, up to 9 themes can be added to control the text label or texture of the button for each speed setting, using a different theme for each of step.</span></span>

<span data-ttu-id="91341-257">Cada evento de clique avançará em `DimensionIndex` 1 em tempo de execução até que o `Dimensions` valor seja atingido.</span><span class="sxs-lookup"><span data-stu-id="91341-257">Every click event will advance the `DimensionIndex` by 1 at runtime until the `Dimensions` value is reached.</span></span> <span data-ttu-id="91341-258">Em seguida, o ciclo será redefinido como 0.</span><span class="sxs-lookup"><span data-stu-id="91341-258">Then the cycle will reset to 0.</span></span>

![Exemplo de perfil multidimensional](../images/interactable/Profile_multiDimensions.png)

<span data-ttu-id="91341-260">Os desenvolvedores podem avaliar o [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) para determinar qual dimensão está ativa no momento.</span><span class="sxs-lookup"><span data-stu-id="91341-260">Developers can assess the [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) to determine which dimension is currently active.</span></span>

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a><span data-ttu-id="91341-261">Criar interagindo em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="91341-261">Create Interactable at runtime</span></span>

<span data-ttu-id="91341-262">O *interagir* pode ser facilmente adicionado a qualquer gameobject no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="91341-262">*Interactable* can be easily added to any GameObject at runtime.</span></span> <span data-ttu-id="91341-263">O exemplo a seguir demonstra como atribuir um perfil com um [tema Visual](visual-themes.md).</span><span class="sxs-lookup"><span data-stu-id="91341-263">The following example demonstrates how to assign a profile with a [visual theme](visual-themes.md).</span></span>

```c#
var interactableObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
var interactable = interactableObject.AddComponent<Interactable>();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

interactable.Profiles = new List<InteractableProfileItem>()
{
    new InteractableProfileItem()
    {
        Themes = new List<Theme>()
        {
            Interactable.GetDefaultThemeAsset(new List<ThemeDefinition>() { newThemeType })
        },
        Target = interactableObject,
    },
};

// Force the Interactable to be clicked
interactable.TriggerOnClick()
```

### <a name="interactable-events-via-code"></a><span data-ttu-id="91341-264">Eventos de interação via código</span><span class="sxs-lookup"><span data-stu-id="91341-264">Interactable events via code</span></span>

<span data-ttu-id="91341-265">É possível adicionar uma ação ao evento base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) por meio de código com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="91341-265">One can add an action to the base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) event via code with the following example.</span></span>

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

<span data-ttu-id="91341-266">Use a [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) função para adicionar receptores de eventos dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="91341-266">Use the [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) function to add event receivers dynamically at runtime.</span></span>

<span data-ttu-id="91341-267">O código de exemplo abaixo demonstra como adicionar um [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), que escuta o foco entrar/sair e, além disso, define o código de ação a ser executado quando as instâncias de evento são acionadas.</span><span class="sxs-lookup"><span data-stu-id="91341-267">The example code below demonstrates how to add an [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for focus enter/exit, and furthermore define action code to perform when the event instances fire.</span></span>

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

<span data-ttu-id="91341-268">O código de exemplo abaixo demonstra como adicionar um [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), que escuta as transições de estado selecionadas/desmarcadas em *Interactables* de alternância habilitada e, além disso, define o código de ação a ser executado quando as instâncias de evento são acionadas.</span><span class="sxs-lookup"><span data-stu-id="91341-268">The example code below demonstrates how to add an [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for selected/deselected state transitions on toggle-able *Interactables*, and furthermore defines action code to perform when the event instances fire.</span></span>

```c#
public static void AddToggleEvents(Interactable interactable)
{
    var toggleReceiver = interactable.AddReceiver<InteractableOnToggleReceiver>();

    // Make the interactable have toggle capability, from code.
    // In the gui editor it's much easier
    interactable.Dimensions = 2;
    interactable.CanSelect = true;
    interactable.CanDeselect  = true;

    toggleReceiver.OnSelect.AddListener(() => Debug.Log("Toggle selected"));
    toggleReceiver.OnDeselect.AddListener(() => Debug.Log("Toggle un-selected"));
}
```

## <a name="see-also"></a><span data-ttu-id="91341-269">Confira também</span><span class="sxs-lookup"><span data-stu-id="91341-269">See also</span></span>

* [<span data-ttu-id="91341-270">Temas visuais</span><span class="sxs-lookup"><span data-stu-id="91341-270">Visual Themes</span></span>](visual-themes.md)
* [<span data-ttu-id="91341-271">Ações de entrada</span><span class="sxs-lookup"><span data-stu-id="91341-271">Input Actions</span></span>](../input/input-actions.md)
* [<span data-ttu-id="91341-272">Comandos de fala</span><span class="sxs-lookup"><span data-stu-id="91341-272">Speech Commands</span></span>](../input/speech.md)
* [<span data-ttu-id="91341-273">Botões</span><span class="sxs-lookup"><span data-stu-id="91341-273">Buttons</span></span>](button.md)
* [<span data-ttu-id="91341-274">Sombreador padrão MRTK</span><span class="sxs-lookup"><span data-stu-id="91341-274">MRTK Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)
