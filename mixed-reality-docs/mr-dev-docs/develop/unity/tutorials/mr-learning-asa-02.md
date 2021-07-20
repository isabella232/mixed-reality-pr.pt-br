---
title: Introdução às Âncoras Espaciais do Azure
description: Conclua este curso para aprender a usar as Âncoras Espaciais do Azure para ancorar objetos em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure
ms.localizationpriority: high
ms.openlocfilehash: 9c3ae23c39bf4d0b32d8a5d82716f93fee48b6db
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656639"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="374ae-104">2. Introdução às Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="374ae-104">2. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="374ae-105">Neste tutorial, você vai explorar as várias etapas necessárias para iniciar e parar uma sessão de Âncoras Espaciais do Azure e criar, carregar e baixá-las em apenas um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="374ae-105">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="374ae-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="374ae-106">Objectives</span></span>

* <span data-ttu-id="374ae-107">Conheça os conceitos básicos do desenvolvimento com Âncoras Espaciais do Azure para o HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="374ae-107">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="374ae-108">Saber como criar âncoras espaciais e buscá-las no Azure</span><span class="sxs-lookup"><span data-stu-id="374ae-108">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="374ae-109">Como criar e preparar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="374ae-109">Creating and preparing the Unity project</span></span>

<span data-ttu-id="374ae-110">Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.</span><span class="sxs-lookup"><span data-stu-id="374ae-110">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="374ae-111">Primeiro, siga [Como inicializar o seu projeto e implantar o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar o seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="374ae-111">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="374ae-112">[Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*</span><span class="sxs-lookup"><span data-stu-id="374ae-112">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="374ae-113">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="374ae-113">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="374ae-114">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="374ae-114">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="374ae-115">Como importar o Kit de ferramentas de Realidade Misturada e configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="374ae-115">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="374ae-116">[Criar e configurar a cena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) e dar um nome adequado à cena, por exemplo, *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="374ae-116">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="374ae-117">Em seguida, siga as instruções em [Alterar a Opção de Exibição de Reconhecimento Espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para verificar se o perfil de configuração do MRTK da sua cena é o **DefaultHoloLens2ConfigurationProfile** e alterar as opções de exibição da malha de reconhecimento espacial para **Oclusão**.</span><span class="sxs-lookup"><span data-stu-id="374ae-117">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile**  and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a><span data-ttu-id="374ae-118">Instalação de pacotes incorporados do Unity e importação de ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="374ae-118">Installing inbuilt Unity packages and Importing the tutorial assets</span></span>

[!INCLUDE[](includes/installing-packages-for-asa.md)]

## <a name="preparing-the-scene"></a><span data-ttu-id="374ae-119">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="374ae-119">Preparing the scene</span></span>

<span data-ttu-id="374ae-120">Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.</span><span class="sxs-lookup"><span data-stu-id="374ae-120">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="374ae-121">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureSpatialAnchors** > **Pré-fabricados** e clique e arraste os seguintes pré-fabricados para a janela Hierarquia para adicioná-los à sua cena:</span><span class="sxs-lookup"><span data-stu-id="374ae-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="374ae-122">Pré-fabricados **ButtonParent**</span><span class="sxs-lookup"><span data-stu-id="374ae-122">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="374ae-123">Pré-fabricados **DebugWindow**</span><span class="sxs-lookup"><span data-stu-id="374ae-123">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="374ae-124">Pré-fabricados **Instructions**</span><span class="sxs-lookup"><span data-stu-id="374ae-124">**Instructions** prefabs</span></span>
* <span data-ttu-id="374ae-125">Pré-fabricados **ParentAnchor**</span><span class="sxs-lookup"><span data-stu-id="374ae-125">**ParentAnchor** prefabs</span></span>

![Unity com os pré-fabricados recém-adicionados selecionados](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="374ae-127">Se você considerar que ícones grandes na sua cena, por exemplo, os ícones "T" grandes, causam distração, poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o Utensílio</a> para a posição de desligado, conforme mostrado na imagem acima.</span><span class="sxs-lookup"><span data-stu-id="374ae-127">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

<span data-ttu-id="374ae-128">Selecione o objeto **MixedRealityToolkit** na janela Hierarquia e use o botão **Adicionar Componente** na janela Inspetor para adicionar os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="374ae-128">Select **MixedRealityToolkit** object in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="374ae-129">AR Anchor Manager (Script)</span><span class="sxs-lookup"><span data-stu-id="374ae-129">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="374ae-130">DisableDiagnosticsSystem (Script)</span><span class="sxs-lookup"><span data-stu-id="374ae-130">DisableDiagnosticsSystem (Script)</span></span>

![<span data-ttu-id="374ae-131">Objeto MixedRealityToolkit do Unity com o AR Anchor Manager e os componentes DisableDiagnosticsSystem adicionados</span><span class="sxs-lookup"><span data-stu-id="374ae-131">Unity MixedRealityToolkit object with AR Anchor Manager and DisableDiagnosticsSystem components added</span></span> ](images/mr-learning-asa/asa-02-section4-step1-2.PNG)

> [!WARNING]
> <span data-ttu-id="374ae-132">Existe um problema conhecido com o ASA v2.9.0 e o v2.10.0-versão prévia.1 que exige que dois objetos adicionais sejam incluidos.</span><span class="sxs-lookup"><span data-stu-id="374ae-132">There is a known issue with ASA v2.9.0 and v2.10.0-preview.1 that requires two additional objects to be placed in the scene.</span></span> <span data-ttu-id="374ae-133">Use o botão **Adicionar componente** na janela Inspetor para adicionar um Gerenciador de Câmera AR (script) e uma sessão AR (script) ao objeto **MixedRealityToolkit**.</span><span class="sxs-lookup"><span data-stu-id="374ae-133">Please use the **Add Component** button in the inspector window to add an AR Camera Manager (Script) and an AR Session (Script) to the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="374ae-134">Não se esqueça de desabilitar a Câmera, que é criada automaticamente ao adicionar o Gerenciador de câmera AR (script), desmarcando a caixa de seleção ao lado do objeto Câmera na janela Inspetor.</span><span class="sxs-lookup"><span data-stu-id="374ae-134">Be sure to disable the Camera that is created automatically while adding the AR Camera Manager (Script) by unchecking the checkbox next to the Camera object in the inspector window.</span></span> <span data-ttu-id="374ae-135">Esse problema será abordado na versão completa do ASA v2.10.0.</span><span class="sxs-lookup"><span data-stu-id="374ae-135">This issue will be addressed in the full release of ASA v2.10.0.</span></span>
>

> [!NOTE]
> <span data-ttu-id="374ae-136">Quando você adiciona o componente AR Anchor Manager (script), o componente AR Session Origin (script) é adicionado automaticamente, pois ele é exigido pelo componente AR Anchor Manager (script).</span><span class="sxs-lookup"><span data-stu-id="374ae-136">When you add the AR Anchor Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Anchor Manager (Script) component.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="374ae-137">Como configurar os botões para operar a cena</span><span class="sxs-lookup"><span data-stu-id="374ae-137">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="374ae-138">Nesta seção, você adicionará scripts à cena para criar uma série de eventos de botão que demonstram os conceitos básicos de como as âncoras locais e as Âncoras Espaciais do Azure se comportam em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="374ae-138">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="374ae-139">Na janela Hierarquia, expanda o objeto **ButtonParent** e selecione o primeiro objeto filho chamado **StartAzureSession**, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="374ae-139">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="374ae-140">Atribua o objeto **ParentAnchor** como ouvinte para o evento On Click () arrastando-o da janela Hierarquia até o campo **Nenhum (objeto)**</span><span class="sxs-lookup"><span data-stu-id="374ae-140">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="374ae-141">Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **StartAzureSession ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="374ae-141">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity com o evento OnClick do botão StartAzureSession configurado](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="374ae-143">Na janela Hierarquia, selecione o próximo botão denominado **StopAzureSession**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="374ae-143">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="374ae-144">Atribua o objeto **ParentAnchor** como ouvinte para o evento On Click () arrastando-o da janela Hierarquia até o campo **Nenhum (objeto)**</span><span class="sxs-lookup"><span data-stu-id="374ae-144">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="374ae-145">Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **StopAzureSession ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="374ae-145">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity com o evento OnClick do botão StopAzureSession configurado](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="374ae-147">Na janela Hierarquia, selecione o próximo botão denominado **CreateAzureAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="374ae-147">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="374ae-148">Atribua o objeto **ParentAnchor** como ouvinte para o evento On Click () arrastando-o da janela Hierarquia até o campo **Nenhum (objeto)**</span><span class="sxs-lookup"><span data-stu-id="374ae-148">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="374ae-149">Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **CreateAzureAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="374ae-149">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="374ae-150">Atribua o objeto **ParentAnchor** ao campo vazio **Nenhum (Objeto de Jogo)** para torná-lo o argumento para a função CreateAzureAnchor ()</span><span class="sxs-lookup"><span data-stu-id="374ae-150">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![Unity com o evento OnClick do botão CreateAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="374ae-152">Na janela Hierarquia, selecione o próximo botão denominado **RemoveLocalAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="374ae-152">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="374ae-153">Atribua o objeto **ParentAnchor** como ouvinte para o evento On Click () arrastando-o da janela Hierarquia até o campo **Nenhum (objeto)**</span><span class="sxs-lookup"><span data-stu-id="374ae-153">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="374ae-154">Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **RemoveLocalAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="374ae-154">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="374ae-155">Atribua o objeto **ParentAnchor** ao campo vazio **Nenhum (Objeto de Jogo)** para torná-lo o argumento para a função RemoveLocalAnchor ()</span><span class="sxs-lookup"><span data-stu-id="374ae-155">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![Unity com o evento OnClick do botão RemoveLocalAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="374ae-157">Na janela Hierarquia, selecione o próximo botão denominado **FindAzureAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="374ae-157">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="374ae-158">Atribua o objeto **ParentAnchor** como ouvinte para o evento On Click () arrastando-o da janela Hierarquia até o campo **Nenhum (objeto)**</span><span class="sxs-lookup"><span data-stu-id="374ae-158">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="374ae-159">Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **FindAzureAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="374ae-159">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity com o evento OnClick do botão FindAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="374ae-161">Na janela Hierarquia, selecione o próximo botão denominado **DeleteAzureAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="374ae-161">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="374ae-162">Atribua o objeto **ParentAnchor** como ouvinte para o evento On Click () arrastando-o da janela Hierarquia até o campo **Nenhum (objeto)**</span><span class="sxs-lookup"><span data-stu-id="374ae-162">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="374ae-163">Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **DeleteAzureAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="374ae-163">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity com o evento OnClick do botão DeleteAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="374ae-165">Como conectar a cena ao recurso do Azure</span><span class="sxs-lookup"><span data-stu-id="374ae-165">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="374ae-166">Na janela Hierarquia, selecione o objeto **ParentAnchor** e, na janela Inspetor, localize o componente **Gerenciador de Âncora Espacial (Script)** .</span><span class="sxs-lookup"><span data-stu-id="374ae-166">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="374ae-167">Configure a seção **Credenciais** com as credenciais da conta das Âncoras Espaciais do Azure criada como parte dos [Pré-requisitos](mr-learning-asa-01.md#prerequisites) desta série de tutoriais:</span><span class="sxs-lookup"><span data-stu-id="374ae-167">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="374ae-168">No campo **ID da Conta das Âncoras Espaciais**, cole a **ID da Conta** da sua conta das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="374ae-168">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="374ae-169">No campo **Chave de Conta das Âncoras Espaciais**, cole a **Chave de Acesso** primária ou secundária da sua conta das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="374ae-169">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="374ae-170">No campo **Domínio da Conta das Âncoras Espaciais**, cole o **Domínio da Conta** da sua conta das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="374ae-170">In the **Spatial Anchors Account Domain** field, paste the **Account Domain** from your Azure Spatial Anchors account</span></span>

![Unity com o Gerenciador de Âncora Espacial configurado](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="374ae-172">Experimentando os comportamentos básicos das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="374ae-172">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="374ae-173">As Âncoras Espaciais do Azure não podem ser executadas no Unity, portanto, para testar a funcionalidade delas, você precisa criar o projeto e implantar o aplicativo no seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="374ae-173">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="374ae-174">Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="374ae-174">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="374ae-175">Quando o aplicativo for executado no seu dispositivo, siga as instruções na tela exibidas no painel Instruções do Tutorial de Âncora Espacial do Azure:</span><span class="sxs-lookup"><span data-stu-id="374ae-175">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="374ae-176">Mover o cubo para uma localização diferente</span><span class="sxs-lookup"><span data-stu-id="374ae-176">Move the cube to a different location</span></span>
2. <span data-ttu-id="374ae-177">Iniciar a Sessão do Azure</span><span class="sxs-lookup"><span data-stu-id="374ae-177">Start Azure Session</span></span>
3. <span data-ttu-id="374ae-178">Criar Âncora do Azure (cria uma âncora na localização do cubo).</span><span class="sxs-lookup"><span data-stu-id="374ae-178">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
4. <span data-ttu-id="374ae-179">Interromper a Sessão do Azure</span><span class="sxs-lookup"><span data-stu-id="374ae-179">Stop Azure Session</span></span>
5. <span data-ttu-id="374ae-180">Remover a Âncora Local (permite que o usuário mova o cubo)</span><span class="sxs-lookup"><span data-stu-id="374ae-180">Remove Local Anchor (allows the user to move the cube)</span></span>
6. <span data-ttu-id="374ae-181">Mover o cubo para outro lugar</span><span class="sxs-lookup"><span data-stu-id="374ae-181">Move the cube somewhere else</span></span>
7. <span data-ttu-id="374ae-182">Iniciar a Sessão do Azure</span><span class="sxs-lookup"><span data-stu-id="374ae-182">Start Azure Session</span></span>
8. <span data-ttu-id="374ae-183">Localizar a Âncora do Azure (posiciona o cubo na localização da etapa 3)</span><span class="sxs-lookup"><span data-stu-id="374ae-183">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
9. <span data-ttu-id="374ae-184">Excluir a Âncora do Azure</span><span class="sxs-lookup"><span data-stu-id="374ae-184">Delete Azure Anchor</span></span>
10. <span data-ttu-id="374ae-185">Interromper a sessão do Azure</span><span class="sxs-lookup"><span data-stu-id="374ae-185">Stop Azure session</span></span>

![Unity com o objeto Instructions selecionado](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="374ae-187">As Âncoras Espaciais do Azure usam a Internet para salvar e carregar os dados de âncora para garantir que o dispositivo esteja conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="374ae-187">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="374ae-188">Como ancorar uma experiência</span><span class="sxs-lookup"><span data-stu-id="374ae-188">Anchoring an experience</span></span>

<span data-ttu-id="374ae-189">Nas seções anteriores, você aprendeu os conceitos básicos das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="374ae-189">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="374ae-190">Usamos um cubo para representar e visualizar o objeto de jogo pai com a âncora anexada.</span><span class="sxs-lookup"><span data-stu-id="374ae-190">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="374ae-191">Nesta seção, você aprenderá a ancorar uma experiência inteira colocando-a como um filho do objeto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="374ae-191">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="374ae-192">Na janela Hierarquia, selecione o objeto **ParentAnchor** e, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="374ae-192">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="374ae-193">Altere a **Escala X** para 1,1</span><span class="sxs-lookup"><span data-stu-id="374ae-193">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="374ae-194">Altere a **Escala Z** para 1,1</span><span class="sxs-lookup"><span data-stu-id="374ae-194">Change **Scale Z** to 1.1</span></span>

![Unity com o objeto ParentAnchor selecionado, posicionado e escalado](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="374ae-196">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-fabricados** > **Rover** e, em seguida, clique e arraste o pré-fabricado **RoverExplorer_Complete** na janela Hierarquia para adicioná-lo à cena:</span><span class="sxs-lookup"><span data-stu-id="374ae-196">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![Unity com o pré-fabricado RoverExplorer_Complete recém-adicionado](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="374ae-198">Com o objeto RocketLauncher_Complete recém-adicionado ainda selecionado na janela Hierarquia, arraste-o sobre o objeto **ParentAnchor** para torná-lo um filho do objeto ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="374ae-198">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![Unity com o objeto RoverExplorer_Complete definido como filho de ParentAnchor](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="374ae-200">Se agora você recompilar o projeto e implantar o aplicativo no seu dispositivo, você poderá reposicionar toda a experiência do Explorador do Rover movendo o cubo redimensionado.</span><span class="sxs-lookup"><span data-stu-id="374ae-200">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="374ae-201">Há uma variedade de fluxos de experiência do usuário para reposicionar experiências, incluindo o uso de um objeto de reposicionamento (como o cubo usado neste tutorial), o uso de um botão para alternar um controle de limites que envolve a experiência, o uso de utensílios de posição e rotação e muito mais.</span><span class="sxs-lookup"><span data-stu-id="374ae-201">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounds control that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="374ae-202">Parabéns</span><span class="sxs-lookup"><span data-stu-id="374ae-202">Congratulations</span></span>

<span data-ttu-id="374ae-203">Neste tutorial, você aprendeu os conceitos básicos das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="374ae-203">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="374ae-204">Este tutorial forneceu vários botões que permitem explorar as várias etapas necessárias para iniciar e parar uma sessão de Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="374ae-204">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="374ae-205">Além disso, para criar, carregar e baixar Âncoras Espaciais do Azure em um único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="374ae-205">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="374ae-206">No próximo tutorial, você aprenderá a salvar as IDs de âncora do Azure no seu HoloLens 2 para recuperação, mesmo depois que o aplicativo for reiniciado, bem como a transferir IDs de âncora entre vários dispositivos para obter o alinhamento espacial.</span><span class="sxs-lookup"><span data-stu-id="374ae-206">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="374ae-207">Próximo tutorial: 3. Salvar, recuperar e compartilhar Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="374ae-207">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
