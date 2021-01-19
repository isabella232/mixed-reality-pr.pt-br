---
title: Introdução ao MRTK – Como usar interações espaciais comuns
description: Como usar o Kit de Ferramentas de Realidade Misturada do Unity para interações básicas para HoloLens 2, HoloLens, Windows Mixed Reality e Open VR.
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada, Windows Mixed Reality, design, aplicativo de exemplo, controles, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.localizationpriority: high
ms.openlocfilehash: 8b9af843dc059ef4d50aa5508356c7aeed968a4e
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98248022"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="73591-104">MRTK 101: Como usar o Kit de Ferramentas de Realidade Misturada do Unity para interações espaciais</span><span class="sxs-lookup"><span data-stu-id="73591-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="73591-106">Saiba mais sobre como usar o MRTK para obter alguns dos padrões comuns de interação mais amplamente usados em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="73591-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="73591-107">Como simular as interações de entrada no editor do Unity?</span><span class="sxs-lookup"><span data-stu-id="73591-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="73591-108">Como pegar e mover um objeto?</span><span class="sxs-lookup"><span data-stu-id="73591-108">How to grab and move an object?</span></span>
- <span data-ttu-id="73591-109">Como redimensionar um objeto?</span><span class="sxs-lookup"><span data-stu-id="73591-109">How to resize an object?</span></span>
- <span data-ttu-id="73591-110">Como mover ou girar um objeto com precisão?</span><span class="sxs-lookup"><span data-stu-id="73591-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="73591-111">Como fazer um objeto responder a eventos de entrada?</span><span class="sxs-lookup"><span data-stu-id="73591-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="73591-112">Como adicionar comentários visuais?</span><span class="sxs-lookup"><span data-stu-id="73591-112">How to add visual feedback?</span></span>
- <span data-ttu-id="73591-113">Como adicionar comentários de áudio?</span><span class="sxs-lookup"><span data-stu-id="73591-113">How to add audio feedback?</span></span>
- <span data-ttu-id="73591-114">Como usar pré-fabricados do botão no estilo HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="73591-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="73591-115">Como fazer um objeto seguir você?</span><span class="sxs-lookup"><span data-stu-id="73591-115">How to make an object follow you?</span></span>
- <span data-ttu-id="73591-116">Como fazer um objeto olhar para você?</span><span class="sxs-lookup"><span data-stu-id="73591-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="73591-117">Este artigo foi atualizado para refletir as alterações na [versão do MRTK v2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span><span class="sxs-lookup"><span data-stu-id="73591-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="73591-118">Todo o conteúdo desta página pode ser testado no editor do Unity com a simulação de entrada do MRTK.</span><span class="sxs-lookup"><span data-stu-id="73591-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="73591-119">Caso ainda não tenha feito isso, siga o [Guia de Instalação do MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) para instalar a última versão do MRTK.</span><span class="sxs-lookup"><span data-stu-id="73591-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="73591-120">Como simular as interações de entrada no editor do Unity?</span><span class="sxs-lookup"><span data-stu-id="73591-120">How to simulate input interactions in Unity editor?</span></span>

