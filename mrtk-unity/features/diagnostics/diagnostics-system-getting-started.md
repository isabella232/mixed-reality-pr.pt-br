---
title: Visão geral do sistema de diagnóstico
description: Documentação para habilitar e desabilitar o diagnóstico no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: a31b88f661c141941cae2d0b01668b26c0bed7d7
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177241"
---
# <a name="diagnostics-system-overview"></a><span data-ttu-id="366bb-104">Visão geral do sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="366bb-104">Diagnostics system overview</span></span>

<span data-ttu-id="366bb-105">O Sistema de Diagnóstico Toolkit Mixed Reality fornece ferramentas de diagnóstico que são executados dentro do aplicativo para habilitar a análise de problemas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="366bb-105">The Mixed Reality Toolkit Diagnostic System provides diagnostic tools that run within the application to enable analysis of application issues.</span></span>

<span data-ttu-id="366bb-106">A primeira versão do Sistema de Diagnóstico contém o [Visual Profiler](using-visual-profiler.md) para permitir a análise de problemas de desempenho ao usar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="366bb-106">The first release of the Diagnostic System contains the [Visual Profiler](using-visual-profiler.md) to allow for analyzing performance issues while using the application.</span></span>

## <a name="getting-started"></a><span data-ttu-id="366bb-107">Introdução</span><span class="sxs-lookup"><span data-stu-id="366bb-107">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="366bb-108">É altamente **_recomendável_** que o Sistema de Diagnóstico seja habilitado em todo o ciclo de desenvolvimento do produto e desabilitado como a última alteração antes de criar e liberar a versão final.</span><span class="sxs-lookup"><span data-stu-id="366bb-108">It is **_highly_** recommended that the Diagnostic System be enabled throughout the entire product development cycle and disabled as the last change prior to building and releasing the final version.</span></span>

<span data-ttu-id="366bb-109">Há duas etapas principais para começar a usar o Sistema de Diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="366bb-109">There are two key steps to start using the Diagnostic System.</span></span>

1. <span data-ttu-id="366bb-110">[Habilitar](#enable-diagnostics) o sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="366bb-110">[Enable](#enable-diagnostics) the Diagnostic System</span></span>
2. <span data-ttu-id="366bb-111">[Configurar opções](#configure-diagnostic-options) de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="366bb-111">[Configure](#configure-diagnostic-options) diagnostic options</span></span>

### <a name="enable-diagnostics"></a><span data-ttu-id="366bb-112">Habilitar diagnósticos</span><span class="sxs-lookup"><span data-stu-id="366bb-112">Enable diagnostics</span></span>

<span data-ttu-id="366bb-113">O sistema de diagnóstico é gerenciado pelo objeto MixedRealityToolkit (ou outro [componente do registrador de](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) serviços).</span><span class="sxs-lookup"><span data-stu-id="366bb-113">The diagnostics system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="366bb-114">As etapas a seguir presumem o uso do objeto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="366bb-114">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="366bb-115">As etapas necessárias para outros registradores de serviço podem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="366bb-115">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="366bb-116">Selecione o objeto MixedRealityToolkit na hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="366bb-116">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Hierarquia de cena configurada do MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="366bb-118">Navegue pelo painel Inspetor até a seção Sistema de Diagnóstico e marque Habilitar</span><span class="sxs-lookup"><span data-stu-id="366bb-118">Navigate the Inspector panel to the Diagnostics System section and check Enable</span></span>
1. <span data-ttu-id="366bb-119">Selecione a implementação do Sistema de Diagnóstico</span><span class="sxs-lookup"><span data-stu-id="366bb-119">Select the Diagnostics System implementation</span></span>

    ![Selecione a implementação do sistema de diagnóstico](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="366bb-121">Os usuários do perfil padrão, `DefaultMixedRealityToolkitConfigurationProfile` (Ativos/MRTK/SDK/Perfis), terão o sistema de diagnóstico pré-configurado para usar o [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) objeto .</span><span class="sxs-lookup"><span data-stu-id="366bb-121">Users of the default profile, `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles), will have the diagnostics system pre-configured to use the [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) object.</span></span>

### <a name="configure-diagnostic-options"></a><span data-ttu-id="366bb-122">Configurar opções de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="366bb-122">Configure diagnostic options</span></span>

<span data-ttu-id="366bb-123">O sistema de diagnóstico usa um perfil de configuração para especificar quais componentes devem ser exibidos e definir suas configurações.</span><span class="sxs-lookup"><span data-stu-id="366bb-123">The diagnostics system uses a configuration profile to specify which components are to be displayed and to configure their settings.</span></span> <span data-ttu-id="366bb-124">Consulte [Configurando o sistema de diagnóstico para](configuring-diagnostics.md) obter mais informações referentes às configurações de componente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="366bb-124">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information pertaining to the available component settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="366bb-125">Embora seja possível usar o Modo de Reprodução do Unity ao desenvolver aplicativos sem exigir as etapas de build e implantação, é importante avaliar os resultados do sistema de diagnóstico usando um aplicativo compilado em execução no hardware e na plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="366bb-125">While it is possible to use Unity's Play Mode while developing applications without requiring the build and deploy steps, it is important to evaluate the diagnostics system results using a compiled application running on the target hardware and platform.</span></span>
>
> <span data-ttu-id="366bb-126">O diagnóstico de desempenho, como o [Visual Profiler,](using-visual-profiler.md)pode não refletir com precisão o desempenho real do aplicativo quando executado de dentro do editor.</span><span class="sxs-lookup"><span data-stu-id="366bb-126">Performance diagnostics, such as the [Visual Profiler](using-visual-profiler.md), may not accurately reflect actual application performance when run from within the editor.</span></span>

## <a name="see-also"></a><span data-ttu-id="366bb-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="366bb-127">See also</span></span>

- [<span data-ttu-id="366bb-128">Documentação da API de Diagnóstico</span><span class="sxs-lookup"><span data-stu-id="366bb-128">Diagnostics API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [<span data-ttu-id="366bb-129">Configurando o sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="366bb-129">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
- [<span data-ttu-id="366bb-130">Usando o Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="366bb-130">Using the Visual Profiler</span></span>](using-visual-profiler.md)
