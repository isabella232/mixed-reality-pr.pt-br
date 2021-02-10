---
title: Como inicializar o seu projeto e implantar o primeiro aplicativo
description: Este curso mostra como configurar seu projeto do Unity para o MRTK (Kit de Ferramentas de Realidade Misturada) e como implantá-lo no HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 82551257339d41940075ee06a6e6937624b83900
ms.sourcegitcommit: 08503cada8a29a34bcbd9fd955cb23adfe9b60a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99627847"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="c2098-104">2. Como inicializar o seu projeto e implantar o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="c2098-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="c2098-105">Neste tutorial, você aprenderá a criar um projeto do Unity, configurá-lo para o desenvolvimento do <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK (Kit de Ferramentas de Realidade Misturada)</a> e importar o MRTK.</span><span class="sxs-lookup"><span data-stu-id="c2098-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="c2098-106">Você também aprenderá mais sobre como configurar, compilar e implantar uma cena básica do Unity do Visual Studio para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c2098-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="c2098-107">Depois de implantá-la no HoloLens 2, você verá uma malha de mapeamento espacial que abrange as superfícies percebidas pelo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c2098-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="c2098-108">Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2098-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="c2098-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c2098-109">Objectives</span></span>

* <span data-ttu-id="c2098-110">Saiba como configurar o Unity para o desenvolvimento no HoloLens</span><span class="sxs-lookup"><span data-stu-id="c2098-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="c2098-111">Saiba como criar e implantar o seu aplicativo no HoloLens</span><span class="sxs-lookup"><span data-stu-id="c2098-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="c2098-112">Experimente a malha de mapeamento espacial, as malhas de mão e o contador da taxa de quadros no dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c2098-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="c2098-113">Como criar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="c2098-113">Creating the Unity project</span></span>

