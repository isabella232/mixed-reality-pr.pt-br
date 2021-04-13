---
title: Botões
description: Visão geral sobre os botões em MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, botões de MRTK
ms.openlocfilehash: 43570c225f25b9ea73c9d1fc4cc9b6c92b8c2dfc
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003097"
---
# <a name="button"></a><span data-ttu-id="b16c8-104">Botão</span><span class="sxs-lookup"><span data-stu-id="b16c8-104">Button</span></span>

![Botão principal](../images/button/MRTK_Button_Main.png)

<span data-ttu-id="b16c8-106">Um botão dá ao usuário uma forma de acionar uma ação imediata.</span><span class="sxs-lookup"><span data-stu-id="b16c8-106">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="b16c8-107">É um dos componentes mais fundamentais da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="b16c8-107">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="b16c8-108">O MRTK fornece vários tipos de pré-fabricados de botão.</span><span class="sxs-lookup"><span data-stu-id="b16c8-108">MRTK provides various types of button prefabs.</span></span>

## <a name="button-prefabs-in-mrtk"></a><span data-ttu-id="b16c8-109">Botão pré-fabricados em MRTK</span><span class="sxs-lookup"><span data-stu-id="b16c8-109">Button prefabs in MRTK</span></span>

<span data-ttu-id="b16c8-110">Exemplos do botão pré-fabricados na ``MRTK/SDK/Features/UX/Interactable/Prefabs`` pasta</span><span class="sxs-lookup"><span data-stu-id="b16c8-110">Examples of the button prefabs under ``MRTK/SDK/Features/UX/Interactable/Prefabs`` folder</span></span>

