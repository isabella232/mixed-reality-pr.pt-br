---
title: Controladores de movimento no Unity
description: Saiba como agir em seu olhar no Unity com a entrada do controlador de movimento usando XR e APIs comuns de botão e eixo.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: controladores de movimento, unity, entrada, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, MRTK, Kit de Ferramentas de Realidade Misturada
ms.openlocfilehash: d8f9ce292c0ab1cfa89faf58f0e5b90322192b35
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394510"
---
# <a name="motion-controllers-in-unity"></a><span data-ttu-id="aaaa8-104">Controladores de movimento no Unity</span><span class="sxs-lookup"><span data-stu-id="aaaa8-104">Motion controllers in Unity</span></span>

<span data-ttu-id="aaaa8-105">Há duas maneiras principais de agir em seu olhar [](../../design/motion-controllers.md) no [Unity,](gaze-in-unity.md) [gestos](../../design/gaze-and-commit.md#composite-gestures) de mão e controladores de movimento no HoloLens e HMD imersivo.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="aaaa8-106">Você acessa os dados de ambas as fontes de entrada espacial por meio das mesmas APIs no Unity.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="aaaa8-107">O Unity fornece duas maneiras principais de acessar dados de entrada espaciais para Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="aaaa8-108">As APIs *Input.GetButton/Input.GetAxis* comuns funcionam em vários SDKs XR do Unity, enquanto a API *InteractionManager/GestureRecognizer* específica Windows Mixed Reality expõe o conjunto completo de dados de entrada espaciais.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="aaaa8-109">APIs de entrada do Unity XR</span><span class="sxs-lookup"><span data-stu-id="aaaa8-109">Unity XR input APIs</span></span>

<span data-ttu-id="aaaa8-110">Para novos projetos, é recomendável usar as novas APIs de entrada XR desde o início.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="aaaa8-111">Você pode encontrar mais informações sobre as [APIs XR aqui](https://docs.unity3d.com/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="aaaa8-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="aaaa8-112">Tabela de mapeamento de eixo/botão do Unity</span><span class="sxs-lookup"><span data-stu-id="aaaa8-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="aaaa8-113">O Gerenciador de Entrada do Unity para controladores Windows Mixed Reality de movimento do Unity dá suporte às IDs do botão e do eixo listadas abaixo por meio das APIs *Input.GetButton/GetAxis.*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="aaaa8-114">A coluna "Específica do Windows MR" refere-se às propriedades disponíveis fora do *tipo InteractionSourceState.*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="aaaa8-115">Cada uma dessas APIs é descrita em detalhes nas seções abaixo.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="aaaa8-116">Os mapeamentos de ID do botão/eixo para Windows Mixed Reality geralmente corresponderem às IDs de botão/eixo do Oculus.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="aaaa8-117">Os mapeamentos de ID do botão/eixo Windows Mixed Reality diferentes dos mapeamentos do OpenVR de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="aaaa8-118">O mapeamento usa IDs de touchpad diferentes do thumbstick para dar suporte a controladores com thumbsticks e touchpads.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="aaaa8-119">O mapeamento evita sobrecarregar as IDs de botão A e X dos botões Menu para deixá-las disponíveis para os botões FÍSICOS DO ABXY.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="aaaa8-120">Entrada</span><span class="sxs-lookup"><span data-stu-id="aaaa8-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="aaaa8-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">APIs comuns do Unity</a></span><span class="sxs-lookup"><span data-stu-id="aaaa8-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="aaaa8-122">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="aaaa8-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">API de Entrada específica do WINDOWS MR</a></span><span class="sxs-lookup"><span data-stu-id="aaaa8-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="aaaa8-124">(XR. Wsa. Entrada)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="aaaa8-125">Mão esquerda</span><span class="sxs-lookup"><span data-stu-id="aaaa8-125">Left hand</span></span> </th><th> <span data-ttu-id="aaaa8-126">Mão direita</span><span class="sxs-lookup"><span data-stu-id="aaaa8-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="aaaa8-127">Selecionar gatilho pressionado</span><span class="sxs-lookup"><span data-stu-id="aaaa8-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="aaaa8-128">Eixo 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="aaaa8-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="aaaa8-129">Eixo 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="aaaa8-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="aaaa8-130">selectPressed</span><span class="sxs-lookup"><span data-stu-id="aaaa8-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-131">Selecionar o valor análogo do gatilho</span><span class="sxs-lookup"><span data-stu-id="aaaa8-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="aaaa8-132">Eixo 9</span><span class="sxs-lookup"><span data-stu-id="aaaa8-132">Axis 9</span></span> </td><td> <span data-ttu-id="aaaa8-133">Eixo 10</span><span class="sxs-lookup"><span data-stu-id="aaaa8-133">Axis 10</span></span> </td><td> <span data-ttu-id="aaaa8-134">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="aaaa8-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-135">Selecionar gatilho parcialmente pressionado</span><span class="sxs-lookup"><span data-stu-id="aaaa8-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="aaaa8-136">Botão 14 <i>(compat do gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="aaaa8-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="aaaa8-137">Botão 15 <i>(compat do gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="aaaa8-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="aaaa8-138">selectPressedAmount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="aaaa8-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-139">Botão de menu pressionado</span><span class="sxs-lookup"><span data-stu-id="aaaa8-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="aaaa8-140">Botão 6\*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-140">Button 6\*</span></span> </td><td> <span data-ttu-id="aaaa8-141">Botão 7\*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-141">Button 7\*</span></span> </td><td> <span data-ttu-id="aaaa8-142">menuPressed</span><span class="sxs-lookup"><span data-stu-id="aaaa8-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-143">Botão de segurar pressionado</span><span class="sxs-lookup"><span data-stu-id="aaaa8-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="aaaa8-144">Eixo 11 = 1,0 (sem valores análogo)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="aaaa8-145">Botão 4 <i>(compat do gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="aaaa8-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="aaaa8-146">Eixo 12 = 1,0 (sem valores análogo)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="aaaa8-147">Botão 5 <i>(compat do gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="aaaa8-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="aaaa8-148">Agarrou</span><span class="sxs-lookup"><span data-stu-id="aaaa8-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-149">Thumbstick X <i>(esquerda: -1.0, direita: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="aaaa8-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="aaaa8-150">Eixo 1</span><span class="sxs-lookup"><span data-stu-id="aaaa8-150">Axis 1</span></span> </td><td> <span data-ttu-id="aaaa8-151">Eixo 4</span><span class="sxs-lookup"><span data-stu-id="aaaa8-151">Axis 4</span></span> </td><td> <span data-ttu-id="aaaa8-152">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="aaaa8-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-153">Thumbstick Y <i>(superior: -1.0, inferior: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="aaaa8-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="aaaa8-154">Eixo 2</span><span class="sxs-lookup"><span data-stu-id="aaaa8-154">Axis 2</span></span> </td><td> <span data-ttu-id="aaaa8-155">Eixo 5</span><span class="sxs-lookup"><span data-stu-id="aaaa8-155">Axis 5</span></span> </td><td> <span data-ttu-id="aaaa8-156">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="aaaa8-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-157">Thumbstick pressionado</span><span class="sxs-lookup"><span data-stu-id="aaaa8-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="aaaa8-158">Botão 8</span><span class="sxs-lookup"><span data-stu-id="aaaa8-158">Button 8</span></span> </td><td> <span data-ttu-id="aaaa8-159">Botão 9</span><span class="sxs-lookup"><span data-stu-id="aaaa8-159">Button 9</span></span> </td><td> <span data-ttu-id="aaaa8-160">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="aaaa8-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-161">Touchpad X <i>(esquerda: -1.0, direita: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="aaaa8-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="aaaa8-162">Eixo 17\*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="aaaa8-163">Eixo 19\*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="aaaa8-164">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="aaaa8-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-165">Touchpad Y <i>(superior: -1.0, inferior: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="aaaa8-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="aaaa8-166">Eixo 18\*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="aaaa8-167">Eixo 20\*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="aaaa8-168">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="aaaa8-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-169">Touchpad tocada</span><span class="sxs-lookup"><span data-stu-id="aaaa8-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="aaaa8-170">Botão 18\*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-170">Button 18\*</span></span> </td><td> <span data-ttu-id="aaaa8-171">Botão 19\*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-171">Button 19\*</span></span> </td><td> <span data-ttu-id="aaaa8-172">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="aaaa8-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-173">Touchpad pressionado</span><span class="sxs-lookup"><span data-stu-id="aaaa8-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="aaaa8-174">Botão 16\*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-174">Button 16\*</span></span> </td><td> <span data-ttu-id="aaaa8-175">Botão 17\*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-175">Button 17\*</span></span> </td><td> <span data-ttu-id="aaaa8-176">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="aaaa8-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-177">6 Pose ou pose de ponteiro da mão deDoF</span><span class="sxs-lookup"><span data-stu-id="aaaa8-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="aaaa8-178"><i>Pose</i> de mão apenas: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="aaaa8-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="aaaa8-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">Xr. InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="aaaa8-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="aaaa8-180">Passar <i>a mão</i> ou <i>ponteiro</i> como um argumento: sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="aaaa8-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="aaaa8-181">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="aaaa8-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-182">Estado de acompanhamento</span><span class="sxs-lookup"><span data-stu-id="aaaa8-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="aaaa8-183"><i>A precisão da posição e o risco de perda de origem só estão disponíveis por meio da API específica do MR</i> </span><span class="sxs-lookup"><span data-stu-id="aaaa8-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="aaaa8-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="aaaa8-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="aaaa8-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="aaaa8-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="aaaa8-186">Essas IDs de botão/eixo diferem das IDs que o Unity usa para OpenVR devido a colisões nos mapeamentos usados por gamepads, Oculus Touch e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

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

### <a name="openxr"></a><span data-ttu-id="aaaa8-187">OpenXR</span><span class="sxs-lookup"><span data-stu-id="aaaa8-187">OpenXR</span></span>

<span data-ttu-id="aaaa8-188">Para saber as noções básicas sobre interações de realidade misturada no Unity, visite o Manual do [Unity para Entrada XR do Unity.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-188">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="aaaa8-189">Esta documentação do Unity aborda os mapeamentos de entradas específicas do controlador para entradas mais generalizáveis **InputFeatureUsage** s, como as entradas XR disponíveis podem ser identificadas e categorizadas, como ler dados dessas entradas e muito mais.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-189">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="aaaa8-190">O Plug-in OpenXR de Realidade Misturada fornece perfis de interação de entrada adicionais, mapeados para **InputFeatureUsage** s padrão, conforme detalhado abaixo:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-190">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="aaaa8-191">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="aaaa8-191">InputFeatureUsage</span></span> | <span data-ttu-id="aaaa8-192">Controlador HP Reverb G2 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-192">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="aaaa8-193">Mão do HoloLens (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-193">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="aaaa8-194">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="aaaa8-194">primary2DAxis</span></span> | <span data-ttu-id="aaaa8-195">Joystick</span><span class="sxs-lookup"><span data-stu-id="aaaa8-195">Joystick</span></span> | |
| <span data-ttu-id="aaaa8-196">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="aaaa8-196">primary2DAxisClick</span></span> | <span data-ttu-id="aaaa8-197">Mouse – Click</span><span class="sxs-lookup"><span data-stu-id="aaaa8-197">Joystick - Click</span></span> | |
| <span data-ttu-id="aaaa8-198">gatilho</span><span class="sxs-lookup"><span data-stu-id="aaaa8-198">trigger</span></span> | <span data-ttu-id="aaaa8-199">Gatilho</span><span class="sxs-lookup"><span data-stu-id="aaaa8-199">Trigger</span></span>  | |
| <span data-ttu-id="aaaa8-200">Aperto</span><span class="sxs-lookup"><span data-stu-id="aaaa8-200">grip</span></span> | <span data-ttu-id="aaaa8-201">Dimensiona</span><span class="sxs-lookup"><span data-stu-id="aaaa8-201">Grip</span></span> | <span data-ttu-id="aaaa8-202">Toque ou aperte o ar</span><span class="sxs-lookup"><span data-stu-id="aaaa8-202">Air tap or squeeze</span></span> |
| <span data-ttu-id="aaaa8-203">primaryButton</span><span class="sxs-lookup"><span data-stu-id="aaaa8-203">primaryButton</span></span> | <span data-ttu-id="aaaa8-204">[X/A]-Pressione</span><span class="sxs-lookup"><span data-stu-id="aaaa8-204">[X/A] - Press</span></span> | <span data-ttu-id="aaaa8-205">Fechar e abrir dedos indicador e polegar</span><span class="sxs-lookup"><span data-stu-id="aaaa8-205">Air tap</span></span> |
| <span data-ttu-id="aaaa8-206">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="aaaa8-206">secondaryButton</span></span> | <span data-ttu-id="aaaa8-207">[S/B]-Pressione</span><span class="sxs-lookup"><span data-stu-id="aaaa8-207">[Y/B] - Press</span></span> | |
| <span data-ttu-id="aaaa8-208">gripButton</span><span class="sxs-lookup"><span data-stu-id="aaaa8-208">gripButton</span></span> | <span data-ttu-id="aaaa8-209">Segure a tecla</span><span class="sxs-lookup"><span data-stu-id="aaaa8-209">Grip - Press</span></span> | |
| <span data-ttu-id="aaaa8-210">triggerButton</span><span class="sxs-lookup"><span data-stu-id="aaaa8-210">triggerButton</span></span> | <span data-ttu-id="aaaa8-211">Gatilho-Pressione</span><span class="sxs-lookup"><span data-stu-id="aaaa8-211">Trigger - Press</span></span> | |
| <span data-ttu-id="aaaa8-212">menuButton</span><span class="sxs-lookup"><span data-stu-id="aaaa8-212">menuButton</span></span> | <span data-ttu-id="aaaa8-213">Menu</span><span class="sxs-lookup"><span data-stu-id="aaaa8-213">Menu</span></span> | |

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="aaaa8-214">Segurar pose vs. ponto de apontar</span><span class="sxs-lookup"><span data-stu-id="aaaa8-214">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="aaaa8-215">O Windows Mixed Reality dá suporte a controladores de movimento em uma variedade de fatores forma.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-215">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="aaaa8-216">O design de cada controlador difere em sua relação entre a posição da mão do usuário e a direção natural "encaminhar" que os aplicativos devem usar para apontar ao renderizar o controlador.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-216">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="aaaa8-217">Para representar melhor esses controladores, há dois tipos de poses que você pode investigar para cada origem de interação, a **pose de alça** e a pose do **ponteiro**.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-217">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="aaaa8-218">As coordenadas de pose pose e ponteiro representam expressas por todas as APIs do Unity nas coordenadas do mundo global do Unity.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-218">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="aaaa8-219">Segurar pose</span><span class="sxs-lookup"><span data-stu-id="aaaa8-219">Grip pose</span></span>

<span data-ttu-id="aaaa8-220">A **alça de pose** representa o local dos usuários Palm, detectado por um HoloLens ou segurando um controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-220">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="aaaa8-221">Em headsets de imersão, a alça de pose é mais bem usada para renderizar **a mão do usuário** ou **um objeto mantido na mão do usuário**.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-221">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="aaaa8-222">A pose de alça também é usada ao visualizar um controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-222">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="aaaa8-223">O **modelo renderizado** fornecido pelo Windows para um controlador de movimento usa a alça de pose como sua origem e o centro de rotação.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-223">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="aaaa8-224">A pose de alça é definida especificamente da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-224">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="aaaa8-225">A **posição de alça**: o Palm centróide ao manter o controlador naturalmente, ajustado para a esquerda ou para a direita para centralizar a posição dentro da alça.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-225">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="aaaa8-226">No controlador de movimento de realidade mista do Windows, essa posição geralmente se alinha com o botão compreender.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-226">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="aaaa8-227">O **eixo direito da orientação de alça**: quando você abre completamente a mão para formar uma pose plana de 5 dedos, o raio normal para o Palm (para frente do Palm esquerdo, para trás do Palm direito)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-227">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="aaaa8-228">O **eixo de encaminhamento da orientação de alça**: quando você fecha a sua mão parcialmente (como se você mantiver o controlador), o raio que aponta para "encaminhar" por meio do tubo formado por seus dedos não-thumbs.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-228">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="aaaa8-229">O **eixo superior da orientação de alça**: o eixo superior implícito pelas definições direita e avançar.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-229">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="aaaa8-230">Você pode acessar a alça de pose por meio da API de entrada entre fornecedores do Unity (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) ou por meio da API específica do Windows Mr (*SourceState. SourcePose. TryGetPosition/Rotation*, solicitando dados de pose para o nó de **fixação** ).</span><span class="sxs-lookup"><span data-stu-id="aaaa8-230">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="aaaa8-231">Pose de ponteiro</span><span class="sxs-lookup"><span data-stu-id="aaaa8-231">Pointer pose</span></span>

<span data-ttu-id="aaaa8-232">A **pose do ponteiro** representa a ponta do controlador que está apontando para frente.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-232">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="aaaa8-233">A pose de ponteiro fornecida pelo sistema é mais bem usada para Raycast quando você está **renderizando o próprio modelo de controlador**.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-233">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="aaaa8-234">Se estiver renderizando algum outro objeto virtual no lugar do controlador, como uma arma virtual, você deve apontar um raio mais natural para esse objeto virtual, como um Ray que viaja ao longo do cilindro do modelo de pressão definido pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-234">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="aaaa8-235">Como os usuários podem ver o objeto virtual e não o controlador físico, apontar com o objeto virtual provavelmente será mais natural para aqueles que usam seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-235">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="aaaa8-236">Atualmente, a pose do ponteiro está disponível no Unity somente por meio da API específica do Windows Sr, *SourceState. sourcePose. TryGetPosition/Rotation*, passando *InteractionSourceNode. pointer* como o argumento.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-236">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

### <a name="openxr"></a><span data-ttu-id="aaaa8-237">OpenXR</span><span class="sxs-lookup"><span data-stu-id="aaaa8-237">OpenXR</span></span> 

<span data-ttu-id="aaaa8-238">Você tem acesso a dois conjuntos de poses por meio de interações de entrada OpenXR:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-238">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="aaaa8-239">A alça representa a renderização de objetos à mão</span><span class="sxs-lookup"><span data-stu-id="aaaa8-239">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="aaaa8-240">O objetivo se destaca no mundo.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-240">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="aaaa8-241">Mais informações sobre esse design e as diferenças entre as duas poses podem ser encontradas na [especificação OpenXR-subcaminhos de entrada](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span><span class="sxs-lookup"><span data-stu-id="aaaa8-241">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="aaaa8-242">As poses fornecidas pelo InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** e **DeviceAngularVelocity** representam a pose de **alça** de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-242">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="aaaa8-243">Os InputFeatureUsages relacionados a pose são definidos no [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)do Unity.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-243">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="aaaa8-244">As poses fornecidas pelo InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** e **PointerAngularVelocity** representam a pose de **AIM** de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-244">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="aaaa8-245">Esses InputFeatureUsages não são definidos em nenhum arquivo C# incluído, portanto, você precisará definir seu próprio InputFeatureUsages da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-245">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

## <a name="haptics"></a><span data-ttu-id="aaaa8-246">Haptics</span><span class="sxs-lookup"><span data-stu-id="aaaa8-246">Haptics</span></span>

<span data-ttu-id="aaaa8-247">Para obter informações sobre como usar o haptics no sistema de entrada XR da Unity, a documentação pode ser encontrada no [manual do Unity para o Unity XR Input-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span><span class="sxs-lookup"><span data-stu-id="aaaa8-247">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="aaaa8-248">Estado de controle do controlador</span><span class="sxs-lookup"><span data-stu-id="aaaa8-248">Controller tracking state</span></span>

<span data-ttu-id="aaaa8-249">Assim como os headsets, o controlador de movimento do Windows Mixed Reality não requer nenhuma configuração de sensores de controle externo.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-249">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="aaaa8-250">Em vez disso, os controladores são acompanhados por sensores no próprio headset.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-250">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="aaaa8-251">Se o usuário mover os controladores para fora do campo de visão do headset, o Windows continuará inferindo as posições do controlador na maioria dos casos.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-251">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="aaaa8-252">Quando o controlador tiver perdido o acompanhamento Visual por tempo suficiente, as posições do controlador serão descartadas para as posições de precisão aproximada.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-252">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="aaaa8-253">Neste ponto, o sistema bloqueará o corpo do controlador para o usuário, controlando a posição do usuário à medida que eles se movimentam, ao mesmo tempo em que ainda expõe a orientação verdadeira do controlador usando seus sensores de orientação interna.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-253">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="aaaa8-254">Muitos aplicativos que usam controladores para apontar e ativar elementos de interface do usuário podem operar normalmente em precisão aproximada sem que o usuário perceba.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-254">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="aaaa8-255">Raciocínio sobre o estado de rastreamento explicitamente</span><span class="sxs-lookup"><span data-stu-id="aaaa8-255">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="aaaa8-256">Os aplicativos que desejam tratar as posições de forma diferente com base no estado de controle podem ir além e inspecionar as propriedades no estado do controlador, como *SourceLossRisk* e *PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-256">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="aaaa8-257">Estado de acompanhamento</span><span class="sxs-lookup"><span data-stu-id="aaaa8-257">Tracking state</span></span> </th><th> <span data-ttu-id="aaaa8-258">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="aaaa8-258">SourceLossRisk</span></span> </th><th> <span data-ttu-id="aaaa8-259">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="aaaa8-259">PositionAccuracy</span></span> </th><th> <span data-ttu-id="aaaa8-260">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="aaaa8-260">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="aaaa8-261"><b>Alta precisão</b> </span><span class="sxs-lookup"><span data-stu-id="aaaa8-261"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="aaaa8-262">&lt; 1,0</span><span class="sxs-lookup"><span data-stu-id="aaaa8-262">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="aaaa8-263">Alta</span><span class="sxs-lookup"><span data-stu-id="aaaa8-263">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="aaaa8-264">true</span><span class="sxs-lookup"><span data-stu-id="aaaa8-264">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-265"><b>Alta precisão (com risco de perda)</b> </span><span class="sxs-lookup"><span data-stu-id="aaaa8-265"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="aaaa8-266">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="aaaa8-266">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="aaaa8-267">Alta</span><span class="sxs-lookup"><span data-stu-id="aaaa8-267">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="aaaa8-268">true</span><span class="sxs-lookup"><span data-stu-id="aaaa8-268">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-269"><b>Precisão aproximada</b> </span><span class="sxs-lookup"><span data-stu-id="aaaa8-269"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="aaaa8-270">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="aaaa8-270">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="aaaa8-271">Aproximado</span><span class="sxs-lookup"><span data-stu-id="aaaa8-271">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="aaaa8-272">true</span><span class="sxs-lookup"><span data-stu-id="aaaa8-272">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="aaaa8-273"><b>Sem posição</b> </span><span class="sxs-lookup"><span data-stu-id="aaaa8-273"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="aaaa8-274">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="aaaa8-274">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="aaaa8-275">Aproximado</span><span class="sxs-lookup"><span data-stu-id="aaaa8-275">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="aaaa8-276">false</span><span class="sxs-lookup"><span data-stu-id="aaaa8-276">false</span></span></td>
</tr>
</table>

<span data-ttu-id="aaaa8-277">Esses Estados de acompanhamento do controlador de movimento são definidos da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-277">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="aaaa8-278">**Alta precisão:** Embora o controlador de movimento esteja dentro do campo de exibição do headset, ele geralmente fornecerá posições de alta precisão, com base no rastreamento visual.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-278">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="aaaa8-279">Um controlador móvel que deixa momentaneamente o campo de exibição ou é momentaneamente obscurecido dos sensores do headset (por exemplo, por outro lado do usuário) continuará a retornar poses de alta precisão por um curto período, com base no acompanhamento inércia do próprio controlador.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-279">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="aaaa8-280">**Alta precisão (com risco de perda):** Quando o usuário move o controlador de movimento para cima da borda do campo de exibição do headset, o headset em breve não será capaz de rastrear visualmente a posição do controlador.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-280">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="aaaa8-281">O aplicativo sabe quando o controlador atingiu esse limite de FOV vendo o **SourceLossRisk** REACH 1,0.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-281">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="aaaa8-282">Nesse ponto, o aplicativo pode optar por pausar gestos do controlador que exigem um fluxo constante de poses de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-282">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="aaaa8-283">**Precisão aproximada:** Quando o controlador tiver perdido o acompanhamento Visual por tempo suficiente, as posições do controlador serão descartadas para as posições de precisão aproximada.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-283">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="aaaa8-284">Neste ponto, o sistema bloqueará o corpo do controlador para o usuário, controlando a posição do usuário à medida que eles se movimentam, ao mesmo tempo em que ainda expõe a orientação verdadeira do controlador usando seus sensores de orientação interna.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-284">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="aaaa8-285">Muitos aplicativos que usam controladores para apontar para e ativar elementos da interface do usuário podem operar normalmente em precisão aproximada sem que o usuário perceba.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-285">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="aaaa8-286">Os aplicativos com requisitos de entrada mais pesados podem optar por detectar essa queda de **alta** precisão à precisão **aproximada** inspecionando a propriedade **PositionAccuracy** , por exemplo, para dar ao usuário um hitbox mais generosa em destinos fora da tela durante esse tempo.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-286">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="aaaa8-287">**Sem posição:** Embora o controlador possa operar com precisão aproximada por um longo tempo, às vezes o sistema sabe que até mesmo uma posição bloqueada pelo corpo não é significativa no momento.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-287">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="aaaa8-288">Por exemplo, um controlador que foi ativado pode nunca ter sido observado visualmente ou um usuário pode colocar um controlador selecionado por outra pessoa.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-288">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="aaaa8-289">Naqueles momentos, o sistema não fornecerá nenhuma posição ao aplicativo e *TryGetPosition* retornará false.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-289">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="aaaa8-290">APIs comuns do Unity (Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-290">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="aaaa8-291">**Namespace:** *UnityEngine*, *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-291">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="aaaa8-292">**Tipos**: *Input*, *XR. InputTracking*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-292">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="aaaa8-293">No momento, o Unity usa suas APIs de *entrada geral. getbutton/Input. getaxis* para expor a entrada para [o SDK do OCULUS](https://docs.unity3d.com/Manual/OculusControllers.html), [o SDK do OpenVR e a](https://docs.unity3d.com/Manual/OpenVRControllers.html) realidade mista do Windows, incluindo controladores de mãos e de movimento.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-293">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="aaaa8-294">Se seu aplicativo usa essas APIs para entrada, ele pode facilmente dar suporte a controladores de movimento em vários SDKs do XR, incluindo a realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-294">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="aaaa8-295">Obtendo o estado pressionado de um botão lógico</span><span class="sxs-lookup"><span data-stu-id="aaaa8-295">Getting a logical button's pressed state</span></span>

<span data-ttu-id="aaaa8-296">Para usar as APIs de entrada gerais da Unity, você normalmente começará com a vinculação de botões e eixos a nomes lógicos no [Gerenciador de entrada do Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), ligando um botão ou IDs de eixo a cada nome.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-296">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="aaaa8-297">Em seguida, você pode escrever código que se refere a esse botão lógico/nome do eixo.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-297">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="aaaa8-298">Por exemplo, para mapear o botão de gatilho do controlador de movimento à esquerda para a ação enviar, acesse **editar > configurações do projeto > entrada** no Unity e expanda as propriedades da seção enviar em eixos.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-298">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="aaaa8-299">Altere o **botão positivo** ou a propriedade do **botão Alt positivo** para ler o **botão 14 do joystick**, desta forma:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-299">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="aaaa8-300">![InputManager do Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-300">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="aaaa8-301&quot;>*Unity InputManager*</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aaaa8-301&quot;>*Unity InputManager*</span></span>

<span data-ttu-id=&quot;aaaa8-302&quot;>Em seguida, o script pode verificar a ação Enviar usando *Input.GetButton:*</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aaaa8-302&quot;>Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton(&quot;Submit"))
{
  // ...
}
```
<span data-ttu-id="aaaa8-303">Você pode adicionar mais botões lógicos alterando a **propriedade Tamanho** em **Eixos**.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-303">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="aaaa8-304">Obter o estado pressionado de um botão físico diretamente</span><span class="sxs-lookup"><span data-stu-id="aaaa8-304">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="aaaa8-305">Você também pode acessar os botões manualmente por seu nome totalmente qualificado, usando *Input.GetKey*:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-305">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="aaaa8-306">Como obter uma pose do controlador de movimento ou de mão</span><span class="sxs-lookup"><span data-stu-id="aaaa8-306">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="aaaa8-307">Você pode acessar a posição e a rotação do controlador usando *XR. InputTracking:*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-307">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="aaaa8-308">O código acima representa a pose de mão do controlador (em que o usuário mantém o controlador), que é útil para renderizar uma lâmina ou umaada na mão do usuário ou um modelo do próprio controlador.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-308">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="aaaa8-309">A relação entre essa pose de mão e a pose do ponteiro (em que a dica do controlador está apontando) pode ser diferente entre controladores.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-309">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="aaaa8-310">Neste momento, o acesso à pose de ponteiro do controlador só é possível por meio da API de entrada específica do MR, descrita nas seções abaixo.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-310">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="aaaa8-311">APIs específicas do Windows (XR. Wsa. Entrada)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-311">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="aaaa8-312">Se o projeto estiver usando qualquer um dos XR. APIs do WSA, elas estão sendo desaparadas em favor do SDK do XR em versões futuras do Unity.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-312">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="aaaa8-313">Para novos projetos, recomendamos usar o SDK do XR desde o início.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-313">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="aaaa8-314">Você pode encontrar mais informações sobre o sistema de [Entrada XR e as APIs aqui](https://docs.unity3d.com/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="aaaa8-314">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="aaaa8-315">**Namespace:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-315">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="aaaa8-316">**Tipos:** *InteractionManager,* *InteractionSourceState,* *InteractionSource*, *InteractionSourceProperties,* *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-316">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="aaaa8-317">Para obter informações mais detalhadas sobre Windows Mixed Reality entrada à mão (para HoloLens) e controladores de movimento, você pode optar por usar as APIs de entrada espaciais específicas do Windows no namespace *UnityEngine.XR.WSA.Input.*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-317">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="aaaa8-318">Isso permite que você acesse informações adicionais, como a precisão da posição ou o tipo de origem, o que permite separar as mãos e os controladores.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-318">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="aaaa8-319">Sondagem para o estado de mãos e controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="aaaa8-319">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="aaaa8-320">Você pode sondar o estado desse quadro para cada fonte de interação (mão ou controlador de movimento) usando o *método GetCurrentReading.*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-320">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="aaaa8-321">Cada *InteractionSourceState* que você receber de volta representa uma fonte de interação no momento atual.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-321">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="aaaa8-322">O *InteractionSourceState* expõe informações como:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-322">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="aaaa8-323">Quais [tipos de pressionamentos](../../design/motion-controllers.md) estão ocorrendo (Selecionar/Menu/Compreensão/Touchpad/Thumbstick)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-323">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="aaaa8-324">Outros dados específicos para controladores de movimento, como coordenadas XY do touchpad e/ou thumbstick e estado tocado</span><span class="sxs-lookup"><span data-stu-id="aaaa8-324">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="aaaa8-325">O InteractionSourceKind para saber se a origem é uma mão ou um controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="aaaa8-325">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="aaaa8-326">Sondagem de poses de renderização previstas para a frente</span><span class="sxs-lookup"><span data-stu-id="aaaa8-326">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="aaaa8-327">Ao sondar dados de origem de interação de mãos e controladores, as poses que você recebe são poses previstas para frente no momento em que os fótons desse quadro alcançarão os olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-327">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="aaaa8-328">As poses previstas para frente são mais bem usadas para **renderizar** o controlador ou um objeto mantido em cada quadro.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-328">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="aaaa8-329">Se você estiver direcionando uma determinada press ou versão com o controlador, isso será mais preciso se você usar as APIs de evento histórico descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-329">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="aaaa8-330">Você também pode obter a pose de cabeça prevista para frente para esse quadro atual.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-330">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="aaaa8-331">Assim como acontece com **a** pose de origem, isso é útil para renderizar um cursor, embora o direcionamento a uma determinada press ou versão seja mais preciso se você usar as APIs de evento históricos descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-331">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="aaaa8-332">Manipulando eventos de origem de interação</span><span class="sxs-lookup"><span data-stu-id="aaaa8-332">Handling interaction source events</span></span>

<span data-ttu-id="aaaa8-333">Para manipular eventos de entrada conforme eles ocorrem com seus dados de pose históricos precisos, você pode manipular eventos de origem de interação em vez de sondagem.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-333">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="aaaa8-334">Para manipular eventos de origem de interação:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-334">To handle interaction source events:</span></span>
* <span data-ttu-id="aaaa8-335">Registre-se *para um evento de entrada InteractionManager.*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-335">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="aaaa8-336">Para cada tipo de evento de interação no qual você está interessado, você precisa se inscrever nele.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-336">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="aaaa8-337">Manipular o evento.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-337">Handle the event.</span></span> <span data-ttu-id="aaaa8-338">Depois de assinar um evento de interação, você receberá o retorno de chamada quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-338">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="aaaa8-339">No exemplo *SourcePressed,* isso ocorrerá depois que a origem for detectada e antes de ser liberada ou perdida.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-339">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="aaaa8-340">Como parar de manipular um evento</span><span class="sxs-lookup"><span data-stu-id="aaaa8-340">How to stop handling an event</span></span>

<span data-ttu-id="aaaa8-341">Você precisa parar de manipular um evento quando não estiver mais interessado no evento ou estiver destrói o objeto que assinou o evento.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-341">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="aaaa8-342">Para interromper o tratamento do evento, cancele a assinatura do evento.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-342">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="aaaa8-343">Lista de eventos de origem de interação</span><span class="sxs-lookup"><span data-stu-id="aaaa8-343">List of interaction source events</span></span>

<span data-ttu-id="aaaa8-344">Os eventos de origem de interação disponíveis são:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-344">The available interaction source events are:</span></span>
* <span data-ttu-id="aaaa8-345">*InteractionSourceDetected (a* origem fica ativa)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-345">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="aaaa8-346">*InteractionSourceLost* (fica inativo)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-346">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="aaaa8-347">*InteractionSourcePressed* (toque, pressiona o botão ou "Selecionar" enunciado)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-347">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="aaaa8-348">*InteractionSourceReleased* (fim de um toque, botão liberado ou final de "Selecionar" enunciado)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-348">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="aaaa8-349">*InteractionSourceUpdated* (move ou altera algum estado)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-349">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="aaaa8-350">Eventos para direcionamento histórico representam as que mais se combinam com uma press ou versão</span><span class="sxs-lookup"><span data-stu-id="aaaa8-350">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="aaaa8-351">As APIs de sondagem descritas anteriormente oferecem ao seu aplicativo poses previstas para o futuro.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-351">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="aaaa8-352">Embora essas poses previstas sejam melhores para renderizar o controlador ou um objeto portátil virtual, as poses futuras não são ideais para direcionamento, por dois motivos principais:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-352">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="aaaa8-353">Quando o usuário pressiona um botão em um controlador, pode haver cerca de 20 ms de latência sem fio por Bluetooth antes que o sistema receba a pressão.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-353">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="aaaa8-354">Em seguida, se você estiver usando uma pose prevista para frente, haverá outra previsão de 10 a 20 ms aplicada para direcionar a hora em que os fótons do quadro atual alcançarão os olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-354">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="aaaa8-355">Isso significa que a sondagem oferece uma pose de origem ou uma pose de cabeça que é de 30 a 40 ms para frente de onde a cabeça e as mãos do usuário realmente estavam de volta quando a pressão ou a liberação aconteceu.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-355">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="aaaa8-356">Para a entrada manual do HoloLens, embora não haja atraso na transmissão sem fio, há um atraso de processamento semelhante para detectar a pressão.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-356">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="aaaa8-357">Para direcionar com precisão com base na intenção original do usuário para uma pressionamento de mão ou controlador, você deve usar a pose de origem histórica ou a pose de cabeça desse evento de entrada *InteractionSourcePressed* ou *InteractionSourceReleased.*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-357">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="aaaa8-358">Você pode direcionar uma press ou versão com dados de pose históricos da cabeça do usuário ou do controlador:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-358">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="aaaa8-359">A posição da cabeça no momento em que ocorreu um  gesto ou pressionamento de controlador, que pode ser usado para direcionamento para determinar o que o usuário estava [olhando:](../../design/gaze-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-359">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="aaaa8-360">A pose de origem no momento em que ocorreu  uma pressão do controlador de movimento, que pode ser usada para direcionamento para determinar em que o usuário estava apontando o controlador.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-360">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="aaaa8-361">Esse será o estado do controlador que passou pela pressão.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-361">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="aaaa8-362">Se você estiver renderizar o controlador em si, poderá solicitar a pose do ponteiro em vez da pose da mão, para disparar o raio de direcionamento do que o usuário considerará a dica natural desse controlador renderizado:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-362">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="aaaa8-363">Exemplo de manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="aaaa8-363">Event handlers example</span></span>

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

## <a name="motion-controllers-in-mrtk"></a><span data-ttu-id="aaaa8-364">Controladores de movimento no MRTK</span><span class="sxs-lookup"><span data-stu-id="aaaa8-364">Motion Controllers in MRTK</span></span>

<span data-ttu-id="aaaa8-365">Você pode acessar [o gesto e o controlador de movimento](/windows/mixed-reality/mrtk-unity/features/input/controllers) do Gerenciador de entrada.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-365">You can access [gesture and motion controller](/windows/mixed-reality/mrtk-unity/features/input/controllers) from the input Manager.</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="aaaa8-366">Acompanhe com tutoriais</span><span class="sxs-lookup"><span data-stu-id="aaaa8-366">Follow along with tutorials</span></span>

<span data-ttu-id="aaaa8-367">Tutoriais passo a passo, com exemplos de personalização mais detalhados, estão disponíveis no Mixed Reality Academy:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-367">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="aaaa8-368">Entrada do MR 211: gesto</span><span class="sxs-lookup"><span data-stu-id="aaaa8-368">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="aaaa8-369">Entrada do MR 213: controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="aaaa8-369">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="aaaa8-370">[![Entrada 213 do MR – Controlador de movimento](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="aaaa8-370">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="aaaa8-371">*Entrada 213 do MR – Controlador de movimento*</span><span class="sxs-lookup"><span data-stu-id="aaaa8-371">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="aaaa8-372">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="aaaa8-372">Next Development Checkpoint</span></span>

<span data-ttu-id="aaaa8-373">Se você estiver seguindo o percurso de desenvolvimento do Unity que fizemos, você está no meio da exploração dos blocos de construção principais do MRTK.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-373">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="aaaa8-374">Deste ponto, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-374">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aaaa8-375">Acompanhamento de mãos e olhos</span><span class="sxs-lookup"><span data-stu-id="aaaa8-375">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="aaaa8-376">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="aaaa8-376">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aaaa8-377">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="aaaa8-377">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="aaaa8-378">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="aaaa8-378">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="aaaa8-379">Veja também</span><span class="sxs-lookup"><span data-stu-id="aaaa8-379">See also</span></span>

* [<span data-ttu-id="aaaa8-380">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="aaaa8-380">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="aaaa8-381">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="aaaa8-381">Motion controllers</span></span>](../../design/motion-controllers.md)