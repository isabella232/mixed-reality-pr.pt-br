---
title: Controladores, ponteiros e foco
description: Interagindo com controladores, ponteiros e foco.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Ponteiros, Controladores
ms.openlocfilehash: b3e4438c1318abbc60606bcbca42854edae28167
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121614"
---
# <a name="controllers-pointers-and-focus"></a><span data-ttu-id="2c745-104">Controladores, ponteiros e foco</span><span class="sxs-lookup"><span data-stu-id="2c745-104">Controllers, pointers, and focus</span></span>

<span data-ttu-id="2c745-105">Controladores, ponteiros e foco são conceitos de nível superior que se baseam na base estabelecida pelo sistema de entrada principal.</span><span class="sxs-lookup"><span data-stu-id="2c745-105">Controllers, pointers, and focus are higher-level concepts that build upon the foundation established by the core input system.</span></span> <span data-ttu-id="2c745-106">Juntos, eles fornecem uma grande parte do mecanismo para interagir com objetos na cena.</span><span class="sxs-lookup"><span data-stu-id="2c745-106">Together, they provide a large portion of the mechanism for interacting with objects in the scene.</span></span>

## <a name="controllers"></a><span data-ttu-id="2c745-107">Controladores</span><span class="sxs-lookup"><span data-stu-id="2c745-107">Controllers</span></span>

<span data-ttu-id="2c745-108">Controladores são representações de um controlador físico (6 graus de liberdade, mão articulada etc.).</span><span class="sxs-lookup"><span data-stu-id="2c745-108">Controllers are representations of a physical controller (6-degrees of freedom, articulated hand, etc).</span></span> <span data-ttu-id="2c745-109">Eles são criados por gerenciadores de dispositivos e são responsáveis por se comunicar com o sistema subjacente correspondente e traduzir esses dados em eventos e dados em forma de MRTK.a</span><span class="sxs-lookup"><span data-stu-id="2c745-109">They are created by device managers and are responsible for communicating with the corresponding underlying system and translating that data into MRTK-shaped data and events.a</span></span>

<span data-ttu-id="2c745-110">Por exemplo, na plataforma Windows Mixed Reality, o é um controlador responsável por fazer a interfação com as APIs de acompanhamento de mão subjacentes do Windows para obter informações sobre as junções, a pose e outras propriedades da [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) mão. [](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)</span><span class="sxs-lookup"><span data-stu-id="2c745-110">For example, on the Windows Mixed Reality platform, the [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) is a controller that is responsible for interfacing with the underlying Windows [hand tracking APIs](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) to get information about the joints, pose, and other properties of the hand.</span></span> <span data-ttu-id="2c745-111">Ele é responsável por transformar esses dados em eventos relevantes do MRTK (por exemplo, chamando RaisePoseInputChanged ou RaiseHandJointsUpdated) e atualizando seu próprio estado interno para que as consultas para retornem dados [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) corretos.</span><span class="sxs-lookup"><span data-stu-id="2c745-111">It is responsible for turning this data into relevant MRTK events (for example, by calling RaisePoseInputChanged or RaiseHandJointsUpdated) and by updating its own internal state so that queries for [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) will return correct data.</span></span>

<span data-ttu-id="2c745-112">Em geral, o ciclo de vida de um controlador envolverá:</span><span class="sxs-lookup"><span data-stu-id="2c745-112">Generally, a controller's lifecycle will involve:</span></span>

1. <span data-ttu-id="2c745-113">Um controlador é criado por um gerenciador de dispositivos após a detecção de uma nova fonte (por exemplo, o gerenciador de dispositivos detecta e começa a rastrear uma mão).</span><span class="sxs-lookup"><span data-stu-id="2c745-113">A controller gets created by a device manager upon detection of a new source (for example, the device manager detects and starts tracking a hand).</span></span>

2. <span data-ttu-id="2c745-114">No loop Update() do controlador, ele chama em seu sistema de API subjacente.</span><span class="sxs-lookup"><span data-stu-id="2c745-114">In the controller's Update() loop, it calls into its underlying API system.</span></span>

3. <span data-ttu-id="2c745-115">No mesmo loop de atualização, ele gera alterações de evento de entrada chamando diretamente no próprio sistema de entrada principal (por exemplo, inging HandMeshUpdated ou HandJointsUpdated).</span><span class="sxs-lookup"><span data-stu-id="2c745-115">In the same update loop, it raises input event changes by calling directly into the core input system itself (for example, raising HandMeshUpdated, or HandJointsUpdated).</span></span>

