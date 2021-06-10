---
title: Tutoriais de áudio espacial – 2. Espacializar sons de interação de botão
description: Adicione um botão ao projeto e espacialize os sons de interação do botão.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade misturada, UWP, Windows 10, HRTF, função de transferência relacionada à cabeça, reverb, Microsoft Spatializer, prefabs, curva de volume
ms.openlocfilehash: f3f2faf8220eaebcc674bcf02a45d99d58169076
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712785"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="9336c-105">2. Espacializar sons de interação de botão</span><span class="sxs-lookup"><span data-stu-id="9336c-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="9336c-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="9336c-106">Overview</span></span>

<span data-ttu-id="9336c-107">Neste tutorial, você aprenderá a espacializar os sons de interação do botão e também a usar um clipe de áudio para testar a interação espacializada do botão.</span><span class="sxs-lookup"><span data-stu-id="9336c-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="9336c-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9336c-108">Objectives</span></span>

* <span data-ttu-id="9336c-109">Adicionar e espacializar os sons de clique do botão</span><span class="sxs-lookup"><span data-stu-id="9336c-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="9336c-110">Adicionar um botão</span><span class="sxs-lookup"><span data-stu-id="9336c-110">Add a button</span></span>

<span data-ttu-id="9336c-111">Para adicionar o pré-fab  Botão,  na janela Projeto, selecione Pacotes e digite "PressableButtonHoloLens2" na barra de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="9336c-111">To add the Button prefab, in the **Project** window, select **Packages** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![Prefab do botão em Ativos](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

<span data-ttu-id="9336c-113">O prefab do botão é a entrada representada por um ícone azul.</span><span class="sxs-lookup"><span data-stu-id="9336c-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="9336c-114">Clique e arraste o pré-fab **PressableButtonHoloLens2** para a Hierarquia.</span><span class="sxs-lookup"><span data-stu-id="9336c-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="9336c-115">Com o **objeto PressableButtonHoloLens2** ainda selecionado, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9336c-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="9336c-116">**Posição:** X = 0, Y = -0,4, Z = 2</span><span class="sxs-lookup"><span data-stu-id="9336c-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="9336c-117">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="9336c-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="9336c-118">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="9336c-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Transformação de botão](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

<span data-ttu-id="9336c-120">Para se concentrar nos objetos na cena, você pode clicar duas vezes no objeto **PressableButtonHoloLens2** e ampliar um pouco novamente:</span><span class="sxs-lookup"><span data-stu-id="9336c-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="9336c-121">Comentários sobre o botão Espacializar</span><span class="sxs-lookup"><span data-stu-id="9336c-121">Spatialize button feedback</span></span>

<span data-ttu-id="9336c-122">Nesta etapa, você espacializará os comentários de áudio para o botão.</span><span class="sxs-lookup"><span data-stu-id="9336c-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="9336c-123">Para sugestões de design relacionadas, consulte [design de som espacial](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="9336c-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="9336c-124">Na janela **Mixer de Áudio,** você definirá destinos chamados **Grupos do Mixer** para reprodução de áudio de componentes de Fonte **de** Áudio.</span><span class="sxs-lookup"><span data-stu-id="9336c-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="9336c-125">Para abrir a janela **Do Mixer de** Áudio, no menu do Unity, selecione Janela   >  **Audio**  >  **Mixer:** ![ Abrir Janela do Mixer de Áudio](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)</span><span class="sxs-lookup"><span data-stu-id="9336c-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)</span></span>

 <span data-ttu-id="9336c-126">Crie um **Mixer** clicando no '+' ao lado de **Mixers** e insira um nome adequado para o Mixer, por exemplo, _Mixer de Áudio Espacial._</span><span class="sxs-lookup"><span data-stu-id="9336c-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="9336c-127">O novo mixer incluirá um Grupo **padrão** chamado **Mestre.**</span><span class="sxs-lookup"><span data-stu-id="9336c-127">The new mixer will include a default **Group** called **Master**.</span></span>

