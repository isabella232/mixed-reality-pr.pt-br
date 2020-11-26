---
title: MRTK 101 – Como usar o Kit de Ferramentas de Realidade Misturada do Unity para interações espaciais comuns (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
description: Como usar a o Mixed Reality Toolkit Unity para interações básicas (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada, Windows Mixed Reality, design, aplicativo de exemplo, controles, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.localizationpriority: high
ms.openlocfilehash: 95d8f8c52b226eda7ea1601feffc1464c2ea91c5
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677526"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="b787f-104">MRTK 101: Como usar o Kit de Ferramentas de Realidade Misturada do Unity para interações espaciais</span><span class="sxs-lookup"><span data-stu-id="b787f-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>
![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="b787f-106">Saiba mais sobre como usar o MRTK para obter alguns dos padrões comuns de interação mais amplamente usados em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="b787f-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="b787f-107">Como simular as interações de entrada no editor do Unity?</span><span class="sxs-lookup"><span data-stu-id="b787f-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="b787f-108">Como pegar e mover um objeto?</span><span class="sxs-lookup"><span data-stu-id="b787f-108">How to grab and move an object?</span></span>
- <span data-ttu-id="b787f-109">Como redimensionar um objeto?</span><span class="sxs-lookup"><span data-stu-id="b787f-109">How to resize an object?</span></span>
- <span data-ttu-id="b787f-110">Como mover ou girar um objeto com precisão?</span><span class="sxs-lookup"><span data-stu-id="b787f-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="b787f-111">Como fazer um objeto responder a eventos de entrada?</span><span class="sxs-lookup"><span data-stu-id="b787f-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="b787f-112">Como adicionar comentários visuais?</span><span class="sxs-lookup"><span data-stu-id="b787f-112">How to add visual feedback?</span></span>
- <span data-ttu-id="b787f-113">Como adicionar comentários de áudio?</span><span class="sxs-lookup"><span data-stu-id="b787f-113">How to add audio feedback?</span></span>
- <span data-ttu-id="b787f-114">Como usar pré-fabricados do botão no estilo HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="b787f-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="b787f-115">Como fazer um objeto seguir você?</span><span class="sxs-lookup"><span data-stu-id="b787f-115">How to make an object follow you?</span></span>
- <span data-ttu-id="b787f-116">Como fazer um objeto olhar para você?</span><span class="sxs-lookup"><span data-stu-id="b787f-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="b787f-117">Este artigo foi atualizado para refletir as alterações na [versão do MRTK v2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span><span class="sxs-lookup"><span data-stu-id="b787f-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="b787f-118">Todo o conteúdo desta página pode ser testado no editor do Unity com a simulação de entrada do MRTK.</span><span class="sxs-lookup"><span data-stu-id="b787f-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="b787f-119">Caso ainda não tenha feito isso, siga o [Guia de Instalação do MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) para instalar a última versão do MRTK.</span><span class="sxs-lookup"><span data-stu-id="b787f-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="b787f-120">Como simular as interações de entrada no editor do Unity?</span><span class="sxs-lookup"><span data-stu-id="b787f-120">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="b787f-121">O MRTK é compatível com a simulação de entrada no editor.</span><span class="sxs-lookup"><span data-stu-id="b787f-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="b787f-122">Basta executar sua cena clicando no botão reproduzir do Unity.</span><span class="sxs-lookup"><span data-stu-id="b787f-122">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="b787f-123">Use essas chaves para simular a entrada.</span><span class="sxs-lookup"><span data-stu-id="b787f-123">Use these keys to simulate input.</span></span>
<span data-ttu-id="b787f-124">Pressione as teclas W, A, S, D para mover a câmera.</span><span class="sxs-lookup"><span data-stu-id="b787f-124">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="b787f-125">Mantenha o botão direito do mouse pressionado e mova o mouse para examinar.</span><span class="sxs-lookup"><span data-stu-id="b787f-125">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="b787f-126">Para exibir as mãos simuladas, pressione a barra de Espaço (à direita) ou a tecla Shift esquerda (à esquerda) para manter as mãos simuladas na exibição, pressione a tecla T ou Y para girar as mãos simuladas, pressione Q ou E (horizontal)/R ou F (vertical)</span><span class="sxs-lookup"><span data-stu-id="b787f-126">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="b787f-127">Saiba mais sobre a Simulação de Entrada na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="b787f-127">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="b787f-128">Como pegar e mover um objeto?</span><span class="sxs-lookup"><span data-stu-id="b787f-128">How to grab and move an object?</span></span>
<span data-ttu-id="b787f-129">Para tornar um objeto captável, atribua estes dois scripts: **ObjectManipulator.cs** e **NearInteractionGrabbable.cs** (para captura direta com entrada de acompanhamento de mão articulada): ObjectManipulator dá suporte a interações próximas e distantes.</span><span class="sxs-lookup"><span data-stu-id="b787f-129">To make an object grabbable, assign these two scripts: **ObjectManipulator.cs** and **NearInteractionGrabbable.cs**(for direct grab with articulated hand tracking input) ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="b787f-130">Você pode pegar e mover um objeto com a entrada de acompanhamento de mão articulada do HoloLens 2 (próximo), raio da mão (distante), feixe do controlador de movimento (distante), cursor de olhar do HoloLens e toque no ar (distante).</span><span class="sxs-lookup"><span data-stu-id="b787f-130">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="b787f-131">Como redimensionar um objeto?</span><span class="sxs-lookup"><span data-stu-id="b787f-131">How to resize an object?</span></span>
<span data-ttu-id="b787f-132">**ObjectManipulator.cs** dá suporte à escala/rotação de duas mãos.</span><span class="sxs-lookup"><span data-stu-id="b787f-132">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="b787f-133">Isso funciona com vários tipos de entrada, como entrada de mão articulada do HoloLens 2, entrada de olhar + gesto do HoloLens 1 e entrada do controlador de movimento do headset imersivo do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b787f-133">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="b787f-134">Saiba mais sobre o Object Manipulator na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="b787f-134">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="b787f-135">Como mover ou girar um objeto com precisão?</span><span class="sxs-lookup"><span data-stu-id="b787f-135">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="b787f-136">Atribua **BoundsControl.cs** a um objeto para usar a Caixa Delimitadora que é a interface para dimensionar e girar um objeto.</span><span class="sxs-lookup"><span data-stu-id="b787f-136">Assign **BoundsControl.cs** to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="b787f-137">Por padrão, ele mostra as alças e os fios azuis no estilo HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="b787f-137">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="b787f-138">Para usar as alças animadas com base em proximidades no estilo HoloLens 2, você precisa atribuir pré-fabricados e materiais.</span><span class="sxs-lookup"><span data-stu-id="b787f-138">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="b787f-139">Saiba mais sobre o Controle de Limites na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="b787f-139">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="b787f-140">Como fazer um objeto responder a eventos de entrada?</span><span class="sxs-lookup"><span data-stu-id="b787f-140">How to make an object respond to input events?</span></span>
<span data-ttu-id="b787f-141">Atribua **PointerHandler.cs** a um objeto.</span><span class="sxs-lookup"><span data-stu-id="b787f-141">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="b787f-142">No inspetor, você poderá usar os eventos OnPointerDown(), OnPointerUp(), OnPointerClicked() e OnPointerDragged(). Para usar esses eventos em um script, implemente **IMixedRealityPointerHandler**.</span><span class="sxs-lookup"><span data-stu-id="b787f-142">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="b787f-143">Saiba mais sobre o Sistema de Entrada na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="b787f-143">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="b787f-144">Como adicionar comentários visuais?</span><span class="sxs-lookup"><span data-stu-id="b787f-144">How to add visual feedback?</span></span>
<span data-ttu-id="b787f-145">Atribua **Interactable.cs** a um objeto.</span><span class="sxs-lookup"><span data-stu-id="b787f-145">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="b787f-146">No inspetor, adicione um objeto de destino e crie um tema.</span><span class="sxs-lookup"><span data-stu-id="b787f-146">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="b787f-147">Usando perfis de tema de interação, você pode adicionar facilmente comentários visuais a todos os estados de interação de entrada disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b787f-147">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="b787f-148">O item passível de interação fornece vários tipos de temas, incluindo o tema do sombreador, que permite controlar as propriedades do sombreador por estado de interação.</span><span class="sxs-lookup"><span data-stu-id="b787f-148">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="b787f-149">Saiba mais sobre o item passível de interação na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="b787f-149">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="b787f-150">Outro bloco de construção importante para comentários visuais é o **Sombreador Padrão do MRTK**.</span><span class="sxs-lookup"><span data-stu-id="b787f-150">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="b787f-151">Com o sombreador Padrão MRTK, você pode adicionar facilmente efeitos de comentários visuais, como luz de foco e luz de proximidade.</span><span class="sxs-lookup"><span data-stu-id="b787f-151">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="b787f-152">Como o sombreador Padrão MRTK executa significativamente menos cálculos do que o sombreador Padrão Unity, você pode criar uma experiência de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="b787f-152">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="b787f-153">Crie um material e selecione o sombreador "Mixed Reality Toolkit > Padrão".</span><span class="sxs-lookup"><span data-stu-id="b787f-153">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="b787f-154">Ou você pode escolher um dos materiais existentes que usam o Sombreador Padrão MRTK.</span><span class="sxs-lookup"><span data-stu-id="b787f-154">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="b787f-155">Saiba mais sobre o Sombreador Padrão MRTK na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="b787f-155">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="b787f-156">Como adicionar comentários de áudio?</span><span class="sxs-lookup"><span data-stu-id="b787f-156">How to add audio feedback?</span></span>
<span data-ttu-id="b787f-157">Adicione **AudioSource** a um objeto.</span><span class="sxs-lookup"><span data-stu-id="b787f-157">Add **AudioSource** to an object.</span></span> <span data-ttu-id="b787f-158">Em seguida, nos scripts que expõem eventos de entrada (por exemplo, Interactable.cs ou PointerHandler.cs), atribua o objeto com AudioSource ao evento e selecione **AudioSource.PlayOneShot()** .</span><span class="sxs-lookup"><span data-stu-id="b787f-158">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="b787f-159">Você pode usar seus clipes de áudio ou escolher um dos ativos de áudio do MRTK.</span><span class="sxs-lookup"><span data-stu-id="b787f-159">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="b787f-160">Como usar pré-fabricados do botão no estilo HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="b787f-160">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="b787f-161">O MRTK fornece vários tipos de botões no estilo shell (sistema operacional) do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b787f-161">MRTK provides various types of HoloLens 2's shell (OS) style buttons.</span></span> <span data-ttu-id="b787f-162">Ele fornece comentários visuais sofisticados, como luz de proximidade, caixa de compactação e um efeito de ondulação na superfície do botão para aprimorar a confiança do usuário.</span><span class="sxs-lookup"><span data-stu-id="b787f-162">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="b787f-163">Basta arrastar e soltar um dos **pré-fabricados de botão pressionável de estilo HoloLens 2** na sua cena.</span><span class="sxs-lookup"><span data-stu-id="b787f-163">Simply drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="b787f-164">O pré-fabricado usa Interactable.cs, que é apresentado acima.</span><span class="sxs-lookup"><span data-stu-id="b787f-164">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="b787f-165">Você pode usar eventos expostos, como OnClick(), em ações de gatilho de interação.</span><span class="sxs-lookup"><span data-stu-id="b787f-165">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="b787f-166">Saiba mais sobre os pré-fabricados de Botão na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="b787f-166">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="b787f-167">Como fazer um objeto seguir você?</span><span class="sxs-lookup"><span data-stu-id="b787f-167">How to make an object follow you?</span></span>
<span data-ttu-id="b787f-168">Atribua o script **RadialView.cs** ou **Follow.cs** a um objeto.</span><span class="sxs-lookup"><span data-stu-id="b787f-168">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="b787f-169">Ele faz parte da série de scripts do Solucionador que permite alcançar vários tipos de posicionamento de objeto no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="b787f-169">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="b787f-170">O **SolverHandler.cs** será adicionado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b787f-170">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="b787f-171">Veja abaixo um exemplo de configuração do RadialView para obter a marca "acompanhamento lento" ao longo do comportamento, assim como o menu Iniciar no shell do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b787f-171">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="b787f-172">Você pode especificar a distância mínima/máxima e os graus de exibição mínimo/máximo.</span><span class="sxs-lookup"><span data-stu-id="b787f-172">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="b787f-173">O exemplo a seguir mostra o posicionamento do objeto entre o intervalo de 0,4 m e 0,8 m dentro de 15°.</span><span class="sxs-lookup"><span data-stu-id="b787f-173">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="b787f-174">Ajuste os valores de Tempo de Lerp para tornar a atualização posicional mais rápida ou mais lenta.</span><span class="sxs-lookup"><span data-stu-id="b787f-174">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="b787f-175">Saiba mais sobre Solucionadores na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="b787f-175">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="b787f-176">Como fazer um objeto olhar para você?</span><span class="sxs-lookup"><span data-stu-id="b787f-176">How to make an object face you?</span></span>
<span data-ttu-id="b787f-177">Atribua o script **Billboard.cs** a um objeto.</span><span class="sxs-lookup"><span data-stu-id="b787f-177">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="b787f-178">Ele sempre vai olhar para você, independentemente da sua posição.</span><span class="sxs-lookup"><span data-stu-id="b787f-178">It will always face you, regardless of your position.</span></span> <span data-ttu-id="b787f-179">Você pode especificar a opção de eixo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="b787f-179">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="b787f-180">Pronto para criar experiências incríveis para realidade misturada?</span><span class="sxs-lookup"><span data-stu-id="b787f-180">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="b787f-181">Visite as páginas abaixo e saiba mais sobre MRTK e realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="b787f-181">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="b787f-182">Sobre o autor</span><span class="sxs-lookup"><span data-stu-id="b787f-182">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="b787f-183"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="b787f-183"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="b787f-184">Designer de UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="b787f-184">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b787f-185">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="b787f-185">Next Development Checkpoint</span></span>

<span data-ttu-id="b787f-186">Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unity, você está no meio da exploração dos principais blocos de construção do MRTK.</span><span class="sxs-lookup"><span data-stu-id="b787f-186">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="b787f-187">De lá, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="b787f-187">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="b787f-188">Câmera</span><span class="sxs-lookup"><span data-stu-id="b787f-188">Camera</span></span>](camera-in-unity.md)

<span data-ttu-id="b787f-189">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="b787f-189">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b787f-190">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="b787f-190">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="b787f-191">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="b787f-191">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b787f-192">Confira também</span><span class="sxs-lookup"><span data-stu-id="b787f-192">See also</span></span>
* [<span data-ttu-id="b787f-193">Guia de Instalação do MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="b787f-193">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="b787f-194">Mixed Reality Toolkit-Unity (MRTK) – GitHub</span><span class="sxs-lookup"><span data-stu-id="b787f-194">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="b787f-195">Portal de documentação do MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="b787f-195">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="b787f-196">Diretrizes de portabilidade do HoloToolkit para o MRTK</span><span class="sxs-lookup"><span data-stu-id="b787f-196">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
