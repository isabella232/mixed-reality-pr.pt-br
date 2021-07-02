---
title: Roteiro
description: documentação para delinear o roteiro do MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK
ms.openlocfilehash: 7385d516e986c1602ad59e2825aa6d1262504727
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175584"
---
# <a name="roadmap"></a><span data-ttu-id="e994e-104">Roteiro</span><span class="sxs-lookup"><span data-stu-id="e994e-104">Roadmap</span></span>

<span data-ttu-id="e994e-105">Este documento descreve o roteiro da política de Realidade Misturada Toolkit.</span><span class="sxs-lookup"><span data-stu-id="e994e-105">This document outlines the roadmap of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="e994e-106">Observe que o seguinte reflete o trabalho que está em datas de desenvolvimento e de destino refletem estimativas.</span><span class="sxs-lookup"><span data-stu-id="e994e-106">Please note that the following reflects work that is in development and target dates reflect estimates.</span></span>

## <a name="current-release"></a><span data-ttu-id="e994e-107">Versão atual</span><span class="sxs-lookup"><span data-stu-id="e994e-107">Current release</span></span>

<span data-ttu-id="e994e-108">Microsoft Mixed Reality Toolkit v2.6</span><span class="sxs-lookup"><span data-stu-id="e994e-108">Microsoft Mixed Reality Toolkit v2.6</span></span>

## <a name="upcoming-releases"></a><span data-ttu-id="e994e-109">Versões futuras</span><span class="sxs-lookup"><span data-stu-id="e994e-109">Upcoming releases</span></span>

