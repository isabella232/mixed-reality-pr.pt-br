---
title: Ponto de Partida com MRTK e XRSDK
description: Página de aterrissagem do MRTK com XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, XRSDK,
ms.openlocfilehash: ef6d8c9205a9d801e8cb0ec2690d77b74c72b5fb
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143525"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="baa3b-104">Como começar a trabalhar com o MRTK e o SDK do XR</span><span class="sxs-lookup"><span data-stu-id="baa3b-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="baa3b-105">O SDK do XR é o novo pipeline XR do [Unity no Unity 2019.3 e além de](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="baa3b-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="baa3b-106">No Unity 2019, ele fornece uma alternativa ao pipeline XR existente.</span><span class="sxs-lookup"><span data-stu-id="baa3b-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="baa3b-107">No Unity 2020, ele se tornará o único pipeline XR no Unity.</span><span class="sxs-lookup"><span data-stu-id="baa3b-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="baa3b-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="baa3b-108">Prerequisites</span></span>

<span data-ttu-id="baa3b-109">Para começar a trabalhar com o Kit de Ferramentas de Realidade Misturada, siga [as etapas fornecidas](../install-the-tools.md#importing-the-mixed-reality-toolkit) para adicionar o MRTK a um projeto.</span><span class="sxs-lookup"><span data-stu-id="baa3b-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="baa3b-110">Configurando o Unity para o pipeline do SDK do XR</span><span class="sxs-lookup"><span data-stu-id="baa3b-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="baa3b-111">Atualmente, o pipeline do SDK do XR dá suporte a três plataformas: Windows Mixed Reality, Oculus e OpenXR.</span><span class="sxs-lookup"><span data-stu-id="baa3b-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="baa3b-112">As seções a seguir abrangem as etapas necessárias para configurar o SDK do XR para cada plataforma.</span><span class="sxs-lookup"><span data-stu-id="baa3b-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="baa3b-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="baa3b-113">Windows Mixed Reality</span></span>

<span data-ttu-id="baa3b-114">Acesse o **pacote de Gerenciador de Pacotes** do Unity e instale o pacote do Plug-in do Windows XR, que adiciona suporte para Windows Mixed Reality no SDK do XR.</span><span class="sxs-lookup"><span data-stu-id="baa3b-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="baa3b-115">Isso também efetuará pull de alguns pacotes de dependência.</span><span class="sxs-lookup"><span data-stu-id="baa3b-115">This will pull down a few dependency packages as well.</span></span> 

1. <span data-ttu-id="baa3b-116">Certifique-se de que todos os seguintes foram instalados com êxito:</span><span class="sxs-lookup"><span data-stu-id="baa3b-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="baa3b-117">Gerenciamento de plug-in XR</span><span class="sxs-lookup"><span data-stu-id="baa3b-117">XR Plugin Management</span></span>
   * <span data-ttu-id="baa3b-118">Plug-in do Windows XR</span><span class="sxs-lookup"><span data-stu-id="baa3b-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="baa3b-119">Auxiliares de entrada herddos do XR</span><span class="sxs-lookup"><span data-stu-id="baa3b-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="baa3b-120">Acesse **Editar > Configurações do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="baa3b-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="baa3b-121">Clique na guia Gerenciamento de Plug-in XR na janela Configurações do Projeto.</span><span class="sxs-lookup"><span data-stu-id="baa3b-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="baa3b-122">Vá para as Plataforma Universal do Windows configurações e verifique se Windows Mixed Reality está marcada em Provedores de Plug-in.</span><span class="sxs-lookup"><span data-stu-id="baa3b-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="baa3b-123">Verifique se Inicializar XR na Inicialização está marcada.</span><span class="sxs-lookup"><span data-stu-id="baa3b-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="baa3b-124">(**_Necessário para comunicação remota do HoloLens no editor, caso contrário, opcional_**) Vá para as configurações autônomas e verifique se a realidade mista do Windows está marcada em provedores de plug-in.</span><span class="sxs-lookup"><span data-stu-id="baa3b-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="baa3b-125">Verifique também se inicializar XR na inicialização está marcado.</span><span class="sxs-lookup"><span data-stu-id="baa3b-125">Also ensure that Initialize XR on Startup is checked.</span></span>

![Gerenciamento de plugin XR com guia autônoma selecionada](images/xr-management-img-02.png)

7. <span data-ttu-id="baa3b-127">(**_Opcional_**) Clique na guia realidade misturada do Windows em gerenciamento de plug-in do XR e crie um perfil de configurações personalizadas para alterar os padrões.</span><span class="sxs-lookup"><span data-stu-id="baa3b-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="baa3b-128">Se a lista de configurações já estiver lá, nenhum perfil precisará ser criado.</span><span class="sxs-lookup"><span data-stu-id="baa3b-128">If the list of settings are already there, no profile needs to be created.</span></span>

![Gerenciamento de plugin XR com a guia Windows selecionada](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="baa3b-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="baa3b-130">Oculus</span></span>

1. <span data-ttu-id="baa3b-131">Siga a guia [como configurar o Oculus Quest no MRTK usando o pipeline do XR SDK](../supported-devices/oculus-quest-mrtk.md) para o final.</span><span class="sxs-lookup"><span data-stu-id="baa3b-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="baa3b-132">O guia descreve as etapas necessárias para configurar o Unity e o MRTK para usar o pipeline do SDK do XR para o Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="baa3b-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="baa3b-133">OpenXR (visualização)</span><span class="sxs-lookup"><span data-stu-id="baa3b-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="baa3b-134">O OpenXR no Unity só tem suporte no Unity 2020,2 e superior.</span><span class="sxs-lookup"><span data-stu-id="baa3b-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="baa3b-135">Atualmente, ele também dá suporte apenas a compilações de x64 e ARM64.</span><span class="sxs-lookup"><span data-stu-id="baa3b-135">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="baa3b-136">Siga o guia [usando o plug-in Mixed Reality OpenXR plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) , incluindo as etapas para configurar a otimização e o gerenciamento de plug-in do XR para instalar o plug-in do OpenXR em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="baa3b-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="baa3b-137">Verifique se os itens a seguir foram instalados com êxito:</span><span class="sxs-lookup"><span data-stu-id="baa3b-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="baa3b-138">Gerenciamento de plugin XR</span><span class="sxs-lookup"><span data-stu-id="baa3b-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="baa3b-139">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="baa3b-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="baa3b-140">Plug-in OpenXR de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="baa3b-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="baa3b-141">Vá para editar configurações de projeto >.</span><span class="sxs-lookup"><span data-stu-id="baa3b-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="baa3b-142">Clique na guia gerenciamento de plug-ins do XR na janela Configurações do projeto.</span><span class="sxs-lookup"><span data-stu-id="baa3b-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="baa3b-143">Verifique se inicializar XR na inicialização está marcado.</span><span class="sxs-lookup"><span data-stu-id="baa3b-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="baa3b-144">(**_Opcional_**) Se estiver direcionando o HoloLens 2, certifique-se de que você está na plataforma UWP e selecione Microsoft HoloLens conjunto de recursos</span><span class="sxs-lookup"><span data-stu-id="baa3b-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![Gerenciamento de plug-ins Open XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="baa3b-146">Se você tiver um projeto pré-existente que está usando o MRTK do UPM, certifique-se de que a linha a seguir está no arquivo **link.xml** localizado na pasta MixedRealityToolkit.Generated.</span><span class="sxs-lookup"><span data-stu-id="baa3b-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="baa3b-147">Para a versão inicial do MRTK e do OpenXR, somente as mãos articuladas do HoloLens 2 e Windows Mixed Reality de movimento têm suporte nativo.</span><span class="sxs-lookup"><span data-stu-id="baa3b-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="baa3b-148">O suporte para hardware adicional será adicionado em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="baa3b-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="baa3b-149">Configurando o MRTK para o pipeline do SDK do XR</span><span class="sxs-lookup"><span data-stu-id="baa3b-149">Configuring MRTK for the XR SDK pipeline</span></span>

<span data-ttu-id="baa3b-150">Se estiver usando o OpenXR, escolha "DefaultOpenXRConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.</span><span class="sxs-lookup"><span data-stu-id="baa3b-150">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="baa3b-151">Se estiver usando outros runtimes XR na configuração de Gerenciamento de Plug-in XR, como Windows Mixed Reality ou Oculus, escolha "DefaultXRSDKConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.</span><span class="sxs-lookup"><span data-stu-id="baa3b-151">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="baa3b-152">Esses perfis são definidos com os sistemas e provedores corretos, quando necessário.</span><span class="sxs-lookup"><span data-stu-id="baa3b-152">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="baa3b-153">Consulte [os documentos de perfis](../features/profiles/profiles.md#xr-sdk) para obter mais informações sobre o perfil e o suporte de exemplo com o SDK do XR.</span><span class="sxs-lookup"><span data-stu-id="baa3b-153">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="baa3b-154">Para migrar um perfil existente para o SDK do XR, os seguintes serviços e provedores de dados devem ser atualizados:</span><span class="sxs-lookup"><span data-stu-id="baa3b-154">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

### <a name="camera"></a><span data-ttu-id="baa3b-155">Câmera</span><span class="sxs-lookup"><span data-stu-id="baa3b-155">Camera</span></span>

<span data-ttu-id="baa3b-156">De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="baa3b-156">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Configurações de câmera herddas](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="baa3b-158">para</span><span class="sxs-lookup"><span data-stu-id="baa3b-158">to</span></span>

| <span data-ttu-id="baa3b-159">OpenXR</span><span class="sxs-lookup"><span data-stu-id="baa3b-159">OpenXR</span></span> | <span data-ttu-id="baa3b-160">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="baa3b-160">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="baa3b-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**e**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="baa3b-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![Configurações de câmera do SDK do XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="baa3b-163">Entrada</span><span class="sxs-lookup"><span data-stu-id="baa3b-163">Input</span></span>

<span data-ttu-id="baa3b-164">De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="baa3b-164">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Configurações de entrada herddas](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="baa3b-166">para</span><span class="sxs-lookup"><span data-stu-id="baa3b-166">to</span></span>

| <span data-ttu-id="baa3b-167">OpenXR</span><span class="sxs-lookup"><span data-stu-id="baa3b-167">OpenXR</span></span> | <span data-ttu-id="baa3b-168">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="baa3b-168">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="baa3b-169">__OpenXR:__</span><span class="sxs-lookup"><span data-stu-id="baa3b-169">__OpenXR__:</span></span>

![Configurações de entrada do OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="baa3b-171">__Windows Mixed Reality__:</span><span class="sxs-lookup"><span data-stu-id="baa3b-171">__Windows Mixed Reality__:</span></span>

![Configurações de entrada do SDK do XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="baa3b-173">Limite</span><span class="sxs-lookup"><span data-stu-id="baa3b-173">Boundary</span></span>

<span data-ttu-id="baa3b-174">De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="baa3b-174">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Configurações de limite herdadas](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="baa3b-176">para</span><span class="sxs-lookup"><span data-stu-id="baa3b-176">to</span></span>

| <span data-ttu-id="baa3b-177">OpenXR</span><span class="sxs-lookup"><span data-stu-id="baa3b-177">OpenXR</span></span> | <span data-ttu-id="baa3b-178">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="baa3b-178">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Configurações de limite do SDK do XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="baa3b-180">Conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="baa3b-180">Spatial awareness</span></span>

<span data-ttu-id="baa3b-181">De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="baa3b-181">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Configurações de conscientização espacial herdadas](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="baa3b-183">para</span><span class="sxs-lookup"><span data-stu-id="baa3b-183">to</span></span>

| <span data-ttu-id="baa3b-184">OpenXR</span><span class="sxs-lookup"><span data-stu-id="baa3b-184">OpenXR</span></span> | <span data-ttu-id="baa3b-185">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="baa3b-185">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="baa3b-186">Em Andamento</span><span class="sxs-lookup"><span data-stu-id="baa3b-186">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Configurações de reconhecimento espacial do SDK do XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="baa3b-188">Mapeamentos de controlador</span><span class="sxs-lookup"><span data-stu-id="baa3b-188">Controller mappings</span></span>

<span data-ttu-id="baa3b-189">Se você estiver usando perfis de mapeamento de controlador personalizado, abra um deles e execute o item de menu Mixed Reality Toolkit-> Utilities-> Update-> controlador de mapeamento de perfis para garantir que os novos tipos de controlador do SDK do XR sejam definidos.</span><span class="sxs-lookup"><span data-stu-id="baa3b-189">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="baa3b-190">Confira também</span><span class="sxs-lookup"><span data-stu-id="baa3b-190">See also</span></span>

* [<span data-ttu-id="baa3b-191">Introdução ao desenvolvimento do AR no Unity</span><span class="sxs-lookup"><span data-stu-id="baa3b-191">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="baa3b-192">Introdução ao desenvolvimento VR no Unity</span><span class="sxs-lookup"><span data-stu-id="baa3b-192">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)