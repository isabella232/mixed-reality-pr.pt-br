---
title: Foco com a cabeça e confirmação
description: Começar a trabalhar com o modelo de entrada de confirmação e com o olhar com a cabeça, incluindo o posicionamento, o posicionamento e a estabilização de destino.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Realidade Misturada, foco, direcionamento de foco, interação, design, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada, destino, foco, suavização
ms.openlocfilehash: 74f963a6b450d1fb7f1302886a01c12cf79ce28a
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196511"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="637b2-104">Foco com a cabeça e confirmação</span><span class="sxs-lookup"><span data-stu-id="637b2-104">Head-gaze and commit</span></span>

<span data-ttu-id="637b2-105">_O olhar com a cabeça_ e [](gaze-and-commit.md) a confirmação são um caso especial do modelo de entrada de olhar e confirmação que envolve o direcionamento de um objeto com a direção da cabeça dos usuários.</span><span class="sxs-lookup"><span data-stu-id="637b2-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="637b2-106">Você pode agir no destino com uma entrada secundária, como o toque de ar do gesto de mão ou o comando de voz "Selecionar".</span><span class="sxs-lookup"><span data-stu-id="637b2-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="637b2-107">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="637b2-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="637b2-108"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="637b2-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="637b2-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="637b2-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="637b2-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="637b2-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="637b2-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="637b2-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="637b2-112">Foco com a cabeça e confirmação</span><span class="sxs-lookup"><span data-stu-id="637b2-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="637b2-113">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="637b2-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="637b2-114">✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</span><span class="sxs-lookup"><span data-stu-id="637b2-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="637b2-115">➕ Opção alternativa</span><span class="sxs-lookup"><span data-stu-id="637b2-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="head-and-eye-tracking-design-concepts-demo"></a><span data-ttu-id="637b2-116">Demonstração de conceitos de design de acompanhamento ocular e de cabeça</span><span class="sxs-lookup"><span data-stu-id="637b2-116">Head and eye tracking design concepts demo</span></span>

<span data-ttu-id="637b2-117">Se você quiser ver os conceitos de design de acompanhamento de cabeça e de olho em ação, confira nossa demonstração de vídeo **Designing Holograms – Head Tracking and Eye Tracking** abaixo.</span><span class="sxs-lookup"><span data-stu-id="637b2-117">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="637b2-118">Quando terminar, continue para obter uma análise mais detalhada de tópicos específicos.</span><span class="sxs-lookup"><span data-stu-id="637b2-118">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="637b2-119">*Este vídeo foi tirado do aplicativo "Projetando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui.](https://aka.ms/dhapp)*</span><span class="sxs-lookup"><span data-stu-id="637b2-119">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="637b2-120">Dimensionamento e comentários sobre o alvo</span><span class="sxs-lookup"><span data-stu-id="637b2-120">Target sizing and feedback</span></span>