## <a name="pointers-and-focus"></a><span data-ttu-id="2c745-116">Ponteiros e foco</span><span class="sxs-lookup"><span data-stu-id="2c745-116">Pointers and focus</span></span>

<span data-ttu-id="2c745-117">Ponteiros são usados para interagir com objetos de jogo.</span><span class="sxs-lookup"><span data-stu-id="2c745-117">Pointers are used to interact with game objects.</span></span> <span data-ttu-id="2c745-118">Esta seção descreve como os ponteiros são criados, como eles são atualizados e como eles determinam os objetos que estão em foco.</span><span class="sxs-lookup"><span data-stu-id="2c745-118">This section describes how pointers are created, how they get updated, and how they determine the object(s) that are in focus.</span></span> <span data-ttu-id="2c745-119">Ele também abrange os diferentes tipos de ponteiros existentes e os cenários em que eles estão ativos.</span><span class="sxs-lookup"><span data-stu-id="2c745-119">It will also cover the different types of pointers that exist and the scenarios in which they are active.</span></span>

### <a name="pointer-categories"></a><span data-ttu-id="2c745-120">Categorias de ponteiro</span><span class="sxs-lookup"><span data-stu-id="2c745-120">Pointer categories</span></span>

<span data-ttu-id="2c745-121">Os ponteiros geralmente se enquadram em uma das seguintes categorias:</span><span class="sxs-lookup"><span data-stu-id="2c745-121">Pointers generally fall into one of the following categories:</span></span>

- <span data-ttu-id="2c745-122">**Ponteiros distantes**</span><span class="sxs-lookup"><span data-stu-id="2c745-122">**Far pointers**</span></span>

  <span data-ttu-id="2c745-123">Esses tipos de ponteiros são usados para interagir com objetos que estão longe do usuário (distante é definido como simplesmente "não próximo").</span><span class="sxs-lookup"><span data-stu-id="2c745-123">These types of pointers are used to interact with objects that are far away from the user (far away is defined as simply “not near”).</span></span> <span data-ttu-id="2c745-124">Esses tipos de ponteiros geralmente lançam linhas que podem ir muito longe no mundo e permitir que o usuário interaja e manipule objetos que não estão imediatamente ao lado deles.</span><span class="sxs-lookup"><span data-stu-id="2c745-124">These types of pointers generally cast lines that can go far into the world and allow the user to interact with and manipulate objects that are not immediately next to them.</span></span>

- <span data-ttu-id="2c745-125">**Ponteiros próximos**</span><span class="sxs-lookup"><span data-stu-id="2c745-125">**Near pointers**</span></span>

  <span data-ttu-id="2c745-126">Esses tipos de ponteiros são usados para interagir com objetos próximos o suficiente do usuário para pegar, tocar e manipular.</span><span class="sxs-lookup"><span data-stu-id="2c745-126">These types of pointers are used to interact with objects that are close enough to the user to grab, touch, and manipulate.</span></span> <span data-ttu-id="2c745-127">Em geral, esses tipos de ponteiros interagem com objetos procurando objetos nas proximidades (seja fazendo o raycast em distâncias pequenas, fazendo a transmissão esférica procurando objetos nas proximidades ou enumerando listas de objetos que são considerados acessíveis/tocáveis).</span><span class="sxs-lookup"><span data-stu-id="2c745-127">Generally, these types of pointers interact with objects by looking for objects in the nearby vicinity (either by doing raycasting at small distances, doing spherical casting looking for objects in the vicinity, or enumerating lists of objects that are considered grabbable/touchable).</span></span>

- <span data-ttu-id="2c745-128">**Ponteiros de teletransporte**</span><span class="sxs-lookup"><span data-stu-id="2c745-128">**Teleport pointers**</span></span>

  <span data-ttu-id="2c745-129">Esses tipos de ponteiros se conectam ao sistema de transporte para lidar com a movimentação do usuário para o local de destino do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="2c745-129">These types of pointers plug into the teleportation system to handle moving the user to the location targeted by the pointer.</span></span>

## <a name="pointer-mediation"></a><span data-ttu-id="2c745-130">Ponteiro de ponteiro</span><span class="sxs-lookup"><span data-stu-id="2c745-130">Pointer mediation</span></span>

