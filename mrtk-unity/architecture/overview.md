---
title: Visão geral da arquitetura
description: Visão geral da arquitetura do MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, arquitetura MRTK,
ms.openlocfilehash: 431e091cb6dc0efa0f941b95f58811d57166c82f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281914"
---
# <a name="architecture-overview"></a><span data-ttu-id="e77fa-104">Visão geral da arquitetura</span><span class="sxs-lookup"><span data-stu-id="e77fa-104">Architecture overview</span></span>

<span data-ttu-id="e77fa-105">Para obter uma introdução geral ao conteúdo de MRTK, as informações de arquitetura contidas neste documento ajudarão você a entender o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e77fa-105">For an overall introduction to the contents of MRTK, the architecture information contained in this document will help you understand the following:</span></span>

- <span data-ttu-id="e77fa-106">Grandes pedaços de MRTK e como eles se conectam</span><span class="sxs-lookup"><span data-stu-id="e77fa-106">Large pieces of MRTK and how they connect</span></span>
- <span data-ttu-id="e77fa-107">Conceitos que o MRTK introduz, que pode não existir no Unity da baunilha</span><span class="sxs-lookup"><span data-stu-id="e77fa-107">Concepts that MRTK introduces which may not exist in vanilla Unity</span></span>
- <span data-ttu-id="e77fa-108">Como alguns dos sistemas maiores (como entrada) funcionam</span><span class="sxs-lookup"><span data-stu-id="e77fa-108">How some of the larger systems (such as Input) work</span></span>

<span data-ttu-id="e77fa-109">Esta seção não se destina a ensinar como realizar tarefas, mas como essas tarefas são estruturadas e por quê.</span><span class="sxs-lookup"><span data-stu-id="e77fa-109">This section isn't intended to teach you how to do tasks, but rather how such tasks are structured and why.</span></span>

## <a name="many-audiences-one-toolkit"></a><span data-ttu-id="e77fa-110">Muitos públicos, um kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="e77fa-110">Many audiences, one toolkit</span></span>

<span data-ttu-id="e77fa-111">O MRTK não tem um público único e uniforme.</span><span class="sxs-lookup"><span data-stu-id="e77fa-111">MRTK doesn't have a single, uniform audience.</span></span> <span data-ttu-id="e77fa-112">Ele foi escrito para dar suporte a casos de uso que vão desde o primeiro hackathons, até indivíduos que criam experiências complexas e compartilhadas para empresas.</span><span class="sxs-lookup"><span data-stu-id="e77fa-112">It's been written to support use cases ranging from first time hackathons, to individuals building complex, shared experiences for enterprise.</span></span> <span data-ttu-id="e77fa-113">Alguns códigos e APIs podem ter sido escritos e otimizados para um mais do que o outro (ou seja, algumas partes do MRTK parecem mais otimizadas para "configurar um clique"), mas é importante observar que alguns deles são mais para motivos históricos e de terceirização.</span><span class="sxs-lookup"><span data-stu-id="e77fa-113">Some code and APIs may have been written that are optimized for one more than the other (i.e. some parts of the MRTK seem more optimized for "one click configure"), but it's important to note that some of those are more for historical and resourcing reasons.</span></span> <span data-ttu-id="e77fa-114">À medida que o MRTK evolui, os recursos que são criados devem ser projetados para serem dimensionados para dar suporte ao intervalo de casos de uso.</span><span class="sxs-lookup"><span data-stu-id="e77fa-114">As MRTK evolves, the features that get built should be designed to scale to support the range of use cases.</span></span>

<span data-ttu-id="e77fa-115">O MRTK também tem requisitos para dimensionar normalmente em experiências de VR e AR.</span><span class="sxs-lookup"><span data-stu-id="e77fa-115">MRTK also has requirements to gracefully scale across VR and AR experiences.</span></span> <span data-ttu-id="e77fa-116">deve ser fácil criar aplicativos que são normalmente fallback no comportamento quando implantados em um HoloLens 2 ou em um HoloLens 1, e deve ser simples criar aplicativos direcionados a OpenVR e WMR (e outras plataformas).</span><span class="sxs-lookup"><span data-stu-id="e77fa-116">It should be easy to build applications that gracefully fallback in behavior when deployed on a HoloLens 2 OR a HoloLens 1, and it should be simple to build applications that target OpenVR and WMR (and other platforms).</span></span> <span data-ttu-id="e77fa-117">Embora às vezes a equipe possa focar uma iteração específica em um sistema ou plataforma específica, a meta a longo prazo é criar uma ampla gama de suporte para sempre que as pessoas criarem experiências de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="e77fa-117">While at times the team may focus a particular iteration on a specific system or platform, the long term goal is to build a wide range of support for wherever people are building mixed reality experiences.</span></span>

## <a name="high-level-breakdown"></a><span data-ttu-id="e77fa-118">Divisão de alto nível</span><span class="sxs-lookup"><span data-stu-id="e77fa-118">High level breakdown</span></span>

<span data-ttu-id="e77fa-119">O MRTK é uma coleção de ferramentas para obter experiências de realidade misturada (MR) com a base rapidamente, e também uma estrutura de aplicativo com opiniões sobre seu próprio tempo de execução, como ela deve ser estendida e como deve ser configurada.</span><span class="sxs-lookup"><span data-stu-id="e77fa-119">The MRTK is both a collection of tools for getting mixed reality (MR) experiences off the ground quickly, and also an application framework with opinions on its own runtime, how it should be extended, and how it should be configured.</span></span>

<span data-ttu-id="e77fa-120">Em um alto nível, o MRTK pode ser dividido das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="e77fa-120">At a high level, the MRTK can be broken down in the following ways:</span></span>

![Diagrama de visão geral da arquitetura](../features/images/architecture/MRTK_Architecture.png)

<span data-ttu-id="e77fa-122">O MRTK também contém outro conjunto de utilitários de captura que têm pouca ou nenhuma dependência no restante do MRTK (para listar alguns: ferramentas de compilação, resolvedores, influenciadores de áudio, utilitários de suavização e renderizadores de linha)</span><span class="sxs-lookup"><span data-stu-id="e77fa-122">The MRTK also contains another set of grab-bag utilities that have little to no dependencies on the rest of the MRTK (to list a few: build tools, solvers, audio influencers, smoothing utilities, and line renderers)</span></span>

<span data-ttu-id="e77fa-123">O restante da documentação da arquitetura será criado de forma inferior, começando com a estrutura e o tempo de execução, progredindo para sistemas mais interessantes e complexos, como entrada.</span><span class="sxs-lookup"><span data-stu-id="e77fa-123">The remainder of the architecture documentation will build bottom up, starting from the framework and runtime, progressing to more interesting and complex systems, such as input.</span></span> <span data-ttu-id="e77fa-124">Consulte o Sumário para continuar com a visão geral da arquitetura.</span><span class="sxs-lookup"><span data-stu-id="e77fa-124">Please see the table of contents to continue with the architectural overview.</span></span>