<span data-ttu-id="73591-121">O MRTK é compatível com a simulação de entrada no editor.</span><span class="sxs-lookup"><span data-stu-id="73591-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="73591-122">Execute sua cena clicando no botão de reprodução do Unity e, em seguida, use as seguintes chaves para simular a entrada:</span><span class="sxs-lookup"><span data-stu-id="73591-122">Run your scene by clicking Unity's play button, then use the following keys to simulate input:</span></span>
- <span data-ttu-id="73591-123">Pressione as teclas W, A, S, D para mover a câmera.</span><span class="sxs-lookup"><span data-stu-id="73591-123">Press W, A, S, D keys to move the camera.</span></span>
- <span data-ttu-id="73591-124">Mantenha o botão direito do mouse pressionado e mova o mouse para examinar.</span><span class="sxs-lookup"><span data-stu-id="73591-124">Hold the right mouse button and move the mouse to look around.</span></span>
- <span data-ttu-id="73591-125">Pressione barra de espaço (à direita) ou tecla SHIFT esquerda para exibir as mãos simuladas</span><span class="sxs-lookup"><span data-stu-id="73591-125">Press Space bar(Right hand) or left Shift key(Left hand) to bring up the simulated hands</span></span>
- <span data-ttu-id="73591-126">Pressione as teclas T ou Y para manter as mãos simuladas no modo de exibição</span><span class="sxs-lookup"><span data-stu-id="73591-126">Press T or Y keys to keep simulated hands in view</span></span>
- <span data-ttu-id="73591-127">Pressione Q ou E (horizontal)/R ou F (vertical) para girar as mãos simuladas</span><span class="sxs-lookup"><span data-stu-id="73591-127">Press Q or E(horizontal) / R or F(vertical) to rotate simulated hands</span></span>

