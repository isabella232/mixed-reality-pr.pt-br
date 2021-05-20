---
title: Focar e confirmar
description: Saiba mais sobre o modelo de entrada de olhar e confirmação, incluindo dois tipos de olhar (com o olhar e com o olhar) e vários tipos de confirmação.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidade Misturada, olhar, direcionamento de olhar, interação, design, acompanhamento ocular, acompanhamento de cabeça, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada
ms.openlocfilehash: db394ab4aded7136550e8e88eb3d66e06f3eeb92
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196561"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="9ba15-104">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="9ba15-104">Gaze and commit</span></span>

<span data-ttu-id="9ba15-105">_O olhar e_ a confirmação são um modelo de entrada fundamental que está intimamente relacionado à maneira como estamos interagindo com nossos computadores usando o mouse: aponte para & _clique em_.</span><span class="sxs-lookup"><span data-stu-id="9ba15-105">_Gaze and commit_ is a fundamental input model that is closely related to the way we're interacting with our computers using the mouse: _Point & click_.</span></span> <span data-ttu-id="9ba15-106">Nesta página, apresentamos dois tipos de entrada de olhar (com a cabeça e o olhar) e diferentes tipos de ações de commit.</span><span class="sxs-lookup"><span data-stu-id="9ba15-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> <span data-ttu-id="9ba15-107">_O olhar e a commit_ são considerados um modelo de entrada distante com manipulação indireta.</span><span class="sxs-lookup"><span data-stu-id="9ba15-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span> <span data-ttu-id="9ba15-108">Ele é mais bem usado para interagir com o conteúdo holográfico que está fora de alcance.</span><span class="sxs-lookup"><span data-stu-id="9ba15-108">It's best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="9ba15-109">Os headsets de realidade misturada podem usar a posição e a orientação da cabeça do usuário para determinar o vetor de direção da cabeça.</span><span class="sxs-lookup"><span data-stu-id="9ba15-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="9ba15-110">Pense no foco como um raio apontando diretamente para frente diretamente entre os olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="9ba15-110">Think of gaze as a laser pointing straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="9ba15-111">Essa é uma aproximação bastante grosseira da direção para a qual o usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="9ba15-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="9ba15-112">Seu aplicativo pode intersecção desse raio com objetos virtuais ou do mundo real e desenhar um cursor nesse local para permitir que o usuário saiba o que ele está direcionando.</span><span class="sxs-lookup"><span data-stu-id="9ba15-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they're targeting.</span></span>

<span data-ttu-id="9ba15-113">Além do olhar para a cabeça, alguns headsets de realidade misturada, como o HoloLens 2, incluem sistemas de acompanhamento ocular que produzem um vetor de olhar.</span><span class="sxs-lookup"><span data-stu-id="9ba15-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="9ba15-114">Isso fornece uma medida refinada da direção para a qual o usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="9ba15-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="9ba15-115">Em ambos os casos, o olhar representa um sinal importante para a intenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="9ba15-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="9ba15-116">Quanto melhor o sistema puder interpretar e prever as ações pretendíveis do usuário, mais satisfação e desempenho do usuário melhorarão.</span><span class="sxs-lookup"><span data-stu-id="9ba15-116">The better the system can interpret and predict the user's intended actions, the more user satisfaction and performance improves.</span></span>

<span data-ttu-id="9ba15-117">Abaixo estão alguns exemplos de como você, como desenvolvedor de realidade misturada, pode se beneficiar do olhar ou da cabeça:</span><span class="sxs-lookup"><span data-stu-id="9ba15-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="9ba15-118">Seu aplicativo pode interseção de olhar com os hologramas em sua cena para determinar onde está a atenção do usuário (mais preciso com o olhar).</span><span class="sxs-lookup"><span data-stu-id="9ba15-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="9ba15-119">Seu aplicativo pode canalizar gestos e pressionas de controlador com base no olhar do usuário, o que permite que o usuário selecione, ative, segure, role ou interaja diretamente com seus hologramas.</span><span class="sxs-lookup"><span data-stu-id="9ba15-119">Your app can channel gestures and controller presses based on the user's gaze, which lets the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="9ba15-120">Seu aplicativo pode permitir que o usuário Coloque os hologramas em superfícies do mundo real interseccionando seu olhar Ray com a malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="9ba15-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="9ba15-121">Seu aplicativo pode saber quando o usuário não está olhando para a direção de um objeto importante, o que pode fazer com que seu aplicativo dê indicações visuais e de áudio para virar esse objeto.</span><span class="sxs-lookup"><span data-stu-id="9ba15-121">Your app can know when the user isn't looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="9ba15-122">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="9ba15-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9ba15-123"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="9ba15-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="9ba15-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="9ba15-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="9ba15-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="9ba15-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="9ba15-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="9ba15-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9ba15-127">Foco com a cabeça e confirmação</span><span class="sxs-lookup"><span data-stu-id="9ba15-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="9ba15-128">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="9ba15-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="9ba15-129">✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</span><span class="sxs-lookup"><span data-stu-id="9ba15-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="9ba15-130">➕ Opção alternativa</span><span class="sxs-lookup"><span data-stu-id="9ba15-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="9ba15-131">Focar com o olhar e confirmar</span><span class="sxs-lookup"><span data-stu-id="9ba15-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="9ba15-132">❌ Não disponível</span><span class="sxs-lookup"><span data-stu-id="9ba15-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="9ba15-133">✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</span><span class="sxs-lookup"><span data-stu-id="9ba15-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="9ba15-134">❌ Não disponível</span><span class="sxs-lookup"><span data-stu-id="9ba15-134">❌ Not available</span></span></td>
    </tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a><span data-ttu-id="9ba15-135">Demonstração dos conceitos de design de controle de cabeça e olho</span><span class="sxs-lookup"><span data-stu-id="9ba15-135">Head and eye tracking design concepts demo</span></span>