| <span data-ttu-id="e994e-110">Produto</span><span class="sxs-lookup"><span data-stu-id="e994e-110">Product</span></span> | <span data-ttu-id="e994e-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="e994e-111">Description</span></span> | <span data-ttu-id="e994e-112">Linha do tempo</span><span class="sxs-lookup"><span data-stu-id="e994e-112">Timeline</span></span> | <span data-ttu-id="e994e-113">Project placa</span><span class="sxs-lookup"><span data-stu-id="e994e-113">Project board</span></span> |
| --- | --- | --- | --- |
| [<span data-ttu-id="e994e-114">MRTK V2.7</span><span class="sxs-lookup"><span data-stu-id="e994e-114">MRTK V2.7</span></span>](#270) | <span data-ttu-id="e994e-115">Próxima iteração do MRTK</span><span class="sxs-lookup"><span data-stu-id="e994e-115">Next iteration of MRTK</span></span> | <span data-ttu-id="e994e-116">Maio de 2021</span><span class="sxs-lookup"><span data-stu-id="e994e-116">May 2021</span></span> | https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14 |

<span data-ttu-id="e994e-117">As versões são centralizadas em torno de temas (por ex. áreas de recursos grandes) e são agendadas para ocorrer aproximadamente a cada 8 a 12 semanas.</span><span class="sxs-lookup"><span data-stu-id="e994e-117">Releases are centered around themes (ex: large feature areas) and are scheduled to occur approximately every 8-12 weeks.</span></span>

<span data-ttu-id="e994e-118">Os detalhes da versão, incluindo itens da lista de pendências, podem ser encontrados [nas páginas GitHub marcos.](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones)</span><span class="sxs-lookup"><span data-stu-id="e994e-118">Release details, including backlog items, can be found on the [GitHub milestone pages](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones).</span></span> <span data-ttu-id="e994e-119">O conjunto completo de problemas abertos também pode ser encontrado [no GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="e994e-119">The complete set of open issues can also be found on [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a><span data-ttu-id="e994e-120">Roteiro do MRTK (Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="e994e-120">Mixed Reality Toolkit (MRTK) roadmap</span></span>

<span data-ttu-id="e994e-121">A plataforma Toolkit realidade misturada foi criada para ser cruzada pela plataforma MR/AR/VR/XR por design.</span><span class="sxs-lookup"><span data-stu-id="e994e-121">The Mixed Reality Toolkit is built to be cross MR/AR/VR/XR platform by design.</span></span> <span data-ttu-id="e994e-122">Atualmente, o kit de ferramentas dá suporte ao Unity 2019.4.x e ao Unity 2018.4.x.</span><span class="sxs-lookup"><span data-stu-id="e994e-122">The toolkit currently supports Unity 2019.4.x and Unity 2018.4.x.</span></span>

> <span data-ttu-id="e994e-123">Quando o Unity lançar um produto LTS (suporte a longo prazo), o Toolkit realidade misturada será atualizado para a versão LTS.</span><span class="sxs-lookup"><span data-stu-id="e994e-123">When Unity releases an LTS (Long Term Support) product, the Mixed Reality Toolkit will update to the LTS release.</span></span> <span data-ttu-id="e994e-124">Embora o Toolkit realidade misturada seja executado na versão mais recente do branch técnico não beta (por ex: 2020.1) do Unity, ele não tem suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="e994e-124">Although the Mixed Reality Toolkit runs on the latest non-beta (ex: 2020.1) tech branch version of Unity, it is not officially supported.</span></span>

### <a name="270"></a><span data-ttu-id="e994e-125">2.7.0</span><span class="sxs-lookup"><span data-stu-id="e994e-125">2.7.0</span></span>

<span data-ttu-id="e994e-126">No momento, estamos planejando a versão 2.7.0 e teremos mais atualizações para você em breve!</span><span class="sxs-lookup"><span data-stu-id="e994e-126">We are currently planning the 2.7.0 release and will have more updates for you soon!</span></span>
<span data-ttu-id="e994e-127">Para o status mais recente da versão, visite a página [do marco](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).</span><span class="sxs-lookup"><span data-stu-id="e994e-127">For the latest status of the release, please visit the [milestone page](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).</span></span>

<span data-ttu-id="e994e-128">Status: Planejamento</span><span class="sxs-lookup"><span data-stu-id="e994e-128">Status: Planning</span></span>

<span data-ttu-id="e994e-129">Linha do tempo de destino: maio de 2021</span><span class="sxs-lookup"><span data-stu-id="e994e-129">Target Timeline: May 2021</span></span>

<span data-ttu-id="e994e-130">Temas:</span><span class="sxs-lookup"><span data-stu-id="e994e-130">Themes:</span></span>

- <span data-ttu-id="e994e-131">Stability</span><span class="sxs-lookup"><span data-stu-id="e994e-131">Stability</span></span> 
- <span data-ttu-id="e994e-132">Expansão da plataforma: OpenXR</span><span class="sxs-lookup"><span data-stu-id="e994e-132">Platform Expansion: OpenXR</span></span>
- <span data-ttu-id="e994e-133">Experiência de usuário</span><span class="sxs-lookup"><span data-stu-id="e994e-133">User Experience</span></span>
- <span data-ttu-id="e994e-134">Educação do desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="e994e-134">Developer Education</span></span>
- <span data-ttu-id="e994e-135">Empacotamento</span><span class="sxs-lookup"><span data-stu-id="e994e-135">Packaging</span></span>

<span data-ttu-id="e994e-136">**Estabilidade**</span><span class="sxs-lookup"><span data-stu-id="e994e-136">**Stability**</span></span>

<span data-ttu-id="e994e-137">A qualidade e a estabilidade são a prioridade principal para este e todas as versões do Microsoft Mixed Reality Toolkit versões.</span><span class="sxs-lookup"><span data-stu-id="e994e-137">Quality and stability are the top priority for this and all Microsoft Mixed Reality Toolkit releases.</span></span> <span data-ttu-id="e994e-138">Continuaremos priorizando problemas de clientes e parceiros que impactam a estabilidade dos componentes do MRTK.</span><span class="sxs-lookup"><span data-stu-id="e994e-138">We will continue to prioritize customer and partner issues that impact the stability of MRTK components.</span></span>

<span data-ttu-id="e994e-139">**Expansão da plataforma: OpenXR**</span><span class="sxs-lookup"><span data-stu-id="e994e-139">**Platform Expansion: OpenXR**</span></span>

<span data-ttu-id="e994e-140">A equipe do MRTK dá suporte ao futuro aberto da realidade misturada por meio [do OpenXR.](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672)</span><span class="sxs-lookup"><span data-stu-id="e994e-140">The MRTK team supports the open future of mixed reality through [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672).</span></span> <span data-ttu-id="e994e-141">Atualmente, o suporte para OpenXR está em desenvolvimento, com suporte de visualização inicial lançado no MRTK 2.5.2.</span><span class="sxs-lookup"><span data-stu-id="e994e-141">Support for OpenXR is currently under development, with initial preview support released in MRTK 2.5.2.</span></span>

<span data-ttu-id="e994e-142">**Experiência do Usuário**</span><span class="sxs-lookup"><span data-stu-id="e994e-142">**User Experience**</span></span>

<span data-ttu-id="e994e-143">Estamos escutando seus comentários sobre o MRTK e temos planos contínuos para:</span><span class="sxs-lookup"><span data-stu-id="e994e-143">We're listening to your feedback about MRTK and have continued plans for:</span></span>

- <span data-ttu-id="e994e-144">Correções de bug</span><span class="sxs-lookup"><span data-stu-id="e994e-144">Bug fixes</span></span>
- <span data-ttu-id="e994e-145">Facilitando a compreensão dos controles de UX do MRTK</span><span class="sxs-lookup"><span data-stu-id="e994e-145">Making MRTK UX controls easier to understand</span></span>
- <span data-ttu-id="e994e-146">HoloLens Paridade do shell</span><span class="sxs-lookup"><span data-stu-id="e994e-146">HoloLens Shell parity</span></span>
- <span data-ttu-id="e994e-147">Testes para garantir que os recursos não regredim</span><span class="sxs-lookup"><span data-stu-id="e994e-147">Tests to ensure features do not regress</span></span>

<span data-ttu-id="e994e-148">**Educação do desenvolvedor**</span><span class="sxs-lookup"><span data-stu-id="e994e-148">**Developer Education**</span></span>

<span data-ttu-id="e994e-149">Migramos nossa documentação do desenvolvedor do Github para uma nova plataforma de documentos!</span><span class="sxs-lookup"><span data-stu-id="e994e-149">We've migrated our developer documentation from Github to a new docs platform!</span></span> <span data-ttu-id="e994e-150">Queremos ouvir seus comentários para que possamos continuar melhorando nossa experiência de documentação do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="e994e-150">We want to hear your feedback so we can continue to improve our developer documentation experience.</span></span>
<span data-ttu-id="e994e-151">Atualmente, temos tutoriais [do MRTK](/windows/mixed-reality/develop/unity/tutorials) que estão em uma seção diferente dos documentos de Realidade Misturada. Migraremos esses tutoriais para trabalhar com o restante da documentação do MRTK.</span><span class="sxs-lookup"><span data-stu-id="e994e-151">We currently have [MRTK tutorials](/windows/mixed-reality/develop/unity/tutorials) that live in a different section of Mixed Reality docs. We will be migrating these tutorials to live with the rest of the MRTK documentation.</span></span> 

<span data-ttu-id="e994e-152">**Empacotamento**</span><span class="sxs-lookup"><span data-stu-id="e994e-152">**Packaging**</span></span>

<span data-ttu-id="e994e-153">A [Ferramenta de Recursos de Realidade](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) Misturada é uma nova maneira para os desenvolvedores descobrirem, atualizarem e adicionarem pacotes de recursos de Realidade Misturada em projetos do Unity.</span><span class="sxs-lookup"><span data-stu-id="e994e-153">The [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="e994e-154">Você pode pesquisar pacotes por nome ou categoria, ver as respectivas dependências e, até mesmo, ver as alterações propostas no arquivo de manifesto dos seus projetos antes da importação.</span><span class="sxs-lookup"><span data-stu-id="e994e-154">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="e994e-155">Pretendemos fazer atualizações para a Ferramenta de Recursos de Realidade Misturada conforme respondemos a solicitações de recursos e bugs.</span><span class="sxs-lookup"><span data-stu-id="e994e-155">We intend to make updates to the Mixed Reality Feature Tool as we respond to feature requests and bugs.</span></span>

## <a name="backlog"></a><span data-ttu-id="e994e-156">Lista de pendências</span><span class="sxs-lookup"><span data-stu-id="e994e-156">Backlog</span></span>

<span data-ttu-id="e994e-157">A lista a seguir destaca alguns dos principais investimentos que a equipe do MRTK pretende buscar.</span><span class="sxs-lookup"><span data-stu-id="e994e-157">The following list highlights some of the key investments the MRTK team intends to pursue.</span></span>

- <span data-ttu-id="e994e-158">Expansão da plataforma</span><span class="sxs-lookup"><span data-stu-id="e994e-158">Platform expansion</span></span>
- <span data-ttu-id="e994e-159">Extensibilidade</span><span class="sxs-lookup"><span data-stu-id="e994e-159">Extensibility</span></span>
- <span data-ttu-id="e994e-160">Modularidade</span><span class="sxs-lookup"><span data-stu-id="e994e-160">Modularity</span></span>
- <span data-ttu-id="e994e-161">Funcionalidades de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="e994e-161">Accessibility features</span></span>
- <span data-ttu-id="e994e-162">Aprimoramentos de globalização</span><span class="sxs-lookup"><span data-stu-id="e994e-162">Globalization enhancements</span></span>
- <span data-ttu-id="e994e-163">Suporte ao serviço de nuvem</span><span class="sxs-lookup"><span data-stu-id="e994e-163">Cloud service support</span></span>
- <span data-ttu-id="e994e-164">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="e994e-164">Tools</span></span>
