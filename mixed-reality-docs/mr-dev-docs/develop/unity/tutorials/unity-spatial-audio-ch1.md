---
title: Adicionando áudio espacial ao seu projeto
description: Adicione o plug-in do Microsoft Spatializer ao seu projeto do Unity para acessar o descarregamento de hardware do HoloLens 2 HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer
ms.openlocfilehash: 80bf19e8a091bd241e28afff0a42c13ca72e1d45
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007466"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="b740b-104">Adicionando áudio espacial ao seu projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="b740b-104">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="b740b-105">Bem-vindo ao tutorial de áudio espacial do Unity no HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="b740b-105">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="b740b-106">Esta sequência de tutorial mostra:</span><span class="sxs-lookup"><span data-stu-id="b740b-106">This tutorial sequence shows:</span></span>
* <span data-ttu-id="b740b-107">Como usar o descarregamento de função de transferência relacionada ao cabeçalho (HRTF) no HoloLens 2 no Unity</span><span class="sxs-lookup"><span data-stu-id="b740b-107">How to use head-related transfer function (HRTF) offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="b740b-108">Como habilitar o reverberador ao usar o descarregamento de HRTF</span><span class="sxs-lookup"><span data-stu-id="b740b-108">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="b740b-109">O [repositório GitHub do Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) tem um projeto de Unity concluído desta sequência de tutorial.</span><span class="sxs-lookup"><span data-stu-id="b740b-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="b740b-110">Para obter uma compreensão sobre o que significa espacialar sons usando tecnologias de espacial com base em HRTF e recomendações para quando puder ser útil, consulte [design de som espacial](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="b740b-110">For an understanding about what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="b740b-111">O que é descarregamento de HRTF?</span><span class="sxs-lookup"><span data-stu-id="b740b-111">What is HRTF offload?</span></span>

<span data-ttu-id="b740b-112">O processamento de áudio usando algoritmos baseados em HRTF exige uma grande quantidade de computação especializada.</span><span class="sxs-lookup"><span data-stu-id="b740b-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="b740b-113">O HoloLens 2 inclui um hardware dedicado que pode ser utilizado para evitar sobrecarregar o processador de aplicativos, portanto, "descarregando" o processamento de algoritmos baseados em HRTF.</span><span class="sxs-lookup"><span data-stu-id="b740b-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="b740b-114">O plug-in do Microsoft spatializer fornece uma maneira fácil de seu aplicativo aproveitar o hardware dedicado do HRTF para que seu aplicativo possa usar mais do processador de aplicativos para operações que não sejam de áudio espacial.</span><span class="sxs-lookup"><span data-stu-id="b740b-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="b740b-115">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b740b-115">Objectives</span></span>

<span data-ttu-id="b740b-116">Neste primeiro capítulo, você vai:</span><span class="sxs-lookup"><span data-stu-id="b740b-116">In this first chapter, you'll:</span></span>
* <span data-ttu-id="b740b-117">Criar um projeto do Unity e importar MRTK</span><span class="sxs-lookup"><span data-stu-id="b740b-117">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="b740b-118">Importar o plug-in Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="b740b-118">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="b740b-119">Habilitar o plug-in Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="b740b-119">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="b740b-120">Habilitar o áudio espacial em sua estação de trabalho do desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="b740b-120">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="b740b-121">Criar um projeto e adicionar o NuGet para o Unity</span><span class="sxs-lookup"><span data-stu-id="b740b-121">Create a project and add NuGet for Unity</span></span>