<span data-ttu-id="73591-128">Saiba mais sobre a Simulação de Entrada na [documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span><span class="sxs-lookup"><span data-stu-id="73591-128">You can learn more about Input Simulation in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span></span>

## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="73591-129">Como pegar e mover um objeto?</span><span class="sxs-lookup"><span data-stu-id="73591-129">How to grab and move an object?</span></span>

<span data-ttu-id="73591-130">Anexe os scripts **ObjectManipulator.cs** e **NearInteractionGrabbable.cs** para tornar um objeto capturável.</span><span class="sxs-lookup"><span data-stu-id="73591-130">Attach the **ObjectManipulator.cs** and **NearInteractionGrabbable.cs** scripts to make an object grabbable.</span></span> <span data-ttu-id="73591-131">ObjectManipulator é compatível com interações próxima e distante.</span><span class="sxs-lookup"><span data-stu-id="73591-131">ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="73591-132">Você pode pegar e mover um objeto com a entrada de acompanhamento de mão articulada do HoloLens 2 (próximo), raio da mão (distante), feixe do controlador de movimentos (distante), cursor de olhar do HoloLens e toque no ar (distante).</span><span class="sxs-lookup"><span data-stu-id="73591-132">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), and HoloLens gaze cursor and air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="73591-133">Como redimensionar um objeto?</span><span class="sxs-lookup"><span data-stu-id="73591-133">How to resize an object?</span></span>
<span data-ttu-id="73591-134">**ObjectManipulator.cs** dá suporte à escala/rotação de duas mãos.</span><span class="sxs-lookup"><span data-stu-id="73591-134">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="73591-135">O script funciona com vários tipos de entrada, como entrada de mão articulada do HoloLens 2, entrada de olhar + gesto do HoloLens 1 e entrada do controlador de movimentos do headset imersivo do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="73591-135">The script works with various input types, such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="73591-136">Saiba mais sobre o Object Manipulator na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="73591-136">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="73591-137">Como mover ou girar um objeto com precisão?</span><span class="sxs-lookup"><span data-stu-id="73591-137">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="73591-138">Atribua **BoundsControl.cs** a um objeto para usar a Caixa Delimitadora, que é a interface para dimensionar e girar um objeto.</span><span class="sxs-lookup"><span data-stu-id="73591-138">Assign **BoundsControl.cs** to an object to use Bounding Box, which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="73591-139">Por padrão, ele mostra as alças e os fios azuis no estilo HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="73591-139">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="73591-140">Para usar as alças animadas com base em proximidades no estilo HoloLens 2, você precisa atribuir pré-fabricados e materiais.</span><span class="sxs-lookup"><span data-stu-id="73591-140">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="73591-141">Saiba mais sobre o Controle de Limites na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="73591-141">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="73591-142">Como fazer um objeto responder a eventos de entrada?</span><span class="sxs-lookup"><span data-stu-id="73591-142">How to make an object respond to input events?</span></span>
<span data-ttu-id="73591-143">Atribua **PointerHandler.cs** a um objeto.</span><span class="sxs-lookup"><span data-stu-id="73591-143">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="73591-144">No inspetor, você pode usar os eventos OnPointerDown(), OnPointerUp(), OnPointerClicked() e OnPointerDragged(). Para usar esses eventos em um script, implemente **IMixedRealityPointerHandler**.</span><span class="sxs-lookup"><span data-stu-id="73591-144">In the inspector, you can use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="73591-145">Saiba mais sobre o Sistema de Entrada na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="73591-145">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="73591-146">Como adicionar comentários visuais?</span><span class="sxs-lookup"><span data-stu-id="73591-146">How to add visual feedback?</span></span>
<span data-ttu-id="73591-147">Atribua **Interactable.cs** a um objeto.</span><span class="sxs-lookup"><span data-stu-id="73591-147">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="73591-148">No inspetor, adicione um objeto de destino e crie um tema.</span><span class="sxs-lookup"><span data-stu-id="73591-148">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="73591-149">Usando perfis de tema de interação, você pode adicionar facilmente comentários visuais a todos os estados de interação de entrada disponíveis.</span><span class="sxs-lookup"><span data-stu-id="73591-149">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="73591-150">O item passível de interação fornece vários tipos de temas, incluindo o tema do sombreador, que permite controlar as propriedades do sombreador por estado de interação.</span><span class="sxs-lookup"><span data-stu-id="73591-150">Interactable provides various types of themes including the shader theme, which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="73591-151">Saiba mais sobre o item passível de interação na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="73591-151">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="73591-152">Outro bloco de construção importante para comentários visuais é o **Sombreador Padrão do MRTK**.</span><span class="sxs-lookup"><span data-stu-id="73591-152">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="73591-153">Com o sombreador Padrão MRTK, você pode adicionar facilmente efeitos de comentários visuais, como luz de foco e luz de proximidade.</span><span class="sxs-lookup"><span data-stu-id="73591-153">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="73591-154">Como o sombreador Padrão MRTK executa menos computação do que o sombreador Padrão Unity, você pode criar uma experiência de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="73591-154">Since MRTK Standard shader performs less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="73591-155">Crie um material e selecione o sombreador "Mixed Reality Toolkit > Padrão".</span><span class="sxs-lookup"><span data-stu-id="73591-155">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="73591-156">Ou você pode escolher um dos materiais existentes que usam o Sombreador Padrão MRTK.</span><span class="sxs-lookup"><span data-stu-id="73591-156">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="73591-157">Saiba mais sobre o Sombreador Padrão MRTK na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="73591-157">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="73591-158">Como adicionar comentários de áudio?</span><span class="sxs-lookup"><span data-stu-id="73591-158">How to add audio feedback?</span></span>
<span data-ttu-id="73591-159">Adicione **AudioSource** a um objeto.</span><span class="sxs-lookup"><span data-stu-id="73591-159">Add **AudioSource** to an object.</span></span> <span data-ttu-id="73591-160">Em seguida, nos scripts que expõem eventos de entrada (por exemplo, Interactable.cs ou PointerHandler.cs), atribua o objeto com AudioSource ao evento e selecione **AudioSource.PlayOneShot()** .</span><span class="sxs-lookup"><span data-stu-id="73591-160">Then, in the scripts that expose input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="73591-161">Você pode usar seus clipes de áudio ou escolher um dos ativos de áudio do MRTK.</span><span class="sxs-lookup"><span data-stu-id="73591-161">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="73591-162">Como usar pré-fabricados do botão no estilo HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="73591-162">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="73591-163">O MRTK fornece vários tipos de botões de estilo do shell (SO) do HoloLens 2, incluindo comentários visuais, como luz de proximidade, caixa de compactação e um efeito de ondulação na superfície do botão que aprimoram a confiança do usuário.</span><span class="sxs-lookup"><span data-stu-id="73591-163">MRTK provides various types of HoloLens 2's shell (OS) style buttons, including visual feedback like proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="73591-164">Arraste e solte um dos **pré-fabricados de botão pressionável de estilo HoloLens 2** na sua cena.</span><span class="sxs-lookup"><span data-stu-id="73591-164">Drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="73591-165">O pré-fabricado usa Interactable.cs, que é apresentado acima.</span><span class="sxs-lookup"><span data-stu-id="73591-165">The prefab uses Interactable.cs introduced above.</span></span> <span data-ttu-id="73591-166">Você pode usar eventos expostos, como OnClick(), em ações de gatilho de interação.</span><span class="sxs-lookup"><span data-stu-id="73591-166">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="73591-167">Saiba mais sobre os pré-fabricados de Botão na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="73591-167">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="73591-168">Como fazer um objeto seguir você?</span><span class="sxs-lookup"><span data-stu-id="73591-168">How to make an object follow you?</span></span>
<span data-ttu-id="73591-169">Atribua o script **RadialView.cs** ou **Follow.cs** a um objeto.</span><span class="sxs-lookup"><span data-stu-id="73591-169">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="73591-170">Ele faz parte da série de scripts do Solucionador que permite obter vários tipos de posicionamento de objeto no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="73591-170">It's part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="73591-171">O **SolverHandler.cs** será adicionado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="73591-171">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="73591-172">Veja abaixo um exemplo de configuração do RadialView para obter a marca "acompanhamento lento" ao longo do comportamento, assim como o menu Iniciar no shell do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="73591-172">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="73591-173">Você pode especificar a distância mínima/máxima e os graus de exibição mínimo/máximo.</span><span class="sxs-lookup"><span data-stu-id="73591-173">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="73591-174">O exemplo a seguir mostra o posicionamento do objeto entre o intervalo de 0,4 m e 0,8 m dentro de 15°.</span><span class="sxs-lookup"><span data-stu-id="73591-174">The example below shows positioning the object between 0.4 m and 0.8-m range within 15°.</span></span> <span data-ttu-id="73591-175">Ajuste os valores de Tempo de Lerp para tornar a atualização posicional mais rápida ou mais lenta.</span><span class="sxs-lookup"><span data-stu-id="73591-175">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="73591-176">Saiba mais sobre Solucionadores na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="73591-176">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="73591-177">Como fazer um objeto olhar para você?</span><span class="sxs-lookup"><span data-stu-id="73591-177">How to make an object face you?</span></span>
<span data-ttu-id="73591-178">Atribua o script **Billboard.cs** a um objeto.</span><span class="sxs-lookup"><span data-stu-id="73591-178">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="73591-179">Ele sempre fica de frente para você, independentemente da sua posição.</span><span class="sxs-lookup"><span data-stu-id="73591-179">It will always face you, whatever your position.</span></span> <span data-ttu-id="73591-180">Você pode especificar a opção de eixo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="73591-180">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="73591-181">Pronto para criar experiências incríveis para realidade misturada?</span><span class="sxs-lookup"><span data-stu-id="73591-181">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="73591-182">Visite as páginas abaixo e saiba mais sobre MRTK e realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="73591-182">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="73591-183">Sobre o autor</span><span class="sxs-lookup"><span data-stu-id="73591-183">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="73591-184"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="73591-184"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="73591-185">Designer de UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="73591-185">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="73591-186">Confira também</span><span class="sxs-lookup"><span data-stu-id="73591-186">See also</span></span>
* [<span data-ttu-id="73591-187">Guia de Instalação do MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="73591-187">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="73591-188">Mixed Reality Toolkit-Unity (MRTK) – GitHub</span><span class="sxs-lookup"><span data-stu-id="73591-188">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="73591-189">Portal de documentação do MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="73591-189">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="73591-190">Diretrizes de portabilidade do HoloToolkit para o MRTK</span><span class="sxs-lookup"><span data-stu-id="73591-190">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
