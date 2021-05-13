---
title: OculusQuestMRTK
description: Documentação para configurar o Oculus Quest no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Oculus Quest,
ms.openlocfilehash: 9350ed7c8426c3bb31cf41493056fb6fc1e26107
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852304"
---
# <a name="how-to-configure-oculus-quest-in-mrtk-using-the-xr-sdk-pipeline"></a><span data-ttu-id="43e8d-104">Como configurar o Oculus Quest no MRTK usando o pipeline do SDK do XR</span><span class="sxs-lookup"><span data-stu-id="43e8d-104">How to configure Oculus Quest in MRTK using the XR SDK pipeline</span></span>

<span data-ttu-id="43e8d-105">Uma [Quest Oculus](https://www.oculus.com/quest/) é necessária.</span><span class="sxs-lookup"><span data-stu-id="43e8d-105">A [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="43e8d-106">O suporte do MRTK para o Oculus Quest é fornecido por meio de duas fontes diferentes, o pipeline XR do Unity e o pacote do Oculus Integration Unity.</span><span class="sxs-lookup"><span data-stu-id="43e8d-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="43e8d-107">O **OCULUS XRSDK provedor de dados** permite o uso de ambas as fontes e deve ser usado para usar o MRTK no Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="43e8d-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to use MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="43e8d-108">O [pipeline XR do Unity](https://docs.unity3d.com/Manual/XR.html) permite o uso de controladores de toque Oculus e acompanhamento de cabeçalho com o Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="43e8d-108">The [Unity's XR Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="43e8d-109">Esse pipeline é o padrão para desenvolver aplicativos XR no Unity 2019,3 e posterior.</span><span class="sxs-lookup"><span data-stu-id="43e8d-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="43e8d-110">Para usar esse pipeline, certifique-se de usar o **Unity 2019,3 ou mais recente**.</span><span class="sxs-lookup"><span data-stu-id="43e8d-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span>

<span data-ttu-id="43e8d-111">O [pacote do Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permite o uso do **acompanhamento manual** com o Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="43e8d-111">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span>
<span data-ttu-id="43e8d-112">Este provedor de dados **não usa o** pipeline **XR** do Unity ou o **tubulator XR herdado**, mas como os controladores e Headtracking são tratados pelo pipeline XR do Unity, as etapas na **configuração do projeto para o Oculus Quest** devem ser seguidas para garantir que você esteja usando o **pipeline XR** e não o pipeline de @ **Legacy herdado** a ser preterido.</span><span class="sxs-lookup"><span data-stu-id="43e8d-112">This data provider does **NOT** use Unity's **XR Pipeline** or **Legacy XR Pipeline**, but because controllers and headtracking are handled by the Unity's XR Pipeline, the steps in **Setting up project for the Oculus Quest** must be followed to ensure that you are using the **XR Pipeline** and not the to-be-deprecated **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="43e8d-113">Configurando o projeto para o Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="43e8d-113">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="43e8d-114">Siga [estas etapas](https://developer.oculus.com/documentation/unity/book-unity-gsg/) para garantir que seu projeto esteja pronto para ser implantado no Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="43e8d-114">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="43e8d-115">Verifique se o [modo de desenvolvedor](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) está habilitado em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="43e8d-115">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="43e8d-116">A instalação dos drivers Oculus ADB é opcional.</span><span class="sxs-lookup"><span data-stu-id="43e8d-116">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-pipeline-for-oculus-quest"></a><span data-ttu-id="43e8d-117">Configurando o pipeline XR para Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="43e8d-117">Setting up the XR Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="43e8d-118">Verifique se o **plug-in OCULUS XR** está instalado na **janela--> Package Manager**</span><span class="sxs-lookup"><span data-stu-id="43e8d-118">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Pacote de plug-in Oculus XR](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="43e8d-120">Verifique se o provedor de plug-in do Oculus está incluído no seu projeto acessando **Editar--> configurações do projeto--> o gerenciamento de plug-ins do XR--provedores de plug-in do >**</span><span class="sxs-lookup"><span data-stu-id="43e8d-120">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Provedor de plug-in do Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="43e8d-122">Configurando o pacote do Unity de Integração do Oculus para habilitar o retrocesso</span><span class="sxs-lookup"><span data-stu-id="43e8d-122">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="43e8d-123">Baixe e importe a [Integração do Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) do Unity Asset Store.</span><span class="sxs-lookup"><span data-stu-id="43e8d-123">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="43e8d-124">A versão mais recente testada para funcionar é a 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="43e8d-124">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="43e8d-125">Versões mais antigas podem ser encontradas neste [arquivo](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span><span class="sxs-lookup"><span data-stu-id="43e8d-125">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span></span>

1. <span data-ttu-id="43e8d-126">Navegue até Kit de Ferramentas de Realidade Misturada > utilitários > Oculus > integrar módulos do Unity de integração do Oculus.</span><span class="sxs-lookup"><span data-stu-id="43e8d-126">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="43e8d-127">Isso atualizará as asmdefs com definições e referências necessárias para que o código relevante do Oculus Quest funcione.</span><span class="sxs-lookup"><span data-stu-id="43e8d-127">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="43e8d-128">Ele também atualizará o arquivo csc para filtrar os avisos obsoletos produzidos pelos ativos de Integração do Oculus.</span><span class="sxs-lookup"><span data-stu-id="43e8d-128">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="43e8d-129">O repo do MRTK contém um arquivo csc que converte avisos em erros; essa conversão interrompe o processo MRTK-Quest configuração.</span><span class="sxs-lookup"><span data-stu-id="43e8d-129">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Asmdef de integração do Oculus](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="43e8d-131">Na pasta Oculus importada (deve ser encontrada em Ativos/Oculus), há um objeto que pode ser script chamado OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="43e8d-131">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="43e8d-132">Nesse arquivo de configuração, você precisa definir HandTrackingSupport como "Controladores e Mãos".</span><span class="sxs-lookup"><span data-stu-id="43e8d-132">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Controlador de integração e mãos do Oculus](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="43e8d-134">Configurando a cena</span><span class="sxs-lookup"><span data-stu-id="43e8d-134">Setting up the scene</span></span>

1. <span data-ttu-id="43e8d-135">Criar uma nova cena do Unity ou abrir uma cena pré-existente, como HandInteractionExamples</span><span class="sxs-lookup"><span data-stu-id="43e8d-135">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples</span></span>
1. <span data-ttu-id="43e8d-136">Adicione o MRTK à cena navegando até Kit de Ferramentas de **Realidade** Misturada  >  **Adicionar à Cena e Configurar**</span><span class="sxs-lookup"><span data-stu-id="43e8d-136">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="43e8d-137">Usando o SDK do Oculus XR Provedor de Dados</span><span class="sxs-lookup"><span data-stu-id="43e8d-137">Using the Oculus XR SDK Data Provider</span></span>

1. <span data-ttu-id="43e8d-138">Configure seu perfil para usar o **SDK do Oculus XR Provedor de Dados**</span><span class="sxs-lookup"><span data-stu-id="43e8d-138">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="43e8d-139">Se não pretende modificar os perfis de configuração</span><span class="sxs-lookup"><span data-stu-id="43e8d-139">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="43e8d-140">Altere seu perfil para DefaultXRSDKConfigurationProfile e vá para Criar e implantar seu [projeto no OculusNix](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="43e8d-140">Change your profile to DefaultXRSDKConfigurationProfile and go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span></span>

    - <span data-ttu-id="43e8d-141">Caso contrário, siga o seguinte:</span><span class="sxs-lookup"><span data-stu-id="43e8d-141">Otherwise follow the following:</span></span>
        - <span data-ttu-id="43e8d-142">Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione **copiar e personalizar** para clonar o perfil de realidade misturada padrão.</span><span class="sxs-lookup"><span data-stu-id="43e8d-142">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Clonar perfil](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="43e8d-144">Selecionar o perfil de configuração de **entrada**</span><span class="sxs-lookup"><span data-stu-id="43e8d-144">Select the **Input** Configuration Profile</span></span>

        ![Perfil de configuração de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="43e8d-146">Selecione **clonar** no perfil do sistema de entrada para habilitar a modificação.</span><span class="sxs-lookup"><span data-stu-id="43e8d-146">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Clonar perfil do sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="43e8d-148">Abra a seção **provedores de dados de entrada** , selecione **Adicionar provedor de dados** na parte superior, e o novo provedor de dados será adicionado no final da lista.</span><span class="sxs-lookup"><span data-stu-id="43e8d-148">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="43e8d-149">Abra o novo provedor de dados e defina o **tipo** como **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="43e8d-149">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span></span>

        ![Oculus adicionar XRSDK Provedor de Dados](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. <span data-ttu-id="43e8d-151">O SDK do Oculus XR Provedor de Dados inclui um Rig da câmera OVR pré-fabricado que configura automaticamente o projeto com um dispositivo de câmera OVR e as mãos de OVR para rotear corretamente a entrada.</span><span class="sxs-lookup"><span data-stu-id="43e8d-151">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="43e8d-152">Adicionar manualmente um Rig da câmera OVR à cena exigirá a configuração manual de configurações e de entrada.</span><span class="sxs-lookup"><span data-stu-id="43e8d-152">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="43e8d-153">Criar e implantar seu projeto no Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="43e8d-153">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="43e8d-154">Conecte seu Oculus Quest por meio de um cabo USB 3,0-> USB C</span><span class="sxs-lookup"><span data-stu-id="43e8d-154">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="43e8d-155">Navegue até o **arquivo > configurações de Build**</span><span class="sxs-lookup"><span data-stu-id="43e8d-155">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="43e8d-156">Alterar a implantação para **Android**</span><span class="sxs-lookup"><span data-stu-id="43e8d-156">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="43e8d-157">Verifique se a Quest Oculus está selecionada como o dispositivo de execução aplicável</span><span class="sxs-lookup"><span data-stu-id="43e8d-157">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus executar dispositivo](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="43e8d-159">Selecione compilar e executar</span><span class="sxs-lookup"><span data-stu-id="43e8d-159">Select Build and Run</span></span>
    - <span data-ttu-id="43e8d-160">Você provavelmente encontrará o seguinte conjunto de erros de compilação ao selecionar *Compilar e executar* a primeira vez.</span><span class="sxs-lookup"><span data-stu-id="43e8d-160">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="43e8d-161">Você deve ser capaz de implantar com êxito ao selecionar *Build e Executar* novamente.</span><span class="sxs-lookup"><span data-stu-id="43e8d-161">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Erros de build esperados do Oculus](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="43e8d-163">Aceite o _prompt Permitir Depuração USB_ de dentro da busca</span><span class="sxs-lookup"><span data-stu-id="43e8d-163">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="43e8d-164">Veja sua cena dentro do Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="43e8d-164">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="43e8d-165">Removendo a integração do Oculus do projeto</span><span class="sxs-lookup"><span data-stu-id="43e8d-165">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="43e8d-166">Navegue até o Kit de Ferramentas de Realidade Misturada > Oculus > Módulos separados do Oculus Integration Unity  ![ Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="43e8d-166">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="43e8d-167">Permitir que o Unity seja atualizado como referências no Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef e outros arquivos serão modificados nesta etapa</span><span class="sxs-lookup"><span data-stu-id="43e8d-167">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="43e8d-168">Fechar Unity</span><span class="sxs-lookup"><span data-stu-id="43e8d-168">Close Unity</span></span>
1. <span data-ttu-id="43e8d-169">Feche Visual Studio, se estiver aberto</span><span class="sxs-lookup"><span data-stu-id="43e8d-169">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="43e8d-170">Abra Explorador de Arquivos e navegue até a raiz do projeto unity do MRTK</span><span class="sxs-lookup"><span data-stu-id="43e8d-170">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="43e8d-171">Excluir o diretório UnityProjectName/Library</span><span class="sxs-lookup"><span data-stu-id="43e8d-171">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="43e8d-172">Excluir o diretório UnityProjectName/Assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="43e8d-172">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="43e8d-173">Excluir o arquivo UnityProjectName/Assets/Oculus.meta</span><span class="sxs-lookup"><span data-stu-id="43e8d-173">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="43e8d-174">Reabrir o Unity</span><span class="sxs-lookup"><span data-stu-id="43e8d-174">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="43e8d-175">Erros comuns</span><span class="sxs-lookup"><span data-stu-id="43e8d-175">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="43e8d-176">Busca não reconhecida pelo Unity</span><span class="sxs-lookup"><span data-stu-id="43e8d-176">Quest not recognized by Unity</span></span>

<span data-ttu-id="43e8d-177">Certifique-se de que os caminhos do Android estão configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="43e8d-177">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="43e8d-178">Se você continuar encontrando problemas, siga este [guia](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="43e8d-178">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="43e8d-179">**Editar > preferências > ferramentas externas > Android**</span><span class="sxs-lookup"><span data-stu-id="43e8d-179">**Edit > Preferences > External Tools > Android**</span></span>

![Configuração das Ferramentas do Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
