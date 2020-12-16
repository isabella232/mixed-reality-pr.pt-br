---
title: Critérios de qualidade do aplicativo
description: Este documento descreve os principais fatores que afetam a qualidade dos aplicativos de realidade misturada.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: critérios de qualidade de aplicativo, realidade mista, aplicativo de realidade misturada, headset de realidade mista, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 788a2e8ac1a364f8c33e3895992fd99fa220a26a
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530285"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="4544c-104">Critérios de qualidade do aplicativo</span><span class="sxs-lookup"><span data-stu-id="4544c-104">App quality criteria</span></span>

<span data-ttu-id="4544c-105">Este documento descreve os principais fatores que afetam a qualidade dos aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="4544c-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="4544c-106">Para cada fator, as informações a seguir são fornecidas</span><span class="sxs-lookup"><span data-stu-id="4544c-106">For each factor, the following information is provided</span></span>
* <span data-ttu-id="4544c-107">Visão geral – uma breve descrição do fator de qualidade e por que ele é importante.</span><span class="sxs-lookup"><span data-stu-id="4544c-107">Overview – a brief description of the quality factor and why it's important.</span></span>
* <span data-ttu-id="4544c-108">Impacto do dispositivo – qual tipo de o dispositivo de realidade misturada da janela é afetado.</span><span class="sxs-lookup"><span data-stu-id="4544c-108">Device impact - which type of Window Mixed Reality device is affected.</span></span>
* <span data-ttu-id="4544c-109">Critérios de qualidade – como avaliar o fator de qualidade.</span><span class="sxs-lookup"><span data-stu-id="4544c-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="4544c-110">Como medir – métodos para medir (ou experimentar) o problema.</span><span class="sxs-lookup"><span data-stu-id="4544c-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="4544c-111">Recomendações – Resumo de abordagens para fornecer uma melhor experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="4544c-112">Recursos – desenvolvedor relevante e recursos de design que são úteis para criar melhores experiências de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4544c-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="4544c-113">Taxa de quadros</span><span class="sxs-lookup"><span data-stu-id="4544c-113">Frame rate</span></span>

<span data-ttu-id="4544c-114">A taxa de quadros é o primeiro pilar da estabilidade do holograma e do conforto do usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="4544c-115">A taxa de quadros abaixo dos destinos recomendados pode fazer com que os hologramas pareçam tremulação, afetando negativamente a believability da experiência e potencialmente causando fadiga de olho.</span><span class="sxs-lookup"><span data-stu-id="4544c-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="4544c-116">A taxa de quadros de destino para sua experiência em headsets de imersão de realidade mista do Windows é de 60 Hz ou 90 Hz, dependendo de quais PCs compatíveis com a realidade mista do Windows você está dando suporte.</span><span class="sxs-lookup"><span data-stu-id="4544c-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets is either 60 Hz or 90 Hz depending on which Windows Mixed Reality Compatible PCs you're supporting.</span></span> <span data-ttu-id="4544c-117">Para o HoloLens, a taxa de quadros de destino é de 60 Hz.</span><span class="sxs-lookup"><span data-stu-id="4544c-117">For HoloLens, the target frame rate is 60 Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4544c-118">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4544c-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4544c-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4544c-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4544c-121">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-121">✔️</span></span></td>
        <td><span data-ttu-id="4544c-122">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4544c-123">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="4544c-123">Quality criteria</span></span>

|  <span data-ttu-id="4544c-124">Melhor</span><span class="sxs-lookup"><span data-stu-id="4544c-124">Best</span></span>  |  <span data-ttu-id="4544c-125">Corresponde</span><span class="sxs-lookup"><span data-stu-id="4544c-125">Meets</span></span> |  <span data-ttu-id="4544c-126">Falha</span><span class="sxs-lookup"><span data-stu-id="4544c-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="4544c-127">O aplicativo atende consistentemente a meta de quadros por segundo (FPS) para o dispositivo de destino: 60 fps no HoloLens; 90 fps em ultra PCs; e 60 fps em computadores de base.</span><span class="sxs-lookup"><span data-stu-id="4544c-127">The app consistently meets frames per second (FPS) goal for target device: 60 fps on HoloLens; 90 fps on Ultra PCs; and 60 fps on mainstream PCs.</span></span> | <span data-ttu-id="4544c-128">O aplicativo tem quedas de quadros intermitentes que não impedem a experiência principal, ou FPS é consistentemente menor do que a meta desejada, mas não impede a experiência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4544c-128">The app has intermittent frame drops not impeding the core experience, or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="4544c-129">O aplicativo está apresentando uma queda na taxa de quadros em média a cada 10 segundos ou menos.</span><span class="sxs-lookup"><span data-stu-id="4544c-129">The app is experiencing a drop in frame rate on average every 10 seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="4544c-130">Como medir</span><span class="sxs-lookup"><span data-stu-id="4544c-130">How to measure</span></span>

