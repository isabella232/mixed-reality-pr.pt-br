---
title: Botões
description: Visão geral sobre botões no MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Botões do MRTK
ms.openlocfilehash: 16baeede2c63437e933eb1367f01af7f372cd62f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281854"
---
# <a name="buttons"></a><span data-ttu-id="c0b7f-104">Botões</span><span class="sxs-lookup"><span data-stu-id="c0b7f-104">Buttons</span></span>

![Botão Principal](../images/button/MRTK_Button_Main.png)

<span data-ttu-id="c0b7f-106">Um botão dá ao usuário uma forma de acionar uma ação imediata.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-106">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="c0b7f-107">É um dos componentes mais fundamentais na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-107">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="c0b7f-108">O MRTK fornece vários tipos de pré-requisitos de botão.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-108">MRTK provides various types of button prefabs.</span></span>

## <a name="button-prefabs-in-mrtk"></a><span data-ttu-id="c0b7f-109">Pré-requisitos de botão no MRTK</span><span class="sxs-lookup"><span data-stu-id="c0b7f-109">Button prefabs in MRTK</span></span>

<span data-ttu-id="c0b7f-110">Exemplos dos pré-requisitos de botão na ``MRTK/SDK/Features/UX/Interactable/Prefabs`` pasta</span><span class="sxs-lookup"><span data-stu-id="c0b7f-110">Examples of the button prefabs under ``MRTK/SDK/Features/UX/Interactable/Prefabs`` folder</span></span>

