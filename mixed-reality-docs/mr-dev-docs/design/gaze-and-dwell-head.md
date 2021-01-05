---
title: Focar com a cabeça e esperar
description: Visão geral do modelo de entrada de focar com a cabeça e esperar
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Realidade misturada, olhar, pesquisa, interação, design, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade mista, UX, diretrizes, exibição de lista
ms.openlocfilehash: 060d78ec629905ac9f2134851998ec131d85f0cd
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847371"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="0d562-104">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="0d562-104">Head-gaze and dwell</span></span>

<span data-ttu-id="0d562-105">Quando as mãos estão ocupadas com ferramentas e peças, os gestos podem ser entediantes ou impossíveis.</span><span class="sxs-lookup"><span data-stu-id="0d562-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="0d562-106">Os comandos de voz, assim como os gestos, podem não ser confiáveis em determinados contextos (por exemplo, em ambientes excessivamente barulhentos).</span><span class="sxs-lookup"><span data-stu-id="0d562-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="0d562-107">Além disso, usar a voz para controlar computadores não é universalmente comum, mas certamente está ganhando força!</span><span class="sxs-lookup"><span data-stu-id="0d562-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="0d562-108">O modelo de focar com a cabeça e esperar oferece o mecanismo mais familiar e fácil de dominar para trabalhar sem utilizar as mãos no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0d562-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="0d562-109">Além disso, esse modelo é 100% confiável, independentemente da interferência de ruído e das restrições de silêncio do ambiente operacional.</span><span class="sxs-lookup"><span data-stu-id="0d562-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="0d562-110">Cenários</span><span class="sxs-lookup"><span data-stu-id="0d562-110">Scenarios</span></span>

<span data-ttu-id="0d562-111">O Head-olhar e a pesquisa são ótimos em cenários nos quais as mãos de uma pessoa estão ocupadas com outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="0d562-111">Head-gaze and dwell is great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="0d562-112">O recurso também é útil quando a voz não é 100% confiável ou está disponível devido a restrições de ambiente ou sociais.</span><span class="sxs-lookup"><span data-stu-id="0d562-112">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span> <span data-ttu-id="0d562-113">Um bom exemplo é uma pessoa que usa o HoloLens para sobrepor informações de referência ao realizar reparos no motor de um carro.</span><span class="sxs-lookup"><span data-stu-id="0d562-113">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="0d562-114">Suas mãos estão ocupadas com ferramentas ou para apoiar o corpo conforme acessa o compartimento do motor.</span><span class="sxs-lookup"><span data-stu-id="0d562-114">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="0d562-115">O ambiente da garagem é barulhento, com estrondos e zumbidos constantes de ferramentas, o que dificulta os comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="0d562-115">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="0d562-116">O Head-olhar e a pesquisa permitem que a pessoa que usa o HoloLens Navegue com confiança no material de referência sem interromper o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0d562-116">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="0d562-117">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="0d562-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="0d562-118"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="0d562-118"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="0d562-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="0d562-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="0d562-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="0d562-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="0d562-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="0d562-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="0d562-122">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="0d562-122">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="0d562-123">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="0d562-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="0d562-124">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="0d562-124">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="0d562-125">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="0d562-125">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="0d562-126">Princípios de design</span><span class="sxs-lookup"><span data-stu-id="0d562-126">Design principles</span></span>

<span data-ttu-id="0d562-127">**Evitar "Mirar como uma arma"**</span><span class="sxs-lookup"><span data-stu-id="0d562-127">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="0d562-128">A ação de focar com a cabeça e esperar exige que o retorno visual seja intuitivo, mas seu excesso pode induzir a ansiedade.</span><span class="sxs-lookup"><span data-stu-id="0d562-128">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="0d562-129">Os comentários devem ajudar um usuário a saber o que eles estão direcionando, mas não selecioná-lo em sua intenção.</span><span class="sxs-lookup"><span data-stu-id="0d562-129">The feedback should help a user know what they're targeting, but not autoselect it against their intent.</span></span> <span data-ttu-id="0d562-130">Ao ler texto, ícones e rótulos, você precisa fornecer ao usuário tempo para absorver as informações antes de selecionar.</span><span class="sxs-lookup"><span data-stu-id="0d562-130">When reading text, icons, and labels, you need to provide users time to absorb the information before selecting.</span></span>
    
