---
title: Modularidade do MRTK
description: Descreve a componentização no MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 04b2e6155e591a918b95aed20961a0450afe5f43
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144423"
---
# <a name="mixed-reality-toolkit-componentization"></a><span data-ttu-id="1b19d-104">Componentização do Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="1b19d-104">Mixed Reality Toolkit componentization</span></span>

<span data-ttu-id="1b19d-105">Um dos novos recursos excelentes do Kit de Ferramentas de Realidade Misturada v2 é a melhoria da componentização.</span><span class="sxs-lookup"><span data-stu-id="1b19d-105">One of the great new features of Mixed Reality Toolkit v2 is improved componentization.</span></span> <span data-ttu-id="1b19d-106">Sempre que possível, os componentes individuais são isolados de todos, menos da camada principal da base.</span><span class="sxs-lookup"><span data-stu-id="1b19d-106">Wherever possible, individual components are isolated from all but the core layer of the foundation.</span></span>

## <a name="minimized-dependencies"></a><span data-ttu-id="1b19d-107">Dependências minimizadas</span><span class="sxs-lookup"><span data-stu-id="1b19d-107">Minimized dependencies</span></span>

<span data-ttu-id="1b19d-108">O MRTK v2 foi desenvolvido intencionalmente para ser modular e minimizar as dependências entre os serviços do sistema (por ex. reconhecimento espacial).</span><span class="sxs-lookup"><span data-stu-id="1b19d-108">MRTK v2 was intentionally developed to be modular and to minimize dependencies between system services (ex: spatial awareness).</span></span>

<span data-ttu-id="1b19d-109">Devido à natureza de alguns serviços do sistema (por ex. entrada e teletransportação), há um pequeno número de dependências.</span><span class="sxs-lookup"><span data-stu-id="1b19d-109">Due to the nature of some system services (ex: input and teleportation), a small number of dependencies exist.</span></span>

<span data-ttu-id="1b19d-110">Embora seja esperado que os serviços precisem de um ou mais componentes do provedor de dados, não há links diretos entre eles.</span><span class="sxs-lookup"><span data-stu-id="1b19d-110">While it is expected that services will need one or more data provider components, there are no direct links between them.</span></span> <span data-ttu-id="1b19d-111">O mesmo vale para recursos do SDK (por exemplo, Interface do Usuário componentes).</span><span class="sxs-lookup"><span data-stu-id="1b19d-111">The same is true for SDK features (ex: User Interface components).</span></span>

## <a name="component-communication"></a><span data-ttu-id="1b19d-112">Comunicação de componente</span><span class="sxs-lookup"><span data-stu-id="1b19d-112">Component communication</span></span>

<span data-ttu-id="1b19d-113">Para garantir que não haja links diretos entre componentes, o MRTK v2 utiliza interfaces para se comunicar entre serviços, provedores de dados e código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b19d-113">To ensure that there are no direct links between components, MRTK v2 utilizes interfaces to communicate between services, data providers and application code.</span></span> <span data-ttu-id="1b19d-114">Essas interfaces são definidas em e toda a comunicação é roteada por meio do componente principal do Kit de Ferramentas de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="1b19d-114">These interfaces are defined in and all communication is routed through the Mixed Reality Toolkit core component.</span></span>