<span data-ttu-id="637b2-121">O vetor de olhar para a cabeça foi mostrado repetidamente para ser acessível para direcionamento fino, mas geralmente funciona melhor para direcionamento bruto– adquirir destinos maiores.</span><span class="sxs-lookup"><span data-stu-id="637b2-121">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="637b2-122">Tamanhos mínimos de destino de 1 a 1,5 graus permitem ações bem-sucedidas do usuário na maioria dos cenários, embora os destinos de 3 graus geralmente permitam maior velocidade.</span><span class="sxs-lookup"><span data-stu-id="637b2-122">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="637b2-123">O tamanho que o usuário tem como destino é efetivamente uma área 2D, mesmo para elementos 3D, o que quer que a projeção está voltada para eles deve ser a área de destino.</span><span class="sxs-lookup"><span data-stu-id="637b2-123">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="637b2-124">Fornecer alguma indicação de que um elemento está "ativo" (que o usuário está direcionando para ele) é útil.</span><span class="sxs-lookup"><span data-stu-id="637b2-124">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="637b2-125">Isso pode incluir tratamentos como efeitos visíveis de "foco", realçamentos de áudio ou cliques ou alinhamento claro de um cursor com um elemento.</span><span class="sxs-lookup"><span data-stu-id="637b2-125">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="637b2-126">![Tamanho ideal do alvo em uma distância de 2 metros](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="637b2-126">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="637b2-127">*Tamanho de destino ideal a uma distância de 2 metros*</span><span class="sxs-lookup"><span data-stu-id="637b2-127">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="637b2-128">![Um exemplo de realce de um objeto direcionado por foco](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="637b2-128">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="637b2-129">*Um exemplo de realce de um objeto direcionado por foco*</span><span class="sxs-lookup"><span data-stu-id="637b2-129">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="637b2-130">Posicionamento do alvo</span><span class="sxs-lookup"><span data-stu-id="637b2-130">Target placement</span></span>

<span data-ttu-id="637b2-131">Os usuários geralmente não conseguem localizar elementos de interface do usuário localizados muito altos ou baixos em seu campo de exibição.</span><span class="sxs-lookup"><span data-stu-id="637b2-131">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="637b2-132">A maior parte de sua atenção termina em áreas ao redor de seu foco principal, que está aproximadamente no nível do olho.</span><span class="sxs-lookup"><span data-stu-id="637b2-132">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="637b2-133">O posicionamento da maioria dos alvos em uma faixa razoável em torno do nível dos olhos pode ajudar.</span><span class="sxs-lookup"><span data-stu-id="637b2-133">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="637b2-134">Considerando a tendência para os usuários se concentrarem em uma área Visual relativamente pequena a qualquer momento (o cone de atenção de visão é de aproximadamente 10 graus), agrupar elementos da interface do usuário em conjunto com o grau relacionado conceitualmente pode usar comportamentos de encadeamento de atenção do item para o item, uma vez que um usuário move sua olhar por uma área.</span><span class="sxs-lookup"><span data-stu-id="637b2-134">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="637b2-135">Ao projetar a interface do usuário, tenha em mente a grande variação potencial no campo de visão entre o HoloLens e os headsets imersivos.</span><span class="sxs-lookup"><span data-stu-id="637b2-135">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="637b2-136">![Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="637b2-136">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="637b2-137&quot;>*Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer*</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;637b2-137&quot;>*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name=&quot;improving-targeting-behaviors&quot;></a><span data-ttu-id=&quot;637b2-138&quot;>Como melhorar os comportamentos de direcionamento</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;637b2-138&quot;>Improving targeting behaviors</span></span>

<span data-ttu-id=&quot;637b2-139&quot;>Se a intenção do usuário de direcionar algo puder ser determinada ou aproximada, pode ser útil aceitar tentativas de interação quase ausentes como se elas estivessem corretas corretamente.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;637b2-139&quot;>If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id=&quot;637b2-140&quot;>Aqui estão alguns métodos bem-sucedidos que podem ser incorporados em experiências de realidade misturada:</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;637b2-140&quot;>Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name=&quot;head-gaze-stabilization-gravity-wells&quot;></a><span data-ttu-id=&quot;637b2-141&quot;>Estabilização do foco com a cabeça (&quot;poços gravitacionais")</span><span class="sxs-lookup"><span data-stu-id="637b2-141">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="637b2-142">Isso deve ser ativado na maior parte das vezes.</span><span class="sxs-lookup"><span data-stu-id="637b2-142">This should be turned on most or all of the time.</span></span> <span data-ttu-id="637b2-143">Essa técnica remove a cabeça natural e as tremulações do pescoço que os usuários podem ter também movimento por causa de comportamentos de aparência e fala.</span><span class="sxs-lookup"><span data-stu-id="637b2-143">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="637b2-144">Algoritmos de vínculo mais próximo</span><span class="sxs-lookup"><span data-stu-id="637b2-144">Closest link algorithms</span></span>

<span data-ttu-id="637b2-145">Esses algoritmos funcionam melhor em áreas com conteúdo interativo esparso.</span><span class="sxs-lookup"><span data-stu-id="637b2-145">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="637b2-146">Se houver uma alta probabilidade de que você possa determinar o que um usuário estava tentando interagir, você pode complementar seus recursos de direcionamento assumindo algum nível de intenção.</span><span class="sxs-lookup"><span data-stu-id="637b2-146">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="637b2-147">Ações de backencontros e de reencontros</span><span class="sxs-lookup"><span data-stu-id="637b2-147">Backdating and postdating actions</span></span>

<span data-ttu-id="637b2-148">Esse mecanismo é útil para tarefas que exigem velocidade.</span><span class="sxs-lookup"><span data-stu-id="637b2-148">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="637b2-149">Quando um usuário está passando por uma série de manobras de direcionamento e ativação em velocidade, é útil assumir alguma intenção.</span><span class="sxs-lookup"><span data-stu-id="637b2-149">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="637b2-150">Também é útil permitir que etapas perdidas atuem em destinos que o usuário tinha em foco um pouco antes ou ligeiramente após o toque (50 ms antes/depois era efetivo no teste inicial).</span><span class="sxs-lookup"><span data-stu-id="637b2-150">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="637b2-151">Suavização</span><span class="sxs-lookup"><span data-stu-id="637b2-151">Smoothing</span></span>

<span data-ttu-id="637b2-152">Esse mecanismo é útil para a trajetória de movimentos, reduzindo a ligeira tremulação e Wobbles devido a características de movimento de cabeçalho natural.</span><span class="sxs-lookup"><span data-stu-id="637b2-152">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="637b2-153">Ao suavizar movimentos de caminho, Smooth pelo tamanho e distância dos movimentos em vez de ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="637b2-153">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="637b2-154">Magnetismo</span><span class="sxs-lookup"><span data-stu-id="637b2-154">Magnetism</span></span>

<span data-ttu-id="637b2-155">Esse mecanismo pode ser considerado como uma versão mais comum dos algoritmos de link mais próximos, desenhando um cursor em direção a um destino ou simplesmente aumentando hitboxes, seja visivelmente ou não, à medida que os usuários abordam os alvos prováveis usando algum conhecimento do layout interativo para melhorar melhor a intenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="637b2-155">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="637b2-156">Isso pode ser poderoso para destinos pequenos.</span><span class="sxs-lookup"><span data-stu-id="637b2-156">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="637b2-157">Adesão do foco</span><span class="sxs-lookup"><span data-stu-id="637b2-157">Focus stickiness</span></span>

<span data-ttu-id="637b2-158">Ao determinar quais elementos interativos próximos dar, concentre-se, a mesmidade de foco fornece um desvio para o elemento que está focalizado no momento.</span><span class="sxs-lookup"><span data-stu-id="637b2-158">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="637b2-159">Isso ajuda a reduzir comportamentos de alternação de foco instável ao flutuar em um ponto médio entre dois elementos com ruído natural.</span><span class="sxs-lookup"><span data-stu-id="637b2-159">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="637b2-160">Confira também</span><span class="sxs-lookup"><span data-stu-id="637b2-160">See also</span></span>

* [<span data-ttu-id="637b2-161">Interação ocular</span><span class="sxs-lookup"><span data-stu-id="637b2-161">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="637b2-162">Focar e esperar</span><span class="sxs-lookup"><span data-stu-id="637b2-162">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="637b2-163">Mãos – Manipulação direta</span><span class="sxs-lookup"><span data-stu-id="637b2-163">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="637b2-164">Mãos – Gestos</span><span class="sxs-lookup"><span data-stu-id="637b2-164">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="637b2-165">Mãos – Apontar e confirmar</span><span class="sxs-lookup"><span data-stu-id="637b2-165">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="637b2-166">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="637b2-166">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="637b2-167">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="637b2-167">Voice input</span></span>](voice-input.md)