<span data-ttu-id="b740b-122">Comece com um projeto do Unity vazio e, em seguida, adicione e configure o NuGet para o Unity:</span><span class="sxs-lookup"><span data-stu-id="b740b-122">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="b740b-123">Baixe o [NuGetForUnity. unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) mais recente</span><span class="sxs-lookup"><span data-stu-id="b740b-123">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="b740b-124">Na barra de menus do Unity, clique em **ativos-> importar pacote-> pacote personalizado...** e instale o pacote NuGetForUnity:</span><span class="sxs-lookup"><span data-stu-id="b740b-124">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![Importar pacote personalizado](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="b740b-126">Adicionar o pacote do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b740b-126">Add the Windows Mixed Reality package</span></span>

<span data-ttu-id="b740b-127">O suporte do Windows Mixed Reality no Unity 2019 e posterior está contido em um pacote opcional.</span><span class="sxs-lookup"><span data-stu-id="b740b-127">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="b740b-128">Para adicioná-lo ao seu projeto, abra o **Gerenciador de pacotes do > de janela** na barra de menus do Unity:</span><span class="sxs-lookup"><span data-stu-id="b740b-128">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![Menu do Gerenciador de pacotes](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="b740b-130">Em seguida, localize e instale o pacote do **Windows Mixed Reality** :</span><span class="sxs-lookup"><span data-stu-id="b740b-130">Then find and install the **Windows Mixed Reality** package:</span></span>

![Janela do Gerenciador de pacotes](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="b740b-132">Instalar o MRTK e o Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="b740b-132">Install MRTK and Microsoft Spatializer</span></span>

<span data-ttu-id="b740b-133">Usando o NuGet para Unity, instale os plug-ins MRTK e Microsoft Spatializer:</span><span class="sxs-lookup"><span data-stu-id="b740b-133">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="b740b-134">Na barra de menus do Unity, clique em **NuGet-> gerenciar pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b740b-134">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![Gerenciar pacotes NuGet](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="b740b-136">Na caixa de **pesquisa** , digite "Microsoft. MixedReality. Toolkit" e instale o pacote do MRTK Core: **Microsoft. MixedReality. Toolkit. Foundation**</span><span class="sxs-lookup"><span data-stu-id="b740b-136">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![Pacote NuGet do MRTK](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="b740b-138">O [pacote NuGet do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) tem detalhes e contexto adicionais.</span><span class="sxs-lookup"><span data-stu-id="b740b-138">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="b740b-139">Na caixa de **pesquisa** , digite "Microsoft. SpatialAudio" e instale o pacote do Microsoft Spatializer: **Microsoft. SpatialAudio. Spatializer. Unity**</span><span class="sxs-lookup"><span data-stu-id="b740b-139">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![NuGet do plugin Spatializer](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="b740b-141">Configurar o MRTK em seu projeto</span><span class="sxs-lookup"><span data-stu-id="b740b-141">Set up MRTK in your project</span></span>

1. <span data-ttu-id="b740b-142">Abra a janela configurações de Build acessando **arquivo-> configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="b740b-142">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="b740b-143">Selecione o _plataforma universal do Windows_ e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="b740b-143">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="b740b-144">Clique em **configurações do Player** na **janela criar** para abrir as propriedades **das configurações do Player** no painel **Inspetor** .</span><span class="sxs-lookup"><span data-stu-id="b740b-144">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="b740b-145">Em **configurações de XR**, marque a caixa de seleção **suporte à realidade virtual**</span><span class="sxs-lookup"><span data-stu-id="b740b-145">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="b740b-146">Em **configurações de XR**, altere o **modo de renderização de estéreo** para **passagem única com instância**.</span><span class="sxs-lookup"><span data-stu-id="b740b-146">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="b740b-147">Em **configurações de publicação**, marque a caixa de seleção **percepção espacial** na seção **recursos**</span><span class="sxs-lookup"><span data-stu-id="b740b-147">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="b740b-148">Na barra de menus, clique em **Kit de ferramentas de realidade misturada-> adicionar à cena e configurar..**</span><span class="sxs-lookup"><span data-stu-id="b740b-148">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="b740b-149">para adicionar MRTK à sua cena.</span><span class="sxs-lookup"><span data-stu-id="b740b-149">to add MRTK to your scene.</span></span>

<span data-ttu-id="b740b-150">Para obter diretrizes adicionais, incluindo como criar seu aplicativo e implantá-lo em um HoloLens 2, consulte [o capítulo 1 do módulo de base de aprendizado do Mr](../../../mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="b740b-150">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](../../../mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="b740b-151">Habilitar o plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="b740b-151">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="b740b-152">Habilite o plug-in **Microsoft Spatializer** .</span><span class="sxs-lookup"><span data-stu-id="b740b-152">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="b740b-153">Abra o **editar > configurações do projeto-> áudio** e altere o **plug-in Spatializer** para "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="b740b-153">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="b740b-154">A seção **áudio** das **configurações do projeto** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="b740b-154">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Configurações do projeto mostrando o plug-in spatializer](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="b740b-156">Habilitar áudio espacial em sua estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="b740b-156">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="b740b-157">Em versões de área de trabalho do Windows, o áudio espacial é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="b740b-157">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="b740b-158">Habilite-o clicando com o botão direito do mouse no ícone de volume na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="b740b-158">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="b740b-159">Para obter a melhor representação do que você ouvirá no HoloLens 2, escolha **som espacial-> Windows Sonic para fones de ouvido**.</span><span class="sxs-lookup"><span data-stu-id="b740b-159">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Configurações de áudio espacial da área de trabalho](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="b740b-161">Essa configuração só será necessária se você planeja testar seu projeto no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="b740b-161">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b740b-162">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b740b-162">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b740b-163">Capítulo 2 de áudio espacial do Unity</span><span class="sxs-lookup"><span data-stu-id="b740b-163">Unity spatial audio chapter 2</span></span>](unity-spatial-audio-ch2.md)

