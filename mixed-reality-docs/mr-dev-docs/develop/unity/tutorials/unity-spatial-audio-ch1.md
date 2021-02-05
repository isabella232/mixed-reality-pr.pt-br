---
title: Tutoriais de áudio espacial-1. Adicionando áudio espacial ao seu projeto
description: Adicione o plug-in do Microsoft Spatializer ao seu projeto do Unity para acessar o descarregamento de hardware do HoloLens 2 HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial, MRTK, kit de ferramentas de realidade mista, UWP, Windows 10, HRTF, função de transferência relacionada ao cabeçalho, reverberação, Microsoft Spatializer
ms.openlocfilehash: 7ed1355e3c522fcd94a96dd761a8a9ebb01c4c4c
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590038"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="03ccc-105">1. adicionando áudio espacial ao seu projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="03ccc-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="03ccc-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="03ccc-106">Overview</span></span>

<span data-ttu-id="03ccc-107">Bem-vindo ao tutorial de áudio espacial do Unity no HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="03ccc-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="03ccc-108">Nesta série de tutoriais, você aprenderá a usar o descarregamento de HRTF (função de transferência relacionada ao cabeçalho) no HoloLens 2 e como habilitar o reverberador ao usar o descarregamento do HRTF.</span><span class="sxs-lookup"><span data-stu-id="03ccc-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="03ccc-109">O [repositório GitHub do Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) tem um projeto de Unity concluído desta sequência de tutorial.</span><span class="sxs-lookup"><span data-stu-id="03ccc-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="03ccc-110">Para entender o que isso significa para espacialar sons usando tecnologias de espacial com base em HRTF e recomendações para quando puder ser útil, consulte [design de som espacial](/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="03ccc-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="03ccc-111">O que é descarregamento de HRTF?</span><span class="sxs-lookup"><span data-stu-id="03ccc-111">What is HRTF offload?</span></span>

<span data-ttu-id="03ccc-112">O processamento de áudio usando algoritmos baseados em HRTF exige uma grande quantidade de computação especializada.</span><span class="sxs-lookup"><span data-stu-id="03ccc-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="03ccc-113">O HoloLens 2 inclui um hardware dedicado que pode ser utilizado para evitar sobrecarregar o processador de aplicativos, portanto, "descarregando" o processamento de algoritmos baseados em HRTF.</span><span class="sxs-lookup"><span data-stu-id="03ccc-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="03ccc-114">O plug-in do Microsoft spatializer fornece uma maneira fácil de seu aplicativo aproveitar o hardware dedicado do HRTF para que seu aplicativo possa usar mais do processador de aplicativos para operações que não sejam de áudio espacial.</span><span class="sxs-lookup"><span data-stu-id="03ccc-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="03ccc-115">Objetivos</span><span class="sxs-lookup"><span data-stu-id="03ccc-115">Objectives</span></span>

* <span data-ttu-id="03ccc-116">Importando e habilitando o plug-in Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="03ccc-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="03ccc-117">Habilitando o áudio espacial em sua estação de trabalho do desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="03ccc-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="03ccc-118">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="03ccc-118">Prerequisites</span></span>

* <span data-ttu-id="03ccc-119">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="03ccc-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="03ccc-120">Conhecimento básico de programação em C#</span><span class="sxs-lookup"><span data-stu-id="03ccc-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="03ccc-121">Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="03ccc-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="03ccc-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019 LTS montado e o módulo Suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="03ccc-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="03ccc-123">É **altamente recomendável** concluir a série de tutoriais de [introdução](mr-learning-base-01.md) ou ter alguma experiência prévia básica com o Unity e o MRTK antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="03ccc-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="03ccc-124">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="03ccc-124">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="03ccc-125">Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="03ccc-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="03ccc-126">Como criar e preparar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="03ccc-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="03ccc-127">Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.</span><span class="sxs-lookup"><span data-stu-id="03ccc-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="03ccc-128">Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="03ccc-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="03ccc-129">[Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*</span><span class="sxs-lookup"><span data-stu-id="03ccc-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="03ccc-130">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="03ccc-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="03ccc-131">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="03ccc-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="03ccc-132">Como importar o Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="03ccc-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="03ccc-133">Como configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="03ccc-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="03ccc-134">[Criar e definir a cena](mr-learning-base-02.md#creating-and-configuring-the-scene) e dar à cena um nome adequado, por exemplo, *SpatialAudio*</span><span class="sxs-lookup"><span data-stu-id="03ccc-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="03ccc-135">Em seguida, siga as instruções de [alteração da opção de exibição de conscientização espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para garantir que o perfil de configuração MRTK para sua cena seja **DefaultHoloLens2ConfigurationProfile** e altere as opções de exibição para a malha de conscientização espacial para **oclusão**.</span><span class="sxs-lookup"><span data-stu-id="03ccc-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="03ccc-136">Adicionando o Microsoft Spatializer ao projeto</span><span class="sxs-lookup"><span data-stu-id="03ccc-136">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="03ccc-137">Baixe e importe o Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. SpatialAudio. Spatializer. Unity. 1.0.18. unitypackage </a></span><span class="sxs-lookup"><span data-stu-id="03ccc-137">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="03ccc-138">Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções de [importação dos ativos do tutorial](mr-learning-base-04.md#importing-the-tutorial-assets) .</span><span class="sxs-lookup"><span data-stu-id="03ccc-138">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="03ccc-139">Habilitar o plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="03ccc-139">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="03ccc-140">Depois de importar o **Microsoft Spatializer** , você precisa habilitá-lo.</span><span class="sxs-lookup"><span data-stu-id="03ccc-140">After importing the **Microsoft Spatializer** you need to enable it.</span></span> <span data-ttu-id="03ccc-141">Abra o **editar > configurações do projeto-> áudio** e altere o **plug-in Spatializer** para "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="03ccc-141">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![Configurações do projeto mostrando o plug-in spatializer](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="03ccc-143">Habilitar áudio espacial em sua estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="03ccc-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="03ccc-144">Em versões de área de trabalho do Windows, o áudio espacial é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="03ccc-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="03ccc-145">Habilite-o clicando com o botão direito do mouse no ícone de volume na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="03ccc-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="03ccc-146">Para obter a melhor representação do que você ouvirá no HoloLens 2, escolha **som espacial-> Windows Sonic para fones de ouvido**.</span><span class="sxs-lookup"><span data-stu-id="03ccc-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Configurações de áudio espacial da área de trabalho](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="03ccc-148">Essa configuração só será necessária se você planeja testar seu projeto no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="03ccc-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="03ccc-149">Parabéns</span><span class="sxs-lookup"><span data-stu-id="03ccc-149">Congratulations</span></span>

<span data-ttu-id="03ccc-150">Neste tutorial, você aprenderá a importar e habilitar o plug-in Microsoft Spatializer e também a habilitar o áudio espacial em sua estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="03ccc-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="03ccc-151">No próximo tutorial, você aprenderá a adicionar áudio espacial no projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="03ccc-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="03ccc-152">Próximo tutorial: 2. isespacialando sons de interação do botão</span><span class="sxs-lookup"><span data-stu-id="03ccc-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