<span data-ttu-id="9ba15-136">Se você gostaria de ver os conceitos de design de controle de cabeça e olho em ação, Confira nossa demonstração de vídeo **de acompanhamento de holograma e** acompanhamento de cabeça abaixo.</span><span class="sxs-lookup"><span data-stu-id="9ba15-136">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="9ba15-137">Quando tiver terminado, continue em para obter mais detalhes sobre tópicos específicos.</span><span class="sxs-lookup"><span data-stu-id="9ba15-137">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="9ba15-138">*Este vídeo foi tirado do aplicativo "criando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*</span><span class="sxs-lookup"><span data-stu-id="9ba15-138">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="gaze"></a><span data-ttu-id="9ba15-139">Focar</span><span class="sxs-lookup"><span data-stu-id="9ba15-139">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="9ba15-140">Olho ou cabeça-olhar?</span><span class="sxs-lookup"><span data-stu-id="9ba15-140">Eye- or head-gaze?</span></span>
<span data-ttu-id="9ba15-141">Há várias considerações ao enfrentar a pergunta se você deve usar o modelo de entrada "olho-olhar e confirmar" ou "Head-olhar e Commit".</span><span class="sxs-lookup"><span data-stu-id="9ba15-141">There are several considerations when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="9ba15-142">Se você estiver desenvolvendo para um headset de imersão ou para o HoloLens (1º gen), a escolha será simples: Head-olhar e Commit.</span><span class="sxs-lookup"><span data-stu-id="9ba15-142">If you're developing for an immersive headset or for HoloLens (1st gen), then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="9ba15-143">Se você estiver desenvolvendo para o HoloLens 2, a escolha se tornará um pouco mais difícil.</span><span class="sxs-lookup"><span data-stu-id="9ba15-143">If you're developing for HoloLens 2, the choice becomes a little harder.</span></span> <span data-ttu-id="9ba15-144">É importante entender as vantagens e os desafios que acompanham cada um deles.</span><span class="sxs-lookup"><span data-stu-id="9ba15-144">It's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="9ba15-145">Compilamos alguns dos nossos profissionais e contratados na tabela abaixo para contrastars em contraste com a olhar de direcionamento.</span><span class="sxs-lookup"><span data-stu-id="9ba15-145">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="9ba15-146">Isso está longe de ser concluído e sugerimos saber mais sobre o direcionamento olhar para a realidade misturada aqui:</span><span class="sxs-lookup"><span data-stu-id="9ba15-146">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="9ba15-147">[Acompanhamento de olho no hololens 2](eye-tracking.md): introdução geral do nosso novo recurso de acompanhamento de olho no hololens 2, incluindo algumas diretrizes para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="9ba15-147">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="9ba15-148">[Olhar interação](eye-gaze-interaction.md)entre os olhos: considerações de design e recomendações ao planejar o uso de acompanhamento de olho como uma entrada.</span><span class="sxs-lookup"><span data-stu-id="9ba15-148">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="9ba15-149"><strong>Direcionamento de olhar de olho</strong></span><span class="sxs-lookup"><span data-stu-id="9ba15-149"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="9ba15-150"><strong>Direcionamento de foco com a cabeça</strong></span><span class="sxs-lookup"><span data-stu-id="9ba15-150"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9ba15-151">Rápida!</span><span class="sxs-lookup"><span data-stu-id="9ba15-151">Fast!</span></span></td>
        <td><span data-ttu-id="9ba15-152">Mais lento</span><span class="sxs-lookup"><span data-stu-id="9ba15-152">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9ba15-153">Baixo esforço (praticamente todos os movimentos de corpo necessários)</span><span class="sxs-lookup"><span data-stu-id="9ba15-153">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="9ba15-154">Pode ser fatiguing – Possível estresse (por exemplo, tensão de cabeça)</span><span class="sxs-lookup"><span data-stu-id="9ba15-154">Can be fatiguing - Possible discomfort (for example, neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9ba15-155">Não requer um cursor, mas comentários sutis são recomendados</span><span class="sxs-lookup"><span data-stu-id="9ba15-155">Doesn't require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="9ba15-156">Requer para mostrar um cursor</span><span class="sxs-lookup"><span data-stu-id="9ba15-156">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9ba15-157">Sem movimentos de olho suaves – por exemplo, não é bom para desenho</span><span class="sxs-lookup"><span data-stu-id="9ba15-157">No smooth eye movements – for example, not good for drawing</span></span></td>
        <td><span data-ttu-id="9ba15-158">Mais controlado e explícito</span><span class="sxs-lookup"><span data-stu-id="9ba15-158">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9ba15-159">Difícil para destinos pequenos (por exemplo, botões pequenos ou weblinks)</span><span class="sxs-lookup"><span data-stu-id="9ba15-159">Difficult for small targets (for example, tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="9ba15-160">Confiável!</span><span class="sxs-lookup"><span data-stu-id="9ba15-160">Reliable!</span></span> <span data-ttu-id="9ba15-161">Excelente fallback!</span><span class="sxs-lookup"><span data-stu-id="9ba15-161">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9ba15-162">...</span><span class="sxs-lookup"><span data-stu-id="9ba15-162">...</span></span></td>
        <td><span data-ttu-id="9ba15-163">...</span><span class="sxs-lookup"><span data-stu-id="9ba15-163">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="9ba15-164">Se você usar o olhar com a cabeça ou com o olhar para seu modelo de entrada de olhar e de commit, cada um deles vem com diferentes conjuntos de restrições de design.</span><span class="sxs-lookup"><span data-stu-id="9ba15-164">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model, each comes with different sets of design constraints.</span></span> <span data-ttu-id="9ba15-165">Eles são abordados separadamente nos artigos [de](gaze-and-commit-eyes.md) confirmação e de olhar com o olhar e [com a cabeça e commit.](gaze-and-commit-head.md)</span><span class="sxs-lookup"><span data-stu-id="9ba15-165">These are covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="9ba15-166">Cursor</span><span class="sxs-lookup"><span data-stu-id="9ba15-166">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="9ba15-167">Para o olhar para a cabeça, a maioria dos aplicativos deve usar um [cursor](cursors.md) ou outra indicação auditiva/visual para dar ao usuário confiança sobre com o que eles estão prestes a interagir.</span><span class="sxs-lookup"><span data-stu-id="9ba15-167">For head gaze, most apps should use a [cursor](cursors.md) or other auditory/visual indication to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="9ba15-168">Normalmente, você posiciona esse cursor no mundo em que o raio de olhar de cabeça primeiro intersecciona um objeto, que pode ser um holograma ou uma superfície do mundo real.</span><span class="sxs-lookup"><span data-stu-id="9ba15-168">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="9ba15-169">Para o foco com  o olhar, geralmente recomendamos não mostrar um cursor, pois isso pode se tornar rapidamente uma distração e uma distração para o usuário.</span><span class="sxs-lookup"><span data-stu-id="9ba15-169">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="9ba15-170">Em vez disso, realça subtly os destinos visuais ou use um cursor de olho para dar confiança sobre com o que o usuário está prestes a interagir.</span><span class="sxs-lookup"><span data-stu-id="9ba15-170">Instead subtly highlight visual targets or use a faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="9ba15-171">Para obter mais informações, confira nossas [diretrizes de design para](eye-tracking.md) entrada com base nos olhos no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9ba15-171">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="9ba15-172">![Um cursor visual de exemplo para mostrar o olhar](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="9ba15-172">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="9ba15-173">*Imagem: um cursor visual de exemplo para mostrar o olhar*</span><span class="sxs-lookup"><span data-stu-id="9ba15-173">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="9ba15-174">Commit</span><span class="sxs-lookup"><span data-stu-id="9ba15-174">Commit</span></span>
