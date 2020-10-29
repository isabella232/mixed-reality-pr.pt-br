---
title: Som espacial no Unity
description: Reproduzir o som espacial de um ponto 3D específico dentro de sua cena do Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, som espacial, HRTF, tamanho da sala
ms.openlocfilehash: 9c5f71b2d9d13fa40f0d1674237d2da6c769e584
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675222"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="ee605-104">Som espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="ee605-104">Spatial sound in Unity</span></span>

<span data-ttu-id="ee605-105">Esta página contém links para recursos de som espacial no Unity.</span><span class="sxs-lookup"><span data-stu-id="ee605-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="ee605-106">Opções de Spatializer</span><span class="sxs-lookup"><span data-stu-id="ee605-106">Spatializer options</span></span>
<span data-ttu-id="ee605-107">As opções de Spatializer para aplicativos de realidade misturada incluem:</span><span class="sxs-lookup"><span data-stu-id="ee605-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="ee605-108">*SPATIALIZER HRTF MS* .</span><span class="sxs-lookup"><span data-stu-id="ee605-108">The *MS HRTF Spatializer* .</span></span> <span data-ttu-id="ee605-109">O Unity fornece isso como parte do pacote opcional do *Windows Mixed Reality* .</span><span class="sxs-lookup"><span data-stu-id="ee605-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="ee605-110">Isso é executado na CPU em uma arquitetura de ' fonte única ' de maior custo.</span><span class="sxs-lookup"><span data-stu-id="ee605-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="ee605-111">Isso é fornecido para compatibilidade com versões anteriores com aplicativos de HoloLens originais.</span><span class="sxs-lookup"><span data-stu-id="ee605-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="ee605-112">O *Microsoft Spatializer* .</span><span class="sxs-lookup"><span data-stu-id="ee605-112">The *Microsoft Spatializer* .</span></span> <span data-ttu-id="ee605-113">Isso está disponível no [repositório GitHub do Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="ee605-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="ee605-114">Isso usa uma arquitetura de "várias fontes" de menor custo.</span><span class="sxs-lookup"><span data-stu-id="ee605-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="ee605-115">No HoloLens 2, isso é descarregado para um acelerador de hardware.</span><span class="sxs-lookup"><span data-stu-id="ee605-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="ee605-116">Para novos aplicativos, recomendamos o *Microsoft Spatializer* .</span><span class="sxs-lookup"><span data-stu-id="ee605-116">For new applications, we recommend the *Microsoft Spatializer* .</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="ee605-117">Habilitar a espacialização</span><span class="sxs-lookup"><span data-stu-id="ee605-117">Enable spatialization</span></span>

<span data-ttu-id="ee605-118">Use o [NuGet para o Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) para instalar _Microsoft. SpatialAudio. Spatializer. Unity_ e escolha **Microsoft Spatializer** nas configurações de áudio do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ee605-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="ee605-119">Em seguida:</span><span class="sxs-lookup"><span data-stu-id="ee605-119">Then:</span></span>
* <span data-ttu-id="ee605-120">Anexar uma **fonte de áudio** a um objeto na hierarquia</span><span class="sxs-lookup"><span data-stu-id="ee605-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="ee605-121">Marque a caixa de seleção **habilitar a espacial**</span><span class="sxs-lookup"><span data-stu-id="ee605-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="ee605-122">Mover o controle deslizante de **mistura espacial** para ' 1 '</span><span class="sxs-lookup"><span data-stu-id="ee605-122">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="ee605-123">Verifique se o áudio espacial está habilitado na estação de trabalho do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="ee605-123">Ensure spatial audio is enabled on your developer workstation.</span></span> <span data-ttu-id="ee605-124">Habilite-o clicando com o botão direito do mouse no ícone de volume na barra de tarefas e verificando se o som espacial está definido como algo diferente de "desativado".</span><span class="sxs-lookup"><span data-stu-id="ee605-124">Enable it by right-clicking on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off."</span></span> <span data-ttu-id="ee605-125">Para obter a melhor representação do que você ouvirá no HoloLens 2, escolha **Windows Sonic para fones de ouvido** .</span><span class="sxs-lookup"><span data-stu-id="ee605-125">To get the best representation of what you'll hear on HoloLens 2, choose **Windows Sonic for Headphones** .</span></span>

>[!NOTE]
><span data-ttu-id="ee605-126">Se você receber um erro no Unity sobre não poder carregar o plugin Microsoft. SpatialAudio. Spatializer. Unity porque uma de suas dependências está ausente, verifique se você tem a versão mais recente do [Microsoft Visual C++ redistribuível](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) instalado no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ee605-126">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="ee605-127">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="ee605-127">For more details, see:</span></span>
* [<span data-ttu-id="ee605-128">Repositório GitHub do Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="ee605-128">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="ee605-129">Tutorial do spatializer da Microsoft</span><span class="sxs-lookup"><span data-stu-id="ee605-129">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="ee605-130">Documentação da fonte de áudio do Unity</span><span class="sxs-lookup"><span data-stu-id="ee605-130">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="ee605-131">Documentação do spatializer do Unity</span><span class="sxs-lookup"><span data-stu-id="ee605-131">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="ee605-132">Atenuação de distância</span><span class="sxs-lookup"><span data-stu-id="ee605-132">Distance-based attenuation</span></span>
<span data-ttu-id="ee605-133">O decaimento baseado em distância padrão da Unity tem uma distância mínima de 1 medidor e uma distância máxima de 500 metros, com um rolloff logarítmica.</span><span class="sxs-lookup"><span data-stu-id="ee605-133">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="ee605-134">Essas configurações podem funcionar para seu cenário, ou você pode achar que as fontes são atenuadas muito rapidamente ou lentas.</span><span class="sxs-lookup"><span data-stu-id="ee605-134">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="ee605-135">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="ee605-135">For more details, see:</span></span>
* <span data-ttu-id="ee605-136">[Design de som em realidade misturada](../../design/spatial-sound-design.md) para as configurações recomendadas.</span><span class="sxs-lookup"><span data-stu-id="ee605-136">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="ee605-137">[Documentação de fonte de áudio do Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) para obter instruções sobre como definir essas curvas.</span><span class="sxs-lookup"><span data-stu-id="ee605-137">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="ee605-138">Reverberação</span><span class="sxs-lookup"><span data-stu-id="ee605-138">Reverb</span></span>
<span data-ttu-id="ee605-139">Por padrão, o _Microsoft Spatializer_ desabilita os efeitos de Spatializer.</span><span class="sxs-lookup"><span data-stu-id="ee605-139">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="ee605-140">Para habilitar o reverberar e outros efeitos para fontes espaciais:</span><span class="sxs-lookup"><span data-stu-id="ee605-140">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="ee605-141">Anexar o componente de **nível de envio de efeito Room** a cada fonte</span><span class="sxs-lookup"><span data-stu-id="ee605-141">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="ee605-142">Ajuste a curva de nível de envio para cada fonte, para controlar o lucro do áudio enviado de volta ao grafo para o processamento de efeitos</span><span class="sxs-lookup"><span data-stu-id="ee605-142">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="ee605-143">Consulte [o capítulo 5 do tutorial do spatializer](tutorials/unity-spatial-audio-ch5.md) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="ee605-143">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="ee605-144">Exemplos de som espacial do Unity</span><span class="sxs-lookup"><span data-stu-id="ee605-144">Unity spatial sound examples</span></span>
<span data-ttu-id="ee605-145">Para obter exemplos de som espacial no Unity, consulte:</span><span class="sxs-lookup"><span data-stu-id="ee605-145">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="ee605-146">Demonstrações do MRTK</span><span class="sxs-lookup"><span data-stu-id="ee605-146">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="ee605-147">O [projeto de exemplo Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="ee605-147">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="ee605-148">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="ee605-148">Next Development Checkpoint</span></span>

<span data-ttu-id="ee605-149">Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos principais blocos de construção da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="ee605-149">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="ee605-150">A partir daqui, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="ee605-150">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ee605-151">Text</span><span class="sxs-lookup"><span data-stu-id="ee605-151">Text</span></span>](text-in-unity.md)

<span data-ttu-id="ee605-152">Ou vá para recursos e APIs da plataforma de realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="ee605-152">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ee605-153">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="ee605-153">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="ee605-154">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="ee605-154">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee605-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee605-155">See also</span></span>
* [<span data-ttu-id="ee605-156">Design de som em realidade misturada</span><span class="sxs-lookup"><span data-stu-id="ee605-156">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="ee605-157">Tutorial do spatializer da Microsoft</span><span class="sxs-lookup"><span data-stu-id="ee605-157">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
