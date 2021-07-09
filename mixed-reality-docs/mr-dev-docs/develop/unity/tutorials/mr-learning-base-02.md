---
title: Como inicializar o seu projeto e implantar o primeiro aplicativo
description: Este curso mostra como configurar seu projeto do Unity para o MRTK (Kit de Ferramentas de Realidade Misturada) e como implantá-lo no HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175969"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="3fbc1-104">2. Como inicializar o seu projeto e implantar o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="3fbc1-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="3fbc1-105">Neste tutorial, você aprenderá a criar um projeto do Unity, configurá-lo para o desenvolvimento do MRTK (Kit de Ferramentas de Realidade Misturada) e importar o MRTK.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-105">In this tutorial, you'll learn how to create a new Unity project, configure it for Mixed Reality Toolkit (MRTK) development, and import MRTK.</span></span> <span data-ttu-id="3fbc1-106">Você também aprenderá mais sobre como configurar, compilar e implantar uma cena básica do Unity do Visual Studio para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="3fbc1-107">Depois de implantá-la no HoloLens 2, você verá uma malha de mapeamento espacial que abrange as superfícies percebidas pelo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="3fbc1-108">Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="3fbc1-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3fbc1-109">Objectives</span></span>

* <span data-ttu-id="3fbc1-110">Saiba como configurar o Unity para o desenvolvimento no HoloLens</span><span class="sxs-lookup"><span data-stu-id="3fbc1-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="3fbc1-111">Saiba como criar e implantar o seu aplicativo no HoloLens</span><span class="sxs-lookup"><span data-stu-id="3fbc1-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="3fbc1-112">Experimente a malha de mapeamento espacial, as malhas de mão e o contador da taxa de quadros no dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3fbc1-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

### <a name="steps-overview"></a><span data-ttu-id="3fbc1-113">Visão geral das etapas</span><span class="sxs-lookup"><span data-stu-id="3fbc1-113">Steps overview</span></span>
:::row:::
    :::column:::
       <span data-ttu-id="3fbc1-114">![Visão Geral da Etapa 1](images/mr-learning-base/base-02-overview-step1.png) **1. Criar um novo projeto do Unity**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-114">![Overview Step 1](images/mr-learning-base/base-02-overview-step1.png) **1. Create a new Unity project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3fbc1-115">![Visão Geral da Etapa 2](images/mr-learning-base/base-02-overview-step2.png) **2. Importar o MRTK para o projeto**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-115">![Overview Step 2](images/mr-learning-base/base-02-overview-step2.png) **2. Import MRTK into the project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3fbc1-116">![Visão Geral da Etapa 3](images/mr-learning-base/base-02-overview-step3.png) **3. Configurar uma nova cena com o MRTK**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-116">![Overview Step 3](images/mr-learning-base/base-02-overview-step3.png) **3. Configure a new scene with MRTK**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       <span data-ttu-id="3fbc1-117">![Visão Geral da Etapa 4](images/mr-learning-base/base-02-overview-step4.png) **4. Compilar o Projeto do Unity**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-117">![Overview Step 4](images/mr-learning-base/base-02-overview-step4.png) **4. Build Unity Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3fbc1-118">![Visão Geral da Etapa 5](images/mr-learning-base/base-02-overview-step5.png) **5. Compilar o Projeto do UWP**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-118">![Overview Step 5](images/mr-learning-base/base-02-overview-step5.png) **5. Build UWP Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3fbc1-119">![Visão Geral da Etapa 6](images/mr-learning-base/base-02-overview-step6.png) **6. Executar o Projeto no Dispositivo**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-119">![Overview Step 6](images/mr-learning-base/base-02-overview-step6.png) **6. Run Project on the Device**</span></span>
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a><span data-ttu-id="3fbc1-120">Como criar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="3fbc1-120">Creating the Unity project</span></span>

<span data-ttu-id="3fbc1-121">Inicie o **Hub do Unity**, selecione a guia **Projetos** e clique na **seta para baixo** ao lado do botão **Novo**:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