<span data-ttu-id="2c745-131">Como um único controlador pode ter vários ponteiros (por exemplo, a mão articulada pode ter ponteiros de interação próximos e distantes), existe um componente que é responsável por mediar qual ponteiro deve estar ativo.</span><span class="sxs-lookup"><span data-stu-id="2c745-131">Because a single controller can have multiple pointers (for example, the articulated hand can have both near and far interaction pointers), there exists a component that is responsible for mediating which pointer should be active.</span></span>

<span data-ttu-id="2c745-132">Por exemplo, conforme a mão do usuário se aproxima de um botão pressionável, o deve parar de aparecer [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) e o deve ser [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) envolvido.</span><span class="sxs-lookup"><span data-stu-id="2c745-132">For example, as the user’s hand approaches a pressable button, the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) should stop showing, and the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) should be engaged.</span></span>

<span data-ttu-id="2c745-133">Isso é tratado pelo , que é responsável por determinar quais ponteiros estão ativos, com [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) base no estado de todos os ponteiros.</span><span class="sxs-lookup"><span data-stu-id="2c745-133">This is handled by the [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator), which is responsible for determining which pointers are active, based on the state of all pointers.</span></span> <span data-ttu-id="2c745-134">Uma das principais coisas que isso faz é desabilitar ponteiros distantes quando um ponteiro próximo estiver próximo a um objeto (consulte [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).</span><span class="sxs-lookup"><span data-stu-id="2c745-134">One of the key things this does is disable far pointers when a near pointer is close to an object (please see [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)).</span></span>

<span data-ttu-id="2c745-135">É possível fornecer uma implementação alternativa do mediador de ponteiro alterando a [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) propriedade no perfil do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="2c745-135">It's possible to provide an alternate implementation of the pointer mediator by changing the [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) property on the pointer profile.</span></span>

### <a name="how-to-disable-pointers"></a><span data-ttu-id="2c745-136">Como desabilitar ponteiros</span><span class="sxs-lookup"><span data-stu-id="2c745-136">How to disable pointers</span></span>

<span data-ttu-id="2c745-137">Como o mediador de ponteiro executa cada quadro, ele acaba controlando o estado ativo/inativo de todos os ponteiros.</span><span class="sxs-lookup"><span data-stu-id="2c745-137">Because the pointer mediator runs every frame, it ends up controlling the active / inactive state of all pointers.</span></span> <span data-ttu-id="2c745-138">Portanto, se você definir a propriedade IsInteractionEnabled de um ponteiro no código, ela será substituída pelo mediador de ponteiro a cada quadro.</span><span class="sxs-lookup"><span data-stu-id="2c745-138">Therefore, if you set a pointer's IsInteractionEnabled property in code, it will get overwritten by the pointer mediator every frame.</span></span> <span data-ttu-id="2c745-139">Em vez disso, você pode especificar [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) o para controlar se os ponteiros devem estar ativas ou desligados por conta própria.</span><span class="sxs-lookup"><span data-stu-id="2c745-139">Instead, you can specify the [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) to control whether pointers should be on or off yourself.</span></span> <span data-ttu-id="2c745-140">Observe que isso só funcionará se você estiver usando o padrão [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) e [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) no MRTK.</span><span class="sxs-lookup"><span data-stu-id="2c745-140">Note that this will only work if you are using the default [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) and [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.</span></span>

#### <a name="example-disable-hand-rays-in-mrtk"></a><span data-ttu-id="2c745-141">Exemplo: Desabilitar raios de mão no MRTK</span><span class="sxs-lookup"><span data-stu-id="2c745-141">Example: Disable hand rays in MRTK</span></span>

<span data-ttu-id="2c745-142">O código a seguir desligará os raios de mão no MRTK:</span><span class="sxs-lookup"><span data-stu-id="2c745-142">The following code will turn off the hand rays in MRTK:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

<span data-ttu-id="2c745-143">O código a seguir retornará raios de mão para seu comportamento padrão no MRTK:</span><span class="sxs-lookup"><span data-stu-id="2c745-143">The following code will return hand rays to their default behavior in MRTK:</span></span>

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

<span data-ttu-id="2c745-144">O código a seguir forçará a adoção de raios de mão, independentemente de estar próximo a um grabbable:</span><span class="sxs-lookup"><span data-stu-id="2c745-144">The following code will force hand rays to be on, regardless if near a grabbable:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="2c745-145">Consulte [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) e para obter mais [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) exemplos.</span><span class="sxs-lookup"><span data-stu-id="2c745-145">See [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) and [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) for more examples.</span></span>

### <a name="focusprovider"></a><span data-ttu-id="2c745-146">FocusProvider</span><span class="sxs-lookup"><span data-stu-id="2c745-146">FocusProvider</span></span>

<span data-ttu-id="2c745-147">O é o trabalhador responsável por iterar na lista de todos os ponteiros e descobrir qual é o objeto focalizado [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) para cada ponteiro.</span><span class="sxs-lookup"><span data-stu-id="2c745-147">The [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) is the workhorse that is responsible for iterating over the list of all pointers and figuring out what the focused object is for each pointer.</span></span>

<span data-ttu-id="2c745-148">Em cada `Update()` chamada, isso vai:</span><span class="sxs-lookup"><span data-stu-id="2c745-148">In each `Update()` call, this will:</span></span>

1. <span data-ttu-id="2c745-149">Atualize todos os ponteiros, raycasting e fazendo a detecção de acertos conforme configurado pelo próprio ponteiro (por exemplo, o ponteiro de esfera pode especificar SphereOverlap raycastMode, portanto, FocusProvider fará uma colisão baseada em esfera)</span><span class="sxs-lookup"><span data-stu-id="2c745-149">Update all of the pointers, by raycasting and doing hit detection as-configured by the pointer itself (for example, the sphere pointer could specify the SphereOverlap raycastMode, so FocusProvider will do a sphere-based collision)</span></span>

2. <span data-ttu-id="2c745-150">Atualize o objeto focalizado por ponteiro (ou seja, se um objeto ganhasse foco, ele também dispararia eventos para esse objeto, se um objeto tivesse perdido o foco, ele dispararia a perda de foco etc.).</span><span class="sxs-lookup"><span data-stu-id="2c745-150">Update the focused object on a per-pointer basis (i.e. if an object gained focus, it would also trigger events to those object, if an object lost focus, it would trigger focus lost, etc).</span></span>

### <a name="pointer-configuration-and-lifecycle"></a><span data-ttu-id="2c745-151">Configuração e ciclo de vida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="2c745-151">Pointer configuration and lifecycle</span></span>

<span data-ttu-id="2c745-152">[Os ponteiros podem ser configurados](../features/input/pointers.md) na seção *Ponteiros* do perfil do sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="2c745-152">[Pointers can be configured](../features/input/pointers.md) in the *Pointers* section of the input system profile.</span></span>

<span data-ttu-id="2c745-153">O tempo de vida de um ponteiro geralmente é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2c745-153">The lifetime of a pointer is generally the following:</span></span>

1. <span data-ttu-id="2c745-154">Um gerenciador de dispositivos detectará a presença de um controlador.</span><span class="sxs-lookup"><span data-stu-id="2c745-154">A device manager will detect the presence of a controller.</span></span> <span data-ttu-id="2c745-155">Esse gerenciador de dispositivos criará o conjunto de ponteiros associados ao controlador por meio de uma chamada para [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="2c745-155">This device manager will then create the set of pointers associated with the controller via a call to [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager).</span></span>

2. <span data-ttu-id="2c745-156">O FocusProvider, em seu loop Update(), iterará em todos os ponteiros válidos e fará a lógica de detecção de raycast ou de hit associada.</span><span class="sxs-lookup"><span data-stu-id="2c745-156">The FocusProvider, in its Update() loop, will iterate over all of the valid pointers and do the associated raycast or hit detection logic.</span></span> <span data-ttu-id="2c745-157">Isso é usado para determinar o objeto focalizado por cada ponteiro específico.</span><span class="sxs-lookup"><span data-stu-id="2c745-157">This is used to determine the object that is focused by each particular pointer.</span></span>

    - <span data-ttu-id="2c745-158">Como é possível ter várias fontes de entrada ativas ao mesmo tempo (por exemplo, duas mãos ativas presentes), também é possível ter vários objetos que têm foco ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="2c745-158">Because it's possible to have multiple sources of input active at the same time (for example, two hands active present), it's also possible to have multiple objects that have focus at the same time.</span></span>

3. <span data-ttu-id="2c745-159">O gerenciador de dispositivos, ao descobrir que uma origem do controlador foi perdida, destruirá os ponteiros associados ao controlador perdido.</span><span class="sxs-lookup"><span data-stu-id="2c745-159">The device manager, upon discovering that a controller source was lost, will tear down the pointers associated with the lost controller.</span></span>