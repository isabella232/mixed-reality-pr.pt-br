---
title: Implantação no Oculus Quest
description: Documentação para configurar o Oculus Quest no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Oculus Quest
ms.openlocfilehash: d910f26374b21be26377bd40b9be0d45872e007a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177455"
---
# <a name="deploying-to-oculus-quest"></a><span data-ttu-id="419c9-104">Implantação no Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="419c9-104">Deploying to Oculus Quest</span></span>

<span data-ttu-id="419c9-105">Uma [Quest Oculus](https://www.oculus.com/quest/) é necessária.</span><span class="sxs-lookup"><span data-stu-id="419c9-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="419c9-106">O suporte do MRTK para o Oculus Quest é fornecido por meio de duas fontes diferentes, o pipeline do SDK XR do Unity e o pacote do Oculus Integration Unity.</span><span class="sxs-lookup"><span data-stu-id="419c9-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="419c9-107">o **Oculus XRSDK Provedor de Dados** permite o uso de ambas as fontes e deve ser usado para implantar MRTK no Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="419c9-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="419c9-108">O [pipeline do SDK do Unity XR](https://docs.unity3d.com/Manual/XR.html) permite o uso de controladores de toque Oculus e acompanhamento de cabeçalho com o Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="419c9-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="419c9-109">Esse pipeline é o padrão para desenvolver aplicativos XR no Unity 2019,3 e posterior.</span><span class="sxs-lookup"><span data-stu-id="419c9-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="419c9-110">Para usar esse pipeline, certifique-se de usar o **Unity 2019,3 ou mais recente**.</span><span class="sxs-lookup"><span data-stu-id="419c9-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="419c9-111">Isso é **necessário** para implantar aplicativos MRTK no Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="419c9-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span>

<span data-ttu-id="419c9-112">O [pacote do Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permite o uso do **acompanhamento manual** com o Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="419c9-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="419c9-113">Este provedor de dados **não usa o** **pipeline do SDK XR** do Unity ou o **pipeline XR herdado**.</span><span class="sxs-lookup"><span data-stu-id="419c9-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="419c9-114">Configurando o projeto para o Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="419c9-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="419c9-115">Siga [estas etapas](https://developer.oculus.com/documentation/unity/book-unity-gsg/) para garantir que seu projeto esteja pronto para ser implantado no Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="419c9-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="419c9-116">Verifique se o [modo de desenvolvedor](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) está habilitado em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="419c9-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="419c9-117">A instalação dos drivers Oculus ADB é opcional.</span><span class="sxs-lookup"><span data-stu-id="419c9-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="419c9-118">Configurando o pipeline do SDK do XR para Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="419c9-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="419c9-119">verifique se o **plug-in Oculus XR** está instalado em **Window--> Gerenciador de Pacotes**</span><span class="sxs-lookup"><span data-stu-id="419c9-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Pacote de plug-in Oculus XR](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="419c9-121">verifique se o provedor de Plug-in do Oculus está incluído no seu projeto acessando **editar--> Project Configurações--> o gerenciamento de plug-ins do Management--> provedores de plug-in**</span><span class="sxs-lookup"><span data-stu-id="419c9-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Provedor de plug-in Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="419c9-123">Configurando o pacote do Oculus Integration Unity para habilitar o handtracking</span><span class="sxs-lookup"><span data-stu-id="419c9-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="419c9-124">Baixe e importe a [integração do Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) do repositório de ativos do Unity.</span><span class="sxs-lookup"><span data-stu-id="419c9-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="419c9-125">A versão mais recente testada para o trabalho é 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="419c9-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="419c9-126">Versões mais antigas podem ser encontradas neste [arquivo morto](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span><span class="sxs-lookup"><span data-stu-id="419c9-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span></span>

1. <span data-ttu-id="419c9-127">navegue até realidade misturada Toolkit > Utilities > Oculus > integrar módulos do Oculus Integration Unity.</span><span class="sxs-lookup"><span data-stu-id="419c9-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="419c9-128">Isso atualizará o asmdefs com definições e referências necessárias para que o código relevante da Quest Oculus funcione.</span><span class="sxs-lookup"><span data-stu-id="419c9-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="419c9-129">Ele também atualizará o arquivo csc para filtrar os avisos obsoletos produzidos pelos ativos de integração do Oculus.</span><span class="sxs-lookup"><span data-stu-id="419c9-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="419c9-130">O repositório MRTK contém um arquivo csc que converte avisos em erros, essa conversão interrompe o processo de configuração MRTK-Quest.</span><span class="sxs-lookup"><span data-stu-id="419c9-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Integração do Oculus Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="419c9-132">Na pasta importada oculus (ela deve ser encontrada em assets/Oculus), há um objeto programável chamado OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="419c9-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="419c9-133">Nesse arquivo de configuração, você precisa definir HandTrackingSupport como "controladores e mãos".</span><span class="sxs-lookup"><span data-stu-id="419c9-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Controlador de integração e mãos do Oculus](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="419c9-135">Configurando a cena</span><span class="sxs-lookup"><span data-stu-id="419c9-135">Setting up the scene</span></span>

1. <span data-ttu-id="419c9-136">Crie uma nova cena do Unity ou abra uma cena já existente como HandInteractionExamples.</span><span class="sxs-lookup"><span data-stu-id="419c9-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples.</span></span>
1. <span data-ttu-id="419c9-137">adicione MRTK à cena navegando até a **realidade misturada Toolkit**  >  **adicionar à cena e configurar**.</span><span class="sxs-lookup"><span data-stu-id="419c9-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="419c9-138">usando o SDK do Oculus XR Provedor de Dados</span><span class="sxs-lookup"><span data-stu-id="419c9-138">Using the Oculus XR SDK Data Provider</span></span>

::: moniker range=">= mrtkunity-2021-05"

1. <span data-ttu-id="419c9-139">configurar seu perfil para usar o **SDK do Oculus XR Provedor de Dados**</span><span class="sxs-lookup"><span data-stu-id="419c9-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="419c9-140">Se não pretende modificar os perfis de configuração</span><span class="sxs-lookup"><span data-stu-id="419c9-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="419c9-141">Use qualquer um dos perfis de MRTK padrão, que são todos configurados nos pipelines XR do Unity.</span><span class="sxs-lookup"><span data-stu-id="419c9-141">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="419c9-142">O DefaultXRSDKConfigurationProfile anterior agora está rotulado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="419c9-142">The previous DefaultXRSDKConfigurationProfile is now labeled obsolete.</span></span>
        - <span data-ttu-id="419c9-143">Vá para [Compilar e implantar seu projeto no Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span><span class="sxs-lookup"><span data-stu-id="419c9-143">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="419c9-144">Caso contrário, siga o seguinte:</span><span class="sxs-lookup"><span data-stu-id="419c9-144">Otherwise follow the following:</span></span>
        - <span data-ttu-id="419c9-145">Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione **copiar e personalizar** para clonar o perfil de realidade misturada padrão.</span><span class="sxs-lookup"><span data-stu-id="419c9-145">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Clonar perfil](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="419c9-147">Selecione o perfil de configuração de **entrada** .</span><span class="sxs-lookup"><span data-stu-id="419c9-147">Select the **Input** Configuration Profile.</span></span>

        ![Perfil de configuração de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="419c9-149">Selecione **clonar** no perfil do sistema de entrada para habilitar a modificação.</span><span class="sxs-lookup"><span data-stu-id="419c9-149">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Clonar perfil do sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="419c9-151">abra a seção **provedores de dados de entrada** , selecione **adicionar Provedor de Dados** na parte superior, e o novo provedor de dados será adicionado no final da lista.</span><span class="sxs-lookup"><span data-stu-id="419c9-151">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="419c9-152">Abra o novo provedor de dados e defina o **tipo** como **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**.</span><span class="sxs-lookup"><span data-stu-id="419c9-152">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus adicionar XRSDK Provedor de Dados](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. <span data-ttu-id="419c9-154">configurar seu perfil para usar o **SDK do Oculus XR Provedor de Dados**</span><span class="sxs-lookup"><span data-stu-id="419c9-154">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="419c9-155">Se não pretende modificar os perfis de configuração</span><span class="sxs-lookup"><span data-stu-id="419c9-155">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="419c9-156">Altere seu perfil para DefaultXRSDKConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="419c9-156">Change your profile to DefaultXRSDKConfigurationProfile.</span></span>
        - <span data-ttu-id="419c9-157">Vá para [Compilar e implantar seu projeto no Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span><span class="sxs-lookup"><span data-stu-id="419c9-157">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="419c9-158">Caso contrário, siga o seguinte:</span><span class="sxs-lookup"><span data-stu-id="419c9-158">Otherwise follow the following:</span></span>
        - <span data-ttu-id="419c9-159">Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione **copiar e personalizar** para clonar o perfil de realidade misturada padrão.</span><span class="sxs-lookup"><span data-stu-id="419c9-159">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Clonar perfil](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="419c9-161">Selecione o perfil de configuração de **entrada** .</span><span class="sxs-lookup"><span data-stu-id="419c9-161">Select the **Input** Configuration Profile.</span></span>

        ![Perfil de configuração de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="419c9-163">Selecione **clonar** no perfil do sistema de entrada para habilitar a modificação.</span><span class="sxs-lookup"><span data-stu-id="419c9-163">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Clonar perfil do sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="419c9-165">abra a seção **provedores de dados de entrada** , selecione **adicionar Provedor de Dados** na parte superior, e o novo provedor de dados será adicionado no final da lista.</span><span class="sxs-lookup"><span data-stu-id="419c9-165">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="419c9-166">Abra o novo provedor de dados e defina o **tipo** como **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**.</span><span class="sxs-lookup"><span data-stu-id="419c9-166">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus adicionar XRSDK Provedor de Dados](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. <span data-ttu-id="419c9-168">o SDK do Oculus XR Provedor de Dados inclui um rig da câmera ovr pré-fabricado que configura automaticamente o projeto com um dispositivo de câmera ovr e as mãos de ovr para rotear corretamente a entrada.</span><span class="sxs-lookup"><span data-stu-id="419c9-168">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="419c9-169">Adicionar manualmente um Rig da câmera OVR à cena exigirá a configuração manual de configurações e de entrada.</span><span class="sxs-lookup"><span data-stu-id="419c9-169">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="419c9-170">Criar e implantar seu projeto no Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="419c9-170">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="419c9-171">Conecte seu Oculus Quest por meio de um cabo USB 3,0-> USB C</span><span class="sxs-lookup"><span data-stu-id="419c9-171">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="419c9-172">navegue até o **arquivo > Build Configurações**</span><span class="sxs-lookup"><span data-stu-id="419c9-172">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="419c9-173">Alterar a implantação para **Android**</span><span class="sxs-lookup"><span data-stu-id="419c9-173">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="419c9-174">Verifique se a Quest Oculus está selecionada como o dispositivo de execução aplicável</span><span class="sxs-lookup"><span data-stu-id="419c9-174">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus executar dispositivo](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="419c9-176">Selecione compilar e executar</span><span class="sxs-lookup"><span data-stu-id="419c9-176">Select Build and Run</span></span>
    - <span data-ttu-id="419c9-177">Você provavelmente encontrará o seguinte conjunto de erros de compilação ao selecionar *Compilar e executar* a primeira vez.</span><span class="sxs-lookup"><span data-stu-id="419c9-177">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="419c9-178">Você deve ser capaz de implantar com êxito ao selecionar *Compilar e executar* novamente.</span><span class="sxs-lookup"><span data-stu-id="419c9-178">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus erros de compilação esperados](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="419c9-180">Aceite o prompt _permitir depuração de USB_ de dentro do Quest</span><span class="sxs-lookup"><span data-stu-id="419c9-180">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="419c9-181">Veja sua cena dentro do Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="419c9-181">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="419c9-182">Removendo a integração do Oculus do Project</span><span class="sxs-lookup"><span data-stu-id="419c9-182">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="419c9-183">navegue até a realidade misturada Toolkit > Oculus > módulos do Unity integração Oculus separados ![ Oculus separação Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="419c9-183">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="419c9-184">Deixe o Unity atualizar como referências no Microsoft. MixedReality. Toolkit. Providers. Oculus. asmdef e outros arquivos são modificados nesta etapa</span><span class="sxs-lookup"><span data-stu-id="419c9-184">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="419c9-185">Fechar o Unity</span><span class="sxs-lookup"><span data-stu-id="419c9-185">Close Unity</span></span>
1. <span data-ttu-id="419c9-186">feche Visual Studio, se estiver aberto</span><span class="sxs-lookup"><span data-stu-id="419c9-186">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="419c9-187">Abra o explorador de arquivos e navegue até a raiz do projeto do MRTK Unity</span><span class="sxs-lookup"><span data-stu-id="419c9-187">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="419c9-188">Excluir o diretório de UnityProjectName/biblioteca</span><span class="sxs-lookup"><span data-stu-id="419c9-188">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="419c9-189">Excluir o diretório UnityProjectName/assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="419c9-189">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="419c9-190">Excluir o arquivo UnityProjectName/assets/Oculus. meta</span><span class="sxs-lookup"><span data-stu-id="419c9-190">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="419c9-191">Reabrir o Unity</span><span class="sxs-lookup"><span data-stu-id="419c9-191">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="419c9-192">Erros comuns</span><span class="sxs-lookup"><span data-stu-id="419c9-192">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="419c9-193">Quest não reconhecida pelo Unity</span><span class="sxs-lookup"><span data-stu-id="419c9-193">Quest not recognized by Unity</span></span>

<span data-ttu-id="419c9-194">Verifique se os caminhos do Android estão configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="419c9-194">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="419c9-195">Se você continuar a encontrar problemas, siga este [guia](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="419c9-195">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="419c9-196">**Editar preferências de > > ferramentas externas > Android**</span><span class="sxs-lookup"><span data-stu-id="419c9-196">**Edit > Preferences > External Tools > Android**</span></span>

![Configuração de ferramentas do Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
