---
title: Registro de serviço de realidade misturada
description: Documentação em MixedRealityServiceRegistry e IMixedRealityServiceRegistrar
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 061e4233d61de817b1aaed7faaa6d461427d6f07
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176701"
---
# <a name="mixed-reality-service-registry"></a><span data-ttu-id="93a9f-104">Registro de serviço de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="93a9f-104">Mixed Reality service registry</span></span>

<span data-ttu-id="93a9f-105">a realidade misturada Toolkit tem dois componentes nomeados de forma semelhante que executam tarefas relacionadas: MixedRealityServiceRegistry e IMixedRealityServiceRegistrar.</span><span class="sxs-lookup"><span data-stu-id="93a9f-105">The Mixed Reality Toolkit has two very similarly named components that perform related tasks: MixedRealityServiceRegistry and IMixedRealityServiceRegistrar.</span></span>

## <a name="mixedrealityserviceregistry"></a><span data-ttu-id="93a9f-106">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="93a9f-106">MixedRealityServiceRegistry</span></span>

<span data-ttu-id="93a9f-107">O [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) é o componente que contém instâncias de cada serviço registrado (sistemas principais e serviços de extensão).</span><span class="sxs-lookup"><span data-stu-id="93a9f-107">The [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) is the component that contains instances of each registered service (core systems and extension services).</span></span>

> [!NOTE]
> <span data-ttu-id="93a9f-108">O MixedRealityServiceRegistry contém instâncias de objetos que implementam a interface [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) , incluindo [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span><span class="sxs-lookup"><span data-stu-id="93a9f-108">The MixedRealityServiceRegistry contains instances of objects that implement [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface, including [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span></span>
>
><span data-ttu-id="93a9f-109">Objetos que implementam o [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (uma subclasse de IMixedRealityService) não são explicitamente registrados no MixedRealityServiceRegistry.</span><span class="sxs-lookup"><span data-stu-id="93a9f-109">Objects implementing the [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (a subclass of IMixedRealityService) are explicitly not registered in the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="93a9f-110">Esses objetos são gerenciados pelos serviços individuais (por exemplo, reconhecimento espacial).</span><span class="sxs-lookup"><span data-stu-id="93a9f-110">These objects are managed by the individual services (ex: Spatial Awareness).</span></span>

<span data-ttu-id="93a9f-111">O MixedRealityServiceRegistry é implementado como uma classe C# estática e é o padrão recomendado a ser usado para adquirir instâncias de serviço no código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93a9f-111">The MixedRealityServiceRegistry is implemented as a static C# class and is the recommended pattern to use to acquire service instances in application code.</span></span>

<span data-ttu-id="93a9f-112">O trecho a seguir demonstra a aquisição de uma instância IMixedRealityInputSystem.</span><span class="sxs-lookup"><span data-stu-id="93a9f-112">The following snippet demonstrates acquiring an IMixedRealityInputSystem instance.</span></span>

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a><span data-ttu-id="93a9f-113">IMixedRealityServiceRegistrar</span><span class="sxs-lookup"><span data-stu-id="93a9f-113">IMixedRealityServiceRegistrar</span></span>

<span data-ttu-id="93a9f-114">O [IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) é a interface que define a funcionalidade implementada por componentes que gerenciam o registro de um ou mais serviços.</span><span class="sxs-lookup"><span data-stu-id="93a9f-114">The [IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) is the interface that defines the functionality implemented by components that manage the registration of one or more services.</span></span> <span data-ttu-id="93a9f-115">Os componentes que implementam IMixedRealityServiceRegistrar são responsáveis por adicionar e remover os dados dentro do MixedRealityServiceRegistry.</span><span class="sxs-lookup"><span data-stu-id="93a9f-115">Components that implement IMixedRealityServiceRegistrar are responsible for adding and removing the data within the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="93a9f-116">O objeto [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) é um desses componentes.</span><span class="sxs-lookup"><span data-stu-id="93a9f-116">The [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object is one such component.</span></span>

<span data-ttu-id="93a9f-117">Outros registradores podem ser encontrados na pasta MRTK/SDK/experimental/Features.</span><span class="sxs-lookup"><span data-stu-id="93a9f-117">Other registrars can be found in the MRTK/SDK/Experimental/Features folder.</span></span> <span data-ttu-id="93a9f-118">Esses componentes podem ser usados para adicionar suporte a um único serviço (por exemplo, reconhecimento espacial) a um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93a9f-118">These components can be used to add single service (ex: Spatial Awareness) support to an application.</span></span> <span data-ttu-id="93a9f-119">Esses gerenciadores de serviços únicos estão listados abaixo.</span><span class="sxs-lookup"><span data-stu-id="93a9f-119">These single service managers are listed below.</span></span>

- [<span data-ttu-id="93a9f-120">BoundarySystemManager</span><span class="sxs-lookup"><span data-stu-id="93a9f-120">BoundarySystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [<span data-ttu-id="93a9f-121">CameraSystemManager</span><span class="sxs-lookup"><span data-stu-id="93a9f-121">CameraSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [<span data-ttu-id="93a9f-122">DiagnosticsSystemManager</span><span class="sxs-lookup"><span data-stu-id="93a9f-122">DiagnosticsSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [<span data-ttu-id="93a9f-123">InputSystemManager</span><span class="sxs-lookup"><span data-stu-id="93a9f-123">InputSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [<span data-ttu-id="93a9f-124">SpatialAwarenessSystemManager</span><span class="sxs-lookup"><span data-stu-id="93a9f-124">SpatialAwarenessSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [<span data-ttu-id="93a9f-125">TeleportSystemManager</span><span class="sxs-lookup"><span data-stu-id="93a9f-125">TeleportSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

<span data-ttu-id="93a9f-126">Cada um dos componentes acima, com exceção do InputSystemManager, é responsável por gerenciar o registro e o status de um único tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="93a9f-126">Each of the above components, with the exception of the InputSystemManager, are responsible for managing the registration and status of a single service type.</span></span> <span data-ttu-id="93a9f-127">O InputSystem requer alguns serviços de suporte adicionais (ex: Focusprovider) que também são gerenciados pelo InputSystemManager.</span><span class="sxs-lookup"><span data-stu-id="93a9f-127">The InputSystem requires some additional support services (ex: FocusProvider) that are also managed by the InputSystemManager.</span></span>

<span data-ttu-id="93a9f-128">Em geral, os métodos definidos por IMixedRealityServiceRegistrar são chamados internamente pelos componentes de gerenciamento de serviços ou chamados por serviços que exigem componentes de serviço adicionais para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="93a9f-128">In general, the methods defined by IMixedRealityServiceRegistrar are called internally by service management components or called by services that require additional service components to function correctly.</span></span> <span data-ttu-id="93a9f-129">O código do aplicativo deve, em geral, não chamar esses métodos, pois isso pode fazer com que o aplicativo se comporte de modo não previsível (por exemplo: uma instância de serviço em cache pode se tornar inválida).</span><span class="sxs-lookup"><span data-stu-id="93a9f-129">Application code should, generally, not call these methods as doing so may cause the application to behave unpredictably (ex: a cached service instance may become invalid).</span></span>

## <a name="see-also"></a><span data-ttu-id="93a9f-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="93a9f-130">See also</span></span>

- [<span data-ttu-id="93a9f-131">Documentação da API do IMixedRealityServiceRegistrar</span><span class="sxs-lookup"><span data-stu-id="93a9f-131">IMixedRealityServiceRegistrar API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [<span data-ttu-id="93a9f-132">Documentação da API do MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="93a9f-132">MixedRealityServiceRegistry API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