<span data-ttu-id="9ba15-175">Depois de falar sobre diferentes maneiras _de_ olhar para um destino, vamos falar um pouco mais sobre a parte _de confirmação_ no olhar e fazer _commit do_.</span><span class="sxs-lookup"><span data-stu-id="9ba15-175">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="9ba15-176">Depois de direcionar um objeto ou elemento de interface do usuário, o usuário pode interagir ou clicar nele usando uma entrada secundária.</span><span class="sxs-lookup"><span data-stu-id="9ba15-176">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="9ba15-177">Isso é conhecido como a etapa de confirmação do modelo de entrada.</span><span class="sxs-lookup"><span data-stu-id="9ba15-177">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="9ba15-178">Os seguintes métodos de confirmação são compatíveis:</span><span class="sxs-lookup"><span data-stu-id="9ba15-178">The following commit methods are supported:</span></span>
- <span data-ttu-id="9ba15-179">Gesto de toque do ar à mão (ou seja, eleve sua mão na frente e reúna o dedo e o polegar)</span><span class="sxs-lookup"><span data-stu-id="9ba15-179">Air tap hand gesture (that is, raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="9ba15-180">Diga _"Select"_ ou um dos comandos de voz de destino</span><span class="sxs-lookup"><span data-stu-id="9ba15-180">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="9ba15-181">Pressione um único botão em um [clicador de HoloLens](/hololens/hololens1-clicker)</span><span class="sxs-lookup"><span data-stu-id="9ba15-181">Press a single button on a [HoloLens Clicker](/hololens/hololens1-clicker)</span></span>
- <span data-ttu-id="9ba15-182">Pressione o botão ' A ' em um gamepad do Xbox</span><span class="sxs-lookup"><span data-stu-id="9ba15-182">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="9ba15-183">Pressione o botão ' A ' em um controlador adaptável do Xbox</span><span class="sxs-lookup"><span data-stu-id="9ba15-183">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="9ba15-184">Gesto de toque olhar e Air</span><span class="sxs-lookup"><span data-stu-id="9ba15-184">Gaze and air tap gesture</span></span>
<span data-ttu-id="9ba15-185">Fechar e abrir dedos indicador e polegar é um gesto de tocar feito com a mão levantada.</span><span class="sxs-lookup"><span data-stu-id="9ba15-185">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="9ba15-186">Para usar um toque de ar, aumente o seu indicador para a posição pronta, aperte o polegar e aumente o seu dedo de índice de volta para o lançamento.</span><span class="sxs-lookup"><span data-stu-id="9ba15-186">To use an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="9ba15-187">No HoloLens (1ª gen), o Air Tap é a entrada secundária mais comum.</span><span class="sxs-lookup"><span data-stu-id="9ba15-187">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="9ba15-188">![Dedo na posição pronta](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="9ba15-188">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="9ba15-189">**Dedo na posição pronta**</span><span class="sxs-lookup"><span data-stu-id="9ba15-189">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="9ba15-190">![Pressione dedo para baixo para tocar ou clique](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="9ba15-190">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="9ba15-191&quot;>**Pressione dedo para baixo para tocar ou clique**</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9ba15-191&quot;>**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id=&quot;9ba15-192&quot;>O toque de ar também está disponível no HoloLens 2.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9ba15-192&quot;>Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id=&quot;9ba15-193&quot;>Ele foi relaxado da versão original.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9ba15-193&quot;>It has been relaxed from the original version.</span></span> <span data-ttu-id=&quot;9ba15-194&quot;>Quase todos os tipos de pinçações agora têm suporte, contanto que a mão esteja na vertical e mantendo ainda.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9ba15-194&quot;>Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id=&quot;9ba15-195&quot;>Isso torna muito mais fácil para os usuários aprender e usar o gesto.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9ba15-195&quot;>This makes it much easier for users to learn and use the gesture.</span></span> <span data-ttu-id=&quot;9ba15-196&quot;>Esse novo toque de ar substitui o antigo por meio da mesma API, de modo que os aplicativos existentes terão o novo comportamento automaticamente após a recompilação para o HoloLens 2.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9ba15-196&quot;>This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name=&quot;gaze-and-select-voice-command&quot;></a><span data-ttu-id=&quot;9ba15-197&quot;>Olhar e comando de voz &quot;Select&quot;</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9ba15-197&quot;>Gaze and &quot;Select&quot; voice command</span></span>
<span data-ttu-id=&quot;9ba15-198&quot;>A linha de comando de voz é um dos principais métodos de interação na realidade misturada.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9ba15-198&quot;>Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id=&quot;9ba15-199&quot;>Ele fornece um poderoso mecanismo prático para controlar o sistema.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9ba15-199&quot;>It provides a powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id=&quot;9ba15-200&quot;>Há diferentes tipos de modelos de interação de voz:</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9ba15-200&quot;>There are different types of voice interaction models:</span></span>

- <span data-ttu-id=&quot;9ba15-201&quot;>O comando genérico &quot;Selecionar&quot; que usa uma acionamento de clique ou confirmação como uma entrada secundária.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9ba15-201&quot;>The generic &quot;Select&quot; command that uses a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id=&quot;9ba15-202&quot;>Comandos de objeto (por exemplo, &quot;Fechar&quot; ou &quot;Aumentar") executam e se comprometem com uma ação como uma entrada secundária.</span><span class="sxs-lookup"><span data-stu-id="9ba15-202">Object commands (for example, "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="9ba15-203">Comandos globais (por exemplo, "Ir para iniciar") não exigem um destino.</span><span class="sxs-lookup"><span data-stu-id="9ba15-203">Global commands (for example, "Go to start") don't require a target.</span></span>
- <span data-ttu-id="9ba15-204">Interfaces de usuário de conversa ou entidades como a Cortana têm uma funcionalidade de linguagem natural de IA.</span><span class="sxs-lookup"><span data-stu-id="9ba15-204">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="9ba15-205">Comandos de voz personalizados</span><span class="sxs-lookup"><span data-stu-id="9ba15-205">Custom voice commands</span></span>

<span data-ttu-id="9ba15-206">Para saber mais sobre detalhes e uma lista abrangente de comandos de voz disponíveis e como usá-los, confira nossas [diretrizes de comandos de](../out-of-scope/voice-design.md) voz.</span><span class="sxs-lookup"><span data-stu-id="9ba15-206">To find out more about details and a comprehensive list of available voice commands and how to use them, check out our [voice commanding](../out-of-scope/voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="9ba15-207">Gaze e HoloLens Clicker</span><span class="sxs-lookup"><span data-stu-id="9ba15-207">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="9ba15-208">O HoloLens Clicker é o primeiro dispositivo periférico criado especificamente para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9ba15-208">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="9ba15-209">Ele está incluído no HoloLens (1ª geração) Development Edition.</span><span class="sxs-lookup"><span data-stu-id="9ba15-209">It's included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="9ba15-210">O HoloLens Clicker permite que um usuário clique com movimento mínimo de mão e faça commit como uma entrada secundária.</span><span class="sxs-lookup"><span data-stu-id="9ba15-210">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="9ba15-211">O HoloLens Clicker se conecta ao HoloLens (1ª geração) ou ao HoloLens 2 usando Bluetooth de Baixa Energia (BTLE).</span><span class="sxs-lookup"><span data-stu-id="9ba15-211">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="9ba15-212">Mais informações e instruções para emparelhar o dispositivo</span><span class="sxs-lookup"><span data-stu-id="9ba15-212">More information and instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="9ba15-213">*Imagem: HoloLens Clicker*</span><span class="sxs-lookup"><span data-stu-id="9ba15-213">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="9ba15-215">Gaze e controlador sem fio Xbox</span><span class="sxs-lookup"><span data-stu-id="9ba15-215">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="9ba15-216">O Controlador Sem Fio Xbox executa uma audição de clique como uma entrada secundária usando o botão "A".</span><span class="sxs-lookup"><span data-stu-id="9ba15-216">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="9ba15-217">O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar e controlar o sistema.</span><span class="sxs-lookup"><span data-stu-id="9ba15-217">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="9ba15-218">Se você quiser personalizar o controlador, use o aplicativo Acessórios Xbox para configurar o controlador sem fio Xbox.</span><span class="sxs-lookup"><span data-stu-id="9ba15-218">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="9ba15-219">Como emparelhar um controlador Xbox com seu computador</span><span class="sxs-lookup"><span data-stu-id="9ba15-219">How to pair an Xbox controller with your PC</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="9ba15-220">*Imagem: Controlador Sem Fio Xbox*</span><span class="sxs-lookup"><span data-stu-id="9ba15-220">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Controle sem Fio Xbox](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="9ba15-222">Controlador adaptável olhar e Xbox</span><span class="sxs-lookup"><span data-stu-id="9ba15-222">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="9ba15-223">Projetado principalmente para atender às necessidades de jogos com mobilidade limitada, o controlador adaptável do Xbox é um hub unificado para dispositivos que ajuda a tornar a realidade misturada mais acessível.</span><span class="sxs-lookup"><span data-stu-id="9ba15-223">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="9ba15-224">O controlador adaptável do Xbox executa um clique actuation como uma entrada secundária usando o botão ' A '.</span><span class="sxs-lookup"><span data-stu-id="9ba15-224">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="9ba15-225">O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar e controlar o sistema.</span><span class="sxs-lookup"><span data-stu-id="9ba15-225">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="9ba15-226">Se você quiser personalizar o controlador, use o aplicativo de acessórios do Xbox para configurar o controlador adaptável do Xbox.</span><span class="sxs-lookup"><span data-stu-id="9ba15-226">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="9ba15-227">![Controle Adaptável Xbox](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="9ba15-227">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="9ba15-228">*Controle Adaptável Xbox*</span><span class="sxs-lookup"><span data-stu-id="9ba15-228">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="9ba15-229">Conecte dispositivos externos, como comutadores, botões, montagens e joysticks, para criar uma experiência de controlador personalizada que seja exclusivamente sua.</span><span class="sxs-lookup"><span data-stu-id="9ba15-229">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="9ba15-230">As entradas de botão, Thumbstick e gatilho são controladas com dispositivos assistenciais conectados por meio de portas USB e conectores de 3,5-mm.</span><span class="sxs-lookup"><span data-stu-id="9ba15-230">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5-mm jacks and USB ports.</span></span>

<span data-ttu-id="9ba15-231">![Portas do Controle Adaptável Xbox](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="9ba15-231">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="9ba15-232">*Portas do Controle Adaptável Xbox*</span><span class="sxs-lookup"><span data-stu-id="9ba15-232">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="9ba15-233">Instruções para emparelhar o dispositivo</span><span class="sxs-lookup"><span data-stu-id="9ba15-233">Instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="9ba15-234"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Mais informações disponíveis no site do Xbox</a></span><span class="sxs-lookup"><span data-stu-id="9ba15-234"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="9ba15-235">Gestos compostos</span><span class="sxs-lookup"><span data-stu-id="9ba15-235">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="9ba15-236">Fechar e abrir dedos indicador e polegar</span><span class="sxs-lookup"><span data-stu-id="9ba15-236">Air tap</span></span>
<span data-ttu-id="9ba15-237">O gesto de toque do ar (e os outros gestos abaixo) reage apenas a um toque específico.</span><span class="sxs-lookup"><span data-stu-id="9ba15-237">The air tap gesture (and the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="9ba15-238">Para detectar outros toques, como menu ou compreender, seu aplicativo deve usar diretamente as interações de nível inferior descritas na seção dois principais gestos de componente acima.</span><span class="sxs-lookup"><span data-stu-id="9ba15-238">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="9ba15-239">Fechar e abrir dedos indicador e polegar e manter</span><span class="sxs-lookup"><span data-stu-id="9ba15-239">Tap and hold</span></span>
<span data-ttu-id="9ba15-240">Manter é simplesmente manter a posição do dedo para baixo no gesto de fechar e abrir dedos indicador e polegar.</span><span class="sxs-lookup"><span data-stu-id="9ba15-240">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="9ba15-241">A combinação de toque e suspensão do ar permite várias interações mais complexas de "clicar e arrastar" quando combinadas com a movimentação do ARM, como a seleção de um objeto, em vez de ativá-lo ou interações secundárias de MouseDown, como mostrar um menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="9ba15-241">The combination of air tap and hold allows for various more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="9ba15-242">Deve-se ter cuidado ao criar esse gesto, pois os usuários podem estar propensos a relaxar suas posturas de mão durante qualquer gesto estendido.</span><span class="sxs-lookup"><span data-stu-id="9ba15-242">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="9ba15-243">manipulação</span><span class="sxs-lookup"><span data-stu-id="9ba15-243">Manipulation</span></span>
<span data-ttu-id="9ba15-244">Os gestos de manipulação podem ser usados para mover, redimensionar ou girar um holograma quando você quiser que o holograma reaja 1:1 aos movimentos da mão do usuário.</span><span class="sxs-lookup"><span data-stu-id="9ba15-244">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="9ba15-245">Um uso para essas movimentações de 1:1 é permitir que o usuário desenhe ou pinte no mundo.</span><span class="sxs-lookup"><span data-stu-id="9ba15-245">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="9ba15-246">O direcionamento inicial de um gesto de manipulação deve ser feito pelo foco ou apontando.</span><span class="sxs-lookup"><span data-stu-id="9ba15-246">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="9ba15-247">Quando o toque e a suspensão são iniciados, qualquer manipulação de objeto é tratada por movimentos de mão, o que libera o usuário para examinar enquanto manipula.</span><span class="sxs-lookup"><span data-stu-id="9ba15-247">Once the tap and hold starts, any object manipulation is handled by hand movements, which frees the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="9ba15-248">Navegação</span><span class="sxs-lookup"><span data-stu-id="9ba15-248">Navigation</span></span>
<span data-ttu-id="9ba15-249">Os gestos de navegação funcionam como um joystick virtual e podem ser usados para navegar por widgets de interface do usuário, como menus radiais.</span><span class="sxs-lookup"><span data-stu-id="9ba15-249">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="9ba15-250">Feche e abra os dedos indicador e polegar e mantenha para iniciar o gesto e, em seguida, mova a mão dentro de um cubo 3D normalizado, centralizado em torno do pressionamento inicial.</span><span class="sxs-lookup"><span data-stu-id="9ba15-250">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="9ba15-251">Você pode mover sua mão ao longo do eixo X, Y ou Z de um valor de-1 para 1, sendo que 0 é o ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="9ba15-251">You can move your hand along the X, Y, or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="9ba15-252">A navegação pode ser usada para criar gestos de rolagem ou zoom contínuo baseados em velocidade, semelhante à rolagem de uma interface do usuário 2D com um clique no botão do meio do mouse e, em seguida, a movimentação do mouse para cima e para baixo.</span><span class="sxs-lookup"><span data-stu-id="9ba15-252">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="9ba15-253">A navegação com Rails refere-se à capacidade de reconhecer movimentos em determinado eixo até que um determinado limite seja atingido nesse eixo.</span><span class="sxs-lookup"><span data-stu-id="9ba15-253">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="9ba15-254">Isso só é útil quando a movimentação em mais de um eixo é habilitada em um aplicativo pelo desenvolvedor, como se um aplicativo estiver configurado para reconhecer gestos de navegação no eixo X, Y, mas também especificado eixo X com trilhos.</span><span class="sxs-lookup"><span data-stu-id="9ba15-254">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="9ba15-255">Nesse caso, o sistema reconhecerá os movimentos de mão no eixo X, desde que permaneçam dentro de um trilho imaginário (guia) no eixo X, se o movimento da mão também ocorrer no eixo Y.</span><span class="sxs-lookup"><span data-stu-id="9ba15-255">In this case, the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="9ba15-256">Em aplicativos 2D, os usuários podem usar gestos de navegação vertical para rolagem, zoom ou operações de arrastar dentro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9ba15-256">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="9ba15-257">Isso injeta toques de dedo virtuais no aplicativo para simular gestos de toque do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="9ba15-257">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="9ba15-258">Os usuários podem selecionar quais dessas ações ocorrem ao fazer a agregação entre as ferramentas na barra acima do aplicativo, selecionando o botão ou dizendo "<Ferramenta de Rolagem/Arrastar/Ampliar>".</span><span class="sxs-lookup"><span data-stu-id="9ba15-258">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="9ba15-259">Mais informações sobre gestos compostos</span><span class="sxs-lookup"><span data-stu-id="9ba15-259">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="9ba15-260">Reconhecedores de gestos</span><span class="sxs-lookup"><span data-stu-id="9ba15-260">Gesture recognizers</span></span>

<span data-ttu-id="9ba15-261">Um benefício de usar o reconhecimento de gestos é que você pode configurar um reconhecedor de gestos somente para os gestos que o holograma atualmente direcionado pode aceitar.</span><span class="sxs-lookup"><span data-stu-id="9ba15-261">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="9ba15-262">A plataforma só faz a desambiguidade conforme necessário para distinguir esses gestos com suporte específicos.</span><span class="sxs-lookup"><span data-stu-id="9ba15-262">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="9ba15-263">Dessa forma, um holograma que dá suporte apenas ao toque de ar pode aceitar qualquer período de tempo entre a pressão e a liberação, enquanto um holograma que dá suporte ao toque e à espera pode promover o toque para uma espera após o limite de tempo de espera.</span><span class="sxs-lookup"><span data-stu-id="9ba15-263">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="9ba15-264">Reconhecimento de mão</span><span class="sxs-lookup"><span data-stu-id="9ba15-264">Hand recognition</span></span>
<span data-ttu-id="9ba15-265">O HoloLens reconhece gestos de mão acompanhando a posição de uma ou das duas mãos visíveis para o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9ba15-265">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="9ba15-266">O HoloLens vê as mãos quando elas estão no estado pronto (parte posterior da mão voltada para você com o dedo indicador para cima) ou no estado pressionado (parte posterior da mão voltada para você com o dedo indicador para baixo).</span><span class="sxs-lookup"><span data-stu-id="9ba15-266">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="9ba15-267">Quando as mãos estão em outras poses, o HoloLens as ignora.</span><span class="sxs-lookup"><span data-stu-id="9ba15-267">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="9ba15-268">Para cada mão detectada pelo HoloLens, você pode acessar sua posição sem orientação e seu estado pressionado.</span><span class="sxs-lookup"><span data-stu-id="9ba15-268">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="9ba15-269">Conforme a mão se aproxima da borda do quadro de gesto, você também recebe um vetor de direção, que você pode mostrar ao usuário para que ele saiba como mover a mão para retorná-la ao local em que o HoloLens possa vê-la.</span><span class="sxs-lookup"><span data-stu-id="9ba15-269">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="9ba15-270">Quadro de gesto</span><span class="sxs-lookup"><span data-stu-id="9ba15-270">Gesture frame</span></span>
<span data-ttu-id="9ba15-271">Para gestos no HoloLens, a mão deve estar dentro de um quadro de gesto, em um intervalo que as câmeras de gestos possam ver adequadamente, desde o nariz até a cabeça e entre os olhos.</span><span class="sxs-lookup"><span data-stu-id="9ba15-271">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="9ba15-272">Os usuários precisam ser treinados nessa área de reconhecimento para o sucesso da ação e para seu próprio conforto.</span><span class="sxs-lookup"><span data-stu-id="9ba15-272">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="9ba15-273">Inicialmente, muitos usuários pressupom que o quadro de gestos deve estar dentro de sua exibição por meio do HoloLens e manterão seus braços incomparáveis para interagir.</span><span class="sxs-lookup"><span data-stu-id="9ba15-273">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold up their arms uncomfortably to interact.</span></span> <span data-ttu-id="9ba15-274">Ao usar o HoloLens Clicker, não é necessário que as mãos sejam dentro do quadro de gestos.</span><span class="sxs-lookup"><span data-stu-id="9ba15-274">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="9ba15-275">Para gestos contínuos em particular, há algum risco de os usuários moverem as mãos para fora do quadro de gestos durante o gesto ao mover um objeto holográfico, por exemplo, e perderem o resultado pretendido.</span><span class="sxs-lookup"><span data-stu-id="9ba15-275">For continuous gestures in particular, there's some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="9ba15-276">Há três coisas que você deve considerar:</span><span class="sxs-lookup"><span data-stu-id="9ba15-276">There are three things that you should consider:</span></span>

- <span data-ttu-id="9ba15-277">Educação do usuário na existência do quadro gesto e limites aproximados.</span><span class="sxs-lookup"><span data-stu-id="9ba15-277">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="9ba15-278">Isso é ensinado durante a configuração do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9ba15-278">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="9ba15-279">Notificar os usuários quando seus gestos estiverem se aproximando ou dividindo os limites de quadro de gesto dentro de um aplicativo no grau de um gesto perdido levar a resultados indesejados.</span><span class="sxs-lookup"><span data-stu-id="9ba15-279">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="9ba15-280">A pesquisa mostrou as principais qualidades desse sistema de notificação.</span><span class="sxs-lookup"><span data-stu-id="9ba15-280">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="9ba15-281">O Shell do HoloLens fornece um bom exemplo desse tipo de notificação – Visual, no cursor central, indicando a direção na qual o cruzamento de limites está ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="9ba15-281">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="9ba15-282">As consequências de sair dos limites do quadro do gesto deverão ser minimizadas.</span><span class="sxs-lookup"><span data-stu-id="9ba15-282">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="9ba15-283">Em geral, isso significa que o resultado de um gesto deve ser interrompido no limite e não revertido.</span><span class="sxs-lookup"><span data-stu-id="9ba15-283">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="9ba15-284">Por exemplo, se um usuário estiver movendo algum objeto Holographic em uma sala, a movimentação deverá parar quando o quadro do gesto for violado e não retornar ao ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="9ba15-284">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="9ba15-285">O usuário pode enfrentar alguma frustração, mas pode entender mais rapidamente os limites e não precisa reiniciar suas ações pretendidas todas as vezes.</span><span class="sxs-lookup"><span data-stu-id="9ba15-285">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="9ba15-286">Confira também</span><span class="sxs-lookup"><span data-stu-id="9ba15-286">See also</span></span>
* [<span data-ttu-id="9ba15-287">Interação ocular</span><span class="sxs-lookup"><span data-stu-id="9ba15-287">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="9ba15-288">Acompanhamento ocular no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9ba15-288">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="9ba15-289">Focar e esperar</span><span class="sxs-lookup"><span data-stu-id="9ba15-289">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="9ba15-290">Mãos – Manipulação direta</span><span class="sxs-lookup"><span data-stu-id="9ba15-290">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9ba15-291">Mãos – Gestos</span><span class="sxs-lookup"><span data-stu-id="9ba15-291">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="9ba15-292">Mãos – Apontar e confirmar</span><span class="sxs-lookup"><span data-stu-id="9ba15-292">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="9ba15-293">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="9ba15-293">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="9ba15-294">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="9ba15-294">Voice input</span></span>](voice-input.md)