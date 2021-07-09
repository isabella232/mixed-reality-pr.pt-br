---
title: Âncoras Espaciais do Azure para o Android e o iOS
description: Conclua este curso para aprender a implantar um projeto do Unity com o MRTK (Kit de Ferramentas de Realidade Misturada) e as Âncoras Espaciais do Azure para Android e iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, android, ios, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 67bda33f8d2d0711c83791be2e76d91b53ff934f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403400"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="10cb0-104">5. Âncoras Espaciais do Azure para o Android e o iOS</span><span class="sxs-lookup"><span data-stu-id="10cb0-104">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="10cb0-105">Neste tutorial, você aprenderá a criar seu projeto para dispositivos Android e iOS usando o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="10cb0-105">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="10cb0-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="10cb0-106">Objectives</span></span>

* <span data-ttu-id="10cb0-107">Saiba como criar o projeto para seu dispositivo Android usando o Plug-in ARCore XR e o AR Foundation do Unity</span><span class="sxs-lookup"><span data-stu-id="10cb0-107">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="10cb0-108">Saiba como criar o projeto para seu dispositivo iOS usando o Plug-in ARKit XR e o AR Foundation do Unity</span><span class="sxs-lookup"><span data-stu-id="10cb0-108">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="10cb0-109">Instalar pacotes internos do Unity</span><span class="sxs-lookup"><span data-stu-id="10cb0-109">Installing inbuilt Unity packages</span></span>

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="10cb0-110">Configurar o MRTK para a Câmera do AR Foundation</span><span class="sxs-lookup"><span data-stu-id="10cb0-110">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="10cb0-111">Nesta seção, você aprenderá a configurar o MRTK para implantação em um dispositivo móvel.</span><span class="sxs-lookup"><span data-stu-id="10cb0-111">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="10cb0-112">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**.</span><span class="sxs-lookup"><span data-stu-id="10cb0-112">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="10cb0-113">Em seguida, na janela Inspetor, selecione a guia **Câmera**, clone o perfil da câmera e dê a ele um nome adequado, por exemplo, **AzureSpatialAnchors_ARCameraProfile**:</span><span class="sxs-lookup"><span data-stu-id="10cb0-113">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![Unity com o ARCameraProfile recém-criado selecionado](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="10cb0-115">Para lembrar como clonar perfis de MRTK, consulte as instruções em [Configurando os perfis do Kit de Ferramentas de Realidade Misturada](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="10cb0-115">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="10cb0-116">Com a guia **Câmera** ainda selecionada na janela Inspetor, expanda os **Provedores de Configuração da Câmera** e, clicando em "-", remova a **Configuração da Câmera do Windows Mixed Reality** ou a **Configuração da Câmera XR SDK do Windows Mixed Reality**:</span><span class="sxs-lookup"><span data-stu-id="10cb0-116">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and by clicking the "-" remove the **Windows Mixed Reality Camera Setting** or **XR SDK Windows Mixed Reality Camera Setting**:</span></span>

![<span data-ttu-id="10cb0-117">ARCameraProfile do Unity com o novo provedor de dados adicionado</span><span class="sxs-lookup"><span data-stu-id="10cb0-117">Unity ARCameraProfile with new data provider added</span></span> ](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="10cb0-118">e clique em **+ Adicionar Provedor de Configurações da Câmera** e expanda o **Novo provedor de dados** recém-adicionado:</span><span class="sxs-lookup"><span data-stu-id="10cb0-118">and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider**:</span></span>

![Câmera AR adicionada para Android](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="10cb0-120">Usando a lista suspensa **Tipo**, altere o tipo para **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span><span class="sxs-lookup"><span data-stu-id="10cb0-120">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![ARCameraProfile do Unity com o caminho para a seleção do tipo de provedor de dados](images/mr-learning-asa/asa-05-section2-step1-4.png)

<span data-ttu-id="10cb0-122">Atualize as definições de script do UnityAR do MRTK invocando o item de menu: **Realidade Misturada** > **Kit de ferramentas** > **Utilitários** > **UnityAR** > Atualizar as definições de script</span><span class="sxs-lookup"><span data-stu-id="10cb0-122">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality** > **Toolkit** > **Utilities** > **UnityAR** > Update Scripting Defines</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="10cb0-123">Compilar o aplicativo para seu dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="10cb0-123">Building your application to your Android device</span></span>

<span data-ttu-id="10cb0-124">Nesta seção, você aprenderá a configurar seu projeto para compilá-lo e implantá-lo em um dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="10cb0-124">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="10cb0-125">No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build e, em seguida, alterne a plataforma para Android:</span><span class="sxs-lookup"><span data-stu-id="10cb0-125">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![Janela Configurações de Build do Unity com a plataforma Android selecionada](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="10cb0-127">Para lembrar como mudar a plataforma de build, consulte as instruções em [Como alternar a plataforma de build](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="10cb0-127">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="10cb0-128">Feche a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="10cb0-128">Close the Build Settings window.</span></span>

<span data-ttu-id="10cb0-129">No menu do Unity, selecione **Realidade Misturada** > **Kit de Ferramentas** > **Utilitários** > **Configurar projeto do MRTK** para abrir a janela do **Configurador de projeto do MRTK**. Confirme se todas as opções estão selecionadas e clique em **Aplicar** para aplicar as configurações:</span><span class="sxs-lookup"><span data-stu-id="10cb0-129">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Configurador de projeto do MRTK no Unity 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="10cb0-131">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Outras Configurações**, selecione **Vulkan** e remova-o clicando no símbolo de **"-"** :</span><span class="sxs-lookup"><span data-stu-id="10cb0-131">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![Outras Configurações do Unity com o Vulcan selecionado](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

<span data-ttu-id="10cb0-133">Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar a cena atual à lista de **Cenas no Build**.</span><span class="sxs-lookup"><span data-stu-id="10cb0-133">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="10cb0-134">Em seguida, use um cabo USB, conecte seu dispositivo Android ao seu computador e selecione-o na lista suspensa **Executar Dispositivo**:</span><span class="sxs-lookup"><span data-stu-id="10cb0-134">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![Janela Configurações de Build do Unity com a cena adicionada e a opção Executar Dispositivo selecionada](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="10cb0-136">Se o dispositivo não aparecer na lista suspensa Executar Dispositivo, pode ser necessário pressionar o botão Atualizar ao lado do menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="10cb0-136">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="10cb0-137">Na janela Configurações de Build, clique no botão **Compilar e Executar** para abrir a janela Compilar Android.</span><span class="sxs-lookup"><span data-stu-id="10cb0-137">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="10cb0-138">Escolha um local adequado para armazenar o build, por exemplo, _D:\MixedRealityLearning\Builds_ e dê ao APK um nome adequado, por exemplo, _MRTKTutorials-AzureSpatialAnchors_ e clique no botão **Salvar** para iniciar o processo de build:</span><span class="sxs-lookup"><span data-stu-id="10cb0-138">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![Janela Configurações de Build do Unity com a janela de prompt Salvar para Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> <span data-ttu-id="10cb0-140">Se você receber algum erro na janela do Console do Unity relacionado aos módulos SDK, NDK ou JDK do Android, será necessário abrir o Hub do Unity e instalar os módulos de Suporte de Build do Android associados.</span><span class="sxs-lookup"><span data-stu-id="10cb0-140">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="10cb0-141">Quando o processo de build for concluído, os aplicativos deverão ser carregados automaticamente em seu dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="10cb0-141">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="10cb0-142">Compilar o aplicativo para seu dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="10cb0-142">Building your application to your iOS device</span></span>

<span data-ttu-id="10cb0-143">Nesta seção, você aprenderá a configurar seu projeto para compilá-lo e implantá-lo em seu dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="10cb0-143">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="10cb0-144">No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build e alterne a plataforma para iOS:</span><span class="sxs-lookup"><span data-stu-id="10cb0-144">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![Janela Configurações de Build do Unity com o iOS selecionado](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="10cb0-146">Para lembrar como mudar a plataforma de build, consulte as instruções em [Como alternar a plataforma de build](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="10cb0-146">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="10cb0-147">Feche a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="10cb0-147">Close the Build Settings window.</span></span>

<span data-ttu-id="10cb0-148">No menu do Unity, selecione **Realidade Misturada** > **Kit de Ferramentas** > **Utilitários** > **Configurar projeto do MRTK** para abrir a janela do **Configurador de projeto do MRTK**. Confirme se todas as opções estão selecionadas e clique em **Aplicar** para aplicar as configurações:</span><span class="sxs-lookup"><span data-stu-id="10cb0-148">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Janela Configurador de Projeto do MRTK no Unity para iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

<span data-ttu-id="10cb0-150">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Outras Configurações**, desmarque a caixa de seleção **Remover Código do Mecanismo** para desabilitá-la:</span><span class="sxs-lookup"><span data-stu-id="10cb0-150">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![Outras Configurações do Unity com a opção Remover Código do Mecanismo desabilitada](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="10cb0-152">Feche a janela Configurações do Player e abra a janela **Configurações de Build** novamente.</span><span class="sxs-lookup"><span data-stu-id="10cb0-152">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="10cb0-153">Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar a cena atual à lista de **Cenas no Build**:</span><span class="sxs-lookup"><span data-stu-id="10cb0-153">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![Janela Configurações de Build do Unity com a cena adicionada](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="10cb0-155">Na janela Configurações de Build, clique no botão **Compilar** para abrir a janela Compilar iOS.</span><span class="sxs-lookup"><span data-stu-id="10cb0-155">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="10cb0-156">Escolha um local adequado para armazenar o projeto do Xcode, por exemplo, _D:\MixedRealityLearning\Builds_, crie uma pasta e dê a ela um nome adequado, por exemplo, _MRTKTutorials-AzureSpatialAnchors_ e, em seguida, clique no botão **Selecionar Pasta** para iniciar o processo de build:</span><span class="sxs-lookup"><span data-stu-id="10cb0-156">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![Janela Configurações de Build do Unity com a janela de prompt Salvar para iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="10cb0-158">Quando o processo de build for concluído, siga as instruções de [Exportar o projeto do Xcode](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) para aprender a implantar o projeto do Xcode em seu dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="10cb0-158">When the build process is complete, follow the [Export the Xcode project](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="10cb0-159">Parabéns</span><span class="sxs-lookup"><span data-stu-id="10cb0-159">Congratulations</span></span>

<span data-ttu-id="10cb0-160">Neste tutorial, você aprendeu a criar o projeto para dispositivos Android e iOS usando o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="10cb0-160">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>
