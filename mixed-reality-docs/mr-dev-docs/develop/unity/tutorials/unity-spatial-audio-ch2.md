---
title: Tutoriais de áudio espacial-2. Espacializar sons de interação de botão
description: Adicione um botão ao seu projeto e espaciale os sons de interação do botão.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer, pré-fabricados, curva de volume
ms.openlocfilehash: e4b2ed99f56fea82b1c72e4fce5205c14e1d3533
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578465"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="abbe4-105">2. Espacializar sons de interação de botão</span><span class="sxs-lookup"><span data-stu-id="abbe4-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="abbe4-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="abbe4-106">Overview</span></span>

<span data-ttu-id="abbe4-107">Neste tutorial, você aprenderá a gerar os sons de interação do botão e também aprenderá a usar um clipe de áudio para testar a interação do botão espacialed.</span><span class="sxs-lookup"><span data-stu-id="abbe4-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="abbe4-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="abbe4-108">Objectives</span></span>

* <span data-ttu-id="abbe4-109">Adicionar e Espacialar o botão clique em sons</span><span class="sxs-lookup"><span data-stu-id="abbe4-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="abbe4-110">Adicionar um botão</span><span class="sxs-lookup"><span data-stu-id="abbe4-110">Add a button</span></span>

<span data-ttu-id="abbe4-111">Para adicionar o botão pré-fabricado, na janela do **projeto** , selecione **ativos** e digite "PressableButtonHoloLens2" na barra de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="abbe4-111">To add the Button prefab, in the **Project** window, select **Assets** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![Botão pré-fabricado em ativos](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

<span data-ttu-id="abbe4-113">O botão pré-fabricado é a entrada representada por um ícone azul.</span><span class="sxs-lookup"><span data-stu-id="abbe4-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="abbe4-114">Clique e arraste o **PressableButtonHoloLens2** pré-fabricado para a hierarquia.</span><span class="sxs-lookup"><span data-stu-id="abbe4-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="abbe4-115">Com o objeto **PressableButtonHoloLens2** ainda selecionado, na janela Inspetor, configure o componente **transformação** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="abbe4-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="abbe4-116">**Posição**: X = 0, Y =-0,4, Z = 2</span><span class="sxs-lookup"><span data-stu-id="abbe4-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="abbe4-117">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="abbe4-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="abbe4-118">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="abbe4-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Transformação de botão](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

<span data-ttu-id="abbe4-120">Para se concentrar nos objetos na cena, você pode clicar duas vezes no objeto **PressableButtonHoloLens2** e, em seguida, reduzir um pouco o zoom novamente:</span><span class="sxs-lookup"><span data-stu-id="abbe4-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="abbe4-121">Comentar o botão espacial</span><span class="sxs-lookup"><span data-stu-id="abbe4-121">Spatialize button feedback</span></span>

<span data-ttu-id="abbe4-122">Nesta etapa, você causará a espacial dos comentários de áudio para o botão.</span><span class="sxs-lookup"><span data-stu-id="abbe4-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="abbe4-123">Para obter sugestões de design relacionadas, consulte [design de som espacial](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="abbe4-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="abbe4-124">Na janela do **mixer de áudio** , você definirá destinos chamados grupos de **mixers** para reprodução de áudio de componentes de **fonte de áudio** .</span><span class="sxs-lookup"><span data-stu-id="abbe4-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="abbe4-125">Para abrir a janela do **mixer de áudio** , no menu do Unity, selecione **janela**  >  mixer de áudio de **áudio**  >  : ![ Abrir janela do mixer de áudio](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="abbe4-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span></span>

 <span data-ttu-id="abbe4-126">Crie um **mixer** clicando no botão ' + ' ao lado de **mixers** e insira um nome adequado para o mixer, por exemplo, _mixer de áudio espacial_.</span><span class="sxs-lookup"><span data-stu-id="abbe4-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="abbe4-127">O novo mixer incluirá um **grupo** padrão chamado **Master**.</span><span class="sxs-lookup"><span data-stu-id="abbe4-127">The new mixer will include a default **Group** called **Master**.</span></span>

![Painel do mixer com o primeiro mixer](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="abbe4-129">Até que o verbo de reverberação esteja habilitado no [quinto capítulo: usando o reverberar para adicionar distância ao áudio espacial](unity-spatial-audio-ch5.md), o medidor de volume do mixer não mostra a atividade de sons reproduzidos por meio do Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="abbe4-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="abbe4-130">Na janela hierarquia, selecione o **PressableButtonHoloLens2** , em seguida, na janela Inspetor, localize o componente **fonte de áudio** e configure o componente fonte de áudio da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="abbe4-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="abbe4-131">Para a propriedade **saída** , clique no seletor e escolha o **mixer** que você criou.</span><span class="sxs-lookup"><span data-stu-id="abbe4-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="abbe4-132">Marque a caixa de seleção **espacialize** .</span><span class="sxs-lookup"><span data-stu-id="abbe4-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="abbe4-133">Mova o controle deslizante de **mistura espacial** para 3D (1).</span><span class="sxs-lookup"><span data-stu-id="abbe4-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![Fonte de áudio do botão](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="abbe4-135">Se você mover a **mistura espacial** para 1 (3D) sem marcar a caixa de seleção **espacialize** , o Unity usará seu spatializer panorâmico, em vez do **Microsoft spatializer** com HRTFs.</span><span class="sxs-lookup"><span data-stu-id="abbe4-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="abbe4-136">Ajustar a curva de volume</span><span class="sxs-lookup"><span data-stu-id="abbe4-136">Adjust the Volume curve</span></span>

<span data-ttu-id="abbe4-137">Por padrão, o Unity atenua os sons espaciais à medida que eles ficam mais distantes do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="abbe4-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="abbe4-138">Quando essa atenuação é aplicada aos sons de comentários de interação, a interface pode ser mais difícil de usar.</span><span class="sxs-lookup"><span data-stu-id="abbe4-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="abbe4-139">Para desabilitar essa atenuação, você precisa ajustar a curva de **volume** no componente **fonte de áudio** .</span><span class="sxs-lookup"><span data-stu-id="abbe4-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="abbe4-140">Na janela hierarquia, selecione o **PressableButtonHoloLens2** , em seguida, na janela Inspetor, navegue até **fonte de áudio**  >  **3D configurações de som** e configure da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="abbe4-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="abbe4-141">Defina a propriedade **volume rolloff** como linear rolloff</span><span class="sxs-lookup"><span data-stu-id="abbe4-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="abbe4-142">Arraste o ponto de extremidade na curva de **volume** (a curva vermelha) de ' 0 ' no eixo y até ' 1 '</span><span class="sxs-lookup"><span data-stu-id="abbe4-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="abbe4-143">Para ajustar a forma da curva de **volume** para ser simples, arraste o controle forma de curva de branco para ser paralelo ao eixo X</span><span class="sxs-lookup"><span data-stu-id="abbe4-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![Configurações de som 3D do botão](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="abbe4-145">Testando o áudio espacial</span><span class="sxs-lookup"><span data-stu-id="abbe4-145">Testing the spatialize audio</span></span>

<span data-ttu-id="abbe4-146">Para testar o áudio espacial no editor do Unity, você precisa adicionar um clipe de áudio na opção o componente de **origem de áudio** com **loop** com check-in no objeto **PressableButtonHoloLens2** .</span><span class="sxs-lookup"><span data-stu-id="abbe4-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="abbe4-147">No modo de reprodução, mova o objeto **PressableButtonHoloLens2** da esquerda para a direita e compare com e sem áudio espacial habilitado em sua estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="abbe4-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="abbe4-148">Você também pode alterar as configurações de fonte de áudio para teste:</span><span class="sxs-lookup"><span data-stu-id="abbe4-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="abbe4-149">Movendo a propriedade de **mistura espacial** entre 0-1 (2D sem espacial e um som espacial 3D)</span><span class="sxs-lookup"><span data-stu-id="abbe4-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="abbe4-150">Verificando e desmarcando a propriedade **espacialize**</span><span class="sxs-lookup"><span data-stu-id="abbe4-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="abbe4-151">Experimente o aplicativo no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="abbe4-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="abbe4-152">No aplicativo, você pode clicar no botão e ouvir os sons de interação do botão espacialado.</span><span class="sxs-lookup"><span data-stu-id="abbe4-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="abbe4-153">Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="abbe4-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="abbe4-154">Parabéns</span><span class="sxs-lookup"><span data-stu-id="abbe4-154">Congratulations</span></span>

<span data-ttu-id="abbe4-155">Neste tutorial, você aprenderá a espacialar os sons de interação do botão e a usar um clipe de áudio para testar a interação do botão espacialed.</span><span class="sxs-lookup"><span data-stu-id="abbe4-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="abbe4-156">No próximo tutorial, você aprenderá a gerar uma espacial de áudio de uma fonte de vídeo.</span><span class="sxs-lookup"><span data-stu-id="abbe4-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="abbe4-157">Próximo tutorial: 3. disespacial de áudio de um vídeo</span><span class="sxs-lookup"><span data-stu-id="abbe4-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)
