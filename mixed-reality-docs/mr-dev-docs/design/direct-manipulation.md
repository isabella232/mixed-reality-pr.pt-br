---
title: Manipulação direta com as mãos
description: Saiba mais sobre a manipulação direta, um modelo de entrada no qual os usuários tocam os hologramas diretamente com as mãos.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, Foco, direcionamento de foco, interação, design, mãos perto, HoloLens, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, MRTK, Kit de Ferramentas de Realidade Misturada, botão, colisores, caixa delimitadora, 2D, gestos instintivos
ms.openlocfilehash: 7a689f887bfd358b0d6e0826d41ef409bf887042
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600465"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="f3881-104">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="f3881-104">Direct manipulation with hands</span></span>

![Botão](images/UX_Hero_Manipulation.jpg)

<span data-ttu-id="f3881-106">A manipulação direta é um modelo de entrada que envolve tocar hologramas diretamente com suas mãos.</span><span class="sxs-lookup"><span data-stu-id="f3881-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="f3881-107">A ideia por trás desse conceito é que os objetos se comportem exatamente como no mundo real.</span><span class="sxs-lookup"><span data-stu-id="f3881-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="f3881-108">Os botões podem ser ativados simplesmente pressionando-os, os objetos podem ser pegados e o conteúdo 2D se comporta como uma tela de toque virtual.</span><span class="sxs-lookup"><span data-stu-id="f3881-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="f3881-109">A manipulação direta é baseada em funcionalidade, o que significa que é amigável ao usuário.</span><span class="sxs-lookup"><span data-stu-id="f3881-109">Direct manipulation is affordance-based, meaning it's user-friendly.</span></span> <span data-ttu-id="f3881-110">Não há nenhum gesto simbólico para ensinar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="f3881-110">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="f3881-111">Todas as interações são criadas em torno de um elemento visual que você pode tocar ou pegar.</span><span class="sxs-lookup"><span data-stu-id="f3881-111">All interactions are built around a visual element that you can touch or grab.</span></span> <span data-ttu-id="f3881-112">Ela é considerada um modelo de entrada "próximo", ou seja, é mais adequado para interagir com o conteúdo que está no alcance dos braços.</span><span class="sxs-lookup"><span data-stu-id="f3881-112">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

## <a name="device-support"></a><span data-ttu-id="f3881-113">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="f3881-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="f3881-114"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="f3881-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="f3881-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3881-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="f3881-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3881-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
     <td><span data-ttu-id="f3881-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3881-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="f3881-118">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="f3881-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="f3881-119">❌ Sem suporte</span><span class="sxs-lookup"><span data-stu-id="f3881-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="f3881-120">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="f3881-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="f3881-121">➕ Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f3881-121">➕ Supported.</span></span>  <span data-ttu-id="f3881-122">Para a interface do usuário, recomendamos <a href="point-and-commit.md">apontar e confirmar com as mãos</a>.</span><span class="sxs-lookup"><span data-stu-id="f3881-122">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="f3881-123">A manipulação direta é um modelo de entrada primário no HoloLens 2, que usa o novo sistema articulado de acompanhamento com as mãos.</span><span class="sxs-lookup"><span data-stu-id="f3881-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="f3881-124">O modelo de entrada também está disponível nos headsets imersivos com o uso de controladores de movimentos, mas não é recomendado como o principal meio de interação além da manipulação de objetos.</span><span class="sxs-lookup"><span data-stu-id="f3881-124">The input model is also available on immersive headsets by using motion controllers, but isn't recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="f3881-125">A manipulação direta não está disponível no HoloLens (1ª geração).</span><span class="sxs-lookup"><span data-stu-id="f3881-125">Direct manipulation isn't available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="basic-hand-tracking-and-instinctual-interactions-demo"></a><span data-ttu-id="f3881-126">Demonstração do rastreamento básico de mãos e interações instintivas</span><span class="sxs-lookup"><span data-stu-id="f3881-126">Basic hand tracking and instinctual interactions demo</span></span>

