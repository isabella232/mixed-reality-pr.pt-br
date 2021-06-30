---
title: Provedor de extensões do sistema
description: Extensões de MRTK e provedores de dados
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, extensões do sistema,
ms.openlocfilehash: 358294702971b7d9e8de1b842d3bc1844e5dc9bf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121464"
---
# <a name="systems-extension-services-and-data-providers"></a><span data-ttu-id="6068e-104">Sistemas, serviços de extensão e provedores de dados</span><span class="sxs-lookup"><span data-stu-id="6068e-104">Systems, extension services and data providers</span></span>

<span data-ttu-id="6068e-105">No kit de ferramentas de realidade misturada, muitos dos recursos são fornecidos na forma de serviços.</span><span class="sxs-lookup"><span data-stu-id="6068e-105">In the Mixed Reality Toolkit, many of the features are delivered in the form of services.</span></span> <span data-ttu-id="6068e-106">Os serviços são agrupados em três categorias principais: sistemas, serviços de extensão e provedores de dados.</span><span class="sxs-lookup"><span data-stu-id="6068e-106">Services are grouped into three primary categories: systems, extension services and data providers.</span></span>

## <a name="systems"></a><span data-ttu-id="6068e-107">Sistemas</span><span class="sxs-lookup"><span data-stu-id="6068e-107">Systems</span></span>

