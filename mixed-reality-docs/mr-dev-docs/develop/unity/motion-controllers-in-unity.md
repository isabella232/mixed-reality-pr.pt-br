---
title: Controladores de movimento no Unity
description: Saiba como agir em seu olhar no Unity com a entrada do controlador de movimento usando a XR e as APIs de botão e de eixo comuns.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: controladores de animação, Unity, entrada, realidade misturada Headset, headset da realidade mista do Windows, headset da realidade virtual, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: bf9aad0ee67a406280cefedec8b55fb1de130b8b
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192944"
---
# <a name="motion-controllers-in-unity"></a><span data-ttu-id="9b6b9-104">Controladores de movimento no Unity</span><span class="sxs-lookup"><span data-stu-id="9b6b9-104">Motion controllers in Unity</span></span>

<span data-ttu-id="9b6b9-105">Há duas maneiras principais de agir em sua [olhar no Unity](gaze-in-unity.md), [gestos de mão](../../design/gaze-and-commit.md#composite-gestures) e [controladores de movimento](../../design/motion-controllers.md) no HoloLens e HMD de imersão.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="9b6b9-106">Você acessa os dados de ambas as fontes de entrada espacial por meio das mesmas APIs no Unity.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="9b6b9-107">O Unity fornece duas maneiras principais de acessar dados de entrada espaciais para a realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="9b6b9-108">As APIs comuns *Input. getbutton/Input. getaxis* funcionam em vários SDKs do Unity XR, enquanto a API *interactionmanager/GestureRecognizer* específica para a realidade mista do Windows expõe o conjunto completo de dados de entrada espaciais.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="9b6b9-109">APIs de entrada do Unity XR</span><span class="sxs-lookup"><span data-stu-id="9b6b9-109">Unity XR input APIs</span></span>

<span data-ttu-id="9b6b9-110">Para novos projetos, é recomendável usar as novas APIs de entrada XR desde o início.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="9b6b9-111">Você pode encontrar mais informações sobre as [APIs XR aqui](https://docs.unity3d.com/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="9b6b9-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="9b6b9-112">Tabela de mapeamento de botões/eixos do Unity</span><span class="sxs-lookup"><span data-stu-id="9b6b9-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="9b6b9-113">O Gerenciador de entrada do Unity para controladores de movimento de realidade mista do Windows oferece suporte às IDs de botão e eixo listadas abaixo por meio das APIs *Input. getbutton/getaxis* .</span><span class="sxs-lookup"><span data-stu-id="9b6b9-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="9b6b9-114">A coluna "Windows Sr-specific" refere-se às propriedades disponíveis no tipo *InteractionSourceState* .</span><span class="sxs-lookup"><span data-stu-id="9b6b9-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="9b6b9-115">Cada uma dessas APIs é descrita detalhadamente nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="9b6b9-116">Os mapeamentos de ID de botão/eixo para a realidade mista do Windows geralmente correspondem às IDs de eixo/botão Oculus.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="9b6b9-117">Os mapeamentos de ID de botão/eixo para a realidade mista do Windows diferem dos mapeamentos do OpenVR de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="9b6b9-118">O mapeamento usa IDs de touchpad que são diferentes de Thumbstick para dar suporte a controladores com Thumbsticks e touchpads.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="9b6b9-119">O mapeamento evita sobrecarregar as IDs de botão a e X para os botões de menu para deixá-los disponíveis para os botões físicos de ABXY.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="9b6b9-120">Entrada</span><span class="sxs-lookup"><span data-stu-id="9b6b9-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="9b6b9-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">APIs comuns do Unity</a></span><span class="sxs-lookup"><span data-stu-id="9b6b9-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="9b6b9-122">(Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="9b6b9-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="9b6b9-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">API de entrada específica do Windows MR</a></span><span class="sxs-lookup"><span data-stu-id="9b6b9-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="9b6b9-124">XR. WSA. Entrada</span><span class="sxs-lookup"><span data-stu-id="9b6b9-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="9b6b9-125">À esquerda</span><span class="sxs-lookup"><span data-stu-id="9b6b9-125">Left hand</span></span> </th><th> <span data-ttu-id="9b6b9-126">À direita</span><span class="sxs-lookup"><span data-stu-id="9b6b9-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="9b6b9-127">Selecionar gatilho pressionado</span><span class="sxs-lookup"><span data-stu-id="9b6b9-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="9b6b9-128">Eixo 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="9b6b9-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="9b6b9-129">Eixo 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="9b6b9-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="9b6b9-130">selectPressed</span><span class="sxs-lookup"><span data-stu-id="9b6b9-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-131">Selecionar valor analógico do gatilho</span><span class="sxs-lookup"><span data-stu-id="9b6b9-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="9b6b9-132">Eixo 9</span><span class="sxs-lookup"><span data-stu-id="9b6b9-132">Axis 9</span></span> </td><td> <span data-ttu-id="9b6b9-133">Eixo 10</span><span class="sxs-lookup"><span data-stu-id="9b6b9-133">Axis 10</span></span> </td><td> <span data-ttu-id="9b6b9-134">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="9b6b9-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-135">Selecionar gatilho parcialmente pressionado</span><span class="sxs-lookup"><span data-stu-id="9b6b9-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="9b6b9-136">Botão 14 <i>(compatível com gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="9b6b9-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="9b6b9-137">Botão 15 <i>(compatível com gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="9b6b9-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="9b6b9-138">selectPressedAmount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="9b6b9-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-139">Botão de menu pressionado</span><span class="sxs-lookup"><span data-stu-id="9b6b9-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="9b6b9-140">Botão 6 \*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-140">Button 6\*</span></span> </td><td> <span data-ttu-id="9b6b9-141">Botão 7 \*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-141">Button 7\*</span></span> </td><td> <span data-ttu-id="9b6b9-142">menuPressed</span><span class="sxs-lookup"><span data-stu-id="9b6b9-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-143">Botão de alça pressionado</span><span class="sxs-lookup"><span data-stu-id="9b6b9-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="9b6b9-144">Eixo 11 = 1,0 (sem valores analógicos)</span><span class="sxs-lookup"><span data-stu-id="9b6b9-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="9b6b9-145">Botão 4 <i>(compatível com gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="9b6b9-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="9b6b9-146">Eixo 12 = 1,0 (sem valores analógicos)</span><span class="sxs-lookup"><span data-stu-id="9b6b9-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="9b6b9-147">Botão 5 <i>(compatível com gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="9b6b9-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="9b6b9-148">compreenderam</span><span class="sxs-lookup"><span data-stu-id="9b6b9-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-149">Thumbstick X <i>(esquerda:-1,0, direita: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="9b6b9-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="9b6b9-150">Eixo 1</span><span class="sxs-lookup"><span data-stu-id="9b6b9-150">Axis 1</span></span> </td><td> <span data-ttu-id="9b6b9-151">Eixo 4</span><span class="sxs-lookup"><span data-stu-id="9b6b9-151">Axis 4</span></span> </td><td> <span data-ttu-id="9b6b9-152">thumbstickPosition. x</span><span class="sxs-lookup"><span data-stu-id="9b6b9-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-153">Thumbstick Y <i>(superior:-1,0, inferior: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="9b6b9-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="9b6b9-154">Eixo 2</span><span class="sxs-lookup"><span data-stu-id="9b6b9-154">Axis 2</span></span> </td><td> <span data-ttu-id="9b6b9-155">Eixo 5</span><span class="sxs-lookup"><span data-stu-id="9b6b9-155">Axis 5</span></span> </td><td> <span data-ttu-id="9b6b9-156">thumbstickPosition. y</span><span class="sxs-lookup"><span data-stu-id="9b6b9-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-157">Thumbstick pressionado</span><span class="sxs-lookup"><span data-stu-id="9b6b9-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="9b6b9-158">Botão 8</span><span class="sxs-lookup"><span data-stu-id="9b6b9-158">Button 8</span></span> </td><td> <span data-ttu-id="9b6b9-159">Botão 9</span><span class="sxs-lookup"><span data-stu-id="9b6b9-159">Button 9</span></span> </td><td> <span data-ttu-id="9b6b9-160">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="9b6b9-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-161">Touchpad X <i>(esquerda:-1,0, direita: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="9b6b9-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="9b6b9-162">Eixo 17 \*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="9b6b9-163">Eixo 19 \*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="9b6b9-164">touchpadPosition. x</span><span class="sxs-lookup"><span data-stu-id="9b6b9-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-165">Touchpad Y <i>(superior:-1,0, inferior: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="9b6b9-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="9b6b9-166">Eixo 18 \*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="9b6b9-167">Eixo 20 \*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="9b6b9-168">touchpadPosition. y</span><span class="sxs-lookup"><span data-stu-id="9b6b9-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-169">Touchpad tocado</span><span class="sxs-lookup"><span data-stu-id="9b6b9-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="9b6b9-170">Botão 18 \*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-170">Button 18\*</span></span> </td><td> <span data-ttu-id="9b6b9-171">Botão 19 \*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-171">Button 19\*</span></span> </td><td> <span data-ttu-id="9b6b9-172">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="9b6b9-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-173">Touchpad pressionado</span><span class="sxs-lookup"><span data-stu-id="9b6b9-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="9b6b9-174">Botão 16 \*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-174">Button 16\*</span></span> </td><td> <span data-ttu-id="9b6b9-175">Botão 17 \*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-175">Button 17\*</span></span> </td><td> <span data-ttu-id="9b6b9-176">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="9b6b9-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-177">pose da alça de 6DoF de pose ou de ponteiro</span><span class="sxs-lookup"><span data-stu-id="9b6b9-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="9b6b9-178"><i>Segure</i> somente pose: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking. GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="9b6b9-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="9b6b9-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="9b6b9-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="9b6b9-180">Passar <i>alça</i> ou <i>ponteiro</i> como um argumento: SourceState. sourcePose. TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="9b6b9-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="9b6b9-181">origemstate. sourcePose. TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="9b6b9-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-182">Estado de acompanhamento</span><span class="sxs-lookup"><span data-stu-id="9b6b9-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="9b6b9-183"><i>A precisão da posição e o risco de perda de origem só estão disponíveis por meio da API específica do MR</i> </span><span class="sxs-lookup"><span data-stu-id="9b6b9-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="9b6b9-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">origemstate. sourcePose. positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="9b6b9-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="9b6b9-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">SourceState. Properties. sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="9b6b9-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="9b6b9-186">Essas IDs de botão/eixo diferem das IDs que o Unity usa para OpenVR devido a colisões nos mapeamentos usados por gamepads, Oculus Touch e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="9b6b9-187">Segurar pose vs. ponto de apontar</span><span class="sxs-lookup"><span data-stu-id="9b6b9-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="9b6b9-188">O Windows Mixed Reality dá suporte a controladores de movimento em uma variedade de fatores forma.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-188">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="9b6b9-189">O design de cada controlador difere em sua relação entre a posição da mão do usuário e a direção natural "encaminhar" que os aplicativos devem usar para apontar ao renderizar o controlador.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-189">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="9b6b9-190">Para representar melhor esses controladores, há dois tipos de poses que você pode investigar para cada origem de interação, a **pose de alça** e a pose do **ponteiro**.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-190">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="9b6b9-191">As coordenadas de pose pose e ponteiro representam expressas por todas as APIs do Unity nas coordenadas do mundo global do Unity.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-191">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="9b6b9-192">Segurar pose</span><span class="sxs-lookup"><span data-stu-id="9b6b9-192">Grip pose</span></span>

<span data-ttu-id="9b6b9-193">A **alça de pose** representa o local dos usuários Palm, detectado por um HoloLens ou segurando um controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-193">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="9b6b9-194">Em headsets de imersão, a alça de pose é mais bem usada para renderizar **a mão do usuário** ou **um objeto mantido na mão do usuário**.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-194">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="9b6b9-195">A pose de alça também é usada ao visualizar um controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-195">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="9b6b9-196">O **modelo renderizado** fornecido pelo Windows para um controlador de movimento usa a alça de pose como sua origem e o centro de rotação.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-196">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="9b6b9-197">A pose de alça é definida especificamente da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-197">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="9b6b9-198">A **posição de alça**: o Palm centróide ao manter o controlador naturalmente, ajustado para a esquerda ou para a direita para centralizar a posição dentro da alça.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-198">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="9b6b9-199">No controlador de movimento de realidade mista do Windows, essa posição geralmente se alinha com o botão compreender.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-199">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="9b6b9-200">O **eixo direito da orientação de alça**: quando você abre completamente a mão para formar uma pose plana de 5 dedos, o raio normal para o Palm (para frente do Palm esquerdo, para trás do Palm direito)</span><span class="sxs-lookup"><span data-stu-id="9b6b9-200">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="9b6b9-201">O **eixo de encaminhamento da orientação de alça**: quando você fecha a sua mão parcialmente (como se você mantiver o controlador), o raio que aponta para "encaminhar" por meio do tubo formado por seus dedos não-thumbs.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-201">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="9b6b9-202">O **eixo superior da orientação de alça**: o eixo superior implícito pelas definições direita e avançar.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-202">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="9b6b9-203">Você pode acessar a alça de pose por meio da API de entrada entre fornecedores do Unity (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) ou por meio da API específica do Windows Mr (*SourceState. SourcePose. TryGetPosition/Rotation*, solicitando dados de pose para o nó de **fixação** ).</span><span class="sxs-lookup"><span data-stu-id="9b6b9-203">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="9b6b9-204">Pose de ponteiro</span><span class="sxs-lookup"><span data-stu-id="9b6b9-204">Pointer pose</span></span>

<span data-ttu-id="9b6b9-205">A **pose do ponteiro** representa a ponta do controlador que está apontando para frente.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-205">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="9b6b9-206">A pose de ponteiro fornecida pelo sistema é mais bem usada para Raycast quando você está **renderizando o próprio modelo de controlador**.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-206">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="9b6b9-207">Se estiver renderizando algum outro objeto virtual no lugar do controlador, como uma arma virtual, você deve apontar um raio mais natural para esse objeto virtual, como um Ray que viaja ao longo do cilindro do modelo de pressão definido pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-207">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="9b6b9-208">Como os usuários podem ver o objeto virtual e não o controlador físico, apontar com o objeto virtual provavelmente será mais natural para aqueles que usam seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-208">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="9b6b9-209">Atualmente, a pose do ponteiro está disponível no Unity somente por meio da API específica do Windows Sr, *SourceState. sourcePose. TryGetPosition/Rotation*, passando *InteractionSourceNode. pointer* como o argumento.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-209">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="9b6b9-210">Estado de controle do controlador</span><span class="sxs-lookup"><span data-stu-id="9b6b9-210">Controller tracking state</span></span>

<span data-ttu-id="9b6b9-211">Assim como os headsets, o controlador de movimento do Windows Mixed Reality não requer nenhuma configuração de sensores de controle externo.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-211">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="9b6b9-212">Em vez disso, os controladores são acompanhados por sensores no próprio headset.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-212">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="9b6b9-213">Se o usuário mover os controladores para fora do campo de visão do headset, o Windows continuará inferindo as posições do controlador na maioria dos casos.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-213">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="9b6b9-214">Quando o controlador tiver perdido o acompanhamento Visual por tempo suficiente, as posições do controlador serão descartadas para as posições de precisão aproximada.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-214">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="9b6b9-215">Neste ponto, o sistema bloqueará o corpo do controlador para o usuário, controlando a posição do usuário à medida que eles se movimentam, ao mesmo tempo em que ainda expõe a orientação verdadeira do controlador usando seus sensores de orientação interna.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-215">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="9b6b9-216">Muitos aplicativos que usam controladores para apontar e ativar elementos de interface do usuário podem operar normalmente em precisão aproximada sem que o usuário perceba.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-216">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="9b6b9-217">A melhor maneira de ter uma ideia para isso é experimentá-lo por conta própria.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-217">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="9b6b9-218">Confira este vídeo com exemplos de conteúdo de imersão que funciona com controladores de movimento em vários Estados de controle:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-218">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="9b6b9-219">Raciocínio sobre o estado de rastreamento explicitamente</span><span class="sxs-lookup"><span data-stu-id="9b6b9-219">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="9b6b9-220">Os aplicativos que desejam tratar as posições de forma diferente com base no estado de controle podem ir além e inspecionar as propriedades no estado do controlador, como *SourceLossRisk* e *PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-220">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="9b6b9-221">Estado de acompanhamento</span><span class="sxs-lookup"><span data-stu-id="9b6b9-221">Tracking state</span></span> </th><th> <span data-ttu-id="9b6b9-222">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="9b6b9-222">SourceLossRisk</span></span> </th><th> <span data-ttu-id="9b6b9-223">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="9b6b9-223">PositionAccuracy</span></span> </th><th> <span data-ttu-id="9b6b9-224">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="9b6b9-224">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="9b6b9-225"><b>Alta precisão</b> </span><span class="sxs-lookup"><span data-stu-id="9b6b9-225"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="9b6b9-226">&lt; 1,0</span><span class="sxs-lookup"><span data-stu-id="9b6b9-226">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="9b6b9-227">Alta</span><span class="sxs-lookup"><span data-stu-id="9b6b9-227">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="9b6b9-228">true</span><span class="sxs-lookup"><span data-stu-id="9b6b9-228">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-229"><b>Alta precisão (com risco de perda)</b> </span><span class="sxs-lookup"><span data-stu-id="9b6b9-229"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="9b6b9-230">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="9b6b9-230">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="9b6b9-231">Alta</span><span class="sxs-lookup"><span data-stu-id="9b6b9-231">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="9b6b9-232">true</span><span class="sxs-lookup"><span data-stu-id="9b6b9-232">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-233"><b>Precisão aproximada</b> </span><span class="sxs-lookup"><span data-stu-id="9b6b9-233"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="9b6b9-234">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="9b6b9-234">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="9b6b9-235">Aproximado</span><span class="sxs-lookup"><span data-stu-id="9b6b9-235">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="9b6b9-236">true</span><span class="sxs-lookup"><span data-stu-id="9b6b9-236">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9b6b9-237"><b>Sem posição</b> </span><span class="sxs-lookup"><span data-stu-id="9b6b9-237"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="9b6b9-238">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="9b6b9-238">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="9b6b9-239">Aproximado</span><span class="sxs-lookup"><span data-stu-id="9b6b9-239">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="9b6b9-240">false</span><span class="sxs-lookup"><span data-stu-id="9b6b9-240">false</span></span></td>
</tr>
</table>

<span data-ttu-id="9b6b9-241">Esses Estados de acompanhamento do controlador de movimento são definidos da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-241">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="9b6b9-242">**Alta precisão:** Embora o controlador de movimento esteja dentro do campo de exibição do headset, ele geralmente fornecerá posições de alta precisão, com base no rastreamento visual.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-242">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="9b6b9-243">Um controlador móvel que deixa momentaneamente o campo de exibição ou é momentaneamente obscurecido dos sensores do headset (por exemplo, por outro lado do usuário) continuará a retornar poses de alta precisão por um curto período, com base no acompanhamento inércia do próprio controlador.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-243">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="9b6b9-244">**Alta precisão (com risco de perda):** Quando o usuário move o controlador de movimento para cima da borda do campo de exibição do headset, o headset em breve não será capaz de rastrear visualmente a posição do controlador.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-244">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="9b6b9-245">O aplicativo sabe quando o controlador atingiu esse limite de FOV vendo o **SourceLossRisk** REACH 1,0.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-245">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="9b6b9-246">Nesse ponto, o aplicativo pode optar por pausar gestos do controlador que exigem um fluxo constante de poses de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-246">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="9b6b9-247">**Precisão aproximada:** Quando o controlador tiver perdido o acompanhamento Visual por tempo suficiente, as posições do controlador serão descartadas para as posições de precisão aproximada.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-247">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="9b6b9-248">Neste ponto, o sistema bloqueará o corpo do controlador para o usuário, controlando a posição do usuário à medida que eles se movimentam, ao mesmo tempo em que ainda expõe a orientação verdadeira do controlador usando seus sensores de orientação interna.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-248">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="9b6b9-249">Muitos aplicativos que usam controladores para apontar para e ativar elementos da interface do usuário podem operar normalmente em precisão aproximada sem que o usuário perceba.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-249">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="9b6b9-250">Os aplicativos com requisitos de entrada mais pesados podem optar por detectar essa queda de **alta** precisão à precisão **aproximada** inspecionando a propriedade **PositionAccuracy** , por exemplo, para dar ao usuário um hitbox mais generosa em destinos fora da tela durante esse tempo.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-250">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="9b6b9-251">**Sem posição:** Embora o controlador possa operar com precisão aproximada por um longo tempo, às vezes o sistema sabe que até mesmo uma posição bloqueada pelo corpo não é significativa no momento.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-251">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="9b6b9-252">Por exemplo, um controlador que foi ativado pode nunca ter sido observado visualmente ou um usuário pode colocar um controlador selecionado por outra pessoa.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-252">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="9b6b9-253">Naqueles momentos, o sistema não fornecerá nenhuma posição ao aplicativo e *TryGetPosition* retornará false.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-253">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="9b6b9-254">APIs comuns do Unity (Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="9b6b9-254">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="9b6b9-255">**Namespace:** *UnityEngine*, *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-255">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="9b6b9-256">**Tipos**: *Input*, *XR. InputTracking*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-256">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="9b6b9-257">No momento, o Unity usa suas APIs de *entrada geral. getbutton/Input. getaxis* para expor a entrada para [o SDK do OCULUS](https://docs.unity3d.com/Manual/OculusControllers.html), [o SDK do OpenVR e a](https://docs.unity3d.com/Manual/OpenVRControllers.html) realidade mista do Windows, incluindo controladores de mãos e de movimento.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-257">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="9b6b9-258">Se seu aplicativo usa essas APIs para entrada, ele pode facilmente dar suporte a controladores de movimento em vários SDKs do XR, incluindo a realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-258">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="9b6b9-259">Obtendo o estado pressionado de um botão lógico</span><span class="sxs-lookup"><span data-stu-id="9b6b9-259">Getting a logical button's pressed state</span></span>

<span data-ttu-id="9b6b9-260">Para usar as APIs de entrada gerais da Unity, você normalmente começará com a vinculação de botões e eixos a nomes lógicos no [Gerenciador de entrada do Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), ligando um botão ou IDs de eixo a cada nome.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-260">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="9b6b9-261">Em seguida, você pode escrever código que se refere a esse botão lógico/nome do eixo.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-261">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="9b6b9-262">Por exemplo, para mapear o botão de gatilho do controlador de movimento à esquerda para a ação enviar, acesse **editar > configurações do projeto > entrada** no Unity e expanda as propriedades da seção enviar em eixos.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-262">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="9b6b9-263">Altere o **botão positivo** ou a propriedade do **botão Alt positivo** para ler o **botão 14 do joystick**, desta forma:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-263">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="9b6b9-264">![InputManager do Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="9b6b9-264">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="9b6b9-265">*InputManager do Unity*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-265">*Unity InputManager*</span></span>

<span data-ttu-id="9b6b9-266">O script pode, então, verificar a ação de envio usando *Input. getbutton*:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-266">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="9b6b9-267">Você pode adicionar mais botões lógicos alterando a propriedade **tamanho** em **eixos**.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-267">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="9b6b9-268">Obtendo um estado de botão físico pressionado diretamente</span><span class="sxs-lookup"><span data-stu-id="9b6b9-268">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="9b6b9-269">Você também pode acessar os botões manualmente por seu nome totalmente qualificado, usando *Input. GetKey*:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-269">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="9b6b9-270">Obter uma pose do controlador de movimento ou mão</span><span class="sxs-lookup"><span data-stu-id="9b6b9-270">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="9b6b9-271">Você pode acessar a posição e a rotação do controlador, usando o *XR. InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-271">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="9b6b9-272">O código acima representa a pose de alça do controlador (onde o usuário mantém o controlador), o que é útil para renderizar um gumes ou armar na mão do usuário ou em um modelo do próprio controlador.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-272">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="9b6b9-273">A relação entre essa alça de fixação e a pose do ponteiro (onde a ponta do controlador está apontando) pode diferir entre os controladores.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-273">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="9b6b9-274">Neste momento, o acesso à pose do ponteiro do controlador só é possível por meio da API de entrada específica do MR, descrita nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-274">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="9b6b9-275">APIs específicas do Windows (XR. WSA. Entrada</span><span class="sxs-lookup"><span data-stu-id="9b6b9-275">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="9b6b9-276">Se o seu projeto estiver usando qualquer uma das XR. APIs de WSA, que estão sendo divididas em favor do SDK do XR em versões futuras do Unity.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-276">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="9b6b9-277">Para novos projetos, é recomendável usar o SDK do XR desde o início.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-277">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="9b6b9-278">Você pode encontrar mais informações sobre as [APIs e o sistema de entrada XR aqui](https://docs.unity3d.com/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="9b6b9-278">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="9b6b9-279">**Namespace:** *UnityEngine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-279">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="9b6b9-280">**Tipos**: *interactionmanager*, *InteractionSourceState*, *peractionname*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-280">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="9b6b9-281">Para obter informações mais detalhadas sobre a entrada da mão de realidade mista do Windows (para o HoloLens) e os controladores de movimento, você pode optar por usar as APIs de entrada espaciais específicas do Windows no namespace *UnityEngine. XR. WSA. Input* .</span><span class="sxs-lookup"><span data-stu-id="9b6b9-281">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="9b6b9-282">Isso permite que você acesse informações adicionais, como precisão de posição ou tipo de fonte, permitindo que você diga as mãos e os controladores.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-282">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="9b6b9-283">Sondando o estado dos controladores de mãos e de movimento</span><span class="sxs-lookup"><span data-stu-id="9b6b9-283">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="9b6b9-284">Você pode sondar o estado deste quadro para cada fonte de interação (controlador de mão ou de movimento) usando o método *GetCurrentReading* .</span><span class="sxs-lookup"><span data-stu-id="9b6b9-284">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="9b6b9-285">Cada *InteractionSourceState* que você retorna representa uma fonte de interação no momento atual.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-285">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="9b6b9-286">O *InteractionSourceState* expõe informações como:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-286">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="9b6b9-287">Que [tipos de prensas](../../design/motion-controllers.md) estão ocorrendo (Select/menu/Segure/Touchpad/Thumbstick)</span><span class="sxs-lookup"><span data-stu-id="9b6b9-287">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="9b6b9-288">Outros dados específicos de controladores de movimento, como as coordenadas XY do Touchpad e/ou do Thumbstick e o estado tocado</span><span class="sxs-lookup"><span data-stu-id="9b6b9-288">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="9b6b9-289">O InteractionSourceKind para saber se a origem é uma mão ou um controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="9b6b9-289">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="9b6b9-290">Sondagem para encaminhar representações de renderização previstas</span><span class="sxs-lookup"><span data-stu-id="9b6b9-290">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="9b6b9-291">Durante a sondagem de dados de origem de interação de mãos e controladores, as poses que você obtém são as mais previstas para o momento em que o fótons do quadro atingirá os olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-291">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="9b6b9-292">As poses de encaminhamento antecipado são mais bem usadas para **renderizar** o controlador ou um objeto mantido em cada quadro.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-292">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="9b6b9-293">Se você estiver direcionando um determinado Press ou Release com o controlador, isso será mais preciso se você usar as APIs de eventos de histórico descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-293">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="9b6b9-294">Você também pode obter a pose de cabeça prevista para este quadro atual.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-294">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="9b6b9-295">Assim como acontece com o pose de origem, isso é útil para **renderizar** um cursor, embora o direcionamento de uma determinada prensa ou versão seja mais preciso se você usar as APIs de evento históricas descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-295">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="9b6b9-296">Tratamento de eventos de origem de interação</span><span class="sxs-lookup"><span data-stu-id="9b6b9-296">Handling interaction source events</span></span>

<span data-ttu-id="9b6b9-297">Para lidar com eventos de entrada à medida que eles acontecem com seus dados históricos de histórico precisos, você pode manipular eventos de origem de interação em vez de sondagem.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-297">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="9b6b9-298">Para lidar com eventos de origem de interação:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-298">To handle interaction source events:</span></span>
* <span data-ttu-id="9b6b9-299">Registre-se para um evento de entrada entre *ações* .</span><span class="sxs-lookup"><span data-stu-id="9b6b9-299">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="9b6b9-300">Para cada tipo de evento de interação em que você está interessado, você precisa assiná-lo.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-300">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="9b6b9-301">Manipule o evento.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-301">Handle the event.</span></span> <span data-ttu-id="9b6b9-302">Depois de se inscrever em um evento de interação, você receberá o retorno de chamada quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-302">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="9b6b9-303">No exemplo de *SourcePressed* , isso será depois que a origem for detectada e antes de ser liberada ou perdida.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-303">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="9b6b9-304">Como parar de lidar com um evento</span><span class="sxs-lookup"><span data-stu-id="9b6b9-304">How to stop handling an event</span></span>

<span data-ttu-id="9b6b9-305">Você precisa parar de lidar com um evento quando não estiver mais interessado no evento ou se estiver destruindo o objeto que assinou o evento.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-305">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="9b6b9-306">Para parar de lidar com o evento, cancele a assinatura do evento.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-306">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="9b6b9-307">Lista de eventos de origem de interação</span><span class="sxs-lookup"><span data-stu-id="9b6b9-307">List of interaction source events</span></span>

<span data-ttu-id="9b6b9-308">Os eventos de origem de interação disponíveis são:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-308">The available interaction source events are:</span></span>
* <span data-ttu-id="9b6b9-309">*InteractionSourceDetected* (a origem se torna ativa)</span><span class="sxs-lookup"><span data-stu-id="9b6b9-309">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="9b6b9-310">*InteractionSourceLost* (torna-se inativo)</span><span class="sxs-lookup"><span data-stu-id="9b6b9-310">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="9b6b9-311">*InteractionSourcePressed* (toque, pressionamento de botão ou "selecionar" desmarcado)</span><span class="sxs-lookup"><span data-stu-id="9b6b9-311">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="9b6b9-312">*InteractionSourceReleased* (fim de um toque, botão liberado ou fim de "selecionar" exmovida)</span><span class="sxs-lookup"><span data-stu-id="9b6b9-312">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="9b6b9-313">*InteractionSourceUpdated* (move ou altera qualquer Estado)</span><span class="sxs-lookup"><span data-stu-id="9b6b9-313">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="9b6b9-314">Os eventos de direcionamento histórico representam que correspondem mais precisamente a uma prensa ou liberação</span><span class="sxs-lookup"><span data-stu-id="9b6b9-314">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="9b6b9-315">As APIs de sondagem descritas anteriormente fornecem às suas representações previstas de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-315">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="9b6b9-316">Embora essas representações previstas sejam melhores para renderizar o controlador ou um objeto portátil Virtual, as poses futuras não são ideais para o direcionamento, por dois motivos principais:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-316">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="9b6b9-317">Quando o usuário pressiona um botão em um controlador, pode haver cerca de 20 ms de latência sem fio sobre o Bluetooth antes que o sistema receba a prensa.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-317">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="9b6b9-318">Em seguida, se você estiver usando uma pose prevista para o futuro, haveria outro 10-20 ms de previsão de encaminhamento aplicado ao destino quando o fótons do quadro atual atingirá os olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-318">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="9b6b9-319">Isso significa que a sondagem fornece uma pose de origem ou uma localização de cabeçalho que é de 30-40 MS forward de onde a cabeça do usuário e as mãos realmente estavam de volta quando ocorreu a ocorrência de Press ou Release.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-319">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="9b6b9-320">Para entrada à mão do HoloLens, enquanto não há atraso de transmissão sem fio, há um atraso de processamento semelhante para detectar a prensa.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-320">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="9b6b9-321">Para ter um destino com precisão com base na intenção original do usuário para um pressionamento de mão ou de controlador, você deve usar a pose de origem histórica ou de cabeçalho desse evento de entrada *InteractionSourcePressed* ou *InteractionSourceReleased* .</span><span class="sxs-lookup"><span data-stu-id="9b6b9-321">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="9b6b9-322">Você pode direcionar um Press ou Release com dados históricos de pose do cabeçalho do usuário ou de seu controlador:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-322">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="9b6b9-323">A parte de cabeça no momento em que uma ocorrência de gesto ou controlador ocorreu, que pode ser **usada para determinar** o que o usuário estava [nuvensndo](../../design/gaze-and-commit.md) :</span><span class="sxs-lookup"><span data-stu-id="9b6b9-323">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="9b6b9-324">A origem representa no momento em que uma ocorrência de controlador de movimento ocorreu, que pode ser **usada para determinar a que o** usuário estava apontando o controlador.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-324">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="9b6b9-325">Esse será o estado do controlador que sofreu a prensa.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-325">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="9b6b9-326">Se você estiver renderizando o próprio controlador, poderá solicitar a pose do ponteiro em vez da pose de alça, para atingir o direcionamento de raio a partir do que o usuário considerará a dica natural desse controlador renderizado:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-326">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="9b6b9-327">Exemplo de manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="9b6b9-327">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk-v2"></a><span data-ttu-id="9b6b9-328">Controladores de movimento no MRTK v2</span><span class="sxs-lookup"><span data-stu-id="9b6b9-328">Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="9b6b9-329">Você pode acessar o [gesto e o controlador de movimento](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html) do Gerenciador de entrada.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-329">You can access [gesture and motion controller](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html) from the input Manager.</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="9b6b9-330">Acompanhe com tutoriais</span><span class="sxs-lookup"><span data-stu-id="9b6b9-330">Follow along with tutorials</span></span>

<span data-ttu-id="9b6b9-331">Os tutoriais passo a passo, com exemplos de personalização mais detalhados, estão disponíveis na Academia de realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-331">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="9b6b9-332">Entrada do MR 211: gesto</span><span class="sxs-lookup"><span data-stu-id="9b6b9-332">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="9b6b9-333">Entrada do MR 213: controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="9b6b9-333">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="9b6b9-334">[![Entrada MR 213-controlador de movimento](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="9b6b9-334">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="9b6b9-335">*Entrada MR 213-controlador de movimento*</span><span class="sxs-lookup"><span data-stu-id="9b6b9-335">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="9b6b9-336">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="9b6b9-336">Next Development Checkpoint</span></span>

<span data-ttu-id="9b6b9-337">Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos blocos de construção do MRTK Core.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-337">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="9b6b9-338">Deste ponto, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-338">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9b6b9-339">Acompanhamento de mãos e olhos</span><span class="sxs-lookup"><span data-stu-id="9b6b9-339">Hand and eye tracking</span></span>](hand-eye-in-unit.md)

<span data-ttu-id="9b6b9-340">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="9b6b9-340">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9b6b9-341">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="9b6b9-341">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="9b6b9-342">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="9b6b9-342">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b6b9-343">Veja também</span><span class="sxs-lookup"><span data-stu-id="9b6b9-343">See also</span></span>

* [<span data-ttu-id="9b6b9-344">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="9b6b9-344">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="9b6b9-345">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="9b6b9-345">Motion controllers</span></span>](../../design/motion-controllers.md)
