---
title: MRTK de solicitação Oculus
description: Documentação a ser configurada para o Oculus Quest no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Oculus Quest,
ms.openlocfilehash: 6b9c3a8f51388785f685714ef02be680bb98e14c
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908391"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a><span data-ttu-id="ac8b5-104">Criando e implantando o MRTK no Oculus Quest usando o pipeline do SDK do XR</span><span class="sxs-lookup"><span data-stu-id="ac8b5-104">Building and deploying MRTK to Oculus Quest using the XR SDK pipeline</span></span>

<span data-ttu-id="ac8b5-105">Uma [Oculus Quest](https://www.oculus.com/quest/) é necessária.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="ac8b5-106">O suporte do MRTK para o Oculus Quest é feito por meio de duas fontes diferentes, o pipeline do SDK XR do Unity e o pacote do Unity de Integração do Oculus.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="ac8b5-107">O **Oculus XRSDK Provedor de Dados** permite o uso de ambas as fontes e deve ser usado para implantar o MRTK na Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="ac8b5-108">O [Pipeline do SDK](https://docs.unity3d.com/Manual/XR.html) do Unity XR permite o uso de controladores Oculus Touch e acompanhamento de cabeça com o Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="ac8b5-109">Esse pipeline é o padrão para desenvolver aplicativos XR no Unity 2019.3 e além.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="ac8b5-110">Para usar esse pipeline, certifique-se de usar **o Unity 2019.3 ou mais novo.**</span><span class="sxs-lookup"><span data-stu-id="ac8b5-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="ac8b5-111">Isso é **necessário para** implantar aplicativos MRTK no Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span>

<span data-ttu-id="ac8b5-112">O [pacote do Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permite o uso do acompanhamento de **mão** com o Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="ac8b5-113">Esse provedor de dados **NÃO usa** o Pipeline **do SDK XR do** Unity ou o Pipeline **XR herdado.**</span><span class="sxs-lookup"><span data-stu-id="ac8b5-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="ac8b5-114">Configurando o projeto para o Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="ac8b5-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="ac8b5-115">Siga [estas etapas](https://developer.oculus.com/documentation/unity/book-unity-gsg/) para garantir que seu projeto esteja pronto para ser implantado no Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="ac8b5-116">Verifique se [o modo de](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) desenvolvedor está habilitado em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="ac8b5-117">Instalar os Drivers do Oculus ADB é opcional.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="ac8b5-118">Configurando o pipeline do SDK do XR para o Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="ac8b5-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="ac8b5-119">Verifique se o **plug-in do Oculus XR** está instalado em **Janela --> Gerenciador de Pacotes**</span><span class="sxs-lookup"><span data-stu-id="ac8b5-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Pacote de plug-in do Oculus XR](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="ac8b5-121">Certifique-se de que o Provedor de Plug-in do Oculus está incluído em seu projeto indo para Editar --> Configurações do Projeto --> Gerenciamento de **Plug-in XR --> Provedores de Plug-in**</span><span class="sxs-lookup"><span data-stu-id="ac8b5-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Provedor de plug-in do Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="ac8b5-123">Configurando o pacote do Unity de Integração do Oculus para habilitar o retrocesso</span><span class="sxs-lookup"><span data-stu-id="ac8b5-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="ac8b5-124">Baixe e importe a [Integração do Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) do Unity Asset Store.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="ac8b5-125">A versão mais recente testada para funcionar é a 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="ac8b5-126">Versões mais antigas podem ser encontradas neste [arquivo](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span><span class="sxs-lookup"><span data-stu-id="ac8b5-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span></span>

1. <span data-ttu-id="ac8b5-127">Navegue até Kit de Ferramentas de Realidade Misturada > utilitários > Oculus > integrar módulos do Unity de integração do Oculus.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="ac8b5-128">Isso atualizará as asmdefs com definições e referências necessárias para que o código relevante do Oculus Quest funcione.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="ac8b5-129">Ele também atualizará o arquivo csc para filtrar os avisos obsoletos produzidos pelos ativos de Integração do Oculus.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="ac8b5-130">O repo do MRTK contém um arquivo csc que converte avisos em erros; essa conversão interrompe o processo MRTK-Quest configuração.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Asmdef de integração do Oculus](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="ac8b5-132">Na pasta Oculus importada (deve ser encontrada em Ativos/Oculus), há um objeto que pode ser script chamado OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="ac8b5-133">Nesse arquivo de configuração, você precisa definir HandTrackingSupport como "Controladores e Mãos".</span><span class="sxs-lookup"><span data-stu-id="ac8b5-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Controlador de integração e mãos do Oculus](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="ac8b5-135">Configurando a cena</span><span class="sxs-lookup"><span data-stu-id="ac8b5-135">Setting up the scene</span></span>

1. <span data-ttu-id="ac8b5-136">Crie uma nova cena do Unity ou abra uma cena pré-existente, como HandInteractionExamples.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples.</span></span>
1. <span data-ttu-id="ac8b5-137">Adicione o MRTK à cena navegando até Kit de Ferramentas de **Realidade** Misturada  >  **Adicionar à Cena e Configurar**.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="ac8b5-138">Usando o SDK do Oculus XR Provedor de Dados</span><span class="sxs-lookup"><span data-stu-id="ac8b5-138">Using the Oculus XR SDK Data Provider</span></span>

::: moniker range=">= mrtkunity-2021-05"

1. <span data-ttu-id="ac8b5-139">Configure seu perfil para usar o **SDK do Oculus XR Provedor de Dados**</span><span class="sxs-lookup"><span data-stu-id="ac8b5-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="ac8b5-140">Se não pretende modificar os perfis de configuração</span><span class="sxs-lookup"><span data-stu-id="ac8b5-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="ac8b5-141">Use qualquer um dos perfis padrão do MRTK, que são todos configurados nos pipelines XR do Unity.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-141">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="ac8b5-142">O DefaultXRSDKConfigurationProfile anterior agora é rotulado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-142">The previous DefaultXRSDKConfigurationProfile is now labeled obsolete.</span></span>
        - <span data-ttu-id="ac8b5-143">Vá para [Criar e implantar seu projeto no Oculus Quest.](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="ac8b5-143">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="ac8b5-144">Caso contrário, siga o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ac8b5-144">Otherwise follow the following:</span></span>
        - <span data-ttu-id="ac8b5-145">Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione Copiar e **Personalizar** para clonar o perfil de realidade misturada padrão.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-145">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Clonar Perfil](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="ac8b5-147">Selecione o **Perfil de Configuração** de Entrada.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-147">Select the **Input** Configuration Profile.</span></span>

        ![Perfil de configuração de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="ac8b5-149">Selecione **Clonar** no perfil do sistema de entrada para habilitar a modificação.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-149">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Clonar perfil do sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="ac8b5-151">Abra a **seção Provedores de** Dados de **Entrada, selecione Adicionar Provedor de Dados** na parte superior e o novo provedor de dados será adicionado ao final da lista.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-151">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="ac8b5-152">Abra o novo provedor de dados e de definir **o Tipo** como **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager.**</span><span class="sxs-lookup"><span data-stu-id="ac8b5-152">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus Add XRSDK Provedor de Dados](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. <span data-ttu-id="ac8b5-154">Configure seu perfil para usar o **SDK do Oculus XR Provedor de Dados**</span><span class="sxs-lookup"><span data-stu-id="ac8b5-154">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="ac8b5-155">Se não pretende modificar os perfis de configuração</span><span class="sxs-lookup"><span data-stu-id="ac8b5-155">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="ac8b5-156">Altere seu perfil para DefaultXRSDKConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-156">Change your profile to DefaultXRSDKConfigurationProfile.</span></span>
        - <span data-ttu-id="ac8b5-157">Vá para [Criar e implantar seu projeto no Oculus Quest.](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="ac8b5-157">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="ac8b5-158">Caso contrário, siga o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ac8b5-158">Otherwise follow the following:</span></span>
        - <span data-ttu-id="ac8b5-159">Selecione o objeto de jogo MixedRealityToolkit na hierarquia e selecione Copiar e **Personalizar** para clonar o perfil de realidade misturada padrão.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-159">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Clonar Perfil](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="ac8b5-161">Selecione o **Perfil de Configuração** de Entrada.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-161">Select the **Input** Configuration Profile.</span></span>

        ![Perfil de configuração de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="ac8b5-163">Selecione **Clonar** no perfil do sistema de entrada para habilitar a modificação.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-163">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Clonar perfil do sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="ac8b5-165">Abra a **seção Provedores de** Dados de **Entrada, selecione Adicionar Provedor de Dados** na parte superior e o novo provedor de dados será adicionado ao final da lista.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-165">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="ac8b5-166">Abra o novo provedor de dados e de definir **o Tipo** como **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager.**</span><span class="sxs-lookup"><span data-stu-id="ac8b5-166">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus Add XRSDK Provedor de Dados](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. <span data-ttu-id="ac8b5-168">O SDK do Oculus XR Provedor de Dados inclui um Pré-fab de Equipamento de Câmera OVR que configura automaticamente o projeto com um Equipamento de Câmera OVR e Mãos OVR para rotear corretamente a entrada.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-168">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="ac8b5-169">Adicionar manualmente um Equipamento de Câmera OVR à cena exigirá a configuração manual de configurações e de entrada.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-169">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="ac8b5-170">Criar e implantar seu projeto no Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="ac8b5-170">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="ac8b5-171">Conecte seu Oculus Quest por meio de um cabo USB 3.0 -> USB C</span><span class="sxs-lookup"><span data-stu-id="ac8b5-171">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="ac8b5-172">Navegue **até Configurações de build > arquivo**</span><span class="sxs-lookup"><span data-stu-id="ac8b5-172">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="ac8b5-173">Alterar a implantação para **Android**</span><span class="sxs-lookup"><span data-stu-id="ac8b5-173">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="ac8b5-174">Verifique se o Oculus Quest está selecionado como o dispositivo de executar aplicável</span><span class="sxs-lookup"><span data-stu-id="ac8b5-174">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Executar dispositivo Oculus](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="ac8b5-176">Selecione Build e Executar</span><span class="sxs-lookup"><span data-stu-id="ac8b5-176">Select Build and Run</span></span>
    - <span data-ttu-id="ac8b5-177">Você provavelmente encontrará o seguinte conjunto de erros de build ao selecionar *Criar e Executar* na primeira vez.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-177">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="ac8b5-178">Você deve ser capaz de implantar com êxito ao selecionar *Build e Executar* novamente.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-178">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Erros de build esperados do Oculus](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="ac8b5-180">Aceite o _prompt Permitir Depuração USB_ de dentro da busca</span><span class="sxs-lookup"><span data-stu-id="ac8b5-180">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="ac8b5-181">Veja sua cena dentro do Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="ac8b5-181">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="ac8b5-182">Removendo a integração do Oculus do projeto</span><span class="sxs-lookup"><span data-stu-id="ac8b5-182">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="ac8b5-183">Navegue até o Kit de Ferramentas de Realidade Misturada > Oculus > Módulos separados do Oculus Integration Unity  ![ Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="ac8b5-183">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="ac8b5-184">Permitir que o Unity seja atualizado como referências no Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef e outros arquivos serão modificados nesta etapa</span><span class="sxs-lookup"><span data-stu-id="ac8b5-184">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="ac8b5-185">Fechar Unity</span><span class="sxs-lookup"><span data-stu-id="ac8b5-185">Close Unity</span></span>
1. <span data-ttu-id="ac8b5-186">Feche Visual Studio, se estiver aberto</span><span class="sxs-lookup"><span data-stu-id="ac8b5-186">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="ac8b5-187">Abra Explorador de Arquivos e navegue até a raiz do projeto unity do MRTK</span><span class="sxs-lookup"><span data-stu-id="ac8b5-187">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="ac8b5-188">Excluir o diretório UnityProjectName/Library</span><span class="sxs-lookup"><span data-stu-id="ac8b5-188">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="ac8b5-189">Excluir o diretório UnityProjectName/Assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="ac8b5-189">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="ac8b5-190">Excluir o arquivo UnityProjectName/Assets/Oculus.meta</span><span class="sxs-lookup"><span data-stu-id="ac8b5-190">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="ac8b5-191">Reabrir o Unity</span><span class="sxs-lookup"><span data-stu-id="ac8b5-191">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="ac8b5-192">Erros comuns</span><span class="sxs-lookup"><span data-stu-id="ac8b5-192">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="ac8b5-193">Busca não reconhecida pelo Unity</span><span class="sxs-lookup"><span data-stu-id="ac8b5-193">Quest not recognized by Unity</span></span>

<span data-ttu-id="ac8b5-194">Certifique-se de que os caminhos do Android estão configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="ac8b5-194">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="ac8b5-195">Se você continuar encontrando problemas, siga este [guia](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="ac8b5-195">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="ac8b5-196">**Editar > preferências > ferramentas externas > Android**</span><span class="sxs-lookup"><span data-stu-id="ac8b5-196">**Edit > Preferences > External Tools > Android**</span></span>

![Configuração das Ferramentas do Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
