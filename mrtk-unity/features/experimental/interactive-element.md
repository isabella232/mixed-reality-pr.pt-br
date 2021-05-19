---
title: Elemento interativo
description: Documentação de MRTK interativaelement
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, elemento interativo, interagir
ms.openlocfilehash: 65f518c53414d68d3a9d2093cb427140cc65560b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144763"
---
# <a name="interactive-element-experimental"></a><span data-ttu-id="5a3ce-104">Elemento interativo [experimental]</span><span class="sxs-lookup"><span data-stu-id="5a3ce-104">Interactive Element [Experimental]</span></span>

<span data-ttu-id="5a3ce-105">Um ponto de entrada centralizado simplificado para o sistema de entrada MRTK.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-105">A simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="5a3ce-106">Contém métodos de gerenciamento de estado, gerenciamento de eventos e a lógica de configuração de estado para os Estados de interação principal.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-106">Contains state management methods, event management and the state setting logic for Core Interaction States.</span></span>

<span data-ttu-id="5a3ce-107">O elemento interativo é um recurso experimental com suporte no Unity 2019,3 e como ele utiliza uma funcionalidade nova para o Unity 2019,3: [serializar referência](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span><span class="sxs-lookup"><span data-stu-id="5a3ce-107">Interactive Element is an experimental feature supported in Unity 2019.3 and up as it utilizes a capability new to Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span></span>

### <a name="interactive-element-inspector"></a><span data-ttu-id="5a3ce-108">Inspetor de elemento interativo</span><span class="sxs-lookup"><span data-stu-id="5a3ce-108">Interactive Element Inspector</span></span>

<span data-ttu-id="5a3ce-109">Durante o modo de reprodução, o Inspetor de elemento interativo fornece comentários visuais que indicam se o estado atual está ativo ou não.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-109">During play mode, the Interactive Element inspector provides visual feedback that indicates whether or not the current state is active.</span></span> <span data-ttu-id="5a3ce-110">Se um estado estiver ativo, ele será realçado com uma cor ciano.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-110">If a state is active, it will be highlighted with a cyan color.</span></span>  <span data-ttu-id="5a3ce-111">Se o estado não estiver ativo, a cor não será alterada.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-111">If the state is not active, the color is not changed.</span></span> <span data-ttu-id="5a3ce-112">Os números ao lado dos Estados no Inspetor são os valores de estado, se o estado estiver ativo, o valor será 1, se o estado não estiver ativo, o valor será 0.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-112">The numbers next to the states in the inspector are the state values, if the state is active then the value is 1, if the state is not active the value is 0.</span></span>

![Elemento interativo com interação de mão virtual](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a><span data-ttu-id="5a3ce-114">Estados principais</span><span class="sxs-lookup"><span data-stu-id="5a3ce-114">Core States</span></span>

<span data-ttu-id="5a3ce-115">O elemento interativo contém Estados principais e dá suporte à adição de [Estados personalizados](#custom-states).</span><span class="sxs-lookup"><span data-stu-id="5a3ce-115">Interactive Element contains core states and supports the addition of [custom states](#custom-states).</span></span>  <span data-ttu-id="5a3ce-116">Um estado de núcleo é aquele que já tem a lógica de configuração de estado definida em `BaseInteractiveElement` .</span><span class="sxs-lookup"><span data-stu-id="5a3ce-116">A core state is one that already has the state setting logic defined in `BaseInteractiveElement`.</span></span> <span data-ttu-id="5a3ce-117">A seguir está uma lista de Estados básicos controlados por entrada atuais:</span><span class="sxs-lookup"><span data-stu-id="5a3ce-117">The following is a list of the current input-driven core states:</span></span> 

### <a name="current-core-states"></a><span data-ttu-id="5a3ce-118">Estados principais atuais</span><span class="sxs-lookup"><span data-stu-id="5a3ce-118">Current Core States</span></span>

- [<span data-ttu-id="5a3ce-119">Padrão</span><span class="sxs-lookup"><span data-stu-id="5a3ce-119">Default</span></span>](#default-state) 

<span data-ttu-id="5a3ce-120">Estados principais de interação próxima e longe:</span><span class="sxs-lookup"><span data-stu-id="5a3ce-120">Near and Far Interaction Core States:</span></span>
- [<span data-ttu-id="5a3ce-121">Foco</span><span class="sxs-lookup"><span data-stu-id="5a3ce-121">Focus</span></span>](#focus-state) 

<span data-ttu-id="5a3ce-122">Estados principais de interação próxima:</span><span class="sxs-lookup"><span data-stu-id="5a3ce-122">Near Interaction Core States:</span></span>

- [<span data-ttu-id="5a3ce-123">Foco próximo</span><span class="sxs-lookup"><span data-stu-id="5a3ce-123">Focus Near</span></span>](#focus-near-state)
- [<span data-ttu-id="5a3ce-124">Tocar</span><span class="sxs-lookup"><span data-stu-id="5a3ce-124">Touch</span></span>](#touch-state)

<span data-ttu-id="5a3ce-125">Estados principais de interação distante:</span><span class="sxs-lookup"><span data-stu-id="5a3ce-125">Far Interaction Core States:</span></span>
- [<span data-ttu-id="5a3ce-126">Foco Distante</span><span class="sxs-lookup"><span data-stu-id="5a3ce-126">Focus Far</span></span>](#focus-far-state)
- [<span data-ttu-id="5a3ce-127">Selecione Distante</span><span class="sxs-lookup"><span data-stu-id="5a3ce-127">Select Far</span></span>](#select-far-state)

<span data-ttu-id="5a3ce-128">Outros estados principais:</span><span class="sxs-lookup"><span data-stu-id="5a3ce-128">Other Core States:</span></span>
- [<span data-ttu-id="5a3ce-129">Clicado</span><span class="sxs-lookup"><span data-stu-id="5a3ce-129">Clicked</span></span>](#clicked-state)
- [<span data-ttu-id="5a3ce-130">Alternar e alternar Para Desligar</span><span class="sxs-lookup"><span data-stu-id="5a3ce-130">Toggle On and Toggle Off</span></span>](#toggle-on-and-toggle-off-state)
- [<span data-ttu-id="5a3ce-131">Palavra-chave speech</span><span class="sxs-lookup"><span data-stu-id="5a3ce-131">Speech Keyword</span></span>](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a><span data-ttu-id="5a3ce-132">Como adicionar um estado principal por meio do Inspetor</span><span class="sxs-lookup"><span data-stu-id="5a3ce-132">How to Add a Core State via Inspector</span></span>

1. <span data-ttu-id="5a3ce-133">Navegue **até Adicionar Estado Principal** no inspetor do Elemento Interativo.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-133">Navigate to **Add Core State** in the inspector for Interactive Element.</span></span>

    ![Adicionar um estado principal por meio do Inspetor](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. <span data-ttu-id="5a3ce-135">Selecione o **botão Selecionar Estado** para escolher o estado principal a ser acrescentado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-135">Select the **Select State** button to choose the core state to add.</span></span> <span data-ttu-id="5a3ce-136">Os estados no menu são classificar por tipo de interação.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-136">The states in the menu are sorted by interaction type.</span></span>

    ![Adicionar um estado principal por meio do Inspetor com o estado selecionado](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. <span data-ttu-id="5a3ce-138">Abra o dobrado Configuração de Eventos para exibir os eventos e propriedades associados ao estado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-138">Open the Event Configuration foldout to view the events and properties associated with the state.</span></span>

    ![Adicionar um estado principal por meio do Inspetor com a configuração de evento](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a><span data-ttu-id="5a3ce-140">Como adicionar um estado principal por meio de script</span><span class="sxs-lookup"><span data-stu-id="5a3ce-140">How to Add a Core State via Script</span></span>

<span data-ttu-id="5a3ce-141">Use o `AddNewState(stateName)` método para adicionar um estado principal.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-141">Use the `AddNewState(stateName)` method to add a core state.</span></span> <span data-ttu-id="5a3ce-142">Para uma lista dos nomes de estado principais disponíveis, use `CoreInteractionState` a enum.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-142">For a list of the available core state names, use the `CoreInteractionState` enum.</span></span>

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a><span data-ttu-id="5a3ce-143">Estrutura interna de estados</span><span class="sxs-lookup"><span data-stu-id="5a3ce-143">States Internal Structure</span></span> 

<span data-ttu-id="5a3ce-144">Os estados no Elemento Interativo são do tipo `InteractionState` .</span><span class="sxs-lookup"><span data-stu-id="5a3ce-144">The states in Interactive Element are of type `InteractionState`.</span></span>  <span data-ttu-id="5a3ce-145">Um `InteractionState` contém as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="5a3ce-145">An `InteractionState` contains the following properties:</span></span>

- <span data-ttu-id="5a3ce-146">**Nome**: o nome do estado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-146">**Name**: The name of the state.</span></span>
- <span data-ttu-id="5a3ce-147">**Valor**: o valor de estado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-147">**Value**: The state value.</span></span>  <span data-ttu-id="5a3ce-148">Se o estado for on, o valor do estado será 1.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-148">If the state is on, the state value is 1.</span></span> <span data-ttu-id="5a3ce-149">Se o estado for off, o valor de estado será 0.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-149">If the state is off, the state value is 0.</span></span>
- <span data-ttu-id="5a3ce-150">**Ativo**: se o estado está ativo no momento.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-150">**Active**: Whether or not the state is currently active.</span></span> <span data-ttu-id="5a3ce-151">O valor da propriedade ativa é true quando o estado for on, false se o estado for off.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-151">The value for the Active property is true when the state is on, false if the state is off.</span></span> 
- <span data-ttu-id="5a3ce-152">**Tipo de interação**: o tipo de interação de um estado é o tipo de interação de que um estado é destinado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-152">**Interaction Type**: The Interaction Type of a state is the type of interaction a state is intended for.</span></span> 
  - <span data-ttu-id="5a3ce-153">`None`: Não oferece suporte a qualquer forma de interação de entrada.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-153">`None`: Does not support any form of input interaction.</span></span>
  - <span data-ttu-id="5a3ce-154">`Near`: Suporte a interação próxima.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-154">`Near`: Near interaction support.</span></span> <span data-ttu-id="5a3ce-155">A entrada é considerada próxima à interação quando uma mão articulada tem contato direto com outro objeto de jogo, ou seja, a posição da mão articulada está perto da posição do objeto de jogo no espaço de mundo.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-155">Input is considered near interaction when an articulated hand has direct contact with another game object, i.e. the position the articulated hand is close to the position of the game object in world space.</span></span>
  - <span data-ttu-id="5a3ce-156">`Far`: Suporte de interação distante.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-156">`Far`: Far interaction support.</span></span> <span data-ttu-id="5a3ce-157">A entrada é considerada longe da interação quando o contato direto com o objeto de jogo não é necessário.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-157">Input is considered far interaction when direct contact with the game object is not required.</span></span> <span data-ttu-id="5a3ce-158">Por exemplo, a entrada por meio do controlador Ray ou olhar é considerada uma entrada de interação distante.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-158">For example, input via controller ray or gaze is considered far interaction input.</span></span>
  - <span data-ttu-id="5a3ce-159">`NearAndFar`: Abrange o suporte à interação próxima e a extrema.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-159">`NearAndFar`: Encompasses both near and far interaction support.</span></span> 
  - <span data-ttu-id="5a3ce-160">`Other`: Suporte à interação independente de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-160">`Other`: Pointer independent interaction support.</span></span>
- <span data-ttu-id="5a3ce-161">**Configuração de evento**: a configuração de evento para um estado é o ponto de entrada do perfil de eventos serializados.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-161">**Event Configuration**: The event configuration for a state is the serialized events profile entry point.</span></span> 

<span data-ttu-id="5a3ce-162">Todas essas propriedades são definidas internamente no `State Manager` elemento interativo contido.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-162">All of these properties are set internally in the `State Manager` contained in Interactive Element.</span></span> <span data-ttu-id="5a3ce-163">Para a modificação de Estados, use os seguintes métodos auxiliares:</span><span class="sxs-lookup"><span data-stu-id="5a3ce-163">For modification of states use the following helper methods:</span></span>

<span data-ttu-id="5a3ce-164">**Métodos auxiliares de configuração de estado**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-164">**State Setting Helper Methods**</span></span>

```c# 
// Get the InteractionState
interactiveElement.GetState("StateName");

// Set a state value to 1/on
interactiveElement.SetStateOn("StateName");

// Set a state value to 0/off
interactiveElement.SetStateOff("StateName");

// Check if a state is present in the state list
interactiveElement.IsStatePresent("StateName");

// Check whether or not a state is active
interactiveElement.IsStateActive("StateName");

// Add a new state to the state list
interactiveElement.AddNewState("StateName");

// Remove a state from the state list
interactiveElement.RemoveState("StateName");
```

<span data-ttu-id="5a3ce-165">Obter a configuração de evento de um estado é específica para o próprio estado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-165">Getting the event configuration of a state is specific to the state itself.</span></span> <span data-ttu-id="5a3ce-166">Cada estado principal tem um tipo de configuração de evento específico que é descrito abaixo nas seções que descrevem cada estado principal.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-166">Each core state has a specific event configuration type which is outlined below under the sections describing each core state.</span></span>

<span data-ttu-id="5a3ce-167">Aqui está um exemplo generalizado de como obter a configuração de evento de um estado:</span><span class="sxs-lookup"><span data-stu-id="5a3ce-167">Here is a generalized example of getting a state's event configuration:</span></span>

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a><span data-ttu-id="5a3ce-168">Estado padrão</span><span class="sxs-lookup"><span data-stu-id="5a3ce-168">Default State</span></span>

<span data-ttu-id="5a3ce-169">O estado Padrão está sempre presente em um Elemento Interativo.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-169">The Default state is always present on an Interactive Element.</span></span>  <span data-ttu-id="5a3ce-170">Esse estado estará ativo somente quando todos os outros estados não estão ativos.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-170">This state will be active only when all other states are not active.</span></span>  <span data-ttu-id="5a3ce-171">Se qualquer outro estado se tornar ativo, o estado Padrão será definido como off internamente.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-171">If any other state becomes active, then the Default state will be set to off internally.</span></span> 

<span data-ttu-id="5a3ce-172">Um Elemento Interativo é inicializado com os estados Padrão e Foco presentes na lista de estados.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-172">An Interactive Element is initialized with the Default and Focus states present in the state list.</span></span> <span data-ttu-id="5a3ce-173">O estado Padrão sempre precisa estar presente na lista de estados.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-173">The Default state always needs to be present in the state list.</span></span> 

#### <a name="getting-default-state-events"></a><span data-ttu-id="5a3ce-174">Obter eventos de estado padrão</span><span class="sxs-lookup"><span data-stu-id="5a3ce-174">Getting Default State Events</span></span>

<span data-ttu-id="5a3ce-175">Tipo de configuração de evento para o Estado Padrão: `StateEvents`</span><span class="sxs-lookup"><span data-stu-id="5a3ce-175">Event configuration type for the Default State: `StateEvents`</span></span>

```c#
StateEvents defaultEvents = interactiveElement.GetStateEvents<StateEvents>("Default");

defaultEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State On");
});

defaultEvents.OnStateOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State Off");
});
```

### <a name="focus-state"></a><span data-ttu-id="5a3ce-176">Estado de foco</span><span class="sxs-lookup"><span data-stu-id="5a3ce-176">Focus State</span></span>

<span data-ttu-id="5a3ce-177">O estado de Foco é um estado de interação próximo e distante que pode ser pensado como a realidade misturada equivalente a focalizar.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-177">The Focus state is a near and far interaction state that can be thought of as the mixed reality equivalent to hover.</span></span> <span data-ttu-id="5a3ce-178">O fator de distinção entre a interação próxima e distante para o estado foco é o tipo de ponteiro ativo atual.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-178">The distinguishing factor between near and far interaction for the Focus state is the current active pointer type.</span></span>  <span data-ttu-id="5a3ce-179">Se o tipo de ponteiro para o estado De foco for o Ponteiro de Ponteiro, a interação será considerada quase interação.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-179">If the pointer type for the Focus state is the Poke Pointer, then the interaction is considered near interaction.</span></span>  <span data-ttu-id="5a3ce-180">Se o ponteiro primário não for o Ponteiro de Ponteiro de Ponteiro, a interação será considerada interação distante.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-180">If the primary pointer is not the Poke Pointer, then the interaction is considered far interaction.</span></span> <span data-ttu-id="5a3ce-181">O estado De foco está presente no Elemento Interativo por padrão.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-181">The Focus state is present in Interactive Element by default.</span></span>

<span data-ttu-id="5a3ce-182">**Comportamento do estado de foco** 
 ![ Estado de foco com interação de mão virtual](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-182">**Focus State Behavior**
![Focus state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span></span> 

<span data-ttu-id="5a3ce-183">**Inspetor de Estado de Foco** 
 ![ Estado de foco no Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-183">**Focus State Inspector**
![Focus state in the Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span></span>

#### <a name="getting-focus-state-events&quot;></a><span data-ttu-id=&quot;5a3ce-184&quot;>Obter eventos de estado de foco</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-184&quot;>Getting Focus State Events</span></span>

<span data-ttu-id=&quot;5a3ce-185&quot;>Tipo de configuração de evento para o Estado de Foco: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-185&quot;>Event configuration type for the Focus State: `FocusEvents`</span></span>

```c#
FocusEvents focusEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;Focus");

focusEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus On");
});

focusEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus Off");
});
```

#### <a name="focus-near-vs-focus-far-behavior"></a><span data-ttu-id="5a3ce-186">Foco próximo versus comportamento distante do foco</span><span class="sxs-lookup"><span data-stu-id="5a3ce-186">Focus Near vs Focus Far Behavior</span></span> 

![Concentre-se perto e longe da interação com a mão virtual](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a><span data-ttu-id="5a3ce-188">Foco próximo ao estado</span><span class="sxs-lookup"><span data-stu-id="5a3ce-188">Focus Near State</span></span>

<span data-ttu-id="5a3ce-189">O foco próximo do estado é definido quando um evento de foco é gerado e o ponteiro principal é o ponteiro de adseção, uma indicação de interação próxima.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-189">The Focus Near state is set when a focus event is raised and the primary pointer is the Poke pointer, an indication of near interaction.</span></span> 

<span data-ttu-id="5a3ce-190">**Focalizar comportamento** 
 ![ de estado próximo Foco próximo ao estado com interação virtual](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-190">**Focus Near State Behavior**
![Focus near state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span></span> 

<span data-ttu-id="5a3ce-191">**Foco próximo ao inspetor** 
 ![ de estado Foco próximo ao componente no Inspetor](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-191">**Focus Near State Inspector**
![Focus near component in the Inspector](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span></span>

#### <a name="getting-focusnear-state-events&quot;></a><span data-ttu-id=&quot;5a3ce-192&quot;>Obtendo eventos de estado FocusNear</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-192&quot;>Getting FocusNear State Events</span></span>

<span data-ttu-id=&quot;5a3ce-193&quot;>Tipo de configuração de evento para o estado FocusNear: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-193&quot;>Event configuration type for the FocusNear State: `FocusEvents`</span></span>

```c#
FocusEvents focusNearEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusNear");

focusNearEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus On");
});

focusNearEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus Off");
});
```

### <a name="focus-far-state"></a><span data-ttu-id="5a3ce-194">Estado distante do foco</span><span class="sxs-lookup"><span data-stu-id="5a3ce-194">Focus Far State</span></span>

<span data-ttu-id="5a3ce-195">O estado de foco é definido quando o ponteiro principal não é o ponteiro de enfrente.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-195">The Focus Far state is set when the primary pointer is not the Poke pointer.</span></span>  <span data-ttu-id="5a3ce-196">Por exemplo, o ponteiro de raio do controlador padrão e o ponteiro GGV (olhar, gesto, voz) são considerados ponteiros de interação distantes.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-196">For example, the default controller ray pointer and the GGV (Gaze, Gesture, Voice) pointer are considered far interaction pointers.</span></span>

<span data-ttu-id="5a3ce-197">Comportamento do estado **distante do foco** 
 ![ Estado de foco muito com interação virtual](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-197">**Focus Far State Behavior**
![Focus state far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span></span>

<span data-ttu-id="5a3ce-198">Inspetor de estado **distante do foco** 
 ![ Componente de foco no Inspetor](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-198">**Focus Far State Inspector**
![Focus far component in the Inspector](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span></span>

#### <a name="getting-focus-far-state-events&quot;></a><span data-ttu-id=&quot;5a3ce-199&quot;>Obtendo eventos de estado distante do foco</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-199&quot;>Getting Focus Far State Events</span></span>

<span data-ttu-id=&quot;5a3ce-200&quot;>Tipo de configuração de evento para o estado FocusFar: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-200&quot;>Event configuration type for the FocusFar State: `FocusEvents`</span></span>

```c#
FocusEvents focusFarEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusFar");

focusFarEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus On");
});

focusFarEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus Off");
});
```

### <a name="touch-state"></a><span data-ttu-id="5a3ce-201">Estado de toque</span><span class="sxs-lookup"><span data-stu-id="5a3ce-201">Touch State</span></span>

<span data-ttu-id="5a3ce-202">O estado de toque é um estado de interação próxima que é definido quando uma mão articulada toca o objeto diretamente.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-202">The Touch state is a near interaction state that is set when an articulated hand touches the object directly.</span></span>  <span data-ttu-id="5a3ce-203">Um toque direto significa que o dedo do índice da mão articulada está muito próximo da posição mundial do objeto.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-203">A direct touch means that the articulated hand's index finger is very close to the world position of the object.</span></span> <span data-ttu-id="5a3ce-204">Por padrão, um `NearInteractionTouchableVolume` componente é anexado ao objeto se o estado de toque for adicionado à lista de estado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-204">By default, a `NearInteractionTouchableVolume` component is attached to the object if the Touch state is added to the the state list.</span></span>  <span data-ttu-id="5a3ce-205">A presença de um  `NearInteractionTouchableVolume` `NearInteractionTouchable` componente ou é necessária para detectar eventos de toque.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-205">The presence of a  `NearInteractionTouchableVolume` or `NearInteractionTouchable` component is required for detecting Touch events.</span></span>  <span data-ttu-id="5a3ce-206">A diferença entre `NearInteractionTouchableVolume` e `NearInteractionTouchable` é que o `NearInteractionTouchableVolume` detecta um toque com base no colisor do objeto e `NearInteractionTouchable` detecta o toque em uma área definida de um plano.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-206">The difference between `NearInteractionTouchableVolume` and `NearInteractionTouchable` is that `NearInteractionTouchableVolume` detects a touch based on the collider of the object and `NearInteractionTouchable`detects touch within a defined area of a plane.</span></span>

<span data-ttu-id="5a3ce-207">**Comportamento do estado de toque** 
 ![ Estado de toque com interação de mão virtual](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-207">**Touch State Behavior**
![Touch state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span></span>

<span data-ttu-id="5a3ce-208">**Inspetor de Estado de Toque** 
 ![ Componente de estado de toque no Inspetor](../images/interactive-element/InEditor/TouchStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-208">**Touch State Inspector**
![Touch state component in the Inspector](../images/interactive-element/InEditor/TouchStateInspector.png)</span></span>

#### <a name="getting-touch-state-events&quot;></a><span data-ttu-id=&quot;5a3ce-209&quot;>Obter eventos de estado de toque</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-209&quot;>Getting Touch State Events</span></span>

<span data-ttu-id=&quot;5a3ce-210&quot;>Tipo de configuração de evento para o Estado de Toque: `TouchEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-210&quot;>Event configuration type for the Touch State: `TouchEvents`</span></span>

```c#
TouchEvents touchEvents = interactiveElement.GetStateEvents<TouchEvents>(&quot;Touch");

touchEvents.OnTouchStarted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Started");
});

touchEvents.OnTouchCompleted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Completed");
});

touchEvents.OnTouchUpdated.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Updated");
});
```

### <a name="select-far-state"></a><span data-ttu-id="5a3ce-211">Selecionar Estado Distante</span><span class="sxs-lookup"><span data-stu-id="5a3ce-211">Select Far State</span></span>

<span data-ttu-id="5a3ce-212">O estado Selecionar Longe é `IMixedRealityPointerHandler` a superfície.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-212">The Select Far state is the `IMixedRealityPointerHandler` surfaced.</span></span>  <span data-ttu-id="5a3ce-213">Esse estado é um estado de interação distante que detecta um clique de interação distante (toque de ar) e mantém o uso de ponteiros de interação distantes, como o ponteiro de raio do controlador padrão ou o ponteiro GGV.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-213">This state is a far interaction state that detects far interaction click (air-tap) and holds through the use of far interaction pointers such as the default controller ray pointer or the GGV pointer.</span></span>  <span data-ttu-id="5a3ce-214">O estado Selecionar Longe tem uma opção no dobramento de configuração de evento chamado `Global` .</span><span class="sxs-lookup"><span data-stu-id="5a3ce-214">The Select Far state has an option under the event configuration foldout named `Global`.</span></span> <span data-ttu-id="5a3ce-215">Se `Global` for true, o `IMixedRealityPointerHandler` será registrado como um manipulador de entrada global.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-215">If `Global` is true, then the `IMixedRealityPointerHandler` is registered as a global input handler.</span></span>  <span data-ttu-id="5a3ce-216">O foco em um objeto não é necessário para disparar eventos do sistema de entrada se um manipulador for registrado como global.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-216">Focus on an object is not required to trigger input system events if a handler is registered as global.</span></span>  <span data-ttu-id="5a3ce-217">Por exemplo, se um usuário quiser saber sempre que o gesto de toque no ar/seleção for executado, independentemente do objeto em foco, de definido `Global` como true.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-217">For example, if a user wants to know anytime the air-tap/select gesture is performed regardless of the object in focus, set `Global` to true.</span></span> 

<span data-ttu-id="5a3ce-218">**Selecionar Comportamento de Estado Distante** 
 ![ Selecionar distante com interação com a mão virtual](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-218">**Select Far State Behavior**
![Select far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span></span>

<span data-ttu-id="5a3ce-219">**Selecione Inspetor de Estado Distante** 
 ![ Selecione o componente distante no Inspetor](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-219">**Select Far State Inspector**
![Select far component in the Inspector](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span></span>

#### <a name="getting-select-far-state-events&quot;></a><span data-ttu-id=&quot;5a3ce-220&quot;>Obter eventos de estado selecionados</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-220&quot;>Getting Select Far State Events</span></span>

<span data-ttu-id=&quot;5a3ce-221&quot;>Tipo de configuração de evento para o estado SelectFar: `SelectFarEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-221&quot;>Event configuration type for the SelectFar State: `SelectFarEvents`</span></span>

```c#
SelectFarEvents selectFarEvents = interactiveElement.GetStateEvents<SelectFarEvents>(&quot;SelectFar");

selectFarEvents.OnSelectUp.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Up");
});

selectFarEvents.OnSelectDown.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Down");
});

selectFarEvents.OnSelectHold.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Hold");
});

selectFarEvents.OnSelectClicked.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Clicked");
});
```

### <a name="clicked-state"></a><span data-ttu-id="5a3ce-222">Estado clicado</span><span class="sxs-lookup"><span data-stu-id="5a3ce-222">Clicked State</span></span>

<span data-ttu-id="5a3ce-223">O estado Clicado é disparado por um clique de interação distante (Selecione o estado Distante) por padrão.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-223">The Clicked state is triggered by a far interaction click (Select Far state) by default.</span></span>  <span data-ttu-id="5a3ce-224">Esse estado é alternado internamente para , invoca o evento OnClicked e, em seguida, é imediatamente desligado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-224">This state is internally switched to on, invokes the OnClicked event and then is immediately switched to off.</span></span> 

> [!NOTE]
> <span data-ttu-id="5a3ce-225">Os comentários visuais no inspetor com base na atividade de estado não estão presentes para o estado Clicado porque ele é ligado e desligado imediatamente.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-225">The visual feedback in the inspector based on state activity is not present for the Clicked state because it is switched on and then off immediately.</span></span> 

<span data-ttu-id="5a3ce-226">**Comportamento de estado clicado** 
 ![ Estado clicado com interações de mão virtual](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-226">**Clicked State Behavior**
![Clicked state with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span></span>

<span data-ttu-id="5a3ce-227">Inspetor de estado **clicado** 
 ![ Clique no componente de estado no Inspetor](../images/interactive-element/InEditor/ClickedStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-227">**Clicked State Inspector**
![Click state component in the Inspector](../images/interactive-element/InEditor/ClickedStateInspector.png)</span></span>

<span data-ttu-id="5a3ce-228">**Exemplo de estado pressionado próximo e longe**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-228">**Near and Far Clicked State Example**</span></span>  
<span data-ttu-id="5a3ce-229">O estado clicado pode ser disparado por meio de pontos de entrada adicionais usando o `interactiveElement.TriggerClickedState()` método.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-229">The clicked state can be triggered through additional entry points using the `interactiveElement.TriggerClickedState()` method.</span></span>  <span data-ttu-id="5a3ce-230">Por exemplo, se um usuário quiser um toque próximo à interação para disparar um clique em um objeto também, ele adicionará o `TriggerClickedState()` método como um ouvinte no estado de toque.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-230">For example, if a user wants a near interaction touch to trigger a click on an object as well, then they would add the `TriggerClickedState()` method as a listener in the touch state.</span></span>   

![Estado próximo e distante com interações virtuais](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a><span data-ttu-id=&quot;5a3ce-232&quot;>Obtendo eventos de estado clicados</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-232&quot;>Getting Clicked State Events</span></span>

<span data-ttu-id=&quot;5a3ce-233&quot;>Tipo de configuração de evento para o estado clicado: `ClickedEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-233&quot;>Event configuration type for the Clicked State: `ClickedEvents`</span></span>

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a><span data-ttu-id="5a3ce-234">Ativar/desativar o estado</span><span class="sxs-lookup"><span data-stu-id="5a3ce-234">Toggle On and Toggle Off state</span></span>

<span data-ttu-id="5a3ce-235">Os Estados ativar/desativar e desligar são um par e ambos precisam estar presentes para o comportamento de alternância.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-235">The Toggle On and Toggle Off states are a pair and both need to be present for toggle behavior.</span></span>  <span data-ttu-id="5a3ce-236">Por padrão, os Estados de alternância e desativação são disparados por um clique de interação extrema (selecione estado distante).</span><span class="sxs-lookup"><span data-stu-id="5a3ce-236">By default, the Toggle On and Toggle Off states are triggered through a far interaction click (Select Far state).</span></span>  <span data-ttu-id="5a3ce-237">Por padrão, o estado de desativação está ativo no início, o que significa que a alternância será inicializada como desativado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-237">By default, the Toggle Off state is active on start, meaning that the toggle will be initialized to off.</span></span>  <span data-ttu-id="5a3ce-238">Se um usuário desejar que o estado de alternância esteja ativo no início, em seguida, no estado ativar/desativar definido `IsSelectedOnStart` como true.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-238">If a user wants the Toggle On state to be active on start, then in the Toggle On state set `IsSelectedOnStart` to true.</span></span>

<span data-ttu-id="5a3ce-239">**Alternar e desativar o comportamento** 
 ![ do estado Ativar e desativar com interações virtuais](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-239">**ToggleOn and Toggle Off State Behavior**
![Toggle on and off with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span></span>

<span data-ttu-id="5a3ce-240">**Alternar e desativar o Inspetor** 
 ![ de estado Ativar/desativar componente no Inspetor](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-240">**ToggleOn and Toggle Off State Inspector**
![Toggle component in the Inspector](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span></span>

<span data-ttu-id="5a3ce-241">**Exemplo de Estados de alternância Near e far**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-241">**Near and Far Toggle States Example**</span></span>  
<span data-ttu-id="5a3ce-242">Semelhante ao estado clicado, alternar configuração de estado pode ter vários pontos de entrada usando o `interactiveElement.SetToggleStates()` método.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-242">Similar to the Clicked state, toggle state setting can have multiple entry points using the `interactiveElement.SetToggleStates()` method.</span></span> <span data-ttu-id="5a3ce-243">Por exemplo, se um usuário quiser tocar como um ponto de entrada adicional para definir os Estados de alternância, ele adicionará o `SetToggleStates()` método a um dos eventos no estado de toque.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-243">For example, if a user wants touch as an additional entry point to set the toggle states, then they add the `SetToggleStates()` method to one of the events in the Touch state.</span></span> 

![Alternância próxima e longe com interações virtuais](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a><span data-ttu-id=&quot;5a3ce-245&quot;>Guia de alternância e desativação de eventos de estado</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-245&quot;>Getting Toggle On and Toggle Off State Events</span></span>

<span data-ttu-id=&quot;5a3ce-246&quot;>Tipo de configuração de evento para o estado de alternância: `ToggleOnEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-246&quot;>Event configuration type for the ToggleOn State: `ToggleOnEvents`</span></span>  
<span data-ttu-id=&quot;5a3ce-247&quot;>Tipo de configuração de evento para o estado ToggleOff: `ToggleOffEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-247&quot;>Event configuration type for the ToggleOff State: `ToggleOffEvents`</span></span>

```c#
// Toggle On Events
ToggleOnEvents toggleOnEvent = interactiveElement.GetStateEvents<ToggleOnEvents>(&quot;ToggleOn");

toggleOnEvent.OnToggleOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled On");
});

// Toggle Off Events
ToggleOffEvents toggleOffEvent = interactiveElement.GetStateEvents<ToggleOffEvents>("ToggleOff");

toggleOffEvent.OnToggleOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled Off");
});
```

### <a name="speech-keyword-state"></a><span data-ttu-id="5a3ce-248">Estado da palavra-chave speech</span><span class="sxs-lookup"><span data-stu-id="5a3ce-248">Speech Keyword State</span></span>

<span data-ttu-id="5a3ce-249">O estado palavra-chave de fala escuta as palavras-chave definidas no Perfil de Fala de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-249">The Speech Keyword state listens for the keywords defined in the Mixed Reality Speech Profile.</span></span> <span data-ttu-id="5a3ce-250">Qualquer nova palavra-chave DEVE ser registrada no perfil de comando de fala antes do runtime (etapas abaixo).</span><span class="sxs-lookup"><span data-stu-id="5a3ce-250">Any new keyword MUST be registered in the speech command profile prior to runtime (steps below).</span></span> 

<span data-ttu-id="5a3ce-251">**Comportamento de estado de palavra-chave de fala** 
 ![ Palavra-chave de fala com interação virtual](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-251">**Speech Keyword State Behavior**
![Speech keyword with virtual interaction](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span></span>

<span data-ttu-id="5a3ce-252">**Inspetor de Estado da Palavra-chave de Fala** 
 ![ Componente de palavra-chave de fala no Inspetor](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-252">**Speech Keyword State Inspector**
![Speech keyword component in the Inspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span></span>

> [!NOTE]
> <span data-ttu-id="5a3ce-253">O estado palavra-chave de fala foi disparado no editor pressionando a tecla F5 no gif acima.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-253">The Speech Keyword state was triggered in editor by pressing the F5 key in the gif above.</span></span> <span data-ttu-id="5a3ce-254">A configuração no teste do editor para fala é descrita nas etapas abaixo.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-254">Setting up in editor testing for speech is outlined the steps below.</span></span> 

#### <a name="how-to-register-a-speech-commandkeyword"></a><span data-ttu-id="5a3ce-255">Como registrar um comando/palavra-chave de fala</span><span class="sxs-lookup"><span data-stu-id="5a3ce-255">How to Register a Speech Command/Keyword</span></span>

1. <span data-ttu-id="5a3ce-256">Selecione o **objeto de jogo MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-256">Select the **MixedRealityToolkit** game object</span></span>

1. <span data-ttu-id="5a3ce-257">Selecione **Copiar e Personalizar** o perfil atual</span><span class="sxs-lookup"><span data-stu-id="5a3ce-257">Select **Copy and Customize** the current profile</span></span>

1. <span data-ttu-id="5a3ce-258">Navegue até a seção Entrada e selecione **Clonar** para habilitar a modificação do perfil de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a3ce-258">Navigate to the Input section and select **Clone** to enable modification of the Input profile</span></span>

1. <span data-ttu-id="5a3ce-259">Scroll down à seção Fala no perfil de Entrada e clonar o Perfil de Fala</span><span class="sxs-lookup"><span data-stu-id="5a3ce-259">Scroll down to the Speech section in the Input profile and clone the Speech Profile</span></span>

    ![Perfil de palavra-chave de fala no objeto de jogo do MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. <span data-ttu-id="5a3ce-261">Selecione Adicionar um Novo Comando de Fala</span><span class="sxs-lookup"><span data-stu-id="5a3ce-261">Select Add a New Speech Command</span></span>

    ![Adicionando uma nova palavra-chave de fala no perfil do MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. <span data-ttu-id="5a3ce-263">Insira a nova palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-263">Enter the new keyword.</span></span> <span data-ttu-id="5a3ce-264">Opcional: altere o KeyCode para F5 (ou outro KeyCode) para permitir testes no editor.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-264">Optional: Change the KeyCode to F5 (or another KeyCode) to allow for testing in editor.</span></span> 

    ![Configurando a palavra-chave de fala no perfil do MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. <span data-ttu-id="5a3ce-266">Go back ao inspetor de estado palavra-chave de fala do elemento interativo e selecione **Adicionar Palavra-chave**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-266">Go back to the Interactive Element Speech Keyword state inspector and select **Add Keyword**</span></span> 

    ![Adicionando palavra-chave ao componente de elemento interativo](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![Validação e registro de palavra-chave](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. <span data-ttu-id="5a3ce-269">Insira a nova palavra-chave que acabou de ser registrada no perfil de fala</span><span class="sxs-lookup"><span data-stu-id="5a3ce-269">Enter the new keyword that was just registered in the Speech Profile</span></span>

    ![Inserindo nova palavra-chave de fala](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


<span data-ttu-id="5a3ce-271">Para testar o estado da palavra-chave Speech no editor, pressione o código de tecla que foi definido na etapa 6 (F5) para simular o evento reconhecido da palavra-chave de fala.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-271">To test the Speech Keyword state in editor, press the KeyCode that was defined in step 6 (F5) to simulate the speech keyword recognized event.</span></span>

#### <a name="getting-speech-keyword-state-events"></a><span data-ttu-id="5a3ce-272">Obtendo eventos de estado de palavra-chave de fala</span><span class="sxs-lookup"><span data-stu-id="5a3ce-272">Getting Speech Keyword State Events</span></span>

<span data-ttu-id="5a3ce-273">Tipo de configuração de evento para o estado SpeechKeyword: `SpeechKeywordEvents`</span><span class="sxs-lookup"><span data-stu-id="5a3ce-273">Event configuration type for the SpeechKeyword State: `SpeechKeywordEvents`</span></span>

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>("SpeechKeyword");

speechKeywordEvents.OnAnySpeechKeywordRecognized.AddListener((speechEventData) =>
{
    Debug.Log($"{speechEventData.Command.Keyword} recognized");
});

// Get the "Change" Keyword event specifically
KeywordEvent keywordEvent = speechKeywordEvents.Keywords.Find((keyword) => keyword.Keyword == "Change");

keywordEvent.OnKeywordRecognized.AddListener(() =>
{ 
    Debug.Log("Change Keyword Recognized"); 
});
```

## <a name="custom-states"></a><span data-ttu-id="5a3ce-274">Estados personalizados</span><span class="sxs-lookup"><span data-stu-id="5a3ce-274">Custom States</span></span>

### <a name="how-to-create-a-custom-state-via-inspector"></a><span data-ttu-id="5a3ce-275">Como criar um estado personalizado por meio do Inspetor</span><span class="sxs-lookup"><span data-stu-id="5a3ce-275">How to Create a Custom State via Inspector</span></span> 

<span data-ttu-id="5a3ce-276">O estado personalizado criado via inspector será inicializado com a configuração de evento de estado padrão.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-276">The custom state created via inspector will be initialized with the default state event configuration.</span></span> <span data-ttu-id="5a3ce-277">A configuração de evento padrão para um estado personalizado é do tipo `StateEvents` e contém os eventos Onstatee e OnStateOff.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-277">The default event configuration for a custom state is of type `StateEvents` and contains the OnStateOn and OnStateOff events.</span></span>

1. <span data-ttu-id="5a3ce-278">Navegue até **criar estado personalizado** no Inspetor para elemento interativo.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-278">Navigate to **Create Custom State** in the inspector for Interactive Element.</span></span>
    
    ![Criando um estado personalizado](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. <span data-ttu-id="5a3ce-280">Insira o nome do novo estado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-280">Enter the name of the new state.</span></span> <span data-ttu-id="5a3ce-281">Esse nome deve ser exclusivo e não pode ser o mesmo que os Estados principais existentes.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-281">This name must be unique and cannot be the same as the existing core states.</span></span> 
    
    ![Inserindo o nome de um novo estado personalizado](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. <span data-ttu-id="5a3ce-283">Selecione **definir nome do estado** para adicionar à lista de estado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-283">Select **Set State Name** to add to the state list.</span></span>
    
    ![Adicionar estado personalizado à lista de estado](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   <span data-ttu-id="5a3ce-285">Esse estado personalizado é inicializado com a `StateEvents` configuração de evento padrão que contém os `OnStateOn` `OnStateOff` eventos e.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-285">This custom state is initialized with the default `StateEvents` event configuration which contains the `OnStateOn` and `OnStateOff` events.</span></span> <span data-ttu-id="5a3ce-286">Para criar uma configuração de evento personalizado para um novo estado, consulte: [criando um estado personalizado com uma configuração de evento personalizado](#creating-a-custom-state-with-a-custom-event-configuration).</span><span class="sxs-lookup"><span data-stu-id="5a3ce-286">To create a custom event configuration for a new state see: [Creating a Custom State with a Custom Event Configuration](#creating-a-custom-state-with-a-custom-event-configuration).</span></span>
    
    ![Novo estado mostrado no componente de elemento interativo](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a><span data-ttu-id=&quot;5a3ce-288&quot;>Como criar um estado personalizado por meio de script</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;5a3ce-288&quot;>How to Create a Custom State via Script</span></span>

```c#
interactiveElement.AddNewState(&quot;MyNewState");

// A new state by default is initialized with a the default StateEvents configuration which contains the 
// OnStateOn and OnStateOff events

StateEvents myNewStateEvents = interactiveElement.GetStateEvents<StateEvents>("MyNewState");

myNewStateEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"MyNewState is On");
});

```

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a><span data-ttu-id="5a3ce-289">Criando um estado personalizado com uma configuração de evento personalizado</span><span class="sxs-lookup"><span data-stu-id="5a3ce-289">Creating a Custom State with a Custom Event Configuration</span></span> 

<span data-ttu-id="5a3ce-290">Os arquivos de exemplo para um estado personalizado chamado **Keyboard** estão localizados aqui: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span><span class="sxs-lookup"><span data-stu-id="5a3ce-290">Example files for a custom state named **Keyboard** are located here: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span></span>

<span data-ttu-id="5a3ce-291">As etapas a seguir percorrem um exemplo existente de criação de uma configuração de evento de estado personalizado e arquivos de receptor.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-291">The following steps walk through an existing example of creating a custom state event configuration and receiver files.</span></span>

1. <span data-ttu-id="5a3ce-292">Considere um nome de estado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-292">Think of a state name.</span></span>  <span data-ttu-id="5a3ce-293">Esse nome deve ser exclusivo e não pode ser o mesmo que os Estados principais existentes.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-293">This name must be unique and cannot be the same as the existing core states.</span></span> <span data-ttu-id="5a3ce-294">Para os fins deste exemplo, o nome do estado será **teclado**.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-294">For the purposes of this example, the state name is going to be **Keyboard**.</span></span>

1. <span data-ttu-id="5a3ce-295">Crie dois arquivos. cs chamados nome do estado + "receptor" e nome do estado + "eventos".</span><span class="sxs-lookup"><span data-stu-id="5a3ce-295">Create two .cs files named state name + "Receiver" and state name + "Events".</span></span> <span data-ttu-id="5a3ce-296">A nomenclatura desses arquivos é levada em consideração internamente e deve seguir o nome do estado + Convenção do evento/receptor.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-296">The naming of these files are taken into consideration internally and must follow the state name + Event/Receiver convention.</span></span> 

    ![Scripts de estado do teclado](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. <span data-ttu-id="5a3ce-298">Consulte os arquivos KeyboardEvents. cs e KeyboardReceiver. cs para obter mais detalhes sobre o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-298">See the KeyboardEvents.cs and KeyboardReceiver.cs files for more details on file contents.</span></span> <span data-ttu-id="5a3ce-299">Novas classes de configuração de evento devem herdar de `BaseInteractionEventConfiguration` e novas classes de receptor de eventos devem herdar de `BaseEventReceiver` .</span><span class="sxs-lookup"><span data-stu-id="5a3ce-299">New event configuration classes must inherit from `BaseInteractionEventConfiguration` and new event receiver classes must inherit from `BaseEventReceiver`.</span></span>  <span data-ttu-id="5a3ce-300">Os exemplos na configuração de estado do estado do teclado estão localizados no `CustomStateSettingExample.cs` arquivo.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-300">Examples on state setting for the Keyboard state are located in the `CustomStateSettingExample.cs` file.</span></span> 

1. <span data-ttu-id="5a3ce-301">Adicione o estado ao elemento interativo usando o nome do estado, o nome do estado será reconhecido se existirem arquivos de configuração de evento e receptor de evento.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-301">Add the state to Interactive Element using the state name, the state name will be recognized if event configuration and event receiver files exist.</span></span>  <span data-ttu-id="5a3ce-302">As propriedades no arquivo de configuração de evento personalizado devem aparecer no Inspetor.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-302">The properties in the custom event configuration file should appear in the inspector.</span></span>

    <span data-ttu-id="5a3ce-303">![Adicionando estado personalizado ao elemento interativo ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ estado personalizado reconhecido no elemento interativo](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span><span class="sxs-lookup"><span data-stu-id="5a3ce-303">![Adding custom state to interactive element](../images/interactive-element/InEditor/AddKeyboardState.png) ![Custom state recognized in the interactive element](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span></span>


1. <span data-ttu-id="5a3ce-304">Para obter mais exemplos de configuração de evento e de arquivos receptor de eventos, consulte os arquivos nestes caminhos:</span><span class="sxs-lookup"><span data-stu-id="5a3ce-304">For more examples of event configuration and event receiver files see the files at these paths:</span></span>    
- <span data-ttu-id="5a3ce-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span><span class="sxs-lookup"><span data-stu-id="5a3ce-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span></span>
- <span data-ttu-id="5a3ce-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span><span class="sxs-lookup"><span data-stu-id="5a3ce-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span></span>

## <a name="example-scene"></a><span data-ttu-id="5a3ce-307">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="5a3ce-307">Example Scene</span></span> 

<span data-ttu-id="5a3ce-308">A cena de exemplo para elemento interativo + Visualizador de estado está localizada aqui: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span><span class="sxs-lookup"><span data-stu-id="5a3ce-308">The example scene for Interactive Element + State Visualizer is located here: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span></span>

![Cena de exemplo com elemento interativo e visualizador de estado](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a><span data-ttu-id="5a3ce-310">Botão compactável</span><span class="sxs-lookup"><span data-stu-id="5a3ce-310">Compressable Button</span></span>

<span data-ttu-id="5a3ce-311">A cena de exemplo contém pré-fabricados nomeado `CompressableButton` e `CompressableButtonToggle` , esses pré-fabricados espelham o comportamento dos `PressableButtonHoloLens2` botões, que são construídos usando o elemento interativo e o Visualizador de estado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-311">The example scene contains prefabs named `CompressableButton` and `CompressableButtonToggle`, these prefabs mirror the behavior of the `PressableButtonHoloLens2` buttons, that are constructed using Interactive Element and the State Visualizer.</span></span> <span data-ttu-id="5a3ce-312">No `CompressableButton` momento, o componente é uma combinação de `PressableButton`  +  `PressableButtonHoloLens2` com `BaseInteractiveElement` como uma classe base.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-312">The `CompressableButton` component is currently a combination of `PressableButton` + `PressableButtonHoloLens2` with `BaseInteractiveElement`as a base class.</span></span> 

## <a name="state-visualizer-experimental"></a><span data-ttu-id="5a3ce-313">Visualizador de estado [experimental]</span><span class="sxs-lookup"><span data-stu-id="5a3ce-313">State Visualizer [Experimental]</span></span>

<span data-ttu-id="5a3ce-314">O componente Visualizador de estado adiciona animações a um objeto com base nos Estados definidos em um componente de elemento interativo vinculado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-314">The State Visualizer component adds animations to an object based on the states defined in a linked Interactive Element component.</span></span> <span data-ttu-id="5a3ce-315">Esse componente cria ativos de animação, coloca-os na pasta MixedRealityToolkit. Generated e habilita a configuração de quadro-chave de animação simplificada por meio da adição de propriedades animáveis a um objeto de jogo de destino.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-315">This component creates animation assets, places them in the MixedRealityToolkit.Generated folder and enables simplified animation keyframe setting through adding Animatable properties to a target game object.</span></span> <span data-ttu-id="5a3ce-316">Para habilitar transições de animação entre Estados, um ativo do controlador Animator é criado e uma máquina de estado padrão é gerada com parâmetros associados e quaisquer transições de estado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-316">To enable animation transitions between states, an Animator Controller asset is created and a default state machine is generated with associated parameters and any state transitions.</span></span>  <span data-ttu-id="5a3ce-317">A máquina de estado pode ser exibida na janela Animator do Unity.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-317">The state machine can be viewed in Unity's Animator window.</span></span>

### <a name="state-visualizer-and-unity-animation-system"></a><span data-ttu-id="5a3ce-318">Visualizador de estado e sistema de animação Unity</span><span class="sxs-lookup"><span data-stu-id="5a3ce-318">State Visualizer and Unity Animation System</span></span>

<span data-ttu-id="5a3ce-319">O Visualizador de estado atualmente utiliza o sistema de animação do Unity.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-319">The State Visualizer currently leverages the Unity Animation System.</span></span> 

<span data-ttu-id="5a3ce-320">Quando o botão **gerar novos clipes de animação** no Visualizador de estado é pressionado, novos ativos de clipe de animação são gerados com base nos nomes de estado no elemento interativo e são colocados na pasta MixedRealityToolkit. Generated.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-320">When the **Generate New Animation Clips** button in the State Visualizer is pressed, new animation clip assets are generated based on the state names in Interactive Element and are placed in the MixedRealityToolkit.Generated folder.</span></span> <span data-ttu-id="5a3ce-321">A propriedade clipe de animação em cada contêiner de estado é definida como o clipe de animação associado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-321">The Animation Clip property in each state container is set to the associated animation clip.</span></span>

![Clipes de animação no componente do Visualizador de estado](../images/interactive-element/StateVisualizer/AnimationClips.png)

<span data-ttu-id="5a3ce-323">Um [computador de estado Animator](https://docs.unity3d.com/Manual/AnimationOverview.html) também é gerado para gerenciar transições suaves entre clipes de animação.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-323">An [Animator State Machine](https://docs.unity3d.com/Manual/AnimationOverview.html) is also generated to manage smooth transitions between animation clips.</span></span>  <span data-ttu-id="5a3ce-324">Por padrão, a máquina de estado utiliza o [estado any](https://docs.unity3d.com/Manual/class-State.html) para permitir transições entre qualquer estado no elemento interativo.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-324">By default, the state machine utilizes the [Any State](https://docs.unity3d.com/Manual/class-State.html) to allow transitions between any state in Interactive Element.</span></span> 

<span data-ttu-id="5a3ce-325">[Os visualizadores de estado](https://docs.unity3d.com/Manual/AnimationParameters.html) disparados no animador também são gerados para cada estado, os parâmetros de gatilho são usados no Visualizador de Estado para disparar uma animação.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-325">[State visualizers triggered in the animator](https://docs.unity3d.com/Manual/AnimationParameters.html) are also generated for each state, the trigger parameters are used in the State Visualizer to trigger an animation.</span></span>

![Computador de estado do Unity](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a><span data-ttu-id="5a3ce-327">Limitações do Runtime</span><span class="sxs-lookup"><span data-stu-id="5a3ce-327">Runtime Limitations</span></span> 

<span data-ttu-id="5a3ce-328">O Visualizador de Estado deve ser adicionado a um objeto por meio do Inspetor e não pode ser adicionado por meio de script.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-328">The State Visualizer must be added to an object via the Inspector and cannot be added via script.</span></span>  <span data-ttu-id="5a3ce-329">As propriedades que modificam o AnimatorStateMachine/AnimationController estão contidas em um namespace do editor ( ) que é removido `UnityEditor.Animations` quando o aplicativo é criado.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-329">The properties that modify the AnimatorStateMachine/AnimationController are contained in an editor namespace (`UnityEditor.Animations`) which get removed when the app is built.</span></span>

## <a name="how-to-use-the-state-visualizer"></a><span data-ttu-id="5a3ce-330">Como usar o Visualizador de Estado</span><span class="sxs-lookup"><span data-stu-id="5a3ce-330">How to use the State Visualizer</span></span>

1. <span data-ttu-id="5a3ce-331">Criar um cubo</span><span class="sxs-lookup"><span data-stu-id="5a3ce-331">Create a Cube</span></span>
1. <span data-ttu-id="5a3ce-332">Anexar elemento interativo</span><span class="sxs-lookup"><span data-stu-id="5a3ce-332">Attach Interactive Element</span></span>
1. <span data-ttu-id="5a3ce-333">Anexar Visualizador de Estado</span><span class="sxs-lookup"><span data-stu-id="5a3ce-333">Attach State Visualizer</span></span>
1. <span data-ttu-id="5a3ce-334">Selecione **Gerar Novos Clipes de Animação**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-334">Select **Generate New Animation Clips**</span></span>

    ![Gerando novos clipes de animação](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![Mostrando clipes de animação gerados em componentes de elemento interativo e visualizador](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. <span data-ttu-id="5a3ce-337">No contêiner Estado de foco, selecione **Adicionar Destino**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-337">In the Focus state container, select **Add Target**</span></span>

    ![Adicionando o destino do visualizador de estado](../images/interactive-element/StateVisualizer/AddTarget.png)

1. <span data-ttu-id="5a3ce-339">Arraste o objeto do jogo atual para o campo de destino</span><span class="sxs-lookup"><span data-stu-id="5a3ce-339">Drag the current game object to the target field</span></span> 

    ![Definindo o destino do visualizador de estado](../images/interactive-element/StateVisualizer/SetTarget.png)

1. <span data-ttu-id="5a3ce-341">Abra o dobrado Propriedades Animatable do Cubo</span><span class="sxs-lookup"><span data-stu-id="5a3ce-341">Open the Cube Animatable Properties foldout</span></span>
1. <span data-ttu-id="5a3ce-342">Selecione o menu suspenso propriedade Animatable e selecione **Cor**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-342">Select the Animatable property drop down menu and select **Color**</span></span>

    ![Definindo a cor do visualizador de estado](../images/interactive-element/StateVisualizer/SetColor.png)

1. <span data-ttu-id="5a3ce-344">Selecione **Adicionar a propriedade Color Animatable**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-344">Select **Add the Color Animatable Property**</span></span>

    ![Selecionando a propriedade animatable de cor do visualizador](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. <span data-ttu-id="5a3ce-346">Escolher uma cor</span><span class="sxs-lookup"><span data-stu-id="5a3ce-346">Choose a Color</span></span> 

    ![Escolhendo uma cor do visualisador no disco de cores](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. <span data-ttu-id="5a3ce-348">Pressione reproduzir e observe a alteração de cor de transição</span><span class="sxs-lookup"><span data-stu-id="5a3ce-348">Press play and observe the transitional color change</span></span>

    ![Exemplo de alteração de cor de transição com interação de mão virtual](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a><span data-ttu-id="5a3ce-350">Propriedades animáveis</span><span class="sxs-lookup"><span data-stu-id="5a3ce-350">Animatable Properties</span></span>

<span data-ttu-id="5a3ce-351">A principal finalidade das propriedades animáveis é simplificar a configuração de quadro-chave do clipe de animação.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-351">The primary purpose of the Animatable Properties is to simplify animation clip keyframe setting.</span></span>  <span data-ttu-id="5a3ce-352">Se um usuário estiver familiarizado com o sistema de animação do Unity e preferir definir diretamente os quadros-chave nos clipes de animação gerados, eles poderão simplesmente não adicionar propriedades animáveis a um objeto de destino e abrir o clipe na janela de animação do Unity (animação de > de animação do Windows >).</span><span class="sxs-lookup"><span data-stu-id="5a3ce-352">If a user is familiar with the Unity Animation System and would prefer to directly set keyframes on the generated animation clips, then they can simply not add Animatable properties to a target object and open the clip in Unity's Animation window (Windows > Animation > Animation).</span></span> 

<span data-ttu-id="5a3ce-353">Se estiver usando as propriedades animáveis para animação, o tipo de curva será definido como EaseInOut.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-353">If using the Animatable properties for animation, the curve type is set to EaseInOut.</span></span>

<span data-ttu-id="5a3ce-354">**Propriedades animáveis atuais:**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-354">**Current Animatable Properties:**</span></span>
- [<span data-ttu-id="5a3ce-355">Deslocamento de escala</span><span class="sxs-lookup"><span data-stu-id="5a3ce-355">Scale Offset</span></span>](#scale-offset)
- [<span data-ttu-id="5a3ce-356">Deslocamento da posição</span><span class="sxs-lookup"><span data-stu-id="5a3ce-356">Position Offset</span></span>](#position-offset)
- [<span data-ttu-id="5a3ce-357">Cor</span><span class="sxs-lookup"><span data-stu-id="5a3ce-357">Color</span></span>](#color)
- [<span data-ttu-id="5a3ce-358">Cor do sombreador</span><span class="sxs-lookup"><span data-stu-id="5a3ce-358">Shader Color</span></span>](#shader-color)
- [<span data-ttu-id="5a3ce-359">Sombreador float</span><span class="sxs-lookup"><span data-stu-id="5a3ce-359">Shader Float</span></span>](#shader-float)
- [<span data-ttu-id="5a3ce-360">Vetor de sombreador</span><span class="sxs-lookup"><span data-stu-id="5a3ce-360">Shader Vector</span></span>](#shader-vector)

### <a name="scale-offset"></a><span data-ttu-id="5a3ce-361">Deslocamento de escala</span><span class="sxs-lookup"><span data-stu-id="5a3ce-361">Scale Offset</span></span>

<span data-ttu-id="5a3ce-362">A propriedade animada de deslocamento de escala usa a escala atual do objeto e adiciona o deslocamento definido.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-362">The Scale Offset Animatable property takes the current scale of the object and adds the defined offset.</span></span>

![Deslocamento de escala com interação de mão virtual](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a><span data-ttu-id="5a3ce-364">Deslocamento da posição</span><span class="sxs-lookup"><span data-stu-id="5a3ce-364">Position Offset</span></span>

<span data-ttu-id="5a3ce-365">A propriedade de deslocamento animada da posição usa a posição atual do objeto e adiciona o deslocamento definido.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-365">The Position Offset Animatable property takes the current position of the object and adds the defined offset.</span></span>

![Deslocamento de posição com interação de mão virtual](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a><span data-ttu-id="5a3ce-367">Color</span><span class="sxs-lookup"><span data-stu-id="5a3ce-367">Color</span></span>

<span data-ttu-id="5a3ce-368">A propriedade de cor animável representa a cor principal de um material se o material tiver uma propriedade de cor principal.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-368">The Color Animatable property represents the main color of a material if the material has a main color property.</span></span> <span data-ttu-id="5a3ce-369">Essa propriedade anima a `material._Color` propriedade.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-369">This property animates the `material._Color` property.</span></span>

![Alteração de cor do foco com interação de mão virtual](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a><span data-ttu-id="5a3ce-371">Cor do sombreador</span><span class="sxs-lookup"><span data-stu-id="5a3ce-371">Shader Color</span></span>

<span data-ttu-id="5a3ce-372">A propriedade animada de cor do sombreador refere-se a uma propriedade shader do tipo Color.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-372">The Shader Color Animatable property refers to a shader property of type color.</span></span> <span data-ttu-id="5a3ce-373">Um nome de propriedade é necessário para todas as propriedades de sombreador.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-373">A property name is required for all shader properties.</span></span> <span data-ttu-id="5a3ce-374">O GIF abaixo demonstra a animação de uma propriedade de cor do sombreador chamada Fill_Color que não é a cor do material principal.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-374">The gif below demonstrates animating a shader color property named Fill_Color that is not the main material color.</span></span>  <span data-ttu-id="5a3ce-375">Observe os valores de alteração no Inspetor de material.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-375">Observe the changing values in the material inspector.</span></span>

![Cor de sombreamento com interação de mão virtual](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a><span data-ttu-id="5a3ce-377">Sombreador float</span><span class="sxs-lookup"><span data-stu-id="5a3ce-377">Shader Float</span></span>

<span data-ttu-id="5a3ce-378">A propriedade animada do sombreador float se refere a uma propriedade shader do tipo float.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-378">The Shader Float Animatable property refers to a shader property of type float.</span></span> <span data-ttu-id="5a3ce-379">Um nome de propriedade é necessário para todas as propriedades de sombreador.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-379">A property name is required for all shader properties.</span></span> <span data-ttu-id="5a3ce-380">No gif abaixo, observe os valores de alteração no Inspetor de material para a propriedade metálica.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-380">In the gif below, observe the changing values in the material inspector for the Metallic property.</span></span> 

![Sombreador float com interação de mão virtual](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a><span data-ttu-id="5a3ce-382">Vetor de sombreador</span><span class="sxs-lookup"><span data-stu-id="5a3ce-382">Shader Vector</span></span>

<span data-ttu-id="5a3ce-383">A propriedade animá vector Shader se refere a uma propriedade shader do tipo Vector4.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-383">The Shader Vector Animatable property refers to a shader property of type Vector4.</span></span> <span data-ttu-id="5a3ce-384">Um nome de propriedade é necessário para todas as propriedades de sombreador.</span><span class="sxs-lookup"><span data-stu-id="5a3ce-384">A property name is required for all shader properties.</span></span> <span data-ttu-id="5a3ce-385">No gif abaixo, observe os valores de alteração no Inspetor de material para a propriedade de colocação em disposição (principal Tex_ST).</span><span class="sxs-lookup"><span data-stu-id="5a3ce-385">In the gif below, observe the changing values in the material inspector for the Tiling (Main Tex_ST) property.</span></span> 

![Vetor de sombreador com interação de mão virtual](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a><span data-ttu-id="5a3ce-387">Como localizar nomes de propriedades de sombreador animáveis</span><span class="sxs-lookup"><span data-stu-id="5a3ce-387">How to Find Animatable Shader Property Names</span></span>

1. <span data-ttu-id="5a3ce-388">Navegue até a > animação > janela</span><span class="sxs-lookup"><span data-stu-id="5a3ce-388">Navigate to Window > Animation > Animation</span></span>
1. <span data-ttu-id="5a3ce-389">Verifique se o objeto com o Visualizador de Estado está selecionado na hierarquia</span><span class="sxs-lookup"><span data-stu-id="5a3ce-389">Ensure that the object with the State Visualizer is selected in the hierarchy</span></span>
1. <span data-ttu-id="5a3ce-390">Selecione qualquer clipe de animação na janela Animação</span><span class="sxs-lookup"><span data-stu-id="5a3ce-390">Select any animation clip in the Animation window</span></span>
1. <span data-ttu-id="5a3ce-391">Selecione **Adicionar Propriedade**, abra o foldout do Renderador de Malha</span><span class="sxs-lookup"><span data-stu-id="5a3ce-391">Select **Add Property**, open the Mesh Renderer foldout</span></span> 

    ![Adicionando a propriedade de animação na janela Animator](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. <span data-ttu-id="5a3ce-393">Esta lista contém os nomes de todos os nomes de propriedade Animatable</span><span class="sxs-lookup"><span data-stu-id="5a3ce-393">This list contains the names of all the Animatable property names</span></span> 

    ![Propriedades de animação do renderdor de malha na janela Animator](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a><span data-ttu-id="5a3ce-395">Confira também</span><span class="sxs-lookup"><span data-stu-id="5a3ce-395">See also</span></span>

- [<span data-ttu-id="5a3ce-396">**Botões**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-396">**Buttons**</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="5a3ce-397">**Controle de limites**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-397">**Bounds Control**</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="5a3ce-398">**Coleção de objetos de grade**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-398">**Grid Object Collection**</span></span>](../ux-building-blocks/object-collection.md)
- [<span data-ttu-id="5a3ce-399">**Solucionador RadialView**</span><span class="sxs-lookup"><span data-stu-id="5a3ce-399">**RadialView Solver**</span></span>](../ux-building-blocks/solvers/solver.md)
