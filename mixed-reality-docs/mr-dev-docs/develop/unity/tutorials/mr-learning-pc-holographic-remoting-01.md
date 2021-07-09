---
title: Introdução à comunicação remota holográfica para PC
description: Conclua este curso para saber como transmitir aplicativos de realidade misturada remotamente do seu PC para o HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, comunicação remota holográfica do PC, dicas de ferramenta, acompanhamento do olho
ms.localizationpriority: high
ms.openlocfilehash: 05831ff19a998bd5e99ab5d20c3fb045a09c55e9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175435"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a><span data-ttu-id="edeea-104">1. Introdução à Comunicação Remota Holográfica para PC</span><span class="sxs-lookup"><span data-stu-id="edeea-104">1. Getting started with PC Holographic Remoting</span></span>

<span data-ttu-id="edeea-105">Bem-vindo(a) aos tutoriais do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="edeea-105">Welcome to the HoloLens 2 tutorials.</span></span> <span data-ttu-id="edeea-106">Nesta série de tutoriais de duas partes, você aprenderá a criar uma demonstração de experiência de realidade misturada e a criar um aplicativo de PC para a Comunicação Remota do Holographic.</span><span class="sxs-lookup"><span data-stu-id="edeea-106">In this two-part tutorial series, you will learn how to create a mixed reality experience demonstration and how to create a PC app for Holographic Remoting.</span></span>

<span data-ttu-id="edeea-107">Neste tutorial, você aprenderá a criar uma experiência de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="edeea-107">In this tutorial, you'll learn how to create a mixed reality experience.</span></span> <span data-ttu-id="edeea-108">Ele demonstrará elementos da interface do usuário, manipulação de modelo 3D, recorte de modelo e recursos de acompanhamento de olho.</span><span class="sxs-lookup"><span data-stu-id="edeea-108">It will demonstrate UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span>

<span data-ttu-id="edeea-109">No segundo tutorial, [Criar um aplicativo de Comunicação Remota Holographic](mr-learning-pc-holographic-remoting-02.md), você aprenderá a criar um aplicativo de PC para Comunicação Remota do Holographic.</span><span class="sxs-lookup"><span data-stu-id="edeea-109">In the second tutorial, [Create a Holographic Remoting application](mr-learning-pc-holographic-remoting-02.md), you will learn how to create a PC app for Holographic Remoting.</span></span> <span data-ttu-id="edeea-110">E conecte-se ao HoloLens 2 a qualquer momento, fornecendo um modo de visualizar o conteúdo 3D em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="edeea-110">And connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="edeea-111">Objetivos</span><span class="sxs-lookup"><span data-stu-id="edeea-111">Objectives</span></span>

* <span data-ttu-id="edeea-112">Importar ativos e configurar a cena</span><span class="sxs-lookup"><span data-stu-id="edeea-112">Import assets and set up the scene</span></span>
* <span data-ttu-id="edeea-113">Interagir com hologramas usando os botões e elementos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="edeea-113">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="edeea-114">Configurar objetos 3D para o recurso de recorte</span><span class="sxs-lookup"><span data-stu-id="edeea-114">Configure 3D objects for the clipping feature</span></span>
* <span data-ttu-id="edeea-115">Aprenda a ativar dicas de ferramentas com acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="edeea-115">Learn about activating tooltips with eye-tracking</span></span>

## <a name="prerequisites"></a><span data-ttu-id="edeea-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="edeea-116">Prerequisites</span></span>

* <span data-ttu-id="edeea-117">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="edeea-117">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="edeea-118">Conhecimento básico de programação em C#</span><span class="sxs-lookup"><span data-stu-id="edeea-118">Basic c# programming knowledge</span></span>
* <span data-ttu-id="edeea-119">Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="edeea-119">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="edeea-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2020/2019 LTS montado e o módulo Suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="edeea-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="edeea-121">**Recomendamos expressamente** a conclusão da série de tutoriais de [Introdução](mr-learning-base-01.md) ou alguma experiência anterior básica com o Unity e o MRTK antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="edeea-121">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="edeea-122">Esta série de tutoriais suporta o Unity 2020 LTS (atualmente 2020.3.x) se você estiver usando o Open XR e o Unity 2019 LTS (atualmente 2019.4.x) se estiver usando o Legacy WSA. Isso substitui os requisitos de versão do Unity declarados nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="edeea-122">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR and Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="edeea-123">Como criar e preparar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="edeea-123">Creating and preparing the Unity project</span></span>

