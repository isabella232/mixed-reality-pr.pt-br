---
title: Cursores
description: Um cursor ou indicador do vetor de direcionamento fornece comentários contínuos para o usuário entender o que o HoloLens entende sobre suas intenções.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1ª geração), HoloLens 2, Realidade Misturada, cursores, direcionamento, olhar, gestos, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada, raios, entrada
ms.openlocfilehash: 829d7b3f766f848228946ee0a623f9f3013adca3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600375"
---
# <a name="cursors"></a><span data-ttu-id="87a59-104">Cursores</span><span class="sxs-lookup"><span data-stu-id="87a59-104">Cursors</span></span>

![Cursores](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="87a59-106">Um cursor fornece comentários contínuos com base em onde o headset acredita que um foco atual dos usuários está em um determinado momento.</span><span class="sxs-lookup"><span data-stu-id="87a59-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="87a59-107">Os comentários do cursor incluem qual área, holograma ou ponto no ambiente virtual responde à entrada.</span><span class="sxs-lookup"><span data-stu-id="87a59-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="87a59-108">Embora o cursor seja uma representação digital de onde o dispositivo entende a atenção do usuário, isso não é o mesmo que determinar as intenções do usuário.</span><span class="sxs-lookup"><span data-stu-id="87a59-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="87a59-109">Os comentários do cursor também permitem que os usuários saibam quais respostas do sistema esperar.</span><span class="sxs-lookup"><span data-stu-id="87a59-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="87a59-110">Você pode usar os comentários para comunicar sua intenção ao dispositivo, o que aumenta a confiança do usuário.</span><span class="sxs-lookup"><span data-stu-id="87a59-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="87a59-111">Há três tipos de cursores: **dedo, raio** e **olhar para a cabeça.**</span><span class="sxs-lookup"><span data-stu-id="87a59-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="87a59-112">Esses cursores que apontam funcionam com diferentes modais de entrada no HoloLens, no HoloLens 2 e em headsets imersivos.</span><span class="sxs-lookup"><span data-stu-id="87a59-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="87a59-113">Abaixo estão as diretrizes sobre qual tipo de cursor usar para cada tipo de headset e modelo de interação.</span><span class="sxs-lookup"><span data-stu-id="87a59-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="87a59-114">No MRTK (Kit de Ferramentas de Realidade Misturada), criamos módulos de cursores do "arrastar e soltar" para ajudá-lo a criar a experiência de apontar para a direita.</span><span class="sxs-lookup"><span data-stu-id="87a59-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="87a59-115">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="87a59-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="87a59-116"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="87a59-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="87a59-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="87a59-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="87a59-118"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="87a59-118"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="87a59-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="87a59-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="87a59-120">Cursor de dedo</span><span class="sxs-lookup"><span data-stu-id="87a59-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="87a59-121">✔️</span><span class="sxs-lookup"><span data-stu-id="87a59-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="87a59-122">Cursor de raio</span><span class="sxs-lookup"><span data-stu-id="87a59-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="87a59-123">✔️</span><span class="sxs-lookup"><span data-stu-id="87a59-123">✔️</span></span></td>
        <td><span data-ttu-id="87a59-124">✔️</span><span class="sxs-lookup"><span data-stu-id="87a59-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="87a59-125">Cursor de olhar para a cabeça</span><span class="sxs-lookup"><span data-stu-id="87a59-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="87a59-126">✔️</span><span class="sxs-lookup"><span data-stu-id="87a59-126">✔️</span></span></td>
        <td><span data-ttu-id="87a59-127">✔️</span><span class="sxs-lookup"><span data-stu-id="87a59-127">✔️</span></span></td>
        <td><span data-ttu-id="87a59-128">✔️</span><span class="sxs-lookup"><span data-stu-id="87a59-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="87a59-129">Cursor de dedo</span><span class="sxs-lookup"><span data-stu-id="87a59-129">Finger cursor</span></span>

<span data-ttu-id="87a59-130">O cursor de dedo só está disponível no HoloLens 2 para aprimorar o[modo](direct-manipulation.md)de interação " manipulação direta com as mãos ".</span><span class="sxs-lookup"><span data-stu-id="87a59-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="87a59-131">Anexamos anéis às dicas de ambos os dedos indicadores para entender melhor para onde o dedo está apontando.</span><span class="sxs-lookup"><span data-stu-id="87a59-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="87a59-132">O tamanho do anel é baseado na proximidade do dedo com a superfície da interface do usuário, que é reduzido a um ponto pequeno quando o dedo toca a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="87a59-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="87a59-133">Quanto mais próximo o dedo, menor será o anel.</span><span class="sxs-lookup"><span data-stu-id="87a59-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="87a59-134">![cursor de dedo](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="87a59-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="87a59-135">**Estados de comentários visuais do cursor** de dedo 1: o anel diminui para um ponto.</span><span class="sxs-lookup"><span data-stu-id="87a59-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="87a59-136">2: o anel se alinha com a superfície.</span><span class="sxs-lookup"><span data-stu-id="87a59-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="87a59-137">3: o anel é um vetor de dedo para o dedo.</span><span class="sxs-lookup"><span data-stu-id="87a59-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="87a59-138">4: Sem anel.</span><span class="sxs-lookup"><span data-stu-id="87a59-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="87a59-139">Cursor de raio</span><span class="sxs-lookup"><span data-stu-id="87a59-139">Ray cursor</span></span>

<span data-ttu-id="87a59-140">Cursores de raio são anexados ao final de raios que apontam muito para permitir a manipulação de objetos que estão fora do alcance das mãos.</span><span class="sxs-lookup"><span data-stu-id="87a59-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="87a59-141">Em headsets imersivos, os raios se disparam dos controladores de movimento e terminam em cursores de ponto.</span><span class="sxs-lookup"><span data-stu-id="87a59-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="87a59-142">No HoloLens 2, aplicamos o modelo mental desses raios do controlador de movimento e os raios de mão projetados que se originam das mãos e terminam em cursores em forma de anel consistentes com cursores de dedo usados na manipulação direta.</span><span class="sxs-lookup"><span data-stu-id="87a59-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="87a59-143">![Controlador de cursor de raio](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="87a59-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="87a59-144">**Cursores de raio de controladores de movimento**</span><span class="sxs-lookup"><span data-stu-id="87a59-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="87a59-145">![Mão do cursor de raio](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="87a59-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="87a59-146">**Cursores de raio de mãos**</span><span class="sxs-lookup"><span data-stu-id="87a59-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="87a59-147">Cursor de olhar para a cabeça</span><span class="sxs-lookup"><span data-stu-id="87a59-147">Head-gaze cursor</span></span>

<span data-ttu-id="87a59-148">O cursor de olhar para a cabeça é um ponto anexado ao final de um vetor invisível de olhar para a cabeça que usa a posição e a rotação da cabeça para apontar.</span><span class="sxs-lookup"><span data-stu-id="87a59-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="87a59-149">Para executar ações, esse cursor apontador é emparelhado com várias entradas de commit, como toque de ar, comandos de voz, pausar e pressionar botão.</span><span class="sxs-lookup"><span data-stu-id="87a59-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="87a59-150">No HoloLens 2, o olhar com a cabeça é melhor emparelhado com qualquer entrada de commit que não seja toque de ar, pois haverá conflito de interação entre o toque do ar e os raios de mão distantes.</span><span class="sxs-lookup"><span data-stu-id="87a59-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="87a59-151">![Mão do cursor de cursor de curso](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="87a59-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="87a59-152">**Cursor de olhar para a cabeça com gesto de mão**</span><span class="sxs-lookup"><span data-stu-id="87a59-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="87a59-153">![Voz do cursor de cursor de olhar para a cabeça](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="87a59-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="87a59-154">**Cursor de olhar para a cabeça com comando de voz**</span><span class="sxs-lookup"><span data-stu-id="87a59-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="87a59-155">Recomendações de personalização do cursor</span><span class="sxs-lookup"><span data-stu-id="87a59-155">Cursor customization recommendations</span></span>

<span data-ttu-id="87a59-156">Se você quiser personalizar os comportamentos e as aparências dos comentários do cursor, aqui estão algumas recomendações de design:</span><span class="sxs-lookup"><span data-stu-id="87a59-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="87a59-157">Escala de cursor</span><span class="sxs-lookup"><span data-stu-id="87a59-157">Cursor scale</span></span>

* <span data-ttu-id="87a59-158">O cursor não deve ser maior do que os destinos disponíveis, permitindo que os usuários interajam facilmente e exibiam o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="87a59-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="87a59-159">Dependendo da experiência que você cria, dimensionar o cursor conforme o usuário procura também é uma consideração importante.</span><span class="sxs-lookup"><span data-stu-id="87a59-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="87a59-160">Por exemplo, à medida que o usuário fica mais distante em sua experiência, o cursor não deve se tornar muito pequeno, de forma que seja perdido.</span><span class="sxs-lookup"><span data-stu-id="87a59-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="87a59-161">Ao dimensionar o cursor, considere aplicar uma animação suave a ele à medida que ele é dimensionamento para dar a ele uma sensação química.</span><span class="sxs-lookup"><span data-stu-id="87a59-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="87a59-162">Evite obstruir o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="87a59-162">Avoid obstructing content.</span></span> <span data-ttu-id="87a59-163">Os hologramas são o que fazem com que a experiência seja uma memória e o cursor não deve estar sendo desacordo deles.</span><span class="sxs-lookup"><span data-stu-id="87a59-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="87a59-164">Forma do cursor sem direção</span><span class="sxs-lookup"><span data-stu-id="87a59-164">Directionless cursor shape</span></span>

* <span data-ttu-id="87a59-165">Embora não haja uma forma de cursor à direita, recomendamos que você use uma forma sem direção como um torus.</span><span class="sxs-lookup"><span data-stu-id="87a59-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="87a59-166">Um cursor que aponta em alguma direção (por exemplo, um cursor de seta tradicional) pode confundir o usuário para sempre ter essa aparência.</span><span class="sxs-lookup"><span data-stu-id="87a59-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="87a59-167">Uma exceção a isso é ao usar o cursor para comunicar a instrução de interação com o usuário.</span><span class="sxs-lookup"><span data-stu-id="87a59-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="87a59-168">Por exemplo, ao dimensionar hologramas no sistema operacional de Realidade Misturada, o cursor inclui temporariamente setas que instruim o usuário sobre como mover a mão para dimensionar o holograma.</span><span class="sxs-lookup"><span data-stu-id="87a59-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="87a59-169">Aparência</span><span class="sxs-lookup"><span data-stu-id="87a59-169">Look and feel</span></span>

* <span data-ttu-id="87a59-170">Um cursor em forma de rosca ou torus funciona para muitos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="87a59-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="87a59-171">Escolha uma cor e uma forma que melhor represente a experiência que você está criando.</span><span class="sxs-lookup"><span data-stu-id="87a59-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="87a59-172">Cursores são especialmente propensos à [separação de cores.](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)</span><span class="sxs-lookup"><span data-stu-id="87a59-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="87a59-173">Um cursor pequeno com opacidade equilibrada o mantém informativo sem dominar a hierarquia visual.</span><span class="sxs-lookup"><span data-stu-id="87a59-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="87a59-174">Seja ciente do uso de sombras ou realçadas por trás do cursor, pois eles podem obstruir o conteúdo e desviar a tarefa em mãos.</span><span class="sxs-lookup"><span data-stu-id="87a59-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="87a59-175">Os cursores devem se alinhar e se alinhar às superfícies em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="87a59-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="87a59-176">Os usuários terão a impressão de que o sistema pode ver onde estão procurando, mas também que o sistema está ciente de seus ambientes.</span><span class="sxs-lookup"><span data-stu-id="87a59-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="87a59-177">Por exemplo, o cursor no sistema operacional de Realidade Misturada se alinha às superfícies do mundo do usuário, criando uma sensação de reconhecimento do mundo mesmo quando o usuário não está olhando diretamente para um holograma.</span><span class="sxs-lookup"><span data-stu-id="87a59-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="87a59-178">O bloqueio magnético do cursor em um elemento interativo quando ele está próximo ao usuário pode ajudar a melhorar a confiança de que o usuário interagirá com esse elemento quando usar uma ação de seleção.</span><span class="sxs-lookup"><span data-stu-id="87a59-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="87a59-179">Dicas visuais</span><span class="sxs-lookup"><span data-stu-id="87a59-179">Visual cues</span></span>

* <span data-ttu-id="87a59-180">Se sua experiência estiver focada em um único holograma, o cursor deverá alinhar e se alinhar somente a esse holograma e alterar a forma quando você olhar para fora desse holograma.</span><span class="sxs-lookup"><span data-stu-id="87a59-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="87a59-181">Isso pode transmitir ao usuário que o holograma pode ser a ação e pode interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="87a59-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="87a59-182">Se o aplicativo usar o mapeamento espacial, o cursor poderá alinhar e se alinhar a todas as superfícies que ele vir.</span><span class="sxs-lookup"><span data-stu-id="87a59-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="87a59-183">Isso fornece comentários aos usuários de que o HoloLens e seu aplicativo podem ver seu espaço.</span><span class="sxs-lookup"><span data-stu-id="87a59-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="87a59-184">Isso reforça o fato de que os hologramas são reais e em nosso mundo e ajudam a fazer a ponte entre o real e o virtual.</span><span class="sxs-lookup"><span data-stu-id="87a59-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="87a59-185">Tenha uma ideia do que o cursor deve fazer quando não houver hologramas ou superfícies em exibição.</span><span class="sxs-lookup"><span data-stu-id="87a59-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="87a59-186">Colocá-lo a uma distância predeterminada na frente do usuário é uma opção.</span><span class="sxs-lookup"><span data-stu-id="87a59-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="87a59-187">Ações possíveis</span><span class="sxs-lookup"><span data-stu-id="87a59-187">Possible actions</span></span>

* <span data-ttu-id="87a59-188">O cursor pode ser representado por ícones diferentes para transmitir possíveis ações que um holograma pode fazer, como dimensionamento ou rotação.</span><span class="sxs-lookup"><span data-stu-id="87a59-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="87a59-189">Adicione apenas informações extras no cursor se ele significa algo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="87a59-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="87a59-190">Caso contrário, os usuários podem não notar as alterações de estado ou se confundirem com o cursor.</span><span class="sxs-lookup"><span data-stu-id="87a59-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="87a59-191">Estado de entrada</span><span class="sxs-lookup"><span data-stu-id="87a59-191">Input state</span></span>

* <span data-ttu-id="87a59-192">Poderíamos usar o cursor para exibir o estado de entrada ou a intenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="87a59-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="87a59-193">Por exemplo, podemos exibir um ícone dizendo ao usuário que o sistema vê seu estado de mão e que o aplicativo sabe que está pronto para tomar medidas.</span><span class="sxs-lookup"><span data-stu-id="87a59-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="87a59-194">Também podemos usar o cursor para mostrar aos usuários que os comandos de voz foram ouvido pelo sistema por meio de uma alteração de cor momentânea</span><span class="sxs-lookup"><span data-stu-id="87a59-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="87a59-195">Os seguintes estados de cursor podem ser implementados de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="87a59-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="87a59-196">Você pode implementar esses estados diferentes modelando o cursor como um computador de estado.</span><span class="sxs-lookup"><span data-stu-id="87a59-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="87a59-197">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="87a59-197">For example:</span></span>
    * <span data-ttu-id="87a59-198">O estado ocioso é onde você mostra o cursor padrão.</span><span class="sxs-lookup"><span data-stu-id="87a59-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="87a59-199">O estado pronto é quando você detecta a mão do usuário na posição pronta.</span><span class="sxs-lookup"><span data-stu-id="87a59-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="87a59-200">O estado de interação é quando o usuário está fazendo uma interação específica.</span><span class="sxs-lookup"><span data-stu-id="87a59-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="87a59-201">O estado de ações possíveis ou o estado de foco é quando você transmite possíveis ações que podem ser executadas em um holograma.</span><span class="sxs-lookup"><span data-stu-id="87a59-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="87a59-202">Você também pode implementar esses estados de maneira capaz de exibir diferentes ativos de arte ao detectar estados diferentes.</span><span class="sxs-lookup"><span data-stu-id="87a59-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="87a59-203">Ir para "sem cursor"</span><span class="sxs-lookup"><span data-stu-id="87a59-203">Going "cursor-free"</span></span>

<span data-ttu-id="87a59-204">O design sem um cursor é recomendado quando a sensação de imersão é um componente fundamental de uma experiência e ao apontar interações (por meio de olhar e gesto) não exigem grande precisão.</span><span class="sxs-lookup"><span data-stu-id="87a59-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="87a59-205">O sistema ainda precisa atender aos requisitos normais de um cursor: fornecer aos usuários comentários contínuos sobre a compreensão do sistema de seus apontamentos e ajudá-los a comunicar suas intenções ao sistema.</span><span class="sxs-lookup"><span data-stu-id="87a59-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="87a59-206">Isso pode ser possível por meio de outras alterações de estado perceptíveis.</span><span class="sxs-lookup"><span data-stu-id="87a59-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="87a59-207">Cursor no MRTK (Kit de Ferramentas de Realidade Misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="87a59-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="87a59-208">Por padrão, [o MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece um cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) que tem o mesmo estado visual que o cursor do sistema do shell.</span><span class="sxs-lookup"><span data-stu-id="87a59-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="87a59-209">Ele é atribuído no perfil de Entrada do MRTK, em Ponteiros.</span><span class="sxs-lookup"><span data-stu-id="87a59-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="87a59-210">Você pode substituir/personalizar esse cursor para sua experiência.</span><span class="sxs-lookup"><span data-stu-id="87a59-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="87a59-211">Para a experiência com a entrada de acompanhamento ocular, o MRTK também fornece EyeGazeCursor, que tem um visual sutil para minimizar a distração.</span><span class="sxs-lookup"><span data-stu-id="87a59-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="87a59-212">MRTK – Perfil de ponteiro</span><span class="sxs-lookup"><span data-stu-id="87a59-212">MRTK - Pointer profile</span></span>](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [<span data-ttu-id="87a59-213">MRTK – Sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="87a59-213">MRTK - Input system</span></span>](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [<span data-ttu-id="87a59-214">MRTK – Ponteiros</span><span class="sxs-lookup"><span data-stu-id="87a59-214">MRTK - Pointers</span></span>](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a><span data-ttu-id="87a59-215">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87a59-215">See also</span></span>

* [<span data-ttu-id="87a59-216">Gestos</span><span class="sxs-lookup"><span data-stu-id="87a59-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="87a59-217">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="87a59-217">Head-gaze and commit</span></span>](gaze-and-commit.md)