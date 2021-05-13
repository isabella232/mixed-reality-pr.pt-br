---
title: GettingStartedWithMRTKAndXRSDK
description: Página de aterrissagem para MRTK com XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, XRSDK,
ms.openlocfilehash: fe50de31ae24b415738db64073822b2aff061636
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850422"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="c821f-104">Introdução ao SDK do MRTK e do XR</span><span class="sxs-lookup"><span data-stu-id="c821f-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="c821f-105">O XR SDK é o [novo pipeline XR do Unity no Unity 2019,3 e posterior](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="c821f-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="c821f-106">No Unity 2019, ele fornece uma alternativa ao pipeline XR existente.</span><span class="sxs-lookup"><span data-stu-id="c821f-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="c821f-107">No Unity 2020, ele se tornará o único pipeline XR no Unity.</span><span class="sxs-lookup"><span data-stu-id="c821f-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c821f-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c821f-108">Prerequisites</span></span>

<span data-ttu-id="c821f-109">Para começar a usar o kit de ferramentas de realidade misturada, siga [as etapas fornecidas](../install-the-tools.md#importing-the-mixed-reality-toolkit) para adicionar o MRTK a um projeto.</span><span class="sxs-lookup"><span data-stu-id="c821f-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="c821f-110">Configurando o Unity para o pipeline do SDK do XR</span><span class="sxs-lookup"><span data-stu-id="c821f-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="c821f-111">Atualmente, o pipeline do XR SDK dá suporte a três plataformas: Windows Mixed Reality, Oculus e OpenXR.</span><span class="sxs-lookup"><span data-stu-id="c821f-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="c821f-112">As seções a seguir abordarão as etapas necessárias para configurar o XR SDK para cada plataforma.</span><span class="sxs-lookup"><span data-stu-id="c821f-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="c821f-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c821f-113">Windows Mixed Reality</span></span>

<span data-ttu-id="c821f-114">Acesse o **Gerenciador de pacotes do Unity** e instale o pacote de plug-in do Windows XR, que adiciona suporte para a realidade mista do Windows no XR SDK.</span><span class="sxs-lookup"><span data-stu-id="c821f-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="c821f-115">Isso também obterá alguns pacotes de dependência.</span><span class="sxs-lookup"><span data-stu-id="c821f-115">This will pull down a few dependency packages as well.</span></span> 

1. <span data-ttu-id="c821f-116">Verifique se todos os itens a seguir foram instalados com êxito:</span><span class="sxs-lookup"><span data-stu-id="c821f-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="c821f-117">Gerenciamento de plugin XR</span><span class="sxs-lookup"><span data-stu-id="c821f-117">XR Plugin Management</span></span>
   * <span data-ttu-id="c821f-118">Plug-in do Windows XR</span><span class="sxs-lookup"><span data-stu-id="c821f-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="c821f-119">Auxiliares de entrada do XR Legacy</span><span class="sxs-lookup"><span data-stu-id="c821f-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="c821f-120">Acesse **Editar > Configurações do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="c821f-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="c821f-121">Clique na guia gerenciamento de plug-ins do XR na janela Configurações do projeto.</span><span class="sxs-lookup"><span data-stu-id="c821f-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="c821f-122">Vá para as configurações de Plataforma Universal do Windows e verifique se a realidade mista do Windows está marcada em provedores de plug-in.</span><span class="sxs-lookup"><span data-stu-id="c821f-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="c821f-123">Verifique se inicializar XR na inicialização está marcado.</span><span class="sxs-lookup"><span data-stu-id="c821f-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="c821f-124">(**_Necessário para a remoção do HoloLens no editor, caso contrário, opcional_**) Acesse as configurações autônomas e verifique se Windows Mixed Reality está marcada em Provedores de Plug-in.</span><span class="sxs-lookup"><span data-stu-id="c821f-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="c821f-125">Verifique também se Inicializar XR na inicialização está marcada.</span><span class="sxs-lookup"><span data-stu-id="c821f-125">Also ensure that Initialize XR on Startup is checked.</span></span>

![Gerenciamento de plug-in XR com a guia Autônoma selecionada](images/xr-management-img-02.png)

7. <span data-ttu-id="c821f-127">(**_Opcional_**) Clique na guia Windows Mixed Reality em Gerenciamento de Plug-in XR e crie um perfil de configurações personalizadas para alterar os padrões.</span><span class="sxs-lookup"><span data-stu-id="c821f-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="c821f-128">Se a lista de configurações já estiver lá, nenhum perfil precisará ser criado.</span><span class="sxs-lookup"><span data-stu-id="c821f-128">If the list of settings are already there, no profile needs to be created.</span></span>

![Gerenciamento de plug-in XR com a guia Windows selecionada](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="c821f-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="c821f-130">Oculus</span></span>

1. <span data-ttu-id="c821f-131">Siga o [guia Como configurar o Oculus Guide no MRTK usando o pipeline do SDK do XR](../supported-devices/oculus-quest-mrtk.md) até o final.</span><span class="sxs-lookup"><span data-stu-id="c821f-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="c821f-132">O guia descreve as etapas necessárias para configurar o Unity e o MRTK para usar o pipeline do SDK do XR para o Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="c821f-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="c821f-133">OpenXR (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="c821f-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c821f-134">O OpenXR no Unity só tem suporte no Unity 2020.2 e superior.</span><span class="sxs-lookup"><span data-stu-id="c821f-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="c821f-135">Atualmente, ele também dá suporte apenas a builds x64 e ARM64.</span><span class="sxs-lookup"><span data-stu-id="c821f-135">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="c821f-136">Siga o guia Usando o plug-in [OpenXR](/windows/mixed-reality/develop/unity/openxr-getting-started) de Realidade Misturada para Unity, incluindo as etapas para configurar o Gerenciamento e Otimização de Plug-in XR para instalar o plug-in OpenXR em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c821f-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="c821f-137">Verifique se o seguinte foi instalado com êxito:</span><span class="sxs-lookup"><span data-stu-id="c821f-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="c821f-138">Gerenciamento de plug-in XR</span><span class="sxs-lookup"><span data-stu-id="c821f-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="c821f-139">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="c821f-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="c821f-140">Plug-in OpenXR de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="c821f-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="c821f-141">Vá para Editar > configurações do projeto.</span><span class="sxs-lookup"><span data-stu-id="c821f-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="c821f-142">Clique na guia Gerenciamento de Plug-in XR na janela Configurações do Projeto.</span><span class="sxs-lookup"><span data-stu-id="c821f-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="c821f-143">Verifique se Inicializar XR na Inicialização está marcada.</span><span class="sxs-lookup"><span data-stu-id="c821f-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="c821f-144">(**_Opcional_**) Se estiver direcionando para o HoloLens 2, verifique se você está na plataforma UWP e selecione conjunto de recursos do Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="c821f-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![Gerenciamento de plugin aberto XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="c821f-146">Se você tiver um projeto pré-existente que esteja usando MRTK do UPM, verifique se a linha a seguir está no arquivo **link.xml** localizado na pasta MixedRealityToolkit. Generated.</span><span class="sxs-lookup"><span data-stu-id="c821f-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="c821f-147">Para a versão inicial do MRTK e do OpenXR, somente as mãos do HoloLens 2 e os controladores de movimento de realidade do Windows Mixed Realm têm suporte nativo.</span><span class="sxs-lookup"><span data-stu-id="c821f-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="c821f-148">O suporte para hardware adicional será adicionado em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="c821f-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="c821f-149">Configurando o MRTK para o pipeline do SDK do XR</span><span class="sxs-lookup"><span data-stu-id="c821f-149">Configuring MRTK for the XR SDK pipeline</span></span>

<span data-ttu-id="c821f-150">Se estiver usando OpenXR, escolha "DefaultOpenXRConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.</span><span class="sxs-lookup"><span data-stu-id="c821f-150">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="c821f-151">Se estiver usando outros tempos de execução do XR na configuração de gerenciamento de plug-in do XR, como o Windows Mixed Reality ou oculus, escolha "DefaultXRSDKConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.</span><span class="sxs-lookup"><span data-stu-id="c821f-151">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="c821f-152">Esses perfis são configurados com os sistemas e provedores corretos, quando necessário.</span><span class="sxs-lookup"><span data-stu-id="c821f-152">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="c821f-153">Consulte [os documentos de perfis](../features/profiles/profiles.md#xr-sdk) para obter mais informações sobre o suporte a perfis e amostras com o XR SDK.</span><span class="sxs-lookup"><span data-stu-id="c821f-153">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="c821f-154">Para migrar um perfil existente para o XR SDK, os seguintes serviços e provedores de dados devem ser atualizados:</span><span class="sxs-lookup"><span data-stu-id="c821f-154">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

### <a name="camera"></a><span data-ttu-id="c821f-155">Câmera</span><span class="sxs-lookup"><span data-stu-id="c821f-155">Camera</span></span>

<span data-ttu-id="c821f-156">De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="c821f-156">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Configurações de câmera herdadas](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="c821f-158">como</span><span class="sxs-lookup"><span data-stu-id="c821f-158">to</span></span>

| <span data-ttu-id="c821f-159">OpenXR</span><span class="sxs-lookup"><span data-stu-id="c821f-159">OpenXR</span></span> | <span data-ttu-id="c821f-160">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c821f-160">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="c821f-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**e**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="c821f-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![Configurações da câmera do XR SDK](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="c821f-163">Entrada</span><span class="sxs-lookup"><span data-stu-id="c821f-163">Input</span></span>

<span data-ttu-id="c821f-164">De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="c821f-164">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Configurações de entrada herdadas](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="c821f-166">como</span><span class="sxs-lookup"><span data-stu-id="c821f-166">to</span></span>

| <span data-ttu-id="c821f-167">OpenXR</span><span class="sxs-lookup"><span data-stu-id="c821f-167">OpenXR</span></span> | <span data-ttu-id="c821f-168">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c821f-168">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="c821f-169">__OpenXR__:</span><span class="sxs-lookup"><span data-stu-id="c821f-169">__OpenXR__:</span></span>

![Configurações de entrada do OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="c821f-171">__Realidade mista do Windows__:</span><span class="sxs-lookup"><span data-stu-id="c821f-171">__Windows Mixed Reality__:</span></span>

![Configurações de entrada do SDK do XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="c821f-173">Limite</span><span class="sxs-lookup"><span data-stu-id="c821f-173">Boundary</span></span>

<span data-ttu-id="c821f-174">De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="c821f-174">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Configurações de limite herdou](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="c821f-176">como</span><span class="sxs-lookup"><span data-stu-id="c821f-176">to</span></span>

| <span data-ttu-id="c821f-177">OpenXR</span><span class="sxs-lookup"><span data-stu-id="c821f-177">OpenXR</span></span> | <span data-ttu-id="c821f-178">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c821f-178">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Configurações de limite do SDK do XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="c821f-180">Reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="c821f-180">Spatial awareness</span></span>

<span data-ttu-id="c821f-181">De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="c821f-181">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Configurações de reconhecimento espacial herddas](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="c821f-183">como</span><span class="sxs-lookup"><span data-stu-id="c821f-183">to</span></span>

| <span data-ttu-id="c821f-184">OpenXR</span><span class="sxs-lookup"><span data-stu-id="c821f-184">OpenXR</span></span> | <span data-ttu-id="c821f-185">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c821f-185">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="c821f-186">Em Andamento</span><span class="sxs-lookup"><span data-stu-id="c821f-186">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Configurações de reconhecimento espacial do SDK do XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="c821f-188">Mapeamentos de controlador</span><span class="sxs-lookup"><span data-stu-id="c821f-188">Controller mappings</span></span>

<span data-ttu-id="c821f-189">Se estiver usando perfis de mapeamento de controlador personalizado, abra um deles e execute o item de menu Utilitários do Kit de Ferramentas de Realidade Misturada -> -> Atualizar -> Perfis de Mapeamento do Controlador para garantir que os novos tipos de controlador do SDK do XR sejam definidos.</span><span class="sxs-lookup"><span data-stu-id="c821f-189">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="c821f-190">Confira também</span><span class="sxs-lookup"><span data-stu-id="c821f-190">See also</span></span>

* [<span data-ttu-id="c821f-191">Começar a trabalhar com o desenvolvimento de RA no Unity</span><span class="sxs-lookup"><span data-stu-id="c821f-191">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="c821f-192">Começar a trabalhar com o desenvolvimento de VR no Unity</span><span class="sxs-lookup"><span data-stu-id="c821f-192">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)