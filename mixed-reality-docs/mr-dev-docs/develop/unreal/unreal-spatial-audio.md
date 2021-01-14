---
title: Áudio espacial no Unreal
description: Conheça as vantagens e desvantagens do plug-in de áudio espacial para aplicativos de realidade misturada do Unreal para dispositivos HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicação remota, realidade misturada, desenvolvimento, introdução, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, áudio espacial
ms.openlocfilehash: 98c10e370cd4ca5e437a4677be6fce3d3aee53a9
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009966"
---
# <a name="spatial-audio-in-unreal"></a><span data-ttu-id="c26a3-104">Áudio espacial no Unreal</span><span class="sxs-lookup"><span data-stu-id="c26a3-104">Spatial Audio in Unreal</span></span>

<span data-ttu-id="c26a3-105">Ao contrário da visão, os seres humanos ouvem o som ao redor em 360 graus.</span><span class="sxs-lookup"><span data-stu-id="c26a3-105">Unlike vision, humans hear in 360-degree surround sound.</span></span> <span data-ttu-id="c26a3-106">O som espacial emula o modo como a audição humana funciona, fornecendo as indicações necessárias para identificar localizações de som no espaço do mundo.</span><span class="sxs-lookup"><span data-stu-id="c26a3-106">Spatial sound emulates how human hearing works, providing the cues needed to identify sound locations in world-space.</span></span> <span data-ttu-id="c26a3-107">Ao adicionar o som espacial aos seus aplicativos de realidade misturada, você está aprimorando o nível de imersão experimentado pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="c26a3-107">When you add spatial sound in your mixed reality applications, you're enhancing the level of immersion your user's experience.</span></span>  

<span data-ttu-id="c26a3-108">O processamento de som espacial de alta qualidade é complexo e, portanto, o HoloLens 2 é fornecido com um hardware dedicado para processar esses objetos de som.</span><span class="sxs-lookup"><span data-stu-id="c26a3-108">High-quality spatial sound processing is complex, so the HoloLens 2 comes with dedicated hardware for processing those sound objects.</span></span>  <span data-ttu-id="c26a3-109">Para acessar esse suporte de processamento de hardware, instale o plug-in **MicrosoftSpatialSound** no seu projeto do Unreal.</span><span class="sxs-lookup"><span data-stu-id="c26a3-109">Before you can access this hardware processing support, you'll need to install the **MicrosoftSpatialSound** plugin in your Unreal project.</span></span> <span data-ttu-id="c26a3-110">Este artigo descreverá a instalação e a configuração do plug-in e indicará recursos mais aprofundados.</span><span class="sxs-lookup"><span data-stu-id="c26a3-110">This article will walk you through the installation and configuration of the plugin and point you towards more in-depth resources.</span></span>

## <a name="installing-the-microsoft-spatial-sound-plugin"></a><span data-ttu-id="c26a3-111">Como instalar o plug-in do Microsoft Spatial Sound</span><span class="sxs-lookup"><span data-stu-id="c26a3-111">Installing the Microsoft Spatial Sound plugin</span></span>

<span data-ttu-id="c26a3-112">A primeira etapa para adicionar som espacial ao seu projeto é instalar o plug-in do Microsoft Spatial Sound, que pode ser encontrado com as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="c26a3-112">The first step to adding spatial sound to your project is installing the Microsoft Spatial Sound plugin, which you can find by:</span></span>

1. <span data-ttu-id="c26a3-113">Clicando em **Editar > Plug-ins** e procurando **MicrosoftSpatialSound** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c26a3-113">Clicking **Edit > Plugins** and searching for **MicrosoftSpatialSound** in the search box.</span></span>
2. <span data-ttu-id="c26a3-114">Marcando a caixa de seleção **Habilitado** no plug-in **MicrosoftSpatialSound**.</span><span class="sxs-lookup"><span data-stu-id="c26a3-114">Selecting the **Enabled** checkbox in the **MicrosoftSpatialSound** plugin.</span></span>
3. <span data-ttu-id="c26a3-115">Reiniciando o editor do Unreal selecionando **Reiniciar Agora** na página de plug-ins.</span><span class="sxs-lookup"><span data-stu-id="c26a3-115">Restarting the Unreal Editor by selecting **Restart Now** from the plugins page.</span></span>

