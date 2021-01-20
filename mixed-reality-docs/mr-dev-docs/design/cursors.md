---
title: Cursores
description: Um cursor ou indicador de seu vetor de direcionamento, fornece comentários contínuos para que o usuário entenda o que o HoloLens entende sobre suas intenções.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1º gen), HoloLens 2, realidade misturada, cursores, direcionamento, olhar, gestos, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada, raios, entrada
ms.openlocfilehash: 0525bb9b30dfe71fba7b8ebf2afd2c87a8c97a27
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582406"
---
# <a name="cursors"></a><span data-ttu-id="78fea-104">Cursores</span><span class="sxs-lookup"><span data-stu-id="78fea-104">Cursors</span></span>

![Cursores](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="78fea-106">Um cursor fornece comentários contínuos com base em onde o headset acredita que o foco de um usuário atual está em um determinado momento.</span><span class="sxs-lookup"><span data-stu-id="78fea-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="78fea-107">Os comentários do cursor incluem qual área, holograma ou ponto no ambiente virtual responde à entrada.</span><span class="sxs-lookup"><span data-stu-id="78fea-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="78fea-108">Embora o cursor seja uma representação digital de onde o dispositivo entende a atenção do usuário, isso não é o mesmo que determinar as intenções do usuário.</span><span class="sxs-lookup"><span data-stu-id="78fea-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="78fea-109">Os comentários do cursor também permitem que os usuários saibam quais respostas do sistema esperam.</span><span class="sxs-lookup"><span data-stu-id="78fea-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="78fea-110">Você pode usar os comentários para comunicar sua intenção ao dispositivo, o que aumenta a confiança do usuário.</span><span class="sxs-lookup"><span data-stu-id="78fea-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="78fea-111">Há três tipos de cursores: **Finger, Ray** e **Head-olhar**.</span><span class="sxs-lookup"><span data-stu-id="78fea-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="78fea-112">Esses cursores de apontação funcionam com modalidades de entrada diferentes nos headsets HoloLens, HoloLens 2 e imersiva.</span><span class="sxs-lookup"><span data-stu-id="78fea-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="78fea-113">Abaixo está a orientação sobre qual tipo de cursor usar para cada tipo de headset e modelo de interação.</span><span class="sxs-lookup"><span data-stu-id="78fea-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="78fea-114">No MRTK (Kit de ferramentas de realidade misturada), criamos módulos de cursores do tipo "arrastar e soltar" para ajudá-lo a criar a experiência correta.</span><span class="sxs-lookup"><span data-stu-id="78fea-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="78fea-115">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="78fea-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="78fea-116"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="78fea-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="78fea-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="78fea-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="78fea-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="78fea-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="78fea-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="78fea-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="78fea-120">Cursor do dedo</span><span class="sxs-lookup"><span data-stu-id="78fea-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="78fea-121">✔️</span><span class="sxs-lookup"><span data-stu-id="78fea-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="78fea-122">Cursor Ray</span><span class="sxs-lookup"><span data-stu-id="78fea-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="78fea-123">✔️</span><span class="sxs-lookup"><span data-stu-id="78fea-123">✔️</span></span></td>
        <td><span data-ttu-id="78fea-124">✔️</span><span class="sxs-lookup"><span data-stu-id="78fea-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="78fea-125">Cursor de olhar de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="78fea-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="78fea-126">✔️</span><span class="sxs-lookup"><span data-stu-id="78fea-126">✔️</span></span></td>
        <td><span data-ttu-id="78fea-127">✔️</span><span class="sxs-lookup"><span data-stu-id="78fea-127">✔️</span></span></td>
        <td><span data-ttu-id="78fea-128">✔️</span><span class="sxs-lookup"><span data-stu-id="78fea-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="78fea-129">Cursor do dedo</span><span class="sxs-lookup"><span data-stu-id="78fea-129">Finger cursor</span></span>

<span data-ttu-id="78fea-130">O cursor do dedo só está disponível no HoloLens 2 para aprimorar o modo de interação "[manipulação direta com as mãos](direct-manipulation.md)".</span><span class="sxs-lookup"><span data-stu-id="78fea-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="78fea-131">Anexamos anéis às dicas de ambos os dedos para entender melhor onde o dedo está apontando.</span><span class="sxs-lookup"><span data-stu-id="78fea-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="78fea-132">O tamanho do anel é baseado na proximidade do dedo com a superfície da interface do usuário, que se reduz a um ponto pequeno quando o dedo toca na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="78fea-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="78fea-133">Quanto mais próximo do dedo, menor o anel.</span><span class="sxs-lookup"><span data-stu-id="78fea-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="78fea-134">![cursor do dedo](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="78fea-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="78fea-135">**Estados de comentários visuais do cursor 1 do dedo** : o anel é reduzido para um ponto.</span><span class="sxs-lookup"><span data-stu-id="78fea-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="78fea-136">2: o anel se alinha com a superfície.</span><span class="sxs-lookup"><span data-stu-id="78fea-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="78fea-137">3: o anel é perpendicular ao vetor de dedo.</span><span class="sxs-lookup"><span data-stu-id="78fea-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="78fea-138">4: nenhum anel.</span><span class="sxs-lookup"><span data-stu-id="78fea-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="78fea-139">Cursor Ray</span><span class="sxs-lookup"><span data-stu-id="78fea-139">Ray cursor</span></span>

<span data-ttu-id="78fea-140">Os cursores de raio são anexados ao fim dos raios distantes para permitir a manipulação de objetos que estão fora de mãos.</span><span class="sxs-lookup"><span data-stu-id="78fea-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="78fea-141">Em headsets de imersão, os raios saem dos controladores de movimento e dos cursores de fim em ponto.</span><span class="sxs-lookup"><span data-stu-id="78fea-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="78fea-142">No HoloLens 2, aplicamos o modelo mental desses raios do controlador de movimento e raios de mão projetadas que se originam de Palms e terminam com cursores em forma de anel que são consistentes com cursores de dedo usados na manipulação direta.</span><span class="sxs-lookup"><span data-stu-id="78fea-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="78fea-143">![Ray cursor Controller](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="78fea-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="78fea-144">**Ray cursores de controladores de movimento**</span><span class="sxs-lookup"><span data-stu-id="78fea-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="78fea-145">![Raio do cursor](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="78fea-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="78fea-146">**Raios cursores de mãos**</span><span class="sxs-lookup"><span data-stu-id="78fea-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="78fea-147">Cursor de olhar de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="78fea-147">Head-gaze cursor</span></span>

<span data-ttu-id="78fea-148">O cursor Head-olhar é um ponto que é anexado ao final de um vetor Head-olhar invisível que usa a posição e a rotação do ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="78fea-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="78fea-149">Para executar ações, esse cursor apontando é emparelhado com várias entradas de confirmação, como toque de ar, comandos de voz, duração e pressionamento de botão.</span><span class="sxs-lookup"><span data-stu-id="78fea-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="78fea-150">No HoloLens 2, o Head-olhar é melhor emparelhado com qualquer entrada de confirmação que não seja o toque de ar, pois haverá um conflito de interação entre toque de ar e raios de distância.</span><span class="sxs-lookup"><span data-stu-id="78fea-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="78fea-151">![Olhar do cursor de cabeçalho](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="78fea-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="78fea-152">**Cursor de cabeçalho olhar com gesto de mão**</span><span class="sxs-lookup"><span data-stu-id="78fea-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="78fea-153">![Voz do cursor olhar de cabeçalho](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="78fea-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="78fea-154">**Cursor de cabeçalho olhar com comando de voz**</span><span class="sxs-lookup"><span data-stu-id="78fea-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="78fea-155">Recomendações de personalização do cursor</span><span class="sxs-lookup"><span data-stu-id="78fea-155">Cursor customization recommendations</span></span>

<span data-ttu-id="78fea-156">Se você quiser personalizar os comportamentos e as aparências dos comentários do cursor, veja algumas recomendações de design:</span><span class="sxs-lookup"><span data-stu-id="78fea-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="78fea-157">Escala do cursor</span><span class="sxs-lookup"><span data-stu-id="78fea-157">Cursor scale</span></span>

* <span data-ttu-id="78fea-158">O cursor não deve ser maior do que os destinos disponíveis, permitindo que os usuários interajam com facilidade e exibam o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="78fea-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="78fea-159">Dependendo da experiência que você criar, dimensionar o cursor à medida que o usuário procura também é uma consideração importante.</span><span class="sxs-lookup"><span data-stu-id="78fea-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="78fea-160">Por exemplo, à medida que o usuário fica mais distante em sua experiência, o cursor não deve se tornar muito pequeno, de modo que ele é perdido.</span><span class="sxs-lookup"><span data-stu-id="78fea-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="78fea-161">Ao dimensionar o cursor, considere aplicar uma animação suave a ele, pois ele é dimensionado para dar a ele uma sensação orgânica.</span><span class="sxs-lookup"><span data-stu-id="78fea-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="78fea-162">Evite obstruir o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="78fea-162">Avoid obstructing content.</span></span> <span data-ttu-id="78fea-163">Os hologramas são o que torna a experiência fácil de memorizar e o cursor não deve ser retirado delas.</span><span class="sxs-lookup"><span data-stu-id="78fea-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="78fea-164">Forma de cursor de direção</span><span class="sxs-lookup"><span data-stu-id="78fea-164">Directionless cursor shape</span></span>

* <span data-ttu-id="78fea-165">Embora não haja uma forma de cursor à direita, recomendamos que você use uma forma sem direção como uma Torus.</span><span class="sxs-lookup"><span data-stu-id="78fea-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="78fea-166">Um cursor que aponta em alguma direção (por exemplo, um cursor de seta tradicional) pode confundir o usuário para sempre verificar dessa forma.</span><span class="sxs-lookup"><span data-stu-id="78fea-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="78fea-167">Uma exceção a isso é quando se usa o cursor para comunicar a instrução de interação ao usuário.</span><span class="sxs-lookup"><span data-stu-id="78fea-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="78fea-168">Por exemplo, ao dimensionar hologramas no sistema operacional de realidade misturada, o cursor inclui temporariamente setas que instruem o usuário sobre como mover sua mão para dimensionar o holograma.</span><span class="sxs-lookup"><span data-stu-id="78fea-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="78fea-169">Aparência</span><span class="sxs-lookup"><span data-stu-id="78fea-169">Look and feel</span></span>

* <span data-ttu-id="78fea-170">Um cursor com formato de rosca ou Torus funciona para muitos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="78fea-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="78fea-171">Escolha uma cor e forma que melhor represente a experiência que você está criando.</span><span class="sxs-lookup"><span data-stu-id="78fea-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="78fea-172">Os cursores estão especialmente sujeitos à [separação de cores](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span><span class="sxs-lookup"><span data-stu-id="78fea-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="78fea-173">Um cursor pequeno com opacidade equilibrada mantém-o informativo sem a predominante da hierarquia visual.</span><span class="sxs-lookup"><span data-stu-id="78fea-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="78fea-174">Seja Cognizant de usar sombras ou destaques por trás do cursor, pois eles podem obstruir o conteúdo e distrair a tarefa em questão.</span><span class="sxs-lookup"><span data-stu-id="78fea-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="78fea-175">Os cursores devem alinhar e Hug as superfícies em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="78fea-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="78fea-176">Os usuários terão a sensação de que o sistema pode ver onde estão olhando, mas também que o sistema está ciente de seus arredores.</span><span class="sxs-lookup"><span data-stu-id="78fea-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="78fea-177">Por exemplo, o cursor no sistema operacional misto da realidade se alinha às superfícies do mundo do usuário, criando uma sensação de conscientização do mundo, mesmo quando o usuário não está olhando diretamente para um holograma.</span><span class="sxs-lookup"><span data-stu-id="78fea-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="78fea-178">Bloquear magneticamente o cursor para um elemento interativo quando ele está próximo do usuário pode ajudar a melhorar a confiança que o usuário irá interagir com esse elemento quando usar uma ação de seleção.</span><span class="sxs-lookup"><span data-stu-id="78fea-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="78fea-179">Indicações visuais</span><span class="sxs-lookup"><span data-stu-id="78fea-179">Visual cues</span></span>

* <span data-ttu-id="78fea-180">Se sua experiência estiver concentrada em um único holograma, o cursor deverá alinhar e hugr apenas esse holograma e alterar a forma quando você olhar para fora desse holograma.</span><span class="sxs-lookup"><span data-stu-id="78fea-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="78fea-181">Isso pode transmitir ao usuário que o holograma é acionável e pode interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="78fea-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="78fea-182">Se seu aplicativo usar o mapeamento espacial, o cursor poderá ser alinhado e Hug cada superfície que vê.</span><span class="sxs-lookup"><span data-stu-id="78fea-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="78fea-183">Isso fornece comentários aos usuários que o HoloLens e seu aplicativo podem ver seu espaço.</span><span class="sxs-lookup"><span data-stu-id="78fea-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="78fea-184">Isso reforça o fato de que os hologramas são reais e em nosso mundo e ajudam a preencher a lacuna entre o real e o virtual.</span><span class="sxs-lookup"><span data-stu-id="78fea-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="78fea-185">Tenha uma ideia do que o cursor deve fazer quando não há hologramas ou superfícies na exibição.</span><span class="sxs-lookup"><span data-stu-id="78fea-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="78fea-186">Colocá-lo em uma distância predeterminada na frente do usuário é uma opção.</span><span class="sxs-lookup"><span data-stu-id="78fea-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="78fea-187">Ações possíveis</span><span class="sxs-lookup"><span data-stu-id="78fea-187">Possible actions</span></span>

* <span data-ttu-id="78fea-188">O cursor pode ser representado por ícones diferentes para transmitir possíveis ações que um holograma pode fazer, como dimensionamento ou rotação.</span><span class="sxs-lookup"><span data-stu-id="78fea-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="78fea-189">Somente adicione informações extras sobre o cursor se isso significa algo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="78fea-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="78fea-190">Caso contrário, os usuários talvez não percebam as alterações de estado ou ficam confusos com o cursor.</span><span class="sxs-lookup"><span data-stu-id="78fea-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="78fea-191">Estado de entrada</span><span class="sxs-lookup"><span data-stu-id="78fea-191">Input state</span></span>

* <span data-ttu-id="78fea-192">Poderíamos usar o cursor para exibir o estado ou a intenção de entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="78fea-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="78fea-193">Por exemplo, podemos exibir um ícone informando ao usuário que o sistema vê seu estado de mão e que o aplicativo sabe que está pronto para agir.</span><span class="sxs-lookup"><span data-stu-id="78fea-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="78fea-194">Também poderíamos usar o cursor para mostrar aos usuários que comandos de voz foram ouvidos pelo sistema por meio de uma alteração de cor momentânea</span><span class="sxs-lookup"><span data-stu-id="78fea-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="78fea-195">Os seguintes Estados de cursor podem ser implementados de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="78fea-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="78fea-196">Você pode implementar esses Estados diferentes modelando o cursor como um computador de estado.</span><span class="sxs-lookup"><span data-stu-id="78fea-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="78fea-197">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="78fea-197">For example:</span></span>
    * <span data-ttu-id="78fea-198">Estado ocioso é onde você mostra o cursor padrão.</span><span class="sxs-lookup"><span data-stu-id="78fea-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="78fea-199">Estado pronto é quando você detecta a mão do usuário na posição pronta.</span><span class="sxs-lookup"><span data-stu-id="78fea-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="78fea-200">O estado de interação é quando o usuário está fazendo uma interação específica.</span><span class="sxs-lookup"><span data-stu-id="78fea-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="78fea-201">O estado de ações possível ou o estado de foco é quando você transmite possíveis ações que podem ser executadas em um holograma.</span><span class="sxs-lookup"><span data-stu-id="78fea-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="78fea-202">Você também pode implementar esses Estados em uma maneira capaz de exibir ativos de arte diferentes ao detectar Estados diferentes.</span><span class="sxs-lookup"><span data-stu-id="78fea-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="78fea-203">Indo "sem cursor"</span><span class="sxs-lookup"><span data-stu-id="78fea-203">Going "cursor-free"</span></span>

<span data-ttu-id="78fea-204">A criação sem um cursor é recomendada quando o sentido do imersão é um componente-chave de uma experiência e quando as interações de ponteiro (por meio de olhar e gesto) não exigem uma ótima precisão.</span><span class="sxs-lookup"><span data-stu-id="78fea-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="78fea-205">O sistema ainda precisa atender aos requisitos normais de um cursor: fornecer aos usuários comentários contínuos sobre o entendimento do sistema e ajudá-los a comunicar suas intenções ao sistema.</span><span class="sxs-lookup"><span data-stu-id="78fea-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="78fea-206">Isso pode ser alcançado por meio de outras alterações de estado perceptível.</span><span class="sxs-lookup"><span data-stu-id="78fea-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="78fea-207">Cursor em MRTK (Mixed Reality Toolkit) para Unity</span><span class="sxs-lookup"><span data-stu-id="78fea-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="78fea-208">Por padrão, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece um cursor pré-fabricado ([DefaultCursor. pré-fabricado](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) que tem o mesmo estado visual que o cursor do sistema do Shell.</span><span class="sxs-lookup"><span data-stu-id="78fea-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="78fea-209">Ele é atribuído no perfil de Entrada do MRTK, em Ponteiros.</span><span class="sxs-lookup"><span data-stu-id="78fea-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="78fea-210">Você pode substituir/personalizar este cursor para sua experiência.</span><span class="sxs-lookup"><span data-stu-id="78fea-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="78fea-211">Para a experiência com a entrada de controle de olho, o MRTK também fornece EyeGazeCursor, que tem Visual sutil para minimizar a distração.</span><span class="sxs-lookup"><span data-stu-id="78fea-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="78fea-212">MRTK – Perfil de ponteiro</span><span class="sxs-lookup"><span data-stu-id="78fea-212">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="78fea-213">MRTK – Sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="78fea-213">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="78fea-214">MRTK – Ponteiros</span><span class="sxs-lookup"><span data-stu-id="78fea-214">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)

---

## <a name="see-also"></a><span data-ttu-id="78fea-215">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78fea-215">See also</span></span>

* [<span data-ttu-id="78fea-216">Gestos</span><span class="sxs-lookup"><span data-stu-id="78fea-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="78fea-217">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="78fea-217">Head-gaze and commit</span></span>](gaze-and-commit.md)