<span data-ttu-id="c2098-114">Inicie o **Hub do Unity**, selecione a guia **Projetos** e clique na **seta para baixo** ao lado do botão **Novo**:</span><span class="sxs-lookup"><span data-stu-id="c2098-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![Hub do Unity com o botão Novo realçado](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="c2098-116">Na lista suspensa, selecione a **versão** do Unity especificada em [Pré-requisitos](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="c2098-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Hub do Unity com a lista suspensa do seletor de NOVA versão](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="c2098-118">Se a versão específica do Unity não estiver disponível no Hub do Unity, você poderá iniciar a instalação em <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Arquivos de Download</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="c2098-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="c2098-119">Na janela Criar um novo projeto:</span><span class="sxs-lookup"><span data-stu-id="c2098-119">In the Create a new project window:</span></span>

* <span data-ttu-id="c2098-120">Verifique se **Modelos** está definido como **3D**</span><span class="sxs-lookup"><span data-stu-id="c2098-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="c2098-121">Insira um **Nome de Projeto** adequado, por exemplo, _Tutoriais do MRTK_</span><span class="sxs-lookup"><span data-stu-id="c2098-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="c2098-122">Escolha um **Local** adequado para armazenar seu projeto, por exemplo, _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="c2098-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="c2098-123">Clique no botão **Criar** para criar e iniciar o novo projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="c2098-123">Click the **Create** button to create and launch your new Unity project</span></span>

![Hub do Unity com a janela Criar um projeto preenchida](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="c2098-125">Ao trabalhar no Windows, há um limite de MAX_PATH de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="c2098-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="c2098-126">Consequentemente, você deve salvar o projeto do Unity próximo à raiz da unidade.</span><span class="sxs-lookup"><span data-stu-id="c2098-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="c2098-127">Aguarde até que o Unity crie o projeto:</span><span class="sxs-lookup"><span data-stu-id="c2098-127">Wait for Unity to create the project:</span></span>

![Criação de projeto do Unity em andamento](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="c2098-129">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="c2098-129">Switching the build platform</span></span>

<span data-ttu-id="c2098-130">No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build:</span><span class="sxs-lookup"><span data-stu-id="c2098-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Caminho do menu Configurações de Build... do Unity](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="c2098-132">Na janela Configurações de Build, selecione **Plataforma Universal do Windows** e clique no botão **Mudar Plataforma**:</span><span class="sxs-lookup"><span data-stu-id="c2098-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Janela Configurações de Build do Unity com o UWP selecionado para alternar a plataforma da opção Autônomo](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="c2098-134">Aguarde até que o Unity termine de mudar a plataforma:</span><span class="sxs-lookup"><span data-stu-id="c2098-134">Wait for Unity to finish switching the platform:</span></span>

![Alternância de plataforma do Unity em andamento](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="c2098-136">Quando o Unity terminar de mudar a plataforma, clique no ícone vermelho **x** para fechar a janela Configurações de Build:</span><span class="sxs-lookup"><span data-stu-id="c2098-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Janela Build do Unity com ícone de Fechar realçado](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="c2098-138">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="c2098-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="c2098-139">No menu do Unity, selecione **Janela** > **TextMeshPro** > **Importar Recursos Essenciais do TMP** para abrir a janela Importar Pacote do Unity:</span><span class="sxs-lookup"><span data-stu-id="c2098-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Caminho do menu Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="c2098-141">Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:</span><span class="sxs-lookup"><span data-stu-id="c2098-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Janela Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="c2098-143">Os Recursos Essenciais do TextMeshPro são exigidos pelos elementos da interface do usuário do MRTK.</span><span class="sxs-lookup"><span data-stu-id="c2098-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="c2098-144">Você poderá ignorar esta etapa se não estiver planejando usar os elementos da interface do usuário do MRTK no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c2098-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="c2098-145">Como importar o Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="c2098-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="c2098-146">Para importar o Kit de Ferramentas de Realidade Misturada no projeto do Unity, você terá que usar a [Ferramenta de Recursos da Realidade Misturada](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) que permite aos desenvolvedores descobrir, atualizar e adicionar pacotes de recursos de Realidade Misturada a projetos do Unity.</span><span class="sxs-lookup"><span data-stu-id="c2098-146">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="c2098-147">Você pode pesquisar pacotes por nome ou categoria, ver as respectivas dependências e, até mesmo, ver as alterações propostas no arquivo de manifesto dos seus projetos antes da importação.</span><span class="sxs-lookup"><span data-stu-id="c2098-147">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="c2098-148">Baixe a última versão da Ferramenta de Recursos da Realidade Misturada no [Centro de Download da Microsoft](https://aka.ms/MRFeatureTool). Quando o download for concluído, descompacte o arquivo e salve-o na sua área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c2098-148">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="c2098-149">Para executar a Ferramenta de Recursos da Realidade Misturada, instale o [runtime do .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="c2098-149">Before you can run the Mixed Reality Feature Tool please instal [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="c2098-150">A Ferramenta de Recursos de Realidade Misturada atualmente só é executada no Windows. Para o MacOS, siga este [procedimento](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) para baixar e importar o Kit de Ferramentas de Realidade Misturada no projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="c2098-150">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

<span data-ttu-id="c2098-151">Abra o arquivo executável **MixedRealityFeatureTool** na pasta baixada para iniciar a Ferramenta de Recursos da Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="c2098-151">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![Abrindo o MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="c2098-153">Quando o **MixedRealityFeatureTool** for aberto, clique em Iniciar para começar a usar a Ferramenta de Recursos da Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="c2098-153">Once **MixedRealityFeatureTool** is opened click on start to get started with Mixed Reality Feature Tool.</span></span>

![MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="c2098-155">Os recursos são agrupados por categoria para que seja mais fácil encontrar o que você quer. Clique na lista suspensa **Kit de Ferramentas de Realidade Misturada** para encontrar pacotes relacionados ao Kit de Ferramentas de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="c2098-155">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![Janela do MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="c2098-157">verifique o **Mixed Reality Toolkit Foundation** e clique na lista suspensa ao lado dele para selecionar a versão necessária do MRTK. Para esta série de tutoriais, selecione **2.5.3**.</span><span class="sxs-lookup"><span data-stu-id="c2098-157">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the required MRTK version, for this tutorial series please select **2.5.3**.</span></span> <span data-ttu-id="c2098-158">em seguida, clique no botão **Obter recursos** para baixar os pacotes selecionados.</span><span class="sxs-lookup"><span data-stu-id="c2098-158">then click on **Get features** button to download the selected packages.</span></span>

![Como selecionar o Mixed Reality Foundation](images/mr-learning-base/base-02-section4-step1-4.png)

<span data-ttu-id="c2098-160">O pacote selecionado **Mixed Reality Toolkit Foundation 2.5.3** é apresentado, juntamente com o pacote de dependência **Mixed Reality Toolkit Standard Assets 2.5.3** na janela **Importar Recursos**.</span><span class="sxs-lookup"><span data-stu-id="c2098-160">Selected package **Mixed Reality Toolkit Foundation 2.5.3** is presented, along with its dependence package **Mixed Reality Toolkit Standard Assets 2.5.3** in the **Import Features** window.</span></span>

<span data-ttu-id="c2098-161">Você também precisa definir a localização do projeto de destino do Unity para fornecer o **Caminho do projeto**. Clique nos **três pontos** ao lado do Caminho do projeto e navegue até a pasta do projeto no explorador, por exemplo, _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="c2098-161">You also need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

> [!NOTE]
> <span data-ttu-id="c2098-162">A caixa de diálogo exibida durante a navegação para a pasta de projeto do Unity contém '_' como o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c2098-162">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="c2098-163">É necessário colocar um valor para o nome do arquivo a fim de permitir que a pasta seja selecionada.</span><span class="sxs-lookup"><span data-stu-id="c2098-163">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="c2098-164">Em seguida, clique no botão **Validar** para validar o pacote selecionado. Você receberá um pop-up com a mensagem **Não foi detectado nenhum problema de validação**, clique em **OK** para fechar o pop-up e clique no botão **Importar**.</span><span class="sxs-lookup"><span data-stu-id="c2098-164">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![Como validar o Mixed Reality Foundation](images/mr-learning-base/base-02-section4-step1-5.png)

<span data-ttu-id="c2098-166">Clique no botão **Aprovar** para adicionar o **Kit de Ferramentas de Realidade Misturada** ao projeto.</span><span class="sxs-lookup"><span data-stu-id="c2098-166">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Aprovar o Mixed Reality Foundation](images/mr-learning-base/base-02-section4-step1-6.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="c2098-168">Como configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="c2098-168">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="c2098-169">1. Aplicar as configurações do Configurador de Projeto do MRTK</span><span class="sxs-lookup"><span data-stu-id="c2098-169">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="c2098-170">Depois que o Unity terminar de importar o pacote da seção anterior, a janela Configurador de Projeto do MRTK deverá aparecer.</span><span class="sxs-lookup"><span data-stu-id="c2098-170">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="c2098-171">Caso contrário, você pode abri-la manualmente acessando **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity**:</span><span class="sxs-lookup"><span data-stu-id="c2098-171">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Caminho do menu Configurar Projeto do Unity no Unity](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="c2098-173">Na janela Configurador de Projeto do MRTK, expanda a seção **Modificar Configurações**, verifique se todas as opções estão marcadas e clique no botão **Aplicar** para aplicar as configurações:</span><span class="sxs-lookup"><span data-stu-id="c2098-173">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Janela Configurador de Projeto do MRTK no Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="c2098-175">A aplicação das Configurações Padrão do MRTK é opcional, mas altamente recomendável, pois ela ajudará a definir algumas das configurações recomendadas do Unity:</span><span class="sxs-lookup"><span data-stu-id="c2098-175">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="c2098-176">Definir o caminho de renderização com uma Instância de Passagem Única: aprimora o desempenho gráfico executando o pipeline de renderização dos dois olhos na mesma chamada de desenho.</span><span class="sxs-lookup"><span data-stu-id="c2098-176">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="c2098-177">Para saber mais sobre este tópico, veja a seção [Renderização com uma Instância de Passagem Única](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) da documentação [Desempenho](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) do MRTK.</span><span class="sxs-lookup"><span data-stu-id="c2098-177">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="c2098-178">Definir camada padrão de Reconhecimento Espacial: cria uma camada do Unity chamada Reconhecimento Espacial e configura o MRTK para usá-la na malha de reconhecimento espacial.</span><span class="sxs-lookup"><span data-stu-id="c2098-178">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="c2098-179">Para saber mais sobre as Camadas do Unity, veja a documentação <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Como personalizar seu workspace</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="c2098-179">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="c2098-180">2. Definir configurações adicionais do projeto</span><span class="sxs-lookup"><span data-stu-id="c2098-180">2. Configure additional project settings</span></span>

<span data-ttu-id="c2098-181">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:</span><span class="sxs-lookup"><span data-stu-id="c2098-181">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="c2098-182">Na janela Configurações do Projeto, selecione **Player** > **Configurações de XR** e marque a caixa de seleção **Realidade Virtual com Suporte**, clique no ícone **+** e selecione Windows Mixed Reality para adicionar o SDK do Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="c2098-182">In the Project Settings window, select **Player** > **XR Settings** and check the **Virual Reality Supported** checkbox then click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![Configurações de XR do Unity com a adição do SDK do Windows Mixed Reality selecionada](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="c2098-184">Depois que o Unity terminar de importar o SDK do Windows Mixed Reality, a janela Configurador de Projeto do MRTK deverá aparecer novamente.</span><span class="sxs-lookup"><span data-stu-id="c2098-184">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="c2098-185">Caso contrário, você pode abri-la manualmente no menu do Unity acessando **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity**</span><span class="sxs-lookup"><span data-stu-id="c2098-185">If it doesn't, you can manually open it from the Unity menu by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**</span></span>

<span data-ttu-id="c2098-186">Na janela Configurador de Projeto do MRTK, use a lista suspensa **Espacializador de áudio** para selecionar o **Espacializador MS HRTF** e clique no botão **Aplicar** para aplicar a configuração:</span><span class="sxs-lookup"><span data-stu-id="c2098-186">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Configurações de XR do Unity com a adição do SDK do Windows Mixed Reality selecionada](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="c2098-188">A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c2098-188">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="c2098-189">Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="c2098-189">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="c2098-190">Para saber mais sobre este tópico, veja os <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutoriais sobre áudio espacial</a>.</span><span class="sxs-lookup"><span data-stu-id="c2098-190">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="c2098-191">Na janela Configurações do Projeto, selecione **Player** > **Configurações de XR** e, em seguida, use a lista suspensa **Formato de Profundidade** para selecionar a **Profundidade de 16 bits**:</span><span class="sxs-lookup"><span data-stu-id="c2098-191">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Habilitação da profundidade de 16 bits do Unity](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="c2098-193">A redução do formato de profundidade para 16 bits é opcional, mas ajuda a aprimorar o desempenho gráfico no projeto.</span><span class="sxs-lookup"><span data-stu-id="c2098-193">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="c2098-194">Para saber mais sobre este tópico, veja a seção <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">Desempenho</a> do MRTK.</span><span class="sxs-lookup"><span data-stu-id="c2098-194">To learn more about this topic, you can refer to the   <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="c2098-195">Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="c2098-195">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Configurações de Publicação do Unity com o Nome do pacote configurado](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="c2098-197">O 'Nome do pacote' é o identificador exclusivo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2098-197">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="c2098-198">Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c2098-198">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="c2098-199">O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c2098-199">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="c2098-200">Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.</span><span class="sxs-lookup"><span data-stu-id="c2098-200">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="c2098-201">Como criar e configurar a cena</span><span class="sxs-lookup"><span data-stu-id="c2098-201">Creating and configuring the scene</span></span>

<span data-ttu-id="c2098-202">No menu do Unity, selecione **Arquivo** > **Nova Cena** para criar uma cena:</span><span class="sxs-lookup"><span data-stu-id="c2098-202">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Caminho do menu Nova Cena do Unity](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="c2098-204">No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Adicionar à Cena e Configurar...** para adicionar o MRTK à cena atual:</span><span class="sxs-lookup"><span data-stu-id="c2098-204">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Caminho do menu Adicionar à Cena e Configurar... do Unity](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="c2098-206">Com o objeto **MixedRealityToolkit** selecionado na janela Hierarquia, na janela Inspetor, verifique se o perfil de configuração **MixedRealityToolkit** está definido como **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="c2098-206">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit do Unity com DefaultMixedRealityTookitConfigurationProfile selecionado](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="c2098-208">No menu do Unity, selecione **Arquivo** > **Salvar Como...** para abrir a janela Salvar Cena:</span><span class="sxs-lookup"><span data-stu-id="c2098-208">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Caminho do menu Salvar como... do Unity](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="c2098-210">Na janela Salvar cena, navegue até a pasta **Cenas** do seu projeto, dê um nome adequado à sua cena (por exemplo, _Introdução_) e clique no botão **Salvar** para salvar a cena:</span><span class="sxs-lookup"><span data-stu-id="c2098-210">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![Janela de prompt Salvar para salvar a cena do Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="c2098-212">Como criar o aplicativo para o seu HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c2098-212">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="c2098-213">1. Compilar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="c2098-213">1. Build the Unity project</span></span>

<span data-ttu-id="c2098-214">No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="c2098-214">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="c2098-215">Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar sua cena atual à lista **Cenas no Build** e clique no botão **Build** para abrir a janela Compilar Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="c2098-215">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Janela Configurações de Build do Unity com o UWP selecionado](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="c2098-217">Na janela Compilar Plataforma Universal do Windows, escolha um local adequado para armazenar seu build, por exemplo, _D:\MixedRealityLearning\Builds_, crie uma nova pasta e dê a ela um nome adequado, por exemplo, _GettingStarted_ e, em seguida, clique no botão **Selecionar Pasta** para iniciar o processo de build:</span><span class="sxs-lookup"><span data-stu-id="c2098-217">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Janela Configurações de Build do Unity com a janela de prompt Selecionar Pasta](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="c2098-219">Aguarde até que o Unity conclua o processo de build:</span><span class="sxs-lookup"><span data-stu-id="c2098-219">Wait for Unity to finish the build process:</span></span>

![Processo de build do Unity em andamento](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="c2098-221">2. Compilar e implantar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="c2098-221">2. Build and deploy the application</span></span>

<span data-ttu-id="c2098-222">Quando o processo de build for concluído, o Unity solicitará que o Explorador de Arquivos do Windows abra a localização em que você armazenou o build.</span><span class="sxs-lookup"><span data-stu-id="c2098-222">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="c2098-223">Navegue dentro da pasta e clique duas vezes no arquivo da solução para abri-lo no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="c2098-223">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Windows Explorer com a solução do Visual Studio recém-criada selecionada](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="c2098-225">Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar-se de que você tenha todos os componentes de pré-requisitos na documentação **[Instalar as Ferramentas](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="c2098-225">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="c2098-226">Configure o Visual Studio para o HoloLens selecionando a configuração **Mestre** ou **Versão**, a arquitetura **ARM64** e o **Dispositivo** como destino:</span><span class="sxs-lookup"><span data-stu-id="c2098-226">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio configurado para implantação no HoloLens 2](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="c2098-228">Se você estiver implantando no HoloLens (1ª geração), selecione a arquitetura **x86**.</span><span class="sxs-lookup"><span data-stu-id="c2098-228">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="c2098-229">Para o HoloLens, você normalmente criará para a arquitetura ARM.</span><span class="sxs-lookup"><span data-stu-id="c2098-229">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="c2098-230">No entanto, há um <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conhecido</strong></a> no Unity 2019.3 que causa erros ao selecionar o ARM como a arquitetura de build no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c2098-230">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="c2098-231">A solução alternativa recomendada é criar para o ARM64.</span><span class="sxs-lookup"><span data-stu-id="c2098-231">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="c2098-232">Se essa não for uma opção, acesse **Editar > Configurações de Projeto > Player > Outras Configurações** e desabilite **Trabalhos Gráficos**.</span><span class="sxs-lookup"><span data-stu-id="c2098-232">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="c2098-233">Se o Dispositivo não for exibido como uma opção de destino, talvez seja necessário alterar o projeto de inicialização para a solução do Visual Studio do projeto IL2CPP para o projeto UWP.</span><span class="sxs-lookup"><span data-stu-id="c2098-233">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="c2098-234">Para fazer isso, no Gerenciador de Soluções, clique com o botão direito do mouse no NomeDoSeuProjeto (Universal do Windows) e selecione **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="c2098-234">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="c2098-235">Conecte o seu HoloLens ao seu computador e, em seguida, selecione **Depurar** > **Iniciar sem Depuração** para criar e implantar no seu dispositivo:</span><span class="sxs-lookup"><span data-stu-id="c2098-235">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Caminho do menu Iniciar Sem Depuração do Visual Studio](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="c2098-237">Antes de compilar no dispositivo, ele precisa estar no Modo de Desenvolvedor e emparelhado com o computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="c2098-237">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="c2098-238">Essas duas etapas podem ser concluídas seguindo [estas instruções](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c2098-238">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="c2098-239">Você também pode implantar no [Emulador do HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou criar um [Pacote do Aplicativo](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) para sideload.</span><span class="sxs-lookup"><span data-stu-id="c2098-239">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="c2098-240">O uso de Iniciar sem Depuração inicia automaticamente o aplicativo no seu dispositivo sem o depurador do Visual Studio anexado.</span><span class="sxs-lookup"><span data-stu-id="c2098-240">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="c2098-241">Selecione **Criar > Implantar Solução** para implantar no seu dispositivo sem iniciar o aplicativo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c2098-241">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="c2098-242">Observe o criador de perfil de Diagnóstico no aplicativo, você pode ativar ou desativar a sua visibilidade usando o comando de fala **Alternar Diagnóstico**.</span><span class="sxs-lookup"><span data-stu-id="c2098-242">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="c2098-243">É recomendável que você mantenha o criador de perfil visível na maior parte do tempo durante o desenvolvimento para entender quando as alterações no aplicativo podem afetar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="c2098-243">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="c2098-244">Por exemplo, os aplicativos do HoloLens devem [ser executados continuamente em 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="c2098-244">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="c2098-245">Parabéns</span><span class="sxs-lookup"><span data-stu-id="c2098-245">Congratulations</span></span>

<span data-ttu-id="c2098-246">Você acabou de implantar o seu primeiro aplicativo do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c2098-246">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="c2098-247">Enquanto caminha, você deverá ver uma malha de mapeamento espacial cobrindo todas as superfícies detectadas pelo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c2098-247">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="c2098-248">Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2098-248">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="c2098-249">Esses recursos são apenas alguns dos componentes fundamentais incluídos no MRTK.</span><span class="sxs-lookup"><span data-stu-id="c2098-249">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="c2098-250">Nos próximos tutoriais, você adicionará o conteúdo à sua cena para explorar as funcionalidades do HoloLens e do MRTK.</span><span class="sxs-lookup"><span data-stu-id="c2098-250">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c2098-251">Próximo tutorial: 3. Como configurar os perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="c2098-251">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