### <a name="unity-ui-imagegraphic-based-buttons"></a><span data-ttu-id="b16c8-111">Imagem da interface do usuário do Unity/botões baseados em gráficos</span><span class="sxs-lookup"><span data-stu-id="b16c8-111">Unity UI Image/Graphic based buttons</span></span>

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a><span data-ttu-id="b16c8-112">Botões baseados em Colisor</span><span class="sxs-lookup"><span data-stu-id="b16c8-112">Collider based buttons</span></span>

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) <span data-ttu-id="b16c8-114">PressableButtonHoloLens2</span><span class="sxs-lookup"><span data-stu-id="b16c8-114">PressableButtonHoloLens2</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) <span data-ttu-id="b16c8-116">PressableButtonHoloLens2Unplated</span><span class="sxs-lookup"><span data-stu-id="b16c8-116">PressableButtonHoloLens2Unplated</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) <span data-ttu-id="b16c8-118">PressableButtonHoloLens2Circular</span><span class="sxs-lookup"><span data-stu-id="b16c8-118">PressableButtonHoloLens2Circular</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="b16c8-119">Botão de estilo de shell do HoloLens 2 com placa de frente que dá suporte a vários comentários visuais, como luz de borda, luz de proximidade e placa frontal compactada</span><span class="sxs-lookup"><span data-stu-id="b16c8-119">HoloLens 2's shell-style button with backplate which supports various visual feedback such as border light, proximity light, and compressed front plate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-120">Botão de estilo de shell do HoloLens 2 sem placa traseira</span><span class="sxs-lookup"><span data-stu-id="b16c8-120">HoloLens 2's shell-style button without backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-121">Botão estilo de shell do HoloLens 2 com forma circular</span><span class="sxs-lookup"><span data-stu-id="b16c8-121">HoloLens 2's shell-style button with circular shape</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="b16c8-122">![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span><span class="sxs-lookup"><span data-stu-id="b16c8-122">![PressableButtonHoloLens2_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-123">![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span><span class="sxs-lookup"><span data-stu-id="b16c8-123">![PressableButtonHoloLens2Bar3H](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-124">![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span><span class="sxs-lookup"><span data-stu-id="b16c8-124">![PressableButtonHoloLens2Bar3V](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="b16c8-125">Botão de estilo de Shell de todo o HoloLens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="b16c8-125">Wide HoloLens 2's shell-style button 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-126">Barra de botões do HoloLens 2 horizontal com placa traseira compartilhada</span><span class="sxs-lookup"><span data-stu-id="b16c8-126">Horizontal HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-127">Barra de botões do HoloLens 2 vertical com placa traseira compartilhada</span><span class="sxs-lookup"><span data-stu-id="b16c8-127">Vertical HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="b16c8-128">![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span><span class="sxs-lookup"><span data-stu-id="b16c8-128">![PressableButtonHoloLens2ToggleCheckBox_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-129">![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span><span class="sxs-lookup"><span data-stu-id="b16c8-129">![PressableButtonHoloLens2ToggleSwitch_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-130">![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span><span class="sxs-lookup"><span data-stu-id="b16c8-130">![PressableButtonHoloLens2ToggleRadio_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="b16c8-131">Caixa de seleção estilo de shell do HoloLens 2 32x32mm</span><span class="sxs-lookup"><span data-stu-id="b16c8-131">HoloLens 2's shell-style checkbox 32x32mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-132">Opção de estilo de shell do HoloLens 2 32x32mm</span><span class="sxs-lookup"><span data-stu-id="b16c8-132">HoloLens 2's shell-style switch 32x32mm</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-133">Opção do estilo shell do HoloLens 2 32x32mm</span><span class="sxs-lookup"><span data-stu-id="b16c8-133">HoloLens 2's shell-style radio 32x32mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="b16c8-134">![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span><span class="sxs-lookup"><span data-stu-id="b16c8-134">![PressableButtonHoloLens2ToggleCheckBox_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-135">![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span><span class="sxs-lookup"><span data-stu-id="b16c8-135">![PressableButtonHoloLens2ToggleSwitch_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-136">![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span><span class="sxs-lookup"><span data-stu-id="b16c8-136">![PressableButtonHoloLens2ToggleRadio_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="b16c8-137">Caixa de seleção estilo de shell do HoloLens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="b16c8-137">HoloLens 2's shell-style checkbox 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-138">Opção de estilo de shell do HoloLens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="b16c8-138">HoloLens 2's shell-style switch 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-139">Opção do estilo shell do HoloLens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="b16c8-139">HoloLens 2's shell-style radio 32x96mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="b16c8-140">![](../images/button/MRTK_Button_Radial.png) **Radial** radial</span><span class="sxs-lookup"><span data-stu-id="b16c8-140">![Radial](../images/button/MRTK_Button_Radial.png) **Radial**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-141">![Caixa de seleção](../images/button/MRTK_Button_Checkbox.png) **Checkbox**</span><span class="sxs-lookup"><span data-stu-id="b16c8-141">![Checkbox](../images/button/MRTK_Button_Checkbox.png) **Checkbox**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-142">![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span><span class="sxs-lookup"><span data-stu-id="b16c8-142">![ToggleSwitch](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="b16c8-143">Botão radial</span><span class="sxs-lookup"><span data-stu-id="b16c8-143">Radial button</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-144">Caixa de seleção</span><span class="sxs-lookup"><span data-stu-id="b16c8-144">Checkbox</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-145">Switch de alternância</span><span class="sxs-lookup"><span data-stu-id="b16c8-145">Toggle switch</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="b16c8-146">![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span><span class="sxs-lookup"><span data-stu-id="b16c8-146">![ButtonHoloLens1](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-147">![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span><span class="sxs-lookup"><span data-stu-id="b16c8-147">![PressableRoundButton](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-148">![Botão base do botão ](../images/button/MRTK_Button_Base.png) </span><span class="sxs-lookup"><span data-stu-id="b16c8-148">![Button Base](../images/button/MRTK_Button_Base.png) **Button**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="b16c8-149">Botão de estilo de Shell da 1ª Gen do HoloLens</span><span class="sxs-lookup"><span data-stu-id="b16c8-149">HoloLens 1st gen's shell style button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-150">Botão de ação de forma arredondada</span><span class="sxs-lookup"><span data-stu-id="b16c8-150">Round shape push button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b16c8-151">Botão básico</span><span class="sxs-lookup"><span data-stu-id="b16c8-151">Basic button</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="b16c8-152">O `Button` (assets/MRTK/SDK/Features/UX/interagible/pré-fabricados/Button. pré-fabricado) baseia-se no conceito [interagindo](interactable.md) para fornecer controles de interface do usuário fáceis para botões ou outros tipos de superfícies interativas.</span><span class="sxs-lookup"><span data-stu-id="b16c8-152">The `Button` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) is based on the [Interactable](interactable.md) concept to provide easy UI controls for buttons or other types of interactive surfaces.</span></span> <span data-ttu-id="b16c8-153">O botão linha de base dá suporte a todos os métodos de entrada disponíveis, incluindo a entrada de mão articulada para as interações de near, bem como olhar + Air-TAP para as interações distantes.</span><span class="sxs-lookup"><span data-stu-id="b16c8-153">The baseline button supports all available input methods, including articulated hand input for the near interactions as well as gaze + air-tap for the far interactions.</span></span> <span data-ttu-id="b16c8-154">Você também pode usar o comando de voz para disparar o botão.</span><span class="sxs-lookup"><span data-stu-id="b16c8-154">You can also use voice command to trigger the button.</span></span>

<span data-ttu-id="b16c8-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interajaable/pré-fabricados/PressableButtonHoloLens2. pré-fabricado) é o botão de shell do HoloLens 2 que dá suporte à movimentação precisa do botão para a entrada de rastreamento direto.</span><span class="sxs-lookup"><span data-stu-id="b16c8-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) is HoloLens 2's shell style button that supports the precise movement of the button for the direct hand tracking input.</span></span> <span data-ttu-id="b16c8-156">Ele combina `Interactable` script com `PressableButton` script.</span><span class="sxs-lookup"><span data-stu-id="b16c8-156">It combines `Interactable` script with `PressableButton` script.</span></span>

<span data-ttu-id="b16c8-157">Para o HoloLens 2, é recomendável usar botões com uma chapa traseira opaca.</span><span class="sxs-lookup"><span data-stu-id="b16c8-157">For HoloLens 2, it is recommended to use buttons with an opaque backplate.</span></span> <span data-ttu-id="b16c8-158">Botões transparentes não são recomendados devido a esses problemas de usabilidade e estabilidade:</span><span class="sxs-lookup"><span data-stu-id="b16c8-158">Transparent buttons are not recommended because of these usability and stability issues:</span></span>

* <span data-ttu-id="b16c8-159">O ícone e o texto são difíceis de ler com o ambiente físico</span><span class="sxs-lookup"><span data-stu-id="b16c8-159">Icon and text are difficult to read with the physical environment</span></span>
* <span data-ttu-id="b16c8-160">É difícil entender quando o evento é disparado</span><span class="sxs-lookup"><span data-stu-id="b16c8-160">It is hard to understand when the event triggers</span></span>
* <span data-ttu-id="b16c8-161">Os hologramas exibidos por meio de um plano transparente podem ser instáveis com estabilização LSR de profundidade 2 do HoloLens</span><span class="sxs-lookup"><span data-stu-id="b16c8-161">Holograms that are displayed through a transparent plane can be unstable with HoloLens 2's Depth LSR stabilization</span></span>

![Botão folheado](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a><span data-ttu-id="b16c8-163">Como usar botões prensais</span><span class="sxs-lookup"><span data-stu-id="b16c8-163">How to use pressable buttons</span></span>

### <a name="unity-ui-based-buttons"></a><span data-ttu-id="b16c8-164">Botões baseados na interface do usuário do Unity</span><span class="sxs-lookup"><span data-stu-id="b16c8-164">Unity UI based buttons</span></span>

<span data-ttu-id="b16c8-165">Crie uma tela em sua cena (gameobject-> interface do usuário > tela).</span><span class="sxs-lookup"><span data-stu-id="b16c8-165">Create a Canvas in your scene (GameObject -> UI -> Canvas).</span></span> <span data-ttu-id="b16c8-166">No painel do inspetor para sua tela:</span><span class="sxs-lookup"><span data-stu-id="b16c8-166">In the Inspector panel for your Canvas:</span></span>

* <span data-ttu-id="b16c8-167">Clique em "converter para tela do MRTK"</span><span class="sxs-lookup"><span data-stu-id="b16c8-167">Click "Convert to MRTK Canvas"</span></span>
* <span data-ttu-id="b16c8-168">Clique em "Adicionar NearInteractionTouchableUnityUI"</span><span class="sxs-lookup"><span data-stu-id="b16c8-168">Click "Add NearInteractionTouchableUnityUI"</span></span>
* <span data-ttu-id="b16c8-169">Defina a escala X, Y e Z do componente de transformação Rect como 0, 1</span><span class="sxs-lookup"><span data-stu-id="b16c8-169">Set the Rect Transform component's X, Y, and Z scale to 0.001</span></span>

<span data-ttu-id="b16c8-170">Em seguida, arraste `PressableButtonUnityUI` (assets/MRTK/SDK/Features/UX/interagir/pré-fabricados/PressableButtonUnityUI. pré-fabricado), `PressableButtonUnityUICircular` (assets/MRTK/SDK/Features/UX/interajable/pré-fabricados/PressableButtonUnityUICircular. pré-fabricado) ou `PressableButtonHoloLens2UnityUI` (assets/MRTK/SDK/Features/UX/interajable/pré-fabricados/PressableButtonHoloLens2UnityUI. pré-fabricado) na tela.</span><span class="sxs-lookup"><span data-stu-id="b16c8-170">Then, drag `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab), or `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) onto the Canvas.</span></span>

### <a name="collider-based-buttons"></a><span data-ttu-id="b16c8-171">Botões baseados em Colisor</span><span class="sxs-lookup"><span data-stu-id="b16c8-171">Collider based buttons</span></span>

<span data-ttu-id="b16c8-172">Basta arrastar `PressableButtonHoloLens2` (assets/MRTK/SDK/Features/UX/interajaable/pré-fabricados/PressableButtonHoloLens2. pré-fabricado) ou `PressableButtonHoloLens2Unplated` (assets/MRTK/SDK/Features/UX/interajable/pré-fabricados/PressableButtonHoloLens2Unplated. pré-fabricado) para a cena.</span><span class="sxs-lookup"><span data-stu-id="b16c8-172">Simply drag `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) or `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) into the scene.</span></span> <span data-ttu-id="b16c8-173">Essas pré-fabricados de botão já estão configuradas para ter comentários visuais de áudio para os vários tipos de entradas, incluindo entrada de mão articulada e olhar.</span><span class="sxs-lookup"><span data-stu-id="b16c8-173">These button prefabs are already configured to have audio-visual feedback for the various types of inputs, including articulated hand input and gaze.</span></span>

<span data-ttu-id="b16c8-174">Os eventos expostos no próprio pré-fabricado, bem como o componente que pode [interagir](interactable.md) , podem ser usados para disparar ações adicionais.</span><span class="sxs-lookup"><span data-stu-id="b16c8-174">The events exposed in the prefab itself as well as the [Interactable](interactable.md) component can be used to trigger additional actions.</span></span> <span data-ttu-id="b16c8-175">Os botões pressionáveis na [cena HandInteractionExample](../example-scenes/hand-interaction-examples.md) usam o evento *onclick* de interagir para disparar uma alteração na cor de um cubo.</span><span class="sxs-lookup"><span data-stu-id="b16c8-175">The pressable buttons in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md) use Interactable's *OnClick* event to trigger a change in the color of a cube.</span></span> <span data-ttu-id="b16c8-176">Esse evento é disparado para diferentes tipos de métodos de entrada, como olhar, toque de ar, mão-raio, bem como pressionamentos de botão físico por meio do script de botão prensado.</span><span class="sxs-lookup"><span data-stu-id="b16c8-176">This event gets triggered for different types of input methods such as gaze, air-tap, hand-ray, as well as physical button presses through the pressable button script.</span></span>

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

<span data-ttu-id="b16c8-177">Você pode configurar quando o botão pressionável aciona o evento *onclick* por meio do `PhysicalPressEventRouter` no botão.</span><span class="sxs-lookup"><span data-stu-id="b16c8-177">You can configure when the pressable button fires the *OnClick* event via the `PhysicalPressEventRouter` on the button.</span></span> <span data-ttu-id="b16c8-178">Por exemplo, você pode definir *onclick* para acionar quando o botão é pressionado pela primeira vez, em oposição a ser pressionado e liberado, definindo interagir com o *evento* de *clique* para ao pressionar.</span><span class="sxs-lookup"><span data-stu-id="b16c8-178">For example, you can set *OnClick* to fire when the button is first pressed, as opposed to being pressed and released, by setting *Interactable On Click* to *Event On Press*.</span></span>

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

<span data-ttu-id="b16c8-179">Para aproveitar informações de estado de entrada articuladas específicas, você pode usar eventos de botões que podem ser prensados – *início do toque*, *fim do toque*, *botão pressionado*, *botão liberado*.</span><span class="sxs-lookup"><span data-stu-id="b16c8-179">To leverage specific articulated hand input state information, you can use pressable buttons events - *Touch Begin*, *Touch End*, *Button Pressed*, *Button Released*.</span></span> <span data-ttu-id="b16c8-180">No entanto, esses eventos não serão disparados em resposta às entradas do toque, do lado do ar ou do raio.</span><span class="sxs-lookup"><span data-stu-id="b16c8-180">These events will not fire in response to air-tap, hand-ray, or eye inputs, however.</span></span> <span data-ttu-id="b16c8-181">**Para dar suporte a interações próximas e distantes, é recomendável usar o evento *onclick* de interagir.**</span><span class="sxs-lookup"><span data-stu-id="b16c8-181">**To support both near and far interactions, it is recommended to use Interactable's *OnClick* event.**</span></span>

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a><span data-ttu-id="b16c8-182">Estados de interação</span><span class="sxs-lookup"><span data-stu-id="b16c8-182">Interaction states</span></span>

<span data-ttu-id="b16c8-183">No estado ocioso, a placa frontal do botão não é visível.</span><span class="sxs-lookup"><span data-stu-id="b16c8-183">In the idle state, the button's front plate is not visible.</span></span> <span data-ttu-id="b16c8-184">Como as abordagens de um dedo ou um cursor da entrada olhar tem como alvo a superfície, a borda brilhante da placa frontal torna-se visível.</span><span class="sxs-lookup"><span data-stu-id="b16c8-184">As a finger approaches or a cursor from gaze input targets the surface, the front plate's glowing border becomes visible.</span></span> <span data-ttu-id="b16c8-185">Há um realce adicional da posição de alcance na superfície da placa frontal.</span><span class="sxs-lookup"><span data-stu-id="b16c8-185">There is additional highlighting of the fingertip position on the front plate surface.</span></span> <span data-ttu-id="b16c8-186">Quando enviado por push com um dedo, a placa frontal se move com a ponta.</span><span class="sxs-lookup"><span data-stu-id="b16c8-186">When pushed with a finger, the front plate moves with the fingertip.</span></span> <span data-ttu-id="b16c8-187">Quando o ponto atinge a superfície da placa frontal, ele mostra um efeito de pulso sutil para dar comentários visuais sobre o toque.</span><span class="sxs-lookup"><span data-stu-id="b16c8-187">When the fingertip touches the surface of the front plate, it shows a subtle pulse effect to give visual feedback of the touch point.</span></span>

<span data-ttu-id="b16c8-188">No botão de estilo de shell do HoloLens 2, há muitas indicações visuais e capacidades para aumentar a confiança do usuário na interação.</span><span class="sxs-lookup"><span data-stu-id="b16c8-188">In HoloLens 2 shell-style button, there are many visual cues and affordances to increase the user's confidence on interaction.</span></span>

|  ![Luz de proximidade](../images/button/ux_button_affordance_proximitylight.jpg) | ![Realce de foco](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Compactando o compartimento](../images/button/ux_button_affordance_compression.jpg) | ![Pulso no gatilho](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="b16c8-193">Luz de proximidade</span><span class="sxs-lookup"><span data-stu-id="b16c8-193">Proximity light</span></span> | <span data-ttu-id="b16c8-194">Realce de foco</span><span class="sxs-lookup"><span data-stu-id="b16c8-194">Focus highlight</span></span> | <span data-ttu-id="b16c8-195">Compactando o compartimento</span><span class="sxs-lookup"><span data-stu-id="b16c8-195">Compressing cage</span></span> | <span data-ttu-id="b16c8-196">Pulso no gatilho</span><span class="sxs-lookup"><span data-stu-id="b16c8-196">Pulse on trigger</span></span> |

<span data-ttu-id="b16c8-197">O efeito de pulso sutil é disparado pelo botão pressionável, que procura *ProximityLight (s)* que residem no ponteiro que está interagindo atualmente.</span><span class="sxs-lookup"><span data-stu-id="b16c8-197">The subtle pulse effect is triggered by the pressable button, which looks for *ProximityLight(s)* that live on the currently interacting pointer.</span></span> <span data-ttu-id="b16c8-198">Se alguma luz de proximidade for encontrada, o `ProximityLight.Pulse` método será chamado, que anima automaticamente os parâmetros do sombreador para exibir um pulso.</span><span class="sxs-lookup"><span data-stu-id="b16c8-198">If any proximity lights are found, the `ProximityLight.Pulse` method is called, which automatically animates shader parameters to display a pulse.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="b16c8-199">Propriedades do Inspetor</span><span class="sxs-lookup"><span data-stu-id="b16c8-199">Inspector properties</span></span>

![Estrutura do botão](../images/button/MRTK_Button_Structure.png)

<span data-ttu-id="b16c8-201"> 
 Colisor `Box Collide\r` de caixa para a placa frontal do botão.</span><span class="sxs-lookup"><span data-stu-id="b16c8-201">**Box Collider**
`Box Collider` for the button's front plate.</span></span>

<span data-ttu-id="b16c8-202">**Botão pressionável** A lógica do botão de movimentação com a interação de pressionar à mão.</span><span class="sxs-lookup"><span data-stu-id="b16c8-202">**Pressable Button** The logic for the button movement with hand press interaction.</span></span>

<span data-ttu-id="b16c8-203">**Roteador de evento de prensa física** Esse script envia eventos da interação de pressionar mão para [interagir](interactable.md).</span><span class="sxs-lookup"><span data-stu-id="b16c8-203">**Physical Press Event Router** This script sends events from hand press interaction to [Interactable](interactable.md).</span></span>

<span data-ttu-id="b16c8-204">**Interagir** 
 [Interagir](interactable.md) manipula vários tipos de Estados de interação e eventos.</span><span class="sxs-lookup"><span data-stu-id="b16c8-204">**Interactable**
[Interactable](interactable.md) handles various types of interaction states and events.</span></span> <span data-ttu-id="b16c8-205">Olhar de HoloLens, gesto e entrada de voz e entrada do controlador de movimento de headset de imersão são tratados diretamente por esse script.</span><span class="sxs-lookup"><span data-stu-id="b16c8-205">HoloLens gaze, gesture, and voice input and immersive headset motion controller input are directly handled by this script.</span></span>

<span data-ttu-id="b16c8-206">**Fonte de áudio** Fonte de áudio do Unity para os clipes de comentários de áudio.</span><span class="sxs-lookup"><span data-stu-id="b16c8-206">**Audio Source** Unity audio source for the audio feedback clips.</span></span>

<span data-ttu-id="b16c8-207">*NearInteractionTouchable. cs* necessário para tornar qualquer objeto tocável com entrada de mão articulada.</span><span class="sxs-lookup"><span data-stu-id="b16c8-207">*NearInteractionTouchable.cs* Required to make any object touchable with articulated hand input.</span></span>

## <a name="prefab-layout"></a><span data-ttu-id="b16c8-208">Layout de pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="b16c8-208">Prefab layout</span></span>

<span data-ttu-id="b16c8-209">O objeto *ButtonContent* contém a placa frontal, o rótulo de texto e o ícone.</span><span class="sxs-lookup"><span data-stu-id="b16c8-209">The *ButtonContent* object contains front plate, text label and icon.</span></span> <span data-ttu-id="b16c8-210">O *FrontPlate* responde à proximidade do índice usando o sombreador de *Button_Box* .</span><span class="sxs-lookup"><span data-stu-id="b16c8-210">The *FrontPlate* responds to the proximity of the index fingertip using the *Button_Box* shader.</span></span> <span data-ttu-id="b16c8-211">Ele mostra bordas brilhantes, luz de proximidade e um efeito de pulso sobre toque.</span><span class="sxs-lookup"><span data-stu-id="b16c8-211">It shows glowing borders, proximity light, and a pulse effect on touch.</span></span> <span data-ttu-id="b16c8-212">O rótulo de texto é criado com o textmesh pro.</span><span class="sxs-lookup"><span data-stu-id="b16c8-212">The text label is made with TextMesh Pro.</span></span> <span data-ttu-id="b16c8-213">A visibilidade do *SeeItSayItLabel* é controlada pelo tema de [interação](interactable.md).</span><span class="sxs-lookup"><span data-stu-id="b16c8-213">*SeeItSayItLabel*'s visibility is controlled by [Interactable](interactable.md)'s theme.</span></span>

![Layout do botão](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a><span data-ttu-id="b16c8-215">Como alterar o ícone e o texto</span><span class="sxs-lookup"><span data-stu-id="b16c8-215">How to change the icon and text</span></span>

<span data-ttu-id="b16c8-216">Os botões MRTK usam um `ButtonConfigHelper` componente para ajudá-lo a alterar o ícone, o texto e o rótulo do botão.</span><span class="sxs-lookup"><span data-stu-id="b16c8-216">MRTK buttons use a `ButtonConfigHelper` component to assist you in changing the button's icon, text and label.</span></span> <span data-ttu-id="b16c8-217">(Observe que alguns campos podem estar ausentes se os elementos não estiverem presentes no botão selecionado.)</span><span class="sxs-lookup"><span data-stu-id="b16c8-217">(Note that some fields may be absent if elements are not present on the selected button.)</span></span>

![Auxiliar de configuração de botão](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a><span data-ttu-id="b16c8-219">Criando e modificando conjuntos de ícones</span><span class="sxs-lookup"><span data-stu-id="b16c8-219">Creating and Modifying Icon Sets</span></span>

<span data-ttu-id="b16c8-220">Um **conjunto de ícones** é um conjunto compartilhado de ativos de ícone usado pelo `ButtonConfigHelper` componente.</span><span class="sxs-lookup"><span data-stu-id="b16c8-220">An **Icon Set** is a shared set of icon assets used by the `ButtonConfigHelper` component.</span></span> <span data-ttu-id="b16c8-221">Há suporte para três *estilos* de ícone.</span><span class="sxs-lookup"><span data-stu-id="b16c8-221">Three icon *styles* are supported.</span></span>

* <span data-ttu-id="b16c8-222">Ícones **quádruplos** são renderizados em um quad usando um `MeshRenderer` .</span><span class="sxs-lookup"><span data-stu-id="b16c8-222">**Quad** icons are rendered on a quad using a `MeshRenderer`.</span></span> <span data-ttu-id="b16c8-223">Esse é o estilo de ícone padrão.</span><span class="sxs-lookup"><span data-stu-id="b16c8-223">This is the default icon style.</span></span>
* <span data-ttu-id="b16c8-224">Os ícones de **Sprite** são renderizados usando um `SpriteRenderer` .</span><span class="sxs-lookup"><span data-stu-id="b16c8-224">**Sprite** icons are rendered using a `SpriteRenderer`.</span></span> <span data-ttu-id="b16c8-225">Isso será útil se você preferir importar os ícones como uma folha de Sprite ou se quiser que os ativos de ícone sejam compartilhados com os componentes da interface do usuário do Unity.</span><span class="sxs-lookup"><span data-stu-id="b16c8-225">This is useful if you prefer to import your icons as a sprite sheet, or if you want your icon assets to be shared with Unity UI components.</span></span> <span data-ttu-id="b16c8-226">Para usar esse estilo, você precisará instalar o pacote do editor Sprite **(Windows-> Package Manager-> 2D Sprite)**</span><span class="sxs-lookup"><span data-stu-id="b16c8-226">To use this style you will need to install the Sprite Editor package **(Windows -> Package Manager -> 2D Sprite)**</span></span>
* <span data-ttu-id="b16c8-227">Ícones de **caracteres** são renderizados usando um `TextMeshPro` componente.</span><span class="sxs-lookup"><span data-stu-id="b16c8-227">**Char** icons are rendered using a `TextMeshPro` component.</span></span> <span data-ttu-id="b16c8-228">Isso será útil se você preferir usar uma fonte de ícone.</span><span class="sxs-lookup"><span data-stu-id="b16c8-228">This is useful if you prefer to use an icon font.</span></span> <span data-ttu-id="b16c8-229">Para usar a fonte do ícone do HoloLens, você precisará criar um `TextMeshPro` ativo de fonte.</span><span class="sxs-lookup"><span data-stu-id="b16c8-229">To use the HoloLens icon font you will need to create a `TextMeshPro` font asset.</span></span>

<span data-ttu-id="b16c8-230">Para alterar o estilo que seu botão usa, expanda a lista suspensa *ícones* no ButtonConfigHelper e selecione na lista suspensa *estilo de ícone* .</span><span class="sxs-lookup"><span data-stu-id="b16c8-230">To change which style your button uses, expand the *Icons* dropdown in the ButtonConfigHelper and select from the *Icon Style* dropdown.</span></span>

<span data-ttu-id="b16c8-231">Você pode criar um novo ícone de botão definido com o menu ativo: **criar > kit de ferramentas de realidade misturada > ícone conjunto.**</span><span class="sxs-lookup"><span data-stu-id="b16c8-231">You can create a new button icon set with the asset menu: **Create > Mixed Reality Toolkit > Icon Set.**</span></span> <span data-ttu-id="b16c8-232">Para adicionar ícones de quatro e Sprite, basta arrastá-los para suas respectivas matrizes.</span><span class="sxs-lookup"><span data-stu-id="b16c8-232">To add quad and sprite icons, simply drag them into their respective arrays.</span></span> <span data-ttu-id="b16c8-233">Para adicionar ícones de caracteres, você deve primeiro criar e atribuir um ativo de fonte.</span><span class="sxs-lookup"><span data-stu-id="b16c8-233">To add Char icons, you must first create and assign a font asset.</span></span>

<span data-ttu-id="b16c8-234">No MRTK 2,4 e posterior, recomendamos que as texturas do ícone personalizado sejam movidas para um ícone do.</span><span class="sxs-lookup"><span data-stu-id="b16c8-234">In MRTK 2.4 and beyond, we recommend custom icon textures be moved into an IconSet.</span></span>
<span data-ttu-id="b16c8-235">Para atualizar os ativos em todos os botões de um projeto para o novo formato recomendado, use o ButtonConfigHelperMigrationHandler.</span><span class="sxs-lookup"><span data-stu-id="b16c8-235">To upgrade the assets on all buttons in a project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="b16c8-236">(O kit de ferramentas da realidade mista – utilitários de >-> janela de migração-> seleção do manipulador de migração-> Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="b16c8-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

<span data-ttu-id="b16c8-237">Importando o pacote Microsoft. MixedRealityToolkit. Unity. Tools necessário para atualizar os botões.</span><span class="sxs-lookup"><span data-stu-id="b16c8-237">Importing the Microsoft.MixedRealityToolkit.Unity.Tools package required to upgrade the buttons.</span></span>

![Caixa de diálogo atualizar janela](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="b16c8-239">Se um ícone não for encontrado no conjunto de ícones padrão durante a migração, um conjunto de ícones personalizado será criado em MixedRealityToolkit. Generated/CustomIconSets.</span><span class="sxs-lookup"><span data-stu-id="b16c8-239">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="b16c8-240">Uma caixa de diálogo indicará que isso foi realizado.</span><span class="sxs-lookup"><span data-stu-id="b16c8-240">A dialog will indicate that this has taken place.</span></span>

![Notificação de ícone personalizado](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a><span data-ttu-id="b16c8-242">Criando um ativo de fonte de ícone do HoloLens</span><span class="sxs-lookup"><span data-stu-id="b16c8-242">Creating a HoloLens Icon Font Asset</span></span>

<span data-ttu-id="b16c8-243">Primeiro, importe a fonte do ícone para o Unity.</span><span class="sxs-lookup"><span data-stu-id="b16c8-243">First, import the icon font into Unity.</span></span> <span data-ttu-id="b16c8-244">Em computadores Windows, você pode encontrar a fonte do HoloLens padrão em *Windows/fonts/holomdl2. ttf.*</span><span class="sxs-lookup"><span data-stu-id="b16c8-244">On Windows machines you can find the default HoloLens font in *Windows/Fonts/holomdl2.ttf.*</span></span> <span data-ttu-id="b16c8-245">Copie e cole esse arquivo em sua pasta de ativos.</span><span class="sxs-lookup"><span data-stu-id="b16c8-245">Copy and paste this file into your Assets folder.</span></span>

<span data-ttu-id="b16c8-246">Em seguida, abra o criador de ativos de fonte TextMeshPro por meio da **janela > TextMeshPro > criador de ativos de fonte.**</span><span class="sxs-lookup"><span data-stu-id="b16c8-246">Next, open the TextMeshPro Font Asset Creator via **Window > TextMeshPro > Font Asset Creator.**</span></span> <span data-ttu-id="b16c8-247">Aqui estão as configurações recomendadas para gerar um Atlas de fontes do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b16c8-247">Here are the recommended settings for generating a HoloLens font atlas.</span></span> <span data-ttu-id="b16c8-248">Para incluir todos os ícones, Cole o seguinte intervalo Unicode no campo de *sequência de caracteres* :</span><span class="sxs-lookup"><span data-stu-id="b16c8-248">To include all icons, paste the following Unicode range into the *Character Sequence* field:</span></span>

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Criação de botão 1](../images/button/MRTK_Font_Asset_Creation_1.png)

<span data-ttu-id="b16c8-250">Depois que o ativo de fonte for gerado, salve-o em seu projeto e atribua-o ao campo de *fonte ícone de caractere* do conjunto de ícones.</span><span class="sxs-lookup"><span data-stu-id="b16c8-250">Once the font asset is generated, save it to your project and assign it to your Icon Set's *Char Icon Font* field.</span></span> <span data-ttu-id="b16c8-251">O menu suspenso *ícones disponíveis* agora será populado.</span><span class="sxs-lookup"><span data-stu-id="b16c8-251">The *Available Icons* dropdown will now be populated.</span></span> <span data-ttu-id="b16c8-252">Para tornar um ícone disponível para ser usado por um botão, clique nele.</span><span class="sxs-lookup"><span data-stu-id="b16c8-252">To make an icon available for use by a button, click it.</span></span> <span data-ttu-id="b16c8-253">Ele será adicionado à lista suspensa *ícones selecionados* e agora será exibido no, `ButtonConfigHelper.` opcionalmente, você pode dar ao ícone uma marca.</span><span class="sxs-lookup"><span data-stu-id="b16c8-253">It will be added to the *Selected Icons* dropdown and will now show up in the `ButtonConfigHelper.` You can optionally give the icon a tag.</span></span> <span data-ttu-id="b16c8-254">Isso habilita a definição do ícone em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b16c8-254">This enables setting the icon at runtime.</span></span>

![Criação de botão 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Criação de botão 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

<span data-ttu-id="b16c8-257">Para usar o conjunto de ícones, selecione um botão, expanda o menu suspenso ícones no `ButtonConfigHelper` e atribua-o ao campo *conjunto de ícones* .</span><span class="sxs-lookup"><span data-stu-id="b16c8-257">To use your Icon Set select a button, expand the Icons dropdown in the `ButtonConfigHelper` and assign it to the *Icon Set* field.</span></span>

![Conjunto de ícones de botão](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a><span data-ttu-id="b16c8-259">Como alterar o tamanho de um botão</span><span class="sxs-lookup"><span data-stu-id="b16c8-259">How to change the size of a button</span></span>

<span data-ttu-id="b16c8-260">O tamanho do botão no estilo do shell do HoloLens 2 é 32x32mm.</span><span class="sxs-lookup"><span data-stu-id="b16c8-260">HoloLens 2's shell-style button's size is 32x32mm.</span></span> <span data-ttu-id="b16c8-261">Para personalizar a dimensão, altere o tamanho desses objetos no botão pré-fabricado:</span><span class="sxs-lookup"><span data-stu-id="b16c8-261">To customize the dimension, change the size of these objects in the button prefab:</span></span>

1. <span data-ttu-id="b16c8-262">**FrontPlate**</span><span class="sxs-lookup"><span data-stu-id="b16c8-262">**FrontPlate**</span></span>
2. <span data-ttu-id="b16c8-263">**Quado** sob placa traseira</span><span class="sxs-lookup"><span data-stu-id="b16c8-263">**Quad** under BackPlate</span></span>
3. <span data-ttu-id="b16c8-264">**Colisor de caixa** na raiz</span><span class="sxs-lookup"><span data-stu-id="b16c8-264">**Box Collider** on the root</span></span>

<span data-ttu-id="b16c8-265">Em seguida, clique no botão **corrigir limites** no script NearInteractionTouchable que está na raiz do botão.</span><span class="sxs-lookup"><span data-stu-id="b16c8-265">Then, click **Fix Bounds** button in the NearInteractionTouchable script which is in the root of the button.</span></span>

<span data-ttu-id="b16c8-266">Atualizar o tamanho do botão FrontPlate ![ personalização 1](../images/button/MRTK_Button_SizeCustomization1.png)</span><span class="sxs-lookup"><span data-stu-id="b16c8-266">Update the size of the FrontPlate ![Button Size customization 1](../images/button/MRTK_Button_SizeCustomization1.png)</span></span>

<span data-ttu-id="b16c8-267">Atualizar o tamanho da personalização do ![ tamanho do botão quádruplo 2](../images/button/MRTK_Button_SizeCustomization2.png)</span><span class="sxs-lookup"><span data-stu-id="b16c8-267">Update the size of the Quad ![Button Size customization 2](../images/button/MRTK_Button_SizeCustomization2.png)</span></span>

<span data-ttu-id="b16c8-268">Atualizar a personalização do tamanho do botão conflitante de caixa ![ 3](../images/button/MRTK_Button_SizeCustomization3.png)</span><span class="sxs-lookup"><span data-stu-id="b16c8-268">Update the size of the Box Collider ![Button Size customization 3](../images/button/MRTK_Button_SizeCustomization3.png)</span></span>

<span data-ttu-id="b16c8-269">Clique no botão "corrigir limites" ![ personalização de tamanho 4](../images/button/MRTK_Button_SizeCustomization4.png)</span><span class="sxs-lookup"><span data-stu-id="b16c8-269">Click 'Fix Bounds' ![Button Size customization 4](../images/button/MRTK_Button_SizeCustomization4.png)</span></span>

## <a name="voice-command-see-it-say-it"></a><span data-ttu-id="b16c8-270">Comando de voz (' see-it, digamos-it ')</span><span class="sxs-lookup"><span data-stu-id="b16c8-270">Voice command ('see-it, say-it')</span></span>

<span data-ttu-id="b16c8-271">**Manipulador de entrada de fala** O script de [interação](interactable.md) no botão pressionável já implementa `IMixedRealitySpeechHandler` .</span><span class="sxs-lookup"><span data-stu-id="b16c8-271">**Speech Input Handler** The [Interactable](interactable.md) script in Pressable Button already implements `IMixedRealitySpeechHandler`.</span></span> <span data-ttu-id="b16c8-272">Uma palavra-chave de comando de voz pode ser definida aqui.</span><span class="sxs-lookup"><span data-stu-id="b16c8-272">A voice command keyword can be set here.</span></span>

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

<span data-ttu-id="b16c8-273">**Perfil de entrada de fala** Além disso, você precisa registrar a palavra-chave do comando de voz no *perfil de comandos de fala* global.</span><span class="sxs-lookup"><span data-stu-id="b16c8-273">**Speech Input Profile** Additionally, you need to register the voice command keyword in the global *Speech Commands Profile*.</span></span>

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

<span data-ttu-id="b16c8-274">**Consulte-it, rótulo-it** O botão pressionável pré-fabricado tem um rótulo de espaço reservado para o TimeMesh pro sob o objeto *SeeItSayItLabel* .</span><span class="sxs-lookup"><span data-stu-id="b16c8-274">**See-it, Say-it label** The pressable button prefab has a placeholder TextMesh Pro label under the *SeeItSayItLabel* object.</span></span> <span data-ttu-id="b16c8-275">Você pode usar esse rótulo para comunicar a palavra-chave de comando de voz para o botão para o usuário.</span><span class="sxs-lookup"><span data-stu-id="b16c8-275">You can use this label to communicate the voice command keyword for the button to the user.</span></span>

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a><span data-ttu-id="b16c8-276">Como fazer um botão do zero</span><span class="sxs-lookup"><span data-stu-id="b16c8-276">How to make a button from scratch</span></span>

<span data-ttu-id="b16c8-277">Você pode encontrar os exemplos desses botões na cena **PressableButtonExample** .</span><span class="sxs-lookup"><span data-stu-id="b16c8-277">You can find the examples of these buttons in the **PressableButtonExample** scene.</span></span>

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a><span data-ttu-id="b16c8-278">1. criando um botão pressionável com Cube (somente interação próxima)</span><span class="sxs-lookup"><span data-stu-id="b16c8-278">1. Creating a pressable button with cube (near interaction only)</span></span>

1. <span data-ttu-id="b16c8-279">Criar um cubo do Unity (gameobject > objeto 3D > cubo)</span><span class="sxs-lookup"><span data-stu-id="b16c8-279">Create a Unity Cube (GameObject > 3D Object > Cube)</span></span>
2. <span data-ttu-id="b16c8-280">Adicionar `PressableButton.cs` script</span><span class="sxs-lookup"><span data-stu-id="b16c8-280">Add `PressableButton.cs` script</span></span>
3. <span data-ttu-id="b16c8-281">Adicionar `NearInteractionTouchable.cs` script</span><span class="sxs-lookup"><span data-stu-id="b16c8-281">Add `NearInteractionTouchable.cs` script</span></span>

<span data-ttu-id="b16c8-282">No `PressableButton` painel Inspetor, atribua o objeto de cubo aos visuais do **botão de movimentação**.</span><span class="sxs-lookup"><span data-stu-id="b16c8-282">In the `PressableButton`'s Inspector panel, assign the cube object to the **Moving Button Visuals**.</span></span>

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

<span data-ttu-id="b16c8-283">Ao selecionar o cubo, você verá várias camadas coloridas no objeto.</span><span class="sxs-lookup"><span data-stu-id="b16c8-283">When you select the cube, you will see multiple colored layers on the object.</span></span> <span data-ttu-id="b16c8-284">Isso visualiza os valores de distância em **configurações de pressione**.</span><span class="sxs-lookup"><span data-stu-id="b16c8-284">This visualizes the distance values under **Press Settings**.</span></span> <span data-ttu-id="b16c8-285">Usando as alças, você pode configurar quando começar a pressionar (mover o objeto) e quando disparar o evento.</span><span class="sxs-lookup"><span data-stu-id="b16c8-285">Using the handles, you can configure when to start press (move the object) and when to trigger event.</span></span>

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

<span data-ttu-id="b16c8-286">Quando você pressiona o botão, ele será movido e gerará eventos apropriados expostos no `PressableButton.cs` script, como TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased ().</span><span class="sxs-lookup"><span data-stu-id="b16c8-286">When you press the button, it will move and generate proper events exposed in the `PressableButton.cs` script such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a><span data-ttu-id="b16c8-287">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="b16c8-287">Troubleshooting</span></span>

<span data-ttu-id="b16c8-288">Se o seu botão estiver executando um pressionamento duplo, verifique se a propriedade **impor Push frontal** está ativa e se o plano de **distância de início de envio** é colocado na frente do plano de **toque próximo da interação** .</span><span class="sxs-lookup"><span data-stu-id="b16c8-288">If your button is executing a double press, make sure the **Enforce Front Push** property is active and the **Start Push Distance** plane is placed in front of the **Near Interaction Touchable** plane.</span></span> <span data-ttu-id="b16c8-289">O plano de **toque próximo à interação** é indicado pelo plano azul colocado na frente da origem da seta branca no gif abaixo:</span><span class="sxs-lookup"><span data-stu-id="b16c8-289">The **Near Interaction Touchable** plane is indicated by the blue plane placed in front of the origin of the white arrow in the gif below:</span></span>

![Componente de script de botão pressionável com impor propriedade de push frontal realçada](../images/button/MRTK_Button_Enforce_Push.png)

![Exemplo animado de mover a distância de envio por push na frente do plano de toque da interação próxima](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a><span data-ttu-id="b16c8-292">2. adicionando comentários visuais ao botão do cubo básico</span><span class="sxs-lookup"><span data-stu-id="b16c8-292">2. Adding visual feedback to the basic cube button</span></span>

<span data-ttu-id="b16c8-293">O sombreador standard do MRTK fornece vários recursos que facilitam a adição de comentários visuais.</span><span class="sxs-lookup"><span data-stu-id="b16c8-293">MRTK Standard Shader provides various features that makes it easy to add visual feedback.</span></span> <span data-ttu-id="b16c8-294">Crie um material e selecione sombreador `Mixed Reality Toolkit/Standard` .</span><span class="sxs-lookup"><span data-stu-id="b16c8-294">Create a material and select shader `Mixed Reality Toolkit/Standard`.</span></span> <span data-ttu-id="b16c8-295">Ou você pode usar ou duplicar um dos materiais existentes sob o `/SDK/StandardAssets/Materials/` que usa o sombreador padrão MRTK.</span><span class="sxs-lookup"><span data-stu-id="b16c8-295">Or you can use or duplicate one of the existing materials under `/SDK/StandardAssets/Materials/` that uses MRTK Standard Shader.</span></span>

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

<span data-ttu-id="b16c8-296">Verifique `Hover Light` e `Proximity Light` em **Opções fluentes**.</span><span class="sxs-lookup"><span data-stu-id="b16c8-296">Check `Hover Light` and `Proximity Light` under **Fluent Options**.</span></span> <span data-ttu-id="b16c8-297">Isso habilita os comentários visuais para interações de ponteiro (luz de proximidade) e ponto de flutuação distantes.</span><span class="sxs-lookup"><span data-stu-id="b16c8-297">This enables visual feedback for both near hand(Proximity Light) and far pointer(Hover Light) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a><span data-ttu-id="b16c8-298">3. adicionando comentários de áudio ao botão do cubo básico</span><span class="sxs-lookup"><span data-stu-id="b16c8-298">3. Adding audio feedback to the basic cube button</span></span>

<span data-ttu-id="b16c8-299">Como `PressableButton.cs` o script expõe eventos como TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased (), podemos atribuir facilmente Comentários de áudio.</span><span class="sxs-lookup"><span data-stu-id="b16c8-299">Since `PressableButton.cs` script exposes events such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), we can easily assign audio feedback.</span></span> <span data-ttu-id="b16c8-300">Basta adicionar Unity `Audio Source` ao objeto Cube e, em seguida, atribuir clipes de áudio selecionando audioname. PlayOneShot ().</span><span class="sxs-lookup"><span data-stu-id="b16c8-300">Simply add Unity's `Audio Source` to the cube object then assign audio clips by selecting AudioSource.PlayOneShot().</span></span> <span data-ttu-id="b16c8-301">Você pode usar MRTK_Select_Main e MRTK_Select_Secondary clipes de áudio na `/SDK/StandardAssets/Audio/` pasta.</span><span class="sxs-lookup"><span data-stu-id="b16c8-301">You can use MRTK_Select_Main and MRTK_Select_Secondary audio clips under `/SDK/StandardAssets/Audio/` folder.</span></span>

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a><span data-ttu-id="b16c8-302">4. adicionando estados visuais e manipulando eventos de interação distante</span><span class="sxs-lookup"><span data-stu-id="b16c8-302">4. Adding visual states and handle far interaction events</span></span>

<span data-ttu-id="b16c8-303">[Interagir](interactable.md) é um script que facilita a criação de um estado visual para os vários tipos de interações de entrada.</span><span class="sxs-lookup"><span data-stu-id="b16c8-303">[Interactable](interactable.md) is a script that makes it easy to create a visual state for the various types of input interactions.</span></span> <span data-ttu-id="b16c8-304">Ele também lida com eventos de interação distantes.</span><span class="sxs-lookup"><span data-stu-id="b16c8-304">It also handles far interaction events.</span></span> <span data-ttu-id="b16c8-305">Adicionar `Interactable.cs` e arrastar e soltar o objeto de cubo no campo de **destino** em **perfis**.</span><span class="sxs-lookup"><span data-stu-id="b16c8-305">Add `Interactable.cs` and drag and drop the cube object onto the **Target** field under **Profiles**.</span></span> <span data-ttu-id="b16c8-306">Em seguida, crie um novo tema com um tipo **ScaleOffsetColorTheme**.</span><span class="sxs-lookup"><span data-stu-id="b16c8-306">Then, create a new Theme with a type **ScaleOffsetColorTheme**.</span></span> <span data-ttu-id="b16c8-307">Sob esse tema, você pode especificar a cor do objeto para os Estados de interação específicos, como **foco** e **pressionado**.</span><span class="sxs-lookup"><span data-stu-id="b16c8-307">Under this theme, you can specify the color of the object for the specific interaction states, such as **Focus** and **Pressed**.</span></span> <span data-ttu-id="b16c8-308">Também é possível controlar a escala e o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="b16c8-308">You can also control Scale and Offset, as well.</span></span> <span data-ttu-id="b16c8-309">Verifique as **atenuações** e defina a duração para tornar a transição Visual suave.</span><span class="sxs-lookup"><span data-stu-id="b16c8-309">Check **Easing** and set duration to make the visual transition smooth.</span></span>

![Selecionar tema do perfil](../images/button/mrtk_button_profiles.gif)

<span data-ttu-id="b16c8-311">Você verá que o objeto responde tanto para as interações de distância (lado raio quanto para o cursor olhar) quanto ao lado (à mão).</span><span class="sxs-lookup"><span data-stu-id="b16c8-311">You will see the object respond to both far (hand ray or gaze cursor) and near(hand) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a><span data-ttu-id="b16c8-312">Exemplos de botões personalizados</span><span class="sxs-lookup"><span data-stu-id="b16c8-312">Custom button examples</span></span>

<span data-ttu-id="b16c8-313">Na [cena HandInteractionExample](../example-scenes/hand-interaction-examples.md), consulte os exemplos de piano e de botão redondo que estão usando `PressableButton` .</span><span class="sxs-lookup"><span data-stu-id="b16c8-313">In the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md), see the piano and round button examples which are both using `PressableButton`.</span></span>

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

<span data-ttu-id="b16c8-314">Cada chave de piano tem um `PressableButton` e um `NearInteractionTouchable` script atribuído.</span><span class="sxs-lookup"><span data-stu-id="b16c8-314">Each piano key has a `PressableButton` and a `NearInteractionTouchable` script assigned.</span></span> <span data-ttu-id="b16c8-315">É importante verificar se a direção de *encaminhamento local* do `NearInteractionTouchable` está correta.</span><span class="sxs-lookup"><span data-stu-id="b16c8-315">It is important to verify that the *Local Forward* direction of `NearInteractionTouchable` is correct.</span></span> <span data-ttu-id="b16c8-316">Ele é representado por uma seta branca no editor.</span><span class="sxs-lookup"><span data-stu-id="b16c8-316">It is represented by a white arrow in the editor.</span></span> <span data-ttu-id="b16c8-317">Verifique se a seta aponta para longe da face frontal do botão:</span><span class="sxs-lookup"><span data-stu-id="b16c8-317">Make sure the arrow points away from the button's front face:</span></span>

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a><span data-ttu-id="b16c8-318">Veja também</span><span class="sxs-lookup"><span data-stu-id="b16c8-318">See also</span></span>

* [<span data-ttu-id="b16c8-319">Interativo</span><span class="sxs-lookup"><span data-stu-id="b16c8-319">Interactable</span></span>](interactable.md)
* [<span data-ttu-id="b16c8-320">Temas visuais</span><span class="sxs-lookup"><span data-stu-id="b16c8-320">Visual Themes</span></span>](visual-themes.md)
