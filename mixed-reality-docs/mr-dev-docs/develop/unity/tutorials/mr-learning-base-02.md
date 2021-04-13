---
title: Como inicializar o seu projeto e implantar o primeiro aplicativo
description: Este curso mostra como configurar seu projeto do Unity para o MRTK (Kit de Ferramentas de Realidade Misturada) e como implantá-lo no HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: c9cf580b1123002e9e8cdfd5c3914c3aa39e2825
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003125"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="29f45-104">2. Como inicializar o seu projeto e implantar o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="29f45-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="29f45-105">Neste tutorial, você aprenderá a criar um projeto do Unity, configurá-lo para o desenvolvimento do <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">MRTK (Kit de Ferramentas de Realidade Misturada)</a> e importar o MRTK.</span><span class="sxs-lookup"><span data-stu-id="29f45-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="29f45-106">Você também aprenderá mais sobre como configurar, compilar e implantar uma cena básica do Unity do Visual Studio para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="29f45-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="29f45-107">Depois de implantá-la no HoloLens 2, você verá uma malha de mapeamento espacial que abrange as superfícies percebidas pelo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="29f45-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="29f45-108">Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="29f45-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

## <a name="objectives"></a><span data-ttu-id="29f45-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="29f45-110">Objectives</span></span>

* <span data-ttu-id="29f45-111">Saiba como configurar o Unity para o desenvolvimento no HoloLens</span><span class="sxs-lookup"><span data-stu-id="29f45-111">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="29f45-112">Saiba como criar e implantar o seu aplicativo no HoloLens</span><span class="sxs-lookup"><span data-stu-id="29f45-112">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="29f45-113">Experimente a malha de mapeamento espacial, as malhas de mão e o contador da taxa de quadros no dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="29f45-113">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="29f45-114">Como criar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="29f45-114">Creating the Unity project</span></span>