![Usando o sistema de reconhecimento espacial por meio de interfaces](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a><span data-ttu-id="1b19d-116">Minimizando o espaço de importação do MRTK</span><span class="sxs-lookup"><span data-stu-id="1b19d-116">Minimizing MRTK import footprint</span></span>

<span data-ttu-id="1b19d-117">Neste momento, o MRTK é importado como um único pacote de base (ignorando por um momento a existência do pacote de exemplos, que é um pacote completamente opcional).</span><span class="sxs-lookup"><span data-stu-id="1b19d-117">At this moment, the MRTK is imported as a single foundation package (ignoring for a moment the existence of the examples package, which is a completely optional package).</span></span> <span data-ttu-id="1b19d-118">É possível tornar esse volume menor reduzindo manualmente os arquivos importados, embora esse seja um processo altamente manual que não tem um guia bem definido.</span><span class="sxs-lookup"><span data-stu-id="1b19d-118">It is possible to make this footprint smaller by manually cutting down on the files imported, though this is a highly manual process which doesn't have a well-defined guide.</span></span>

<span data-ttu-id="1b19d-119">É possível desmarcar itens arbitrários durante a importação do pacote Foundation.</span><span class="sxs-lookup"><span data-stu-id="1b19d-119">It is possible to uncheck arbitrary items during the import of the Foundation package.</span></span> <span data-ttu-id="1b19d-120">No entanto, não é recomendável fazer isso em um estágio inicial no desenvolvimento, pois ele pode quebrar a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="1b19d-120">However, it's not recommended to do this at an early stage in development as it might break functionality.</span></span> <span data-ttu-id="1b19d-121">Depois de descobrir o conjunto de recursos final de um aplicativo, a remoção de provedores e serviços não previstos pode ser feita nas seguintes pastas:</span><span class="sxs-lookup"><span data-stu-id="1b19d-121">After having figured out the final feature set of an app, pruning unneeded providers and services can be done on the following folders:</span></span>

- <span data-ttu-id="1b19d-122">MRTK/Serviços</span><span class="sxs-lookup"><span data-stu-id="1b19d-122">MRTK/Services</span></span>
- <span data-ttu-id="1b19d-123">MRTK/provedores</span><span class="sxs-lookup"><span data-stu-id="1b19d-123">MRTK/Providers</span></span>
- <span data-ttu-id="1b19d-124">MRTK/SDK/recursos</span><span class="sxs-lookup"><span data-stu-id="1b19d-124">MRTK/SDK/Features</span></span>

> [!NOTE]
> <span data-ttu-id="1b19d-125">O MRTK v2. x **_requer_** o conteúdo da pasta assets/MRTK/Core.</span><span class="sxs-lookup"><span data-stu-id="1b19d-125">MRTK v2.x **_requires_** the contents of the Assets/MRTK/Core folder.</span></span>

## <a name="upcoming-features"></a><span data-ttu-id="1b19d-126">Recursos futuros</span><span class="sxs-lookup"><span data-stu-id="1b19d-126">Upcoming features</span></span>

### <a name="application-architecture"></a><span data-ttu-id="1b19d-127">Arquitetura do aplicativo</span><span class="sxs-lookup"><span data-stu-id="1b19d-127">Application architecture</span></span>

<span data-ttu-id="1b19d-128">O MRTK terá suporte para permitir que os aplicativos sejam criados com uma variedade de arquiteturas, incluindo:</span><span class="sxs-lookup"><span data-stu-id="1b19d-128">The MRTK will have support to enable applications to be built with a variety of architectures, including:</span></span>

- [<span data-ttu-id="1b19d-129">Localizador de serviço MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="1b19d-129">MixedRealityToolkit service locator</span></span>](#mixedrealitytoolkit-service-locator)
- [<span data-ttu-id="1b19d-130">Serviços individuais</span><span class="sxs-lookup"><span data-stu-id="1b19d-130">Individual services</span></span>](#individual-service-components)
- [<span data-ttu-id="1b19d-131">Localizador de serviço personalizado</span><span class="sxs-lookup"><span data-stu-id="1b19d-131">Custom service locator</span></span>](#custom-service-locator)
- [<span data-ttu-id="1b19d-132">Arquitetura híbrida</span><span class="sxs-lookup"><span data-stu-id="1b19d-132">Hybrid architecture</span></span>](#hybrid-architecture)

<span data-ttu-id="1b19d-133">Ao selecionar uma arquitetura de aplicativo, é importante considerar a flexibilidade de design e o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b19d-133">When selecting an application architecture, it is important to consider design flexibility and application performance.</span></span> <span data-ttu-id="1b19d-134">As arquiteturas descritas aqui não devem ser adequadas para todos os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1b19d-134">The architectures described here are not expected to be suitable for every application.</span></span>

#### <a name="mixedrealitytoolkit-service-locator"></a><span data-ttu-id="1b19d-135">Localizador de serviço MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="1b19d-135">MixedRealityToolkit service locator</span></span>

<span data-ttu-id="1b19d-136">O MRTK habilita (e configura automaticamente) cenas de aplicativos para usar o componente de [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) localizador de serviço padrão.</span><span class="sxs-lookup"><span data-stu-id="1b19d-136">The MRTK enables (and automatically configures) application scenes to use the default [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator component.</span></span> <span data-ttu-id="1b19d-137">Este componente inclui suporte para configurar sistemas e provedores de dados MRTK por meio de inspetores de configuração e gerencia a vida útil do componente e os comportamentos principais (por exemplo: quando atualizar).</span><span class="sxs-lookup"><span data-stu-id="1b19d-137">This component includes support for configuring MRTK systems and data providers via configuration inspectors and manages component lifespans and core behaviors (ex: when to update).</span></span>

<span data-ttu-id="1b19d-138">Todos os sistemas são representados no Inspetor de configuração principal, independentemente de estarem ou não presentes ou habilitados no projeto.</span><span class="sxs-lookup"><span data-stu-id="1b19d-138">All systems are represented in the core configuration inspector, regardless of whether or not they are present or enabled in the project.</span></span> <span data-ttu-id="1b19d-139">Consulte o [Guia de configuração da realidade misturada](../configuration/mixed-reality-configuration-guide.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="1b19d-139">Please see the [Mixed Reality Configuration Guide](../configuration/mixed-reality-configuration-guide.md) for more information.</span></span>

#### <a name="individual-service-components"></a><span data-ttu-id="1b19d-140">Componentes de serviço individuais</span><span class="sxs-lookup"><span data-stu-id="1b19d-140">Individual service components</span></span>

<span data-ttu-id="1b19d-141">Alguns desenvolvedores expressou um desejo de incluir componentes de serviço individuais na hierarquia de cena do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b19d-141">Some developers have expressed a desire to include individual service components into the application scene hierarchy.</span></span> <span data-ttu-id="1b19d-142">Para habilitar esse uso, os serviços precisarão ser encapsulados em um registrador personalizado ou em Autoregistro/autogerenciamento.</span><span class="sxs-lookup"><span data-stu-id="1b19d-142">To enable this usage, services will either need to be encapsulated in a custom registrar or be self-registering / self-managing.</span></span>

<span data-ttu-id="1b19d-143">Um serviço de registro automático implementaria o [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) e se registrará para que o código do aplicativo pudesse descobrir a instância do serviço por meio de um registro.</span><span class="sxs-lookup"><span data-stu-id="1b19d-143">A self-registering service would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) and register itself so that application code could discover the service instance via a registry.</span></span>

<span data-ttu-id="1b19d-144">Um serviço de autogerenciamento pode ser implementado como um objeto singleton na hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="1b19d-144">A self-managing service could be implemented as a singleton object in the scene hierarchy.</span></span> <span data-ttu-id="1b19d-145">Esse objeto forneceria e a propriedade de instância que o código do aplicativo poderia usar para acessar diretamente a funcionalidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="1b19d-145">This object would provide and instance property which application code could use to directly access service functionality.</span></span>

#### <a name="custom-service-locator"></a><span data-ttu-id="1b19d-146">Localizador de serviço personalizado</span><span class="sxs-lookup"><span data-stu-id="1b19d-146">Custom service locator</span></span>

<span data-ttu-id="1b19d-147">Alguns desenvolvedores solicitaram a capacidade de criar um componente de localizador de serviço personalizado.</span><span class="sxs-lookup"><span data-stu-id="1b19d-147">Some developers have requested the ability to create a custom service locator component.</span></span> <span data-ttu-id="1b19d-148">Os localizadores de serviço personalizados implementariam a interface e gerenciariam o ciclo de vida e [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) os comportamentos principais dos serviços ativos.</span><span class="sxs-lookup"><span data-stu-id="1b19d-148">Custom service locators would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface and manage the life cycle and core behaviors of active services.</span></span>

#### <a name="hybrid-architecture"></a><span data-ttu-id="1b19d-149">Arquitetura híbrida</span><span class="sxs-lookup"><span data-stu-id="1b19d-149">Hybrid architecture</span></span>

<span data-ttu-id="1b19d-150">O MRTK dará suporte a uma arquitetura híbrida na qual os desenvolvedores podem combinar as abordagens anteriores conforme necessário ou desejado.</span><span class="sxs-lookup"><span data-stu-id="1b19d-150">The MRTK will support a hybrid architecture in which developers can combine the previous approaches as needed or desired.</span></span> <span data-ttu-id="1b19d-151">Por exemplo, um desenvolvedor pode começar com o [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) localizador de serviço e adicionar um serviço de auto-registro.</span><span class="sxs-lookup"><span data-stu-id="1b19d-151">For example, a developer could start with the [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator and add a self-registering service.</span></span>

> [!NOTE]
> <span data-ttu-id="1b19d-152">Ao optar por uma arquitetura híbrida, é importante estar atento a qualquer duplicação de trabalho (por exemplo: adquirir dados do controlador de vários componentes).</span><span class="sxs-lookup"><span data-stu-id="1b19d-152">When opting for a hybrid architecture, it is important to be mindful of any duplication of work (ex: acquiring controller data from multiple components).</span></span>