<span data-ttu-id="3fbc1-122">Na lista suspensa, selecione a **versão** do Unity especificada em [Pré-requisitos](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="3fbc1-122">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> <span data-ttu-id="3fbc1-123">Se a versão específica do Unity não estiver disponível no Hub do Unity, você poderá iniciar a instalação em <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Arquivos de Download</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-123">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="3fbc1-124">Na janela Criar um novo projeto:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-124">In the Create a new project window:</span></span>

* <span data-ttu-id="3fbc1-125">Verifique se **Modelos** está definido como **3D**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-125">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="3fbc1-126">Insira um **Nome de Projeto** adequado, por exemplo, _Tutoriais do MRTK_</span><span class="sxs-lookup"><span data-stu-id="3fbc1-126">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="3fbc1-127">Escolha um **Local** adequado para armazenar seu projeto, por exemplo, _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="3fbc1-127">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="3fbc1-128">Clique no botão **Criar** para criar e iniciar o novo projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="3fbc1-128">Click the **Create** button to create and launch your new Unity project</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> <span data-ttu-id="3fbc1-129">Ao trabalhar no Windows, há um limite de MAX_PATH de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-129">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="3fbc1-130">Consequentemente, você deve salvar o projeto do Unity próximo à raiz da unidade.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-130">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="3fbc1-131">Aguarde até que o Unity crie o projeto:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-131">Wait for Unity to create the project:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a><span data-ttu-id="3fbc1-132">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="3fbc1-132">Switching the build platform</span></span>

<span data-ttu-id="3fbc1-133">No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-133">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Caminho do menu Configurações de Build... do Unity](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="3fbc1-135">Na janela Configurações de Build, selecione **Plataforma Universal do Windows** e:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-135">In the Build Settings window, select **Universal Windows Platform** and:</span></span>

1. <span data-ttu-id="3fbc1-136">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-136">Set **Target device** to **HoloLens**</span></span>
2. <span data-ttu-id="3fbc1-137">Defina a **Arquitetura** como **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-137">Set **Architecture** to **ARM 64**</span></span> 
3. <span data-ttu-id="3fbc1-138">Defina **Tipo de Build** como **Projeto D3D**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-138">Set **Build Type** to **D3D Project**</span></span>
4. <span data-ttu-id="3fbc1-139">Defina **Versão do SDK de destino** como **Última instalação**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-139">Set **Target SDK Version** to **Latest Installed**</span></span>
5. <span data-ttu-id="3fbc1-140">Defina **Versão Mínima da Plataforma** como **10.0.1024.0**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-140">Set **Minimum Platform Version** to **10.0.1024.0**</span></span>
6. <span data-ttu-id="3fbc1-141">Defina **Versão do Visual Studio** como **Instalação mais recente**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-141">Set **Visual Studio Version** to **Latest installed**</span></span>
7. <span data-ttu-id="3fbc1-142">Defina **Compilar e executar em** como **Dispositivo USB**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-142">Set **Build and Run on** to **USB Device**</span></span>
8. <span data-ttu-id="3fbc1-143">Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar</span><span class="sxs-lookup"><span data-stu-id="3fbc1-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9. <span data-ttu-id="3fbc1-144">Pressione o botão Alternar Plataforma</span><span class="sxs-lookup"><span data-stu-id="3fbc1-144">Click the Switch Platform button</span></span>

![Configurações de Build do Unity com conjunto de configurações da Plataforma Universal do Windows](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="3fbc1-146">Aguarde até que o Unity termine de mudar a plataforma:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-146">Wait for Unity to finish switching the platform:</span></span>

![Alternância de plataforma do Unity em andamento](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

<span data-ttu-id="3fbc1-148">Quando o Unity terminar de alternar a plataforma, clique no ícone **x** para fechar a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-148">When Unity has finished switching the platform, click the  **x** icon to close the Build Settings window.</span></span>

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a><span data-ttu-id="3fbc1-149">Como importar o Kit de ferramentas de Realidade Misturada e configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="3fbc1-149">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>

<span data-ttu-id="3fbc1-150">Para importar o Kit de Ferramentas de Realidade Misturada no projeto do Unity, você terá que usar a [Ferramenta de Recursos da Realidade Misturada](../welcome-to-mr-feature-tool.md) que permite aos desenvolvedores descobrir, atualizar e adicionar pacotes de recursos de Realidade Misturada a projetos do Unity.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-150">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="3fbc1-151">Você pode pesquisar pacotes por nome ou categoria, ver as respectivas dependências e, até mesmo, ver as alterações propostas no arquivo de manifesto dos seus projetos antes da importação.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-151">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="3fbc1-152">Baixe a última versão da Ferramenta de Recursos da Realidade Misturada no [Centro de Download da Microsoft](https://aka.ms/MRFeatureTool). Quando o download for concluído, descompacte o arquivo e salve-o na sua área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-152">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="3fbc1-153">Para executar a Ferramenta de Recursos da Realidade Misturada, instale o [runtime do .NET 5.0](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)</span><span class="sxs-lookup"><span data-stu-id="3fbc1-153">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)</span></span>

<span data-ttu-id="3fbc1-154">Abra o arquivo executável **MixedRealityFeatureTool** na pasta baixada para iniciar a Ferramenta de Recursos da Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-154">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="3fbc1-155">Como criar a cena e configurar o MRTK</span><span class="sxs-lookup"><span data-stu-id="3fbc1-155">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="3fbc1-156">No menu do Unity, selecione **Arquivo** > **Nova Cena**:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-156">In the Unity menu, select **File** > **New Scene**:</span></span>

![Caminho do menu Nova Cena do Unity](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="3fbc1-158">Na janela **Nova Cena**, selecione **Básico (Interno)** e clique em **criar** para criar uma nova cena:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-158">In the **New Scene** window select **Basic (Built-in)** and click on **create** to create a new scene:</span></span>

![Janela Nova Cena do Unity](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> <span data-ttu-id="3fbc1-160">A captura de tela acima é da Versão 2020 do Unity. Se você estiver usando o Unity 2019, ao clicar em **criar**, uma nova cena vazia será criada.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-160">Above screenshot is from Unity Version 2020, if you are using Unity 2019 when you click on **create** a new empty scene will be created.</span></span>

<span data-ttu-id="3fbc1-161">No menu do Unity, selecione **Realidade Misturada** > **Kit de Ferramentas** > **Adicionar à Cena e Configurar...** para adicionar o MRTK à cena atual:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-161">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Caminho do menu Adicionar à Cena e Configurar... do Unity](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="3fbc1-163">Com o objeto **MixedRealityToolkit** selecionado na janela Hierarquia, na janela Inspetor, verifique se o perfil de configuração **MixedRealityToolkit** está definido como **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-163">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit do Unity com DefaultMixedRealityTookitConfigurationProfile selecionado](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="3fbc1-165">No menu do Unity, selecione **Arquivo** > **Salvar Como...** para abrir a janela Salvar Cena:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-165">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Caminho do menu Salvar como... do Unity](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="3fbc1-167">Salve a cena no projeto em **Ativos** > **Cenas**.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-167">Save the scene in you project under **Asset** > **Scenes**.</span></span>

![Janela de prompt Salvar para salvar a cena do Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a><span data-ttu-id="3fbc1-169">Adicionando interação à mão a um objeto</span><span class="sxs-lookup"><span data-stu-id="3fbc1-169">Adding hand interaction to an object</span></span>

<span data-ttu-id="3fbc1-170">No menu do Unity, selecione **GameObject** > **Objeto 3D** > **Cubo** para adicionar um objeto de cubo à cena.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-170">In the Unity menu, select **GameObject** > **3D Object** > **Cube** to add a cube object to the scene.</span></span>

![Adicionando um cubo à cena](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="3fbc1-172">Clique no objeto **Cubo** na janela Hierarquia, e na janela Inspetor configure o componente **Transformar** da seguinte forma</span><span class="sxs-lookup"><span data-stu-id="3fbc1-172">Click the **Cube** object in the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="3fbc1-173">**Posição**: X = 0, Y = -0.1, Z = 0,5</span><span class="sxs-lookup"><span data-stu-id="3fbc1-173">**Position**: X = 0, Y = -0.1, Z = 0.5</span></span>
* <span data-ttu-id="3fbc1-174">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="3fbc1-174">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="3fbc1-175">**Escala**: X = 0,1, Y = 0,1, Z = 0,1</span><span class="sxs-lookup"><span data-stu-id="3fbc1-175">**Scale**: X = 0.1, Y = 0.1, Z = 0.1</span></span>

<span data-ttu-id="3fbc1-176">1 unidade Unity é 1 metro.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-176">1 Unity unit is 1 meter.</span></span> <span data-ttu-id="3fbc1-177">Atualizamos o tamanho do cubo para 10x10x10 cm, posicionado a 50cm da posição do headset (0, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="3fbc1-177">We have updated cube's size to 10x10x10 cm, placed at 50cm from the headset position (0,0,0).</span></span> <span data-ttu-id="3fbc1-178">10cm abaixo do nível dos olhos para uma interação confortável.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-178">10cm below the eye level for comfortable interaction.</span></span> 

<span data-ttu-id="3fbc1-179">Se você usar a escala padrão (1, 1, 1), o cubo ficará muito grande.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-179">If you use the default scale (1,1,1), the cube will be too big.</span></span> <span data-ttu-id="3fbc1-180">Se você usar a posição padrão (0, 0, 0), o cubo será colocado na mesma posição que o headset, e você não poderá vê-lo até que você se mova para trás.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-180">If you use the default position (0,0,0), the cube will be placed at the same position as your headset and you won't be able to see it until you move backward.</span></span>

![Ajustando informações de transformação](images/mr-learning-base/base-02-section8-step1-1b.png)

<span data-ttu-id="3fbc1-182">Para aumentar o foco nos objetos da cena, você pode clicar duas vezes no objeto **Cubo** e aumentar levemente o zoom de novo.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-182">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again.</span></span> <span data-ttu-id="3fbc1-183">Ou você pode usar a tecla F para aplicar zoom e focar no objeto.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-183">Or you can use F key to zoom and focus on the object.</span></span>

<span data-ttu-id="3fbc1-184">Para interagir e pegar um objeto com as mãos acompanhadas, o objeto deve ter:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-184">To interact and grab an object with tracked hands, the object must have:</span></span>
 * <span data-ttu-id="3fbc1-185">Componente colisor, como **Colisor de Caixa** (o cubo do Unity já tem um Colisor de Caixa por padrão)</span><span class="sxs-lookup"><span data-stu-id="3fbc1-185">Collider component such as **Box Collider** (Unity's cube already has a Box Collider by default)</span></span>
 * <span data-ttu-id="3fbc1-186">Componente **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-186">**Object Manipulator (Script)** component</span></span>
 * <span data-ttu-id="3fbc1-187">Componente **NearInteractionGrabbable(Script)**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-187">**NearInteractionGrabbable(Script)** component</span></span>

<span data-ttu-id="3fbc1-188">O script **ObjectManipulator** do MRTK torna um objeto móvel, dimensionável e giratório usando uma ou as duas mãos.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-188">MRTK's **ObjectManipulator** script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="3fbc1-189">Esse script dá suporte ao modelo de entrada de manipulação direta, pois permite que o usuário toque os hologramas diretamente com as mãos.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-189">This script supports the direct manipulation input model as the script enables the user to touch holograms directly with their hands.</span></span>

<span data-ttu-id="3fbc1-190">Para adicionar o script de Manipulador de Objetos ao objeto Cubo, mantenha o **Cubo** selecionado na janela Hierarquia, clique no botão **Adicionar Componente** na janela Inspetor e, em seguida, pesquise e selecione o script **Manipulador de Objetos**.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-190">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![Como adicionar o Manipulador de Objetos ao Cubo](images/mr-learning-base/base-02-section8-step1-2.PNG)

<span data-ttu-id="3fbc1-192">Repita o mesmo procedimento para adicionar o **script de Interação Próxima com Objeto Segurável** ao Cubo</span><span class="sxs-lookup"><span data-stu-id="3fbc1-192">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![Como adicionar Interação Próxima com Objeto Segurável ao Cubo](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="3fbc1-194">Quando você adiciona um Object Manipulator (Script), nesse caso, o Constraint Manager (Script) é adicionado automaticamente porque o Object Manipulator (Script) depende dele.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-194">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a><span data-ttu-id="3fbc1-195">Testando seu aplicativo no editor do Unity com a simulação de entrada do MRTK</span><span class="sxs-lookup"><span data-stu-id="3fbc1-195">Testing your application in Unity editor with MRTK input simulation</span></span>

<span data-ttu-id="3fbc1-196">Com a simulação de entrada do MRTK, você pode testar vários tipos de interações no editor do Unity sem compilar e implantar em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-196">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="3fbc1-197">Isso permite que você itere rapidamente suas ideias no processo de design e desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-197">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="3fbc1-198">Use combinações de teclado e mouse para controlar as entradas simuladas.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-198">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="3fbc1-199">Clique no botão reproduzir e insira o modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-199">Click the play button and enter the play mode.</span></span> <span data-ttu-id="3fbc1-200">Mantenha pressionada a tecla **Shift da Esquerda** ou a tecla **Espaço** para exibir o controlador (mãos simuladas). Você pode mover o controlador com o mouse e usar o botão de rolagem para aproximá-lo ou afastá-lo da câmera.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-200">Hold the **Left Shift** or **Space** key to bring up the controller (simulated hands), Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="3fbc1-201">Com o ponteiro sobre o Cubo, mantenha pressionado o **botão esquerdo do mouse** para segurar o objeto Cubo.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-201">Once the pointer is on the Cube press and hold **Left Mouse Button** to grab the Cube object.</span></span>

* <span data-ttu-id="3fbc1-202">Pressione as teclas **W, A, S, D, Q, E** para mover a câmera.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-202">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="3fbc1-203">Mantenha o **Botão direito do mouse** pressionado e mova o mouse para examinar.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-203">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="3fbc1-204">Para exibir as mãos simuladas, pressione **Barra de espaço (à direita)** ou **tecla SHIFT esquerda**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-204">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="3fbc1-205">Para manter as mãos simuladas no modo de exibição, pressione as teclas **T** ou **Y**</span><span class="sxs-lookup"><span data-stu-id="3fbc1-205">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="3fbc1-206">Para girar as mãos simuladas, pressione e mantenha pressionada a tecla **Ctrl** e mova o mouse</span><span class="sxs-lookup"><span data-stu-id="3fbc1-206">To rotate simulated hands, press and hold **Ctrl** key and move mouse</span></span>

![Modo de Jogo](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="3fbc1-208">Como criar o aplicativo para o seu HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3fbc1-208">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="3fbc1-209">1. Compilar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="3fbc1-209">1. Build the Unity project</span></span>

<span data-ttu-id="3fbc1-210">No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-210">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="3fbc1-211">Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar sua cena atual à lista **Cenas no Build** e clique no botão **Build** para abrir a janela Compilar Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-211">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Janela Configurações de Build do Unity com o UWP selecionado](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="3fbc1-213">Na janela Compilar Plataforma Universal do Windows, escolha um local adequado para armazenar seu build, por exemplo, _D:\MixedRealityLearning\Builds_, crie uma nova pasta e dê a ela um nome adequado, por exemplo, _GettingStarted_ e, em seguida, clique no botão **Selecionar Pasta** para iniciar o processo de build:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-213">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Janela Configurações de Build do Unity com a janela de prompt Selecionar Pasta](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="3fbc1-215">Aguarde até que o Unity conclua o processo de build:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-215">Wait for Unity to finish the build process:</span></span>

![Processo de build do Unity em andamento](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="3fbc1-217">2. Compilar e implantar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3fbc1-217">2. Build and deploy the application</span></span>

<span data-ttu-id="3fbc1-218">Quando o processo de build for concluído, o Unity solicitará que o Explorador de Arquivos do Windows abra a localização em que você armazenou o build.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-218">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="3fbc1-219">Navegue dentro da pasta e clique duas vezes no arquivo da solução para abri-lo no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-219">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Windows Explorer com a solução do Visual Studio recém-criada selecionada](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="3fbc1-221">Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar-se de que você tenha todos os componentes de pré-requisitos na documentação **[Instalar as Ferramentas](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="3fbc1-221">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="3fbc1-222">Configure o Visual Studio para o HoloLens selecionando a configuração **Mestre** ou **Versão**, a arquitetura **ARM64** e o **Dispositivo** como destino:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-222">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio configurado para implantação no HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="3fbc1-224">Se você estiver implantando no HoloLens (1ª geração), selecione a arquitetura **x86**.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-224">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="3fbc1-225">Para o HoloLens, você normalmente criará para a arquitetura ARM.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-225">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="3fbc1-226">No entanto, há um <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conhecido</strong></a> no Unity 2019.3 que causa erros ao selecionar o ARM como a arquitetura de build no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-226">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="3fbc1-227">A solução alternativa recomendada é criar para o ARM64.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-227">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="3fbc1-228">Se essa não for uma opção, acesse **Editar > Configurações de Projeto > Player > Outras Configurações** e desabilite **Trabalhos Gráficos**.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-228">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="3fbc1-229">Se o Dispositivo não for exibido como uma opção de destino, talvez seja necessário alterar o projeto de inicialização para a solução do Visual Studio do projeto IL2CPP para o projeto UWP.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-229">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="3fbc1-230">Para fazer isso, no Gerenciador de Soluções, clique com o botão direito do mouse no NomeDoSeuProjeto (Universal do Windows) e selecione **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-230">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="3fbc1-231">Conecte o seu HoloLens ao seu computador e, em seguida, selecione **Depurar** > **Iniciar sem Depuração** para criar e implantar no seu dispositivo:</span><span class="sxs-lookup"><span data-stu-id="3fbc1-231">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Caminho do menu Iniciar Sem Depuração do Visual Studio](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="3fbc1-233">Antes de compilar no dispositivo, ele precisa estar no Modo de Desenvolvedor e emparelhado com o computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-233">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="3fbc1-234">Essas duas etapas podem ser concluídas seguindo [estas instruções](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="3fbc1-234">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="3fbc1-235">Você também pode implantar no [Emulador do HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou criar um [Pacote do Aplicativo](/windows/uwp/packaging/packaging-uwp-apps) para sideload.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-235">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="3fbc1-236">O uso de Iniciar sem Depuração inicia automaticamente o aplicativo no seu dispositivo sem o depurador do Visual Studio anexado.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-236">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="3fbc1-237">Selecione **Criar > Implantar Solução** para implantar no seu dispositivo sem iniciar o aplicativo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-237">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="3fbc1-238">Observe o criador de perfil de Diagnóstico no aplicativo, você pode ativar ou desativar a sua visibilidade usando o comando de fala **“Alternar Diagnóstico”** .</span><span class="sxs-lookup"><span data-stu-id="3fbc1-238">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **"Toggle Diagnostics"**.</span></span> <span data-ttu-id="3fbc1-239">É recomendável que você mantenha o criador de perfil visível na maior parte do tempo durante o desenvolvimento para entender quando as alterações no aplicativo podem afetar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-239">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="3fbc1-240">Por exemplo, os aplicativos do HoloLens devem [ser executados continuamente em 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="3fbc1-240">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="3fbc1-241">Parabéns</span><span class="sxs-lookup"><span data-stu-id="3fbc1-241">Congratulations</span></span>

<span data-ttu-id="3fbc1-242">Você acabou de implantar o seu primeiro aplicativo do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-242">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="3fbc1-243">Com o aplicativo aberto, você verá um objeto Cubo em sua frente poderá interagir com ele, movendo-o. Ao caminhar você verá uma malha de mapeamento espacial que sobre as superfícies que são detectadas pelo Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-243">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="3fbc1-244">Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-244">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="3fbc1-245">Esses recursos são apenas alguns dos componentes fundamentais incluídos no MRTK.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-245">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="3fbc1-246">Nos próximos tutoriais, você adicionará o conteúdo à sua cena para explorar as funcionalidades do HoloLens e do MRTK.</span><span class="sxs-lookup"><span data-stu-id="3fbc1-246">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3fbc1-247">Próximo tutorial: 3. Como configurar os perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="3fbc1-247">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
