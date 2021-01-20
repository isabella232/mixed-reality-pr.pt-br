---
title: Foco com a cabeça e confirmação
description: Comece a usar o olhar e confirme o modelo de entrada, incluindo dimensionamento, posicionamento e estabilização de destino.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Realidade misturada, olhar, direcionamento de olhar, interação, design, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada, destino, foco, suavização
ms.openlocfilehash: a69b855e2246327affeeb0f771f565b94ea65cb2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582287"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="82239-104">Foco com a cabeça e confirmação</span><span class="sxs-lookup"><span data-stu-id="82239-104">Head-gaze and commit</span></span>

<span data-ttu-id="82239-105">_Head-olhar e commit_ é um caso especial do modelo de entrada [olhar e commit](gaze-and-commit.md) que envolve o direcionamento de um objeto com uma direção de cabeçalho de usuários.</span><span class="sxs-lookup"><span data-stu-id="82239-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="82239-106">Você pode agir no destino com uma entrada secundária, como o comando de voz do gesto de toque de mão ou "selecionar".</span><span class="sxs-lookup"><span data-stu-id="82239-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="82239-107">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="82239-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="82239-108"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="82239-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="82239-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="82239-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="82239-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="82239-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="82239-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="82239-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="82239-112">Foco com a cabeça e confirmação</span><span class="sxs-lookup"><span data-stu-id="82239-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="82239-113">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="82239-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="82239-114">✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</span><span class="sxs-lookup"><span data-stu-id="82239-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="82239-115">➕ Opção alternativa</span><span class="sxs-lookup"><span data-stu-id="82239-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="82239-116">Dimensionamento e comentários sobre o alvo</span><span class="sxs-lookup"><span data-stu-id="82239-116">Target sizing and feedback</span></span>