![Painel mixer com o primeiro mixer](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> <span data-ttu-id="9336c-129">Até que o reverb seja habilitado no [5º Capítulo:](unity-spatial-audio-ch5.md)Usando o reverb para adicionar distância ao áudio espacial, o medidor de volume do mixer não mostra a atividade de sons tocadas por meio do Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="9336c-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="9336c-130">Na janela Hierarquia, selecione **PressableButtonHoloLens2** e, na  janela Inspetor, encontre o componente Fonte de Áudio e Configure o componente Fonte de Áudio da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="9336c-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="9336c-131">Para a **propriedade Saída,** clique no seletor e escolha o **Mixer** que você criou.</span><span class="sxs-lookup"><span data-stu-id="9336c-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="9336c-132">Marque a **caixa de seleção Espacializar.**</span><span class="sxs-lookup"><span data-stu-id="9336c-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="9336c-133">Mova o **controle deslizante do Spatial Blend** para 3D (1).</span><span class="sxs-lookup"><span data-stu-id="9336c-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![Fonte de áudio do botão](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="9336c-135">Se você mover **o Spatial Blend** para 1  (3D) sem verificar a caixa de seleção Espacializar, o Unity usará seu espacializador de panorâmico, em vez do **Microsoft Spatializer** com HRTFs.</span><span class="sxs-lookup"><span data-stu-id="9336c-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="9336c-136">Ajustar a curva volume</span><span class="sxs-lookup"><span data-stu-id="9336c-136">Adjust the Volume curve</span></span>

<span data-ttu-id="9336c-137">Por padrão, o Unity atenua os sons espacializados à medida que eles ficam mais distantes do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="9336c-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="9336c-138">Quando essa atenuação é aplicada aos sons de comentários de interação, a interface pode se tornar mais difícil de usar.</span><span class="sxs-lookup"><span data-stu-id="9336c-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="9336c-139">Para desabilitar essa atenuação, você precisa ajustar a curva **volume** no componente **Fonte de** Áudio.</span><span class="sxs-lookup"><span data-stu-id="9336c-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="9336c-140">Na janela Hierarquia, selecione **PressableButtonHoloLens2** e, na janela Inspetor, navegue até Configurações de Som  >  **3D** da Fonte de Áudio e Configure da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="9336c-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="9336c-141">Definir a **propriedade Volume Rolloff** como Rolloff Linear</span><span class="sxs-lookup"><span data-stu-id="9336c-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="9336c-142">Arraste o ponto de extremidade na curva **volume** (a curva vermelha) de '0' no eixo y até '1'</span><span class="sxs-lookup"><span data-stu-id="9336c-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="9336c-143">Para ajustar a forma da curva **volume** a ser plana, arraste o controle de forma de curva branca para ser paralelo ao eixo X</span><span class="sxs-lookup"><span data-stu-id="9336c-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![Configurações de som 3D do botão](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="9336c-145">Testando o áudio de espacialização</span><span class="sxs-lookup"><span data-stu-id="9336c-145">Testing the spatialize audio</span></span>

<span data-ttu-id="9336c-146">Para testar o áudio espacializado no editor do Unity,  você precisa adicionar um clipe de áudio no componente Fonte de Áudio com a opção **Loop** marcada no objeto **PressableButtonHoloLens2.**</span><span class="sxs-lookup"><span data-stu-id="9336c-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="9336c-147">No modo de reprodução, mova o objeto **PressableButtonHoloLens2** da esquerda para a direita e compare com e sem áudio espacial habilitado em sua estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9336c-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="9336c-148">Você também pode alterar as configurações da Fonte de Áudio para teste:</span><span class="sxs-lookup"><span data-stu-id="9336c-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="9336c-149">Movendo a **propriedade Spatial Blend** entre 0 e 1 (som espacializado 2D não espacializado e 3D)</span><span class="sxs-lookup"><span data-stu-id="9336c-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="9336c-150">Verificando e desmarcando a **propriedade Spatialize**</span><span class="sxs-lookup"><span data-stu-id="9336c-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="9336c-151">Experimente o aplicativo no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9336c-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="9336c-152">No aplicativo, você pode clicar no botão e ouvir os sons de interação do botão espacializado.</span><span class="sxs-lookup"><span data-stu-id="9336c-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="9336c-153">Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="9336c-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9336c-154">Parabéns</span><span class="sxs-lookup"><span data-stu-id="9336c-154">Congratulations</span></span>

<span data-ttu-id="9336c-155">Neste tutorial, você aprendeu a espacializar os sons de interação do botão e a usar um clipe de áudio para testar a interação espacializada do botão.</span><span class="sxs-lookup"><span data-stu-id="9336c-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="9336c-156">No próximo tutorial, você aprenderá a espacializar o áudio de uma fonte de vídeo.</span><span class="sxs-lookup"><span data-stu-id="9336c-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9336c-157">Próximo Tutorial: 3. Espacializando o áudio de um vídeo</span><span class="sxs-lookup"><span data-stu-id="9336c-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)
