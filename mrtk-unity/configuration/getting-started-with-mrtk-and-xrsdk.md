---
title: Introdução ao SDK do MRTK e do XR
description: Página de aterrissagem do MRTK com o XR SDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, XRSDK, XR SDK
ms.openlocfilehash: bc2924f8e080b0c202f7c3e394a5382cf306431c
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603687"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="44371-104">Introdução ao SDK do MRTK e do XR</span><span class="sxs-lookup"><span data-stu-id="44371-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="44371-105">O XR SDK é o [novo pipeline XR do Unity no Unity 2019,3 e posterior](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="44371-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="44371-106">No Unity 2019, ele fornece uma alternativa ao pipeline XR existente.</span><span class="sxs-lookup"><span data-stu-id="44371-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="44371-107">No Unity 2020, é o único pipeline XR no Unity.</span><span class="sxs-lookup"><span data-stu-id="44371-107">In Unity 2020, it is the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="44371-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="44371-108">Prerequisites</span></span>

<span data-ttu-id="44371-109">para começar com a realidade misturada Toolkit, siga [as etapas fornecidas](../install-the-tools.md#importing-the-mixed-reality-toolkit) para adicionar o MRTK a um projeto.</span><span class="sxs-lookup"><span data-stu-id="44371-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="44371-110">Configurando o Unity para o pipeline do SDK do XR</span><span class="sxs-lookup"><span data-stu-id="44371-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="44371-111">o pipeline do XR SDK atualmente dá suporte a três plataformas: Windows Mixed Reality, Oculus e OpenXR.</span><span class="sxs-lookup"><span data-stu-id="44371-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="44371-112">As seções a seguir abordarão as etapas necessárias para configurar o XR SDK para cada plataforma.</span><span class="sxs-lookup"><span data-stu-id="44371-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="44371-113">Realidade Misturada do Windows</span><span class="sxs-lookup"><span data-stu-id="44371-113">Windows Mixed Reality</span></span>

<span data-ttu-id="44371-114">acesse o **Gerenciador de Pacotes do Unity** e instale o pacote de plug-in Windows xr, que adiciona suporte para Windows Mixed Reality no XR SDK.</span><span class="sxs-lookup"><span data-stu-id="44371-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="44371-115">Isso também obterá alguns pacotes de dependência.</span><span class="sxs-lookup"><span data-stu-id="44371-115">This will pull down a few dependency packages as well.</span></span>

1. <span data-ttu-id="44371-116">Verifique se todos os itens a seguir foram instalados com êxito:</span><span class="sxs-lookup"><span data-stu-id="44371-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="44371-117">Gerenciamento de plugin XR</span><span class="sxs-lookup"><span data-stu-id="44371-117">XR Plugin Management</span></span>
   * <span data-ttu-id="44371-118">Windows Plug-in XR</span><span class="sxs-lookup"><span data-stu-id="44371-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="44371-119">Auxiliares de entrada do XR Legacy</span><span class="sxs-lookup"><span data-stu-id="44371-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="44371-120">Acesse **Editar > Configurações do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="44371-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="44371-121">clique na guia gerenciamento de Plug-ins do XR na janela Project Configurações.</span><span class="sxs-lookup"><span data-stu-id="44371-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="44371-122">vá para as configurações de Plataforma Universal do Windows e verifique se Windows Mixed Reality está marcado em provedores de Plug-in.</span><span class="sxs-lookup"><span data-stu-id="44371-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="44371-123">Verifique se inicializar XR na inicialização está marcado.</span><span class="sxs-lookup"><span data-stu-id="44371-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="44371-124">(**_necessário para comunicação remota HoloLens no editor, caso contrário, opcional_**) vá para as configurações autônomas e verifique se Windows Mixed Reality está marcado em provedores de Plug-in.</span><span class="sxs-lookup"><span data-stu-id="44371-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="44371-125">Verifique também se inicializar XR na inicialização está marcado.</span><span class="sxs-lookup"><span data-stu-id="44371-125">Also ensure that Initialize XR on Startup is checked.</span></span>

    ![Gerenciamento de plugin XR com guia autônoma selecionada](images/xr-management-img-02.png)

7. <span data-ttu-id="44371-127">(**_Opcional_**) clique na guia Windows Mixed Reality em gerenciamento de Plug-in de XR e crie um perfil de configurações personalizadas para alterar os padrões.</span><span class="sxs-lookup"><span data-stu-id="44371-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="44371-128">Se a lista de configurações já estiver lá, nenhum perfil precisará ser criado.</span><span class="sxs-lookup"><span data-stu-id="44371-128">If the list of settings are already there, no profile needs to be created.</span></span>

    ![gerenciamento de Plugin XR com guia Windows selecionada](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="44371-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="44371-130">Oculus</span></span>

1. <span data-ttu-id="44371-131">Siga a guia [como configurar o Oculus Quest no MRTK usando o pipeline do XR SDK](../supported-devices/oculus-quest-mrtk.md) para o final.</span><span class="sxs-lookup"><span data-stu-id="44371-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="44371-132">O guia descreve as etapas necessárias para configurar o Unity e o MRTK para usar o pipeline do SDK do XR para o Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="44371-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr"></a><span data-ttu-id="44371-133">OpenXR</span><span class="sxs-lookup"><span data-stu-id="44371-133">OpenXR</span></span>

> [!IMPORTANT]
> <span data-ttu-id="44371-134">O OpenXR no Unity só tem suporte no Unity 2020,2 e superior.</span><span class="sxs-lookup"><span data-stu-id="44371-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
> <span data-ttu-id="44371-135">Ele também dá suporte apenas a compilações de x64, ARM e ARM64.</span><span class="sxs-lookup"><span data-stu-id="44371-135">It also only supports x64, ARM, and ARM64 builds.</span></span>

1. <span data-ttu-id="44371-136">Siga o guia [usando o plug-in Mixed Reality OpenXR plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) , incluindo as etapas para configurar a otimização e o gerenciamento de plug-in do XR para instalar o plug-in do OpenXR em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="44371-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="44371-137">Verifique se os itens a seguir foram instalados com êxito:</span><span class="sxs-lookup"><span data-stu-id="44371-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="44371-138">Gerenciamento de plugin XR</span><span class="sxs-lookup"><span data-stu-id="44371-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="44371-139">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="44371-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="44371-140">Plug-in OpenXR de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="44371-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="44371-141">vá para editar > Project Configurações.</span><span class="sxs-lookup"><span data-stu-id="44371-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="44371-142">clique na guia gerenciamento de Plug-ins do XR na janela Project Configurações.</span><span class="sxs-lookup"><span data-stu-id="44371-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="44371-143">Verifique se inicializar XR na inicialização está marcado.</span><span class="sxs-lookup"><span data-stu-id="44371-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="44371-144">(**_Opcional_**) se estiver direcionando HoloLens 2, verifique se você está na plataforma UWP e selecione Microsoft HoloLens conjunto de recursos</span><span class="sxs-lookup"><span data-stu-id="44371-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![OpenXR de gerenciamento de plugin](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="44371-146">Se você tiver um projeto pré-existente que esteja usando MRTK do UPM, verifique se a linha a seguir está no arquivo **link.xml** localizado na pasta MixedRealityToolkit. Generated.</span><span class="sxs-lookup"><span data-stu-id="44371-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="44371-147">para a versão inicial do MRTK e do OpenXR, somente os HoloLens 2 hands e os controladores de movimento de Windows Mixed Reality são suportados nativamente.</span><span class="sxs-lookup"><span data-stu-id="44371-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="44371-148">O suporte para hardware adicional será adicionado em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="44371-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="44371-149">Configurando o MRTK para o pipeline do SDK do XR</span><span class="sxs-lookup"><span data-stu-id="44371-149">Configuring MRTK for the XR SDK pipeline</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="44371-150">Use qualquer um dos perfis de MRTK padrão, que são todos configurados nos pipelines XR do Unity.</span><span class="sxs-lookup"><span data-stu-id="44371-150">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="44371-151">Os "DefaultOpenXRConfigurationProfile" e "DefaultXRSDKConfigurationProfile" anteriores agora estão rotulados como obsoletos.</span><span class="sxs-lookup"><span data-stu-id="44371-151">The previous "DefaultOpenXRConfigurationProfile" and "DefaultXRSDKConfigurationProfile" are now labeled obsolete.</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="44371-152">Se estiver usando OpenXR, escolha "DefaultOpenXRConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.</span><span class="sxs-lookup"><span data-stu-id="44371-152">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="44371-153">se estiver usando outros tempos de execução do xr na configuração de gerenciamento de Plug-in do xr, como Windows Mixed Reality ou Oculus, escolha "DefaultXRSDKConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.</span><span class="sxs-lookup"><span data-stu-id="44371-153">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="44371-154">Esses perfis são configurados com os sistemas e provedores corretos, quando necessário.</span><span class="sxs-lookup"><span data-stu-id="44371-154">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="44371-155">Consulte [os documentos de perfis](../features/profiles/profiles.md#xr-sdk) para obter mais informações sobre o suporte a perfis e amostras com o XR SDK.</span><span class="sxs-lookup"><span data-stu-id="44371-155">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>
::: moniker-end

<span data-ttu-id="44371-156">Para migrar um perfil existente para o XR SDK, os serviços e provedores de dados a seguir devem ser atualizados.</span><span class="sxs-lookup"><span data-stu-id="44371-156">To migrate an existing profile to XR SDK, the following services and data providers should be updated.</span></span>
::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="44371-157">Você poderá ver os novos provedores de dados na guia do SDK do XR no Unity 2019 ou na exibição principal/somente no Unity 2020 +, em que o XR herdado não existe.</span><span class="sxs-lookup"><span data-stu-id="44371-157">You will be able to see the new data providers under the XR SDK tab in Unity 2019, or in the main/only view in Unity 2020+, where legacy XR doesn't exist.</span></span>

![A guia do SDK do XR](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a><span data-ttu-id="44371-159">Câmera</span><span class="sxs-lookup"><span data-stu-id="44371-159">Camera</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="44371-160">Adicionar os seguintes provedores de dados</span><span class="sxs-lookup"><span data-stu-id="44371-160">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="44371-161">De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="44371-161">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Configurações de câmera herdadas](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="44371-163">como</span><span class="sxs-lookup"><span data-stu-id="44371-163">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="44371-164">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="44371-164">OpenXR Plugin</span></span> | <span data-ttu-id="44371-165">Windows Plug-in XR</span><span class="sxs-lookup"><span data-stu-id="44371-165">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="44371-166">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="44371-166">OpenXR Plugin</span></span> | <span data-ttu-id="44371-167">Windows Plug-in XR</span><span class="sxs-lookup"><span data-stu-id="44371-167">Windows XR Plugin</span></span> |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![Configurações da câmera do XR SDK](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="44371-169">Entrada</span><span class="sxs-lookup"><span data-stu-id="44371-169">Input</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="44371-170">Adicionar os seguintes provedores de dados</span><span class="sxs-lookup"><span data-stu-id="44371-170">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="44371-171">De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="44371-171">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Configurações de entrada herdadas](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="44371-173">como</span><span class="sxs-lookup"><span data-stu-id="44371-173">to</span></span>
::: moniker-end

| <span data-ttu-id="44371-174">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="44371-174">OpenXR Plugin</span></span> | <span data-ttu-id="44371-175">Windows Plug-in XR</span><span class="sxs-lookup"><span data-stu-id="44371-175">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="44371-176">__OpenXR__:</span><span class="sxs-lookup"><span data-stu-id="44371-176">__OpenXR__:</span></span>

![Configurações de entrada do OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="44371-178">__Windows Mixed Reality__:</span><span class="sxs-lookup"><span data-stu-id="44371-178">__Windows Mixed Reality__:</span></span>

![Configurações de entrada do SDK do XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="44371-180">Limite</span><span class="sxs-lookup"><span data-stu-id="44371-180">Boundary</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="44371-181">Adicionar os seguintes provedores de dados</span><span class="sxs-lookup"><span data-stu-id="44371-181">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="44371-182">De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="44371-182">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Configurações de limite herdadas](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="44371-184">como</span><span class="sxs-lookup"><span data-stu-id="44371-184">to</span></span>
::: moniker-end

| <span data-ttu-id="44371-185">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="44371-185">OpenXR Plugin</span></span> | <span data-ttu-id="44371-186">Windows Plug-in XR</span><span class="sxs-lookup"><span data-stu-id="44371-186">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Configurações de limite do SDK do XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="44371-188">Conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="44371-188">Spatial awareness</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="44371-189">Adicionar os seguintes provedores de dados</span><span class="sxs-lookup"><span data-stu-id="44371-189">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="44371-190">De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="44371-190">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Configurações de conscientização espacial herdadas](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="44371-192">como</span><span class="sxs-lookup"><span data-stu-id="44371-192">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="44371-193">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="44371-193">OpenXR Plugin</span></span> | <span data-ttu-id="44371-194">Windows Plug-in XR</span><span class="sxs-lookup"><span data-stu-id="44371-194">Windows XR Plugin</span></span> |
|---------------|-------------------|
| <span data-ttu-id="44371-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (para UWP)</span><span class="sxs-lookup"><span data-stu-id="44371-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (for UWP)</span></span> | <span data-ttu-id="44371-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (para UWP)</span><span class="sxs-lookup"><span data-stu-id="44371-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (for UWP)</span></span> |
| <span data-ttu-id="44371-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (para não UWP)</span><span class="sxs-lookup"><span data-stu-id="44371-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (for non-UWP)</span></span> | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="44371-198">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="44371-198">OpenXR Plugin</span></span> | <span data-ttu-id="44371-199">Windows Plug-in XR</span><span class="sxs-lookup"><span data-stu-id="44371-199">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![Configurações de reconhecimento espacial do SDK do XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="44371-201">Mapeamentos de controlador</span><span class="sxs-lookup"><span data-stu-id="44371-201">Controller mappings</span></span>

<span data-ttu-id="44371-202">Se estiver usando perfis de mapeamento de controlador personalizado, abra um deles e execute o item de menu Utilitários de Toolkit -> -> Update -> Controller Mapping Profiles para garantir que os novos tipos de controlador do SDK do XR sejam definidos.</span><span class="sxs-lookup"><span data-stu-id="44371-202">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="44371-203">Confira também</span><span class="sxs-lookup"><span data-stu-id="44371-203">See also</span></span>

* [<span data-ttu-id="44371-204">Começar a trabalhar com o desenvolvimento de RA no Unity</span><span class="sxs-lookup"><span data-stu-id="44371-204">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="44371-205">Começar a trabalhar com o desenvolvimento de VR no Unity</span><span class="sxs-lookup"><span data-stu-id="44371-205">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
