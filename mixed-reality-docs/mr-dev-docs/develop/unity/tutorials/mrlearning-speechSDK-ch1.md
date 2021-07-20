---
title: Tutoriais de Serviços de Fala do Azure – 1. Integrar e usar a transcrição e o reconhecimento de fala
description: Conclua este curso para saber como implementar o SDK de Fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure, reconhecimento de fala, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 39eaa8a17d4616dc9c044f9bff7522dde41cffb7
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656633"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="fa708-105">1. Integrar e usar a transcrição e o reconhecimento de fala</span><span class="sxs-lookup"><span data-stu-id="fa708-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="fa708-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="fa708-106">Overview</span></span>

<span data-ttu-id="fa708-107">Nesta série de tutoriais, você criará um aplicativo de realidade misturada que explora o uso dos Serviços de Fala do Azure com o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fa708-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="fa708-108">Ao concluir esta série de tutoriais, você poderá usar o microfone do dispositivo para transcrever a conversão de fala em texto em tempo real, traduzir sua fala em outras linguagens e aproveitar o recurso de reconhecimento de Intenção para entender os comandos de voz usando inteligência artificial.</span><span class="sxs-lookup"><span data-stu-id="fa708-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="fa708-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="fa708-109">Objectives</span></span>

* <span data-ttu-id="fa708-110">Saiba como integrar os Serviços de Fala do Azure com um aplicativo do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fa708-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="fa708-111">Saiba como usar o reconhecimento de fala para transcrever texto</span><span class="sxs-lookup"><span data-stu-id="fa708-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fa708-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fa708-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="fa708-113">Se você ainda não concluiu a série de [Tutoriais de introdução](mr-learning-base-01.md), recomendamos que você a conclua primeiro.</span><span class="sxs-lookup"><span data-stu-id="fa708-113">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="fa708-114">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="fa708-114">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="fa708-115">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="fa708-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="fa708-116">Alguma habilidade básica de programação em C#</span><span class="sxs-lookup"><span data-stu-id="fa708-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="fa708-117">Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="fa708-117">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="fa708-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2020/2019 LTS instalado e o módulo Suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="fa708-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!Important]
> <span data-ttu-id="fa708-119">Essa série de tutoriais suporta o Unity 2020 LTS (atualmente 2020.3.x) se você estiver usando o Open XR ou o Windows XR Plugin, e também o Unity 2019 LTS (atualmente 2019.4.x) se estiver usando o Legacy WSA ou o Windows XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="fa708-119">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="fa708-120">Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="fa708-120">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="fa708-121">Como criar e preparar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="fa708-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="fa708-122">Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.</span><span class="sxs-lookup"><span data-stu-id="fa708-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="fa708-123">Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="fa708-123">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="fa708-124">[Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*</span><span class="sxs-lookup"><span data-stu-id="fa708-124">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="fa708-125">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="fa708-125">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="fa708-126">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="fa708-126">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="fa708-127">Como importar o Kit de ferramentas de Realidade Misturada e configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="fa708-127">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="fa708-128">[Criar e configurar a cena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) e dar um nome adequado à cena, por exemplo, *AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="fa708-128">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="fa708-129">Em seguida, siga as instruções em [Alterar a Opção de Exibição de Reconhecimento Espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para verificar se o perfil de configuração do MRTK da sua cena é o **DefaultHoloLens2ConfigurationProfile** e alterar as opções de exibição da malha de reconhecimento espacial para **Oclusão**.</span><span class="sxs-lookup"><span data-stu-id="fa708-129">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile**  and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="fa708-130">Como configurar o comportamento de início dos comandos de fala</span><span class="sxs-lookup"><span data-stu-id="fa708-130">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="fa708-131">Como você usará o SDK de Fala para reconhecimento de fala e transcrição, será necessário configurar os comandos de fala MRTK para que eles não interfiram na funcionalidade do SDK de Fala.</span><span class="sxs-lookup"><span data-stu-id="fa708-131">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="fa708-132">Para conseguir isso, você pode alterar o comportamento de início dos comandos de fala de Início Automático para Início Manual.</span><span class="sxs-lookup"><span data-stu-id="fa708-132">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="fa708-133">Com o objeto **MixedRealityToolkit** selecionado na janela Hierarquia, na janela Inspetor, selecione a guia **Entrada**, clone o **DefaultHoloLens2InputSystemProfile** e o **DefaultMixedRealitySpeechCommandsProfile** e, em seguida, altere o **Comportamento de Início** dos comandos de fala para **Início Manual**:</span><span class="sxs-lookup"><span data-stu-id="fa708-133">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech 1](images/mrlearning-speech/tutorial1-section2-step1-1.png)

## <a name="configuring-the-capabilities"></a><span data-ttu-id="fa708-135">Como configurar as funcionalidades</span><span class="sxs-lookup"><span data-stu-id="fa708-135">Configuring the capabilities</span></span>

<span data-ttu-id="fa708-136">No menu do Unity, selecione **Editar** > **Configurações de projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Configurações de Publicação**:</span><span class="sxs-lookup"><span data-stu-id="fa708-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech 2](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="fa708-138">Em **Configurações de publicação**, role para baixo até a seção **Funcionalidades** e verifique se as funcionalidades **InternetClient**, **Microphone** e **SpatialPerception**, que você habilitou ao criar o projeto no início do tutorial, estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="fa708-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which was enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="fa708-139">Em seguida, habilite as funcionalidades **InternetClientServer** e **PrivateNetworkClientServer**:</span><span class="sxs-lookup"><span data-stu-id="fa708-139">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech 3](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="fa708-141">Como importar os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="fa708-141">Importing the tutorial assets</span></span>

<span data-ttu-id="fa708-142">Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:</span><span class="sxs-lookup"><span data-stu-id="fa708-142">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="fa708-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (versão mais recente)</span><span class="sxs-lookup"><span data-stu-id="fa708-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="fa708-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="fa708-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="fa708-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="fa708-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage</span></span>](https://github.com/onginnovations/MixedRealityLearning/releases/download/azure-speech-services-v2.5.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage)

> [!TIP]
> <span data-ttu-id="fa708-146">Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções em [Como importar o Kit de Ferramentas de Realidade Misturada](mr-learning-base-04.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="fa708-146">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

<span data-ttu-id="fa708-147">Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="fa708-147">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech 4](images/mrlearning-speech/tutorial1-section4-step1-1.png)

<span data-ttu-id="fa708-149">Você precisa configurar o projeto do Unity para publicar os plug-ins de Fala do Azure para ARM64. Para fazer isso na janela do Projeto, navegue até **Ativos** > **SpeechSDK** > **Plug-ins** > **WSA** > **ARM64** e selecione o plug-in **Microsoft.CognitiveServices.Speech.core**.</span><span class="sxs-lookup"><span data-stu-id="fa708-149">You need to setup the Unity project to publish the Azure Speech plugins for ARM64,to do this in the Project window, navigate to **Assets** > **SpeechSDK** > **Plugins** > **WSA** > **ARM64** and select **Microsoft.CognitiveServices.Speech.core** plugin.</span></span>

![mrlearning-speech 5](images/mrlearning-speech/tutorial1-section4-step1-2.PNG)

<span data-ttu-id="fa708-151">com o plug-in **Microsoft.CognitiveServices.Speech.core** ainda selecionado, na janela inspetor Ativar **WSA Player** em **Configurações da plataforma**, selecione **UWP** para SDK, **ARM64** para CPU e clique em Aplicar para aplicar essas configurações ao plug-in.</span><span class="sxs-lookup"><span data-stu-id="fa708-151">with **Microsoft.CognitiveServices.Speech.core** plugin still selected, in the inspector window Enable **WSA Player** then under **Platform settings** select **UWP** for SDK, **ARM64** for CPU and click on Apply to apply these settings to the plugin.</span></span>

![mrlearning-speech 6](images/mrlearning-speech/tutorial1-section4-step1-3.PNG)

<span data-ttu-id="fa708-153">Repita essas etapas para cada um dos plug-ins restantes:</span><span class="sxs-lookup"><span data-stu-id="fa708-153">Repeat this steps for each of the remaining plugins:</span></span>

* <span data-ttu-id="fa708-154">**Microsoft.CognitiveServices.Speech.extension.audio.sys**</span><span class="sxs-lookup"><span data-stu-id="fa708-154">**Microsoft.CognitiveServices.Speech.extension.audio.sys**</span></span>
* <span data-ttu-id="fa708-155">**Microsoft.CognitiveServices.Speech.extension.kws**</span><span class="sxs-lookup"><span data-stu-id="fa708-155">**Microsoft.CognitiveServices.Speech.extension.kws**</span></span>
* <span data-ttu-id="fa708-156">**Microsoft.CognitiveServices.Speech.extension.lu**</span><span class="sxs-lookup"><span data-stu-id="fa708-156">**Microsoft.CognitiveServices.Speech.extension.lu**</span></span>
* <span data-ttu-id="fa708-157">**Microsoft.CognitiveServices.Speech.extension.silk_codec**</span><span class="sxs-lookup"><span data-stu-id="fa708-157">**Microsoft.CognitiveServices.Speech.extension.silk_codec**</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="fa708-158">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="fa708-158">Preparing the scene</span></span>

<span data-ttu-id="fa708-159">Nesta seção, você vai preparar a cena adicionando o tutorial pré-fabricado e configurar o componente do Controlador Lunarcom (Script) para controlar sua cena.</span><span class="sxs-lookup"><span data-stu-id="fa708-159">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="fa708-160">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutoriais.AzureSpeechServices** > **Pré-fabricados** e arraste o pré-fabricado **Lunarcom** para a janela Hierarquia para adicioná-lo à sua cena:</span><span class="sxs-lookup"><span data-stu-id="fa708-160">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech 7](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="fa708-162">Com o objeto **Lunarcom** ainda selecionado na janela Hierarquia, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Controlador do Lunarcom (Script)** ao objeto Lunarcom:</span><span class="sxs-lookup"><span data-stu-id="fa708-162">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech 8](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="fa708-164">O componente Controlador do Lunarcom (Script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="fa708-164">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="fa708-165">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="fa708-165">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="fa708-166">Com o objeto **Lunarcom** ainda selecionado, expanda-o para revelar seus objetos filho e, em seguida, arraste o objeto **Terminal** para o campo **Terminal** do componente Controlador do Lunarcom (Script):</span><span class="sxs-lookup"><span data-stu-id="fa708-166">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech 9](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="fa708-168">Com o objeto **Lunarcom** ainda selecionado, expanda o objeto Terminal para revelar seus objetos filho e, em seguida, arraste o objeto **ConnectionLight** para o campo **Luz de Conexão** do componente Controlador do Lunarcom (Script) e o objeto **OutputText** para o campo **Texto de Saída**:</span><span class="sxs-lookup"><span data-stu-id="fa708-168">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech 10](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="fa708-170">Com o objeto **Lunarcom** ainda selecionado, expanda o objeto Botões para revelar seus objetos filho e, em seguida, na janela Inspetor, expanda a lista **Botões**, defina seu **Tamanho** como 3 e arraste os objetos **MicButton**, **SatelliteButton** e **RocketButton** para os campos 0, 1 e 2 do **Elemento**, respectivamente:</span><span class="sxs-lookup"><span data-stu-id="fa708-170">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech 11](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="fa708-172">Como conectar o projeto do Unity ao recurso do Azure</span><span class="sxs-lookup"><span data-stu-id="fa708-172">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="fa708-173">Para usar os Serviços de Fala do Azure, você precisa criar um recurso do Azure e obter uma chave de API para o Serviço de Fala.</span><span class="sxs-lookup"><span data-stu-id="fa708-173">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="fa708-174">Siga as instruções de [Experimentar o serviço de Fala gratuitamente](/azure/cognitive-services/speech-service/get-started) e tome nota da sua região de serviço (também conhecida como Localização) e a chave de API (também conhecida como Key1 ou Key2).</span><span class="sxs-lookup"><span data-stu-id="fa708-174">Follow the [Try the Speech service for free](/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="fa708-175">Na janela Hierarquia, selecione o objeto **Lunarcom**, então, na janela Inspetor, localize a seção **Credenciais do SDK de Fala** do componente **Controlador do Lunarcom (Script)** e configure-a da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="fa708-175">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="fa708-176">No campo **Chave de API do Serviço de Fala**, insira sua chave de API (Key1 ou Key2)</span><span class="sxs-lookup"><span data-stu-id="fa708-176">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="fa708-177">No campo **Região do Serviço de Fala**, insira sua região de serviço (Localização) usando letras minúsculas e espaços removidos</span><span class="sxs-lookup"><span data-stu-id="fa708-177">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech 12](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="fa708-179">Como usar o reconhecimento de fala para transcrever a fala</span><span class="sxs-lookup"><span data-stu-id="fa708-179">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="fa708-180">Na janela Hierarquia, selecione o objeto **Lunarcom** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Reconhecedor de Fala do Lunarcom (Script)** ao objeto Lunarcom:</span><span class="sxs-lookup"><span data-stu-id="fa708-180">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech 13](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="fa708-182">O componente Reconhecedor de Fala do Lunarcom (Script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="fa708-182">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="fa708-183">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="fa708-183">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="fa708-184">Se agora você entrar no modo de Jogo, poderá testar o reconhecimento de fala pressionando primeiro o botão de microfone:</span><span class="sxs-lookup"><span data-stu-id="fa708-184">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech 14](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="fa708-186">Em seguida, supondo que o computador tenha um microfone, quando você disser algo, sua fala será transcrita no painel do terminal:</span><span class="sxs-lookup"><span data-stu-id="fa708-186">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech 15](images/mrlearning-speech/tutorial1-section7-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="fa708-188">O aplicativo precisa se conectar ao Azure, portanto, verifique se o computador/dispositivo está conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="fa708-188">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="fa708-189">Parabéns</span><span class="sxs-lookup"><span data-stu-id="fa708-189">Congratulations</span></span>

<span data-ttu-id="fa708-190">Você implementou o reconhecimento de fala da plataforma Azure.</span><span class="sxs-lookup"><span data-stu-id="fa708-190">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="fa708-191">Execute o aplicativo em seu dispositivo para garantir que o recurso esteja funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="fa708-191">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="fa708-192">No próximo tutorial, você aprenderá a executar comandos usando o reconhecimento de fala do Azure.</span><span class="sxs-lookup"><span data-stu-id="fa708-192">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fa708-193">Próximo tutorial: 2. Executar comandos usando o reconhecimento de fala do Azure</span><span class="sxs-lookup"><span data-stu-id="fa708-193">Next tutorial: 2. Execute commands using Azure speech recognition</span></span>](mrlearning-speechSDK-ch2.md)