<span data-ttu-id="f3881-127">Se quiser ver os conceitos de design de rastreamento da cabeça e dos olhos em ação, confira abaixo nosso vídeo de demonstração do **Projetando hologramas - Rastreamento da cabeça e rastreamento dos olhos**.</span><span class="sxs-lookup"><span data-stu-id="f3881-127">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="f3881-128">Depois de assistir ao vídeo, prossiga para saber mais sobre os tópicos específicos.</span><span class="sxs-lookup"><span data-stu-id="f3881-128">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

<span data-ttu-id="f3881-129">*Este vídeo foi retirado do aplicativo "Projetando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*</span><span class="sxs-lookup"><span data-stu-id="f3881-129">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="collidable-fingertip"></a><span data-ttu-id="f3881-130">Ponta do dedo colidente</span><span class="sxs-lookup"><span data-stu-id="f3881-130">Collidable fingertip</span></span>

<span data-ttu-id="f3881-131">No HoloLens 2, as mãos do usuário são reconhecidas e interpretadas como modelos estruturais esquerdo e direito.</span><span class="sxs-lookup"><span data-stu-id="f3881-131">On HoloLens 2, the user's hands are recognized and interpreted as left and right-hand skeletal models.</span></span> <span data-ttu-id="f3881-132">Para implementar a ideia de tocar hologramas diretamente com mãos, idealmente, cinco colisores podem ser anexados às pontas dos cinco dedos de cada modelo estrutural de mão.</span><span class="sxs-lookup"><span data-stu-id="f3881-132">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="f3881-133">No entanto, devido à falta de retorno tátil, dez pontas de dedo colidentes podem causar colisões inesperadas e imprevisíveis com os hologramas.</span><span class="sxs-lookup"><span data-stu-id="f3881-133">However, because of the lack of tactile feedback, 10 collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="f3881-134">Sugerimos colocar apenas um colisor em cada dedo indicador.</span><span class="sxs-lookup"><span data-stu-id="f3881-134">We suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="f3881-135">As pontas de dedo indicador colidentes ainda podem servir como pontos de toque ativos para diversos gestos de toque que envolvam outros dedos.</span><span class="sxs-lookup"><span data-stu-id="f3881-135">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers.</span></span> <span data-ttu-id="f3881-136">Os gestos de toque incluem pressionar com um dedo, tocar com um dedo, pressionar com dois dedos e pressionar com cinco dedos, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="f3881-136">Touch gestures include One-finger press, One-finger tap, Two-finger press, and Five-finger press, as shown below:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="f3881-137">![ponta do dedo colidente](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-137">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="f3881-138">**Ponta do dedo colidente**</span><span class="sxs-lookup"><span data-stu-id="f3881-138">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-139">![Pressionar com um dedo](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-139">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="f3881-140">**Pressionar com um dedo**</span><span class="sxs-lookup"><span data-stu-id="f3881-140">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-141">![Tocar com um dedo](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-141">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="f3881-142">**Tocar com um dedo**</span><span class="sxs-lookup"><span data-stu-id="f3881-142">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-143">![Pressionar com cinco dedos](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-143">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="f3881-144">**Pressionar com cinco dedos**</span><span class="sxs-lookup"><span data-stu-id="f3881-144">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="f3881-145">Colisor esférico</span><span class="sxs-lookup"><span data-stu-id="f3881-145">Sphere collider</span></span>

<span data-ttu-id="f3881-146">Em vez de usar uma forma genérica aleatória, sugerimos que você use um colisor esférico.</span><span class="sxs-lookup"><span data-stu-id="f3881-146">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="f3881-147">Em seguida, você pode renderizá-lo visualmente para fornecer indicações melhores para direcionamento próximo.</span><span class="sxs-lookup"><span data-stu-id="f3881-147">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="f3881-148">O diâmetro da esfera deve corresponder à espessura do dedo indicador para aumentar a precisão do toque.</span><span class="sxs-lookup"><span data-stu-id="f3881-148">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="f3881-149">É mais fácil recuperar a variável de espessura do dedo chamando a API da mão.</span><span class="sxs-lookup"><span data-stu-id="f3881-149">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="f3881-150">Cursor de ponta do dedo</span><span class="sxs-lookup"><span data-stu-id="f3881-150">Fingertip cursor</span></span>

