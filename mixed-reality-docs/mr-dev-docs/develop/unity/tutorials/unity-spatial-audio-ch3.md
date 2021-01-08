---
title: Espacializar áudio de um vídeo
description: Saiba como importar um ativo de vídeo para seu projeto de realidade mista do Unity e espacialar o áudio do vídeo.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer, importação de vídeo, player de vídeo
ms.openlocfilehash: 211d1e32a8137444d0f33d442a60067dcd77ca36
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007407"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="ed1b8-104">Espacializar áudio de um vídeo</span><span class="sxs-lookup"><span data-stu-id="ed1b8-104">Spatializing audio from a video</span></span>

<span data-ttu-id="ed1b8-105">Neste terceiro capítulo do módulo de áudio espacial dos tutoriais do HoloLens 2 Unity, você irá:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-105">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="ed1b8-106">Importar um vídeo e adicionar um player de vídeo</span><span class="sxs-lookup"><span data-stu-id="ed1b8-106">Import a video and add a Video Player</span></span>
* <span data-ttu-id="ed1b8-107">Reproduza o vídeo em um Quadrangle</span><span class="sxs-lookup"><span data-stu-id="ed1b8-107">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="ed1b8-108">Rotear áudio do vídeo para o Quadrangle e espacialar o áudio</span><span class="sxs-lookup"><span data-stu-id="ed1b8-108">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="ed1b8-109">Importar um vídeo e adicionar um player de vídeo</span><span class="sxs-lookup"><span data-stu-id="ed1b8-109">Import a video and add a Video Player</span></span>

