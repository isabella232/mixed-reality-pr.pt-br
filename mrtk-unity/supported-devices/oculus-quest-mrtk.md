---
title: MRTK de solicitação Oculus
description: Documentação para configurar o Oculus Quest no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Oculus Quest,
ms.openlocfilehash: 0892e0d416cd07d1bedbeea0ddb316e3eb012b94
ms.sourcegitcommit: 4c1dd5c22af69eeb192425118c2bfb95344b8dd9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110441175"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a><span data-ttu-id="85388-104">Criando e implantando MRTK para Oculus Quest usando o pipeline do SDK do XR</span><span class="sxs-lookup"><span data-stu-id="85388-104">Building and deploying MRTK to Oculus Quest using the XR SDK pipeline</span></span>

<span data-ttu-id="85388-105">Uma [Quest Oculus](https://www.oculus.com/quest/) é necessária.</span><span class="sxs-lookup"><span data-stu-id="85388-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="85388-106">O suporte do MRTK para o Oculus Quest é fornecido por meio de duas fontes diferentes, o pipeline do SDK XR do Unity e o pacote do Oculus Integration Unity.</span><span class="sxs-lookup"><span data-stu-id="85388-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="85388-107">O **OCULUS XRSDK provedor de dados** permite o uso de ambas as fontes e deve ser usado para implantar MRTK no Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="85388-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="85388-108">O [pipeline do SDK do Unity XR](https://docs.unity3d.com/Manual/XR.html) permite o uso de controladores de toque Oculus e acompanhamento de cabeçalho com o Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="85388-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="85388-109">Esse pipeline é o padrão para desenvolver aplicativos XR no Unity 2019,3 e posterior.</span><span class="sxs-lookup"><span data-stu-id="85388-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="85388-110">Para usar esse pipeline, certifique-se de usar o **Unity 2019,3 ou mais recente**.</span><span class="sxs-lookup"><span data-stu-id="85388-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="85388-111">Isso é **necessário** para implantar aplicativos MRTK no Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="85388-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span> 

<span data-ttu-id="85388-112">O [pacote do Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permite o uso do **acompanhamento manual** com o Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="85388-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="85388-113">Este provedor de dados **não usa o** **pipeline do SDK XR** do Unity ou o **pipeline XR herdado**.</span><span class="sxs-lookup"><span data-stu-id="85388-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="85388-114">Configurando o projeto para o Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="85388-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="85388-115">Siga [estas etapas](https://developer.oculus.com/documentation/unity/book-unity-gsg/) para garantir que seu projeto esteja pronto para ser implantado no Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="85388-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="85388-116">Verifique se o [modo de desenvolvedor](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) está habilitado em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="85388-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="85388-117">A instalação dos drivers Oculus ADB é opcional.</span><span class="sxs-lookup"><span data-stu-id="85388-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="85388-118">Configurando o pipeline do SDK do XR para Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="85388-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="85388-119">Verifique se o **plug-in OCULUS XR** está instalado na **janela--> Package Manager**</span><span class="sxs-lookup"><span data-stu-id="85388-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Pacote de plug-in Oculus XR](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="85388-121">Verifique se o provedor de plug-in do Oculus está incluído no seu projeto acessando **Editar--> configurações do projeto--> o gerenciamento de plug-ins do XR--provedores de plug-in do >**</span><span class="sxs-lookup"><span data-stu-id="85388-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Provedor de plug-in Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="85388-123">Configurando o pacote do Oculus Integration Unity para habilitar o handtracking</span><span class="sxs-lookup"><span data-stu-id="85388-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="85388-124">Baixe e importe a [integração do Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) do repositório de ativos do Unity.</span><span class="sxs-lookup"><span data-stu-id="85388-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="85388-125">A versão mais recente testada para o trabalho é 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="85388-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="85388-126">Versões mais antigas podem ser encontradas neste [arquivo morto](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span><span class="sxs-lookup"><span data-stu-id="85388-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span></span>

1. <span data-ttu-id="85388-127">Navegue até Mixed Reality Toolkit > Utilities > Oculus > integrar módulos do Oculus Integration Unity.</span><span class="sxs-lookup"><span data-stu-id="85388-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="85388-128">Isso atualizará o asmdefs com definições e referências necessárias para que o código relevante da Quest Oculus funcione.</span><span class="sxs-lookup"><span data-stu-id="85388-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="85388-129">Ele também atualizará o arquivo csc para filtrar os avisos obsoletos produzidos pelos ativos de integração do Oculus.</span><span class="sxs-lookup"><span data-stu-id="85388-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="85388-130">O repositório MRTK contém um arquivo csc que converte avisos em erros, essa conversão interrompe o processo de configuração MRTK-Quest.</span><span class="sxs-lookup"><span data-stu-id="85388-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Integração do Oculus Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="85388-132">Na pasta importada oculus (ela deve ser encontrada em assets/Oculus), há um objeto programável chamado OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="85388-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="85388-133">Nesse arquivo de configuração, você precisa definir HandTrackingSupport como "controladores e mãos".</span><span class="sxs-lookup"><span data-stu-id="85388-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Controlador de integração e mãos do Oculus](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="85388-135">Configurando a cena</span><span class="sxs-lookup"><span data-stu-id="85388-135">Setting up the scene</span></span>

1. <span data-ttu-id="85388-136">Criar uma nova cena do Unity ou abrir uma cena pré-existente como HandInteractionExamples</span><span class="sxs-lookup"><span data-stu-id="85388-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples</span></span>
1. <span data-ttu-id="85388-137">Adicione MRTK à cena navegando até **Mixed Reality Toolkit**  >  **Adicionar à cena e configurar**</span><span class="sxs-lookup"><span data-stu-id="85388-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="85388-138">Usando o SDK do Oculus XR Provedor de Dados</span><span class="sxs-lookup"><span data-stu-id="85388-138">Using the Oculus XR SDK Data Provider</span></span>

1. <span data-ttu-id="85388-139">Configurar seu perfil para usar o **SDK do OCULUS XR provedor de dados**</span><span class="sxs-lookup"><span data-stu-id="85388-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="85388-140">Se não pretende modificar os perfis de configuração</span><span class="sxs-lookup"><span data-stu-id="85388-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="85388-141">Altere seu perfil para DefaultXRSDKConfigurationProfile e vá para [Compilar e implantar seu projeto no Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="85388-141">Change your profile to DefaultXRSDKConfigurationProfile and go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span></span>

    - <span data-ttu-id="85388-142">Caso contrário, siga o seguinte:</span><span class="sxs-lookup"><span data-stu-id="85388-142">Otherwise follow the following:</span></span>
        - <span data-ttu-id="85388-143">Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione **copiar e personalizar** para clonar o perfil de realidade misturada padrão.</span><span class="sxs-lookup"><span data-stu-id="85388-143">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Clonar perfil](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="85388-145">Selecionar o perfil de configuração de **entrada**</span><span class="sxs-lookup"><span data-stu-id="85388-145">Select the **Input** Configuration Profile</span></span>

        ![Perfil de configuração de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="85388-147">Selecione **clonar** no perfil do sistema de entrada para habilitar a modificação.</span><span class="sxs-lookup"><span data-stu-id="85388-147">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Clonar perfil do sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="85388-149">Abra a seção **provedores de dados de entrada** , selecione **Adicionar provedor de dados** na parte superior, e o novo provedor de dados será adicionado no final da lista.</span><span class="sxs-lookup"><span data-stu-id="85388-149">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="85388-150">Abra o novo provedor de dados e defina o **tipo** como **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="85388-150">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span></span>

        ![Oculus adicionar XRSDK Provedor de Dados](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. <span data-ttu-id="85388-152">O SDK do Oculus XR Provedor de Dados inclui um Rig da câmera OVR pré-fabricado que configura automaticamente o projeto com um dispositivo de câmera OVR e as mãos de OVR para rotear corretamente a entrada.</span><span class="sxs-lookup"><span data-stu-id="85388-152">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="85388-153">Adicionar manualmente um Rig da câmera OVR à cena exigirá a configuração manual de configurações e de entrada.</span><span class="sxs-lookup"><span data-stu-id="85388-153">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="85388-154">Criar e implantar seu projeto no Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="85388-154">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="85388-155">Conecte seu Oculus Quest por meio de um cabo USB 3,0-> USB C</span><span class="sxs-lookup"><span data-stu-id="85388-155">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="85388-156">Navegue até o **arquivo > configurações de Build**</span><span class="sxs-lookup"><span data-stu-id="85388-156">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="85388-157">Alterar a implantação para **Android**</span><span class="sxs-lookup"><span data-stu-id="85388-157">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="85388-158">Verifique se a Quest Oculus está selecionada como o dispositivo de execução aplicável</span><span class="sxs-lookup"><span data-stu-id="85388-158">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus executar dispositivo](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="85388-160">Selecione compilar e executar</span><span class="sxs-lookup"><span data-stu-id="85388-160">Select Build and Run</span></span>
    - <span data-ttu-id="85388-161">Você provavelmente encontrará o seguinte conjunto de erros de compilação ao selecionar *Compilar e executar* a primeira vez.</span><span class="sxs-lookup"><span data-stu-id="85388-161">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="85388-162">Você deve ser capaz de implantar com êxito ao selecionar *Compilar e executar* novamente.</span><span class="sxs-lookup"><span data-stu-id="85388-162">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus erros de compilação esperados](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="85388-164">Aceite o prompt _permitir depuração de USB_ de dentro do Quest</span><span class="sxs-lookup"><span data-stu-id="85388-164">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="85388-165">Veja sua cena dentro do Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="85388-165">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="85388-166">Removendo a integração do Oculus do projeto</span><span class="sxs-lookup"><span data-stu-id="85388-166">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="85388-167">Navegue até o kit de ferramentas de realidade misturada > Oculus > módulos de integração do Oculus separados  ![ Oculus separação Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="85388-167">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="85388-168">Permitir que o Unity atualize como referências no Microsoft. MixedReality. Toolkit. Providers. Oculus. asmdef e outros arquivos sejam modificados nesta etapa</span><span class="sxs-lookup"><span data-stu-id="85388-168">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="85388-169">Fechar o Unity</span><span class="sxs-lookup"><span data-stu-id="85388-169">Close Unity</span></span>
1. <span data-ttu-id="85388-170">Feche o Visual Studio, se ele estiver aberto</span><span class="sxs-lookup"><span data-stu-id="85388-170">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="85388-171">Abra o explorador de arquivos e navegue até a raiz do projeto do MRTK Unity</span><span class="sxs-lookup"><span data-stu-id="85388-171">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="85388-172">Excluir o diretório de UnityProjectName/biblioteca</span><span class="sxs-lookup"><span data-stu-id="85388-172">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="85388-173">Excluir o diretório UnityProjectName/assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="85388-173">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="85388-174">Excluir o arquivo UnityProjectName/assets/Oculus. meta</span><span class="sxs-lookup"><span data-stu-id="85388-174">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="85388-175">Reabrir o Unity</span><span class="sxs-lookup"><span data-stu-id="85388-175">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="85388-176">Erros comuns</span><span class="sxs-lookup"><span data-stu-id="85388-176">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="85388-177">Quest não reconhecida pelo Unity</span><span class="sxs-lookup"><span data-stu-id="85388-177">Quest not recognized by Unity</span></span>

<span data-ttu-id="85388-178">Verifique se os caminhos do Android estão configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="85388-178">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="85388-179">Se você continuar a encontrar problemas, siga este [guia](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="85388-179">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="85388-180">**Editar preferências de > > ferramentas externas > Android**</span><span class="sxs-lookup"><span data-stu-id="85388-180">**Edit > Preferences > External Tools > Android**</span></span>

![Configuração de ferramentas do Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