### <a name="unity-ui-imagegraphic-based-buttons"></a><span data-ttu-id="c0b7f-111">Botões baseados em imagem/gráfico da interface do usuário do Unity</span><span class="sxs-lookup"><span data-stu-id="c0b7f-111">Unity UI Image/Graphic based buttons</span></span>

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a><span data-ttu-id="c0b7f-112">Botões baseados em colisor</span><span class="sxs-lookup"><span data-stu-id="c0b7f-112">Collider based buttons</span></span>

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) <span data-ttu-id="c0b7f-114">PressableButtonHoloLens2</span><span class="sxs-lookup"><span data-stu-id="c0b7f-114">PressableButtonHoloLens2</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) <span data-ttu-id="c0b7f-116">PressableButtonHoloLens2Unplated</span><span class="sxs-lookup"><span data-stu-id="c0b7f-116">PressableButtonHoloLens2Unplated</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) <span data-ttu-id="c0b7f-118">PressableButtonHoloLens2Circular</span><span class="sxs-lookup"><span data-stu-id="c0b7f-118">PressableButtonHoloLens2Circular</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="c0b7f-119">HoloLens de estilo shell do HoloLens 2 com o backplate que dá suporte a vários comentários visuais, como luz de borda, luz de proximidade e placa frontal compactada</span><span class="sxs-lookup"><span data-stu-id="c0b7f-119">HoloLens 2's shell-style button with backplate which supports various visual feedback such as border light, proximity light, and compressed front plate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-120">HoloLens botão de estilo shell do 2 sem o backplate</span><span class="sxs-lookup"><span data-stu-id="c0b7f-120">HoloLens 2's shell-style button without backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-121">HoloLens de estilo shell 2 com forma circular</span><span class="sxs-lookup"><span data-stu-id="c0b7f-121">HoloLens 2's shell-style button with circular shape</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="c0b7f-122">![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-122">![PressableButtonHoloLens2_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-123">![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-123">![PressableButtonHoloLens2Bar3H](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-124">![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-124">![PressableButtonHoloLens2Bar3V](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="c0b7f-125">Largura HoloLens botão de estilo shell 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="c0b7f-125">Wide HoloLens 2's shell-style button 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-126">Barra de HoloLens 2 horizontal com o backplate compartilhado</span><span class="sxs-lookup"><span data-stu-id="c0b7f-126">Horizontal HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-127">Barra de HoloLens 2 vertical com o backplate compartilhado</span><span class="sxs-lookup"><span data-stu-id="c0b7f-127">Vertical HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="c0b7f-128">![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-128">![PressableButtonHoloLens2ToggleCheckBox_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-129">![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-129">![PressableButtonHoloLens2ToggleSwitch_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-130">![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-130">![PressableButtonHoloLens2ToggleRadio_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="c0b7f-131">HoloLens caixa de seleção estilo shell 2 32x32mm</span><span class="sxs-lookup"><span data-stu-id="c0b7f-131">HoloLens 2's shell-style checkbox 32x32mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-132">HoloLens com opção de estilo shell 2 32x32mm</span><span class="sxs-lookup"><span data-stu-id="c0b7f-132">HoloLens 2's shell-style switch 32x32mm</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-133">HoloLens rádio de estilo shell 2 32x32mm</span><span class="sxs-lookup"><span data-stu-id="c0b7f-133">HoloLens 2's shell-style radio 32x32mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="c0b7f-134">![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-134">![PressableButtonHoloLens2ToggleCheckBox_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-135">![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-135">![PressableButtonHoloLens2ToggleSwitch_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-136">![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-136">![PressableButtonHoloLens2ToggleRadio_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="c0b7f-137">HoloLens caixa de seleção de estilo shell 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="c0b7f-137">HoloLens 2's shell-style checkbox 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-138">HoloLens com opção de estilo shell 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="c0b7f-138">HoloLens 2's shell-style switch 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-139">HoloLens rádio de estilo shell 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="c0b7f-139">HoloLens 2's shell-style radio 32x96mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="c0b7f-140">![Radial ](../images/button/MRTK_Button_Radial.png) **radial**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-140">![Radial](../images/button/MRTK_Button_Radial.png) **Radial**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-141">![Caixa ](../images/button/MRTK_Button_Checkbox.png)  de seleção</span><span class="sxs-lookup"><span data-stu-id="c0b7f-141">![Checkbox](../images/button/MRTK_Button_Checkbox.png) **Checkbox**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-142">![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-142">![ToggleSwitch](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="c0b7f-143">Botão radial</span><span class="sxs-lookup"><span data-stu-id="c0b7f-143">Radial button</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-144">Caixa de seleção</span><span class="sxs-lookup"><span data-stu-id="c0b7f-144">Checkbox</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-145">Switch de alternância</span><span class="sxs-lookup"><span data-stu-id="c0b7f-145">Toggle switch</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="c0b7f-146">![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-146">![ButtonHoloLens1](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-147">![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-147">![PressableRoundButton](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-148">![Botão Base do ](../images/button/MRTK_Button_Base.png) **Botão**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-148">![Button Base](../images/button/MRTK_Button_Base.png) **Button**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="c0b7f-149">HoloLens botão de estilo de shell da 1ª geração</span><span class="sxs-lookup"><span data-stu-id="c0b7f-149">HoloLens 1st gen's shell style button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-150">Botão de push de forma arredondada</span><span class="sxs-lookup"><span data-stu-id="c0b7f-150">Round shape push button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="c0b7f-151">Botão Básico</span><span class="sxs-lookup"><span data-stu-id="c0b7f-151">Basic button</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="c0b7f-152">O `Button` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) baseia-se no conceito Interativo para fornecer controles de interface do usuário fáceis para botões ou outros tipos de superfícies interativas. [](interactable.md)</span><span class="sxs-lookup"><span data-stu-id="c0b7f-152">The `Button` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) is based on the [Interactable](interactable.md) concept to provide easy UI controls for buttons or other types of interactive surfaces.</span></span> <span data-ttu-id="c0b7f-153">O botão de linha de base dá suporte a todos os métodos de entrada disponíveis, incluindo entrada de mão articulada para as interações próximas, bem como o olhar + toque de ar para as interações distantes.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-153">The baseline button supports all available input methods, including articulated hand input for the near interactions as well as gaze + air-tap for the far interactions.</span></span> <span data-ttu-id="c0b7f-154">Você também pode usar o comando de voz para disparar o botão.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-154">You can also use voice command to trigger the button.</span></span>

<span data-ttu-id="c0b7f-155">`PressableButtonHoloLens2`(Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) é o botão de estilo de shell do HoloLens 2 que dá suporte ao movimento preciso do botão para a entrada de acompanhamento de mão direta.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) is HoloLens 2's shell style button that supports the precise movement of the button for the direct hand tracking input.</span></span> <span data-ttu-id="c0b7f-156">Ele combina `Interactable` script com `PressableButton` script.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-156">It combines `Interactable` script with `PressableButton` script.</span></span>

<span data-ttu-id="c0b7f-157">Por HoloLens 2, é recomendável usar botões com um backplate opaco.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-157">For HoloLens 2, it is recommended to use buttons with an opaque backplate.</span></span> <span data-ttu-id="c0b7f-158">Botões transparentes não são recomendados devido a esses problemas de usabilidade e estabilidade:</span><span class="sxs-lookup"><span data-stu-id="c0b7f-158">Transparent buttons are not recommended because of these usability and stability issues:</span></span>

* <span data-ttu-id="c0b7f-159">Ícone e texto são difíceis de ler com o ambiente físico</span><span class="sxs-lookup"><span data-stu-id="c0b7f-159">Icon and text are difficult to read with the physical environment</span></span>
* <span data-ttu-id="c0b7f-160">É difícil entender quando o evento é disparado</span><span class="sxs-lookup"><span data-stu-id="c0b7f-160">It is hard to understand when the event triggers</span></span>
* <span data-ttu-id="c0b7f-161">Hologramas que são exibidos por meio de um plano transparente pode ser instável com a estabilização de LSR de profundidade HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c0b7f-161">Holograms that are displayed through a transparent plane can be unstable with HoloLens 2's Depth LSR stabilization</span></span>

![Botão com o botão pressionado](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a><span data-ttu-id="c0b7f-163">Como usar botões pressionáveis</span><span class="sxs-lookup"><span data-stu-id="c0b7f-163">How to use pressable buttons</span></span>

### <a name="unity-ui-based-buttons"></a><span data-ttu-id="c0b7f-164">Botões baseados na interface do usuário do Unity</span><span class="sxs-lookup"><span data-stu-id="c0b7f-164">Unity UI based buttons</span></span>

<span data-ttu-id="c0b7f-165">Crie uma Tela em sua cena (GameObject -> interface do usuário -> Canvas).</span><span class="sxs-lookup"><span data-stu-id="c0b7f-165">Create a Canvas in your scene (GameObject -> UI -> Canvas).</span></span> <span data-ttu-id="c0b7f-166">No painel Inspetor da tela:</span><span class="sxs-lookup"><span data-stu-id="c0b7f-166">In the Inspector panel for your Canvas:</span></span>

* <span data-ttu-id="c0b7f-167">Clique em "Converter em Tela do MRTK"</span><span class="sxs-lookup"><span data-stu-id="c0b7f-167">Click "Convert to MRTK Canvas"</span></span>
* <span data-ttu-id="c0b7f-168">Clique em "Adicionar NearInteractionTouchableUnityUI"</span><span class="sxs-lookup"><span data-stu-id="c0b7f-168">Click "Add NearInteractionTouchableUnityUI"</span></span>
* <span data-ttu-id="c0b7f-169">Definir a escala X, Y e Z do componente Rect Transform como 0,001</span><span class="sxs-lookup"><span data-stu-id="c0b7f-169">Set the Rect Transform component's X, Y, and Z scale to 0.001</span></span>

<span data-ttu-id="c0b7f-170">Em seguida, arraste `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab) ou `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) na tela.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-170">Then, drag `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab), or `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) onto the Canvas.</span></span>

### <a name="collider-based-buttons"></a><span data-ttu-id="c0b7f-171">Botões baseados em colisor</span><span class="sxs-lookup"><span data-stu-id="c0b7f-171">Collider based buttons</span></span>

<span data-ttu-id="c0b7f-172">Basta arrastar `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) ou `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) para a cena.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-172">Simply drag `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) or `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) into the scene.</span></span> <span data-ttu-id="c0b7f-173">Esses pré-fabs de botão já estão configurados para ter comentários audiovisual para os vários tipos de entradas, incluindo entrada e olhar de mão articulados.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-173">These button prefabs are already configured to have audio-visual feedback for the various types of inputs, including articulated hand input and gaze.</span></span>

<span data-ttu-id="c0b7f-174">Os eventos expostos no próprio pré-fab, bem como o componente Interacionável, podem ser usados para disparar ações adicionais. [](interactable.md)</span><span class="sxs-lookup"><span data-stu-id="c0b7f-174">The events exposed in the prefab itself as well as the [Interactable](interactable.md) component can be used to trigger additional actions.</span></span> <span data-ttu-id="c0b7f-175">Os botões pressionáveis na cena [HandInteractionExample](../example-scenes/hand-interaction-examples.md) usam o evento *OnClick* do Interactable para disparar uma alteração na cor de um cubo.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-175">The pressable buttons in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md) use Interactable's *OnClick* event to trigger a change in the color of a cube.</span></span> <span data-ttu-id="c0b7f-176">Esse evento é disparado para diferentes tipos de métodos de entrada, como gaze, toque de ar, raio de mão, bem como pressiona o botão físico por meio do script de botão pressionável.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-176">This event gets triggered for different types of input methods such as gaze, air-tap, hand-ray, as well as physical button presses through the pressable button script.</span></span>

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

<span data-ttu-id="c0b7f-177">Você pode configurar quando o botão pressionável disparar o *evento OnClick* por meio `PhysicalPressEventRouter` do no botão.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-177">You can configure when the pressable button fires the *OnClick* event via the `PhysicalPressEventRouter` on the button.</span></span> <span data-ttu-id="c0b7f-178">Por exemplo, você pode definir *OnClick* para ativá-lo quando o botão for pressionado pela primeira vez, em vez de ser pressionado e liberado, definindo *Interactable On* Click to *Event On Press*.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-178">For example, you can set *OnClick* to fire when the button is first pressed, as opposed to being pressed and released, by setting *Interactable On Click* to *Event On Press*.</span></span>

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

<span data-ttu-id="c0b7f-179">Para aproveitar informações específicas de estado de entrada da mão articulada, você pode usar eventos de botões pressionáveis – *Início* do Toque, *Toque Final,* Botão *Pressionado,* *Botão Liberado.*</span><span class="sxs-lookup"><span data-stu-id="c0b7f-179">To leverage specific articulated hand input state information, you can use pressable buttons events - *Touch Begin*, *Touch End*, *Button Pressed*, *Button Released*.</span></span> <span data-ttu-id="c0b7f-180">No entanto, esses eventos não serão ativas em resposta a entradas de toque no ar, raio de mão ou olho.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-180">These events will not fire in response to air-tap, hand-ray, or eye inputs, however.</span></span> <span data-ttu-id="c0b7f-181">**Para dar suporte a interações próximas e distantes, é recomendável usar o evento *OnClick* do Interactable.**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-181">**To support both near and far interactions, it is recommended to use Interactable's *OnClick* event.**</span></span>

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a><span data-ttu-id="c0b7f-182">Estados de interação</span><span class="sxs-lookup"><span data-stu-id="c0b7f-182">Interaction states</span></span>

<span data-ttu-id="c0b7f-183">No estado ocioso, a placa frontal do botão não está visível.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-183">In the idle state, the button's front plate is not visible.</span></span> <span data-ttu-id="c0b7f-184">À medida que um dedo se aproxima ou um cursor da entrada de olhar tem como alvo a superfície, a borda vermelha da placa frontal se torna visível.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-184">As a finger approaches or a cursor from gaze input targets the surface, the front plate's glowing border becomes visible.</span></span> <span data-ttu-id="c0b7f-185">Há realçamento adicional da posição do dedo na superfície da placa frontal.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-185">There is additional highlighting of the fingertip position on the front plate surface.</span></span> <span data-ttu-id="c0b7f-186">Quando pressionado com um dedo, a placa frontal se move com a ponta do dedo.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-186">When pushed with a finger, the front plate moves with the fingertip.</span></span> <span data-ttu-id="c0b7f-187">Quando a ponta do dedo toca a superfície da placa frontal, ela mostra um efeito de pulso sutil para dar comentários visuais sobre o ponto de toque.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-187">When the fingertip touches the surface of the front plate, it shows a subtle pulse effect to give visual feedback of the touch point.</span></span>

<span data-ttu-id="c0b7f-188">No HoloLens de estilo shell 2, há muitas dicas visuais e recursos para aumentar a confiança do usuário na interação.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-188">In HoloLens 2 shell-style button, there are many visual cues and affordances to increase the user's confidence on interaction.</span></span>

|  ![Luz de proximidade](../images/button/ux_button_affordance_proximitylight.jpg) | ![Realçando o foco](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Compactando a cadeia](../images/button/ux_button_affordance_compression.jpg) | ![Pulso no gatilho](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="c0b7f-193">Luz de proximidade</span><span class="sxs-lookup"><span data-stu-id="c0b7f-193">Proximity light</span></span> | <span data-ttu-id="c0b7f-194">Realçando o foco</span><span class="sxs-lookup"><span data-stu-id="c0b7f-194">Focus highlight</span></span> | <span data-ttu-id="c0b7f-195">Compactando a cadeia</span><span class="sxs-lookup"><span data-stu-id="c0b7f-195">Compressing cage</span></span> | <span data-ttu-id="c0b7f-196">Pulso no gatilho</span><span class="sxs-lookup"><span data-stu-id="c0b7f-196">Pulse on trigger</span></span> |

<span data-ttu-id="c0b7f-197">O efeito de pulso sutil é disparado pelo botão pressionável, que procura por *ProximityLight* que estão no ponteiro que está interagindo no momento.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-197">The subtle pulse effect is triggered by the pressable button, which looks for *ProximityLight(s)* that live on the currently interacting pointer.</span></span> <span data-ttu-id="c0b7f-198">Se alguma luz de proximidade for encontrada, o método será chamado, o que animará automaticamente os parâmetros do sombreador `ProximityLight.Pulse` para exibir um pulso.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-198">If any proximity lights are found, the `ProximityLight.Pulse` method is called, which automatically animates shader parameters to display a pulse.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="c0b7f-199">Propriedades do inspetor</span><span class="sxs-lookup"><span data-stu-id="c0b7f-199">Inspector properties</span></span>

![Estrutura do botão](../images/button/MRTK_Button_Structure.png)

<span data-ttu-id="c0b7f-201"> 
 Colisor `Box Collide\r` de caixa para a placa frontal do botão.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-201">**Box Collider**
`Box Collider` for the button's front plate.</span></span>

<span data-ttu-id="c0b7f-202">**Botão pressionável** A lógica do botão de movimentação com a interação de pressionar à mão.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-202">**Pressable Button** The logic for the button movement with hand press interaction.</span></span>

<span data-ttu-id="c0b7f-203">**Roteador de evento de prensa física** Esse script envia eventos da interação de pressionar mão para [interagir](interactable.md).</span><span class="sxs-lookup"><span data-stu-id="c0b7f-203">**Physical Press Event Router** This script sends events from hand press interaction to [Interactable](interactable.md).</span></span>

<span data-ttu-id="c0b7f-204">**Interagir** 
 [Interagir](interactable.md) manipula vários tipos de Estados de interação e eventos.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-204">**Interactable**
[Interactable](interactable.md) handles various types of interaction states and events.</span></span> <span data-ttu-id="c0b7f-205">HoloLens olhar, gesto e entrada de voz e entrada do controlador de movimento de headset de imersão são tratados diretamente por esse script.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-205">HoloLens gaze, gesture, and voice input and immersive headset motion controller input are directly handled by this script.</span></span>

<span data-ttu-id="c0b7f-206">**Fonte de áudio** Fonte de áudio do Unity para os clipes de comentários de áudio.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-206">**Audio Source** Unity audio source for the audio feedback clips.</span></span>

<span data-ttu-id="c0b7f-207">*NearInteractionTouchable. cs* necessário para tornar qualquer objeto tocável com entrada de mão articulada.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-207">*NearInteractionTouchable.cs* Required to make any object touchable with articulated hand input.</span></span>

## <a name="prefab-layout"></a><span data-ttu-id="c0b7f-208">Layout de pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="c0b7f-208">Prefab layout</span></span>

<span data-ttu-id="c0b7f-209">O objeto *ButtonContent* contém a placa frontal, o rótulo de texto e o ícone.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-209">The *ButtonContent* object contains front plate, text label and icon.</span></span> <span data-ttu-id="c0b7f-210">O *FrontPlate* responde à proximidade do índice usando o sombreador de *Button_Box* .</span><span class="sxs-lookup"><span data-stu-id="c0b7f-210">The *FrontPlate* responds to the proximity of the index fingertip using the *Button_Box* shader.</span></span> <span data-ttu-id="c0b7f-211">Ele mostra bordas brilhantes, luz de proximidade e um efeito de pulso sobre toque.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-211">It shows glowing borders, proximity light, and a pulse effect on touch.</span></span> <span data-ttu-id="c0b7f-212">O rótulo de texto é feito com textmesh Pro.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-212">The text label is made with TextMesh Pro.</span></span> <span data-ttu-id="c0b7f-213">A visibilidade do *SeeItSayItLabel* é controlada pelo tema de [interação](interactable.md).</span><span class="sxs-lookup"><span data-stu-id="c0b7f-213">*SeeItSayItLabel*'s visibility is controlled by [Interactable](interactable.md)'s theme.</span></span>

![Layout do botão](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a><span data-ttu-id="c0b7f-215">Como alterar o ícone e o texto</span><span class="sxs-lookup"><span data-stu-id="c0b7f-215">How to change the icon and text</span></span>

<span data-ttu-id="c0b7f-216">Os botões MRTK usam um `ButtonConfigHelper` componente para ajudá-lo a alterar o ícone, o texto e o rótulo do botão.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-216">MRTK buttons use a `ButtonConfigHelper` component to assist you in changing the button's icon, text and label.</span></span> <span data-ttu-id="c0b7f-217">(Observe que alguns campos podem estar ausentes se os elementos não estiverem presentes no botão selecionado.)</span><span class="sxs-lookup"><span data-stu-id="c0b7f-217">(Note that some fields may be absent if elements are not present on the selected button.)</span></span>

![Auxiliar de configuração de botão](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a><span data-ttu-id="c0b7f-219">Criando e modificando conjuntos de ícones</span><span class="sxs-lookup"><span data-stu-id="c0b7f-219">Creating and Modifying Icon Sets</span></span>

<span data-ttu-id="c0b7f-220">Um **conjunto de ícones** é um conjunto compartilhado de ativos de ícone usado pelo `ButtonConfigHelper` componente.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-220">An **Icon Set** is a shared set of icon assets used by the `ButtonConfigHelper` component.</span></span> <span data-ttu-id="c0b7f-221">Há suporte para três *estilos* de ícone.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-221">Three icon *styles* are supported.</span></span>

* <span data-ttu-id="c0b7f-222">Ícones **quádruplos** são renderizados em um quad usando um `MeshRenderer` .</span><span class="sxs-lookup"><span data-stu-id="c0b7f-222">**Quad** icons are rendered on a quad using a `MeshRenderer`.</span></span> <span data-ttu-id="c0b7f-223">Esse é o estilo de ícone padrão.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-223">This is the default icon style.</span></span>
* <span data-ttu-id="c0b7f-224">Os ícones de **Sprite** são renderizados usando um `SpriteRenderer` .</span><span class="sxs-lookup"><span data-stu-id="c0b7f-224">**Sprite** icons are rendered using a `SpriteRenderer`.</span></span> <span data-ttu-id="c0b7f-225">Isso será útil se você preferir importar os ícones como uma folha de Sprite ou se quiser que os ativos de ícone sejam compartilhados com os componentes da interface do usuário do Unity.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-225">This is useful if you prefer to import your icons as a sprite sheet, or if you want your icon assets to be shared with Unity UI components.</span></span> <span data-ttu-id="c0b7f-226">para usar esse estilo, você precisará instalar o pacote do Editor Sprite **(Windows-> Gerenciador de Pacotes-> 2d Sprite)**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-226">To use this style you will need to install the Sprite Editor package **(Windows -> Package Manager -> 2D Sprite)**</span></span>
* <span data-ttu-id="c0b7f-227">Ícones de **caracteres** são renderizados usando um `TextMeshPro` componente.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-227">**Char** icons are rendered using a `TextMeshPro` component.</span></span> <span data-ttu-id="c0b7f-228">Isso será útil se você preferir usar uma fonte de ícone.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-228">This is useful if you prefer to use an icon font.</span></span> <span data-ttu-id="c0b7f-229">para usar a fonte do ícone de HoloLens, você precisará criar um `TextMeshPro` ativo de fonte.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-229">To use the HoloLens icon font you will need to create a `TextMeshPro` font asset.</span></span>

<span data-ttu-id="c0b7f-230">Para alterar o estilo que seu botão usa, expanda a lista suspensa *ícones* no ButtonConfigHelper e selecione na lista suspensa *estilo de ícone* .</span><span class="sxs-lookup"><span data-stu-id="c0b7f-230">To change which style your button uses, expand the *Icons* dropdown in the ButtonConfigHelper and select from the *Icon Style* dropdown.</span></span>

<span data-ttu-id="c0b7f-231">você pode criar um novo ícone de botão definido com o menu ativo: **criar > realidade misturada Toolkit ícone > conjunto.**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-231">You can create a new button icon set with the asset menu: **Create > Mixed Reality Toolkit > Icon Set.**</span></span> <span data-ttu-id="c0b7f-232">Para adicionar ícones de quatro e Sprite, basta arrastá-los para suas respectivas matrizes.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-232">To add quad and sprite icons, simply drag them into their respective arrays.</span></span> <span data-ttu-id="c0b7f-233">Para adicionar ícones de caracteres, você deve primeiro criar e atribuir um ativo de fonte.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-233">To add Char icons, you must first create and assign a font asset.</span></span>

<span data-ttu-id="c0b7f-234">No MRTK 2,4 e posterior, recomendamos que as texturas do ícone personalizado sejam movidas para um ícone do.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-234">In MRTK 2.4 and beyond, we recommend custom icon textures be moved into an IconSet.</span></span>
<span data-ttu-id="c0b7f-235">Para atualizar os ativos em todos os botões de um projeto para o novo formato recomendado, use o ButtonConfigHelperMigrationHandler.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-235">To upgrade the assets on all buttons in a project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="c0b7f-236">(Toolkit de realidade misturada-> utilitários-> janela de migração-> seleção do manipulador de migração-> Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="c0b7f-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

<span data-ttu-id="c0b7f-237">Importando o pacote Microsoft. MixedRealityToolkit. Unity. Tools necessário para atualizar os botões.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-237">Importing the Microsoft.MixedRealityToolkit.Unity.Tools package required to upgrade the buttons.</span></span>

![Caixa de diálogo atualizar janela](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="c0b7f-239">Se um ícone não for encontrado no conjunto de ícones padrão durante a migração, um conjunto de ícones personalizado será criado em MixedRealityToolkit. Generated/CustomIconSets.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-239">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="c0b7f-240">Uma caixa de diálogo indicará que isso foi realizado.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-240">A dialog will indicate that this has taken place.</span></span>

![Notificação de ícone personalizado](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a><span data-ttu-id="c0b7f-242">criando um ativo de fonte de ícone de HoloLens</span><span class="sxs-lookup"><span data-stu-id="c0b7f-242">Creating a HoloLens Icon Font Asset</span></span>

<span data-ttu-id="c0b7f-243">Primeiro, importe a fonte do ícone para o Unity.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-243">First, import the icon font into Unity.</span></span> <span data-ttu-id="c0b7f-244">em computadores Windows, você pode encontrar a fonte de HoloLens padrão em *Windows/Fonts/holomdl2.ttf.*</span><span class="sxs-lookup"><span data-stu-id="c0b7f-244">On Windows machines you can find the default HoloLens font in *Windows/Fonts/holomdl2.ttf.*</span></span> <span data-ttu-id="c0b7f-245">Copie e cole esse arquivo em sua pasta de ativos.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-245">Copy and paste this file into your Assets folder.</span></span>

<span data-ttu-id="c0b7f-246">Em seguida, abra o criador de ativos de fonte TextMeshPro por meio da **janela > TextMeshPro > criador de ativos de fonte.**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-246">Next, open the TextMeshPro Font Asset Creator via **Window > TextMeshPro > Font Asset Creator.**</span></span> <span data-ttu-id="c0b7f-247">aqui estão as configurações recomendadas para gerar um HoloLens atlas de fontes.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-247">Here are the recommended settings for generating a HoloLens font atlas.</span></span> <span data-ttu-id="c0b7f-248">Para incluir todos os ícones, Cole o seguinte intervalo Unicode no campo de *sequência de caracteres* :</span><span class="sxs-lookup"><span data-stu-id="c0b7f-248">To include all icons, paste the following Unicode range into the *Character Sequence* field:</span></span>

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Criação de botão 1](../images/button/MRTK_Font_Asset_Creation_1.png)

<span data-ttu-id="c0b7f-250">Depois que o ativo de fonte for gerado, salve-o em seu projeto e atribua-o ao campo de *fonte ícone de caractere* do conjunto de ícones.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-250">Once the font asset is generated, save it to your project and assign it to your Icon Set's *Char Icon Font* field.</span></span> <span data-ttu-id="c0b7f-251">O menu suspenso *ícones disponíveis* agora será populado.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-251">The *Available Icons* dropdown will now be populated.</span></span> <span data-ttu-id="c0b7f-252">Para tornar um ícone disponível para ser usado por um botão, clique nele.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-252">To make an icon available for use by a button, click it.</span></span> <span data-ttu-id="c0b7f-253">Ele será adicionado à lista suspensa *ícones selecionados* e agora será exibido no, `ButtonConfigHelper.` opcionalmente, você pode dar ao ícone uma marca.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-253">It will be added to the *Selected Icons* dropdown and will now show up in the `ButtonConfigHelper.` You can optionally give the icon a tag.</span></span> <span data-ttu-id="c0b7f-254">Isso habilita a definição do ícone em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-254">This enables setting the icon at runtime.</span></span>

![Criação de botão 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Criação de botão 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

<span data-ttu-id="c0b7f-257">Para usar o conjunto de ícones, selecione um botão, expanda o menu suspenso ícones no `ButtonConfigHelper` e atribua-o ao campo *conjunto de ícones* .</span><span class="sxs-lookup"><span data-stu-id="c0b7f-257">To use your Icon Set select a button, expand the Icons dropdown in the `ButtonConfigHelper` and assign it to the *Icon Set* field.</span></span>

![Conjunto de ícones de botão](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a><span data-ttu-id="c0b7f-259">Como alterar o tamanho de um botão</span><span class="sxs-lookup"><span data-stu-id="c0b7f-259">How to change the size of a button</span></span>

<span data-ttu-id="c0b7f-260">o tamanho do botão do estilo de shell do HoloLens 2 é 32x32mm.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-260">HoloLens 2's shell-style button's size is 32x32mm.</span></span> <span data-ttu-id="c0b7f-261">Para personalizar a dimensão, altere o tamanho desses objetos no botão pré-fabricado:</span><span class="sxs-lookup"><span data-stu-id="c0b7f-261">To customize the dimension, change the size of these objects in the button prefab:</span></span>

1. <span data-ttu-id="c0b7f-262">**FrontPlate**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-262">**FrontPlate**</span></span>
2. <span data-ttu-id="c0b7f-263">**Quado** sob placa traseira</span><span class="sxs-lookup"><span data-stu-id="c0b7f-263">**Quad** under BackPlate</span></span>
3. <span data-ttu-id="c0b7f-264">**Colisor de caixa** na raiz</span><span class="sxs-lookup"><span data-stu-id="c0b7f-264">**Box Collider** on the root</span></span>

<span data-ttu-id="c0b7f-265">Em seguida, clique no botão **corrigir limites** no script NearInteractionTouchable que está na raiz do botão.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-265">Then, click **Fix Bounds** button in the NearInteractionTouchable script which is in the root of the button.</span></span>

<span data-ttu-id="c0b7f-266">Atualizar o tamanho do botão FrontPlate ![ personalização 1](../images/button/MRTK_Button_SizeCustomization1.png)</span><span class="sxs-lookup"><span data-stu-id="c0b7f-266">Update the size of the FrontPlate ![Button Size customization 1](../images/button/MRTK_Button_SizeCustomization1.png)</span></span>

<span data-ttu-id="c0b7f-267">Atualizar o tamanho da personalização do ![ tamanho do botão quádruplo 2](../images/button/MRTK_Button_SizeCustomization2.png)</span><span class="sxs-lookup"><span data-stu-id="c0b7f-267">Update the size of the Quad ![Button Size customization 2](../images/button/MRTK_Button_SizeCustomization2.png)</span></span>

<span data-ttu-id="c0b7f-268">Atualizar a personalização do tamanho do botão conflitante de caixa ![ 3](../images/button/MRTK_Button_SizeCustomization3.png)</span><span class="sxs-lookup"><span data-stu-id="c0b7f-268">Update the size of the Box Collider ![Button Size customization 3](../images/button/MRTK_Button_SizeCustomization3.png)</span></span>

<span data-ttu-id="c0b7f-269">Clique no botão "corrigir limites" ![ personalização de tamanho 4](../images/button/MRTK_Button_SizeCustomization4.png)</span><span class="sxs-lookup"><span data-stu-id="c0b7f-269">Click 'Fix Bounds' ![Button Size customization 4](../images/button/MRTK_Button_SizeCustomization4.png)</span></span>

## <a name="voice-command-see-it-say-it"></a><span data-ttu-id="c0b7f-270">Comando de voz (' see-it, digamos-it ')</span><span class="sxs-lookup"><span data-stu-id="c0b7f-270">Voice command ('see-it, say-it')</span></span>

<span data-ttu-id="c0b7f-271">**Manipulador de entrada de fala** O script de [interação](interactable.md) no botão pressionável já implementa `IMixedRealitySpeechHandler` .</span><span class="sxs-lookup"><span data-stu-id="c0b7f-271">**Speech Input Handler** The [Interactable](interactable.md) script in Pressable Button already implements `IMixedRealitySpeechHandler`.</span></span> <span data-ttu-id="c0b7f-272">Uma palavra-chave de comando de voz pode ser definida aqui.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-272">A voice command keyword can be set here.</span></span>

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

<span data-ttu-id="c0b7f-273">**Perfil de entrada de fala** Além disso, você precisa registrar a palavra-chave do comando de voz no *perfil de comandos de fala* global.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-273">**Speech Input Profile** Additionally, you need to register the voice command keyword in the global *Speech Commands Profile*.</span></span>

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

<span data-ttu-id="c0b7f-274">**Consulte-it, rótulo-it** o botão pressionável pré-fabricado tem um espaço reservado para Pro o rótulo do timemesh no objeto *SeeItSayItLabel* .</span><span class="sxs-lookup"><span data-stu-id="c0b7f-274">**See-it, Say-it label** The pressable button prefab has a placeholder TextMesh Pro label under the *SeeItSayItLabel* object.</span></span> <span data-ttu-id="c0b7f-275">Você pode usar esse rótulo para comunicar a palavra-chave de comando de voz para o botão para o usuário.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-275">You can use this label to communicate the voice command keyword for the button to the user.</span></span>

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a><span data-ttu-id="c0b7f-276">Como fazer um botão do zero</span><span class="sxs-lookup"><span data-stu-id="c0b7f-276">How to make a button from scratch</span></span>

<span data-ttu-id="c0b7f-277">Você pode encontrar os exemplos desses botões na cena **PressableButtonExample** .</span><span class="sxs-lookup"><span data-stu-id="c0b7f-277">You can find the examples of these buttons in the **PressableButtonExample** scene.</span></span>

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a><span data-ttu-id="c0b7f-278">1. criando um botão pressionável com Cube (somente interação próxima)</span><span class="sxs-lookup"><span data-stu-id="c0b7f-278">1. Creating a pressable button with cube (near interaction only)</span></span>

1. <span data-ttu-id="c0b7f-279">Criar um cubo do Unity (gameobject > objeto 3D > cubo)</span><span class="sxs-lookup"><span data-stu-id="c0b7f-279">Create a Unity Cube (GameObject > 3D Object > Cube)</span></span>
2. <span data-ttu-id="c0b7f-280">Adicionar `PressableButton.cs` script</span><span class="sxs-lookup"><span data-stu-id="c0b7f-280">Add `PressableButton.cs` script</span></span>
3. <span data-ttu-id="c0b7f-281">Adicionar `NearInteractionTouchable.cs` script</span><span class="sxs-lookup"><span data-stu-id="c0b7f-281">Add `NearInteractionTouchable.cs` script</span></span>

<span data-ttu-id="c0b7f-282">No `PressableButton` painel Inspetor, atribua o objeto de cubo aos visuais do **botão de movimentação**.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-282">In the `PressableButton`'s Inspector panel, assign the cube object to the **Moving Button Visuals**.</span></span>

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

<span data-ttu-id="c0b7f-283">Ao selecionar o cubo, você verá várias camadas coloridas no objeto.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-283">When you select the cube, you will see multiple colored layers on the object.</span></span> <span data-ttu-id="c0b7f-284">isso visualiza os valores de distância em **pressionar Configurações**.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-284">This visualizes the distance values under **Press Settings**.</span></span> <span data-ttu-id="c0b7f-285">Usando as alças, você pode configurar quando começar a pressionar (mover o objeto) e quando disparar o evento.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-285">Using the handles, you can configure when to start press (move the object) and when to trigger event.</span></span>

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

<span data-ttu-id="c0b7f-286">Quando você pressiona o botão, ele será movido e gerará eventos apropriados expostos no `PressableButton.cs` script, como TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased ().</span><span class="sxs-lookup"><span data-stu-id="c0b7f-286">When you press the button, it will move and generate proper events exposed in the `PressableButton.cs` script such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a><span data-ttu-id="c0b7f-287">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="c0b7f-287">Troubleshooting</span></span>

<span data-ttu-id="c0b7f-288">Se o seu botão estiver executando um pressionamento duplo, verifique se a propriedade **impor Push frontal** está ativa e se o plano de **distância de início de envio** é colocado na frente do plano de **toque próximo da interação** .</span><span class="sxs-lookup"><span data-stu-id="c0b7f-288">If your button is executing a double press, make sure the **Enforce Front Push** property is active and the **Start Push Distance** plane is placed in front of the **Near Interaction Touchable** plane.</span></span> <span data-ttu-id="c0b7f-289">O plano de **toque próximo à interação** é indicado pelo plano azul colocado na frente da origem da seta branca no gif abaixo:</span><span class="sxs-lookup"><span data-stu-id="c0b7f-289">The **Near Interaction Touchable** plane is indicated by the blue plane placed in front of the origin of the white arrow in the gif below:</span></span>

![Componente de script de botão pressionável com impor propriedade de push frontal realçada](../images/button/MRTK_Button_Enforce_Push.png)

![Exemplo animado de mover a distância de envio por push na frente do plano de toque da interação próxima](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a><span data-ttu-id="c0b7f-292">2. adicionando comentários visuais ao botão do cubo básico</span><span class="sxs-lookup"><span data-stu-id="c0b7f-292">2. Adding visual feedback to the basic cube button</span></span>

<span data-ttu-id="c0b7f-293">O sombreador standard do MRTK fornece vários recursos que facilitam a adição de comentários visuais.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-293">MRTK Standard Shader provides various features that makes it easy to add visual feedback.</span></span> <span data-ttu-id="c0b7f-294">Crie um material e selecione sombreador `Mixed Reality Toolkit/Standard` .</span><span class="sxs-lookup"><span data-stu-id="c0b7f-294">Create a material and select shader `Mixed Reality Toolkit/Standard`.</span></span> <span data-ttu-id="c0b7f-295">Ou você pode usar ou duplicar um dos materiais existentes sob o `/SDK/StandardAssets/Materials/` que usa o sombreador padrão MRTK.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-295">Or you can use or duplicate one of the existing materials under `/SDK/StandardAssets/Materials/` that uses MRTK Standard Shader.</span></span>

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

<span data-ttu-id="c0b7f-296">verifique `Hover Light` e `Proximity Light` em **opções de Fluent**.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-296">Check `Hover Light` and `Proximity Light` under **Fluent Options**.</span></span> <span data-ttu-id="c0b7f-297">Isso habilita os comentários visuais para interações de ponteiro (luz de proximidade) e ponto de flutuação distantes.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-297">This enables visual feedback for both near hand(Proximity Light) and far pointer(Hover Light) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a><span data-ttu-id="c0b7f-298">3. adicionando comentários de áudio ao botão do cubo básico</span><span class="sxs-lookup"><span data-stu-id="c0b7f-298">3. Adding audio feedback to the basic cube button</span></span>

<span data-ttu-id="c0b7f-299">Como `PressableButton.cs` o script expõe eventos como TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased (), podemos atribuir facilmente Comentários de áudio.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-299">Since `PressableButton.cs` script exposes events such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), we can easily assign audio feedback.</span></span> <span data-ttu-id="c0b7f-300">Basta adicionar Unity `Audio Source` ao objeto Cube e, em seguida, atribuir clipes de áudio selecionando audioname. PlayOneShot ().</span><span class="sxs-lookup"><span data-stu-id="c0b7f-300">Simply add Unity's `Audio Source` to the cube object then assign audio clips by selecting AudioSource.PlayOneShot().</span></span> <span data-ttu-id="c0b7f-301">Você pode usar MRTK_Select_Main e MRTK_Select_Secondary clipes de áudio na `/SDK/StandardAssets/Audio/` pasta .</span><span class="sxs-lookup"><span data-stu-id="c0b7f-301">You can use MRTK_Select_Main and MRTK_Select_Secondary audio clips under `/SDK/StandardAssets/Audio/` folder.</span></span>

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a><span data-ttu-id="c0b7f-302">4. Adicionar estados visuais e manipular eventos de interação distantes</span><span class="sxs-lookup"><span data-stu-id="c0b7f-302">4. Adding visual states and handle far interaction events</span></span>

<span data-ttu-id="c0b7f-303">[Interajante](interactable.md) é um script que facilita a criação de um estado visual para os vários tipos de interações de entrada.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-303">[Interactable](interactable.md) is a script that makes it easy to create a visual state for the various types of input interactions.</span></span> <span data-ttu-id="c0b7f-304">Ele também lida com eventos de interação distantes.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-304">It also handles far interaction events.</span></span> <span data-ttu-id="c0b7f-305">Adicione `Interactable.cs` e arraste e solte o objeto de cubo no **campo** Destino em **Perfis**.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-305">Add `Interactable.cs` and drag and drop the cube object onto the **Target** field under **Profiles**.</span></span> <span data-ttu-id="c0b7f-306">Em seguida, crie um novo Tema com um tipo **ScaleOffsetColorTheme**.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-306">Then, create a new Theme with a type **ScaleOffsetColorTheme**.</span></span> <span data-ttu-id="c0b7f-307">Nesse tema, você pode especificar a cor do objeto para os estados de interação específicos, como **Foco** **e Pressionado.**</span><span class="sxs-lookup"><span data-stu-id="c0b7f-307">Under this theme, you can specify the color of the object for the specific interaction states, such as **Focus** and **Pressed**.</span></span> <span data-ttu-id="c0b7f-308">Você também pode controlar Escala e Deslocamento.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-308">You can also control Scale and Offset, as well.</span></span> <span data-ttu-id="c0b7f-309">Verifique **Easing e** de definir a duração para tornar a transição visual suave.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-309">Check **Easing** and set duration to make the visual transition smooth.</span></span>

![Selecionar tema de perfil](../images/button/mrtk_button_profiles.gif)

<span data-ttu-id="c0b7f-311">Você verá o objeto responder a interações distantes (raio de mão ou cursor de olhar) e próximas (mão).</span><span class="sxs-lookup"><span data-stu-id="c0b7f-311">You will see the object respond to both far (hand ray or gaze cursor) and near(hand) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a><span data-ttu-id="c0b7f-312">Exemplos de botão personalizados</span><span class="sxs-lookup"><span data-stu-id="c0b7f-312">Custom button examples</span></span>

<span data-ttu-id="c0b7f-313">Na cena [HandInteractionExample](../example-scenes/hand-interaction-examples.md), consulte os exemplos de botão round e de round que estão usando `PressableButton` .</span><span class="sxs-lookup"><span data-stu-id="c0b7f-313">In the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md), see the piano and round button examples which are both using `PressableButton`.</span></span>

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

<span data-ttu-id="c0b7f-314">Cada chave de grupo tem `PressableButton` um e um script `NearInteractionTouchable` atribuídos.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-314">Each piano key has a `PressableButton` and a `NearInteractionTouchable` script assigned.</span></span> <span data-ttu-id="c0b7f-315">É importante verificar se a direção *de Encaminhamento Local* de está `NearInteractionTouchable` correta.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-315">It is important to verify that the *Local Forward* direction of `NearInteractionTouchable` is correct.</span></span> <span data-ttu-id="c0b7f-316">Ele é representado por uma seta branca no editor.</span><span class="sxs-lookup"><span data-stu-id="c0b7f-316">It is represented by a white arrow in the editor.</span></span> <span data-ttu-id="c0b7f-317">Certifique-se de que a seta aponta para fora da face frontal do botão:</span><span class="sxs-lookup"><span data-stu-id="c0b7f-317">Make sure the arrow points away from the button's front face:</span></span>

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a><span data-ttu-id="c0b7f-318">Confira também</span><span class="sxs-lookup"><span data-stu-id="c0b7f-318">See also</span></span>

* [<span data-ttu-id="c0b7f-319">Interativo</span><span class="sxs-lookup"><span data-stu-id="c0b7f-319">Interactable</span></span>](interactable.md)
* [<span data-ttu-id="c0b7f-320">Temas visuais</span><span class="sxs-lookup"><span data-stu-id="c0b7f-320">Visual Themes</span></span>](visual-themes.md)