* <span data-ttu-id="4544c-131">Um grafo de taxa de quadros em tempo real é fornecido pelo [portal do dispositivo do Windows](using-the-windows-device-portal.md#system-performance) em "desempenho do sistema".</span><span class="sxs-lookup"><span data-stu-id="4544c-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="4544c-132">Para a depuração de desenvolvimento, adicione um contador de diagnóstico de taxa de quadros ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4544c-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="4544c-133">Consulte recursos para um contador de exemplo.</span><span class="sxs-lookup"><span data-stu-id="4544c-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="4544c-134">Quedas de taxa de quadros podem ser experimentadas no dispositivo enquanto o aplicativo está em execução, movendo seu cabeçalho de lado para o outro.</span><span class="sxs-lookup"><span data-stu-id="4544c-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="4544c-135">Se o holograma mostrar uma movimentação de tremulação inesperada, a taxa de quadros baixa ou o plano de estabilidade provavelmente será a causa.</span><span class="sxs-lookup"><span data-stu-id="4544c-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4544c-136">Recomendações</span><span class="sxs-lookup"><span data-stu-id="4544c-136">Recommendations</span></span>

* <span data-ttu-id="4544c-137">Adicione um contador de taxa de quadros no início do trabalho de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="4544c-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="4544c-138">As alterações que incorrem em uma taxa de quadros de queda devem ser avaliadas e resolvidas adequadamente como um bug de desempenho.</span><span class="sxs-lookup"><span data-stu-id="4544c-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="4544c-139">Recursos</span><span class="sxs-lookup"><span data-stu-id="4544c-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4544c-140">Documentação</span><span class="sxs-lookup"><span data-stu-id="4544c-140">Documentation</span></span>

* [<span data-ttu-id="4544c-141">Entendendo o desempenho da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="4544c-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="4544c-142">Estabilidade e taxa de quadros do holograma</span><span class="sxs-lookup"><span data-stu-id="4544c-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="4544c-143">Orçamento de desempenho do ativo</span><span class="sxs-lookup"><span data-stu-id="4544c-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="4544c-144">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="4544c-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4544c-145">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="4544c-145">Tools and tutorials</span></span>

* [<span data-ttu-id="4544c-146">Kit de ferramentas de realidade misturada, exibição do contador de FPS</span><span class="sxs-lookup"><span data-stu-id="4544c-146">Mixed Reality Toolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="4544c-147">Kit de ferramentas de realidade misturada, sombreadores</span><span class="sxs-lookup"><span data-stu-id="4544c-147">Mixed Reality Toolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="4544c-148">Referências externas</span><span class="sxs-lookup"><span data-stu-id="4544c-148">External references</span></span>

* [<span data-ttu-id="4544c-149">Unity, otimizando aplicativos móveis</span><span class="sxs-lookup"><span data-stu-id="4544c-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="4544c-150">Estabilidade do holograma</span><span class="sxs-lookup"><span data-stu-id="4544c-150">Hologram stability</span></span>

<span data-ttu-id="4544c-151">Os hologramas estáveis aumentarão a usabilidade e a believability de seu aplicativo e criarão uma experiência de exibição mais confortável para o usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="4544c-152">A qualidade da estabilidade do holograma é um resultado do bom desenvolvimento de aplicativos e da capacidade do dispositivo de entender (controlar) seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="4544c-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="4544c-153">Embora a taxa de quadros seja o primeiro pilar da estabilidade, outros fatores podem afetar a estabilidade, incluindo:</span><span class="sxs-lookup"><span data-stu-id="4544c-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="4544c-154">Uso do plano de estabilização</span><span class="sxs-lookup"><span data-stu-id="4544c-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="4544c-155">Distâncias para âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="4544c-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="4544c-156">Acompanhamento</span><span class="sxs-lookup"><span data-stu-id="4544c-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="4544c-157">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4544c-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4544c-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4544c-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4544c-160">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4544c-161">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="4544c-161">Quality criteria</span></span>

|  <span data-ttu-id="4544c-162">Melhor</span><span class="sxs-lookup"><span data-stu-id="4544c-162">Best</span></span>  |  <span data-ttu-id="4544c-163">Corresponde</span><span class="sxs-lookup"><span data-stu-id="4544c-163">Meets</span></span> |  <span data-ttu-id="4544c-164">Falha</span><span class="sxs-lookup"><span data-stu-id="4544c-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4544c-165">Os hologramas parecem consistentemente estáveis.</span><span class="sxs-lookup"><span data-stu-id="4544c-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="4544c-166">Conteúdo secundário mostra movimento inesperado; ou o movimento inesperado não impede a experiência geral do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4544c-166">Secondary content shows unexpected movement; or unexpected movement doesn't impede overall app experience.</span></span> | <span data-ttu-id="4544c-167">O conteúdo primário no quadro mostra movimento inesperado.</span><span class="sxs-lookup"><span data-stu-id="4544c-167">Primary content in frame shows unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="4544c-168">Como medir</span><span class="sxs-lookup"><span data-stu-id="4544c-168">How to measure</span></span>

<span data-ttu-id="4544c-169">Ao desgastar o dispositivo e exibir a experiência:</span><span class="sxs-lookup"><span data-stu-id="4544c-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="4544c-170">Mova seu cabeçalho de lado a lado.</span><span class="sxs-lookup"><span data-stu-id="4544c-170">Move your head from side to side.</span></span> <span data-ttu-id="4544c-171">Se os hologramas mostrarem o movimento inesperado, a taxa de quadros baixa ou o alinhamento impróprio do plano de estabilidade para o plano focal será a causa provável.</span><span class="sxs-lookup"><span data-stu-id="4544c-171">If the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="4544c-172">Mova-se para os hologramas e o ambiente, procure comportamentos como, por exemplo, nada e salto.</span><span class="sxs-lookup"><span data-stu-id="4544c-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="4544c-173">Esse tipo de movimento é provavelmente causado pelo dispositivo não rastreando o ambiente ou pela distância para a âncora espacial.</span><span class="sxs-lookup"><span data-stu-id="4544c-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="4544c-174">Se houver grandes ou vários hologramas no quadro, observe o comportamento do holograma em várias profundidades ao mover sua posição de cabeçalho de lado a lado, se shakiness parecer que isso é provavelmente causado pelo plano de estabilização.</span><span class="sxs-lookup"><span data-stu-id="4544c-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4544c-175">Recomendações</span><span class="sxs-lookup"><span data-stu-id="4544c-175">Recommendations</span></span>

* <span data-ttu-id="4544c-176">Adicione um contador de taxa de quadros no início do trabalho de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="4544c-176">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="4544c-177">Use o plano de estabilização.</span><span class="sxs-lookup"><span data-stu-id="4544c-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="4544c-178">Sempre renderizar hologramas ancorados dentro de 3 metros de sua âncora.</span><span class="sxs-lookup"><span data-stu-id="4544c-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="4544c-179">Verifique se o ambiente está configurado para acompanhamento adequado.</span><span class="sxs-lookup"><span data-stu-id="4544c-179">Make sure your environment is set up for proper tracking.</span></span>
* <span data-ttu-id="4544c-180">Projete sua experiência para evitar hologramas em vários níveis de profundidade focal dentro do quadro.</span><span class="sxs-lookup"><span data-stu-id="4544c-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="4544c-181">Recursos</span><span class="sxs-lookup"><span data-stu-id="4544c-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4544c-182">Documentação</span><span class="sxs-lookup"><span data-stu-id="4544c-182">Documentation</span></span>

* [<span data-ttu-id="4544c-183">Estabilidade e taxa de quadros do holograma</span><span class="sxs-lookup"><span data-stu-id="4544c-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="4544c-184">Estudo de caso, usando o plano de estabilização</span><span class="sxs-lookup"><span data-stu-id="4544c-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="4544c-185">Entendendo o desempenho da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="4544c-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="4544c-186">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="4544c-186">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="4544c-187">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="4544c-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="4544c-188">Manipulação de erros de controle</span><span class="sxs-lookup"><span data-stu-id="4544c-188">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="4544c-189">Quadro estacionário de referência</span><span class="sxs-lookup"><span data-stu-id="4544c-189">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4544c-190">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="4544c-190">Tools and tutorials</span></span>

* [<span data-ttu-id="4544c-191">Sr Companion Kit, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="4544c-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="4544c-192">Posição dos hologramas em superfícies reais</span><span class="sxs-lookup"><span data-stu-id="4544c-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="4544c-193">Os desalinhamentos de hologramas com objetos físicos (se a intenção de serem colocados em relação uns aos outros) são uma indicação clara da não União de hologramas e do mundo real.</span><span class="sxs-lookup"><span data-stu-id="4544c-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) are a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="4544c-194">A precisão do posicionamento deve ser relativa às necessidades do cenário; por exemplo, o posicionamento de superfície geral pode usar o mapa espacial, mas o posicionamento mais preciso exigirá algum uso de marcadores e calibragem.</span><span class="sxs-lookup"><span data-stu-id="4544c-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4544c-195">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4544c-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4544c-196"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-196"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4544c-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4544c-198">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-198">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4544c-199">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="4544c-199">Quality criteria</span></span>

|  <span data-ttu-id="4544c-200">Melhor</span><span class="sxs-lookup"><span data-stu-id="4544c-200">Best</span></span>  |  <span data-ttu-id="4544c-201">Corresponde</span><span class="sxs-lookup"><span data-stu-id="4544c-201">Meets</span></span> |  <span data-ttu-id="4544c-202">Falha</span><span class="sxs-lookup"><span data-stu-id="4544c-202">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="4544c-203">Os hologramas se alinham à superfície normalmente no intervalo de centímetros para polegadas.</span><span class="sxs-lookup"><span data-stu-id="4544c-203">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="4544c-204">Se você precisar de mais precisão, o aplicativo deverá fornecer um meio eficiente de colaboração na especificação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4544c-204">If you need more accuracy, the app should provide an efficient means for collaboration within the app spec.</span></span> | <span data-ttu-id="4544c-205">NA</span><span class="sxs-lookup"><span data-stu-id="4544c-205">NA</span></span> | <span data-ttu-id="4544c-206">Os hologramas aparecem desalinhados com o objeto de destino físico, dividindo o plano de superfície ou aparecendo flutuando para fora da superfície.</span><span class="sxs-lookup"><span data-stu-id="4544c-206">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="4544c-207">Se a precisão for necessária, os hologramas devem atender à especificação de proximidade do cenário.</span><span class="sxs-lookup"><span data-stu-id="4544c-207">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4544c-208">Como medir</span><span class="sxs-lookup"><span data-stu-id="4544c-208">How to measure</span></span>

* <span data-ttu-id="4544c-209">Os hologramas que são colocados no mapa espacial não devem parecer muito flutuar acima ou abaixo da superfície.</span><span class="sxs-lookup"><span data-stu-id="4544c-209">Holograms that are placed on spatial map shouldn't appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="4544c-210">Os hologramas que exigem posicionamento preciso devem ter alguma forma de marcador e sistema de calibração que seja precisa do requisito do cenário.</span><span class="sxs-lookup"><span data-stu-id="4544c-210">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4544c-211">Recomendações</span><span class="sxs-lookup"><span data-stu-id="4544c-211">Recommendations</span></span>

* <span data-ttu-id="4544c-212">O mapa espacial é útil para colocar objetos em superfícies quando a precisão não é necessária.</span><span class="sxs-lookup"><span data-stu-id="4544c-212">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="4544c-213">Para obter a melhor precisão, use marcadores ou cartazes para definir os hologramas e um controlador Xbox (ou algum mecanismo de alinhamento manual) para a calibragem final.</span><span class="sxs-lookup"><span data-stu-id="4544c-213">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="4544c-214">Considere quebrar hologramas grandes e extras em partes lógicas e alinhar cada parte à superfície.</span><span class="sxs-lookup"><span data-stu-id="4544c-214">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="4544c-215">O IPD (Interpupillary Distance) definido incorretamente também pode afetar o alinhamento do holograma.</span><span class="sxs-lookup"><span data-stu-id="4544c-215">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="4544c-216">Sempre configure o HoloLens para o IPD do usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-216">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="4544c-217">Recursos</span><span class="sxs-lookup"><span data-stu-id="4544c-217">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4544c-218">Documentação</span><span class="sxs-lookup"><span data-stu-id="4544c-218">Documentation</span></span>

* [<span data-ttu-id="4544c-219">Posicionamento de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="4544c-219">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="4544c-220">Processo de verificação de sala</span><span class="sxs-lookup"><span data-stu-id="4544c-220">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="4544c-221">Práticas recomendadas das âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="4544c-221">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="4544c-222">Manipulação de erros de controle</span><span class="sxs-lookup"><span data-stu-id="4544c-222">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="4544c-223">Mapeamento espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="4544c-223">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="4544c-224">Visão geral do desenvolvimento do Vuforia</span><span class="sxs-lookup"><span data-stu-id="4544c-224">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4544c-225">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="4544c-225">Tools and tutorials</span></span>

* [<span data-ttu-id="4544c-226">Sr Toolkit, bibliotecas de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="4544c-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="4544c-227">Sr Companion Kit, exemplo de calibração de pôster</span><span class="sxs-lookup"><span data-stu-id="4544c-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="4544c-228">Sr Companion Kit, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="4544c-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="4544c-229">Referências externas</span><span class="sxs-lookup"><span data-stu-id="4544c-229">External references</span></span>

* [<span data-ttu-id="4544c-230">Estudo de caso do Lowes, alinhamento de precisão</span><span class="sxs-lookup"><span data-stu-id="4544c-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="4544c-231">Exibindo a zona de conforto</span><span class="sxs-lookup"><span data-stu-id="4544c-231">Viewing zone of comfort</span></span>

<span data-ttu-id="4544c-232">Os desenvolvedores de aplicativos controlam onde os olhos dos usuários convergem colocando o conteúdo e os hologramas em várias profundidades.</span><span class="sxs-lookup"><span data-stu-id="4544c-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="4544c-233">Os usuários com o HoloLens serão sempre acomodados a 2,0 m para manter uma imagem clara porque as exibições do HoloLens são corrigidas a uma distância óptica de aproximadamente 2,0 m para fora do usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-233">Users wearing HoloLens will always accommodate to 2.0 m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0 m away from the user.</span></span> <span data-ttu-id="4544c-234">A profundidade de conteúdo inadequado pode levar ao Visual discomfort ou fadiga.</span><span class="sxs-lookup"><span data-stu-id="4544c-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4544c-235">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4544c-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4544c-236"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-236"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4544c-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4544c-238">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4544c-239">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="4544c-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="4544c-240">Melhor</span><span class="sxs-lookup"><span data-stu-id="4544c-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="4544c-241">Coloque o conteúdo em 2 m.</span><span class="sxs-lookup"><span data-stu-id="4544c-241">Place content at 2 m.</span></span></li><li><span data-ttu-id="4544c-242">Quando os hologramas não podem ser colocados em 2 m e os conflitos entre a convergência e a acomodação não podem ser evitados, a zona ideal para o posicionamento do holograma é entre 1,25 m e 5 m.</span><span class="sxs-lookup"><span data-stu-id="4544c-242">When holograms cannot be placed at 2 m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25 m and 5 m.</span></span></li><li><span data-ttu-id="4544c-243">Em todos os casos, os designers devem estruturar o conteúdo para incentivar os usuários a interagir de 1 + m (por exemplo, ajustar o tamanho do conteúdo e os parâmetros de posicionamento padrão).</span><span class="sxs-lookup"><span data-stu-id="4544c-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="4544c-244">A menos que não seja exigido pelo cenário, um plano de recorte deve ser implementado com fade out a partir de 1 m.</span><span class="sxs-lookup"><span data-stu-id="4544c-244">Unless not required by the scenario, a clipping plane should be implement with fade out starting at 1 m.</span></span></li><li><span data-ttu-id="4544c-245">Nos casos em que a observação mais próxima de um holograma não-movimento é necessária, o conteúdo não deve ficar mais próximo que 50 cm.</span><span class="sxs-lookup"><span data-stu-id="4544c-245">In cases where closer observation of a motionless hologram is required, the content shouldn't be closer than 50 cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="4544c-246">Corresponde</span><span class="sxs-lookup"><span data-stu-id="4544c-246">Meets</span></span></td><td> <span data-ttu-id="4544c-247">O conteúdo está dentro das diretrizes de visualização e movimentação, mas uso inadequado ou não uso do plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="4544c-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="4544c-248">Falha</span><span class="sxs-lookup"><span data-stu-id="4544c-248">Fail</span></span> </td><td> <span data-ttu-id="4544c-249">O conteúdo é apresentado muito próximo (geralmente &lt; , 1,25 m ou &lt; 50 cm para hologramas estáticos que exigem uma observação mais detalhada.)</span><span class="sxs-lookup"><span data-stu-id="4544c-249">Content is presented too close (typically &lt;1.25 m, or &lt;50 cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="4544c-250">Como medir</span><span class="sxs-lookup"><span data-stu-id="4544c-250">How to measure</span></span>

* <span data-ttu-id="4544c-251">O conteúdo deve ser normalmente de 2 m, mas não mais que 1,25 ou superior a 5 m.</span><span class="sxs-lookup"><span data-stu-id="4544c-251">Content should typically be 2 m away, but no closer than 1.25 or further than 5 m.</span></span>
* <span data-ttu-id="4544c-252">Com poucas exceções, a distância de renderização de recorte de HoloLens deve ser definida como 85CM com fade out do conteúdo começando em 1 m.</span><span class="sxs-lookup"><span data-stu-id="4544c-252">With few exceptions, the HoloLens clipping render distance should be set to 85CM with fade out of content starting at 1 m.</span></span> <span data-ttu-id="4544c-253">Aborde o conteúdo e observe o efeito do plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="4544c-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="4544c-254">O conteúdo estacionário não deve ficar mais próximo que 50 cm.</span><span class="sxs-lookup"><span data-stu-id="4544c-254">Stationary content should not be closer than 50 cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4544c-255">Recomendações</span><span class="sxs-lookup"><span data-stu-id="4544c-255">Recommendations</span></span>

* <span data-ttu-id="4544c-256">Crie conteúdo para a distância de exibição ideal de 2 m.</span><span class="sxs-lookup"><span data-stu-id="4544c-256">Design content for the optimal viewing distance of 2 m.</span></span>
* <span data-ttu-id="4544c-257">Defina a distância de renderização de recorte como 85 cm com fade out do conteúdo começando em 1 m.</span><span class="sxs-lookup"><span data-stu-id="4544c-257">Set the clipping render distance to 85 cm with fade out of content starting at 1 m.</span></span>
* <span data-ttu-id="4544c-258">Para hologramas estáticos que precisam de exibição mais próxima, o plano de recorte não deve ter mais de 30 cm e desaparecer deve iniciar pelo menos 10 cm fora do plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="4544c-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30 cm and fade out should start at least 10 cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="4544c-259">Recursos</span><span class="sxs-lookup"><span data-stu-id="4544c-259">Resources</span></span>

* [<span data-ttu-id="4544c-260">Distância de renderização</span><span class="sxs-lookup"><span data-stu-id="4544c-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="4544c-261">Ponto de foco no Unity</span><span class="sxs-lookup"><span data-stu-id="4544c-261">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="4544c-262">Experimentando a escala</span><span class="sxs-lookup"><span data-stu-id="4544c-262">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="4544c-263">Texto, tamanho de fonte recomendado</span><span class="sxs-lookup"><span data-stu-id="4544c-263">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="4544c-264">Alternância de profundidade</span><span class="sxs-lookup"><span data-stu-id="4544c-264">Depth switching</span></span>

<span data-ttu-id="4544c-265">Independentemente da exibição da zona de problemas de conforto, as demandas pelo usuário de alternar com frequência ou rapidamente entre objetos focalmente próximos e distantes (incluindo hologramas e conteúdo do mundo real) podem levar a oculomotor fadiga e discomfort geral.</span><span class="sxs-lookup"><span data-stu-id="4544c-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4544c-266">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4544c-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4544c-267"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-267"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4544c-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4544c-269">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-269">✔️</span></span></td>
        <td><span data-ttu-id="4544c-270">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4544c-271">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="4544c-271">Quality criteria</span></span>

|  <span data-ttu-id="4544c-272">Melhor</span><span class="sxs-lookup"><span data-stu-id="4544c-272">Best</span></span>  |  <span data-ttu-id="4544c-273">Corresponde</span><span class="sxs-lookup"><span data-stu-id="4544c-273">Meets</span></span> |  <span data-ttu-id="4544c-274">Falha</span><span class="sxs-lookup"><span data-stu-id="4544c-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4544c-275">Alternância de profundidade limitada ou natural que não faz com que o usuário se concentre de volta natural.</span><span class="sxs-lookup"><span data-stu-id="4544c-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="4544c-276">A mudança de profundidade abrupta é fundamental e projetada para a experiência do aplicativo ou para o interruptor de profundidade abrupta que é causado pelo conteúdo real do mundo inesperado.</span><span class="sxs-lookup"><span data-stu-id="4544c-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="4544c-277">Opção de profundidade consistente ou alternância de profundidade abrupta que não é necessária ou essencial para a experiência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4544c-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4544c-278">Como medir</span><span class="sxs-lookup"><span data-stu-id="4544c-278">How to measure</span></span>

* <span data-ttu-id="4544c-279">Se o aplicativo exigir que o usuário altere o foco de profundidade de forma consistente e/ou abruptamente, haverá um problema de alternância de profundidade.</span><span class="sxs-lookup"><span data-stu-id="4544c-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4544c-280">Recomendações</span><span class="sxs-lookup"><span data-stu-id="4544c-280">Recommendations</span></span>

* <span data-ttu-id="4544c-281">Mantenha o conteúdo principal em um plano focal consistente e verifique se o plano de estabilização corresponde ao plano focal.</span><span class="sxs-lookup"><span data-stu-id="4544c-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="4544c-282">Isso aliviará o oculomotor fadiga e o movimento de holograma inesperado.</span><span class="sxs-lookup"><span data-stu-id="4544c-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="4544c-283">Recursos</span><span class="sxs-lookup"><span data-stu-id="4544c-283">Resources</span></span>

* [<span data-ttu-id="4544c-284">Distância de renderização</span><span class="sxs-lookup"><span data-stu-id="4544c-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="4544c-285">Ponto de foco no Unity</span><span class="sxs-lookup"><span data-stu-id="4544c-285">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="4544c-286">Uso de som espacial</span><span class="sxs-lookup"><span data-stu-id="4544c-286">Use of spatial sound</span></span>

<span data-ttu-id="4544c-287">No Windows Mixed Reality, o mecanismo de áudio fornece o componente auricular da experiência de realidade misturada por meio da simulação de som 3D usando a direção, a distância e as simulações ambientais.</span><span class="sxs-lookup"><span data-stu-id="4544c-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="4544c-288">O uso de som espacial em um aplicativo permite que os desenvolvedores coloquem os sons de forma convincente em um espaço tridimensional (esfera) em todo o usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3-dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="4544c-289">Esses sons parecerão como se estivessem vindo de objetos físicos reais ou de hologramas de realidade misturada no ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="4544c-290">O som espacial é uma ferramenta poderosa para imersão, acessibilidade e design de UX em aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="4544c-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4544c-291">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4544c-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4544c-292"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-292"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4544c-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4544c-294">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-294">✔️</span></span></td>
        <td><span data-ttu-id="4544c-295">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4544c-296">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="4544c-296">Quality criteria</span></span>

|  <span data-ttu-id="4544c-297">Melhor</span><span class="sxs-lookup"><span data-stu-id="4544c-297">Best</span></span>  |  <span data-ttu-id="4544c-298">Corresponde</span><span class="sxs-lookup"><span data-stu-id="4544c-298">Meets</span></span> |  <span data-ttu-id="4544c-299">Falha</span><span class="sxs-lookup"><span data-stu-id="4544c-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4544c-300">O som é logicamente espacial e o UX usa o som adequadamente para auxiliar na descoberta de objetos e nos comentários dos usuários.</span><span class="sxs-lookup"><span data-stu-id="4544c-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="4544c-301">O som é natural e relevante para objetos e normalizados em todo o cenário.</span><span class="sxs-lookup"><span data-stu-id="4544c-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="4544c-302">O áudio espacial é usado adequadamente para believability, mas ausente como meio de ajudar com os comentários do usuário e a descoberta.</span><span class="sxs-lookup"><span data-stu-id="4544c-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="4544c-303">O som não está espacial como esperado e/ou falta de som para auxiliar o usuário no UX.</span><span class="sxs-lookup"><span data-stu-id="4544c-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="4544c-304">Ou o áudio espacial não foi considerado ou usado no design do cenário.</span><span class="sxs-lookup"><span data-stu-id="4544c-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4544c-305">Como medir</span><span class="sxs-lookup"><span data-stu-id="4544c-305">How to measure</span></span>

* <span data-ttu-id="4544c-306">Em geral, os sons relevantes devem emitir de hologramas de destino (por exemplo, som latido proveniente do Holographic Dog.)</span><span class="sxs-lookup"><span data-stu-id="4544c-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="4544c-307">As indicações de som devem ser usadas em todo o UX para ajudar o usuário com comentários ou conscientização de ações fora do quadro do Holographic.</span><span class="sxs-lookup"><span data-stu-id="4544c-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4544c-308">Recomendações</span><span class="sxs-lookup"><span data-stu-id="4544c-308">Recommendations</span></span>

* <span data-ttu-id="4544c-309">Use o áudio espacial para auxiliar na descoberta de objeto e nas interfaces do usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="4544c-310">Os sons reais funcionam melhor que o sintetizado ou o som não natural.</span><span class="sxs-lookup"><span data-stu-id="4544c-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="4544c-311">A maioria dos sons deve ser espacial.</span><span class="sxs-lookup"><span data-stu-id="4544c-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="4544c-312">Evite emissores invisíveis.</span><span class="sxs-lookup"><span data-stu-id="4544c-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="4544c-313">Evite mascaramento espacial.</span><span class="sxs-lookup"><span data-stu-id="4544c-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="4544c-314">Normalizar todos os sons.</span><span class="sxs-lookup"><span data-stu-id="4544c-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="4544c-315">Recursos</span><span class="sxs-lookup"><span data-stu-id="4544c-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4544c-316">Documentação</span><span class="sxs-lookup"><span data-stu-id="4544c-316">Documentation</span></span>

* [<span data-ttu-id="4544c-317">Som espacial</span><span class="sxs-lookup"><span data-stu-id="4544c-317">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="4544c-318">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="4544c-318">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="4544c-319">Som espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="4544c-319">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="4544c-320">Estudo de caso, som espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="4544c-320">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="4544c-321">Estudo de caso, usando o som espacial em RoboRaid</span><span class="sxs-lookup"><span data-stu-id="4544c-321">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4544c-322">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="4544c-322">Tools and tutorials</span></span>

* [<span data-ttu-id="4544c-323">Kit de ferramentas de realidade misturada – áudio espacial</span><span class="sxs-lookup"><span data-stu-id="4544c-323">Mixed Reality Toolkit - Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="4544c-324">Foco nos limites do quadro Holographic (FOV)</span><span class="sxs-lookup"><span data-stu-id="4544c-324">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="4544c-325">Experiências de usuário bem projetadas podem criar e manter um contexto útil do ambiente virtual que se estende pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="4544c-325">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="4544c-326">Reduzir o efeito dos limites de FOV envolve um design elaborado de escala e contexto de conteúdo, uso de áudio espacial, sistemas de orientação e posição do usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-326">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="4544c-327">Se for feito certo, o usuário se sentirá menos prejudicado pelos limites do FOV enquanto tem uma experiência de aplicativo confortável.</span><span class="sxs-lookup"><span data-stu-id="4544c-327">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4544c-328">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4544c-328">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4544c-329"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-329"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4544c-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4544c-331">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-331">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4544c-332">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="4544c-332">Quality criteria</span></span>

|  <span data-ttu-id="4544c-333">Melhor</span><span class="sxs-lookup"><span data-stu-id="4544c-333">Best</span></span>  |  <span data-ttu-id="4544c-334">Corresponde</span><span class="sxs-lookup"><span data-stu-id="4544c-334">Meets</span></span> |  <span data-ttu-id="4544c-335">Falha</span><span class="sxs-lookup"><span data-stu-id="4544c-335">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4544c-336">O usuário nunca perde o contexto e a exibição é confortável.</span><span class="sxs-lookup"><span data-stu-id="4544c-336">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="4544c-337">A assistência de contexto é fornecida para objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="4544c-337">Context assistance is provided for large objects.</span></span> <span data-ttu-id="4544c-338">As diretrizes de descoberta e exibição são fornecidas para objetos fora do quadro.</span><span class="sxs-lookup"><span data-stu-id="4544c-338">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="4544c-339">Em geral, o design de movimento e a escala dos hologramas são apropriados para uma experiência de exibição confortável.</span><span class="sxs-lookup"><span data-stu-id="4544c-339">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="4544c-340">O usuário nunca perde o contexto, mas o movimento de pescoço extra pode ser necessário em situações limitadas.</span><span class="sxs-lookup"><span data-stu-id="4544c-340">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="4544c-341">Em situações limitadas, a escala faz com que os hologramas quebrem o quadro vertical ou horizontal, fazendo com que um movimento de pescoço exiba os hologramas.</span><span class="sxs-lookup"><span data-stu-id="4544c-341">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="4544c-342">O usuário provavelmente perderá o contexto e/ou o movimento de pescoço consistente é necessário para exibir hologramas.</span><span class="sxs-lookup"><span data-stu-id="4544c-342">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="4544c-343">Não há diretrizes de contexto para objetos Holographic grandes, movendo objetos fáceis de serem perdidos fora do quadro sem orientação de descoberta ou hologramas altos requer movimento de pescoço regular para exibição.</span><span class="sxs-lookup"><span data-stu-id="4544c-343">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4544c-344">Como medir</span><span class="sxs-lookup"><span data-stu-id="4544c-344">How to measure</span></span>

* <span data-ttu-id="4544c-345">O contexto de um holograma (grande) é perdido ou não compreendido devido a ser recortado nos limites.</span><span class="sxs-lookup"><span data-stu-id="4544c-345">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="4544c-346">É difícil encontrar locais de hologramas devido à falta de diretores de atenção ou conteúdo que se movem rapidamente para dentro e para fora do quadro Holographic.</span><span class="sxs-lookup"><span data-stu-id="4544c-346">Locations of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="4544c-347">O cenário requer um movimento regular e repetitivo para cima e para baixo para ver totalmente um holograma, resultando em fadiga de pescoço.</span><span class="sxs-lookup"><span data-stu-id="4544c-347">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4544c-348">Recomendações</span><span class="sxs-lookup"><span data-stu-id="4544c-348">Recommendations</span></span>

* <span data-ttu-id="4544c-349">Inicie a experiência com objetos pequenos que se ajustam ao FOV e, em seguida, migre com indicações visuais para versões maiores.</span><span class="sxs-lookup"><span data-stu-id="4544c-349">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="4544c-350">Use os diretores espaciais de áudio e atenção para ajudar o usuário a encontrar conteúdo fora do FOV.</span><span class="sxs-lookup"><span data-stu-id="4544c-350">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="4544c-351">Tanto quanto possível, evite hologramas que recortem verticalmente o FOV.</span><span class="sxs-lookup"><span data-stu-id="4544c-351">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="4544c-352">Forneça ao usuário diretrizes no aplicativo para melhor localização de exibição.</span><span class="sxs-lookup"><span data-stu-id="4544c-352">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="4544c-353">Recursos</span><span class="sxs-lookup"><span data-stu-id="4544c-353">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4544c-354">Documentação</span><span class="sxs-lookup"><span data-stu-id="4544c-354">Documentation</span></span>

* [<span data-ttu-id="4544c-355">Quadro holográfico</span><span class="sxs-lookup"><span data-stu-id="4544c-355">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="4544c-356">Estudo de caso, interface do usuário do HoloStudio e aprendizado de design de interação</span><span class="sxs-lookup"><span data-stu-id="4544c-356">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="4544c-357">Escala de objetos e ambientes</span><span class="sxs-lookup"><span data-stu-id="4544c-357">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="4544c-358">Cursores, indicações visuais</span><span class="sxs-lookup"><span data-stu-id="4544c-358">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="4544c-359">Referências externas</span><span class="sxs-lookup"><span data-stu-id="4544c-359">External references</span></span>

* [<span data-ttu-id="4544c-360">Muito ado sobre o FOV</span><span class="sxs-lookup"><span data-stu-id="4544c-360">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="4544c-361">O conteúdo reage à posição do usuário</span><span class="sxs-lookup"><span data-stu-id="4544c-361">Content reacts to user position</span></span>

<span data-ttu-id="4544c-362">Os hologramas devem reagir à posição do usuário praticamente da mesma maneira que os objetos "reais".</span><span class="sxs-lookup"><span data-stu-id="4544c-362">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="4544c-363">Uma consideração de design notável são os elementos da interface do usuário que não podem, necessariamente, supor que a posição dos usuários seja imóvel e se adapte ao movimento do usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-363">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="4544c-364">A criação de um aplicativo que se adapta corretamente à posição do usuário criará uma experiência mais verossímeis e facilitará o uso.</span><span class="sxs-lookup"><span data-stu-id="4544c-364">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4544c-365">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4544c-365">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4544c-366"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-366"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4544c-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4544c-368">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-368">✔️</span></span></td>
        <td><span data-ttu-id="4544c-369">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-369">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4544c-370">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="4544c-370">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="4544c-371">Melhor</span><span class="sxs-lookup"><span data-stu-id="4544c-371">Best</span></span> </td><td> <span data-ttu-id="4544c-372">O conteúdo e a interface do usuário se adaptam às posições dos usuários, permitindo que o usuário interaja naturalmente com o conteúdo dentro do escopo do movimento de usuário esperado.</span><span class="sxs-lookup"><span data-stu-id="4544c-372">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="4544c-373">Corresponde</span><span class="sxs-lookup"><span data-stu-id="4544c-373">Meets</span></span> </td><td> <span data-ttu-id="4544c-374">A IU se adapta à posição do usuário, mas pode impedir a exibição do conteúdo da chave que exige que o usuário ajuste sua posição.</span><span class="sxs-lookup"><span data-stu-id="4544c-374">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="4544c-375">Falha</span><span class="sxs-lookup"><span data-stu-id="4544c-375">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="4544c-376">Os elementos da interface do usuário são perdidos ou bloqueados durante a movimentação, fazendo com que o usuário volte de volta para (ou localize) controles.</span><span class="sxs-lookup"><span data-stu-id="4544c-376">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="4544c-377">Os elementos da interface do usuário limitam a exibição do conteúdo primário.</span><span class="sxs-lookup"><span data-stu-id="4544c-377">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="4544c-378">O movimento da interface do usuário não é otimizado para exibir a distância e a dinâmica particularmente com elementos de interface do usuário com <a href="../../design/billboarding-and-tag-along.md">marcas</a> .</span><span class="sxs-lookup"><span data-stu-id="4544c-378">UI movement isn't optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="4544c-379">Como medir</span><span class="sxs-lookup"><span data-stu-id="4544c-379">How to measure</span></span>

* <span data-ttu-id="4544c-380">Todas as medidas devem ser feitas dentro de um escopo razoável do cenário.</span><span class="sxs-lookup"><span data-stu-id="4544c-380">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="4544c-381">Embora a movimentação do usuário varie, não tente enganar o aplicativo com movimento extremo do usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-381">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="4544c-382">Para elementos de interface do usuário, os controles relevantes devem estar disponíveis independentemente do movimento do usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-382">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="4544c-383">Por exemplo, se o usuário estiver exibindo e percorrendo um mapa 3D com zoom, o controle de zoom deverá estar prontamente disponível para o usuário, independentemente do local.</span><span class="sxs-lookup"><span data-stu-id="4544c-383">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4544c-384">Recomendações</span><span class="sxs-lookup"><span data-stu-id="4544c-384">Recommendations</span></span>

* <span data-ttu-id="4544c-385">O usuário é a câmera e controla o movimento.</span><span class="sxs-lookup"><span data-stu-id="4544c-385">The user is the camera and they control the movement.</span></span> <span data-ttu-id="4544c-386">Deixe-os na unidade.</span><span class="sxs-lookup"><span data-stu-id="4544c-386">Let them drive.</span></span>
* <span data-ttu-id="4544c-387">Considere a mensagem para os sistemas de texto e de menu que, de outra forma, seriam bloqueados no mundo, se um usuário fosse se movimentando.</span><span class="sxs-lookup"><span data-stu-id="4544c-387">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="4544c-388">Use uma marca para o conteúdo que precisa seguir o usuário enquanto ainda permite que o usuário veja o que está na frente deles.</span><span class="sxs-lookup"><span data-stu-id="4544c-388">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="4544c-389">Recursos</span><span class="sxs-lookup"><span data-stu-id="4544c-389">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4544c-390">Documentação</span><span class="sxs-lookup"><span data-stu-id="4544c-390">Documentation</span></span>

* [<span data-ttu-id="4544c-391">Design de interação</span><span class="sxs-lookup"><span data-stu-id="4544c-391">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="4544c-392">Cor, luz e material</span><span class="sxs-lookup"><span data-stu-id="4544c-392">Color, light, and material</span></span>](../../color,-light-and-materials.md)
* [<span data-ttu-id="4544c-393">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="4544c-393">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="4544c-394">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="4544c-394">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="4544c-395">Automovimento e locomoção do usuário</span><span class="sxs-lookup"><span data-stu-id="4544c-395">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="4544c-396">Clareza da interação de entrada</span><span class="sxs-lookup"><span data-stu-id="4544c-396">Input interaction clarity</span></span>

<span data-ttu-id="4544c-397">A clareza da interação de entrada é essencial para a usabilidade de um aplicativo e inclui consistência de entrada, capacidade de detecção, descoberta de métodos de interação.</span><span class="sxs-lookup"><span data-stu-id="4544c-397">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="4544c-398">O usuário pode usar interações comuns em toda a plataforma sem reaprender.</span><span class="sxs-lookup"><span data-stu-id="4544c-398">User can use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="4544c-399">Se o aplicativo tiver uma entrada personalizada, ele deverá ser claramente comunicado e demonstrado.</span><span class="sxs-lookup"><span data-stu-id="4544c-399">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4544c-400">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4544c-400">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4544c-401"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-401"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4544c-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4544c-403">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-403">✔️</span></span></td>
        <td><span data-ttu-id="4544c-404">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-404">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4544c-405">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="4544c-405">Quality criteria</span></span>

|  <span data-ttu-id="4544c-406">Melhor</span><span class="sxs-lookup"><span data-stu-id="4544c-406">Best</span></span>  |  <span data-ttu-id="4544c-407">Corresponde</span><span class="sxs-lookup"><span data-stu-id="4544c-407">Meets</span></span> |  <span data-ttu-id="4544c-408">Falha</span><span class="sxs-lookup"><span data-stu-id="4544c-408">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4544c-409">Os métodos de interação de entrada são consistentes com as [diretrizes](../../design/interaction-fundamentals.md)do Windows Mixed Reality fornecidas.</span><span class="sxs-lookup"><span data-stu-id="4544c-409">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="4544c-410">Qualquer entrada personalizada não deve ser redundante com entrada padrão (em vez disso, usar a interação padrão) e deve ser claramente comunicada e demonstrada para o usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-410">Any custom input shouldn't be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="4544c-411">Semelhante à melhor, mas as entradas personalizadas são redundantes com métodos de entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="4544c-411">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="4544c-412">O usuário ainda pode alcançar a meta e o progresso por meio da experiência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4544c-412">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="4544c-413">É difícil entender o método de entrada ou o mapeamento de botão.</span><span class="sxs-lookup"><span data-stu-id="4544c-413">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="4544c-414">A entrada é bastante personalizada, não dá suporte à entrada padrão, não há instruções ou provavelmente causar problemas de fadiga e conforto.</span><span class="sxs-lookup"><span data-stu-id="4544c-414">Input is heavily customized, doesn't support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4544c-415">Como medir</span><span class="sxs-lookup"><span data-stu-id="4544c-415">How to measure</span></span>

* <span data-ttu-id="4544c-416">O aplicativo usa [métodos de entrada padrão](../../design/interaction-fundamentals.md) consistentes.</span><span class="sxs-lookup"><span data-stu-id="4544c-416">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="4544c-417">Se o aplicativo tiver uma entrada personalizada, ele será claramente comunicado por meio de:</span><span class="sxs-lookup"><span data-stu-id="4544c-417">If the app has custom input, it's clearly communicated through:</span></span>
* <span data-ttu-id="4544c-418">Experiência de primeira execução</span><span class="sxs-lookup"><span data-stu-id="4544c-418">First-run experience</span></span>
* <span data-ttu-id="4544c-419">Telas introdutórias</span><span class="sxs-lookup"><span data-stu-id="4544c-419">Introductory screens</span></span>
* <span data-ttu-id="4544c-420">Dicas de ferramenta</span><span class="sxs-lookup"><span data-stu-id="4544c-420">Tooltips</span></span>
* <span data-ttu-id="4544c-421">Orientador de mão</span><span class="sxs-lookup"><span data-stu-id="4544c-421">Hand coach</span></span>
* <span data-ttu-id="4544c-422">Seção de ajuda</span><span class="sxs-lookup"><span data-stu-id="4544c-422">Help section</span></span>
* <span data-ttu-id="4544c-423">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="4544c-423">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="4544c-424">Recomendações</span><span class="sxs-lookup"><span data-stu-id="4544c-424">Recommendations</span></span>

* <span data-ttu-id="4544c-425">Use métodos de entrada padrão sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="4544c-425">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="4544c-426">Forneça demonstrações, tutoriais e dicas de ferramenta para métodos de entrada não padrão.</span><span class="sxs-lookup"><span data-stu-id="4544c-426">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="4544c-427">Use um modelo de interação consistente em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4544c-427">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="4544c-428">Recursos</span><span class="sxs-lookup"><span data-stu-id="4544c-428">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4544c-429">Documentação</span><span class="sxs-lookup"><span data-stu-id="4544c-429">Documentation</span></span>

* [<span data-ttu-id="4544c-430">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="4544c-430">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="4544c-431">Objetos que interagem</span><span class="sxs-lookup"><span data-stu-id="4544c-431">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="4544c-432">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="4544c-432">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="4544c-433">Cursores</span><span class="sxs-lookup"><span data-stu-id="4544c-433">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="4544c-434">Conforto e olhar</span><span class="sxs-lookup"><span data-stu-id="4544c-434">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="4544c-435">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="4544c-435">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="4544c-436">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="4544c-436">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="4544c-437">Guia de portabilidade de entrada para Unity</span><span class="sxs-lookup"><span data-stu-id="4544c-437">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="4544c-438">Entrada do teclado no Unity</span><span class="sxs-lookup"><span data-stu-id="4544c-438">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="4544c-439">Foco no Unity</span><span class="sxs-lookup"><span data-stu-id="4544c-439">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="4544c-440">Gestos e controladores de movimento no Unity</span><span class="sxs-lookup"><span data-stu-id="4544c-440">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="4544c-441">Entrada de voz no Unity</span><span class="sxs-lookup"><span data-stu-id="4544c-441">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="4544c-442">Teclado, mouse e entrada do controlador no DirectX</span><span class="sxs-lookup"><span data-stu-id="4544c-442">Keyboard, mouse, and controller input in DirectX</span></span>](../../keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="4544c-443">Olhar fixo com cabeça e olhos no DirectX</span><span class="sxs-lookup"><span data-stu-id="4544c-443">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="4544c-444">Controladores de mãos e emovimento no DirectX</span><span class="sxs-lookup"><span data-stu-id="4544c-444">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="4544c-445">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="4544c-445">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4544c-446">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="4544c-446">Tools and tutorials</span></span>

* [<span data-ttu-id="4544c-447">Estudo de caso: a busca de mais computação pessoal</span><span class="sxs-lookup"><span data-stu-id="4544c-447">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="4544c-448">Estudo de conversão: aprendizado de HoloStudio de interface do usuário e interação do projeto</span><span class="sxs-lookup"><span data-stu-id="4544c-448">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="4544c-449">Aplicativo de exemplo: tabela periódica dos elementos</span><span class="sxs-lookup"><span data-stu-id="4544c-449">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="4544c-450">Aplicativo de exemplo: módulo lunar</span><span class="sxs-lookup"><span data-stu-id="4544c-450">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="4544c-451">Objetos que interagem</span><span class="sxs-lookup"><span data-stu-id="4544c-451">Interactable objects</span></span>

<span data-ttu-id="4544c-452">Um botão tem muito tempo uma metáfora usada para disparar um evento no mundo abstrato de 2D.</span><span class="sxs-lookup"><span data-stu-id="4544c-452">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="4544c-453">No mundo de realidade misturada tridimensional, não precisamos mais ser confinado para esse mundo de abstração.</span><span class="sxs-lookup"><span data-stu-id="4544c-453">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="4544c-454">Qualquer coisa pode ser um objeto que possa ser interagindo que dispara um evento.</span><span class="sxs-lookup"><span data-stu-id="4544c-454">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="4544c-455">Um objeto de interação pode ser representado como qualquer coisa de uma xícara de café na mesa até um balão flutuante no ar.</span><span class="sxs-lookup"><span data-stu-id="4544c-455">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="4544c-456">Independentemente do formulário, os objetos interajantes devem ser claramente reconhecidos pelo usuário por meio de indicações visuais e de áudio.</span><span class="sxs-lookup"><span data-stu-id="4544c-456">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4544c-457">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4544c-457">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4544c-458"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-458"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4544c-459"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-459"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4544c-460">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-460">✔️</span></span></td>
        <td><span data-ttu-id="4544c-461">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-461">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4544c-462">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="4544c-462">Quality criteria</span></span>

|  <span data-ttu-id="4544c-463">Melhor</span><span class="sxs-lookup"><span data-stu-id="4544c-463">Best</span></span>  |  <span data-ttu-id="4544c-464">Corresponde</span><span class="sxs-lookup"><span data-stu-id="4544c-464">Meets</span></span> |  <span data-ttu-id="4544c-465">Falha</span><span class="sxs-lookup"><span data-stu-id="4544c-465">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4544c-466">Independentemente do formulário, os objetos que podem interagir são reconhecidos por meio de indicações visuais e de áudio em três Estados: ocioso, direcionado e selecionado.</span><span class="sxs-lookup"><span data-stu-id="4544c-466">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="4544c-467">"Vê-lo, digamos que" é claro e consistentemente usado em toda a experiência.</span><span class="sxs-lookup"><span data-stu-id="4544c-467">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="4544c-468">Os objetos são dimensionados e distribuídos para permitir o direcionamento livre de erros.</span><span class="sxs-lookup"><span data-stu-id="4544c-468">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="4544c-469">O usuário pode reconhecer o objeto como interagindo por meio de áudio ou comentários visuais e pode direcionar e ativar o objeto.</span><span class="sxs-lookup"><span data-stu-id="4544c-469">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="4544c-470">Não devido a indicações visuais ou de áudio, o usuário não consegue reconhecer um objeto que pode ser interagindo.</span><span class="sxs-lookup"><span data-stu-id="4544c-470">Given no visual or audio cues, user can't recognize an interactable object.</span></span> <span data-ttu-id="4544c-471">As interações são propensas a erros devido à escala ou à distância do objeto entre objetos.</span><span class="sxs-lookup"><span data-stu-id="4544c-471">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4544c-472">Como medir</span><span class="sxs-lookup"><span data-stu-id="4544c-472">How to measure</span></span>

* <span data-ttu-id="4544c-473">Os objetos que podem interagir são reconhecíveis como ' interagindo '; incluindo botões, menus e conteúdo específico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4544c-473">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app-specific content.</span></span> <span data-ttu-id="4544c-474">Como regra prática, deve haver um Visual e uma indicação de áudio ao direcionar objetos que podem interagir.</span><span class="sxs-lookup"><span data-stu-id="4544c-474">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4544c-475">Recomendações</span><span class="sxs-lookup"><span data-stu-id="4544c-475">Recommendations</span></span>

* <span data-ttu-id="4544c-476">Use comentários visuais e de áudio para interações.</span><span class="sxs-lookup"><span data-stu-id="4544c-476">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="4544c-477">Os comentários visuais devem ser diferenciados para cada Estado de entrada (ocioso, direcionado, selecionado)</span><span class="sxs-lookup"><span data-stu-id="4544c-477">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="4544c-478">Os objetos que podem ser interagindo devem ser dimensionados e colocados para direcionamento de erro livre.</span><span class="sxs-lookup"><span data-stu-id="4544c-478">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="4544c-479">Objetos de interação agrupada (como uma barra de menus ou lista) devem ter o espaçamento adequado para o direcionamento.</span><span class="sxs-lookup"><span data-stu-id="4544c-479">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="4544c-480">Os botões e menus que dão suporte ao comando de voz devem fornecer rótulos de texto para a palavra-chave Command ("vê-lo, digamos")</span><span class="sxs-lookup"><span data-stu-id="4544c-480">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="4544c-481">Recursos</span><span class="sxs-lookup"><span data-stu-id="4544c-481">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4544c-482">Documentação</span><span class="sxs-lookup"><span data-stu-id="4544c-482">Documentation</span></span>

* [<span data-ttu-id="4544c-483">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="4544c-483">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="4544c-484">Texto no Unity</span><span class="sxs-lookup"><span data-stu-id="4544c-484">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="4544c-485">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="4544c-485">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="4544c-486">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="4544c-486">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4544c-487">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="4544c-487">Tools and tutorials</span></span>

* [<span data-ttu-id="4544c-488">Kit de ferramentas de realidade misturada-UX</span><span class="sxs-lookup"><span data-stu-id="4544c-488">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="4544c-489">Verificação de sala</span><span class="sxs-lookup"><span data-stu-id="4544c-489">Room scanning</span></span>

<span data-ttu-id="4544c-490">Os aplicativos que exigem dados de mapeamento espacial dependem do dispositivo para coletar automaticamente esses dados ao longo do tempo e entre as sessões, à medida que o usuário explora seu ambiente com o dispositivo ativo.</span><span class="sxs-lookup"><span data-stu-id="4544c-490">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="4544c-491">A integridade e a qualidade desses dados dependem de vários fatores, incluindo a quantidade de explorações que o usuário fez, quanto tempo passou desde a exploração e se os objetos como mobília e portas foram movidos desde que o dispositivo examinou a área.</span><span class="sxs-lookup"><span data-stu-id="4544c-491">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="4544c-492">Muitos aplicativos analisarão os dados de mapeamento espacial no início da experiência para avaliar se o usuário deve executar etapas adicionais para melhorar a integridade e a qualidade do mapa espacial.</span><span class="sxs-lookup"><span data-stu-id="4544c-492">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="4544c-493">Se o usuário for solicitado a verificar o ambiente, as diretrizes claras devem ser fornecidas durante a experiência de verificação.</span><span class="sxs-lookup"><span data-stu-id="4544c-493">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4544c-494">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4544c-494">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4544c-495"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-495"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4544c-496"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-496"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4544c-497">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-497">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4544c-498">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="4544c-498">Quality criteria</span></span>

|  <span data-ttu-id="4544c-499">Melhor</span><span class="sxs-lookup"><span data-stu-id="4544c-499">Best</span></span>  |  <span data-ttu-id="4544c-500">Corresponde</span><span class="sxs-lookup"><span data-stu-id="4544c-500">Meets</span></span> |  <span data-ttu-id="4544c-501">Falha</span><span class="sxs-lookup"><span data-stu-id="4544c-501">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4544c-502">A visualização da malha espacial informa aos usuários que a verificação está em andamento.</span><span class="sxs-lookup"><span data-stu-id="4544c-502">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="4544c-503">O usuário sabe claramente o que fazer e quando a verificação é iniciada e interrompida.</span><span class="sxs-lookup"><span data-stu-id="4544c-503">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="4544c-504">A visualização da malha espacial é fornecida, mas o usuário pode não saber claramente o que fazer e nenhuma informação de progresso é fornecida.</span><span class="sxs-lookup"><span data-stu-id="4544c-504">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="4544c-505">Nenhuma visualização da malha.</span><span class="sxs-lookup"><span data-stu-id="4544c-505">No visualization of mesh.</span></span> <span data-ttu-id="4544c-506">Nenhuma informação de orientação fornecida ao usuário sobre onde procurar ou quando a verificação é iniciada/interrompida.</span><span class="sxs-lookup"><span data-stu-id="4544c-506">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="4544c-507">Como medir</span><span class="sxs-lookup"><span data-stu-id="4544c-507">How to measure</span></span>

* <span data-ttu-id="4544c-508">Durante uma verificação de sala necessária, as diretrizes de áudio e visuais são fornecidas, indicando onde procurar e quando iniciar e parar a verificação.</span><span class="sxs-lookup"><span data-stu-id="4544c-508">During a required room scan, visual and audio guidance are provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4544c-509">Recomendações</span><span class="sxs-lookup"><span data-stu-id="4544c-509">Recommendations</span></span>

* <span data-ttu-id="4544c-510">Indique quanto do volume total nos arredores dos usuários precisa fazer parte da experiência.</span><span class="sxs-lookup"><span data-stu-id="4544c-510">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="4544c-511">Comunique-se quando a verificação for iniciada e parada como um indicador de progresso.</span><span class="sxs-lookup"><span data-stu-id="4544c-511">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="4544c-512">Use uma visualização da malha durante a verificação.</span><span class="sxs-lookup"><span data-stu-id="4544c-512">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="4544c-513">Forneça visuais e indicações de áudio para incentivar o usuário a procurar e se movimentar pela sala.</span><span class="sxs-lookup"><span data-stu-id="4544c-513">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="4544c-514">Informe ao usuário onde ir para melhorar os dados.</span><span class="sxs-lookup"><span data-stu-id="4544c-514">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="4544c-515">Em muitos casos, pode ser melhor informar ao usuário o que eles precisam fazer (por exemplo, examinar o teto, examinar os móveis) para obter a qualidade de digitalização necessária.</span><span class="sxs-lookup"><span data-stu-id="4544c-515">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="4544c-516">Recursos</span><span class="sxs-lookup"><span data-stu-id="4544c-516">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4544c-517">Documentação</span><span class="sxs-lookup"><span data-stu-id="4544c-517">Documentation</span></span>

* [<span data-ttu-id="4544c-518">Visualização de varredura do ambiente</span><span class="sxs-lookup"><span data-stu-id="4544c-518">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="4544c-519">Estudo de caso: expandindo os recursos de mapeamento espacial do HoloLens</span><span class="sxs-lookup"><span data-stu-id="4544c-519">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="4544c-520">Estudo de caso: design de som espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="4544c-520">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="4544c-521">Estudo de caso: criando uma experiência de imersão em fragmentos</span><span class="sxs-lookup"><span data-stu-id="4544c-521">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4544c-522">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="4544c-522">Tools and tutorials</span></span>

* [<span data-ttu-id="4544c-523">Kit de ferramentas de realidade misturada-UX</span><span class="sxs-lookup"><span data-stu-id="4544c-523">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="4544c-524">Indicadores direcionais</span><span class="sxs-lookup"><span data-stu-id="4544c-524">Directional indicators</span></span>

<span data-ttu-id="4544c-525">Em um aplicativo de realidade misturada, o conteúdo pode estar fora do campo de exibição ou obstruído por objetos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="4544c-525">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="4544c-526">Um aplicativo bem projetado tornará mais fácil para o usuário encontrar conteúdo não visível.</span><span class="sxs-lookup"><span data-stu-id="4544c-526">A well-designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="4544c-527">Indicadores direcionais alertam um usuário sobre o conteúdo importante e fornecem orientação para o conteúdo relativo à posição do usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-527">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="4544c-528">As diretrizes para conteúdo não visível podem assumir a forma de emissores de som, setas direcionais ou indicações visuais diretas.</span><span class="sxs-lookup"><span data-stu-id="4544c-528">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4544c-529">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4544c-529">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4544c-530"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-530"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4544c-531"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-531"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4544c-532">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-532">✔️</span></span></td>
        <td><span data-ttu-id="4544c-533">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-533">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4544c-534">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="4544c-534">Quality criteria</span></span>

|  <span data-ttu-id="4544c-535">Melhor</span><span class="sxs-lookup"><span data-stu-id="4544c-535">Best</span></span>  |  <span data-ttu-id="4544c-536">Corresponde</span><span class="sxs-lookup"><span data-stu-id="4544c-536">Meets</span></span> |  <span data-ttu-id="4544c-537">Falha</span><span class="sxs-lookup"><span data-stu-id="4544c-537">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4544c-538">As indicações visuais e de áudio orientam diretamente o usuário ao conteúdo relevante fora do campo de exibição.</span><span class="sxs-lookup"><span data-stu-id="4544c-538">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="4544c-539">Uma seta ou algum indicador que aponta o usuário na direção geral do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4544c-539">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="4544c-540">O conteúdo relevante está fora do campo de exibição e uma orientação de localização ruim ou nenhuma é fornecida ao usuário.</span><span class="sxs-lookup"><span data-stu-id="4544c-540">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4544c-541">Como medir</span><span class="sxs-lookup"><span data-stu-id="4544c-541">How to measure</span></span>

* <span data-ttu-id="4544c-542">O conteúdo relevante fora do campo de exibição do usuário é detectável por meio de indicações visuais e/ou de áudio.</span><span class="sxs-lookup"><span data-stu-id="4544c-542">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4544c-543">Recomendações</span><span class="sxs-lookup"><span data-stu-id="4544c-543">Recommendations</span></span>

* <span data-ttu-id="4544c-544">Quando o conteúdo relevante está fora do campo de exibição do usuário, use indicadores direcionais e indicações de áudio para orientar o usuário no conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4544c-544">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="4544c-545">Em muitos casos, um guia visual direto é preferencial sobre setas direcionais.</span><span class="sxs-lookup"><span data-stu-id="4544c-545">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="4544c-546">Indicadores direcionais não devem ser incorporados ao cursor.</span><span class="sxs-lookup"><span data-stu-id="4544c-546">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="4544c-547">Recursos</span><span class="sxs-lookup"><span data-stu-id="4544c-547">Resources</span></span>

* [<span data-ttu-id="4544c-548">Quadro holográfico</span><span class="sxs-lookup"><span data-stu-id="4544c-548">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="4544c-549">Carregamento de dados</span><span class="sxs-lookup"><span data-stu-id="4544c-549">Data loading</span></span>

<span data-ttu-id="4544c-550">Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento.</span><span class="sxs-lookup"><span data-stu-id="4544c-550">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="4544c-551">Isso pode significar que o usuário não pode interagir com o aplicativo quando o indicador de progresso está visível e também pode indicar quanto tempo de espera pode ser.</span><span class="sxs-lookup"><span data-stu-id="4544c-551">It can mean that the user can't interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4544c-552">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4544c-552">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4544c-553"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-553"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4544c-554"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="4544c-554"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4544c-555">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-555">✔️</span></span></td>
        <td><span data-ttu-id="4544c-556">✔️</span><span class="sxs-lookup"><span data-stu-id="4544c-556">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4544c-557">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="4544c-557">Quality criteria</span></span>

|  <span data-ttu-id="4544c-558">Melhor</span><span class="sxs-lookup"><span data-stu-id="4544c-558">Best</span></span>  |  <span data-ttu-id="4544c-559">Corresponde</span><span class="sxs-lookup"><span data-stu-id="4544c-559">Meets</span></span> |  <span data-ttu-id="4544c-560">Falha</span><span class="sxs-lookup"><span data-stu-id="4544c-560">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4544c-561">Indicador visual animado, na forma de uma barra de progresso ou anel, mostrando o progresso durante qualquer carregamento ou processamento de dados.</span><span class="sxs-lookup"><span data-stu-id="4544c-561">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="4544c-562">O indicador visual fornece orientação sobre quanto tempo a espera pode ser.</span><span class="sxs-lookup"><span data-stu-id="4544c-562">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="4544c-563">O usuário é informado de que o carregamento de dados está em andamento, mas não há nenhuma indicação de quanto tempo a espera poderia ser.</span><span class="sxs-lookup"><span data-stu-id="4544c-563">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="4544c-564">Nenhum indicador de carregamento ou processo de dados para a tarefa demorando mais do que 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="4544c-564">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="4544c-565">Como medir</span><span class="sxs-lookup"><span data-stu-id="4544c-565">How to measure</span></span>

* <span data-ttu-id="4544c-566">Durante o carregamento de dados, verifique se não há nenhum estado em branco por mais de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="4544c-566">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4544c-567">Recomendações</span><span class="sxs-lookup"><span data-stu-id="4544c-567">Recommendations</span></span>

* <span data-ttu-id="4544c-568">Forneça um Animator de carregamento de dados mostrando o progresso em qualquer situação em que o usuário possa perceber que esse aplicativo está parado ou falhou.</span><span class="sxs-lookup"><span data-stu-id="4544c-568">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="4544c-569">Uma regra prática razoável é qualquer atividade de ' carregamento ' que pode levar mais de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="4544c-569">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="4544c-570">Recursos</span><span class="sxs-lookup"><span data-stu-id="4544c-570">Resources</span></span>

* [<span data-ttu-id="4544c-571">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="4544c-571">Displaying progress</span></span>](../../design/progress.md)
