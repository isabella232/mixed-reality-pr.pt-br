---
title: Visão geral do sistema de limite
description: Página de aterrissagem para o sistema de limite no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, sistema de limite,
ms.openlocfilehash: 405a2d06be5d929d5c276fc8cd7ab36b6b3cf68c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121354"
---
# <a name="boundary-system"></a><span data-ttu-id="22697-104">Sistema de limite</span><span class="sxs-lookup"><span data-stu-id="22697-104">Boundary system</span></span>

<span data-ttu-id="22697-105">O sistema de limite fornece suporte para visualização de componentes de limite da realidade virtual em aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="22697-105">The Boundary system provides support for visualizing Virtual Reality boundary components in mixed reality applications.</span></span> <span data-ttu-id="22697-106">Os limites definem a área na qual os usuários podem se movimentar com segurança ao mesmo tempo em que se aproveitam um headset VR.</span><span class="sxs-lookup"><span data-stu-id="22697-106">Boundaries define the area in which users can safely move around while wearing a VR headset.</span></span> <span data-ttu-id="22697-107">Os limites são um componente importante de uma experiência de realidade misturada para ajudar os usuários a evitar obstáculos não vistos ao utilizar um headset de VR.</span><span class="sxs-lookup"><span data-stu-id="22697-107">Boundaries are an important component of a mixed reality experience to help users avoid unseen obstacles while wearing a VR headset.</span></span>

<span data-ttu-id="22697-108">Muitas plataformas de realidade virtual fornecem uma exibição automática, por exemplo, uma estrutura de tópicos branco sobreposta no mundo virtual como o usuário ou seu controlador perto do limite.</span><span class="sxs-lookup"><span data-stu-id="22697-108">Many Virtual Reality platforms provide an automatic display, for example a white outline superimposed on the virtual world as the user or their controller nears the boundary.</span></span> <span data-ttu-id="22697-109">O sistema de limite do kit de ferramentas da realidade misturada estende esse recurso para habilitar a exibição de uma estrutura de tópicos da área controlada, um plano de chão e outros recursos que podem ser usados para fornecer informações adicionais aos usuários.</span><span class="sxs-lookup"><span data-stu-id="22697-109">The Mixed Reality Toolkit's Boundary System extends this feature to enable the display of an outline of the tracked area, a floor plane and other features that can be used to provide additional information to users.</span></span>

## <a name="getting-started"></a><span data-ttu-id="22697-110">Introdução</span><span class="sxs-lookup"><span data-stu-id="22697-110">Getting started</span></span>

<span data-ttu-id="22697-111">Adicionar suporte para limites requer dois componentes principais do kit de ferramentas de realidade misturada: o sistema de limite e uma plataforma de realidade virtual configurada com um limite.</span><span class="sxs-lookup"><span data-stu-id="22697-111">Adding support for boundaries requires two key components of the Mixed Reality Toolkit: the Boundary System and a Virtual Reality platform configured with a boundary.</span></span>

