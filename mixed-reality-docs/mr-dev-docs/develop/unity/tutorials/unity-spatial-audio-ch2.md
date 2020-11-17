---
title: Tutoriais de áudio espacial-2. Espacializar sons de interação de botão
description: Adicione um botão ao seu projeto e espaciale os sons de interação do botão.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer, pré-fabricados, curva de volume
ms.openlocfilehash: eb550c3127e13926d73428b337abfd7cf9872eb7
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678185"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="2e1fd-105">Espacializar sons de interação de botão</span><span class="sxs-lookup"><span data-stu-id="2e1fd-105">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="2e1fd-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2e1fd-106">Objectives</span></span>
<span data-ttu-id="2e1fd-107">Neste segundo capítulo do módulo de áudio espacial dos tutoriais do HoloLens 2, você irá:</span><span class="sxs-lookup"><span data-stu-id="2e1fd-107">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="2e1fd-108">Adicionar um botão</span><span class="sxs-lookup"><span data-stu-id="2e1fd-108">Add a button</span></span>
* <span data-ttu-id="2e1fd-109">Espaciale o botão clique em sons</span><span class="sxs-lookup"><span data-stu-id="2e1fd-109">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="2e1fd-110">Adicionar um botão</span><span class="sxs-lookup"><span data-stu-id="2e1fd-110">Add a button</span></span>
<span data-ttu-id="2e1fd-111">No painel **projeto** , selecione **ativos** e digite "PressableButtonHoloLens2" na barra de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="2e1fd-111">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![Botão pré-fabricado em ativos](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="2e1fd-113">O botão pré-fabricado é a entrada representada por um ícone azul, em vez de um ícone branco.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-113">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="2e1fd-114">Arraste o pré-fabricado chamado **PressableButtonHoloLens2** para o painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="2e1fd-114">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="2e1fd-115">No painel **Inspetor** do botão novo, defina a propriedade **Position** como (0,-0,4, 2) para que ela apareça na frente do usuário quando o aplicativo for iniciado.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-115">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="2e1fd-116">O componente de **transformação** do botão terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="2e1fd-116">The **Transform** component of the button will look like this:</span></span>

![Transformação de botão](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="2e1fd-118">Comentar o botão espacial</span><span class="sxs-lookup"><span data-stu-id="2e1fd-118">Spatialize button feedback</span></span>
<span data-ttu-id="2e1fd-119">Nesta etapa, você causará a espacial dos comentários de áudio para o botão.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-119">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="2e1fd-120">Para obter sugestões de design relacionadas, consulte [design de som espacial](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="2e1fd-120">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span> 

<span data-ttu-id="2e1fd-121">O painel **mixer de áudio** é onde você definirá destinos, chamados de grupos de **mixers**, para reprodução de áudio de componentes de **fonte de áudio** .</span><span class="sxs-lookup"><span data-stu-id="2e1fd-121">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="2e1fd-122">Abra o painel **mixer de áudio** na barra de menus usando o mixer de áudio do > de **áudio > do Windows**</span><span class="sxs-lookup"><span data-stu-id="2e1fd-122">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="2e1fd-123">Crie um **mixer** clicando no sinal de ' + ' ao lado dos **mixers**.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-123">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="2e1fd-124">O novo mixer incluirá um **grupo** padrão chamado **Master**.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-124">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="2e1fd-125">O painel do **mixer** agora terá esta aparência:</span><span class="sxs-lookup"><span data-stu-id="2e1fd-125">Your **Mixer** pane will now look like this:</span></span>

![Painel do mixer com o primeiro mixer](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="2e1fd-127">Até que o verbo de reverberação esteja habilitado no [capítulo 5](unity-spatial-audio-ch5.md), o medidor de volume do mixer não mostra a atividade de sons reproduzidos por meio do Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="2e1fd-127">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="2e1fd-128">Clique no **PressableButtonHoloLens2** no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="2e1fd-128">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="2e1fd-129">No painel **Inspetor** :</span><span class="sxs-lookup"><span data-stu-id="2e1fd-129">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="2e1fd-130">Localizar o componente **fonte de áudio**</span><span class="sxs-lookup"><span data-stu-id="2e1fd-130">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="2e1fd-131">Para a propriedade **saída** , clique no seletor e escolha seu mixer</span><span class="sxs-lookup"><span data-stu-id="2e1fd-131">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="2e1fd-132">Marque a caixa de seleção **espacialize**</span><span class="sxs-lookup"><span data-stu-id="2e1fd-132">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="2e1fd-133">Mova o controle deslizante de **mistura espacial** para 3D (1).</span><span class="sxs-lookup"><span data-stu-id="2e1fd-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="2e1fd-134">Em versões do Unity anteriores a 2019, a caixa de seleção ' Espacialize ' está na parte inferior do painel do **Inspetor** para a **fonte de áudio**.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-134">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="2e1fd-135">Após essas alterações, o componente **fonte de áudio** de seu **PressableButtonHoloLens2** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="2e1fd-135">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![Fonte de áudio do botão](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="2e1fd-137">Se você mover a **mistura espacial** para 1 (3D) sem marcar a caixa de seleção **espacialize** , o Unity usará seu spatializer panorâmico, em vez do **Microsoft spatializer** com HRTFs.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-137">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="2e1fd-138">Ajustar a curva de volume</span><span class="sxs-lookup"><span data-stu-id="2e1fd-138">Adjust the Volume curve</span></span>
<span data-ttu-id="2e1fd-139">Por padrão, o Unity atenua os sons espaciais à medida que eles ficam mais distantes do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-139">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="2e1fd-140">Quando essa atenuação é aplicada aos sons de comentários de interação, a interface pode ser mais difícil de usar.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-140">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="2e1fd-141">Para desabilitar essa atenuação, ajuste a curva de **volume** .</span><span class="sxs-lookup"><span data-stu-id="2e1fd-141">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="2e1fd-142">No componente **fonte de áudio** do painel **Inspetor** para o **PressableButtonHoloLens2**, há uma seção chamada configurações de **som 3D**.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-142">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="2e1fd-143">Nesta seção:</span><span class="sxs-lookup"><span data-stu-id="2e1fd-143">In that section:</span></span>
1. <span data-ttu-id="2e1fd-144">Definir a propriedade **rolloff do volume** como linear</span><span class="sxs-lookup"><span data-stu-id="2e1fd-144">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="2e1fd-145">Arraste o ponto de extremidade na curva de **volume** (a curva vermelha) de ' 0 ' no eixo y até ' 1 '</span><span class="sxs-lookup"><span data-stu-id="2e1fd-145">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="2e1fd-146">Para ajustar a forma da curva de **volume** para ser simples, arraste o controle forma de curva de branco para ser paralelo ao eixo X</span><span class="sxs-lookup"><span data-stu-id="2e1fd-146">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="2e1fd-147">Após essas alterações, a seção **configurações de som 3D** das propriedades da **fonte de áudio** do **PressableButtonHoloLens2** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="2e1fd-147">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![Configurações de som 3D do botão](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="2e1fd-149">Testando o áudio espacial</span><span class="sxs-lookup"><span data-stu-id="2e1fd-149">Testing the spatialize audio</span></span>

<span data-ttu-id="2e1fd-150">Sinta-se à vontade para testar os novos sons de interação de botão espacial:</span><span class="sxs-lookup"><span data-stu-id="2e1fd-150">Feel free to test out the new spatialized button interaction sounds:</span></span>

* <span data-ttu-id="2e1fd-151">Insira o modo de jogo no editor do Unity, idealmente com um exemplo de áudio em loop na cena</span><span class="sxs-lookup"><span data-stu-id="2e1fd-151">Enter game mode in the Unity editor, ideally with a looped audio sample in the scene</span></span>
* <span data-ttu-id="2e1fd-152">Mova o objeto com a fonte de áudio da esquerda para a direita e compare com e sem o áudio espacial habilitado.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-152">Move the object with the audio source from left to right and compare with and without spatial audio enabled.</span></span> <span data-ttu-id="2e1fd-153">Você pode alterar as configurações de fonte de áudio para teste:</span><span class="sxs-lookup"><span data-stu-id="2e1fd-153">You can change the Audio Source settings for testing by:</span></span>
    * <span data-ttu-id="2e1fd-154">Movendo a propriedade de mistura espacial entre 0-1 (2D sem espacial e um som espacial 3D)</span><span class="sxs-lookup"><span data-stu-id="2e1fd-154">Moving the Spatial Blend property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
    * <span data-ttu-id="2e1fd-155">Verificando e desmarcando a propriedade Espacialize</span><span class="sxs-lookup"><span data-stu-id="2e1fd-155">Checking and unchecking the Spatialize property</span></span>

## <a name="next-steps"></a><span data-ttu-id="2e1fd-156">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2e1fd-156">Next steps</span></span>

<span data-ttu-id="2e1fd-157">Experimente seu aplicativo em um HoloLens 2 ou no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-157">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="2e1fd-158">No aplicativo, você pode tocar no botão e ouvir os sons de interação do botão espacial.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-158">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="2e1fd-159">Ao testar no editor do Unity, pressione a barra de espaço e role com a roda de rolagem para ativar a simulação de mão.</span><span class="sxs-lookup"><span data-stu-id="2e1fd-159">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="2e1fd-160">Para obter mais informações, consulte a [documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span><span class="sxs-lookup"><span data-stu-id="2e1fd-160">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e1fd-161">Capítulo 3</span><span class="sxs-lookup"><span data-stu-id="2e1fd-161">Chapter 3</span></span>](unity-spatial-audio-ch3.md)