<span data-ttu-id="f3881-151">Além de renderizar uma esfera colidente na ponta do dedo indicador, criamos um cursor avançado de ponta do dedo para obter uma melhor experiência de direcionamento próximo.</span><span class="sxs-lookup"><span data-stu-id="f3881-151">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to achieve a better near-targeting experience.</span></span> <span data-ttu-id="f3881-152">É um cursor em forma de rosca anexado à ponta do dedo indicador.</span><span class="sxs-lookup"><span data-stu-id="f3881-152">It's a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="f3881-153">De acordo com a proximidade, ele reage dinamicamente a um alvo em relação à orientação e ao tamanho, conforme detalhado abaixo:</span><span class="sxs-lookup"><span data-stu-id="f3881-153">According to proximity, it dynamically reacts to a target for orientation and size as detailed below:</span></span>

* <span data-ttu-id="f3881-154">Quando um dedo indicador se move em direção a um holograma, o cursor sempre fica paralelo à superfície do holograma e diminui gradualmente o tamanho.</span><span class="sxs-lookup"><span data-stu-id="f3881-154">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size.</span></span>
* <span data-ttu-id="f3881-155">Assim que o dedo toca a superfície, o cursor é reduzido a um ponto e emite um evento de toque.</span><span class="sxs-lookup"><span data-stu-id="f3881-155">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="f3881-156">Com o retorno interativo, os usuários podem realizar tarefas de direcionamento próximo com alta precisão, como disparar um hiperlink ou pressionar um botão, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="f3881-156">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="f3881-157">![Cursor de ponta do dedo distante](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-157">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="f3881-158">**Cursor de ponta do dedo distante**</span><span class="sxs-lookup"><span data-stu-id="f3881-158">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-159">![Cursor de ponta do dedo próximo](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-159">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="f3881-160">**Cursor de ponta do dedo próximo**</span><span class="sxs-lookup"><span data-stu-id="f3881-160">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-161">![Cursor de ponta do dedo com contato](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-161">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="f3881-162">**Cursor de ponta do dedo com contato**</span><span class="sxs-lookup"><span data-stu-id="f3881-162">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="f3881-163">Caixa delimitadora com o sombreador de proximidade</span><span class="sxs-lookup"><span data-stu-id="f3881-163">Bounding box with proximity shader</span></span>

<span data-ttu-id="f3881-164">O holograma em si também requer a capacidade de fornecer retorno visual e sonoro para compensar a falta do retorno tátil.</span><span class="sxs-lookup"><span data-stu-id="f3881-164">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="f3881-165">Para isso, criamos o conceito de uma caixa delimitadora com um sombreador de proximidade.</span><span class="sxs-lookup"><span data-stu-id="f3881-165">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="f3881-166">Uma caixa delimitadora é uma área volumétrica mínima que inclui um objeto 3D.</span><span class="sxs-lookup"><span data-stu-id="f3881-166">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="f3881-167">A caixa delimitadora tem um mecanismo de renderização interativo chamado de sombreador de proximidade.</span><span class="sxs-lookup"><span data-stu-id="f3881-167">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="f3881-168">O sombreador de proximidade se comporta da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f3881-168">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="f3881-169">![Focalizar (distante) com comentários visuais](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-169">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="f3881-170">**Focalizar (distante)**</span><span class="sxs-lookup"><span data-stu-id="f3881-170">**Hover (far)**</span></span><br>
       <span data-ttu-id="f3881-171">Quando o dedo indicador está em um intervalo, um destaque da ponta do dedo é mostrado na superfície da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="f3881-171">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-172">![Focalizar (próximo) com comentários visuais](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-172">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="f3881-173">**Focalizar (próximo)**</span><span class="sxs-lookup"><span data-stu-id="f3881-173">**Hover (near)**</span></span><br>
        <span data-ttu-id="f3881-174">Quando a ponta do dedo se aproxima da superfície, o destaque é reduzido.</span><span class="sxs-lookup"><span data-stu-id="f3881-174">When the fingertip gets closer to the surface, the spotlight shrinks.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-175">![O contato começa](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-175">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="f3881-176">**O contato começa**</span><span class="sxs-lookup"><span data-stu-id="f3881-176">**Contact begins**</span></span><br>
       <span data-ttu-id="f3881-177">Quando a ponta do dedo toca a superfície, toda a caixa delimitadora tem sua cor alterada ou gera efeitos visuais para refletir o estado de toque.</span><span class="sxs-lookup"><span data-stu-id="f3881-177">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-178">![O contato termina](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-178">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="f3881-179">**O contato termina**</span><span class="sxs-lookup"><span data-stu-id="f3881-179">**Contact ends**</span></span><br>
       <span data-ttu-id="f3881-180">Um efeito sonoro pode ser ativado para aprimorar o retorno visual do toque.</span><span class="sxs-lookup"><span data-stu-id="f3881-180">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="f3881-181">Botão de pressão</span><span class="sxs-lookup"><span data-stu-id="f3881-181">Pressable button</span></span>

<span data-ttu-id="f3881-182">Com uma ponta do dedo colidente, os usuários podem interagir com um componente holográfico da interface do usuário fundamental, como o botão de pressionar.</span><span class="sxs-lookup"><span data-stu-id="f3881-182">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="f3881-183">Um botão de pressão é um botão holográfico adaptado para o pressionar direto do dedo.</span><span class="sxs-lookup"><span data-stu-id="f3881-183">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="f3881-184">Novamente, devido à falta de retorno tátil, um botão de pressão ativa alguns mecanismos para lidar com os problemas relacionados ao retorno tátil.</span><span class="sxs-lookup"><span data-stu-id="f3881-184">Again, because of the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="f3881-185">O primeiro mecanismo é uma caixa delimitadora com um sombreador de proximidade, o qual é detalhado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="f3881-185">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="f3881-186">Ele fornece aos usuários uma melhor sensação de proximidade quando eles se aproximam e fazem contato com um botão.</span><span class="sxs-lookup"><span data-stu-id="f3881-186">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="f3881-187">O segundo mecanismo é o de liberação.</span><span class="sxs-lookup"><span data-stu-id="f3881-187">The second mechanism is depression.</span></span> <span data-ttu-id="f3881-188">A liberação cria uma ideia de pressionar para baixo depois da ponta de um dedo entrar em contato com um botão.</span><span class="sxs-lookup"><span data-stu-id="f3881-188">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="f3881-189">O mecanismo verifica se o botão se move intimamente com a ponta do dedo ao longo do eixo de profundidade.</span><span class="sxs-lookup"><span data-stu-id="f3881-189">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="f3881-190">O botão pode ser disparado quando atinge uma profundidade escolhida (ao ser pressionado) ou deixa a profundidade (ao ser liberado) depois de passar por ela.</span><span class="sxs-lookup"><span data-stu-id="f3881-190">The button can be triggered when it reaches a chosen depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="f3881-191">O efeito sonoro deve ser adicionado para melhorar o retorno quando o botão é disparado.</span><span class="sxs-lookup"><span data-stu-id="f3881-191">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="f3881-192">![botão de pressionar a distância](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-192">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="f3881-193">**O dedo está longe**</span><span class="sxs-lookup"><span data-stu-id="f3881-193">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-194">![botão de pressionar próximo](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-194">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="f3881-195">**O dedo se aproxima**</span><span class="sxs-lookup"><span data-stu-id="f3881-195">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-196">![o contato com o botão de pressionar começa](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-196">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="f3881-197">**O contato começa**</span><span class="sxs-lookup"><span data-stu-id="f3881-197">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-198">![pressionar o botão de pressionar](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-198">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="f3881-199">**Pressione**</span><span class="sxs-lookup"><span data-stu-id="f3881-199">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="f3881-200">Interação do slate 2D</span><span class="sxs-lookup"><span data-stu-id="f3881-200">2D slate interaction</span></span>

<span data-ttu-id="f3881-201">Um [slate](slate.md) 2D é um contêiner holográfico usado para hospedar o conteúdo do aplicativo 2D, assim como um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="f3881-201">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="f3881-202">O conceito de design para interagir com um slate 2D por meio da manipulação direta é o mesmo que interagir com uma tela touch física.</span><span class="sxs-lookup"><span data-stu-id="f3881-202">The design concept for interacting with a 2D slate via direct manipulation is the same as interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="f3881-203">Para interagir com o contato do slate</span><span class="sxs-lookup"><span data-stu-id="f3881-203">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="f3881-204">![Tocar](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-204">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="f3881-205">**Tocar**</span><span class="sxs-lookup"><span data-stu-id="f3881-205">**Touch**</span></span><br>
       <span data-ttu-id="f3881-206">Use o dedo indicador para pressionar um botão ou hiperlink.</span><span class="sxs-lookup"><span data-stu-id="f3881-206">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-207">![Rolar](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-207">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="f3881-208">**Rolar**</span><span class="sxs-lookup"><span data-stu-id="f3881-208">**Scroll**</span></span><br>
        <span data-ttu-id="f3881-209">Use o dedo indicador para rolar um slate de conteúdo para cima e para baixo.</span><span class="sxs-lookup"><span data-stu-id="f3881-209">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-210">![Aplicar zoom](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-210">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="f3881-211">**Aplicar zoom**</span><span class="sxs-lookup"><span data-stu-id="f3881-211">**Zoom**</span></span><br>
       <span data-ttu-id="f3881-212">O usuário usa os dois dedos indicadores para aumentar e diminuir o zoom no conteúdo do slate, de acordo com o movimento relativo dos dedos.</span><span class="sxs-lookup"><span data-stu-id="f3881-212">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="f3881-213">Para manipular o slate 2D em si</span><span class="sxs-lookup"><span data-stu-id="f3881-213">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="f3881-214">![Gráfico mostrando o recurso segurar e arrastar](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-214">![Graphic showing grab and drag feature](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="f3881-215">**Mover**</span><span class="sxs-lookup"><span data-stu-id="f3881-215">**Move**</span></span><br>
       <span data-ttu-id="f3881-216">Movimente suas mãos para os cantos e bordas para revelar as funcionalidades de manipulação mais próximas.</span><span class="sxs-lookup"><span data-stu-id="f3881-216">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="f3881-217">Segure a barra holográfica na parte superior do slate 2D, o que permite mover todo o slate.</span><span class="sxs-lookup"><span data-stu-id="f3881-217">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-218">![Gráfico mostrando o recurso de escala](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-218">![Graphic showing scale feature](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="f3881-219">**Dimensionar**</span><span class="sxs-lookup"><span data-stu-id="f3881-219">**Scale**</span></span><br>
        <span data-ttu-id="f3881-220">Segure as funcionalidades de manipulação e faça um dimensionamento uniforme utilizando as funcionalidades de canto.</span><span class="sxs-lookup"><span data-stu-id="f3881-220">Grab the manipulation affordances and do uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-221">![Refluxo](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-221">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="f3881-222">**Refluxo**</span><span class="sxs-lookup"><span data-stu-id="f3881-222">**Reflow**</span></span><br>
       <span data-ttu-id="f3881-223">Segure as funcionalidades de manipulação e faça um refluxo por meio das funcionalidades de borda.</span><span class="sxs-lookup"><span data-stu-id="f3881-223">Grab the manipulation affordances and do reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="f3881-224">Manipulação de objetos 3D</span><span class="sxs-lookup"><span data-stu-id="f3881-224">3D object manipulation</span></span>

<span data-ttu-id="f3881-225">O HoloLens 2 permite que os usuários habilitem suas mãos para orientar e manipular objetos holográficos 3D, aplicando uma caixa delimitadora a cada objeto 3D.</span><span class="sxs-lookup"><span data-stu-id="f3881-225">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="f3881-226">A caixa delimitadora fornece uma melhor percepção da profundidade por meio do sombreador de proximidade.</span><span class="sxs-lookup"><span data-stu-id="f3881-226">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="f3881-227">Com a caixa delimitadora, há duas abordagens de design para a manipulação de objetos 3D.</span><span class="sxs-lookup"><span data-stu-id="f3881-227">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="f3881-228">Manipulação baseada em funcionalidade</span><span class="sxs-lookup"><span data-stu-id="f3881-228">Affordance-based manipulation</span></span>

<span data-ttu-id="f3881-229">A manipulação com base em funcionalidade permite manipular o objeto 3D por meio de uma caixa delimitadora, junto com as funcionalidades de manipulação em torno dela.</span><span class="sxs-lookup"><span data-stu-id="f3881-229">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="f3881-230">![Gráfico mostrando uma caixa delimitadora de objetos e o recurso mover](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-230">![Graphic showing an objects bounding box and move feature](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="f3881-231">**Mover**</span><span class="sxs-lookup"><span data-stu-id="f3881-231">**Move**</span></span><br>
       <span data-ttu-id="f3881-232">Quando a mão de um usuário está próxima a um objeto 3D, a caixa delimitadora e a funcionalidade mais próxima são reveladas.</span><span class="sxs-lookup"><span data-stu-id="f3881-232">As soon as a user's hand is close to a 3D object, the bounding box, and the nearest affordance are revealed.</span></span> <span data-ttu-id="f3881-233">Os usuários podem segurar a caixa delimitadora para mover todo o objeto.</span><span class="sxs-lookup"><span data-stu-id="f3881-233">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-234">![Gráfico mostrando o usuário segurando a borda de um objeto para girá-lo](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-234">![Graphic showing user grabbing an objects edge to rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="f3881-235">**Girar**</span><span class="sxs-lookup"><span data-stu-id="f3881-235">**Rotate**</span></span><br>
        <span data-ttu-id="f3881-236">Os usuários podem segurar as funcionalidades de borda para girar.</span><span class="sxs-lookup"><span data-stu-id="f3881-236">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-237">![Gráfico mostrando o usuário segurando o canto de um objeto para dimensioná-lo](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-237">![Graphic showing user grabbing an objects corner to scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="f3881-238">**Dimensionar**</span><span class="sxs-lookup"><span data-stu-id="f3881-238">**Scale**</span></span><br>
       <span data-ttu-id="f3881-239">Os usuários podem segurar as funcionalidades de borda para dimensionar uniformemente.</span><span class="sxs-lookup"><span data-stu-id="f3881-239">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="f3881-240">Manipulação não baseada em funcionalidade</span><span class="sxs-lookup"><span data-stu-id="f3881-240">Non-affordance-based manipulation</span></span>

<span data-ttu-id="f3881-241">A manipulação que não é baseada em funcionalidade não anexa a funcionalidade à caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="f3881-241">Non-affordance-based manipulation doesn't attach affordance to the bounding box.</span></span> <span data-ttu-id="f3881-242">Os usuários podem revelar apenas a caixa delimitadora e interagir diretamente com ela.</span><span class="sxs-lookup"><span data-stu-id="f3881-242">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="f3881-243">Se a caixa delimitadora for pega com uma mão, a translação e rotação do objeto estarão associadas ao movimento e à orientação da mão.</span><span class="sxs-lookup"><span data-stu-id="f3881-243">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="f3881-244">Quando o objeto é pego com as duas mãos, os usuários podem transladá-lo, dimensioná-lo e girá-lo de acordo com os movimentos relativos das duas mãos.</span><span class="sxs-lookup"><span data-stu-id="f3881-244">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="f3881-245">A manipulação específica requer precisão.</span><span class="sxs-lookup"><span data-stu-id="f3881-245">Specific manipulation requires precision.</span></span> <span data-ttu-id="f3881-246">Recomendamos usar a **manipulação baseada em funcionalidade**, pois ela fornece um alto nível de granularidade.</span><span class="sxs-lookup"><span data-stu-id="f3881-246">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="f3881-247">Para a manipulação flexível, recomendamos usar a **manipulação não baseada em funcionalidade**, pois ela permite experiências instantâneas e divertidas.</span><span class="sxs-lookup"><span data-stu-id="f3881-247">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="f3881-248">Gestos instintuais</span><span class="sxs-lookup"><span data-stu-id="f3881-248">Instinctual gestures</span></span>

<span data-ttu-id="f3881-249">Com o HoloLens (1ª geração), ensinamos aos usuários alguns gestos predefinidos, como abrir a mão e fechar e abrir dedos indicador e polegar.</span><span class="sxs-lookup"><span data-stu-id="f3881-249">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="f3881-250">Para o HoloLens 2, não pedimos para os usuários memorizarem gestos simbólicos.</span><span class="sxs-lookup"><span data-stu-id="f3881-250">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="f3881-251">Todos os gestos exigidos do usuário, em que os usuários precisam interagir com os hologramas e o conteúdo, são instintivos.</span><span class="sxs-lookup"><span data-stu-id="f3881-251">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="f3881-252">A forma de atingir gestos instintuais é ajudar os usuários a realizar os gestos por meio do design de funcionalidades da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="f3881-252">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="f3881-253">Por exemplo, se nós incentivarmos o usuário a segurar um objeto ou um ponto de controle com uma pinçagem de dois dedos, o objeto ou o ponto de controle deverá ser pequeno.</span><span class="sxs-lookup"><span data-stu-id="f3881-253">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="f3881-254">Se quisermos que o usuário o segure com cinco dedos, o objeto ou o ponto de controle deverá ser relativamente grande.</span><span class="sxs-lookup"><span data-stu-id="f3881-254">If we want the user to do a five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="f3881-255">Como acontece com os botões, um botão pequeno limitará os usuários a pressioná-lo com um dedo.</span><span class="sxs-lookup"><span data-stu-id="f3881-255">Similar to buttons, a tiny button would limit users to press it with a single finger.</span></span> <span data-ttu-id="f3881-256">Um botão grande encorajará os usuários a pressioná-lo com a palma da mão.</span><span class="sxs-lookup"><span data-stu-id="f3881-256">A large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="f3881-257">![Gráfico mostrando o usuário segurando um objeto pequeno para movê-lo](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-257">![Graphic showing user grabbing small object to move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="f3881-258">**Objeto pequeno**</span><span class="sxs-lookup"><span data-stu-id="f3881-258">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-259">![Gráfico mostrando o usuário segurando um objeto médio para movê-lo](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-259">![Graphic showing user grabbing medium object to move](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="f3881-260">**Objeto médio**</span><span class="sxs-lookup"><span data-stu-id="f3881-260">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3881-261">![Gráfico mostrando o usuário segurando um objeto grande para movê-lo](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3881-261">![Graphic showing user grabbing large object to move](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="f3881-262">**Objeto grande**</span><span class="sxs-lookup"><span data-stu-id="f3881-262">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="f3881-263">Design simétrico entre os controladores de mão e DoF 6</span><span class="sxs-lookup"><span data-stu-id="f3881-263">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="f3881-264">Talvez você tenha observado que há interações paralelas que podemos utilizar entre as mãos em controladores de RA e de movimento na VR.</span><span class="sxs-lookup"><span data-stu-id="f3881-264">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="f3881-265">Ambas as entradas podem ser usadas para disparar manipulações diretas em seus respectivos ambientes.</span><span class="sxs-lookup"><span data-stu-id="f3881-265">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="f3881-266">No HoloLens 2, os movimentos de segurar e arrastar com mãos em distância próxima funcionam da mesma maneira que o botão para segurar nos controladores de movimentos do WMR.</span><span class="sxs-lookup"><span data-stu-id="f3881-266">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="f3881-267">Isso proporciona aos usuários uma familiaridade de interação entre as duas plataformas, o que poderá ser útil se você decidir portar seu aplicativo entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="f3881-267">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application between platforms.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="f3881-268">Otimizar com acompanhamento ocular</span><span class="sxs-lookup"><span data-stu-id="f3881-268">Optimize with eye tracking</span></span>

<span data-ttu-id="f3881-269">A manipulação direta poderá proporcionar uma sensação mágica se funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="f3881-269">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="f3881-270">No entanto, ela também poderá se tornar frustrante se você não puder mover sua mão para algum lugar sem disparar inadvertidamente um holograma.</span><span class="sxs-lookup"><span data-stu-id="f3881-270">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="f3881-271">O acompanhamento ocular ajuda potencialmente a identificar melhor qual é a intenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="f3881-271">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="f3881-272">**Quando**: reduzir o disparo involuntário de uma resposta de manipulação.</span><span class="sxs-lookup"><span data-stu-id="f3881-272">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="f3881-273">O acompanhamento ocular permite entender melhor o que um usuário realmente deseja fazer.</span><span class="sxs-lookup"><span data-stu-id="f3881-273">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="f3881-274">Por exemplo, imagine que você esteja lendo um texto (instrutivo) holográfico e se aproxime para pegar uma ferramenta de trabalho do mundo real.</span><span class="sxs-lookup"><span data-stu-id="f3881-274">For example, imagine you're reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="f3881-275">Ao fazer isso, você move acidentalmente sua mão sobre alguns botões holográficos interativos que não tinha observado antes.</span><span class="sxs-lookup"><span data-stu-id="f3881-275">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before.</span></span> <span data-ttu-id="f3881-276">Por exemplo, ela pode estar fora do FoV (campo de visão) do usuário.</span><span class="sxs-lookup"><span data-stu-id="f3881-276">For example, it  may be outside the user's field-of-view (FoV).</span></span>

<span data-ttu-id="f3881-277">Se o usuário não olhar um holograma por um tempo, mas um evento de toque ou aperto tiver sido detectado para ele, provavelmente, a interação não será intencional.</span><span class="sxs-lookup"><span data-stu-id="f3881-277">If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, the interaction is likely unintentional.</span></span>

* <span data-ttu-id="f3881-278">**Qual deles**:  além de lidar com ativações falso-positivas, outro exemplo inclui a melhor identificação dos hologramas a serem segurados ou tocados, já que o ponto de interseção preciso pode não ser claro da sua perspectiva, especialmente se vários hologramas estão posicionados próximos uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="f3881-278">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="f3881-279">Embora o acompanhamento ocular no HoloLens 2 tenha limitações com base na precisão com a que ele pode determinar seu foco com o olhar, isso ainda pode ser muito útil para interações próximas devido à disparidade de profundidade ao interagir com a entrada de mão.</span><span class="sxs-lookup"><span data-stu-id="f3881-279">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be helpful for near interactions because of depth disparity when interacting with hand input.</span></span> <span data-ttu-id="f3881-280">Isso significa que, às vezes, é difícil determinar se a sua mão está atrás ou na frente de um holograma para segurar precisamente um widget de manipulação, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="f3881-280">This means it's sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="f3881-281">**Onde**: usar informações sobre o que um usuário está vendo com gestos de lançamento rápido.</span><span class="sxs-lookup"><span data-stu-id="f3881-281">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="f3881-282">Segure um holograma e lance-o para seu destino pretendido.</span><span class="sxs-lookup"><span data-stu-id="f3881-282">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="f3881-283">Embora isso geralmente funcione bem, gestos de mão muito rápidos podem resultar em destinos altamente imprecisos.</span><span class="sxs-lookup"><span data-stu-id="f3881-283">While this sometimes works, quickly doing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="f3881-284">No entanto, o acompanhamento ocular poderia melhorar a precisão do gesto.</span><span class="sxs-lookup"><span data-stu-id="f3881-284">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="f3881-285">Manipulação no MRTK (Kit de Ferramentas de Realidade Misturada) para o Unity</span><span class="sxs-lookup"><span data-stu-id="f3881-285">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="f3881-286">Com o **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , você pode alcançar facilmente o comportamento de manipulação comum usando o script **ObjectManipulator**.</span><span class="sxs-lookup"><span data-stu-id="f3881-286">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="f3881-287">Com o ObjectManipulator, você pode pegar e mover objetos diretamente com mãos ou com o raio de mão.</span><span class="sxs-lookup"><span data-stu-id="f3881-287">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="f3881-288">Ele também dá suporte à manipulação com as duas mãos para dimensionar e girar um objeto.</span><span class="sxs-lookup"><span data-stu-id="f3881-288">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="f3881-289">MRTK – Manipulação</span><span class="sxs-lookup"><span data-stu-id="f3881-289">MRTK - Manipulation</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator)

---

## <a name="see-also"></a><span data-ttu-id="f3881-290">Veja também</span><span class="sxs-lookup"><span data-stu-id="f3881-290">See also</span></span>

* [<span data-ttu-id="f3881-291">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="f3881-291">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="f3881-292">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="f3881-292">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="f3881-293">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="f3881-293">Instinctual interactions</span></span>](interaction-fundamentals.md)