<span data-ttu-id="ed1b8-110">Arraste um arquivo de vídeo para o painel **projeto** em seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="ed1b8-110">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="ed1b8-111">Você pode usar [este vídeo](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) do projeto de exemplo de áudio espacial.</span><span class="sxs-lookup"><span data-stu-id="ed1b8-111">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![Pasta de ativos com vídeo](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="ed1b8-113">Ajustar as configurações de qualidade no clipe de vídeo pode garantir uma reprodução suave no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ed1b8-113">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="ed1b8-114">Clique no arquivo de vídeo no painel **projeto** .</span><span class="sxs-lookup"><span data-stu-id="ed1b8-114">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="ed1b8-115">Em seguida, no painel **Inspetor** do arquivo de vídeo, substitua as configurações para aplicativos da Windows Store e:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-115">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="ed1b8-116">Habilitar **transcodificação**</span><span class="sxs-lookup"><span data-stu-id="ed1b8-116">Enable **Transcode**</span></span>
* <span data-ttu-id="ed1b8-117">Definir o **codec** como H264</span><span class="sxs-lookup"><span data-stu-id="ed1b8-117">Set **Codec** to H264</span></span>
* <span data-ttu-id="ed1b8-118">Definir o **modo de taxa de bits** como baixo</span><span class="sxs-lookup"><span data-stu-id="ed1b8-118">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="ed1b8-119">Definir **qualidade espacial** para qualidade espacial média</span><span class="sxs-lookup"><span data-stu-id="ed1b8-119">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="ed1b8-120">Após esses ajustes, o painel de **Inspetor** do arquivo de vídeo terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-120">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![Painel de propriedades de vídeo](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="ed1b8-122">Em seguida, adicione um objeto **player de vídeo** à **hierarquia** clicando com o botão direito do mouse no painel **hierarquia** e escolhendo **vídeo-> player de vídeo**:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-122">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player**:</span></span>

![Player de vídeo na hierarquia](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="ed1b8-124">Reproduzir vídeo em um Quadrangle</span><span class="sxs-lookup"><span data-stu-id="ed1b8-124">Play video onto a quadrangle</span></span>

<span data-ttu-id="ed1b8-125">O objeto **player de vídeo** precisa de um objeto de jogo texturizado no qual renderizar o vídeo.</span><span class="sxs-lookup"><span data-stu-id="ed1b8-125">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="ed1b8-126">Primeiro, adicione um **Quad** à sua **hierarquia** clicando com o botão direito do mouse no painel **hierarquia** e escolhendo **objeto 3D-> Quad**:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-126">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad**:</span></span>

![Adicionar quádruplo à hierarquia](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="ed1b8-128">Para garantir que o **Quad** apareça na frente do usuário quando o aplicativo é iniciado, defina a propriedade **Position** de **Quad** para (0, 0, 2) e a propriedade **Scale** como (1,28, 0,72, 1).</span><span class="sxs-lookup"><span data-stu-id="ed1b8-128">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="ed1b8-129">Após essas alterações, o componente **transformação** no painel **Inspetor** para o **Quad** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-129">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Transformação quádrupla](images/spatial-audio/quad-transform.png)

<span data-ttu-id="ed1b8-131">Para Texturizar o **Quad** com vídeo, crie uma nova **textura de renderização**.</span><span class="sxs-lookup"><span data-stu-id="ed1b8-131">To texture the **Quad** with video, create a new **Render Texture**.</span></span> <span data-ttu-id="ed1b8-132">No painel **projeto** , clique com o botão direito do mouse e escolha **criar-> renderizar textura**:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-132">In the **Project** pane, right-click and choose **Create -> Render Texture**:</span></span>

![Criar textura de renderização](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="ed1b8-134">No painel **Inspetor** da **textura renderizar**, defina a propriedade **tamanho** para corresponder à resolução nativa do vídeo de 1280x720.</span><span class="sxs-lookup"><span data-stu-id="ed1b8-134">On the **Inspector** pane of the **Render Texture**, set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="ed1b8-135">Em seguida, para garantir um bom desempenho de renderização no HoloLens 2, defina a propriedade **buffer de profundidade** com **pelo menos 16 bits de profundidade**.</span><span class="sxs-lookup"><span data-stu-id="ed1b8-135">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span> <span data-ttu-id="ed1b8-136">Após essas configurações, o painel de **Inspetor** para a **textura de renderização** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-136">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![Renderizar Propriedades de textura](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="ed1b8-138">Em seguida, use sua nova **textura de renderização** como a textura para o **Quad**:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-138">Next, use your new **Render Texture** as the texture for the **Quad**:</span></span>
1. <span data-ttu-id="ed1b8-139">Arraste a **textura renderizar** do painel **projeto** para o **Quad** na **hierarquia**</span><span class="sxs-lookup"><span data-stu-id="ed1b8-139">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="ed1b8-140">Para garantir um bom desempenho no HoloLens 2, no painel do **Inspetor** para o **Quad**, selecione o **sombreador standard do kit de ferramentas da realidade misturada**.</span><span class="sxs-lookup"><span data-stu-id="ed1b8-140">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad**, select the **Mixed Reality Toolkit Standard Shader**.</span></span>

<span data-ttu-id="ed1b8-141">Com essas configurações, o componente de **textura** no painel de **Inspetor** para o **Quad** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-141">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Propriedades de textura quádrupla](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="ed1b8-143">Para definir o novo **player de vídeo** e **renderizar a textura** para reproduzir o clipe de vídeo, abra o painel do **Inspetor** para o **player de vídeo** e:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-143">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="ed1b8-144">Defina a propriedade **videoclipe** como seu arquivo de vídeo</span><span class="sxs-lookup"><span data-stu-id="ed1b8-144">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="ed1b8-145">Marque a caixa de seleção **loop**</span><span class="sxs-lookup"><span data-stu-id="ed1b8-145">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="ed1b8-146">Definir a **textura de destino** para sua nova textura de renderização</span><span class="sxs-lookup"><span data-stu-id="ed1b8-146">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="ed1b8-147">O painel **Inspetor** do **player de vídeo** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-147">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![Propriedades do player de vídeo](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="ed1b8-149">Esespacialr o áudio do vídeo</span><span class="sxs-lookup"><span data-stu-id="ed1b8-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="ed1b8-150">No painel de **Inspetor** para o **Quad**, crie uma **fonte de áudio** para a qual você encaminhará o áudio do vídeo:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-150">In the **Inspector** pane for the **Quad**, create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="ed1b8-151">Clique em **Adicionar componente** na parte inferior do painel</span><span class="sxs-lookup"><span data-stu-id="ed1b8-151">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="ed1b8-152">Adicionar uma **fonte de áudio**</span><span class="sxs-lookup"><span data-stu-id="ed1b8-152">Add an **Audio Source**</span></span>

<span data-ttu-id="ed1b8-153">Em seguida, na **fonte de áudio**:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-153">Then, on the **Audio Source**:</span></span>
* <span data-ttu-id="ed1b8-154">Definir **saída** para o mixer</span><span class="sxs-lookup"><span data-stu-id="ed1b8-154">Set **Output** to your mixer</span></span>
* <span data-ttu-id="ed1b8-155">Marque a caixa **espacialize**</span><span class="sxs-lookup"><span data-stu-id="ed1b8-155">Check the **Spatialize** box</span></span>
* <span data-ttu-id="ed1b8-156">Mover o controle deslizante de **mistura espacial** para 1 (3D)</span><span class="sxs-lookup"><span data-stu-id="ed1b8-156">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="ed1b8-157">Após essas alterações, o componente **fonte de áudio** no painel **Inspetor** para o **Quad** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-157">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Inspetor de fonte de áudio quádruplo](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="ed1b8-159">Para definir o **player de vídeo** para rotear seu áudio para a **fonte de áudio** no **Quad**, abra o painel do **Inspetor** para o **player de vídeo** e:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-159">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad**, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="ed1b8-160">Definir o **modo de saída de áudio** como ' fonte de áudio '</span><span class="sxs-lookup"><span data-stu-id="ed1b8-160">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="ed1b8-161">Definir a propriedade **fonte de áudio** para o quad</span><span class="sxs-lookup"><span data-stu-id="ed1b8-161">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="ed1b8-162">Após essas alterações, o painel de **Inspetor** do **player de vídeo** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="ed1b8-162">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![Fonte de áudio definida do player de vídeo](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="ed1b8-164">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ed1b8-164">Next steps</span></span>

<span data-ttu-id="ed1b8-165">Experimente seu aplicativo em um HoloLens 2 ou no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="ed1b8-165">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="ed1b8-166">Você verá e ouvirá o vídeo e o áudio do vídeo será espacial.</span><span class="sxs-lookup"><span data-stu-id="ed1b8-166">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ed1b8-167">Capítulo 4</span><span class="sxs-lookup"><span data-stu-id="ed1b8-167">Chapter 4</span></span>](unity-spatial-audio-ch4.md) 

