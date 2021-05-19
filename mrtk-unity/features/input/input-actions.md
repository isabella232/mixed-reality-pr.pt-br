---
title: Ações de entrada
description: Documentação para criar ações de entrada no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, InputActions,
ms.openlocfilehash: 071d4bc8bb4193a3d60cb53852c192ae975d79df
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144152"
---
# <a name="input-actions"></a><span data-ttu-id="1b2b8-104">Ações de entrada</span><span class="sxs-lookup"><span data-stu-id="1b2b8-104">Input actions</span></span>

<span data-ttu-id="1b2b8-105">[**As Ações de**](input-actions.md) Entrada são abstrações sobre entradas brutas destinadas a ajudar a isolar a lógica do aplicativo das fontes de entrada específicas que produzem uma entrada.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-105">[**Input Actions**](input-actions.md) are abstractions over raw inputs meant to help isolating application logic from the specific input sources producing an input.</span></span> <span data-ttu-id="1b2b8-106">Pode ser útil, por exemplo,  definir uma ação Selecionar e mapeá-la para o botão esquerdo do mouse, um botão em um gamepad e um gatilho em um controlador de 6 DOF.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-106">It can be useful, for example, to define a *Select* action and map it to the left mouse button, a button in a gamepad and a trigger in a 6 DOF controller.</span></span> <span data-ttu-id="1b2b8-107">Em seguida, você pode fazer com que a lógica do aplicativo escute *selecionar* eventos de ação de entrada em vez de ter que estar ciente de todas as diferentes entradas que podem produzi-los.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-107">You can then have your application logic listen for *Select* input action events instead of having to be aware of all the different inputs that can produce it.</span></span>

## <a name="creating-an-input-action"></a><span data-ttu-id="1b2b8-108">Criando uma ação de entrada</span><span class="sxs-lookup"><span data-stu-id="1b2b8-108">Creating an input action</span></span>

<span data-ttu-id="1b2b8-109">As ações de entrada são configuradas  no Perfil de Ações de Entrada **,** dentro do Perfil do Sistema de Entrada no componente Kit de Ferramentas de Realidade Misturada, especificando um nome para a ação e o tipo de entradas *(* Restrição do Eixo ) para o qual ele pode ser mapeado:</span><span class="sxs-lookup"><span data-stu-id="1b2b8-109">Input actions are configured in the **Input Actions Profile**, inside the *Input System Profile* in the Mixed Reality Toolkit component, specifying a name for the action and the type of inputs (*Axis Constraint*) it can be mapped to:</span></span>

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

<span data-ttu-id="1b2b8-110">Estes são os valores mais comumente usados para **Restrição de Eixo:**</span><span class="sxs-lookup"><span data-stu-id="1b2b8-110">These are the most mostly commonly used values for **Axis Constraint**:</span></span>

<span data-ttu-id="1b2b8-111">Restrição de eixo</span><span class="sxs-lookup"><span data-stu-id="1b2b8-111">Axis Constraint</span></span> | <span data-ttu-id="1b2b8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b2b8-112">Description</span></span>
--- | ---
<span data-ttu-id="1b2b8-113">Digital</span><span class="sxs-lookup"><span data-stu-id="1b2b8-113">Digital</span></span> | <span data-ttu-id="1b2b8-114">Entrada ligar/desligar como um botão binário em um gamepad ou mouse.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-114">On/off input like a binary button in a gamepad or mouse.</span></span>
<span data-ttu-id="1b2b8-115">Eixo único</span><span class="sxs-lookup"><span data-stu-id="1b2b8-115">Single Axis</span></span> | <span data-ttu-id="1b2b8-116">Entrada de eixo único como um gatilho análogo em um gamepad.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-116">Single axis analogue input like an analog trigger in a gamepad.</span></span>
<span data-ttu-id="1b2b8-117">Eixo duplo</span><span class="sxs-lookup"><span data-stu-id="1b2b8-117">Dual Axis</span></span> | <span data-ttu-id="1b2b8-118">Entrada de eixo duplo, como um thumbstick.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-118">Dual axis analogue input like a thumbstick.</span></span>
<span data-ttu-id="1b2b8-119">Seis Dof</span><span class="sxs-lookup"><span data-stu-id="1b2b8-119">Six Dof</span></span> | <span data-ttu-id="1b2b8-120">Pose 3D com conversão e rotação como aquela produzida por 6 controladores DOF.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-120">3D pose with translation and rotation like the one produced by 6 DOF controllers.</span></span>

<span data-ttu-id="1b2b8-121">Você pode encontrar a lista completa em [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .</span><span class="sxs-lookup"><span data-stu-id="1b2b8-121">You can find the full list in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType).</span></span>

## <a name="mapping-input-to-actions"></a><span data-ttu-id="1b2b8-122">Mapeando a entrada para ações</span><span class="sxs-lookup"><span data-stu-id="1b2b8-122">Mapping input to actions</span></span>

<span data-ttu-id="1b2b8-123">A maneira como você mapeia uma entrada para a ação e depende do tipo da fonte de entrada:</span><span class="sxs-lookup"><span data-stu-id="1b2b8-123">The way you map an input to and action depends on the type of the input source:</span></span>

