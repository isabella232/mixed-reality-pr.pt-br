---
title: Como inicializar o seu projeto e implantar o primeiro aplicativo
description: Este curso mostra como configurar seu projeto do Unity para o MRTK (Kit de Ferramentas de Realidade Misturada) e como implantá-lo no HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 2ce119e1dd18eacf02088d00e99fb70d06bf956e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008216"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="a5576-104">2. Como inicializar o seu projeto e implantar o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="a5576-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="a5576-105">Neste tutorial, você aprenderá a criar um projeto do Unity, configurá-lo para o desenvolvimento do <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK (Kit de Ferramentas de Realidade Misturada)</a> e importar o MRTK.</span><span class="sxs-lookup"><span data-stu-id="a5576-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="a5576-106">Você também aprenderá mais sobre como configurar, compilar e implantar uma cena básica do Unity do Visual Studio para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a5576-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="a5576-107">Depois de implantá-la no HoloLens 2, você verá uma malha de mapeamento espacial que abrange as superfícies percebidas pelo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a5576-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="a5576-108">Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5576-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="a5576-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="a5576-109">Objectives</span></span>

* <span data-ttu-id="a5576-110">Saiba como configurar o Unity para o desenvolvimento no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a5576-110">Learn how to configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="a5576-111">Saiba como criar e implantar seu aplicativo no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a5576-111">Learn how to build and deploy your app to HoloLens.</span></span>
* <span data-ttu-id="a5576-112">Experimente a malha de mapeamento espacial, as malhas de mão e o contador da taxa de quadros no dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a5576-112">Experience the spatial mapping mesh, hand meshes, and  framerate counter on your HoloLens 2 device.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="a5576-113">Como criar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="a5576-113">Creating the Unity project</span></span>

1. <span data-ttu-id="a5576-114">Inicie o **Hub do Unity**, selecione a guia **Projetos** e clique na **seta para baixo** ao lado do botão **Novo**:</span><span class="sxs-lookup"><span data-stu-id="a5576-114">Launch **Unity Hub**, select the **Projects** tab, and then click the **down arrow** next to the **New** button:</span></span>

![Hub do Unity com a seta para baixo do botão "Novo" realçada](images/mr-learning-base/base-02-section1-step1-1.png)

