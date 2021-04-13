---
title: Mural e tag-along
description: Saiba como usar objetos com o mural, que sempre se orientam a enfrentar o usuário em aplicativos de realidade misturada.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, mensagem de contorno, marca, com a realidade misturada Headset, headset da realidade mista do Windows, headset da realidade virtual, HoloLens, MRTK, kit de ferramentas da realidade misturada
ms.openlocfilehash: 48c7aa28217a38c6c226b65a6e16ed7c950cec59
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299881"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="c4439-104">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="c4439-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="c4439-105">O que é o mural?</span><span class="sxs-lookup"><span data-stu-id="c4439-105">What is billboarding?</span></span>

<span data-ttu-id="c4439-106">A mensagem é um conceito comportamental que pode ser aplicado a objetos em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c4439-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="c4439-107">Os objetos com o mural sempre se orientam para enfrentar o usuário.</span><span class="sxs-lookup"><span data-stu-id="c4439-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="c4439-108">Os sistemas de texto e de menus são casos de uso comuns, em que os objetos estáticos colocados no ambiente do usuário (bloqueado pelo mundo) seriam obscuros ou ilegíveis quando os usuários perfrentem.</span><span class="sxs-lookup"><span data-stu-id="c4439-108">Text and menu systems are common use cases, where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable when users move around.</span></span>

<span data-ttu-id="c4439-109">Os objetos com o mural habilitado podem girar livremente no ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="c4439-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="c4439-110">Eles também podem ser restritos a um único eixo, dependendo das considerações de design.</span><span class="sxs-lookup"><span data-stu-id="c4439-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="c4439-111">Tenha em mente que os objetos convelados podem recortar ou se occluder quando colocados muito próximos de outros objetos, ou no HoloLens, fecham as superfícies digitalizadas.</span><span class="sxs-lookup"><span data-stu-id="c4439-111">Keep in mind, billboarded objects can clip or occlude themselves when placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="c4439-112">Para evitar isso, pense na superfície total que um objeto pode produzir quando girado no eixo habilitado para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="c4439-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="c4439-113">O que é uma marca?</span><span class="sxs-lookup"><span data-stu-id="c4439-113">What is a tag-along?</span></span>