<span data-ttu-id="82239-117">O vetor olhar de cabeçalho foi mostrado repetidamente para ser usado para direcionamento fino, mas geralmente funciona melhor para direcionamento bruto, adquirindo destinos maiores.</span><span class="sxs-lookup"><span data-stu-id="82239-117">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="82239-118">Os tamanhos de destino mínimos de 1 grau a 1,5 graus permitem ações de usuário bem-sucedidas na maioria dos cenários, embora os destinos de 3 graus geralmente permitam maior velocidade.</span><span class="sxs-lookup"><span data-stu-id="82239-118">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="82239-119">O tamanho que o usuário tem como destino é efetivamente uma área 2D mesmo para elementos 3D – qualquer projeção que esteja voltado para eles deve ser a área de destino.</span><span class="sxs-lookup"><span data-stu-id="82239-119">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="82239-120">Fornecer uma indicação evidente de que um elemento é "ativo" (que o usuário está direcionando para ele) é útil.</span><span class="sxs-lookup"><span data-stu-id="82239-120">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="82239-121">Isso pode incluir tratamentos como efeitos "focalizar" visíveis, realces ou cliques de áudio ou alinhamento claro de um cursor com um elemento.</span><span class="sxs-lookup"><span data-stu-id="82239-121">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="82239-122">![Tamanho ideal do alvo em uma distância de 2 metros](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="82239-122">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="82239-123">*Tamanho de destino ideal em distância de 2 metros*</span><span class="sxs-lookup"><span data-stu-id="82239-123">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="82239-124">![Um exemplo de realce de um objeto direcionado por foco](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="82239-124">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="82239-125">*Um exemplo de realce de um objeto direcionado por foco*</span><span class="sxs-lookup"><span data-stu-id="82239-125">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="82239-126">Posicionamento do alvo</span><span class="sxs-lookup"><span data-stu-id="82239-126">Target placement</span></span>

<span data-ttu-id="82239-127">Geralmente, os usuários não conseguem localizar elementos da interface do usuário localizados muito altos ou baixos em seu campo de exibição.</span><span class="sxs-lookup"><span data-stu-id="82239-127">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="82239-128">A maioria das suas atenções acaba com as áreas em torno do foco principal, que é aproximadamente no nível dos olhos.</span><span class="sxs-lookup"><span data-stu-id="82239-128">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="82239-129">O posicionamento da maioria dos alvos em uma faixa razoável em torno do nível dos olhos pode ajudar.</span><span class="sxs-lookup"><span data-stu-id="82239-129">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="82239-130">Considerando a tendência para os usuários se concentrarem em uma área Visual relativamente pequena a qualquer momento (o cone de atenção de visão é de aproximadamente 10 graus), agrupar elementos da interface do usuário em conjunto com o grau relacionado conceitualmente pode usar comportamentos de encadeamento de atenção do item para o item, uma vez que um usuário move sua olhar por uma área.</span><span class="sxs-lookup"><span data-stu-id="82239-130">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="82239-131">Ao projetar a interface do usuário, tenha em mente a grande variação potencial no campo de visão entre o HoloLens e os headsets imersivos.</span><span class="sxs-lookup"><span data-stu-id="82239-131">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="82239-132">![Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="82239-132">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="82239-133">*Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer*</span><span class="sxs-lookup"><span data-stu-id="82239-133">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="82239-134">Como melhorar os comportamentos de direcionamento</span><span class="sxs-lookup"><span data-stu-id="82239-134">Improving targeting behaviors</span></span>

<span data-ttu-id="82239-135">Se a intenção do usuário de direcionar algo puder ser determinada ou aproximada, pode ser útil aceitar tentativas de interação quase ausentes como se elas estivessem corretas corretamente.</span><span class="sxs-lookup"><span data-stu-id="82239-135">If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id="82239-136">Aqui estão alguns métodos bem-sucedidos que podem ser incorporados em experiências de realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="82239-136">Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="82239-137">Estabilização do foco com a cabeça ("poços gravitacionais")</span><span class="sxs-lookup"><span data-stu-id="82239-137">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="82239-138">Isso deve ser ativado na maior parte das vezes.</span><span class="sxs-lookup"><span data-stu-id="82239-138">This should be turned on most or all of the time.</span></span> <span data-ttu-id="82239-139">Essa técnica remove a cabeça natural e as tremulações do pescoço que os usuários podem ter também movimento por causa de comportamentos de aparência e fala.</span><span class="sxs-lookup"><span data-stu-id="82239-139">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="82239-140">Algoritmos de vínculo mais próximo</span><span class="sxs-lookup"><span data-stu-id="82239-140">Closest link algorithms</span></span>

<span data-ttu-id="82239-141">Esses algoritmos funcionam melhor em áreas com conteúdo interativo esparso.</span><span class="sxs-lookup"><span data-stu-id="82239-141">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="82239-142">Se houver uma alta probabilidade de que você possa determinar o que um usuário estava tentando interagir, você pode complementar seus recursos de direcionamento assumindo algum nível de intenção.</span><span class="sxs-lookup"><span data-stu-id="82239-142">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="82239-143">Ações de backencontros e de reencontros</span><span class="sxs-lookup"><span data-stu-id="82239-143">Backdating and postdating actions</span></span>

<span data-ttu-id="82239-144">Esse mecanismo é útil para tarefas que exigem velocidade.</span><span class="sxs-lookup"><span data-stu-id="82239-144">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="82239-145">Quando um usuário está passando por uma série de manobras de direcionamento e ativação em velocidade, é útil assumir alguma intenção.</span><span class="sxs-lookup"><span data-stu-id="82239-145">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="82239-146">Também é útil permitir que etapas perdidas atuem em destinos que o usuário tinha em foco um pouco antes ou ligeiramente após o toque (50 ms antes/depois era efetivo no teste inicial).</span><span class="sxs-lookup"><span data-stu-id="82239-146">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="82239-147">Suavização</span><span class="sxs-lookup"><span data-stu-id="82239-147">Smoothing</span></span>

<span data-ttu-id="82239-148">Esse mecanismo é útil para a trajetória de movimentos, reduzindo a ligeira tremulação e Wobbles devido a características de movimento de cabeçalho natural.</span><span class="sxs-lookup"><span data-stu-id="82239-148">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="82239-149">Ao suavizar movimentos de caminho, Smooth pelo tamanho e distância dos movimentos em vez de ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="82239-149">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="82239-150">Magnetismo</span><span class="sxs-lookup"><span data-stu-id="82239-150">Magnetism</span></span>

<span data-ttu-id="82239-151">Esse mecanismo pode ser considerado como uma versão mais comum dos algoritmos de link mais próximos, desenhando um cursor em direção a um destino ou simplesmente aumentando hitboxes, seja visivelmente ou não, à medida que os usuários abordam os alvos prováveis usando algum conhecimento do layout interativo para melhorar melhor a intenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="82239-151">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="82239-152">Isso pode ser poderoso para destinos pequenos.</span><span class="sxs-lookup"><span data-stu-id="82239-152">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="82239-153">Adesão do foco</span><span class="sxs-lookup"><span data-stu-id="82239-153">Focus stickiness</span></span>

<span data-ttu-id="82239-154">Ao determinar quais elementos interativos adjacentes fornecem, concentre-se, a adesão do foco fornece uma tendência para o elemento que está atualmente focado.</span><span class="sxs-lookup"><span data-stu-id="82239-154">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="82239-155">Isso ajuda a reduzir os comportamentos incorretos de alternância de foco ao flutuar em um ponto médio entre dois elementos com ruído natural.</span><span class="sxs-lookup"><span data-stu-id="82239-155">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="82239-156">Confira também</span><span class="sxs-lookup"><span data-stu-id="82239-156">See also</span></span>

* [<span data-ttu-id="82239-157">Interação ocular</span><span class="sxs-lookup"><span data-stu-id="82239-157">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="82239-158">Focar e esperar</span><span class="sxs-lookup"><span data-stu-id="82239-158">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="82239-159">Mãos – Manipulação direta</span><span class="sxs-lookup"><span data-stu-id="82239-159">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="82239-160">Mãos – Gestos</span><span class="sxs-lookup"><span data-stu-id="82239-160">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="82239-161">Mãos – Apontar e confirmar</span><span class="sxs-lookup"><span data-stu-id="82239-161">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="82239-162">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="82239-162">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="82239-163">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="82239-163">Voice input</span></span>](voice-input.md)