> [!NOTE]
> <span data-ttu-id="c26a3-116">Se ainda não tiver feito isso, você precisará instalar os plug-ins do **Microsoft Windows Mixed Reality** e do **HoloLens** seguindo as instruções da seção **[Como inicializar seu projeto](tutorials/unreal-uxt-ch2.md)** da nossa série de tutoriais do Unreal.</span><span class="sxs-lookup"><span data-stu-id="c26a3-116">If you haven't already, you'll need to install the **Microsoft Windows Mixed Reality** and **HoloLens** plugins by following the instructions in the **[Initializing your project](tutorials/unreal-uxt-ch2.md)** section of our Unreal tutorial series.</span></span>

![Plug-in de áudio espacial do Unreal](images/unreal-spatial-audio-img-01.png)

<span data-ttu-id="c26a3-118">Depois que o editor for reiniciado, o projeto estará pronto.</span><span class="sxs-lookup"><span data-stu-id="c26a3-118">Once the editor restarts, your project is all set!</span></span>

## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a><span data-ttu-id="c26a3-119">Como configurar o plug-in de espacialização para a plataforma HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c26a3-119">Setting the spatialization plugin for HoloLens 2 platform</span></span>

<span data-ttu-id="c26a3-120">A configuração do plug-in de espacialização é feita de acordo com a plataforma.</span><span class="sxs-lookup"><span data-stu-id="c26a3-120">Configuring the spatialization plugin is done on a per-platform basis.</span></span>  <span data-ttu-id="c26a3-121">Habilite o plug-in do Microsoft Spatial Sound para o HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="c26a3-121">You can enable the Microsoft Spatial Sound plugin for the HoloLens 2 by:</span></span>
1. <span data-ttu-id="c26a3-122">Selecionando **Editar > Configurações de Projeto**, rolando o painel até \*\*Plataformas e clicando em **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="c26a3-122">Selecting **Edit > Project Settings**, scrolling to \*\*Platforms, and clicking **HoloLens**.</span></span>
2. <span data-ttu-id="c26a3-123">Expandindo as propriedades de **Áudio** e definindo o campo **Plug-in de Espacialização** como **Microsoft Spatial Sound**.</span><span class="sxs-lookup"><span data-stu-id="c26a3-123">Expanding the **Audio** properties and setting the **Spatialization Plugin** field to **Microsoft Spatial Sound**.</span></span>

![Plug-in de espacialização para a plataforma HoloLens](images/unreal-spatial-audio-img-02.png)

<span data-ttu-id="c26a3-125">Se você pretende visualizar seu aplicativo no editor do Unreal em um computador desktop, repita as etapas acima para a plataforma **Windows**:</span><span class="sxs-lookup"><span data-stu-id="c26a3-125">If you're going to be previewing your application in the Unreal editor on a desktop PC, you'll need to repeat the above steps for the **Windows** platform:</span></span>

