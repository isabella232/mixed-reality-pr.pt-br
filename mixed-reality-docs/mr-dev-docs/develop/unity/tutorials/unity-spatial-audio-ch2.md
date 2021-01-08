---
title: Espacializar sons de interação de botão
description: Saiba como adicionar um botão e espacialar os sons de interação do botão em um aplicativo de realidade misturada.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer, pré-fabricados, curva de volume
ms.openlocfilehash: 1f54ba8cab55ba375a6b1499796761ae02b03a02
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007356"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="01ec8-104">Espacializar sons de interação de botão</span><span class="sxs-lookup"><span data-stu-id="01ec8-104">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="01ec8-105">Objetivos</span><span class="sxs-lookup"><span data-stu-id="01ec8-105">Objectives</span></span>

<span data-ttu-id="01ec8-106">Neste segundo capítulo do módulo de áudio espacial dos tutoriais do HoloLens 2, você irá:</span><span class="sxs-lookup"><span data-stu-id="01ec8-106">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="01ec8-107">Adicionar um botão</span><span class="sxs-lookup"><span data-stu-id="01ec8-107">Add a button</span></span>
* <span data-ttu-id="01ec8-108">Espaciale o botão clique em sons</span><span class="sxs-lookup"><span data-stu-id="01ec8-108">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="01ec8-109">Adicionar um botão</span><span class="sxs-lookup"><span data-stu-id="01ec8-109">Add a button</span></span>