<span data-ttu-id="29f45-115">Inicie o **Hub do Unity**, selecione a guia **Projetos** e clique na **seta para baixo** ao lado do botão **Novo**:</span><span class="sxs-lookup"><span data-stu-id="29f45-115">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![Hub do Unity com o botão Novo realçado](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="29f45-117">Na lista suspensa, selecione a **versão** do Unity especificada em [Pré-requisitos](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="29f45-117">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Hub do Unity com a lista suspensa do seletor de NOVA versão](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="29f45-119">Se a versão específica do Unity não estiver disponível no Hub do Unity, você poderá iniciar a instalação em <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Arquivos de Download</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="29f45-119">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="29f45-120">Na janela Criar um novo projeto:</span><span class="sxs-lookup"><span data-stu-id="29f45-120">In the Create a new project window:</span></span>

* <span data-ttu-id="29f45-121">Verifique se **Modelos** está definido como **3D**</span><span class="sxs-lookup"><span data-stu-id="29f45-121">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="29f45-122">Insira um **Nome de Projeto** adequado, por exemplo, _Tutoriais do MRTK_</span><span class="sxs-lookup"><span data-stu-id="29f45-122">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="29f45-123">Escolha um **Local** adequado para armazenar seu projeto, por exemplo, _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="29f45-123">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="29f45-124">Clique no botão **Criar** para criar e iniciar o novo projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="29f45-124">Click the **Create** button to create and launch your new Unity project</span></span>

![Hub do Unity com a janela Criar um projeto preenchida](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="29f45-126">Ao trabalhar no Windows, há um limite de MAX_PATH de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="29f45-126">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="29f45-127">Consequentemente, você deve salvar o projeto do Unity próximo à raiz da unidade.</span><span class="sxs-lookup"><span data-stu-id="29f45-127">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="29f45-128">Aguarde até que o Unity crie o projeto:</span><span class="sxs-lookup"><span data-stu-id="29f45-128">Wait for Unity to create the project:</span></span>

![Criação de projeto do Unity em andamento](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="29f45-130">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="29f45-130">Switching the build platform</span></span>

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="29f45-131">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="29f45-131">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="29f45-132">No menu do Unity, selecione **Janela** > **TextMeshPro** > **Importar Recursos Essenciais do TMP** para abrir a janela Importar Pacote do Unity:</span><span class="sxs-lookup"><span data-stu-id="29f45-132">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Caminho do menu Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="29f45-134">Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:</span><span class="sxs-lookup"><span data-stu-id="29f45-134">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Janela Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="29f45-136">Os Recursos Essenciais do TextMeshPro são exigidos pelos elementos da interface do usuário do MRTK.</span><span class="sxs-lookup"><span data-stu-id="29f45-136">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="29f45-137">Você poderá ignorar esta etapa se não estiver planejando usar os elementos da interface do usuário do MRTK no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="29f45-137">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="29f45-138">Como importar o Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="29f45-138">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="29f45-139">Para importar o Kit de Ferramentas de Realidade Misturada no projeto do Unity, você terá que usar a [Ferramenta de Recursos da Realidade Misturada](../welcome-to-mr-feature-tool.md) que permite aos desenvolvedores descobrir, atualizar e adicionar pacotes de recursos de Realidade Misturada a projetos do Unity.</span><span class="sxs-lookup"><span data-stu-id="29f45-139">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="29f45-140">Você pode pesquisar pacotes por nome ou categoria, ver as respectivas dependências e, até mesmo, ver as alterações propostas no arquivo de manifesto dos seus projetos antes da importação.</span><span class="sxs-lookup"><span data-stu-id="29f45-140">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="29f45-141">Baixe a última versão da Ferramenta de Recursos da Realidade Misturada no [Centro de Download da Microsoft](https://aka.ms/MRFeatureTool). Quando o download for concluído, descompacte o arquivo e salve-o na sua área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="29f45-141">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="29f45-142">Para executar a Ferramenta de Recursos da Realidade Misturada, instale o [runtime do .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="29f45-142">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="29f45-143">A Ferramenta de Recursos de Realidade Misturada atualmente só é executada no Windows. Para o MacOS, siga este [procedimento](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) para baixar e importar o Kit de Ferramentas de Realidade Misturada no projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="29f45-143">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

<span data-ttu-id="29f45-144">Abra o arquivo executável **MixedRealityFeatureTool** na pasta baixada para iniciar a Ferramenta de Recursos da Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="29f45-144">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![Abrindo o MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)


[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="configuring-the-unity-project"></a><span data-ttu-id="29f45-146">Como configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="29f45-146">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="29f45-147">1. Aplicar as configurações do Configurador de Projeto do MRTK</span><span class="sxs-lookup"><span data-stu-id="29f45-147">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="29f45-148">Depois que o Unity terminar de importar o pacote da seção anterior, a janela Configurador de Projeto do MRTK deverá aparecer.</span><span class="sxs-lookup"><span data-stu-id="29f45-148">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="29f45-149">Caso contrário, você pode abri-la manualmente acessando **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity**:</span><span class="sxs-lookup"><span data-stu-id="29f45-149">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Caminho do menu Configurar Projeto do Unity no Unity](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="29f45-151">Na janela Configurador de Projeto do MRTK, expanda a seção **Modificar Configurações**, verifique se todas as opções estão marcadas e clique no botão **Aplicar** para aplicar as configurações:</span><span class="sxs-lookup"><span data-stu-id="29f45-151">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Janela Configurador de Projeto do MRTK no Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="29f45-153">A aplicação das Configurações Padrão do MRTK é opcional, mas altamente recomendável, pois ela ajudará a definir algumas das configurações recomendadas do Unity:</span><span class="sxs-lookup"><span data-stu-id="29f45-153">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="29f45-154">Definir o caminho de renderização com uma Instância de Passagem Única: aprimora o desempenho gráfico executando o pipeline de renderização dos dois olhos na mesma chamada de desenho.</span><span class="sxs-lookup"><span data-stu-id="29f45-154">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="29f45-155">Para saber mais sobre este tópico, veja a seção [Renderização com uma Instância de Passagem Única](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) da documentação [Desempenho](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) do MRTK.</span><span class="sxs-lookup"><span data-stu-id="29f45-155">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="29f45-156">Definir camada padrão de Reconhecimento Espacial: cria uma camada do Unity chamada Reconhecimento Espacial e configura o MRTK para usá-la na malha de reconhecimento espacial.</span><span class="sxs-lookup"><span data-stu-id="29f45-156">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="29f45-157">Para saber mais sobre as Camadas do Unity, veja a documentação <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Como personalizar seu workspace</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="29f45-157">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="29f45-158">2. Definir configurações adicionais do projeto</span><span class="sxs-lookup"><span data-stu-id="29f45-158">2. Configure additional project settings</span></span>

[!INCLUDE[](includes/configuring-additional-project-settings.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="29f45-159">Como criar a cena e configurar o MRTK</span><span class="sxs-lookup"><span data-stu-id="29f45-159">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="29f45-160">No menu do Unity, selecione **Arquivo** > **Nova Cena** para criar uma cena:</span><span class="sxs-lookup"><span data-stu-id="29f45-160">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Caminho do menu Nova Cena do Unity](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="29f45-162">No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Adicionar à Cena e Configurar...** para adicionar o MRTK à cena atual:</span><span class="sxs-lookup"><span data-stu-id="29f45-162">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Caminho do menu Adicionar à Cena e Configurar... do Unity](images/mr-learning-base/base-02-section6-step1-2.png)

[!INCLUDE[](includes/changing-profile.md)]

<span data-ttu-id="29f45-164">No menu do Unity, selecione **Arquivo** > **Salvar Como...** para abrir a janela Salvar Cena:</span><span class="sxs-lookup"><span data-stu-id="29f45-164">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Caminho do menu Salvar como... do Unity](images/mr-learning-base/base-02-section6-step1-4.png)

> [!TIP]
> <span data-ttu-id="29f45-166">A redução do formato de profundidade para 16 bits é opcional, mas pode ajudar a aprimorar o desempenho gráfico no projeto.</span><span class="sxs-lookup"><span data-stu-id="29f45-166">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="29f45-167">Para saber mais sobre este tópico, veja a seção <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Desempenho</a> do MRTK.</span><span class="sxs-lookup"><span data-stu-id="29f45-167">To learn more about this topic, you can refer to the   <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> Performance </a> documentation.</span></span>

![Janela de prompt Salvar para salvar a cena do Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="29f45-169">Como importar os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="29f45-169">Importing the tutorial assets</span></span>

<span data-ttu-id="29f45-170">Baixe o seguinte pacote personalizado do Unity:</span><span class="sxs-lookup"><span data-stu-id="29f45-170">Download the following Unity custom package:</span></span>

* [<span data-ttu-id="29f45-171">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="29f45-171">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

<span data-ttu-id="29f45-172">Para importar um pacote personalizado do Unity, no menu do Unity selecione **Ativos** > **Importar Pacote** > **Pacote Personalizado...** para abrir a janela Importar pacote...:</span><span class="sxs-lookup"><span data-stu-id="29f45-172">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Como importar um pacote personalizado](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="29f45-174">Na janela Importar Pacote..., selecione o **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** que você baixou e clique no botão Abrir:</span><span class="sxs-lookup"><span data-stu-id="29f45-174">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** you downloaded and click the Open button:</span></span>

![Como selecionar um pacote de ativos](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="29f45-176">Na janela Importar Pacote do Unity, clique no botão Todos para garantir que todos os ativos sejam selecionados e clique no botão Importar para importar os ativos:</span><span class="sxs-lookup"><span data-stu-id="29f45-176">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![Como selecionar todos os ativos a serem importados](images/mr-learning-base/base-02-section7-step1-3.png)

<span data-ttu-id="29f45-178">Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="29f45-178">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Janela de projeto do Unity após importar os ativos](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a><span data-ttu-id="29f45-180">Como configurar a cena</span><span class="sxs-lookup"><span data-stu-id="29f45-180">Configuring the Scene</span></span>

<span data-ttu-id="29f45-181">Na janela Projeto, navegue até a pasta Ativos > MRTK.Tutorials.GettingStarted > Pré-fabricados:</span><span class="sxs-lookup"><span data-stu-id="29f45-181">In the Project window, navigate to the Assets > MRTK.Tutorials.GettingStarted > Prefabs folder:</span></span>

<span data-ttu-id="29f45-182">Na janela Projeto, clique e arraste o pré-fabricado **Cubo** para a janela Hierarquia, e na janela Inspetor configure o componente **Transformar** da seguinte forma</span><span class="sxs-lookup"><span data-stu-id="29f45-182">From the Project window, click-and-drag the **Cube** prefab on to the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="29f45-183">**Posição**: X = 0, Y = 0, Z = 0,5</span><span class="sxs-lookup"><span data-stu-id="29f45-183">**Position**: X = 0, Y = 0, Z = 0.5</span></span>
* <span data-ttu-id="29f45-184">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="29f45-184">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="29f45-185">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="29f45-185">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Adicionando um cubo à cena](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="29f45-187">Para aumentar o foco nos objetos da cena, você pode clicar duas vezes no objeto **Cubo** e aumentar levemente o zoom de novo:</span><span class="sxs-lookup"><span data-stu-id="29f45-187">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again:</span></span>

<span data-ttu-id="29f45-188">Para interagir e segurar um objeto com as mãos rastreadas, o objeto deve ter um componente Colisor, por exemplo, um **Colisor de Caixa**, um componente **Manipulador de Objetos (script)** e um componente **NearInteractionGrabbable (script)** .</span><span class="sxs-lookup"><span data-stu-id="29f45-188">To interact and grab an object with tracked hands, the object must have Collider component for example a **Box Collider**,  **Object Manipulator (Script)** component and **NearInteractionGrabbable(Script)** component.</span></span>

<span data-ttu-id="29f45-189">Para adicionar o script de Manipulador de Objetos ao objeto Cubo, mantenha o **Cubo** selecionado na janela Hierarquia, clique no botão **Adicionar Componente** na janela Inspetor e, em seguida, pesquise e selecione o script **Manipulador de Objetos**.</span><span class="sxs-lookup"><span data-stu-id="29f45-189">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![Como adicionar o Manipulador de Objetos ao Cubo](images/mr-learning-base/base-02-section8-step1-2.png)

<span data-ttu-id="29f45-191">Repita o mesmo procedimento para adicionar o **script de Interação Próxima com Objeto Segurável** ao Cubo</span><span class="sxs-lookup"><span data-stu-id="29f45-191">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![Como adicionar Interação Próxima com Objeto Segurável ao Cubo](images/mr-learning-base/base-02-section8-step1-3.png)

> [!NOTE]
> <span data-ttu-id="29f45-193">Quando você adiciona um Object Manipulator (Script), nesse caso, o Constraint Manager (Script) é adicionado automaticamente porque o Object Manipulator (Script) depende dele.</span><span class="sxs-lookup"><span data-stu-id="29f45-193">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="29f45-194">Para os fins deste tutorial, os colisores já foram adicionados ao Objeto Cubo.</span><span class="sxs-lookup"><span data-stu-id="29f45-194">For the purpose of this tutorial, colliders have already been added to the Cube Object.</span></span> <span data-ttu-id="29f45-195">Para saber mais sobre os colisores, acesse a documentação do <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Colisor</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="29f45-195">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

<span data-ttu-id="29f45-196">Para fazer o teste no editor do Unity, acesse o modo de execução e mantenha pressionada a tecla **Shift da esquerda** ou a tecla **Espaço** para habilitar o controlador. Você pode mover o controlador com o mouse e usar o botão de rolagem para aproximá-lo ou afastá-lo da câmera.</span><span class="sxs-lookup"><span data-stu-id="29f45-196">To test this in the Unity editor, you can enter the play mode and hold the **LeftShift** or **Space** key to enable the controller, Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="29f45-197">Com o ponteiro sobre o Cubo, mantenha pressionado o **botão direito do mouse** para mover o objeto Cubo.</span><span class="sxs-lookup"><span data-stu-id="29f45-197">Once the pointer is on the Cube  press and hold **Right Mouse Button** to move the the Cube object.</span></span>

![Modo de Jogo](images/mr-learning-base/base-02-section8-step1-4.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="29f45-199">Como criar o aplicativo para o seu HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="29f45-199">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="29f45-200">1. Compilar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="29f45-200">1. Build the Unity project</span></span>

<span data-ttu-id="29f45-201">No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="29f45-201">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="29f45-202">Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar sua cena atual à lista **Cenas no Build** e clique no botão **Build** para abrir a janela Compilar Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="29f45-202">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Janela Configurações de Build do Unity com o UWP selecionado](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="29f45-204">Na janela Compilar Plataforma Universal do Windows, escolha um local adequado para armazenar seu build, por exemplo, _D:\MixedRealityLearning\Builds_, crie uma nova pasta e dê a ela um nome adequado, por exemplo, _GettingStarted_ e, em seguida, clique no botão **Selecionar Pasta** para iniciar o processo de build:</span><span class="sxs-lookup"><span data-stu-id="29f45-204">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Janela Configurações de Build do Unity com a janela de prompt Selecionar Pasta](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="29f45-206">Aguarde até que o Unity conclua o processo de build:</span><span class="sxs-lookup"><span data-stu-id="29f45-206">Wait for Unity to finish the build process:</span></span>

![Processo de build do Unity em andamento](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="29f45-208">2. Compilar e implantar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="29f45-208">2. Build and deploy the application</span></span>

<span data-ttu-id="29f45-209">Quando o processo de build for concluído, o Unity solicitará que o Explorador de Arquivos do Windows abra a localização em que você armazenou o build.</span><span class="sxs-lookup"><span data-stu-id="29f45-209">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="29f45-210">Navegue dentro da pasta e clique duas vezes no arquivo da solução para abri-lo no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="29f45-210">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Windows Explorer com a solução do Visual Studio recém-criada selecionada](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="29f45-212">Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar-se de que você tenha todos os componentes de pré-requisitos na documentação **[Instalar as Ferramentas](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="29f45-212">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="29f45-213">Configure o Visual Studio para o HoloLens selecionando a configuração **Mestre** ou **Versão**, a arquitetura **ARM64** e o **Dispositivo** como destino:</span><span class="sxs-lookup"><span data-stu-id="29f45-213">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio configurado para implantação no HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="29f45-215">Se você estiver implantando no HoloLens (1ª geração), selecione a arquitetura **x86**.</span><span class="sxs-lookup"><span data-stu-id="29f45-215">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="29f45-216">Para o HoloLens, você normalmente criará para a arquitetura ARM.</span><span class="sxs-lookup"><span data-stu-id="29f45-216">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="29f45-217">No entanto, há um <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conhecido</strong></a> no Unity 2019.3 que causa erros ao selecionar o ARM como a arquitetura de build no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="29f45-217">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="29f45-218">A solução alternativa recomendada é criar para o ARM64.</span><span class="sxs-lookup"><span data-stu-id="29f45-218">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="29f45-219">Se essa não for uma opção, acesse **Editar > Configurações de Projeto > Player > Outras Configurações** e desabilite **Trabalhos Gráficos**.</span><span class="sxs-lookup"><span data-stu-id="29f45-219">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="29f45-220">Se o Dispositivo não for exibido como uma opção de destino, talvez seja necessário alterar o projeto de inicialização para a solução do Visual Studio do projeto IL2CPP para o projeto UWP.</span><span class="sxs-lookup"><span data-stu-id="29f45-220">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="29f45-221">Para fazer isso, no Gerenciador de Soluções, clique com o botão direito do mouse no NomeDoSeuProjeto (Universal do Windows) e selecione **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="29f45-221">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="29f45-222">Conecte o seu HoloLens ao seu computador e, em seguida, selecione **Depurar** > **Iniciar sem Depuração** para criar e implantar no seu dispositivo:</span><span class="sxs-lookup"><span data-stu-id="29f45-222">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Caminho do menu Iniciar Sem Depuração do Visual Studio](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="29f45-224">Antes de compilar no dispositivo, ele precisa estar no Modo de Desenvolvedor e emparelhado com o computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="29f45-224">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="29f45-225">Essas duas etapas podem ser concluídas seguindo [estas instruções](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="29f45-225">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="29f45-226">Você também pode implantar no [Emulador do HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou criar um [Pacote do Aplicativo](/windows/uwp/packaging/packaging-uwp-apps) para sideload.</span><span class="sxs-lookup"><span data-stu-id="29f45-226">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="29f45-227">O uso de Iniciar sem Depuração inicia automaticamente o aplicativo no seu dispositivo sem o depurador do Visual Studio anexado.</span><span class="sxs-lookup"><span data-stu-id="29f45-227">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="29f45-228">Selecione **Criar > Implantar Solução** para implantar no seu dispositivo sem iniciar o aplicativo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="29f45-228">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="29f45-229">Observe o criador de perfil de Diagnóstico no aplicativo, você pode ativar ou desativar a sua visibilidade usando o comando de fala **Alternar Diagnóstico**.</span><span class="sxs-lookup"><span data-stu-id="29f45-229">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="29f45-230">É recomendável que você mantenha o criador de perfil visível na maior parte do tempo durante o desenvolvimento para entender quando as alterações no aplicativo podem afetar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="29f45-230">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="29f45-231">Por exemplo, os aplicativos do HoloLens devem [ser executados continuamente em 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="29f45-231">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="29f45-232">Parabéns</span><span class="sxs-lookup"><span data-stu-id="29f45-232">Congratulations</span></span>

<span data-ttu-id="29f45-233">Você acabou de implantar o seu primeiro aplicativo do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="29f45-233">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="29f45-234">Com o aplicativo aberto, você verá um objeto Cubo em sua frente poderá interagir com ele, movendo-o. Ao caminhar você verá uma malha de mapeamento espacial que sobre as superfícies que são detectadas pelo Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="29f45-234">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="29f45-235">Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="29f45-235">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="29f45-236">Esses recursos são apenas alguns dos componentes fundamentais incluídos no MRTK.</span><span class="sxs-lookup"><span data-stu-id="29f45-236">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="29f45-237">Nos próximos tutoriais, você adicionará o conteúdo à sua cena para explorar as funcionalidades do HoloLens e do MRTK.</span><span class="sxs-lookup"><span data-stu-id="29f45-237">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="29f45-238">Próximo tutorial: 3. Como configurar os perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="29f45-238">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
