---
title: O que é um holograma?
description: HoloLens permite exibir e interagir com hologramas tridimensionais, objetos feitos de luz e som que aparecem no mundo ao seu redor.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, hologramas, design, interação, headset de realidade misturada, headset de realidade misturada do Windows, o que é realidade aumentada
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634327"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="885b2-104">O que é um holograma?</span><span class="sxs-lookup"><span data-stu-id="885b2-104">What is a hologram?</span></span>

<span data-ttu-id="885b2-105">HoloLens permite exibir **hologramas**, que são objetos feitos de luz e som que aparecem no mundo ao seu redor, como objetos reais.</span><span class="sxs-lookup"><span data-stu-id="885b2-105">HoloLens lets you view **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="885b2-106">Hologramas pode responder ao seu [olhar,](../design/gaze-and-commit.md) [gestos](../design/gaze-and-commit.md#composite-gestures)e comandos [de voz.](../design/voice-input.md)</span><span class="sxs-lookup"><span data-stu-id="885b2-106">Holograms can respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="885b2-107">Eles podem até mesmo interagir com [superfícies do mundo real](../design/spatial-mapping.md) ao seu redor.</span><span class="sxs-lookup"><span data-stu-id="885b2-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="885b2-108">Hologramas são objetos digitais que fazem parte do seu mundo.</span><span class="sxs-lookup"><span data-stu-id="885b2-108">Holograms are digital objects that are part of your world.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

## <a name="device-support"></a><span data-ttu-id="885b2-109">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="885b2-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="885b2-110"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="885b2-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="885b2-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="885b2-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="885b2-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="885b2-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="885b2-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="885b2-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="885b2-114">Hologramas</span><span class="sxs-lookup"><span data-stu-id="885b2-114">Holograms</span></span></td>
        <td><span data-ttu-id="885b2-115">✔️</span><span class="sxs-lookup"><span data-stu-id="885b2-115">✔️</span></span></td>
        <td><span data-ttu-id="885b2-116">✔️</span><span class="sxs-lookup"><span data-stu-id="885b2-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="885b2-117">Um holograma é feito de luz e som</span><span class="sxs-lookup"><span data-stu-id="885b2-117">A hologram is made of light and sound</span></span>

### <a name="light"></a><span data-ttu-id="885b2-118">Claro</span><span class="sxs-lookup"><span data-stu-id="885b2-118">Light</span></span>

<span data-ttu-id="885b2-119">Os hologramas que HoloLens [renderiza](../develop/platform-capabilities-and-apis/rendering.md) aparecem no quadro holográfico diretamente na frente dos olhos dos usuários.</span><span class="sxs-lookup"><span data-stu-id="885b2-119">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of users' eyes.</span></span> <span data-ttu-id="885b2-120">Hologramas adicione luz ao seu mundo, o que significa que você vê a luz da exibição e a luz do seu mundo ao redor.</span><span class="sxs-lookup"><span data-stu-id="885b2-120">Holograms add light to your world, which means that you see both the light from the display and the light from your surrounding world.</span></span> <span data-ttu-id="885b2-121">Como HoloLens usa uma exibição aditiva que adiciona luz, a cor preta será renderizada de forma transparente.</span><span class="sxs-lookup"><span data-stu-id="885b2-121">Since HoloLens uses an additive display that adds light, the black color will be rendered transparent.</span></span> 

<span data-ttu-id="885b2-122">Hologramas pode ter aparências e comportamentos muito diferentes.</span><span class="sxs-lookup"><span data-stu-id="885b2-122">Holograms can have very different appearances and behaviors.</span></span> <span data-ttu-id="885b2-123">Alguns são realistas e sólidos e outros são desenhista e ethereal.</span><span class="sxs-lookup"><span data-stu-id="885b2-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="885b2-124">Você pode usar hologramas para realçar recursos em seu ambiente ou usá-los como elementos na interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="885b2-124">You can use holograms to highlight features in your environment or use them as elements in your app's user interface.</span></span>

![Manipulação de mãos de um holograma](images/hologram-hands-940px.jpg)

### <a name="sound"></a><span data-ttu-id="885b2-126">Som</span><span class="sxs-lookup"><span data-stu-id="885b2-126">Sound</span></span>

<span data-ttu-id="885b2-127">Hologramas também pode produzir [sons](../design/spatial-sound.md), que parecem vir de um local específico em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="885b2-127">Holograms can also produce [sounds](../design/spatial-sound.md), which appear to come from a specific place in your environment.</span></span> <span data-ttu-id="885b2-128">No HoloLens, o som vem de dois alto-falantes localizados diretamente acima de seus olhos.</span><span class="sxs-lookup"><span data-stu-id="885b2-128">On HoloLens, sound comes from two speakers that are located directly above your ears.</span></span> <span data-ttu-id="885b2-129">Da mesma forma que as exibições holográficas, os alto-falantes são aditivos, introduzindo novos sons sem bloquear os sons do seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="885b2-129">Same as the holographic displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="885b2-130">Um holograma pode ser colocado no mundo ou marcar com você</span><span class="sxs-lookup"><span data-stu-id="885b2-130">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="885b2-131">Quando você tem um local fixo para um holograma, pode [colocar](../design/coordinate-systems.md) exatamente nesse ponto do mundo.</span><span class="sxs-lookup"><span data-stu-id="885b2-131">When you have a fixed location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="885b2-132">À medida que você anda, o holograma aparece estacionário com base no mundo ao seu redor, assim como um objeto físico.</span><span class="sxs-lookup"><span data-stu-id="885b2-132">As you walk around, the hologram appears stationary based on the world around you, just like a physical object.</span></span> <span data-ttu-id="885b2-133">Se você usar uma [âncora espacial para](../design/coordinate-systems.md#spatial-anchors) fixar o objeto, o sistema poderá até mesmo se lembrar de onde você o deixou quando voltar mais tarde.</span><span class="sxs-lookup"><span data-stu-id="885b2-133">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![Dois homens usando o Layout do Microsoft Dynamics 365 em um espaço de varejo](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="885b2-135">Em vez disso, alguns hologramas seguem o usuário.</span><span class="sxs-lookup"><span data-stu-id="885b2-135">Some holograms follow the user instead.</span></span> <span data-ttu-id="885b2-136">Eles se posicionam com base no usuário.</span><span class="sxs-lookup"><span data-stu-id="885b2-136">They position themselves based on the user.</span></span> <span data-ttu-id="885b2-137">Você pode optar por trazer um holograma com você e, em seguida, coloque-o na parede quando chegar a outra sala.</span><span class="sxs-lookup"><span data-stu-id="885b2-137">You can choose to bring a hologram with you, and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="885b2-138">**Práticas recomendadas**</span><span class="sxs-lookup"><span data-stu-id="885b2-138">**Best practices**</span></span>

* <span data-ttu-id="885b2-139">Alguns cenários exigem que os hologramas permaneçam facilmente descobertos ou visíveis durante toda a experiência.</span><span class="sxs-lookup"><span data-stu-id="885b2-139">Some scenarios demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="885b2-140">Há duas abordagens de alto nível para esse tipo de posicionamento.</span><span class="sxs-lookup"><span data-stu-id="885b2-140">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="885b2-141">Vamos chamá-los **de bloqueados por exibição** **e bloqueados pelo corpo.**</span><span class="sxs-lookup"><span data-stu-id="885b2-141">Let's call them **display-locked** and **body-locked**.</span></span>
   * <span data-ttu-id="885b2-142">**O conteúdo bloqueado para** exibição é bloqueado no dispositivo de exibição.</span><span class="sxs-lookup"><span data-stu-id="885b2-142">**Display-locked** content is locked to the display device.</span></span> <span data-ttu-id="885b2-143">Esse tipo de conteúdo é complicado por vários motivos, incluindo uma sensação anormal de "desariedade" que deixa muitos usuários frustrados e desejando "abalá-lo".</span><span class="sxs-lookup"><span data-stu-id="885b2-143">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="885b2-144">Em geral, os designers descobriram melhor evitar o conteúdo de bloqueio de exibição.</span><span class="sxs-lookup"><span data-stu-id="885b2-144">In general, designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="885b2-145">**O conteúdo bloqueado pelo** corpo pode ser muito mais tolerante.</span><span class="sxs-lookup"><span data-stu-id="885b2-145">**Body-locked** content can be far more forgiving.</span></span> <span data-ttu-id="885b2-146">O bloqueio do corpo é quando você insera um holograma no corpo ou vetor de olhar do usuário no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="885b2-146">Body-locking is when you tether a hologram to the user's body or gaze vector in 3D space.</span></span> <span data-ttu-id="885b2-147">Muitas experiências adotaram um comportamento de bloqueio do corpo em que o holograma segue o olhar do usuário, o que permite que o usuário gire seu corpo e se mova pelo espaço sem perder o holograma.</span><span class="sxs-lookup"><span data-stu-id="885b2-147">Many experiences have adopted a body-locking behavior where the hologram follows the user's gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="885b2-148">Incorporar um atraso ajuda os movimentos do holograma a se sentir mais natural.</span><span class="sxs-lookup"><span data-stu-id="885b2-148">Incorporating a delay helps the hologram movements to feel more natural.</span></span> <span data-ttu-id="885b2-149">Por exemplo, algumas interfaces do usuário principais do sistema operacional holográfico do Windows usam uma variação no bloqueio de corpo que segue o olhar do usuário com um atraso elástico e elástico enquanto o usuário gira a cabeça.</span><span class="sxs-lookup"><span data-stu-id="885b2-149">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="885b2-150">Coloque o holograma a uma distância de exibição confortável normalmente a cerca de 1 a 2 metros da cabeça.</span><span class="sxs-lookup"><span data-stu-id="885b2-150">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="885b2-151">Permitir que os elementos se desmigam se eles devem estar continuamente no quadro holográfico ou considere mover o conteúdo para um lado da exibição quando o usuário altera seu ponto de vista.</span><span class="sxs-lookup"><span data-stu-id="885b2-151">Allow elements to drift if they must be continually in the holographic frame, or consider moving your content to one side of the display when the user changes their point of view.</span></span> <span data-ttu-id="885b2-152">Para obter mais informações, consulte [a artilce de](../design/billboarding-and-tag-along.md) marcação e de marcação.</span><span class="sxs-lookup"><span data-stu-id="885b2-152">For more information, see the [billboarding and tag-along](../design/billboarding-and-tag-along.md) artilce.</span></span>

<span data-ttu-id="885b2-153">**Colocar hologramas na zona ideal – entre 1,25 m e 5 m**</span><span class="sxs-lookup"><span data-stu-id="885b2-153">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="885b2-154">Dois metros é a distância de exibição mais ideal.</span><span class="sxs-lookup"><span data-stu-id="885b2-154">Two meters is the most optimal viewing distance.</span></span> <span data-ttu-id="885b2-155">A experiência começará a ser degradada à medida que você se aproximar de 1 medidor.</span><span class="sxs-lookup"><span data-stu-id="885b2-155">The experience will start to degrade as you get closer than 1 meter.</span></span> <span data-ttu-id="885b2-156">A distâncias menores que 1 medidor, hologramas que se movem regularmente em profundidade têm maior probabilidade de serem problemáticos do que hologramas estacionários.</span><span class="sxs-lookup"><span data-stu-id="885b2-156">At distances less than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="885b2-157">Considere cortar ou esvasar normalmente seu conteúdo quando ele ficar muito próximo, para que você não agrade o usuário em uma experiência de exibição desagrade.</span><span class="sxs-lookup"><span data-stu-id="885b2-157">Consider gracefully clipping or fading out your content when it gets too close, so you don't jar the user into an unpleasant viewing experience.</span></span>

![Distância ideal para colocar hologramas do usuário.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="885b2-159">Um holograma interage com você e seu mundo</span><span class="sxs-lookup"><span data-stu-id="885b2-159">A hologram interacts with you and your world</span></span>

<span data-ttu-id="885b2-160">Hologramas não são apenas sobre luz e som; eles também são uma parte ativa do seu mundo.</span><span class="sxs-lookup"><span data-stu-id="885b2-160">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="885b2-161">O olhar para um holograma e um gesto com a mão, e um holograma pode começar a seguir você.</span><span class="sxs-lookup"><span data-stu-id="885b2-161">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="885b2-162">Dê um comando de voz e o holograma poderá responder.</span><span class="sxs-lookup"><span data-stu-id="885b2-162">Give a voice command, and the hologram can reply.</span></span>

![Grupo de funcionários públicos que usam Microsoft HoloLens 2 para colaborar em um projeto de desenvolvimento de parques eólicas](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="885b2-164">Hologramas habilitar interações pessoais que não são possíveis em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="885b2-164">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="885b2-165">Como o HoloLens sabe onde ele está no mundo, um caractere holográfico pode olhar para você diretamente nos olhos e iniciar uma conversa com você.</span><span class="sxs-lookup"><span data-stu-id="885b2-165">Because the HoloLens knows where it is in the world, a holographic character can look at you directly in the eyes and start a conversation with you.</span></span>

<span data-ttu-id="885b2-166">Um holograma também pode interagir com seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="885b2-166">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="885b2-167">Por exemplo, você pode colocar uma bola de salto holográfico acima de uma tabela.</span><span class="sxs-lookup"><span data-stu-id="885b2-167">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="885b2-168">Em seguida, com um [toque de ar,](../design/gaze-and-commit.md#composite-gestures)observe a bola quicar e fazer som enquanto ela atinge a tabela.</span><span class="sxs-lookup"><span data-stu-id="885b2-168">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound as it hits the table.</span></span>

<span data-ttu-id="885b2-169">Hologramas também podem ser ocluídos por objetos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="885b2-169">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="885b2-170">Por exemplo, um caractere holográfico pode passar por uma porta e atrás de uma parede, fora de sua vista.</span><span class="sxs-lookup"><span data-stu-id="885b2-170">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="885b2-171">**Dicas para integrar hologramas e o mundo real**</span><span class="sxs-lookup"><span data-stu-id="885b2-171">**Tips for integrating holograms and the real world**</span></span>

* <span data-ttu-id="885b2-172">Alinhar-se às regras de reação torna os hologramas mais fáceis de se relacionar e mais fáceis de se relacionar.</span><span class="sxs-lookup"><span data-stu-id="885b2-172">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="885b2-173">Por exemplo: coloque um cachorro holográfico no chão & um cão na tabela em vez de fazer com que eles fluam no espaço.</span><span class="sxs-lookup"><span data-stu-id="885b2-173">For example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="885b2-174">Muitos designers descobriram que podem integrar hologramas mais compreensíveis criando uma "sombra negativa" na superfície em que o holograma está.</span><span class="sxs-lookup"><span data-stu-id="885b2-174">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="885b2-175">Eles fazem isso criando um brilho suave no chão ao redor do holograma e subtraindo a "sombra" do brilho.</span><span class="sxs-lookup"><span data-stu-id="885b2-175">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="885b2-176">O brilho suave se integra à luz do mundo real.</span><span class="sxs-lookup"><span data-stu-id="885b2-176">The soft glow integrates with the light from the real world.</span></span> <span data-ttu-id="885b2-177">A sombra é usada para basear o holograma no ambiente.</span><span class="sxs-lookup"><span data-stu-id="885b2-177">The shadow is used to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a><span data-ttu-id="885b2-178">Um holograma é o que</span><span class="sxs-lookup"><span data-stu-id="885b2-178">A hologram is what</span></span> <br><span data-ttu-id="885b2-179">você pode se desemocar</span><span class="sxs-lookup"><span data-stu-id="885b2-179">you can dream up</span></span><br>
        <span data-ttu-id="885b2-180">Como desenvolvedor holográfico, você tem o poder de quebrar sua criatividade das telas 2D e do mundo ao seu redor.</span><span class="sxs-lookup"><span data-stu-id="885b2-180">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="885b2-181">O que *você criará?*</span><span class="sxs-lookup"><span data-stu-id="885b2-181">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="885b2-182">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="885b2-182">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="885b2-183">![Mundo imaginário holográfico na sala de estar](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="885b2-183">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="885b2-184">Próximo ponto de verificação de descoberta</span><span class="sxs-lookup"><span data-stu-id="885b2-184">Next Discovery Checkpoint</span></span>

<span data-ttu-id="885b2-185">Você está no percurso [de descoberta](get-started-with-mr.md) que lançamos e explora os conceitos básicos da Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="885b2-185">You're on the [discovery journey](get-started-with-mr.md) we've laid out, and exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="885b2-186">Desse ponto, você poderá prosseguir para o próximo tópico básico:</span><span class="sxs-lookup"><span data-stu-id="885b2-186">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="885b2-187">Expanda seu processo de design</span><span class="sxs-lookup"><span data-stu-id="885b2-187">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)