![Plug-in de espacialização para a plataforma Windows](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a><span data-ttu-id="c26a3-127">Como habilitar o áudio espacial na sua estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="c26a3-127">Enabling spatial audio on your workstation</span></span>

<span data-ttu-id="c26a3-128">O áudio espacial está desabilitado por padrão nas versões de área de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="c26a3-128">Spatial audio is disabled by default on desktop versions of Windows.</span></span> <span data-ttu-id="c26a3-129">Habilite-o:</span><span class="sxs-lookup"><span data-stu-id="c26a3-129">You can enable it by:</span></span>
* <span data-ttu-id="c26a3-130">Clicando com o botão direito do mouse no ícone de **volume** na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="c26a3-130">Right-clicking on the **volume** icon in the task bar.</span></span>
    + <span data-ttu-id="c26a3-131">Escolha **Som espacial -> Windows Sonic para Fones de Ouvido** para obter a melhor representação do que você ouvirá no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c26a3-131">Choose **Spatial sound -> Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

![Plug-in de espacialização](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
><span data-ttu-id="c26a3-133">Essa configuração só é necessária se você planeja testar seu projeto no editor do Unreal.</span><span class="sxs-lookup"><span data-stu-id="c26a3-133">This setting is only required if you plan to test your project in the Unreal editor.</span></span>

## <a name="creating-attenuation-objects"></a><span data-ttu-id="c26a3-134">Como criar objetos de Atenuação</span><span class="sxs-lookup"><span data-stu-id="c26a3-134">Creating Attenuation objects</span></span>

<span data-ttu-id="c26a3-135">Depois de instalar e configurar os plug-ins necessários:</span><span class="sxs-lookup"><span data-stu-id="c26a3-135">After you've installed and configured the necessary plugins:</span></span>
1. <span data-ttu-id="c26a3-136">Procure um ator de **Som Ambiente** na janela **Posicionar Atores** e arraste-o para a janela **Cena**.</span><span class="sxs-lookup"><span data-stu-id="c26a3-136">Search for an **Ambient Sound** actor in the **Place Actors** window and drag it into the **Scene** window.</span></span>

![Como adicionar o ator de som ambiente](images/unreal-spatial-audio-img-07.png)

2. <span data-ttu-id="c26a3-138">Torne o ator de **Som Ambiente** um filho de um elemento visual na cena.</span><span class="sxs-lookup"><span data-stu-id="c26a3-138">Make the **Ambient Sound** actor a child of a visual element in your scene.</span></span>
    * <span data-ttu-id="c26a3-139">Um ator de Som Ambiente não tem nenhuma representação visual por padrão; portanto, você só ouvirá um som da posição dele na cena.</span><span class="sxs-lookup"><span data-stu-id="c26a3-139">An Ambient Sound actor doesn't have any visual representation by default, so you'll only hear a sound from its position in the scene.</span></span> <span data-ttu-id="c26a3-140">A anexação dele a um elemento visual permite que você veja e mova o ator como qualquer outro ativo.</span><span class="sxs-lookup"><span data-stu-id="c26a3-140">Attaching it to a visual element let's you see and move the actor like any other asset.</span></span>

3.  <span data-ttu-id="c26a3-141">Clique com o botão direito do mouse no **Navegador de Conteúdo** e selecione **Criar Ativo Avançado -> Sons -> Atenuação de Som**:</span><span class="sxs-lookup"><span data-stu-id="c26a3-141">Right-click on the **Content Browser** and selecting **Create Advanced Asset -> Sounds -> Sound Attenuation**:</span></span>

![Como criar um ativo de atenuação de som](images/unreal-spatial-audio-img-06.png)

4. <span data-ttu-id="c26a3-143">Clique com o botão direito do mouse no ativo de **Atenuação de Som** na janela **Navegador de Conteúdo** e selecione a opção **Editar** para abrir a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="c26a3-143">Right-click on the **Sound Attenuation** asset in the **Content Browser** window and select the **Edit** option to bring up the properties window.</span></span>
    * <span data-ttu-id="c26a3-144">Alterne o **Método de Espacialização** para **Binaural**.</span><span class="sxs-lookup"><span data-stu-id="c26a3-144">Switch the **Spatialization Method** to **Binaural**.</span></span>

![Definir o método de espacialização](images/unreal-spatial-audio-img-03.png)

5. <span data-ttu-id="c26a3-146">Selecione o ator de **Som Ambiente** e role a página para baixo até a seção **Atenuação** no painel **Detalhes**.</span><span class="sxs-lookup"><span data-stu-id="c26a3-146">Select the **Ambient Sound** actor and scroll down to the **Attenuation** section in the **Details** panel.</span></span>
    * <span data-ttu-id="c26a3-147">Defina a propriedade de **Configurações de Atenuação** como o ativo de **Atenuação de Som** criado.</span><span class="sxs-lookup"><span data-stu-id="c26a3-147">Set the **Attenuation Settings** property to the **Sound Attenuation** asset you created.</span></span>

![Definir a configuração de atenuação](images/unreal-spatial-audio-img-08.png)

6. <span data-ttu-id="c26a3-149">Defina o **Ativo de Som** que deseja anexar ao ator de Som Ambiente:</span><span class="sxs-lookup"><span data-stu-id="c26a3-149">Set the **Sound Asset** you want to attach to the Ambient Sound actor:</span></span>
    * <span data-ttu-id="c26a3-150">Atualize a propriedade **Som** do ator de Som Ambiente para especificar o arquivo SoundAsset a ser usado.</span><span class="sxs-lookup"><span data-stu-id="c26a3-150">Update the **Sound** property of the Ambient Sound actor to specify the SoundAsset file to use.</span></span>

![Definir o ativo de som](images/unreal-spatial-audio-img-09.png)

> [!NOTE]
> <span data-ttu-id="c26a3-152">O arquivo de SoundAsset precisa ser mono para ser espacializado com o plug-in do Microsoft Spatial Sound.</span><span class="sxs-lookup"><span data-stu-id="c26a3-152">The SoundAsset file needs to be mono to be spatialized with the Microsoft Spatial Sound plug-in.</span></span> <span data-ttu-id="c26a3-153">Encontre as propriedades do arquivo de som posicionando o cursor sobre o ativo na janela Navegador de Conteúdo, conforme mostrado na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="c26a3-153">You can find the sound file properties by hovering over the asset in the Content Browser window as shown in the screenshot below.</span></span>

![Novo ativo de atenuação de som](images/unreal-spatial-audio-img-10.png)

<span data-ttu-id="c26a3-155">Quando o ativo de som estiver configurado, o som ambiente poderá ser espacializado por meio do suporte de descarregamento de hardware dedicado do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c26a3-155">When the sound asset is configured, the ambient sound can be spatialized using the dedicated hardware offload support on HoloLens 2.</span></span>

## <a name="configuring-objects-for-spatialization"></a><span data-ttu-id="c26a3-156">Como configurar objetos para espacialização</span><span class="sxs-lookup"><span data-stu-id="c26a3-156">Configuring objects for spatialization</span></span>

<span data-ttu-id="c26a3-157">Trabalhar com áudio espacial significa que você é responsável pelo gerenciamento de como o som se comporta em um ambiente virtual.</span><span class="sxs-lookup"><span data-stu-id="c26a3-157">Working with spatial audio means you're in charge of managing how sound behaves in a virtual environment.</span></span> <span data-ttu-id="c26a3-158">Seu foco principal é a criação de objetos de som que parecem soar mais alto quando o usuário está próximo e mais baixo quando o usuário está distante.</span><span class="sxs-lookup"><span data-stu-id="c26a3-158">Your main focus is creating sound objects that appear louder when the user is close, and quieter when the user is far away.</span></span> <span data-ttu-id="c26a3-159">Isso é conhecido como atenuação de som, fazendo com que os sons pareçam como se estivessem posicionados em um local fixo.</span><span class="sxs-lookup"><span data-stu-id="c26a3-159">This is referred to as sound attenuation, making sounds appear as if they're positioned in a fixed spot.</span></span>

<span data-ttu-id="c26a3-160">Todos os objetos de atenuação são fornecidos com as configurações modificáveis de:</span><span class="sxs-lookup"><span data-stu-id="c26a3-160">All attenuation objects come with modifiable settings for:</span></span>
* <span data-ttu-id="c26a3-161">Distância</span><span class="sxs-lookup"><span data-stu-id="c26a3-161">Distance</span></span>
* <span data-ttu-id="c26a3-162">Espacialização</span><span class="sxs-lookup"><span data-stu-id="c26a3-162">Spatialization</span></span>
* <span data-ttu-id="c26a3-163">Absorção de ar</span><span class="sxs-lookup"><span data-stu-id="c26a3-163">Air Absorption</span></span>
* <span data-ttu-id="c26a3-164">Foco do ouvinte</span><span class="sxs-lookup"><span data-stu-id="c26a3-164">Listener Focus</span></span>
* <span data-ttu-id="c26a3-165">Envio de reverberação</span><span class="sxs-lookup"><span data-stu-id="c26a3-165">Reverb Send</span></span>
* <span data-ttu-id="c26a3-166">Oclusão</span><span class="sxs-lookup"><span data-stu-id="c26a3-166">Occlusion</span></span>

<span data-ttu-id="c26a3-167">O artigo [Atenuação de som no Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) traz detalhes e especificações de implementação sobre cada um desses tópicos.</span><span class="sxs-lookup"><span data-stu-id="c26a3-167">[Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) has details and implementation specifics on each of these topics.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="c26a3-168">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="c26a3-168">Next Development Checkpoint</span></span>

<span data-ttu-id="c26a3-169">Se está seguindo o percurso de desenvolvimento do Unreal que estabelecemos, você está no meio da exploração dos principais blocos de construção do MRTK.</span><span class="sxs-lookup"><span data-stu-id="c26a3-169">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="c26a3-170">Deste ponto, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="c26a3-170">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c26a3-171">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="c26a3-171">Voice input</span></span>](unreal-voice-input.md)

<span data-ttu-id="c26a3-172">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="c26a3-172">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c26a3-173">Câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="c26a3-173">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="c26a3-174">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="c26a3-174">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="see-also"></a><span data-ttu-id="c26a3-175">Veja também</span><span class="sxs-lookup"><span data-stu-id="c26a3-175">See also</span></span>
* [<span data-ttu-id="c26a3-176">Som espacial</span><span class="sxs-lookup"><span data-stu-id="c26a3-176">Spatial Sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [<span data-ttu-id="c26a3-177">Design de som espacial</span><span class="sxs-lookup"><span data-stu-id="c26a3-177">Spatial Sound Design</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [<span data-ttu-id="c26a3-178">MR Espacial 220: som espacial</span><span class="sxs-lookup"><span data-stu-id="c26a3-178">MR Spatial 220: Spatial sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/holograms-220)
