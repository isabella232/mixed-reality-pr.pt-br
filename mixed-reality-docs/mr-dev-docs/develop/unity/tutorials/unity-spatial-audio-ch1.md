---
title: Tutoriais de áudio espacial-1. Adicionando áudio espacial ao seu projeto
description: Adicione o plug-in do Microsoft Spatializer ao seu projeto do Unity para acessar o descarregamento de hardware do HoloLens 2 HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer
ms.openlocfilehash: 112531a3248461a5b380ad4b93de34545a2f2c3f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403357"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="36c77-105">1. adicionando áudio espacial ao seu projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="36c77-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="36c77-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="36c77-106">Overview</span></span>

<span data-ttu-id="36c77-107">Bem-vindo ao tutorial de áudio espacial do Unity no HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="36c77-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="36c77-108">Nesta série de tutoriais, você aprenderá a usar o descarregamento de HRTF (função de transferência relacionada ao cabeçalho) no HoloLens 2 e como habilitar o reverberador ao usar o descarregamento do HRTF.</span><span class="sxs-lookup"><span data-stu-id="36c77-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="36c77-109">O [repositório GitHub do Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) tem um projeto de Unity concluído desta sequência de tutorial.</span><span class="sxs-lookup"><span data-stu-id="36c77-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="36c77-110">Para entender o que isso significa para espacialar sons usando tecnologias de espacial com base em HRTF e recomendações para quando puder ser útil, consulte [design de som espacial](/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="36c77-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="36c77-111">O que é descarregamento de HRTF?</span><span class="sxs-lookup"><span data-stu-id="36c77-111">What is HRTF offload?</span></span>

<span data-ttu-id="36c77-112">O processamento de áudio usando algoritmos baseados em HRTF exige uma grande quantidade de computação especializada.</span><span class="sxs-lookup"><span data-stu-id="36c77-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="36c77-113">O HoloLens 2 inclui um hardware dedicado que pode ser utilizado para evitar sobrecarregar o processador de aplicativos, portanto, "descarregando" o processamento de algoritmos baseados em HRTF.</span><span class="sxs-lookup"><span data-stu-id="36c77-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="36c77-114">O plug-in do Microsoft spatializer fornece uma maneira fácil de seu aplicativo aproveitar o hardware dedicado do HRTF para que seu aplicativo possa usar mais do processador de aplicativos para operações que não sejam de áudio espacial.</span><span class="sxs-lookup"><span data-stu-id="36c77-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="36c77-115">Objetivos</span><span class="sxs-lookup"><span data-stu-id="36c77-115">Objectives</span></span>

* <span data-ttu-id="36c77-116">Importando e habilitando o plug-in Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="36c77-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="36c77-117">Habilitando o áudio espacial em sua estação de trabalho do desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="36c77-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="36c77-118">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="36c77-118">Prerequisites</span></span>

* <span data-ttu-id="36c77-119">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="36c77-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="36c77-120">Conhecimento básico de programação em C#</span><span class="sxs-lookup"><span data-stu-id="36c77-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="36c77-121">Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="36c77-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="36c77-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com Unity 2020/2019 LTS montado e o módulo de suporte do Build plataforma universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="36c77-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="36c77-123">É **altamente recomendável** concluir a série de tutoriais de [introdução](mr-learning-base-01.md) ou ter alguma experiência prévia básica com o Unity e o MRTK antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="36c77-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!Important]
> <span data-ttu-id="36c77-124">Esta série de tutoriais dá suporte a Unity 2020 LTS (atualmente 2020.3. x) se você estiver usando o plug-in Open XR ou Windows XR e também o Unity 2019 LTS (atualmente 2019.4. x) se estiver usando o plug-in do WSA ou do Windows XR herdado.</span><span class="sxs-lookup"><span data-stu-id="36c77-124">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="36c77-125">Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="36c77-125">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="36c77-126">Como criar e preparar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="36c77-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="36c77-127">Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.</span><span class="sxs-lookup"><span data-stu-id="36c77-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="36c77-128">Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="36c77-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="36c77-129">[Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*</span><span class="sxs-lookup"><span data-stu-id="36c77-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="36c77-130">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="36c77-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="36c77-131">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="36c77-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="36c77-132">Importando o kit de ferramentas da realidade mista e Configurando o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="36c77-132">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)

1. <span data-ttu-id="36c77-133">[Criar e configurar a cena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) e dar à cena um nome adequado, por exemplo, *SpatialAudio*</span><span class="sxs-lookup"><span data-stu-id="36c77-133">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="36c77-134">Em seguida, siga as instruções de [alteração da opção de exibição de conscientização espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para garantir que o perfil de configuração MRTK para sua cena seja **DefaultHoloLens2ConfigurationProfile** e altere as opções de exibição para a malha de conscientização espacial para **oclusão**.</span><span class="sxs-lookup"><span data-stu-id="36c77-134">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="36c77-135">Adicionando o Microsoft Spatializer ao projeto</span><span class="sxs-lookup"><span data-stu-id="36c77-135">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="36c77-136">Baixe e importe o Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. SpatialAudio. Spatializer. Unity. 1.0.18. unitypackage </a></span><span class="sxs-lookup"><span data-stu-id="36c77-136">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="36c77-137">Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções [Como importar os ativos de tutorial](mr-learning-base-02.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="36c77-137">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-02.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="36c77-138">Habilitar o plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="36c77-138">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="36c77-139">Depois de importar o Microsoft Spatializer para seu projeto do Unity, a janela **configuradora do projeto MRTK** será exibida, use a lista suspensa de **Spatializer de áudio** para selecionar o **Microsoft Spatializer** e, em seguida, clique no botão Aplicar para aplicar a configuração:</span><span class="sxs-lookup"><span data-stu-id="36c77-139">Once you import the Microsoft Spatializer into your unity project, **MRTK Project Configurator** window will appear, use the **Audio spatializer** dropdown to select the **Microsoft Spatializer**, then click the Apply button to apply the setting:</span></span>

![Configurador de projeto MRTK](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

<span data-ttu-id="36c77-141">Você também pode habilitar manualmente o Microsoft Spatializer: Open **Edit-> Project Settings-> Audio** e alterar o **plug-in Spatializer** para "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="36c77-141">you can also manually enable the Microsoft Spatializer: Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![Configurações do projeto mostrando o plug-in spatializer](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="36c77-143">Habilitar áudio espacial em sua estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="36c77-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="36c77-144">Em versões de área de trabalho do Windows, o áudio espacial é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="36c77-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="36c77-145">Habilite-o clicando com o botão direito do mouse no ícone de volume na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="36c77-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="36c77-146">Para obter a melhor representação do que você ouvirá no HoloLens 2, escolha **som espacial-> Windows Sonic para fones de ouvido**.</span><span class="sxs-lookup"><span data-stu-id="36c77-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Configurações de áudio espacial da área de trabalho](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> <span data-ttu-id="36c77-148">Essa configuração só será necessária se você planeja testar seu projeto no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="36c77-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="36c77-149">Parabéns</span><span class="sxs-lookup"><span data-stu-id="36c77-149">Congratulations</span></span>

<span data-ttu-id="36c77-150">Neste tutorial, você aprenderá a importar e habilitar o plug-in Microsoft Spatializer e também a habilitar o áudio espacial em sua estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="36c77-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="36c77-151">No próximo tutorial, você aprenderá a adicionar áudio espacial no projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="36c77-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="36c77-152">Próximo tutorial: 2. isespacialando sons de interação do botão</span><span class="sxs-lookup"><span data-stu-id="36c77-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
