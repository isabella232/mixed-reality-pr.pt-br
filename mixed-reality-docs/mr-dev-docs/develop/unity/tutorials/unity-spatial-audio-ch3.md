---
title: Tutoriais de áudio espacial-3. Espacializar áudio de um vídeo
description: Importar um ativo de vídeo para seu projeto do Unity e espacialar o áudio do vídeo.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer, importação de vídeo, player de vídeo
ms.openlocfilehash: 876918c3e886fae6cd2066d84c55a6e158e4c773
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590048"
---
# <a name="3-spatializing-audio-from-a-video"></a><span data-ttu-id="84b48-105">3. Espacializar áudio de um vídeo</span><span class="sxs-lookup"><span data-stu-id="84b48-105">3. Spatializing audio from a video</span></span>

## <a name="overview"></a><span data-ttu-id="84b48-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="84b48-106">Overview</span></span>

<span data-ttu-id="84b48-107">Neste tutorial, você aprenderá a gerar uma espacial de áudio de uma fonte de vídeo e testá-la no editor do Unity e no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="84b48-107">In this tutorial, you will learn how to spatialize audio from an video source and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="84b48-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="84b48-108">Objectives</span></span>

* <span data-ttu-id="84b48-109">Importar um vídeo e adicionar um player de vídeo</span><span class="sxs-lookup"><span data-stu-id="84b48-109">Import a video and add a Video Player</span></span>
* <span data-ttu-id="84b48-110">Reproduza o vídeo em um Quadrangle</span><span class="sxs-lookup"><span data-stu-id="84b48-110">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="84b48-111">Rotear áudio do vídeo para o Quadrangle e espacialar o áudio</span><span class="sxs-lookup"><span data-stu-id="84b48-111">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a><span data-ttu-id="84b48-112">Importar um vídeo e adicionar um player de vídeo à cena</span><span class="sxs-lookup"><span data-stu-id="84b48-112">Import a video and add a Video Player to the Scene</span></span>

<span data-ttu-id="84b48-113">Para este tutorial, use [este vídeo](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) do projeto de exemplo de áudio espacial.</span><span class="sxs-lookup"><span data-stu-id="84b48-113">For this tutorial use You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

