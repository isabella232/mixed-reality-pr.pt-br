---
title: Tutoriais de Serviços de Fala do Azure – 1. Integrar e usar a transcrição e o reconhecimento de fala
description: Conclua este curso para saber como implementar o SDK de Fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 07130f7d8f10464219458be4ddd5c420a0512b51
ms.sourcegitcommit: 8fd127aff85b77778bd7a75c5ec5215d27ecf21a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93416982"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="a831f-105">1. Integrar e usar a transcrição e o reconhecimento de fala</span><span class="sxs-lookup"><span data-stu-id="a831f-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="a831f-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="a831f-106">Overview</span></span>


<span data-ttu-id="a831f-107">Nesta série de tutoriais, você criará um aplicativo de realidade misturada que explora o uso dos Serviços de Fala do Azure com o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a831f-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="a831f-108">Ao concluir esta série de tutoriais, você poderá usar o microfone do dispositivo para transcrever a conversão de fala em texto em tempo real, traduzir sua fala em outras linguagens e aproveitar o recurso de reconhecimento de Intenção para entender os comandos de voz usando inteligência artificial.</span><span class="sxs-lookup"><span data-stu-id="a831f-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="a831f-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="a831f-109">Objectives</span></span>

* <span data-ttu-id="a831f-110">Saiba como integrar os Serviços de Fala do Azure com um aplicativo do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a831f-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="a831f-111">Saiba como usar o reconhecimento de fala para transcrever texto</span><span class="sxs-lookup"><span data-stu-id="a831f-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a831f-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a831f-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="a831f-113">Se você ainda não concluiu a série de [Tutoriais de introdução](mr-learning-base-01.md), recomendamos que você a conclua primeiro.</span><span class="sxs-lookup"><span data-stu-id="a831f-113">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="a831f-114">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="a831f-114">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="a831f-115">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="a831f-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="a831f-116">Alguma habilidade básica de programação em C#</span><span class="sxs-lookup"><span data-stu-id="a831f-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="a831f-117">Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="a831f-117">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="a831f-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019 LTS instalado e o módulo Suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="a831f-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a831f-119">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="a831f-119">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="a831f-120">Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="a831f-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="a831f-121">Como criar e preparar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="a831f-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="a831f-122">Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.</span><span class="sxs-lookup"><span data-stu-id="a831f-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="a831f-123">Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="a831f-123">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="a831f-124">[Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*</span><span class="sxs-lookup"><span data-stu-id="a831f-124">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="a831f-125">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="a831f-125">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="a831f-126">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="a831f-126">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="a831f-127">Como importar o Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="a831f-127">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="a831f-128">Como configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="a831f-128">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="a831f-129">[Criar e configurar a cena](mr-learning-base-02.md#creating-and-configuring-the-scene) e dar um nome adequado à cena, por exemplo, *AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="a831f-129">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="a831f-130">Então siga as instruções em [Alterar a opção de Exibição de Reconhecimento Espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para alterar o perfil de configuração do MRTK para sua cena para o **DefaultHoloLens2ConfigurationProfile** e alterar as opções de exibição para a malha de reconhecimento espacial para **Oclusão**.</span><span class="sxs-lookup"><span data-stu-id="a831f-130">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="a831f-131">Como configurar o comportamento de início dos comandos de fala</span><span class="sxs-lookup"><span data-stu-id="a831f-131">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="a831f-132">Como você usará o SDK de Fala para reconhecimento de fala e transcrição, será necessário configurar os comandos de fala MRTK para que eles não interfiram na funcionalidade do SDK de Fala.</span><span class="sxs-lookup"><span data-stu-id="a831f-132">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="a831f-133">Para conseguir isso, você pode alterar o comportamento de início dos comandos de fala de Início Automático para Início Manual.</span><span class="sxs-lookup"><span data-stu-id="a831f-133">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="a831f-134">Com o objeto **MixedRealityToolkit** selecionado na janela Hierarquia, na janela Inspetor, selecione a guia **Entrada** , clone o **DefaultHoloLens2InputSystemProfile** e o **DefaultMixedRealitySpeechCommandsProfile** e, em seguida, altere o **Comportamento de Início** dos comandos de fala para **Início Manual** :</span><span class="sxs-lookup"><span data-stu-id="a831f-134">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile** , and then change the speech commands **Start Behavior** to **Manual Start** :</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="a831f-136">Para lembrar como clonar e configurar perfis do MRTK, consulte as instruções de [Como configurar os perfis do Kit de Ferramentas de Realidade Misturada](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="a831f-136">For a reminder on how to clone and configure MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="a831f-137">Como configurar as funcionalidades</span><span class="sxs-lookup"><span data-stu-id="a831f-137">Configuring the capabilities</span></span>