<span data-ttu-id="01ec8-110">No painel **projeto** , selecione **ativos** e digite "PressableButtonHoloLens2" na barra de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="01ec8-110">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![Botão pré-fabricado em ativos](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="01ec8-112">O botão pré-fabricado é a entrada representada por um ícone azul, em vez de um ícone branco.</span><span class="sxs-lookup"><span data-stu-id="01ec8-112">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="01ec8-113">Arraste o pré-fabricado chamado **PressableButtonHoloLens2** para o painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="01ec8-113">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="01ec8-114">No painel **Inspetor** do botão novo, defina a propriedade **Position** como (0,-0,4, 2) para que ela apareça na frente do usuário quando o aplicativo for iniciado.</span><span class="sxs-lookup"><span data-stu-id="01ec8-114">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="01ec8-115">O componente de **transformação** do botão terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="01ec8-115">The **Transform** component of the button will look like this:</span></span>

![Transformação de botão](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="01ec8-117">Comentar o botão espacial</span><span class="sxs-lookup"><span data-stu-id="01ec8-117">Spatialize button feedback</span></span>

<span data-ttu-id="01ec8-118">Nesta etapa, você causará a espacial dos comentários de áudio para o botão.</span><span class="sxs-lookup"><span data-stu-id="01ec8-118">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="01ec8-119">Para obter sugestões de design relacionadas, consulte [design de som espacial](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="01ec8-119">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span> 

<span data-ttu-id="01ec8-120">O painel **mixer de áudio** é onde você definirá destinos, chamados de grupos de **mixers**, para reprodução de áudio de componentes de **fonte de áudio** .</span><span class="sxs-lookup"><span data-stu-id="01ec8-120">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="01ec8-121">Abra o painel **mixer de áudio** na barra de menus usando o mixer de áudio do > de **áudio > do Windows**</span><span class="sxs-lookup"><span data-stu-id="01ec8-121">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="01ec8-122">Crie um **mixer** clicando no sinal de ' + ' ao lado dos **mixers**.</span><span class="sxs-lookup"><span data-stu-id="01ec8-122">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="01ec8-123">O novo mixer incluirá um **grupo** padrão chamado **Master**.</span><span class="sxs-lookup"><span data-stu-id="01ec8-123">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="01ec8-124">O painel do **mixer** agora terá esta aparência:</span><span class="sxs-lookup"><span data-stu-id="01ec8-124">Your **Mixer** pane will now look like this:</span></span>

![Painel do mixer com o primeiro mixer](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="01ec8-126">Até que o verbo de reverberação esteja habilitado no [capítulo 5](unity-spatial-audio-ch5.md), o medidor de volume do mixer não mostra a atividade de sons reproduzidos por meio do Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="01ec8-126">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="01ec8-127">Clique no **PressableButtonHoloLens2** no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="01ec8-127">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="01ec8-128">No painel **Inspetor** :</span><span class="sxs-lookup"><span data-stu-id="01ec8-128">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="01ec8-129">Localizar o componente **fonte de áudio**</span><span class="sxs-lookup"><span data-stu-id="01ec8-129">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="01ec8-130">Para a propriedade **saída** , clique no seletor e escolha seu mixer</span><span class="sxs-lookup"><span data-stu-id="01ec8-130">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="01ec8-131">Marque a caixa de seleção **espacialize**</span><span class="sxs-lookup"><span data-stu-id="01ec8-131">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="01ec8-132">Mova o controle deslizante de **mistura espacial** para 3D (1).</span><span class="sxs-lookup"><span data-stu-id="01ec8-132">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="01ec8-133">Em versões do Unity anteriores a 2019, a caixa de seleção ' Espacialize ' está na parte inferior do painel do **Inspetor** para a **fonte de áudio**.</span><span class="sxs-lookup"><span data-stu-id="01ec8-133">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="01ec8-134">Após essas alterações, o componente **fonte de áudio** de seu **PressableButtonHoloLens2** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="01ec8-134">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![Fonte de áudio do botão](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="01ec8-136">Se você mover a **mistura espacial** para 1 (3D) sem marcar a caixa de seleção **espacialize** , o Unity usará seu spatializer panorâmico, em vez do **Microsoft spatializer** com HRTFs.</span><span class="sxs-lookup"><span data-stu-id="01ec8-136">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="01ec8-137">Ajustar a curva de volume</span><span class="sxs-lookup"><span data-stu-id="01ec8-137">Adjust the Volume curve</span></span>

<span data-ttu-id="01ec8-138">Por padrão, o Unity atenua os sons espaciais à medida que eles ficam mais distantes do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="01ec8-138">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="01ec8-139">Quando essa atenuação é aplicada aos sons de comentários de interação, a interface pode ser mais difícil de usar.</span><span class="sxs-lookup"><span data-stu-id="01ec8-139">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="01ec8-140">Para desabilitar essa atenuação, ajuste a curva de **volume** .</span><span class="sxs-lookup"><span data-stu-id="01ec8-140">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="01ec8-141">No componente **fonte de áudio** do painel **Inspetor** para o **PressableButtonHoloLens2**, há uma seção chamada configurações de **som 3D**.</span><span class="sxs-lookup"><span data-stu-id="01ec8-141">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="01ec8-142">Nesta seção:</span><span class="sxs-lookup"><span data-stu-id="01ec8-142">In that section:</span></span>
1. <span data-ttu-id="01ec8-143">Definir a propriedade **rolloff do volume** como linear</span><span class="sxs-lookup"><span data-stu-id="01ec8-143">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="01ec8-144">Arraste o ponto de extremidade na curva de **volume** (a curva vermelha) de ' 0 ' no eixo y até ' 1 '</span><span class="sxs-lookup"><span data-stu-id="01ec8-144">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="01ec8-145">Para ajustar a forma da curva de **volume** para ser simples, arraste o controle forma de curva de branco para ser paralelo ao eixo X</span><span class="sxs-lookup"><span data-stu-id="01ec8-145">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="01ec8-146">Após essas alterações, a seção **configurações de som 3D** das propriedades da **fonte de áudio** do **PressableButtonHoloLens2** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="01ec8-146">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![Configurações de som 3D do botão](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="01ec8-148">Testando o áudio espacial</span><span class="sxs-lookup"><span data-stu-id="01ec8-148">Testing the spatialize audio</span></span>

<span data-ttu-id="01ec8-149">Sinta-se à vontade para testar os novos sons de interação de botão espacial:</span><span class="sxs-lookup"><span data-stu-id="01ec8-149">Feel free to test out the new spatialized button interaction sounds:</span></span>

* <span data-ttu-id="01ec8-150">Insira o modo de jogo no editor do Unity, idealmente com um exemplo de áudio em loop na cena</span><span class="sxs-lookup"><span data-stu-id="01ec8-150">Enter game mode in the Unity editor, ideally with a looped audio sample in the scene</span></span>
* <span data-ttu-id="01ec8-151">Mova o objeto com a fonte de áudio da esquerda para a direita e compare com e sem o áudio espacial habilitado.</span><span class="sxs-lookup"><span data-stu-id="01ec8-151">Move the object with the audio source from left to right and compare with and without spatial audio enabled.</span></span> <span data-ttu-id="01ec8-152">Você pode alterar as configurações de fonte de áudio para teste:</span><span class="sxs-lookup"><span data-stu-id="01ec8-152">You can change the Audio Source settings for testing by:</span></span>
    * <span data-ttu-id="01ec8-153">Movendo a propriedade de mistura espacial entre 0-1 (2D sem espacial e um som espacial 3D)</span><span class="sxs-lookup"><span data-stu-id="01ec8-153">Moving the Spatial Blend property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
    * <span data-ttu-id="01ec8-154">Verificando e desmarcando a propriedade Espacialize</span><span class="sxs-lookup"><span data-stu-id="01ec8-154">Checking and unchecking the Spatialize property</span></span>

## <a name="next-steps"></a><span data-ttu-id="01ec8-155">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="01ec8-155">Next steps</span></span>

<span data-ttu-id="01ec8-156">Experimente seu aplicativo em um HoloLens 2 ou no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="01ec8-156">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="01ec8-157">No aplicativo, você pode tocar no botão e ouvir os sons de interação do botão espacial.</span><span class="sxs-lookup"><span data-stu-id="01ec8-157">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="01ec8-158">Ao testar no editor do Unity, pressione a barra de espaço e role com a roda de rolagem para ativar a simulação de mão.</span><span class="sxs-lookup"><span data-stu-id="01ec8-158">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="01ec8-159">Para obter mais informações, consulte a [documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span><span class="sxs-lookup"><span data-stu-id="01ec8-159">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="01ec8-160">Capítulo 3</span><span class="sxs-lookup"><span data-stu-id="01ec8-160">Chapter 3</span></span>](unity-spatial-audio-ch3.md)