<span data-ttu-id="84b48-114">Para importar o vídeo para o projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="84b48-114">To import Video into the unity project.</span></span> <span data-ttu-id="84b48-115">no menu do Unity, selecione **ativo**  >  **importar novo** ativo 
 ![ importando ativo](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="84b48-115">in the Unity menu select **Asset** > **Import New Asset**
![Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span></span>

<span data-ttu-id="84b48-116">Na janela **importar novo ativo...** , selecione o arquivo de **som espacial do Microsoft HoloLens-PTPvx7mDon4** que você baixou e clique no botão **abrir** para importar o ativo para o projeto:</span><span class="sxs-lookup"><span data-stu-id="84b48-116">In the **Import New Asset...** window, select the **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** file you downloaded and click the **Open** button to import the asset into the project:</span></span>

![Selecionando ativo](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

<span data-ttu-id="84b48-118">Ajustar as configurações de qualidade no clipe de vídeo pode garantir uma reprodução suave no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="84b48-118">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="84b48-119">Selecione o arquivo de vídeo na janela do **projeto** e, na janela Inspetor do arquivo de vídeo, **substitua** as configurações para **aplicativos da Windows Store** e:</span><span class="sxs-lookup"><span data-stu-id="84b48-119">Select the video file in the **Project** window and in the Inspector window of the video file, **override** the settings for **Windows Store Apps**, and:</span></span>

* <span data-ttu-id="84b48-120">Habilitar **transcodificação**</span><span class="sxs-lookup"><span data-stu-id="84b48-120">Enable **Transcode**</span></span>
* <span data-ttu-id="84b48-121">Definir o **codec** como H264</span><span class="sxs-lookup"><span data-stu-id="84b48-121">Set **Codec** to H264</span></span>
* <span data-ttu-id="84b48-122">Definir o **modo de taxa de bits** como baixo</span><span class="sxs-lookup"><span data-stu-id="84b48-122">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="84b48-123">Definir **qualidade espacial** para qualidade espacial média</span><span class="sxs-lookup"><span data-stu-id="84b48-123">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="84b48-124">Após esses ajustes, clique em aplicar para alterar a configuração de qualidade no clipe de vídeo.</span><span class="sxs-lookup"><span data-stu-id="84b48-124">After these adjustments, click on Apply to change the quality setting on the video clip.</span></span>

![Alteração de propriedade de vídeo](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

<span data-ttu-id="84b48-126">Clique com o botão direito do mouse na hierarquia, selecione **Video**  >  **Player** de vídeo para adicionar o componente de player de vídeo.</span><span class="sxs-lookup"><span data-stu-id="84b48-126">Right click on the Hierarchy, Select **Video** > **Video Player** to add Video player component.</span></span>

![Adicionar player de vídeo](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="84b48-128">Reproduzir vídeo em um Quadrangle</span><span class="sxs-lookup"><span data-stu-id="84b48-128">Play video onto a quadrangle</span></span>

<span data-ttu-id="84b48-129">O objeto **player de vídeo** precisa de um objeto de jogo texturizado para renderizar o vídeo.</span><span class="sxs-lookup"><span data-stu-id="84b48-129">The **Video Player** object needs a textured game object to render the video.</span></span>

<span data-ttu-id="84b48-130">Clique com o botão direito do mouse na hierarquia, selecione **objeto 3D**  >  **Quad** para criar um quad e configure seu componente de **transformação** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="84b48-130">Right click the Hierarchy , Select **3D Object** > **Quad** to create a quad and configure its **Transform** component as follows:</span></span>

* <span data-ttu-id="84b48-131">**Posição**: X = 0, Y = 0, Z = 2</span><span class="sxs-lookup"><span data-stu-id="84b48-131">**Position**: X = 0, Y = 0, Z = 2</span></span>
* <span data-ttu-id="84b48-132">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="84b48-132">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="84b48-133">**Escala**: X = 1,28, Y = 0,72, Z = 1</span><span class="sxs-lookup"><span data-stu-id="84b48-133">**Scale**: X = 1.28, Y = 0.72, Z = 1</span></span>

![Adicionar um quad](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

<span data-ttu-id="84b48-135">Agora você precisa Texturizar o **Quad** com o vídeo, na janela do **projeto** , clique com o botão direito do mouse e escolha **criar**  >  **textura de renderização** para criar um componente de textura de renderização, insira um nome adequado para a textura de renderização, por exemplo, textura de _áudio espacial_:</span><span class="sxs-lookup"><span data-stu-id="84b48-135">Now you need to texture the **Quad** with the video, In the **Project** window, right-click and choose **Create** > **Render Texture** to create a Render Texture component, enter a suitable name to the Render Texture for example, _Spatial Audio Texture_:</span></span>

![Criar textura de renderização](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

<span data-ttu-id="84b48-137">Selecione a **textura renderizar** e, na janela Inspetor, defina a propriedade **tamanho** para corresponder à resolução nativa do vídeo de 1280x720.</span><span class="sxs-lookup"><span data-stu-id="84b48-137">Select the **Render Texture** and in the Inspector window set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="84b48-138">Em seguida, para garantir um bom desempenho de renderização no HoloLens 2, defina a propriedade **buffer de profundidade** com **pelo menos 16 bits de profundidade**.</span><span class="sxs-lookup"><span data-stu-id="84b48-138">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span>

![Renderizar Propriedades de textura](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

<span data-ttu-id="84b48-140">Em seguida, use a textura de **áudio espacial** da textura de renderização criada como a textura para o **Quad**:</span><span class="sxs-lookup"><span data-stu-id="84b48-140">Next, use the created Render Texture **Spatial Audio Texture** as the texture for the **Quad**:</span></span>

1. <span data-ttu-id="84b48-141">Arraste a **textura de áudio espacial** da janela do **projeto** até o **Quad** na hierarquia para adicionar a textura de renderização ao Quad</span><span class="sxs-lookup"><span data-stu-id="84b48-141">Drag the **Spatial Audio Texture** from the **Project** window onto the **Quad** in the Hierarchy to add the Render Texture to the Quad</span></span>
2. <span data-ttu-id="84b48-142">Para garantir um bom desempenho no HoloLens 2, selecione Quad na hierarquia e, na janela Inspetor para sombreador, selecione o sombreador standard do **Kit de ferramentas da realidade misturada**  >   .</span><span class="sxs-lookup"><span data-stu-id="84b48-142">To ensure good performance on HoloLens 2, select Quad in the Hierarchy and in the Inspector window for shader select the **Mixed Reality Toolkit** > **Standard** Shader.</span></span>

![Propriedades de textura quádrupla](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

<span data-ttu-id="84b48-144">Para definir **o player de vídeo** e a textura de **renderização** para reproduzir o clipe de vídeo, selecione o **player de vídeo** na **hierarquia** e, na janela **Inspetor** ,</span><span class="sxs-lookup"><span data-stu-id="84b48-144">To set **Video Player** and **Render Texture** to play the video clip, select the **Video Player** in the **Hierarchy** and in the **Inspector** window,</span></span>

* <span data-ttu-id="84b48-145">Defina a propriedade **videoclipe** como o arquivo de vídeo baixado ' Microsoft HoloLens-Spatial Sound-PTPvx7mDon4 '</span><span class="sxs-lookup"><span data-stu-id="84b48-145">Set the **Video Clip** property to the downloaded video file 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span></span>
* <span data-ttu-id="84b48-146">Marque a caixa de seleção **loop**</span><span class="sxs-lookup"><span data-stu-id="84b48-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="84b48-147">Definir textura de **destino** para sua nova **textura de áudio espacial** de textura de renderização</span><span class="sxs-lookup"><span data-stu-id="84b48-147">Set **Target Texture** to your new render texture **Spatial Audio Texture**</span></span>

![Propriedades do player de vídeo](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="84b48-149">Esespacialr o áudio do vídeo</span><span class="sxs-lookup"><span data-stu-id="84b48-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="84b48-150">Na janela hierarquia, selecione **Quad** Object e, em seguida, na janela Inspetor, use o botão **Adicionar componente** para adicionar a **fonte de áudio** para a qual você encaminhará o áudio do vídeo.</span><span class="sxs-lookup"><span data-stu-id="84b48-150">In the Hierarchy window, select **Quad** object, then in the Inspector window, use the **Add Component** button to add **Audio Source** to which you'll route the audio from the video.</span></span>

<span data-ttu-id="84b48-151">Na **fonte de áudio**:</span><span class="sxs-lookup"><span data-stu-id="84b48-151">In the **Audio Source**:</span></span>

* <span data-ttu-id="84b48-152">Definir **saída** para o **mixer de áudio espacial**</span><span class="sxs-lookup"><span data-stu-id="84b48-152">Set **Output** to the **Spatial Audio Mixer**</span></span>
* <span data-ttu-id="84b48-153">Marque a caixa **espacialize**</span><span class="sxs-lookup"><span data-stu-id="84b48-153">Check the **Spatialize** box</span></span>
* <span data-ttu-id="84b48-154">Mover o controle deslizante de **mistura espacial** para 1 (3D)</span><span class="sxs-lookup"><span data-stu-id="84b48-154">Move the **Spatial Blend** slider to 1 (3D)</span></span>

![Inspetor de fonte de áudio quádruplo](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

<span data-ttu-id="84b48-156">Para definir o player de vídeo para rotear seu áudio para a **fonte de áudio**, selecione o **player de vídeo** na janela hierarquia e, no objeto player de vídeo do Inspetor, faça as alterações a seguir.</span><span class="sxs-lookup"><span data-stu-id="84b48-156">To set the Video Player to route its audio to the **Audio Source**, select the **Video Player** In the Hierarchy window, and in Video Player object in the Inspector do the following changes.</span></span>

* <span data-ttu-id="84b48-157">Definir o **modo de saída de áudio** como **fonte de áudio**</span><span class="sxs-lookup"><span data-stu-id="84b48-157">Set the **Audio Output Mode** to **Audio Source**</span></span>
* <span data-ttu-id="84b48-158">Definir a propriedade **fonte de áudio** para o **Quad**</span><span class="sxs-lookup"><span data-stu-id="84b48-158">Set the **Audio Source** property to the **Quad**</span></span>

![Fonte de áudio definida do player de vídeo](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="84b48-160">Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="84b48-160">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="84b48-161">Parabéns</span><span class="sxs-lookup"><span data-stu-id="84b48-161">Congratulations</span></span>

<span data-ttu-id="84b48-162">Neste tutorial, você aprendeu a usar a espacial de áudio de uma fonte de vídeo experimentando seu aplicativo em um HoloLens 2 ou no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="84b48-162">In this tutorial, you have learned how to spatialize audio from an video source Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="84b48-163">Você verá e ouvirá o vídeo e o áudio do vídeo será espacial.</span><span class="sxs-lookup"><span data-stu-id="84b48-163">You'll see and hear the video, and the audio from the video is spatialized.</span></span>

<span data-ttu-id="84b48-164">No próximo tutorial, você aprenderá a habilitar e desabilitar a espacial em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="84b48-164">In the next tutorial you will learn how to Enable and disable spatialization at run time</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84b48-165">Próximo tutorial: 4. Habilitando e desabilitando a espacial em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="84b48-165">Next Tutorial: 4. Enabling and disabling spatialization at run time</span></span>](unity-spatial-audio-ch4.md)