<span data-ttu-id="edeea-124">Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.</span><span class="sxs-lookup"><span data-stu-id="edeea-124">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="edeea-125">Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="edeea-125">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="edeea-126">[Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*</span><span class="sxs-lookup"><span data-stu-id="edeea-126">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="edeea-127">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="edeea-127">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="edeea-128">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="edeea-128">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="edeea-129">Como importar o Kit de ferramentas de Realidade Misturada e configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="edeea-129">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="edeea-130">[Criar e definir a cena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) e dar um nome adequado à cena, por exemplo, **Comunicação Remota Holográfica para PC**</span><span class="sxs-lookup"><span data-stu-id="edeea-130">[Creating and setting the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, **PC Holographic Remoting**</span></span>

<span data-ttu-id="edeea-131">Então siga as instruções para [Alterar a Opção de Exibição de Reconhecimento Espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para alterar o perfil de configuração do MRTK para sua cena para o **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="edeea-131">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile**.</span></span> <span data-ttu-id="edeea-132">Altere as opções de exibição da malha de reconhecimento espacial para **Oclusão**.</span><span class="sxs-lookup"><span data-stu-id="edeea-132">Change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="edeea-133">Como importar os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="edeea-133">Importing the tutorial assets</span></span>

[!INCLUDE[](includes/importing-tutorial-assets-pc-holographic-remoting.md)]

## <a name="configuring-and-preparing-the-scene"></a><span data-ttu-id="edeea-134">Como configurar e preparar a cena</span><span class="sxs-lookup"><span data-stu-id="edeea-134">Configuring and preparing the scene</span></span>

<span data-ttu-id="edeea-135">Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.</span><span class="sxs-lookup"><span data-stu-id="edeea-135">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="edeea-136">Na janela do projeto, navegue até a pasta **Ativos** > **MRTK.Tutoriais.PCHolograhicRemoting** > **Pré-fabricados**.</span><span class="sxs-lookup"><span data-stu-id="edeea-136">In the Project window, navigate to **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder.</span></span> <span data-ttu-id="edeea-137">Enquanto pressiona o botão CTRL, clique nos seis pré-fabricados abaixo.</span><span class="sxs-lookup"><span data-stu-id="edeea-137">While holding down the CTRL button, click on the below six prefabs.</span></span>

* <span data-ttu-id="edeea-138">ButtonParent</span><span class="sxs-lookup"><span data-stu-id="edeea-138">ButtonParent</span></span>
* <span data-ttu-id="edeea-139">ClippingObjects</span><span class="sxs-lookup"><span data-stu-id="edeea-139">ClippingObjects</span></span>
* <span data-ttu-id="edeea-140">HandSpatialMapButton</span><span class="sxs-lookup"><span data-stu-id="edeea-140">HandSpatialMapButton</span></span>
* <span data-ttu-id="edeea-141">Instruções</span><span class="sxs-lookup"><span data-stu-id="edeea-141">Instructions</span></span>
* <span data-ttu-id="edeea-142">ModelParent</span><span class="sxs-lookup"><span data-stu-id="edeea-142">ModelParent</span></span>
* <span data-ttu-id="edeea-143">Plataforma</span><span class="sxs-lookup"><span data-stu-id="edeea-143">Platform</span></span>

![Unity com os pré-fabricados a serem adicionados à cena selecionada](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

<span data-ttu-id="edeea-145">Arraste e solte esses modelos da pasta de pré-fabricados na **janela Hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="edeea-145">Drag-and-drop these models from the prefabs folder into the **Hierarchy window**.</span></span>

![Unity com os pré-fabricados recém-adicionados ainda selecionados](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

<span data-ttu-id="edeea-147">Para se concentrar nos objetos da cena, você pode clicar duas vezes no objeto **ModelParent** e, em seguida, reduzir levemente o zoom de novo:</span><span class="sxs-lookup"><span data-stu-id="edeea-147">To focus in on the objects in the scene, you can double-click on the **ModelParent** object, and then zoom slightly in again:</span></span>

![Unity com o objeto ModelParent em foco](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> <span data-ttu-id="edeea-149">Se você considerar que ícones grandes em sua cena, como os ícones "T" grandes, causam distração, poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o Gizmos</a> para a posição de desligado.</span><span class="sxs-lookup"><span data-stu-id="edeea-149">If you find the large icons in your scene, such as, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="edeea-150">Como configurar os botões para operar a cena</span><span class="sxs-lookup"><span data-stu-id="edeea-150">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="edeea-151">Nesta seção, você adicionará scripts à cena para criar eventos de botão que demonstram os conceitos básicos de alternância de modelo e funcionalidade de recorte.</span><span class="sxs-lookup"><span data-stu-id="edeea-151">In this section, you will add scripts into the scene to create button events demonstrating the fundamentals of model switching and clipping functionality.</span></span>

### <a name="1-configuring-the-interactable-script-component"></a><span data-ttu-id="edeea-152">1. Como configurar o componente Interactable (Script)</span><span class="sxs-lookup"><span data-stu-id="edeea-152">1. Configuring the Interactable (Script) component</span></span>

<span data-ttu-id="edeea-153">Na janela Hierarquia, expanda o objeto **ButtonParent** e selecione o **NextButton**.</span><span class="sxs-lookup"><span data-stu-id="edeea-153">In the Hierarchy window, expand the **ButtonParent** object and select the **NextButton**.</span></span> <span data-ttu-id="edeea-154">Na janela Inspetor, localize o componente **Interactable (Script)** e clique no ícone **+** sob o evento **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="edeea-154">In the Inspector window, locate the **Interactable (Script)** component and click on **+** icon under **OnClick ()** event.</span></span>

![Unity com o evento NextButton OnClick adicionado](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

<span data-ttu-id="edeea-156">Com o objeto **NextButton** ainda selecionado na janela Hierarquia, clique e arraste o objeto **ButtonParent** da janela Hierarquia para o campo vazio **Nenhum (Objeto)** do evento que você acabou de adicionar para fazer com que o objeto ButtonParent ouça o evento de clique do botão deste botão:</span><span class="sxs-lookup"><span data-stu-id="edeea-156">With the **NextButton** object still selected in the Hierarchy window, click-and-drag the **ButtonParent** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

![Unity com o ouvinte de eventos NextButton OnClick configurado](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

<span data-ttu-id="edeea-158">Clique no menu suspenso **Nenhuma Função** do mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="edeea-158">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="edeea-159">Em seguida, selecione **ViewButtonControl** > **NextModel ()** para definir a função **NextModel ()** como a ação disparada quando os eventos pressionados pelo botão são acionados desse botão:</span><span class="sxs-lookup"><span data-stu-id="edeea-159">Then select **ViewButtonControl** > **NextModel ()** to set the **NextModel ()** function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![Caminho de seleção de ação de evento NextButton OnClick do Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a><span data-ttu-id="edeea-161">2. Como configurar os botões restantes</span><span class="sxs-lookup"><span data-stu-id="edeea-161">2. Configuring the remaining buttons</span></span>

<span data-ttu-id="edeea-162">Para cada um dos botões restantes, conclua o processo descrito acima para atribuir funções aos eventos **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="edeea-162">For each of the remaining buttons, complete the process outlined above to assign functions to the **OnClick ()** events:</span></span>

* <span data-ttu-id="edeea-163">Para o objeto PreviousButton, atribua a função **ViewButtonControl** l > **PreviousModel ()** .</span><span class="sxs-lookup"><span data-stu-id="edeea-163">For PreviousButton object, assign the **ViewButtonContro** l > **PreviousModel ()** function.</span></span>

* <span data-ttu-id="edeea-164">Para ClippingButton, selecione a função **ToggleButton** > **ToggleClipping ()** .</span><span class="sxs-lookup"><span data-stu-id="edeea-164">For ClippingButton select **ToggleButton** > **ToggleClipping ()** function.</span></span>

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a><span data-ttu-id="edeea-165">3. Como configurar os componentes Controle de Botão de Exibição (Script) e Botão de Alternância (Script)</span><span class="sxs-lookup"><span data-stu-id="edeea-165">3. Configuring the View Button Control (Script)  and Toggle Button (Script) components</span></span>

<span data-ttu-id="edeea-166">Agora, os botões estão configurados para demonstrar a funcionalidade de recorte e troca de modelos.</span><span class="sxs-lookup"><span data-stu-id="edeea-166">Now your buttons are configured to demonstrate the model switching and clipping functionality.</span></span> <span data-ttu-id="edeea-167">É hora de adicionar modelos 3D e os objetos de recorte ao script.</span><span class="sxs-lookup"><span data-stu-id="edeea-167">It is time to add 3D models and the clipping objects to the script.</span></span>

<span data-ttu-id="edeea-168">Fornecemos seis modelos 3D diferentes para demonstração. Expanda o ***ModelParentobject*** para expor esses modelos 3D.</span><span class="sxs-lookup"><span data-stu-id="edeea-168">We have provided six different 3D models for demonstration, expand the ***ModelParentobject*** to expose these 3D models.</span></span>

<span data-ttu-id="edeea-169">Com o objeto ButtonParent ainda selecionado na janela hierarquia, na janela Inspetor, localize o componente **Exibir Controle de Botão (Script)** e expanda a variável **Modelos**.</span><span class="sxs-lookup"><span data-stu-id="edeea-169">With the ButtonParent object still selected in the Hierarchy window, in the Inspector window, locate the **View Button Control (Script)** component and expand the **Models** variable.</span></span>

<span data-ttu-id="edeea-170">No campo **Tamanho**, insira o número de modelos 3D que você gostaria de ter em sua cena.</span><span class="sxs-lookup"><span data-stu-id="edeea-170">In the **Size** field, enter the number of 3D models you would like to have in your scene.</span></span> <span data-ttu-id="edeea-171">Neste caso, seriam seis.</span><span class="sxs-lookup"><span data-stu-id="edeea-171">In this case, it would be six.</span></span> <span data-ttu-id="edeea-172">Ele criará campos para adicionar modelos 3D.</span><span class="sxs-lookup"><span data-stu-id="edeea-172">It will create fields for adding new 3D models.</span></span>

![Unity com os campos do componente de script de ViewButtonControl](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

<span data-ttu-id="edeea-174">Arraste e solte cada objeto filho do objeto ModelParent nesses campos.</span><span class="sxs-lookup"><span data-stu-id="edeea-174">Drag and drop each child object of ModelParent Object into these fields.</span></span>

![Unity com os campos do componente de script de ViewButtonControl configurados](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

<span data-ttu-id="edeea-176">Arraste e solte o objeto **ClippingObjects** da janela Hierarquia para o campo **Objeto de Recorte** do componente **Botão de Alternância (Script)** .</span><span class="sxs-lookup"><span data-stu-id="edeea-176">Drag and drop the  **ClippingObjects** object from the Hierarchy window to the  **Toggle Button (Script)** component **Clipping Object** field.</span></span>
>[!NOTE]
><span data-ttu-id="edeea-177">Fique somente no objeto pai do botão.</span><span class="sxs-lookup"><span data-stu-id="edeea-177">Stay in button parent object only.</span></span>

![Unity com o campo do componente de script de ToggleButton configurado](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

<span data-ttu-id="edeea-179">Na janela Hierarquia, selecione o pré-fabricado **ClippingObjects** e habilite-o na janela Inspetor para ativar os objetos de Recorte.</span><span class="sxs-lookup"><span data-stu-id="edeea-179">In the Hierarchy window, select the **ClippingObjects** prefab and enable it in the Inspector window to turn on the Clipping objects.</span></span>

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a><span data-ttu-id="edeea-180">Como configurar os objetos de recorte para habilitar o recurso de recorte</span><span class="sxs-lookup"><span data-stu-id="edeea-180">Configuring the clipping objects to enable clipping feature</span></span>

<span data-ttu-id="edeea-181">Nesta seção, você adicionará o renderizador de objetos filho do objeto MarsCuriosityRover em um objeto de recorte individual para demonstrar o recorte do modelo MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="edeea-181">In this section, you will add MarsCuriosityRover object's child objects renderer into an individual clipping object to demonstrate the clipping of the MarsCuriosityRover model.</span></span>

<span data-ttu-id="edeea-182">Na janela Hierarquia, expanda o objeto **ClippingObjects** para expor os três objetos de recorte diferentes que você usará neste projeto.</span><span class="sxs-lookup"><span data-stu-id="edeea-182">In the Hierarchy window, expand the **ClippingObjects** object to expose the three different clipping objects that you will be using in this project.</span></span>

<span data-ttu-id="edeea-183">Para configurar o objeto **ClippingSphere**, clique nele e, na janela Inspetor, localize o componente **Esfera de Corte (Script)** .</span><span class="sxs-lookup"><span data-stu-id="edeea-183">To configure the **ClippingSphere** object, click on it, and in the Inspector window, locate the **Clipping Sphere (Script)** component.</span></span> <span data-ttu-id="edeea-184">Insira o número de renderizadores no campo tamanho que você precisa adicionar para seu modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="edeea-184">Enter the number of renderers in the size field that you need to add for your 3D model.</span></span> <span data-ttu-id="edeea-185">Nesse caso, adicione 10 para objetos filho MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="edeea-185">In this case, add 10 for MarsCuriosityRover child objects.</span></span> <span data-ttu-id="edeea-186">Ele criará campos para adicionar renderizadores, arrastar e soltar objetos de modelo filho do objeto MarsCuriosityRover nesses campos.</span><span class="sxs-lookup"><span data-stu-id="edeea-186">It will create fields for adding renderers, drag and drop MarsCuriosityRover Object's child model objects into these fields.</span></span>

![Unity com os campos do componente de script de ClippingSphere configurados](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

<span data-ttu-id="edeea-188">Siga o mesmo processo e adicione os renderizadores de objetos filho de MarsCuriosityRover aos objetos **ClippingBox** e **ClippingPlane**.</span><span class="sxs-lookup"><span data-stu-id="edeea-188">Follow the same process and add MarsCuriosityRover's child objects renderers to the **ClippingBox** and **ClippingPlane** objects.</span></span>

<span data-ttu-id="edeea-189">Neste tutorial, somente o modelo MarsCuriosityRover será usado para demonstrar o recurso de recorte.</span><span class="sxs-lookup"><span data-stu-id="edeea-189">In this tutorial, only the MarsCuriosityRover model will be used for demonstrating the clipping feature.</span></span> <span data-ttu-id="edeea-190">Eles estavam adicionando recursos de recorte a mais modelos, aumentando o tamanho do renderizador e adicionando seus renderizadores de malha individuais.</span><span class="sxs-lookup"><span data-stu-id="edeea-190">They were adding clipping features to more models, increasing the size of the renderer, and adding their individual mesh renderers.</span></span>

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a><span data-ttu-id="edeea-191">Como configurar o acompanhamento de olho para realçar dicas de ferramenta</span><span class="sxs-lookup"><span data-stu-id="edeea-191">Configuring eye-tracking to highlight tooltips</span></span>

<span data-ttu-id="edeea-192">Nesta seção, você vai explorar como habilitar o Acompanhamento Ocular em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="edeea-192">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="edeea-193">Por exemplo, você implementará a funcionalidade para realçar dicas de ferramentas anexadas às partes do MarsCuriosityRover enquanto olha para elas ocultá-las enquanto você está olhando longe delas.</span><span class="sxs-lookup"><span data-stu-id="edeea-193">For example, you will implement the functionality to highlight tooltips attached to MarsCuriosityRover's parts while looking at them and hiding them, while you are looking away from them.</span></span>

### <a name="1-identify-target-objects-and-associated-tooltips"></a><span data-ttu-id="edeea-194">1. Identificar objetos de destino e dicas de ferramenta associadas</span><span class="sxs-lookup"><span data-stu-id="edeea-194">1. Identify target objects and associated tooltips</span></span>

<span data-ttu-id="edeea-195">Na janela Hierarquia, selecione o objeto ModelParent.</span><span class="sxs-lookup"><span data-stu-id="edeea-195">In the Hierarchy window, select the ModelParent object.</span></span> <span data-ttu-id="edeea-196">Expanda ***MarsCuriosity -> Rover** _ para encontrar cinco partes principais do MarsCuriosityRover: _*POI-Camera\*\*, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer** e **POI-RUHF Antenna**.</span><span class="sxs-lookup"><span data-stu-id="edeea-196">Expand the ***MarsCuriosity -> Rover** _ to find five main parts of the MarsCuriosityRover: _*POI-Camera\*\*, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span></span>

* <span data-ttu-id="edeea-197">Observe cinco objetos de dica de ferramentas correspondentes associados a partes MarsCuriosityRover na janela Hierarquia.</span><span class="sxs-lookup"><span data-stu-id="edeea-197">Observe five corresponding tooltip objects associated with MarsCuriosityRover parts in the Hierarchy window.</span></span>
* <span data-ttu-id="edeea-198">Você vai configurar esses objetos para realçar a experiência ao examinar as partes MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="edeea-198">You will be configuring these objects to highlight the experience when you look at the MarsCuriosityRover parts.</span></span>

![Unity com o objeto Rover selecionado e expandido](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a><span data-ttu-id="edeea-200">2. Implementar ao examinar os eventos At Target () e On Look Away ()</span><span class="sxs-lookup"><span data-stu-id="edeea-200">2. Implement While Looking At Target ()  &  On Look Away () events</span></span>

<span data-ttu-id="edeea-201">Na janela Hierarquia, selecione o objeto \***POI-Camera** _.</span><span class="sxs-lookup"><span data-stu-id="edeea-201">In the Hierarchy window, select the \***POI-Camera** _ object.</span></span> <span data-ttu-id="edeea-202">Na janela Inspetor, localize o componente _ *Destino de Acompanhamento com os Olhos (Script)* \* e configure os eventos **While Looking At Target ()**  & **On Look Away ()** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="edeea-202">In the Inspector window, locate the _ *Eye Tracking Target (Script)*\* component and configure the **While Looking At Target ()** & **On Look Away ()** events as follows:</span></span>

* <span data-ttu-id="edeea-203">Para o campo **Nenhum (Objeto)** , atribua o objeto **POI-Camera ToolTip**</span><span class="sxs-lookup"><span data-stu-id="edeea-203">To **None (Object)** field, assign the **POI-Camera ToolTip** object</span></span>
* <span data-ttu-id="edeea-204">Na lista suspensa **Nenhuma Função** do evento **While Looking At Target ()** , selecione **GameObject** > **SetActive (bool).**</span><span class="sxs-lookup"><span data-stu-id="edeea-204">From **No Function** dropdown of **While Looking At Target ()** event, select **GameObject** > **SetActive (bool).**</span></span> <span data-ttu-id="edeea-205">Marque a **Caixa de Seleção** abaixo dela para realçar a dica de ferramenta como a ação que é disparada quando você examina o objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="edeea-205">Select the **Checkbox** under it to highlight the tooltip as the action that is triggered when you look at the target object.</span></span>

![Unity com a configuração de evento EyeTrackingTarget WhileLookingAtTarget em andamento](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* <span data-ttu-id="edeea-207">Siga o mesmo processo e clique no menu suspenso **Nenhuma Função** do ouvinte de eventos **On Look Away ()** .</span><span class="sxs-lookup"><span data-stu-id="edeea-207">Follow the same process and click on the **No Function** dropdown of the **On Look Away ()** event listener.</span></span> <span data-ttu-id="edeea-208">Em seguida, selecione **GameObject** > **SetActive (bool**) e deixe a **Caixa de Seleção** vazia para ocultar a dica de ferramenta como a ação disparada quando você olhar para longe do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="edeea-208">Then select **GameObject** > **SetActive (bool**) and leave the **Checkbox** empty to hide the tooltip as the action that is triggered when you look away from the target object.</span></span>

![Unity com o evento EyeTrackingTarget OnLookAway configurado](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

<span data-ttu-id="edeea-210">Siga o mesmo processo e atribua os respectivos objetos de dica de ferramenta aos mesmos eventos **While Looking At Target ()**  & **On Look Away ()** das partes **MarsCuriosityRover**.</span><span class="sxs-lookup"><span data-stu-id="edeea-210">Follow the same process and assign respective tooltip objects to their same **MarsCuriosityRover** parts **While Looking At Target ()** & **On Look Away ()** events.</span></span>

<span data-ttu-id="edeea-211">Para habilitar o acompanhamento de olho, siga estas [diretrizes](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span><span class="sxs-lookup"><span data-stu-id="edeea-211">To enable eye tracking, please follow these [guidelines](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span></span>

## <a name="congratulations"></a><span data-ttu-id="edeea-212">Parabéns</span><span class="sxs-lookup"><span data-stu-id="edeea-212">Congratulations</span></span>

<span data-ttu-id="edeea-213">Neste tutorial, você aprendeu a criar uma experiência de realidade misturada que demonstra elementos da interface do usuário, manipulação de modelo 3D, recorte de modelo e recursos de acompanhamento de olho.</span><span class="sxs-lookup"><span data-stu-id="edeea-213">In this tutorial, you learned to build a mixed reality experience demonstrating UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span> <span data-ttu-id="edeea-214">O tutorial forneceu a você o NextButton e o PreviousButton que permitem explorar a experiência do visualizador de modelos 3D.</span><span class="sxs-lookup"><span data-stu-id="edeea-214">The tutorial provided you with NextButton and PreviousButton that let you explore the 3D model viewer experience.</span></span> <span data-ttu-id="edeea-215">O ClippingObjectButton fez com que você ativasse objetos de recorte e experimentasse o recurso de recorte.</span><span class="sxs-lookup"><span data-stu-id="edeea-215">The ClippingObjectButton made you turn on clipping objects and experience clipping feature.</span></span> <span data-ttu-id="edeea-216">O tutorial também forneceu a você um elemento de acompanhamento de olho para habilitar o realce das dicas de ferramenta na experiência.</span><span class="sxs-lookup"><span data-stu-id="edeea-216">The tutorial also provided you with an eye-tracking element to enable highlighting the tooltips in the experience.</span></span>

<span data-ttu-id="edeea-217">Na próxima lição, você aprenderá a criar um aplicativo de Comunicação Remota Holográfico para PC para conectar o HoloLens 2 a qualquer momento, fornecendo um modo de visualizar o conteúdo 3D em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="edeea-217">In the next lesson, you will learn how to create a Holographic Remoting application for PC to connect HoloLens 2 at any point, providing a way to Visualize 3D content in mixed reality.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="edeea-218">Próxima lição: 2. Criar aplicativo de Comunicação Remota Holográfico</span><span class="sxs-lookup"><span data-stu-id="edeea-218">Next Lesson: 2. Create Holographic Remoting application</span></span>](mr-learning-pc-holographic-remoting-02.md)