<span data-ttu-id="a831f-138">No menu do Unity, selecione **Editar** > **Configurações de projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Configurações de Publicação** :</span><span class="sxs-lookup"><span data-stu-id="a831f-138">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="a831f-140">Em **Configurações de Publicação** , role para baixo até a seção **Funcionalidades** e verifique se as funcionalidades **InternetClient** , **Microphone** e **SpatialPerception** , que você habilitou ao criar o projeto no início do tutorial, estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="a831f-140">In the  **Publishing Settings** , scroll down to the **Capabilities** section and double-check that the **InternetClient** , **Microphone** , and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="a831f-141">Em seguida, habilite as funcionalidades **InternetClientServer** e **PrivateNetworkClientServer** :</span><span class="sxs-lookup"><span data-stu-id="a831f-141">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="a831f-143">Como importar os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="a831f-143">Importing the tutorial assets</span></span>

<span data-ttu-id="a831f-144">Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados** :</span><span class="sxs-lookup"><span data-stu-id="a831f-144">Download and **import** the following Unity custom packages **in the order they are listed** :</span></span>

* <span data-ttu-id="a831f-145">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (versão mais recente)</span><span class="sxs-lookup"><span data-stu-id="a831f-145">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="a831f-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a831f-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="a831f-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a831f-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="a831f-148">Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções em [Como importar o Kit de Ferramentas de Realidade Misturada](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="a831f-148">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="a831f-149">Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="a831f-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a><span data-ttu-id="a831f-151">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="a831f-151">Preparing the scene</span></span>

<span data-ttu-id="a831f-152">Nesta seção, você vai preparar a cena adicionando o tutorial pré-fabricado e configurar o componente do Controlador Lunarcom (Script) para controlar sua cena.</span><span class="sxs-lookup"><span data-stu-id="a831f-152">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="a831f-153">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutoriais.AzureSpeechServices** > **Pré-fabricados** e arraste o pré-fabricado **Lunarcom** para a janela Hierarquia para adicioná-lo à sua cena:</span><span class="sxs-lookup"><span data-stu-id="a831f-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="a831f-155">Com o objeto **Lunarcom** ainda selecionado na janela Hierarquia, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Controlador do Lunarcom (Script)** ao objeto Lunarcom:</span><span class="sxs-lookup"><span data-stu-id="a831f-155">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="a831f-157">O componente Controlador do Lunarcom (Script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="a831f-157">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="a831f-158">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="a831f-158">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="a831f-159">Com o objeto **Lunarcom** ainda selecionado, expanda-o para revelar seus objetos filho e, em seguida, arraste o objeto **Terminal** para o campo **Terminal** do componente Controlador do Lunarcom (Script):</span><span class="sxs-lookup"><span data-stu-id="a831f-159">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="a831f-161">Com o objeto **Lunarcom** ainda selecionado, expanda o objeto Terminal para revelar seus objetos filho e, em seguida, arraste o objeto **ConnectionLight** para o campo **Luz de Conexão** do componente Controlador do Lunarcom (Script) e o objeto **OutputText** para o campo **Texto de Saída** :</span><span class="sxs-lookup"><span data-stu-id="a831f-161">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="a831f-163">Com o objeto **Lunarcom** ainda selecionado, expanda o objeto Botões para revelar seus objetos filho e, em seguida, na janela Inspetor, expanda a lista **Botões** , defina seu **Tamanho** como 3 e arraste os objetos **MicButton** , **SatelliteButton** e **RocketButton** para os campos 0, 1 e 2 do **Elemento** , respectivamente:</span><span class="sxs-lookup"><span data-stu-id="a831f-163">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton** , **SatelliteButton** , and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="a831f-165">Como conectar o projeto do Unity ao recurso do Azure</span><span class="sxs-lookup"><span data-stu-id="a831f-165">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="a831f-166">Para usar os Serviços de Fala do Azure, você precisa criar um recurso do Azure e obter uma chave de API para o Serviço de Fala.</span><span class="sxs-lookup"><span data-stu-id="a831f-166">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="a831f-167">Siga as instruções de [Experimentar o serviço de Fala gratuitamente](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) e tome nota da sua região de serviço (também conhecida como Localização) e a chave de API (também conhecida como Key1 ou Key2).</span><span class="sxs-lookup"><span data-stu-id="a831f-167">Follow the [Try the Speech service for free](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="a831f-168">Na janela Hierarquia, selecione o objeto **Lunarcom** , então, na janela Inspetor, localize a seção **Credenciais do SDK de Fala** do componente **Controlador do Lunarcom (Script)** e configure-a da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a831f-168">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="a831f-169">No campo **Chave de API do Serviço de Fala** , insira sua chave de API (Key1 ou Key2)</span><span class="sxs-lookup"><span data-stu-id="a831f-169">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="a831f-170">No campo **Região do Serviço de Fala** , insira sua região de serviço (Localização) usando letras minúsculas e espaços removidos</span><span class="sxs-lookup"><span data-stu-id="a831f-170">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="a831f-172">Como usar o reconhecimento de fala para transcrever a fala</span><span class="sxs-lookup"><span data-stu-id="a831f-172">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="a831f-173">Na janela Hierarquia, selecione o objeto **Lunarcom** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Reconhecedor de Fala do Lunarcom (Script)** ao objeto Lunarcom:</span><span class="sxs-lookup"><span data-stu-id="a831f-173">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a831f-175">O componente Reconhecedor de Fala do Lunarcom (Script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="a831f-175">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="a831f-176">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="a831f-176">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="a831f-177">Se agora você entrar no modo de Jogo, poderá testar o reconhecimento de fala pressionando primeiro o botão de microfone:</span><span class="sxs-lookup"><span data-stu-id="a831f-177">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="a831f-179">Em seguida, supondo que o computador tenha um microfone, quando você disser algo, sua fala será transcrita no painel do terminal:</span><span class="sxs-lookup"><span data-stu-id="a831f-179">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> <span data-ttu-id="a831f-181">O aplicativo precisa se conectar ao Azure, portanto, verifique se o computador/dispositivo está conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="a831f-181">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a831f-182">Parabéns</span><span class="sxs-lookup"><span data-stu-id="a831f-182">Congratulations</span></span>

<span data-ttu-id="a831f-183">Você implementou o reconhecimento de fala da plataforma Azure.</span><span class="sxs-lookup"><span data-stu-id="a831f-183">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="a831f-184">Execute o aplicativo em seu dispositivo para garantir que o recurso esteja funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="a831f-184">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="a831f-185">No próximo tutorial, você aprenderá a executar comandos usando o reconhecimento de fala do Azure.</span><span class="sxs-lookup"><span data-stu-id="a831f-185">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a831f-186">Próximo tutorial: 2. Como usar o reconhecimento de fala para executar comandos</span><span class="sxs-lookup"><span data-stu-id="a831f-186">Next tutorial: 2. Using speech recognition to execute commands</span></span>](mrlearning-speechSDK-ch2.md)