<span data-ttu-id="6068e-108">Os sistemas são serviços que fornecem a funcionalidade básica do kit de ferramentas de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="6068e-108">Systems are services that provide the core functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="6068e-109">Todos os sistemas são implementações da [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span><span class="sxs-lookup"><span data-stu-id="6068e-109">All systems are implementations of the [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span></span>

- [<span data-ttu-id="6068e-110">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="6068e-110">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="6068e-111">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="6068e-111">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md)
- [<span data-ttu-id="6068e-112">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="6068e-112">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md)
- [<span data-ttu-id="6068e-113">InputSystem</span><span class="sxs-lookup"><span data-stu-id="6068e-113">InputSystem</span></span>](../features/input/overview.md)
- [<span data-ttu-id="6068e-114">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="6068e-114">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md)
- [<span data-ttu-id="6068e-115">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="6068e-115">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="6068e-116">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="6068e-116">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md)

<span data-ttu-id="6068e-117">Cada um dos sistemas listados está na superfície do [perfil](../features/profiles/profiles.md)de configuração do componente MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="6068e-117">Each of the listed systems are surfaced in the MixedRealityToolkit component's configuration [profile](../features/profiles/profiles.md).</span></span>

## <a name="extensions"></a><span data-ttu-id="6068e-118">Extensões</span><span class="sxs-lookup"><span data-stu-id="6068e-118">Extensions</span></span>

<span data-ttu-id="6068e-119">Os serviços de extensão são componentes que estendem a funcionalidade do kit de ferramentas de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="6068e-119">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="6068e-120">Todos os serviços de extensão devem especificar que eles implementam a [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span><span class="sxs-lookup"><span data-stu-id="6068e-120">All extension services must specify that they implement the [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span></span>

<span data-ttu-id="6068e-121">Para obter informações sobre como criar serviços de extensão, consulte o artigo [serviços de extensão](../features/extensions/extension-services.md) .</span><span class="sxs-lookup"><span data-stu-id="6068e-121">For information on creating extension services, please reference the [Extension services](../features/extensions/extension-services.md) article.</span></span>

<span data-ttu-id="6068e-122">Para ser acessível ao MRTK, os serviços de extensão são registrados e configurados usando a seção de extensões do perfil de configuração do componente MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="6068e-122">To be accessible to the MRTK, extension services are registered and configured using the Extensions section of the MixedRealityToolkit component's configuration profile.</span></span>

![Configurando um serviço de extensão](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a><span data-ttu-id="6068e-124">Provedores de dados</span><span class="sxs-lookup"><span data-stu-id="6068e-124">Data providers</span></span>

<span data-ttu-id="6068e-125">Provedores de dados são componentes que, por seu nome, fornecem dados a um serviço de kit de ferramentas de realidade misto.</span><span class="sxs-lookup"><span data-stu-id="6068e-125">Data providers are components that, per their name, provide data to a Mixed Reality Toolkit service.</span></span> <span data-ttu-id="6068e-126">Todos os provedores de dados devem especificar que eles implementam a [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="6068e-126">All data providers must specify that they implement the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="6068e-127">Nem todos os serviços precisarão de provedores de dados.</span><span class="sxs-lookup"><span data-stu-id="6068e-127">Not all services will require data providers.</span></span> <span data-ttu-id="6068e-128">Dos sistemas mistos do kit de ferramentas da realidade, os sistemas de reconhecimento de entrada e espaciais são os únicos serviços para utilizar provedores de dados.</span><span class="sxs-lookup"><span data-stu-id="6068e-128">Of the Mixed Reality Toolkit's systems, the Input and Spatial Awareness systems are the only services to utilize data providers.</span></span>

<span data-ttu-id="6068e-129">Para ser acessível para o serviço MRTK específico, os provedores de dados são registrados no perfil de configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="6068e-129">To be accessible to the specific MRTK service, data providers are registered in the service's configuration profile.</span></span>

<span data-ttu-id="6068e-130">O código do aplicativo acessa provedores de dados por meio da [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span><span class="sxs-lookup"><span data-stu-id="6068e-130">Application code accesses data providers via the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span></span> <span data-ttu-id="6068e-131">Para simplificar o acesso, os provedores de dados também podem ser recuperados por meio da `CoreServices` classe auxiliar.</span><span class="sxs-lookup"><span data-stu-id="6068e-131">To simplify access, data providers can also be retrieved via the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> <span data-ttu-id="6068e-132">Embora `IMixedRealityDataProvider` herde de `IMixedRealityService` , os provedores de dados não são registrados com o `MixedRealityServiceRegistry` .</span><span class="sxs-lookup"><span data-stu-id="6068e-132">Although `IMixedRealityDataProvider` inherits from `IMixedRealityService`, data providers are not registered with the `MixedRealityServiceRegistry`.</span></span> <span data-ttu-id="6068e-133">Para acessar provedores de dados, o código do aplicativo deve consultar a instância de serviço para a qual eles foram registrados (por exemplo: sistema de entrada).</span><span class="sxs-lookup"><span data-stu-id="6068e-133">To access data providers, application code must query the service instance for which they were registered (ex: input system).</span></span>

### <a name="input"></a><span data-ttu-id="6068e-134">Entrada</span><span class="sxs-lookup"><span data-stu-id="6068e-134">Input</span></span>

<span data-ttu-id="6068e-135">O sistema de entrada MRTK utiliza apenas provedores de dados que implementam o [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="6068e-135">The MRTK input system utilizes only data providers that implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager).</span></span>

![Provedores de dados do sistema de entrada](../features/images/input/RegisteredServiceProviders.PNG)

<span data-ttu-id="6068e-137">O exemplo a seguir demonstra como acessar o provedor de simulação de entrada e alternar a propriedade SmoothEyeTracking.</span><span class="sxs-lookup"><span data-stu-id="6068e-137">The following example demonstrates accessing the input simulation provider and toggle the SmoothEyeTracking property.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess = CoreServices.InputSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IInputSimulationService inputSimulation =
        dataProviderAccess.GetDataProvider<IInputSimulationService>();

    if (inputSimulation != null)
    {
        inputSimulation.SmoothEyeTracking = !inputSimulation.SmoothEyeTracking;
    }
}
```

<span data-ttu-id="6068e-138">O acesso a um provedor de dados para o sistema de entrada principal também pode ser simplificado por meio do uso da `CoreServices` classe auxiliar.</span><span class="sxs-lookup"><span data-stu-id="6068e-138">Accessing a data provider for the core input system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="6068e-139">O sistema de entrada retorna somente provedores de dados com suporte para a plataforma na qual o aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="6068e-139">The input system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="6068e-140">Para obter informações sobre como gravar um provedor de dados para o sistema de entrada MRTK, consulte [criando um provedor de dados do sistema de entrada](../features/input/create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="6068e-140">For information on writing a data provider for the MRTK input system, please see [creating an input system data provider](../features/input/create-data-provider.md).</span></span>

### <a name="spatial-awareness"></a><span data-ttu-id="6068e-141">Conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="6068e-141">Spatial awareness</span></span>

<span data-ttu-id="6068e-142">O sistema de conscientização espacial MRTK utiliza apenas provedores de dados que implementam a [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span><span class="sxs-lookup"><span data-stu-id="6068e-142">The MRTK spatial awareness system utilizes only data providers that implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Provedores de dados do sistema de reconhecimento espacial](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

<span data-ttu-id="6068e-144">O exemplo a seguir demonstra como acessar os provedores de dados de malha espacial registrados e alterar a visibilidade das malhas.</span><span class="sxs-lookup"><span data-stu-id="6068e-144">The following example demonstrates accessing the registered spatial mesh data providers and changing the visibility of the meshes.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess =
    CoreServices.SpatialAwarenessSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IReadOnlyList<IMixedRealitySpatialAwarenessMeshObserver> observers =
        dataProviderAccess.GetDataProviders<IMixedRealitySpatialAwarenessMeshObserver>();

    foreach (IMixedRealitySpatialAwarenessMeshObserver observer in observers)
    {
        // Set the mesh to use the occlusion material
        observer.DisplayOption = SpatialMeshDisplayOptions.Occlusion;
    }
}
```

<span data-ttu-id="6068e-145">O acesso a um provedor de dados para o sistema de conscientização espacial principal também pode ser simplificado por meio do uso da `CoreServices` classe auxiliar.</span><span class="sxs-lookup"><span data-stu-id="6068e-145">Accessing a data provider for the core spatial awareness system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="6068e-146">O sistema de conscientização espacial retorna somente provedores de dados com suporte para a plataforma na qual o aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="6068e-146">The spatial awareness system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="6068e-147">Para obter informações sobre como escrever um provedor de dados para o sistema de conscientização espacial do MRTK, consulte [criando um provedor de dados do sistema de conscientização espacial](../features/spatial-awareness/create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="6068e-147">For information on writing a data provider for the MRTK spatial awareness system, please see [creating a spatial awareness system data provider](../features/spatial-awareness/create-data-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6068e-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="6068e-148">See also</span></span>

- [<span data-ttu-id="6068e-149">Serviços de extensão</span><span class="sxs-lookup"><span data-stu-id="6068e-149">Extension services</span></span>](../features/extensions/extension-services.md)
- [<span data-ttu-id="6068e-150">Criando um provedor de dados do sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="6068e-150">Creating an input system data provider</span></span>](../features/input/create-data-provider.md)
- [<span data-ttu-id="6068e-151">Criando um provedor de dados do sistema do sistema de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="6068e-151">Creating a spatial awareness system system data provider</span></span>](../features/spatial-awareness/create-data-provider.md)
- [<span data-ttu-id="6068e-152">Interface IMixedRealityService</span><span class="sxs-lookup"><span data-stu-id="6068e-152">IMixedRealityService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [<span data-ttu-id="6068e-153">Interface IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="6068e-153">IMixedRealityDataProvider interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="6068e-154">Interface IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="6068e-154">IMixedRealityExtensionService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