2. <span data-ttu-id="a5576-116">No menu suspenso, selecione a versão do Unity especificada nos [Pré-requisitos](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="a5576-116">In the dropdown menu, select the Unity version specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Selecionar a versão do Unity](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="a5576-118">Se a versão específica do Unity não estiver disponível no Hub do Unity, você poderá iniciar a instalação em <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Arquivos de Download</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="a5576-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

3. <span data-ttu-id="a5576-119">Na janela **Criar um projeto**, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a5576-119">In the **Create a new project** window, do the following:</span></span>

    * <span data-ttu-id="a5576-120">Verifique se **Modelos** está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="a5576-120">Ensure **Templates** is set to **3D**.</span></span>
    * <span data-ttu-id="a5576-121">Na caixa **Nome do Projeto**, insira um nome adequado para seu projeto (por exemplo, "Tutoriais do MRTK").</span><span class="sxs-lookup"><span data-stu-id="a5576-121">In the **Project Name** box, enter a suitable name for your project (for example, "MRTK Tutorials").</span></span>
    * <span data-ttu-id="a5576-122">Clique no botão de três pontos ao lado de **Localização** e procure a pasta em que deseja salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="a5576-122">Click the three-dot button next to **Location**, and then navigate to the folder where you want to save your project.</span></span>

> [!CAUTION]
> <span data-ttu-id="a5576-123">Ao trabalhar no Windows, há um limite de MAX_PATH de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="a5576-123">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="a5576-124">Por conta disso, você deve salvar o projeto do Unity próximo à raiz da unidade.</span><span class="sxs-lookup"><span data-stu-id="a5576-124">Because of this, you should save the Unity project close to the root of the drive.</span></span>

    * <span data-ttu-id="a5576-125">Selecione o botão **Criar**.</span><span class="sxs-lookup"><span data-stu-id="a5576-125">Click the **Create** button.</span></span> <span data-ttu-id="a5576-126">Isso cria e inicia o projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="a5576-126">This creates and launches your new Unity project.</span></span>

![Hub do Unity com a janela "Criar um projeto" preenchida](images/mr-learning-base/base-02-section1-step1-3.png)

<span data-ttu-id="a5576-128">A barra de status mantém você atualizado sobre seu progresso.</span><span class="sxs-lookup"><span data-stu-id="a5576-128">The status bar keeps you updated on your progress.</span></span>

![A barra de progresso do Unity mantém você atualizado sobre o status de "criar projeto"](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="a5576-130">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="a5576-130">Switching the build platform</span></span>

1. <span data-ttu-id="a5576-131">Na barra de menus, selecione **Arquivo** > **Configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="a5576-131">On the menu bar, select **File** > **Build Settings...**</span></span>

![Caminho do menu Configurações de Build... do Unity](images/mr-learning-base/base-02-section2-step1-1.png)

2. <span data-ttu-id="a5576-133">Na janela **Configurações de Build**, selecione **Plataforma Universal do Windows** e clique no botão **Mudar Plataforma**:</span><span class="sxs-lookup"><span data-stu-id="a5576-133">In the **Build Settings** window, select **Universal Windows Platform** and then click the **Switch Platform** button:</span></span>

![Janela Configurações de Build do Unity com o UWP selecionado para alternar a plataforma da opção Autônomo](images/mr-learning-base/base-02-section2-step1-2.png)

3. <span data-ttu-id="a5576-135">Aguarde até que o Unity termine de mudar a plataforma e feche a janela **Configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="a5576-135">Wait for Unity to finish switching the platform, and then close the **Build Settings** window.</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="a5576-136">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="a5576-136">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="a5576-137">Os Recursos Essenciais do TextMeshPro são exigidos pelos elementos da interface do usuário do MRTK.</span><span class="sxs-lookup"><span data-stu-id="a5576-137">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="a5576-138">Se não estiver planejando usar os elementos de interface do usuário do MRTK no seu projeto, ignore esta etapa.</span><span class="sxs-lookup"><span data-stu-id="a5576-138">If you are not planning to use MRTK's UI elements in your project, you can skip this step.</span></span>

1. <span data-ttu-id="a5576-139">Na barra de menus, selecione **Janela** > **TextMeshPro** > **Importar Recursos Essenciais do TMP**.</span><span class="sxs-lookup"><span data-stu-id="a5576-139">On the menu bar, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

![Caminho do menu Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-1.png)

2. <span data-ttu-id="a5576-141">Na janela **Importar Pacote do Unity**, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:</span><span class="sxs-lookup"><span data-stu-id="a5576-141">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets:</span></span>

![Janela Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="a5576-143">Como importar o Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="a5576-143">Importing the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="a5576-144">Baixe o pacote personalizado do Unity:</span><span class="sxs-lookup"><span data-stu-id="a5576-144">Download the Unity custom package:</span></span>

    [<span data-ttu-id="a5576-145">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a5576-145">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. <span data-ttu-id="a5576-146">Na barra de menus, selecione **Ativos** > **Importar Pacote** > **Pacote Personalizado...** .</span><span class="sxs-lookup"><span data-stu-id="a5576-146">On the menu bar, select **Assets** > **Import Package** > **Custom Package...**.</span></span>
3. <span data-ttu-id="a5576-147">Na caixa de diálogo **Importar pacote...** , procure a localização do pacote recém-baixado, selecione-o e clique no botão **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="a5576-147">In the **Import package...** dialog, navigate to the location of the package you just downloaded, then select it, and then click the **Open** button.</span></span>
4. <span data-ttu-id="a5576-148">Na janela **Importar Pacote do Unity**, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos.</span><span class="sxs-lookup"><span data-stu-id="a5576-148">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets.</span></span>

## <a name="selecting-mrtk-and-project-settings"></a><span data-ttu-id="a5576-149">Como selecionar as configurações de projeto e do MRTK</span><span class="sxs-lookup"><span data-stu-id="a5576-149">Selecting MRTK and project settings</span></span>

<span data-ttu-id="a5576-150">Depois que o Unity terminar de importar o pacote da seção anterior, a janela **Configurador de Projeto do MRTK** será exibida.</span><span class="sxs-lookup"><span data-stu-id="a5576-150">After Unity has finished importing the package from the previous section, the **MRTK Project Configurator** window should appear.</span></span> <span data-ttu-id="a5576-151">Caso contrário, você pode abri-la manualmente acessando **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity**:</span><span class="sxs-lookup"><span data-stu-id="a5576-151">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Caminho do menu Configurar Projeto do Unity no Unity](images/mr-learning-base/base-02-section5-step1-1.png)

1. <span data-ttu-id="a5576-153">Na janela **Configurador de Projeto do MRTK**, expanda a seção **Modificar Configurações**, se necessário, e verifique se todas as opções estão selecionadas.</span><span class="sxs-lookup"><span data-stu-id="a5576-153">In the **MRTK Project Configurator** window, expand the **Modify Configurations** section, if necessary, and then ensure that all options are selected.</span></span>

![Janela Configurador de Projeto do MRTK no Unity com a opção Modificar Configurações exibida](images/mr-learning-base/base-02-section5-step1-2.png)

2. <span data-ttu-id="a5576-155">Para aplicar as configurações, clique no botão **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="a5576-155">To apply the settings, click the **Apply** button.</span></span>

![Botão Aplicar no MRTK](images/mr-learning-base/apply.png)

> [!NOTE]
> <span data-ttu-id="a5576-157">Você está usando o XR herdado interno do Unity em vez do novo Sistema de Plug-ins do XR, porque o novo sistema não é totalmente compatível com as [versões recomendadas do Unity e do MRTK](mr-learning-base-01.md#prerequisites) para esta série de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="a5576-157">You are using Unity's built-in legacy XR instead of the new XR Plugin System because the new system is not fully compatible with the [recommended Unity and MRTK versions](mr-learning-base-01.md#prerequisites) for this tutorial series.</span></span> <span data-ttu-id="a5576-158">Se você receber algum aviso sobre o XR interno ser preterido, ignore-o.</span><span class="sxs-lookup"><span data-stu-id="a5576-158">If you see any warnings about built-in XR being deprecated, you can ignore them.</span></span>

> [!TIP]
> <span data-ttu-id="a5576-159">A aplicação das Configurações Padrão do MRTK é opcional, mas altamente recomendável, pois ela ajudará a definir algumas das configurações recomendadas do Unity:</span><span class="sxs-lookup"><span data-stu-id="a5576-159">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>
>
> * <span data-ttu-id="a5576-160">Habilitar o XR herdado: habilita a VR para o projeto.</span><span class="sxs-lookup"><span data-stu-id="a5576-160">Enable legacy XR: Enables VR for the project.</span></span>
> * <span data-ttu-id="a5576-161">Definir o caminho de renderização com uma Instância de Passagem Única: aprimora o desempenho gráfico executando o pipeline de renderização dos dois olhos na mesma chamada de desenho.</span><span class="sxs-lookup"><span data-stu-id="a5576-161">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="a5576-162">Para saber mais sobre este tópico, veja a seção [Renderização com uma Instância de Passagem Única](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) da documentação [Desempenho](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) do MRTK.</span><span class="sxs-lookup"><span data-stu-id="a5576-162">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="a5576-163">Definir camada padrão de Reconhecimento Espacial: cria uma camada do Unity chamada Reconhecimento Espacial e configura o MRTK para usá-la na malha de reconhecimento espacial.</span><span class="sxs-lookup"><span data-stu-id="a5576-163">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="a5576-164">Para saber mais sobre as Camadas do Unity, veja a documentação <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Como personalizar seu workspace</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="a5576-164">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

3. <span data-ttu-id="a5576-165">Na barra de menus, selecione **Editar** > **Configurações de Projeto...** .</span><span class="sxs-lookup"><span data-stu-id="a5576-165">On the menu bar, select **Edit** > **Project Settings...** .</span></span>

4. <span data-ttu-id="a5576-166">Na janela **Configurações de Projeto**, selecione **Player**, clique na lista suspensa **Configurações de XR** e escolha a caixa ao lado de **Realidade Virtual Compatível**:</span><span class="sxs-lookup"><span data-stu-id="a5576-166">In the **Project Settings** window, select **Player**, then click the **XR Settings** dropdown, and then select the box next to **Virtual Reality Supported**:</span></span>

![Configurações de XR no Unity com a opção Realidade Virtual Compatível exibida](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="a5576-168">Isso importa o SDK do Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="a5576-168">This imports the Windows Mixed Reality SDK:</span></span>

![Configurações de XR no Unity com a opção SDKs de Realidade Virtual exibida](images/mr-learning-base/mixed-reality-sdk.png)

<span data-ttu-id="a5576-170">Depois que o Unity terminar de importar o SDK do Windows Mixed Reality, a janela **Configurador de Projeto do MRTK** será exibida novamente.</span><span class="sxs-lookup"><span data-stu-id="a5576-170">After Unity has finished importing the Windows Mixed Reality SDK, the **MRTK Project Configurator** window should appear again.</span></span> <span data-ttu-id="a5576-171">Caso contrário, selecione **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity** para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="a5576-171">If it doesn't, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open it.</span></span>

5. <span data-ttu-id="a5576-172">Na janela **Configurador de Projeto do MRTK**, clique na lista suspensa **Espacializador de áudio** e selecione **Espacializador MS HRTF**.</span><span class="sxs-lookup"><span data-stu-id="a5576-172">In the **MRTK Project Configurator** window, click the **Audio spatializer** dropdown, and then select **MS HRTF Spatializer**.</span></span>

![Configurações de projeto com as opções Espacializador de áudio exibidas](images/mr-learning-base/base-02-section5-step2-3.png)

6. <span data-ttu-id="a5576-174">Clique no botão **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="a5576-174">Click the **Apply** button.</span></span> <span data-ttu-id="a5576-175">Isso fechará a janela **Configurador de Projeto do MRTK**.</span><span class="sxs-lookup"><span data-stu-id="a5576-175">This closes the **MRTK Project Configurator** window.</span></span>

    > [!TIP]
    > <span data-ttu-id="a5576-176">A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a5576-176">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="a5576-177">Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="a5576-177">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="a5576-178">Para saber mais sobre este tópico, veja os Tutoriais sobre áudio espacial.</span><span class="sxs-lookup"><span data-stu-id="a5576-178">To learn more about this topic, you can refer to the Spatial audio tutorials.</span></span>

7. <span data-ttu-id="a5576-179">Na janela **Configurações de Projeto**, clique na lista suspensa **Formato de Profundidade** e selecione **Profundidade de 16 bits**:</span><span class="sxs-lookup"><span data-stu-id="a5576-179">In the **Project Settings** window, click the **Depth Format** dropdown, and then select **16-bit depth**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="Configurações de XR do Unity com profundidade de 16 bits selecionada.":::

    > [!TIP]
    > <span data-ttu-id="a5576-181">A redução do formato de profundidade para 16 bits é opcional, mas pode ajudar a aprimorar o desempenho gráfico no projeto.</span><span class="sxs-lookup"><span data-stu-id="a5576-181">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="a5576-182">Para saber mais sobre este tópico, veja a seção [Compartilhamento de buffer de profundidade (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) da documentação [Desempenho](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) do MRTK.</span><span class="sxs-lookup"><span data-stu-id="a5576-182">To learn more about this topic, you can refer to the [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>

8. <span data-ttu-id="a5576-183">Clique na lista suspensa **Configurações de Publicação** e, na caixa **Nome do pacote**, insira um nome adequado (por exemplo, "MRTK-Tutoriais-Getting-Started").</span><span class="sxs-lookup"><span data-stu-id="a5576-183">Click the **Publishing Settings** drop-down, and then in the **Package name** box, enter a suitable name (for example, "MRTK-Tutorials-Getting-Started").</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="Configurações de Publicação do Unity com o Nome do pacote configurado.":::

    <span data-ttu-id="a5576-185">**Nome do Pacote e Nome do Produto**</span><span class="sxs-lookup"><span data-stu-id="a5576-185">**Package Name and Product Name**</span></span>

    - <span data-ttu-id="a5576-186">O 'Nome do pacote' é o identificador exclusivo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5576-186">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="a5576-187">Você deve criar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a5576-187">You should create this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>
    - <span data-ttu-id="a5576-188">O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a5576-188">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="a5576-189">Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.</span><span class="sxs-lookup"><span data-stu-id="a5576-189">To make the app easier to locate during development, you can add an underscore in front of the name to sort it to the top.</span></span>

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="Configurações de Projeto do Unity com o Nome de produto configurado.":::

9. <span data-ttu-id="a5576-191">Feche a janela **Configurações de Projeto**.</span><span class="sxs-lookup"><span data-stu-id="a5576-191">Close the **Project Settings** window.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="a5576-192">Como criar e configurar a cena</span><span class="sxs-lookup"><span data-stu-id="a5576-192">Creating and configuring the scene</span></span>

1. <span data-ttu-id="a5576-193">Na barra de menus, selecione **Arquivo** > **Nova Cena**.</span><span class="sxs-lookup"><span data-stu-id="a5576-193">On the menu bar, select **File** > **New Scene**.</span></span>
2. <span data-ttu-id="a5576-194">Para adicionar o MRTK à cena, na barra de menus, selecione **Kit de Ferramentas de Realidade Misturada** > **Adicionar à Cena e Configurar...** .</span><span class="sxs-lookup"><span data-stu-id="a5576-194">To add the MRTK to the scene, on the menu bar, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Caminho do menu Adicionar à Cena e Configurar... do Unity.":::

3. <span data-ttu-id="a5576-196">Na janela **Hierarquia**, verifique se **MixedRealityToolkit** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="a5576-196">In the **Hierarchy** window, ensure that **MixedRealityToolkit** is selected.</span></span>

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="Verificar se MixedRealityTookit está selecionado.":::

4. <span data-ttu-id="a5576-198">Na seção **MixedRealityToolkit** da janela **Inspetor**, confirme se o perfil de configuração está definido como **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="a5576-198">In the **Inspector** window's **MixedRealityToolkit** section, verify that the configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="Componente MixedRealityToolkit do Unity com DefaultMixedRealityTookitConfigurationProfile selecionado.":::

    > [!IMPORTANT]
    > <span data-ttu-id="a5576-200">Normalmente, você usará o DefaultHoloLens2ConfigurationProfile ao desenvolver para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a5576-200">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="a5576-201">No entanto, para este tutorial, você usará o DefaultMixedRealityToolkitConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="a5576-201">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile.</span></span> <span data-ttu-id="a5576-202">No próximo tutorial, [Como configurar os perfis do MRTK](mr-learning-base-03.md), você o trocará pelo DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="a5576-202">In the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

5. <span data-ttu-id="a5576-203">Na barra de menus, selecione **Arquivo** > **Salvar como...**</span><span class="sxs-lookup"><span data-stu-id="a5576-203">On the menu bar, select **File** > **Save As...**</span></span>
6. <span data-ttu-id="a5576-204">Na caixa de diálogo **Salvar Cena**, procure a pasta **Cenas** do projeto.</span><span class="sxs-lookup"><span data-stu-id="a5576-204">In the **Save Scene** dialog, navigate to your project's **Scenes** folder.</span></span> <span data-ttu-id="a5576-205">Na caixa **Nome do arquivo**, dê um nome adequado à sua cena (por exemplo, "\_GettingStarted\_") e clique no botão **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="a5576-205">In the **File name** box, give your scene a suitable name (for example, "\_GettingStarted\_"), and then click the **Save** button.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Janela do prompt Salvar para salvar a cena do Unity.":::

## <a name="building-and-deploying-to-your-hololens-2"></a><span data-ttu-id="a5576-207">Build e implantação no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a5576-207">Building and deploying to your HoloLens 2</span></span>

> <span data-ttu-id="a5576-208">Antes do build no seu dispositivo, confirme o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a5576-208">Before building to your device, confirm the following:</span></span>
- <span data-ttu-id="a5576-209">Seu dispositivo está no Modo de Desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="a5576-209">Your device is in Developer Mode.</span></span>
- <span data-ttu-id="a5576-210">Ele está emparelhado com o computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="a5576-210">Your device is paired with your development computer.</span></span> <span data-ttu-id="a5576-211">Caso contrário, você verá a seguinte caixa de diálogo no Visual Studio durante o processo de build:</span><span class="sxs-lookup"><span data-stu-id="a5576-211">If it's not, you will see the following dialog box in Visual Studio during the build process:</span></span>

![Como inserir o PIN para emparelhamento de dispositivos](images/mr-learning-base/pin-request.png)

 <span data-ttu-id="a5576-213">Para saber mais sobre essas duas etapas, confira [Como usar o Visual Studio para implantação e depuração](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="a5576-213">To learn more about both of these steps, see [Using Visual Studio to deploy and debug](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

1. <span data-ttu-id="a5576-214">Na barra de menus, selecione **Arquivo** > **Configurações de Build...** .</span><span class="sxs-lookup"><span data-stu-id="a5576-214">On the menu bar, select **File** > **Build Settings...**.</span></span>
2. <span data-ttu-id="a5576-215">Na janela **Configurações de Build**, clique no botão **Adicionar Cenas Abertas** para adicionar a cena atual à lista de **Cenas no Build**.</span><span class="sxs-lookup"><span data-stu-id="a5576-215">In the **Build Settings** window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span>

![Adicionar a cena atual à lista "Cenas no Build"](images/mr-learning-base/base-02-section7-step1-1.png)

3. <span data-ttu-id="a5576-217">Clique no botão **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="a5576-217">Click the **Build** button.</span></span>

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="Clique no botão Compilar.":::

4. <span data-ttu-id="a5576-219">Na caixa de diálogo **Compilar Plataforma Universal do Windows**, escolha uma localização adequada para armazenar o build (por exemplo, o ideal é criar uma pasta "Builds" na pasta "Tutoriais do MRTK").</span><span class="sxs-lookup"><span data-stu-id="a5576-219">In the **Build Universal Windows Platform** dialog, choose a suitable location to store your build (for example, you may want to create a "Builds" folder in your "MRTK Tutorials" folder).</span></span> <span data-ttu-id="a5576-220">Crie uma pasta e dê a ela um nome adequado (por exemplo, "GettingStarted"). Selecione a pasta e clique no botão **Selecionar Pasta** para iniciar o processo de build.</span><span class="sxs-lookup"><span data-stu-id="a5576-220">Create a new folder and give it a suitable name (for example, "GettingStarted"), then select the folder, and then click the **Select Folder** button to start the build process.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="Janela Build do Unity com a pasta de build exibida.":::

    <span data-ttu-id="a5576-222">Uma barra de status será exibida e manterá você atualizado sobre o progresso do build.</span><span class="sxs-lookup"><span data-stu-id="a5576-222">A status bar appears and keeps you updated on your build progress.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Processo de build do Unity em andamento.":::

    > [!TIP]
    > <span data-ttu-id="a5576-224">Você também pode implantar no [Emulador do HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou criar um [Pacote do Aplicativo](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) para sideload.</span><span class="sxs-lookup"><span data-stu-id="a5576-224">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

5. <span data-ttu-id="a5576-225">Quando o processo de build for concluído, no Explorador de Arquivos, procure a localização em que você armazenou o build e clique duas vezes no arquivo de solução para abri-lo no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="a5576-225">When the build process has completed, in File Explorer, navigate to the location where you stored the build, and then double-click the solution file to open it in Visual Studio:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Windows Explorer com o arquivo de solução do Visual Studio recém-criado selecionado.":::

    > [!NOTE]
    > <span data-ttu-id="a5576-227">Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar-se de que você tenha todos os componentes de pré-requisitos na documentação **[Instalar as Ferramentas](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="a5576-227">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

6. <span data-ttu-id="a5576-228">Configure o Visual Studio para o HoloLens selecionando a configuração **Mestre** ou **Versão**, a arquitetura **ARM64** e **Dispositivo** como o destino.</span><span class="sxs-lookup"><span data-stu-id="a5576-228">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as the target.</span></span>

    > [!TIP]
    > <span data-ttu-id="a5576-229">Se você estiver implantando no HoloLens (1ª geração), selecione a arquitetura **x86**.</span><span class="sxs-lookup"><span data-stu-id="a5576-229">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="Visual Studio configurado para implantação no HoloLens 2.":::

    > [!NOTE]
    > <span data-ttu-id="a5576-231">Para o HoloLens, você normalmente criará para a arquitetura ARM.</span><span class="sxs-lookup"><span data-stu-id="a5576-231">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="a5576-232">No entanto, há um <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conhecido</strong></a> no Unity 2019.3 que causa erros ao selecionar o ARM como a arquitetura de build no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5576-232">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="a5576-233">A solução alternativa recomendada é criar para o ARM64.</span><span class="sxs-lookup"><span data-stu-id="a5576-233">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="a5576-234">Se essa não for uma opção, acesse **Editar > Configurações de Projeto > Player > Outras Configurações** e desabilite **Trabalhos Gráficos**.</span><span class="sxs-lookup"><span data-stu-id="a5576-234">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a5576-235">Se o Dispositivo não for exibido como uma opção de destino, talvez seja necessário alterar o projeto de inicialização para a solução do Visual Studio do projeto IL2CPP para o projeto UWP.</span><span class="sxs-lookup"><span data-stu-id="a5576-235">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="a5576-236">Para fazer isso, no Gerenciador de Soluções, clique com o botão direito do mouse em NomeDoProjeto (Universal do Windows) e selecione **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="a5576-236">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows), and then select **Set as StartUp Project**.</span></span>

7. <span data-ttu-id="a5576-237">Conecte o HoloLens ao computador e siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="a5576-237">Connect your HoloLens to your computer, and then do one of the following:</span></span>
- <span data-ttu-id="a5576-238">Para compilar o aplicativo, implante-o no HoloLens e inicie-o automaticamente sem o depurador do Visual Studio anexado. Na barra de menus, selecione **Depurar** > **Iniciar Sem Depuração**.</span><span class="sxs-lookup"><span data-stu-id="a5576-238">To build the app, deploy it to your HoloLens, and start it automatically without the Visual Studio debugger attached, on the menu bar, select **Debug** > **Start Without Debugging**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Caminho do menu Iniciar Sem Depuração do Visual Studio.":::

- <span data-ttu-id="a5576-240">Para compilar e implantar o aplicativo no HoloLens, mas não o iniciar automaticamente, na barra de menus, selecione **Build > Implantar Solução**.</span><span class="sxs-lookup"><span data-stu-id="a5576-240">To build and deploy the app to your HoloLens but not have it start automatically, on the menu bar, select **Build > Deploy Solution**.</span></span>

    > [!NOTE]
    ><span data-ttu-id="a5576-241">Observe o criador de perfil de Diagnóstico no aplicativo, você pode ativar ou desativar a sua visibilidade usando o comando de fala **Alternar Diagnóstico**.</span><span class="sxs-lookup"><span data-stu-id="a5576-241">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="a5576-242">É recomendável que você mantenha o criador de perfil visível na maior parte do tempo durante o desenvolvimento para entender quando as alterações no aplicativo podem afetar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="a5576-242">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="a5576-243">Por exemplo, os aplicativos do HoloLens devem [ser executados continuamente em 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="a5576-243">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="a5576-244">Parabéns</span><span class="sxs-lookup"><span data-stu-id="a5576-244">Congratulations</span></span>

<span data-ttu-id="a5576-245">Você acabou de implantar o seu primeiro aplicativo do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a5576-245">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="a5576-246">Enquanto caminha, você deverá ver uma malha de mapeamento espacial cobrindo todas as superfícies detectadas pelo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a5576-246">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="a5576-247">Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5576-247">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="a5576-248">Esses recursos são apenas alguns dos componentes fundamentais incluídos no MRTK.</span><span class="sxs-lookup"><span data-stu-id="a5576-248">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="a5576-249">Nos próximos tutoriais, você adicionará o conteúdo à sua cena para explorar as funcionalidades do HoloLens e do MRTK.</span><span class="sxs-lookup"><span data-stu-id="a5576-249">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a5576-250">Próximo tutorial: 3. Como configurar os perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="a5576-250">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