1. <span data-ttu-id="22697-112">[Habilitar](#enable-boundary-system) o sistema de limite</span><span class="sxs-lookup"><span data-stu-id="22697-112">[Enable](#enable-boundary-system) the boundary system</span></span>
2. <span data-ttu-id="22697-113">[Configurar](#configure-boundary-visualization) a visualização de limite</span><span class="sxs-lookup"><span data-stu-id="22697-113">[Configure](#configure-boundary-visualization) the boundary visualization</span></span>
3. <span data-ttu-id="22697-114">[Crie e implante](#build-and-deploy) em uma plataforma VR com um limite configurado</span><span class="sxs-lookup"><span data-stu-id="22697-114">[Build and deploy](#build-and-deploy) to a VR platform with a configured boundary</span></span>

## <a name="enable-boundary-system"></a><span data-ttu-id="22697-115">Habilitar sistema de limite</span><span class="sxs-lookup"><span data-stu-id="22697-115">Enable boundary system</span></span>

<span data-ttu-id="22697-116">O sistema de limite é gerenciado pelo objeto MixedRealityToolkit (ou outro componente [registrador de serviço](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).</span><span class="sxs-lookup"><span data-stu-id="22697-116">The Boundary System is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="22697-117">As etapas a seguir presumem o uso do objeto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="22697-117">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="22697-118">As etapas necessárias para outros registradores de serviço podem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="22697-118">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="22697-119">Selecione o objeto MixedRealityToolkit na hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="22697-119">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK hierarquia de cena configurada](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="22697-121">Navegue pelo painel Inspetor até a seção sistema de limite e marque Habilitar</span><span class="sxs-lookup"><span data-stu-id="22697-121">Navigate the Inspector panel to the Boundary System section and check Enable</span></span>

    ![Habilitar o sistema de limite](../images/boundary/MRTKConfig_Boundary.png)

1. <span data-ttu-id="22697-123">Selecione a implementação do sistema de limite.</span><span class="sxs-lookup"><span data-stu-id="22697-123">Select the Boundary System implementation.</span></span> <span data-ttu-id="22697-124">A implementação de classe padrão fornecida pelo MRTK é o [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="22697-124">The default class implementation provided by the MRTK is the [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

    ![Selecione a implementação do sistema de limite](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="22697-126">Toda a implementação do sistema de limite deve estender o [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="22697-126">All Boundary System implementation must extend the [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span></span>

## <a name="configure-boundary-visualization"></a><span data-ttu-id="22697-127">Configurar a visualização de limite</span><span class="sxs-lookup"><span data-stu-id="22697-127">Configure boundary visualization</span></span>

<span data-ttu-id="22697-128">O [sistema de limite usa um perfil de configuração](configuring-boundary-visualization.md) para especificar quais componentes de limite devem ser exibidos e para configurar sua aparência.</span><span class="sxs-lookup"><span data-stu-id="22697-128">The [Boundary System uses a configuration profile](configuring-boundary-visualization.md) to specify which boundary components are to be displayed and to configure their appearance.</span></span>

![Opções de visualização de limite](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> <span data-ttu-id="22697-130">Os usuários do perfil padrão, `DefaultMixedRealityBoundaryVisualizationProfile` (assets/MRTK/SDK/Profiles) terão o sistema de limite pré-configurado para exibir um plano de chão, a área de reprodução e a área rastreada.</span><span class="sxs-lookup"><span data-stu-id="22697-130">Users of the default profile, `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) will have the boundary system pre-configured to display a floor plane, the play area and the tracked area.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="22697-131">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="22697-131">Build and deploy</span></span>

<span data-ttu-id="22697-132">Depois que o sistema de limite é configurado com as opções de visualização desejadas, o projeto pode ser compilado implantado na plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="22697-132">Once the boundary system is configured with the desired visualization options, the project can be built deployed to the target platform.</span></span>

> [!NOTE]
> <span data-ttu-id="22697-133">O modo de reprodução do Unity permite a visualização no editor do limite configurado.</span><span class="sxs-lookup"><span data-stu-id="22697-133">Unity Play Mode enables in-editor visualization of the configured boundary.</span></span> <span data-ttu-id="22697-134">Esse recurso permite desenvolvimento e testes rápidos sem a necessidade de criar e implantar a etapa.</span><span class="sxs-lookup"><span data-stu-id="22697-134">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="22697-135">Certifique-se de fazer o teste de aceitação final usando uma versão compilada e implantada do aplicativo, em execução no hardware e na plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="22697-135">Be sure to do final acceptance testing using an built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="accessing-boundary-system-via-code"></a><span data-ttu-id="22697-136">Acessando o sistema de limite por meio de código</span><span class="sxs-lookup"><span data-stu-id="22697-136">Accessing boundary system via code</span></span>

<span data-ttu-id="22697-137">Se habilitado e configurado, o sistema de limite pode ser acessado por meio da classe auxiliar estático CoreServices.</span><span class="sxs-lookup"><span data-stu-id="22697-137">If enabled and configured, the Boundary System can be accessed via the CoreServices static helper class.</span></span> <span data-ttu-id="22697-138">A referência pode ser usada para alterar dinamicamente os parâmetros de limite e acessar o GameObjects relacionado gerenciado pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="22697-138">The reference can then be used to dynamically change the Boundary parameters and access related GameObjects managed by the system.</span></span>

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a><span data-ttu-id="22697-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="22697-139">See also</span></span>

- [<span data-ttu-id="22697-140">Documentação da API de limite</span><span class="sxs-lookup"><span data-stu-id="22697-140">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="22697-141">Configurando a visualização de limite</span><span class="sxs-lookup"><span data-stu-id="22697-141">Configuring the Boundary Visualization</span></span>](configuring-boundary-visualization.md)