<span data-ttu-id="0d562-131">**Buscar a velocidade ideal**</span><span class="sxs-lookup"><span data-stu-id="0d562-131">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="0d562-132">As interações de espera podem ter tempos diferentes com base no impacto na navegação: as funções usadas com mais frequência geralmente se beneficiam de tempos de preenchimento mais rápidos, enquanto que as funções mais consequentes podem se beneficiar de tempos de preenchimento mais longos.</span><span class="sxs-lookup"><span data-stu-id="0d562-132">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="0d562-133">Ao usar um efeito de preenchimento para mostrar esses tempos, curvas de animação da cor de preenchimento podem influenciar positivamente uma sensação de tempo mais rápido.</span><span class="sxs-lookup"><span data-stu-id="0d562-133">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="0d562-134">Consideração deve ser tomada para permitir a decisão do usuário a partir de substituições das velocidades de preenchimento rápidas/médias/lentas.</span><span class="sxs-lookup"><span data-stu-id="0d562-134">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="0d562-135">**Acabar com o efeito ioiô**</span><span class="sxs-lookup"><span data-stu-id="0d562-135">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="0d562-136">O efeito de Yo-Yo é um padrão de movimento de cabeça desconfortável que ocorre quando os controles de colocação de conteúdo e de cabeçalho/olhar de pesquisa forçam as pessoas a Pesquisar e reduzir repetidamente.</span><span class="sxs-lookup"><span data-stu-id="0d562-136">The yo-yo effect is an uncomfortable head movement pattern that happens when the content placement and head-gaze/dwell controls forces people to look up and down repeatedly.</span></span> <span data-ttu-id="0d562-137">Por exemplo, uma barra de navegação de lista com o botão de olhar e de duração na parte inferior induzi um loop de-Olhe para a pesquisa, pesquisa em resultados, olha para a pesquisa e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="0d562-137">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, and so on.</span></span> <span data-ttu-id="0d562-138">O padrão resultante é desconfortável, portanto, é recomendável colocar controles de navegação em um local centralizado que exija menos suporte.</span><span class="sxs-lookup"><span data-stu-id="0d562-138">The resulting pattern is uncomfortable, so we recommend placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="0d562-139">O posicionamento de botões de pesquisa com base em seus efeitos se torna importante para o conforto.</span><span class="sxs-lookup"><span data-stu-id="0d562-139">Placement of dwell buttons based on their effects becomes important for comfort.</span></span>
<span data-ttu-id="0d562-140">s</span><span class="sxs-lookup"><span data-stu-id="0d562-140">s</span></span>
<br>

---

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="0d562-141">Diretrizes e práticas recomendadas para a experiência do usuário</span><span class="sxs-lookup"><span data-stu-id="0d562-141">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="0d562-142">Tamanhos do alvo</span><span class="sxs-lookup"><span data-stu-id="0d562-142">Target sizes</span></span>

<span data-ttu-id="0d562-143">Para ser facilmente acessível, os destinos de olhar e de pesquisa precisam ser grandes o suficiente para examinar confortavelmente e manter uma cabeça estável no destino pelo tempo prescrito.</span><span class="sxs-lookup"><span data-stu-id="0d562-143">To be easily accessible, head-gaze and dwell targets need to be large enough to look at comfortably, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="0d562-144">Recomendamos um tamanho mínimo de destino de 2 graus para alcançar a experiência mais confortável.</span><span class="sxs-lookup"><span data-stu-id="0d562-144">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="0d562-145">Feedback visual</span><span class="sxs-lookup"><span data-stu-id="0d562-145">Visual feedback</span></span>