### <a name="controller-input"></a><span data-ttu-id="1b2b8-124">Entrada do controlador</span><span class="sxs-lookup"><span data-stu-id="1b2b8-124">Controller input</span></span>

<span data-ttu-id="1b2b8-125">Vá para o Perfil **de Mapeamento de Entrada do Controlador,** no Perfil do Sistema de *Entrada*.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-125">Go to the **Controller Input Mapping Profile**, under the *Input System Profile*.</span></span> <span data-ttu-id="1b2b8-126">Lá, você encontrará uma lista de todos os controladores com suporte:</span><span class="sxs-lookup"><span data-stu-id="1b2b8-126">There you will find a list of all supported controllers:</span></span>

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

<span data-ttu-id="1b2b8-127">Selecione aquela que você deseja configurar e uma janela de diálogo será exibida com todas as entradas do controlador, permitindo que você de definir uma ação para cada uma delas:</span><span class="sxs-lookup"><span data-stu-id="1b2b8-127">Select the one you want to configure and a dialog window will appear with all the controller inputs, allowing you to set an action for each of them:</span></span>

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a><span data-ttu-id="1b2b8-128">Entrada de fala</span><span class="sxs-lookup"><span data-stu-id="1b2b8-128">Speech input</span></span>

<span data-ttu-id="1b2b8-129">No Perfil **de Comando de Fala**, no Perfil do Sistema de *Entrada*, você encontrará a lista de comandos de fala definidos no momento.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-129">In the **Speech Command Profile**, under the *Input System Profile*, you'll find the list of currently defined speech commands.</span></span> <span data-ttu-id="1b2b8-130">Para mapear um deles para uma ação, basta selecioná-lo *na* lista lista de ações.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-130">To map one of them to an action, just select it in the *Action* drop down.</span></span>

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a><span data-ttu-id="1b2b8-131">Entrada de gesto</span><span class="sxs-lookup"><span data-stu-id="1b2b8-131">Gesture input</span></span>

<span data-ttu-id="1b2b8-132">O **Perfil de Gestos**, no Perfil *do Sistema de Entrada*, contém todos os gestos definidos.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-132">The **Gestures Profile**, under the *Input System Profile*, contains all defined gestures.</span></span> <span data-ttu-id="1b2b8-133">Você pode mapear cada um deles para uma ação selecionando-a *na* lista de lista de ações.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-133">You can map each of them to an action by selecting it in the *Action* drop down.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a><span data-ttu-id="1b2b8-134">Manipulando ações de entrada</span><span class="sxs-lookup"><span data-stu-id="1b2b8-134">Handling input actions</span></span>

> [!WARNING]
> <span data-ttu-id="1b2b8-135">Atualmente, somente as ações de entrada *do tipo Digital* podem ser tratadas usando os métodos descritos nesta seção.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-135">Currently only input actions of *Digital* type can be handled using the methods described in this section.</span></span> <span data-ttu-id="1b2b8-136">Para outros tipos de ação, você terá que manipular diretamente os eventos para as entradas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-136">For other action types, you'll have to handle directly the events for the corresponding inputs instead.</span></span> <span data-ttu-id="1b2b8-137">Por exemplo, para lidar com uma ação de 6 DOF mapeada para entradas do controlador, você terá que usar [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) com T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .</span><span class="sxs-lookup"><span data-stu-id="1b2b8-137">For example, to handle a 6 DOF action mapped to controller inputs, you'll have to use [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) with T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="1b2b8-138">A maneira mais fácil de lidar com ações de entrada é usar o [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-138">The easiest way to handle input actions is to make use of the [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span></span> <span data-ttu-id="1b2b8-139">Isso permite que você defina a ação que deseja escutar e reagir a eventos iniciados e encerrados usando eventos do Unity.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-139">This allows you to define the action you want to listen to and react to action started and ended events using Unity Events.</span></span>

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

<span data-ttu-id="1b2b8-140">Se você quiser mais controle, poderá implementar a [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface diretamente em seu script.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-140">If you want more control, you can implement the [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface directly in your script.</span></span> <span data-ttu-id="1b2b8-141">Consulte a [**seção Eventos de Entrada**](input-events.md) para obter mais detalhes sobre a manipulação de eventos por meio de interfaces de manipulador.</span><span class="sxs-lookup"><span data-stu-id="1b2b8-141">See the [**Input Events**](input-events.md) section for more details on event handling via handler interfaces.</span></span>

## <a name="examples"></a><span data-ttu-id="1b2b8-142">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1b2b8-142">Examples</span></span>

<span data-ttu-id="1b2b8-143">Consulte para ver uma cena de exemplo mostrando como criar uma ação, mapeá-la para entradas de controlador, fala e gesto e usá-la para girar um `MRTK/Examples/Demos/Input/Scenes/InputActions` objeto no comando .</span><span class="sxs-lookup"><span data-stu-id="1b2b8-143">See `MRTK/Examples/Demos/Input/Scenes/InputActions` for an example scene showing how to create an action, map it to controller, speech and gesture inputs and use it to rotate an object on command.</span></span>

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