<span data-ttu-id="c4439-114">A marcação é um conceito comportamental que pode ser adicionado a hologramas.</span><span class="sxs-lookup"><span data-stu-id="c4439-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="c4439-115">Um objeto de marca ao longo das tentativas de permanecer em um intervalo que permite que o usuário interaja confortavelmente.</span><span class="sxs-lookup"><span data-stu-id="c4439-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="c4439-116">![O painel Pins do HoloLens é um ótimo exemplo de como a tag se comporta](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4439-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="c4439-117">*O menu Iniciar do HoloLens é um ótimo exemplo de comportamento de marcação*</span><span class="sxs-lookup"><span data-stu-id="c4439-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="c4439-118">Os objetos de marca têm parâmetros, que podem ajustar a forma com que se comportam.</span><span class="sxs-lookup"><span data-stu-id="c4439-118">Tag-along objects have parameters, which can fine-tune the way they behave.</span></span> <span data-ttu-id="c4439-119">O conteúdo pode estar dentro ou fora da linha de visão do usuário, enquanto o usuário se move em torno de seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="c4439-119">Content can be in or out of the user’s line of sight while the user moves around their environment.</span></span> <span data-ttu-id="c4439-120">À medida que você se move, o conteúdo tenta permanecer dentro do periferia do usuário, deslizando para a borda da exibição.</span><span class="sxs-lookup"><span data-stu-id="c4439-120">As you move, the content attempts to stay within the user’s periphery by sliding towards the edge of the view.</span></span> <span data-ttu-id="c4439-121">O conteúdo pode estar temporariamente fora de exibição, dependendo da rapidez com que o usuário está se movendo.</span><span class="sxs-lookup"><span data-stu-id="c4439-121">The content might be temporarily out of view depending on how quickly the user is moving.</span></span> <span data-ttu-id="c4439-122">Quando o usuário gazes em direção ao objeto de marca, ele é mais totalmente na exibição.</span><span class="sxs-lookup"><span data-stu-id="c4439-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="c4439-123">Imagine que o conteúdo esteja sempre sendo "um relance" para que os usuários nunca se esqueçam em que direção seu conteúdo está.</span><span class="sxs-lookup"><span data-stu-id="c4439-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="c4439-124">Os parâmetros extras podem fazer com que a marca de objeto fique anexada à cabeça do usuário por uma faixa de borracha.</span><span class="sxs-lookup"><span data-stu-id="c4439-124">Extra parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="c4439-125">A aceleração ou a desaceleração proporciona peso ao objeto, fazendo com que ele fique mais fisicamente presente.</span><span class="sxs-lookup"><span data-stu-id="c4439-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="c4439-126">Esse comportamento de mola é uma forma que ajuda o usuário a criar um modelo mental preciso de como o Tag-by funciona.</span><span class="sxs-lookup"><span data-stu-id="c4439-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="c4439-127">O áudio ajuda a fornecer outras indicações para quando os usuários têm objetos no modo de marca.</span><span class="sxs-lookup"><span data-stu-id="c4439-127">Audio helps provide other cues for when users have objects in tag-along mode.</span></span> <span data-ttu-id="c4439-128">O áudio deve reforçar a velocidade de movimento; uma rodada de cabeça rápida deve fornecer um efeito de som mais perceptível, ao passo que a movimentação em uma velocidade natural deve ter um mínimo ou sem efeitos de áudio.</span><span class="sxs-lookup"><span data-stu-id="c4439-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect, while walking at a natural speed should have minimal or no audio effects.</span></span>

<span data-ttu-id="c4439-129">Assim como o conteúdo realmente bloqueado, os objetos de marca podem se comprovar de forma exagerada ou nauseating se se moverem intensamente ou se acabarem muito na exibição do usuário.</span><span class="sxs-lookup"><span data-stu-id="c4439-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="c4439-130">À medida que um usuário é examinado e, em seguida, pára rapidamente, seus sentidos dizem que eles foram interrompidos.</span><span class="sxs-lookup"><span data-stu-id="c4439-130">As a user looks around, then quickly stops, their senses tell them they've stopped.</span></span> <span data-ttu-id="c4439-131">Seu saldo informa que sua cabeça parou de ser ativada e sua visão vê o mundo parar de ligar.</span><span class="sxs-lookup"><span data-stu-id="c4439-131">Their balance informs them that their head has stopped turning and their vision sees the world stop turning.</span></span> <span data-ttu-id="c4439-132">No entanto, se a marca ainda mantiver a movimentação quando o usuário for interrompido, ele poderá confundir seus sentidos.</span><span class="sxs-lookup"><span data-stu-id="c4439-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="c4439-133">Contorno e marcação em MRTK (Kit de ferramentas de realidade misturada) para o Unity</span><span class="sxs-lookup"><span data-stu-id="c4439-133">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="c4439-134">O **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts para o comportamento de etiqueta e de contorno.</span><span class="sxs-lookup"><span data-stu-id="c4439-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="c4439-135">Atribua o script do mural. cs em qualquer objeto para adicionar o comportamento da mensagem e fazer com que o objeto sempre fique à sua face.</span><span class="sxs-lookup"><span data-stu-id="c4439-135">Assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="c4439-136">Para adicionar o comportamento de marca, use o script RadialView. cs.</span><span class="sxs-lookup"><span data-stu-id="c4439-136">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="c4439-137">Você pode ajustar várias opções, como lerping time, Distance e diploma.</span><span class="sxs-lookup"><span data-stu-id="c4439-137">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="c4439-138">MRTK-solucionador de exibição radial</span><span class="sxs-lookup"><span data-stu-id="c4439-138">MRTK - Radial View Solver</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [<span data-ttu-id="c4439-139">MRTK-script do mural</span><span class="sxs-lookup"><span data-stu-id="c4439-139">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="c4439-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="c4439-140">See also</span></span>

* [<span data-ttu-id="c4439-141">Cursores</span><span class="sxs-lookup"><span data-stu-id="c4439-141">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="c4439-142">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="c4439-142">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="c4439-143">Botão</span><span class="sxs-lookup"><span data-stu-id="c4439-143">Button</span></span>](button.md)
* [<span data-ttu-id="c4439-144">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="c4439-144">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="c4439-145">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="c4439-145">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="c4439-146">Manipulação</span><span class="sxs-lookup"><span data-stu-id="c4439-146">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c4439-147">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="c4439-147">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="c4439-148">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="c4439-148">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="c4439-149">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="c4439-149">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="c4439-150">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="c4439-150">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="c4439-151">Teclado</span><span class="sxs-lookup"><span data-stu-id="c4439-151">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="c4439-152">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="c4439-152">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="c4439-153">Slate</span><span class="sxs-lookup"><span data-stu-id="c4439-153">Slate</span></span>](slate.md)
* [<span data-ttu-id="c4439-154">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="c4439-154">Slider</span></span>](slider.md)
* [<span data-ttu-id="c4439-155">Sombreador</span><span class="sxs-lookup"><span data-stu-id="c4439-155">Shader</span></span>](shader.md)
* [<span data-ttu-id="c4439-156">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="c4439-156">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="c4439-157">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="c4439-157">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="c4439-158">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="c4439-158">Surface magnetism</span></span>](surface-magnetism.md)