<span data-ttu-id="0d562-146">Ao usar um preenchimento radial para representar o tempo de espera, comece do centro do botão.</span><span class="sxs-lookup"><span data-stu-id="0d562-146">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="0d562-147">Uma resposta consistente é menos confusa que diferentes direções em botões diferentes.</span><span class="sxs-lookup"><span data-stu-id="0d562-147">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="0d562-148">Essa regra pode ser quebrada no entanto para interações direcionais (por exemplo, NAV up/down/esquerda/direita e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="0d562-148">This rule can be broken though for directional interactions (for example, nav up/down/left/right, and so on).</span></span> <span data-ttu-id="0d562-149">Por exemplo, os Guias do Microsoft Dynamics 365 fazem uma exceção a essa regra nos botões AVANÇAR/VOLTAR, que são preenchidos da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="0d562-149">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="0d562-150">Considere inverter o preenchimento radial de fora, para cenários como alternar para fora de um botão.</span><span class="sxs-lookup"><span data-stu-id="0d562-150">Consider inverting radial fill from outside, for scenarios like toggling off a button.</span></span> <span data-ttu-id="0d562-151">A sensação inversa de apertar um botão é um padrão visual adequado para manter.</span><span class="sxs-lookup"><span data-stu-id="0d562-151">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="0d562-152">Divulgação progressiva</span><span class="sxs-lookup"><span data-stu-id="0d562-152">Progressive disclosure</span></span>

<span data-ttu-id="0d562-153">A divulgação progressiva significa mostrar apenas a quantidade de detalhes relevante em cada estágio de uma interação.</span><span class="sxs-lookup"><span data-stu-id="0d562-153">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="0d562-154">Para a pesquisa, isso significa que o destino de pesquisa é revelado no realce (por exemplo, em um controle de lista).</span><span class="sxs-lookup"><span data-stu-id="0d562-154">For dwell, that means the dwell target is revealed on highlight (for example, in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="0d562-155">Alvos muito grandes</span><span class="sxs-lookup"><span data-stu-id="0d562-155">Oversized targets</span></span>

<span data-ttu-id="0d562-156">A região de espera pode ser maior do que o ícone inativo para facilitar o uso, como o botão Voltar nos Guias do Microsoft Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="0d562-156">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="0d562-157">Evite a cintilação usando retornos atrasados</span><span class="sxs-lookup"><span data-stu-id="0d562-157">Prevent flickering with delayed feedback</span></span>

<span data-ttu-id="0d562-158">Aplique um pequeno atraso antes de iniciar o retorno visual para evitar cintilação ao passar sobre um alvo de espera.</span><span class="sxs-lookup"><span data-stu-id="0d562-158">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="0d562-159">Para botões interagir com frequência, mantenha o atraso curto para que o aplicativo se sinta reativo.</span><span class="sxs-lookup"><span data-stu-id="0d562-159">For buttons interacted with frequently, keep the delay short so the application feels reactive.</span></span>
* <span data-ttu-id="0d562-160">Para botões que são interagindo com pouca frequência, um atraso mais longo pode ser apropriado para evitar que a interface se sinta twitchy.</span><span class="sxs-lookup"><span data-stu-id="0d562-160">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>

<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="0d562-161">Padrões da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="0d562-161">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="0d562-162">Botões de alta frequência</span><span class="sxs-lookup"><span data-stu-id="0d562-162">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0d562-163">Botões de alta frequência são botões que são usados normalmente em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0d562-163">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="0d562-164">Um bom exemplo são os botões Voltar e Avançar nos Guias do Microsoft Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="0d562-164">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="0d562-165">**Recomendações**</span><span class="sxs-lookup"><span data-stu-id="0d562-165">**Recommendations**</span></span><br>
  * <span data-ttu-id="0d562-166">Botões de alta frequência devem ser grandes, mais fáceis de atingir com Head-olhar</span><span class="sxs-lookup"><span data-stu-id="0d562-166">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="0d562-167">Fique à altura dos olhos para evitar sobrecarregar o ergonômicos.</span><span class="sxs-lookup"><span data-stu-id="0d562-167">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="0d562-168">*Imagem: botão Avançar dos guias do Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="0d562-168">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Botão Avançar dos guias do Microsoft Dynamics 365](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="0d562-170">Botões de baixa frequência</span><span class="sxs-lookup"><span data-stu-id="0d562-170">Low frequency buttons</span></span>

<span data-ttu-id="0d562-171">Os botões de baixa frequência são botões que não são interagindo com o mais regular em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0d562-171">Low frequency buttons are buttons that aren't interacted with as regularly throughout the application.</span></span> <span data-ttu-id="0d562-172">Um bom exemplo é um botão para acessar o menu de configurações ou um botão para limpar toda a tarefa.</span><span class="sxs-lookup"><span data-stu-id="0d562-172">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="0d562-173">Tente manter esses botões longe dos caminhos de ações frequentes de focar com a cabeça para evitar ativação acidental.</span><span class="sxs-lookup"><span data-stu-id="0d562-173">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="0d562-174">Confirmações</span><span class="sxs-lookup"><span data-stu-id="0d562-174">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0d562-175">Quando uma ação tem um impacto significativo, como cobrar dinheiro, excluir trabalho ou iniciar um longo processo, é útil confirmar que uma pessoa pretendia selecionar um botão.</span><span class="sxs-lookup"><span data-stu-id="0d562-175">When an action has significant impact, like charging money, deleting work, or starting a long process, it's useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="0d562-176">**Recomendações**</span><span class="sxs-lookup"><span data-stu-id="0d562-176">**Recommendations**</span></span><br>
  * <span data-ttu-id="0d562-177">Mostre o realce de seleção no botão principal.</span><span class="sxs-lookup"><span data-stu-id="0d562-177">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="0d562-178">Revele o alvo da espera ao mesmo tempo que o realce da seleção.</span><span class="sxs-lookup"><span data-stu-id="0d562-178">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="0d562-179">Para o botão secundário, revele o alvo da espera ao focar com a cabeça.</span><span class="sxs-lookup"><span data-stu-id="0d562-179">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="0d562-180">*Imagem: caixa de diálogo de confirmação de guias do Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="0d562-180">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Caixa de diálogo de confirmação dos guias do Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="0d562-182">Botões de alternância</span><span class="sxs-lookup"><span data-stu-id="0d562-182">Toggle buttons</span></span>

<span data-ttu-id="0d562-183">Botões de alternância exigem uma lógica sutil para funcionarem corretamente.</span><span class="sxs-lookup"><span data-stu-id="0d562-183">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="0d562-184">Quando uma pessoa faz uma pesquisa em um botão de alternância e a ativa, ela precisa sair do botão e retornar para reiniciar a lógica de duração.</span><span class="sxs-lookup"><span data-stu-id="0d562-184">When a person dwells on a toggle button and activates it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="0d562-185">É importante que os botões de alternância tenham um estado claro ativo versus inativo.</span><span class="sxs-lookup"><span data-stu-id="0d562-185">It's important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="0d562-186">Modos de exibição de lista</span><span class="sxs-lookup"><span data-stu-id="0d562-186">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0d562-187">As exibições de lista apresentam um desafio específico para a entrada de olhar e de duração da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="0d562-187">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="0d562-188">As pessoas podem digitalizar o conteúdo sem se sentir que precisam tiptoer os destinos de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="0d562-188">People can scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="0d562-189">**Recomendações**</span><span class="sxs-lookup"><span data-stu-id="0d562-189">**Recommendations**</span></span><br>
  * <span data-ttu-id="0d562-190">Tenha toda a linha realçada quando Head-gazed, mas não inicia a pesquisa, a menos que Head-olhar esteja no destino de duração específico.</span><span class="sxs-lookup"><span data-stu-id="0d562-190">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="0d562-191">Mostrar somente o destino de duração de pesquisa quando a linha for realçada para reduzir o ruído visual.</span><span class="sxs-lookup"><span data-stu-id="0d562-191">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="0d562-192">Fique claro e consistente com a posição dos destinos de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="0d562-192">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="0d562-193">Não mostre todos os destinos de pesquisa de uma só vez para evitar a interface do usuário repetitiva.</span><span class="sxs-lookup"><span data-stu-id="0d562-193">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="0d562-194">Reutilize o mesmo padrão o mais comum possível para estabelecer a familiaridade de UX.</span><span class="sxs-lookup"><span data-stu-id="0d562-194">Reuse the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="0d562-195">*Imagem: lista de guias do Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="0d562-195">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Lista de guias do Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="0d562-197">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d562-197">See also</span></span>

* [<span data-ttu-id="0d562-198">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="0d562-198">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0d562-199">Mãos – Manipulação direta</span><span class="sxs-lookup"><span data-stu-id="0d562-199">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0d562-200">Mãos – Gestos</span><span class="sxs-lookup"><span data-stu-id="0d562-200">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="0d562-201">Mãos – Apontar e confirmar</span><span class="sxs-lookup"><span data-stu-id="0d562-201">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="0d562-202">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="0d562-202">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="0d562-203">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="0d562-203">Voice input</span></span>](voice-input.md)
