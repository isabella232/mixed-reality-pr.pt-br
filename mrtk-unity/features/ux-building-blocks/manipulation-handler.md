---
title: Manipulador de manipulação
description: Documentação sobre manipulador de manipulação no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Manipulação,
ms.openlocfilehash: 179ef40ba054b0fda3b13e9d578905eb064a58ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176632"
---
# <a name="manipulation-handler"></a><span data-ttu-id="f8f04-104">Manipulador de manipulação</span><span class="sxs-lookup"><span data-stu-id="f8f04-104">Manipulation handler</span></span>

![Manipulador de manipulação](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="f8f04-106">O script *ManipulationHandler* permite que um objeto se deixe móvel, escalonável e rotatável usando uma ou duas mãos.</span><span class="sxs-lookup"><span data-stu-id="f8f04-106">The *ManipulationHandler* script allows for an object to be made movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="f8f04-107">A manipulação pode ser restrita para permitir apenas determinados tipos de transformação.</span><span class="sxs-lookup"><span data-stu-id="f8f04-107">Manipulation can be restricted so that it only allows certain kinds of transformation.</span></span> <span data-ttu-id="f8f04-108">O script funciona com vários tipos de entradas, incluindo HoloLens entrada de mão articulada 2, raios de mão, entrada de gesto HoloLens (1ª geração) e entrada do controlador de movimento do headset imersivo.</span><span class="sxs-lookup"><span data-stu-id="f8f04-108">The script works with various types of inputs including HoloLens 2 articulated hand input, hand-rays, HoloLens (1st gen) gesture input, and immersive headset motion controller input.</span></span>

## <a name="how-to-use-the-manipulation-handler"></a><span data-ttu-id="f8f04-109">Como usar o manipulador de manipulação</span><span class="sxs-lookup"><span data-stu-id="f8f04-109">How to use the manipulation handler</span></span>

<span data-ttu-id="f8f04-110">Adicione o `ManipulationHandler` componente de script a um GameObject.</span><span class="sxs-lookup"><span data-stu-id="f8f04-110">Add the `ManipulationHandler` script component to a GameObject.</span></span> <span data-ttu-id="f8f04-111">Certifique-se também de adicionar um colisor ao objeto, correspondendo aos seus limites que podem ser capturados.</span><span class="sxs-lookup"><span data-stu-id="f8f04-111">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="f8f04-112">Para fazer com que o objeto responda à entrada de mão quase articulada, adicione `NearInteractionGrabbable` o script também.</span><span class="sxs-lookup"><span data-stu-id="f8f04-112">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

![Usando o manipulador de manipulação no editor do Unity](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a><span data-ttu-id="f8f04-114">Propriedades do inspetor</span><span class="sxs-lookup"><span data-stu-id="f8f04-114">Inspector properties</span></span>

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

<span data-ttu-id="f8f04-115">**Transformação host** Transformação que será arrastada.</span><span class="sxs-lookup"><span data-stu-id="f8f04-115">**Host Transform** Transform that will be dragged.</span></span> <span data-ttu-id="f8f04-116">Assume como padrão o objeto do componente.</span><span class="sxs-lookup"><span data-stu-id="f8f04-116">Defaults to the object of the component.</span></span>

<span data-ttu-id="f8f04-117">**Tipo de manipulação** Especifica se o objeto pode ser manipulado usando uma mão, duas mãos ou ambas.</span><span class="sxs-lookup"><span data-stu-id="f8f04-117">**Manipulation Type** Specifies whether the object can be manipulated using one hand, two hands, or both.</span></span>

* <span data-ttu-id="f8f04-118">*Somente uma mão*</span><span class="sxs-lookup"><span data-stu-id="f8f04-118">*One handed only*</span></span>
* <span data-ttu-id="f8f04-119">*Somente duas mãos*</span><span class="sxs-lookup"><span data-stu-id="f8f04-119">*Two handed only*</span></span>
* <span data-ttu-id="f8f04-120">*Uma e duas mãos*</span><span class="sxs-lookup"><span data-stu-id="f8f04-120">*One and Two handed*</span></span>

<span data-ttu-id="f8f04-121">**Tipo de manipulação de duas mãos**</span><span class="sxs-lookup"><span data-stu-id="f8f04-121">**Two Handed Manipulation Type**</span></span>

* <span data-ttu-id="f8f04-122">*Escala:* somente o dimensionamento é permitido.</span><span class="sxs-lookup"><span data-stu-id="f8f04-122">*Scale*: Only scaling is allowed.</span></span>
* <span data-ttu-id="f8f04-123">*Girar:* somente a rotação é permitida.</span><span class="sxs-lookup"><span data-stu-id="f8f04-123">*Rotate*: Only rotation is allowed.</span></span>
* <span data-ttu-id="f8f04-124">*Escala de movimentação:* a movimentação e o dimensionamento são permitidos.</span><span class="sxs-lookup"><span data-stu-id="f8f04-124">*Move Scale*: Moving and scaling is allowed.</span></span>
* <span data-ttu-id="f8f04-125">*Mover Girar:* mover e girar é permitido.</span><span class="sxs-lookup"><span data-stu-id="f8f04-125">*Move Rotate*: Moving and rotating is allowed.</span></span>
* <span data-ttu-id="f8f04-126">*Girar Escala:* rotação e dimensionamento são permitidos.</span><span class="sxs-lookup"><span data-stu-id="f8f04-126">*Rotate Scale*: Rotating and scaling is allowed.</span></span>
* <span data-ttu-id="f8f04-127">*Mover Escala de Rotação:* é permitido mover, girar e dimensionar.</span><span class="sxs-lookup"><span data-stu-id="f8f04-127">*Move Rotate Scale*: Moving, rotating and scaling is allowed.</span></span>

![Manipulador de manipulação](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

<span data-ttu-id="f8f04-129">**Permitir manipulação distante** Especifica se a manipulação pode ser feita usando interação distante com ponteiros.</span><span class="sxs-lookup"><span data-stu-id="f8f04-129">**Allow Far Manipulation** Specifies whether manipulation can be done using far interaction with pointers.</span></span>

<span data-ttu-id="f8f04-130">**Modo de rotação de uma mão próximo** Especifica como o objeto se comportará quando estiver sendo capturado com uma mão/controlador próximo.</span><span class="sxs-lookup"><span data-stu-id="f8f04-130">**One Hand Rotation Mode Near** Specifies how the object will behave when it is being grabbed with one hand / controller near.</span></span>

<span data-ttu-id="f8f04-131">**Modo de rotação de uma mão distante** Especifica como o objeto se comportará quando estiver sendo capturado com uma mão/controlador à distância.</span><span class="sxs-lookup"><span data-stu-id="f8f04-131">**One Hand Rotation Mode Far** Specifies how the object will behave when it is being grabbed with one hand / controller at distance.</span></span>

<span data-ttu-id="f8f04-132">**Opções de modo de rotação de uma mão** Especifica como o objeto girará quando estiver sendo capturado com uma mão.</span><span class="sxs-lookup"><span data-stu-id="f8f04-132">**One Hand Rotation Mode Options** Specifies how the object will rotate when it is being grabbed with one hand.</span></span>

* <span data-ttu-id="f8f04-133">*Manter a rotação original:* não gira o objeto conforme ele está sendo movido</span><span class="sxs-lookup"><span data-stu-id="f8f04-133">*Maintain original rotation*: Does not rotate object as it is being moved</span></span>
* <span data-ttu-id="f8f04-134">*Manter a rotação para* o usuário: mantém a rotação original do objeto para o eixo X/Y para o usuário</span><span class="sxs-lookup"><span data-stu-id="f8f04-134">*Maintain rotation to user*: Maintains the object's original rotation for X/Y axis to the user</span></span>
* <span data-ttu-id="f8f04-135">*A gravidade alinhada mantém a rotação para o* usuário: mantém a rotação original do objeto para o usuário, mas torna o objeto vertical.</span><span class="sxs-lookup"><span data-stu-id="f8f04-135">*Gravity aligned maintain rotation to user*: Maintains object's original rotation to user, but makes the object vertical.</span></span> <span data-ttu-id="f8f04-136">Útil para objetos com um controle de limites.</span><span class="sxs-lookup"><span data-stu-id="f8f04-136">Useful for objects with a bounds control.</span></span>
* <span data-ttu-id="f8f04-137">*Usuário de face:* garante que o objeto sempre enfrenta o usuário.</span><span class="sxs-lookup"><span data-stu-id="f8f04-137">*Face user*: Ensures object always faces the user.</span></span> <span data-ttu-id="f8f04-138">Útil para slates/painéis.</span><span class="sxs-lookup"><span data-stu-id="f8f04-138">Useful for slates/panels.</span></span>
* <span data-ttu-id="f8f04-139">*Face para fora do usuário:* garante que o objeto sempre se desdonte do usuário.</span><span class="sxs-lookup"><span data-stu-id="f8f04-139">*Face away from user*: Ensures object always faces away from user.</span></span> <span data-ttu-id="f8f04-140">Útil para slates/painéis configurados para trás.</span><span class="sxs-lookup"><span data-stu-id="f8f04-140">Useful for slates/panels that are configured backwards.</span></span>
* <span data-ttu-id="f8f04-141">*Girar sobre o centro de objetos:* funciona apenas para mãos/controladores articulados.</span><span class="sxs-lookup"><span data-stu-id="f8f04-141">*Rotate about object center*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="f8f04-142">Girar o objeto usando a rotação da mão/controlador, mas sobre o ponto central do objeto.</span><span class="sxs-lookup"><span data-stu-id="f8f04-142">Rotate object using rotation of the hand/controller, but about the object center point.</span></span> <span data-ttu-id="f8f04-143">Útil para inspecionar à distância.</span><span class="sxs-lookup"><span data-stu-id="f8f04-143">Useful for inspecting at a distance.</span></span>
* <span data-ttu-id="f8f04-144">*Girar sobre o ponto de captura:* funciona apenas para mãos/controladores articulados.</span><span class="sxs-lookup"><span data-stu-id="f8f04-144">*Rotate about grab point*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="f8f04-145">Gire o objeto como se estivesse sendo mantido pela mão/controlador.</span><span class="sxs-lookup"><span data-stu-id="f8f04-145">Rotate object as if it was being held by hand/controller.</span></span> <span data-ttu-id="f8f04-146">Útil para inspeção.</span><span class="sxs-lookup"><span data-stu-id="f8f04-146">Useful for inspection.</span></span>

<span data-ttu-id="f8f04-147">**Comportamento da versão** Quando um objeto é liberado, especifique seu comportamento de movimento físico.</span><span class="sxs-lookup"><span data-stu-id="f8f04-147">**Release Behavior** When an object is released, specify its physical movement behavior.</span></span> <span data-ttu-id="f8f04-148">Requer um componente rigidbody para estar nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="f8f04-148">Requires a rigidbody component to be on that object.</span></span>

* <span data-ttu-id="f8f04-149">*Nothing*</span><span class="sxs-lookup"><span data-stu-id="f8f04-149">*Nothing*</span></span>
* <span data-ttu-id="f8f04-150">*Tudo*</span><span class="sxs-lookup"><span data-stu-id="f8f04-150">*Everything*</span></span>
* <span data-ttu-id="f8f04-151">*Manter a velocidade*</span><span class="sxs-lookup"><span data-stu-id="f8f04-151">*Keep Velocity*</span></span>
* <span data-ttu-id="f8f04-152">*Manter Angular velocidade*</span><span class="sxs-lookup"><span data-stu-id="f8f04-152">*Keep Angular Velocity*</span></span>

<span data-ttu-id="f8f04-153">**Restrições na rotação** Especifica em qual eixo o objeto girará quando interagido.</span><span class="sxs-lookup"><span data-stu-id="f8f04-153">**Constraints on Rotation** Specifies on which axis the object will rotate when interacted with.</span></span>

* <span data-ttu-id="f8f04-154">*Nenhuma*</span><span class="sxs-lookup"><span data-stu-id="f8f04-154">*None*</span></span>
* <span data-ttu-id="f8f04-155">*Somente eixo X*</span><span class="sxs-lookup"><span data-stu-id="f8f04-155">*X-Axis Only*</span></span>
* <span data-ttu-id="f8f04-156">*Somente eixo Y*</span><span class="sxs-lookup"><span data-stu-id="f8f04-156">*Y-Axis Only*</span></span>
* <span data-ttu-id="f8f04-157">*Somente eixo Z*</span><span class="sxs-lookup"><span data-stu-id="f8f04-157">*Z-Axis Only*</span></span>

<span data-ttu-id="f8f04-158">**Usar espaço local para restrição** Uma alternância para alternar entre a aplicação de restrições em relação ao eixo de espaço do mundo ou eixo de espaço local.</span><span class="sxs-lookup"><span data-stu-id="f8f04-158">**Use Local Space For Constraint** A toggle to switch between applying constraints in respect to world-space axis, or local space axis.</span></span>

<span data-ttu-id="f8f04-159">**Restrições de movimentação**</span><span class="sxs-lookup"><span data-stu-id="f8f04-159">**Constraints on Movement**</span></span>

* <span data-ttu-id="f8f04-160">*Nenhuma*</span><span class="sxs-lookup"><span data-stu-id="f8f04-160">*None*</span></span>
* <span data-ttu-id="f8f04-161">*Corrigir a distância da cabeça*</span><span class="sxs-lookup"><span data-stu-id="f8f04-161">*Fix distance from head*</span></span>

<span data-ttu-id="f8f04-162">**Suavização ativa** Especifica se a suavização está ativa.</span><span class="sxs-lookup"><span data-stu-id="f8f04-162">**Smoothing Active** Specifies whether smoothing is active.</span></span>

<span data-ttu-id="f8f04-163">**Suavizando a quantidade uma mão** Quantidade de suavização a ser aplicada à movimentação, escala, rotação.</span><span class="sxs-lookup"><span data-stu-id="f8f04-163">**Smoothing Amount One Hand** Amount of smoothing to apply to the movement, scale, rotation.</span></span> <span data-ttu-id="f8f04-164">Suavização de 0 significa nenhuma suavização.</span><span class="sxs-lookup"><span data-stu-id="f8f04-164">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="f8f04-165">Valor máximo significa nenhuma alteração no valor.</span><span class="sxs-lookup"><span data-stu-id="f8f04-165">Max value means no change to value.</span></span>

## <a name="events"></a><span data-ttu-id="f8f04-166">Eventos</span><span class="sxs-lookup"><span data-stu-id="f8f04-166">Events</span></span>

<span data-ttu-id="f8f04-167">O manipulador de manipulação fornece os seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="f8f04-167">Manipulation handler provides the following events:</span></span>

* <span data-ttu-id="f8f04-168">*OnManipulationStarted:* acionado quando a manipulação é iniciada.</span><span class="sxs-lookup"><span data-stu-id="f8f04-168">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
* <span data-ttu-id="f8f04-169">*OnManipulationEnded:* é a incêndio quando a manipulação termina.</span><span class="sxs-lookup"><span data-stu-id="f8f04-169">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
* <span data-ttu-id="f8f04-170">*OnHoverStarted:* é a incêndio quando uma mão/controlador passar o mouse no manipulador, próximo ou distante.</span><span class="sxs-lookup"><span data-stu-id="f8f04-170">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
* <span data-ttu-id="f8f04-171">*OnHoverEnded:* é a incêndio quando uma mão/controlador destoca o manipulador, próximo ou distante.</span><span class="sxs-lookup"><span data-stu-id="f8f04-171">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>
