---
title: Mural e tag-along
description: Saiba como usar objetos com mistas, que sempre se orientam para enfrentar o usuário em aplicativos de realidade misturada.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, marcação, marcação, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada
ms.openlocfilehash: 0bd1ac2168284d714240c6775468a61ed3e665b8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600335"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="01d03-104">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="01d03-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="01d03-105">O que é a reação de dados?</span><span class="sxs-lookup"><span data-stu-id="01d03-105">What is billboarding?</span></span>

<span data-ttu-id="01d03-106">A mista é um conceito comportamental que pode ser aplicado a objetos na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="01d03-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="01d03-107">Objetos com o uso de objetos sempre se orientam para enfrentar o usuário.</span><span class="sxs-lookup"><span data-stu-id="01d03-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="01d03-108">Sistemas de texto e menu são casos de uso comuns, em que objetos estáticos colocados no ambiente do usuário (bloqueados pelo mundo) seriam obscurecidos ou ilegíveis quando os usuários se movimentam.</span><span class="sxs-lookup"><span data-stu-id="01d03-108">Text and menu systems are common use cases, where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable when users move around.</span></span>

<span data-ttu-id="01d03-109">Objetos com a reação de dados habilitada podem girar livremente no ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="01d03-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="01d03-110">Eles também podem ser restritos a um único eixo, dependendo das considerações de design.</span><span class="sxs-lookup"><span data-stu-id="01d03-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="01d03-111">Lembre-se de que objetos com recodados podem ser repassados ou ocluir a si mesmos quando colocados muito próximos de outros objetos ou, no HoloLens, superfícies examinadas muito próximas.</span><span class="sxs-lookup"><span data-stu-id="01d03-111">Keep in mind, billboarded objects can clip or occlude themselves when placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="01d03-112">Para evitar isso, pense no volume total que um objeto pode produzir quando girado no eixo habilitado para a rotação.</span><span class="sxs-lookup"><span data-stu-id="01d03-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="01d03-113">O que é um tag-along?</span><span class="sxs-lookup"><span data-stu-id="01d03-113">What is a tag-along?</span></span>

<span data-ttu-id="01d03-114">O tag-along é um conceito comportamental que pode ser adicionado aos hologramas.</span><span class="sxs-lookup"><span data-stu-id="01d03-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="01d03-115">Um objeto de marcação ao longo tenta permanecer em um intervalo que permite que o usuário interaja de maneira confortável.</span><span class="sxs-lookup"><span data-stu-id="01d03-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="01d03-116">![O painel de pinos do HoloLens é um ótimo exemplo de como o tag-along se comporta](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="01d03-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="01d03-117">*O menu Iniciar HoloLens é um ótimo exemplo de comportamento de tag-along*</span><span class="sxs-lookup"><span data-stu-id="01d03-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="01d03-118">Os objetos de marcação têm parâmetros, que podem ajustar a maneira como se comportam.</span><span class="sxs-lookup"><span data-stu-id="01d03-118">Tag-along objects have parameters, which can fine-tune the way they behave.</span></span> <span data-ttu-id="01d03-119">O conteúdo pode estar dentro ou fora da linha de visão do usuário enquanto o usuário se move em torno de seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="01d03-119">Content can be in or out of the user’s line of sight while the user moves around their environment.</span></span> <span data-ttu-id="01d03-120">Conforme você se move, o conteúdo tenta permanecer dentro da periférico do usuário deslizando para a borda da exibição.</span><span class="sxs-lookup"><span data-stu-id="01d03-120">As you move, the content attempts to stay within the user’s periphery by sliding towards the edge of the view.</span></span> <span data-ttu-id="01d03-121">O conteúdo pode estar temporariamente fora de exibição, dependendo da rapidez com que o usuário está se movendo.</span><span class="sxs-lookup"><span data-stu-id="01d03-121">The content might be temporarily out of view depending on how quickly the user is moving.</span></span> <span data-ttu-id="01d03-122">Quando o usuário se volta para o objeto tag-along, ele fica mais totalmente em exibição.</span><span class="sxs-lookup"><span data-stu-id="01d03-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="01d03-123">Pense no conteúdo sempre sendo "um relance" para que os usuários nunca se esqueça em qual direção seu conteúdo está.</span><span class="sxs-lookup"><span data-stu-id="01d03-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="01d03-124">Parâmetros extras podem fazer com que o objeto de marcação ao longo se sinta anexado à cabeça do usuário por uma faixa de borracha.</span><span class="sxs-lookup"><span data-stu-id="01d03-124">Extra parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="01d03-125">A aceleração ou a desaceleração mais intensas dão peso ao objeto, fazendo com que ele se sinta fisicamente mais presente.</span><span class="sxs-lookup"><span data-stu-id="01d03-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="01d03-126">Esse comportamento spring é uma capacidade que ajuda o usuário a criar um modelo mental preciso de como o tag-along funciona.</span><span class="sxs-lookup"><span data-stu-id="01d03-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="01d03-127">O áudio ajuda a fornecer outras dicas para quando os usuários têm objetos no modo de tag-along.</span><span class="sxs-lookup"><span data-stu-id="01d03-127">Audio helps provide other cues for when users have objects in tag-along mode.</span></span> <span data-ttu-id="01d03-128">O áudio deve reforçar a velocidade de movimentação; um turno de cabeça rápido deve fornecer um efeito de som mais perceptível, enquanto o trabalho em uma velocidade natural deve ter efeitos de áudio mínimos ou não.</span><span class="sxs-lookup"><span data-stu-id="01d03-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect, while walking at a natural speed should have minimal or no audio effects.</span></span>

<span data-ttu-id="01d03-129">Assim como o conteúdo realmente com a cabeça bloqueada, os objetos de marcação podem se mostrar avassaladores ou desalocar se eles se movem muito ou soltam muito na exibição do usuário.</span><span class="sxs-lookup"><span data-stu-id="01d03-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="01d03-130">À medida que um usuário procura e, em seguida, para rapidamente, seus sentidoes dizem que ele parou.</span><span class="sxs-lookup"><span data-stu-id="01d03-130">As a user looks around, then quickly stops, their senses tell them they've stopped.</span></span> <span data-ttu-id="01d03-131">Seu equilíbrio informa que sua cabeça parou de girar e sua visão vê o mundo parar de girar.</span><span class="sxs-lookup"><span data-stu-id="01d03-131">Their balance informs them that their head has stopped turning and their vision sees the world stop turning.</span></span> <span data-ttu-id="01d03-132">No entanto, se o tag-along continuar se movendo quando o usuário tiver parado, isso poderá confundir seus sentidos.</span><span class="sxs-lookup"><span data-stu-id="01d03-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="01d03-133">Mistas e marcações no MRTK (Kit de Ferramentas de Realidade Misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="01d03-133">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="01d03-134">**[O MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts para o comportamento de Marcação e Marcação.</span><span class="sxs-lookup"><span data-stu-id="01d03-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="01d03-135">Atribua o script Dem.cs a qualquer objeto para adicionar o comportamento de minguação e fazer com que o objeto sempre o despente.</span><span class="sxs-lookup"><span data-stu-id="01d03-135">Assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="01d03-136">Para adicionar o comportamento de tag-along, use o script RadialView.cs.</span><span class="sxs-lookup"><span data-stu-id="01d03-136">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="01d03-137">Você pode ajustar várias opções, como tempo de leitura, distância e grau.</span><span class="sxs-lookup"><span data-stu-id="01d03-137">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="01d03-138">MRTK – Solucionador de Exibição Radial</span><span class="sxs-lookup"><span data-stu-id="01d03-138">MRTK - Radial View Solver</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [<span data-ttu-id="01d03-139">MRTK – Script de Script de Script do MrTK</span><span class="sxs-lookup"><span data-stu-id="01d03-139">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="01d03-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="01d03-140">See also</span></span>

* [<span data-ttu-id="01d03-141">Cursores</span><span class="sxs-lookup"><span data-stu-id="01d03-141">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="01d03-142">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="01d03-142">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="01d03-143">Botão</span><span class="sxs-lookup"><span data-stu-id="01d03-143">Button</span></span>](button.md)
* [<span data-ttu-id="01d03-144">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="01d03-144">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="01d03-145">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="01d03-145">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="01d03-146">Manipulação</span><span class="sxs-lookup"><span data-stu-id="01d03-146">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="01d03-147">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="01d03-147">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="01d03-148">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="01d03-148">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="01d03-149">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="01d03-149">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="01d03-150">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="01d03-150">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="01d03-151">Teclado</span><span class="sxs-lookup"><span data-stu-id="01d03-151">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="01d03-152">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="01d03-152">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="01d03-153">Slate</span><span class="sxs-lookup"><span data-stu-id="01d03-153">Slate</span></span>](slate.md)
* [<span data-ttu-id="01d03-154">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="01d03-154">Slider</span></span>](slider.md)
* [<span data-ttu-id="01d03-155">Sombreador</span><span class="sxs-lookup"><span data-stu-id="01d03-155">Shader</span></span>](shader.md)
* [<span data-ttu-id="01d03-156">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="01d03-156">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="01d03-157">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="01d03-157">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="01d03-158">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="01d03-158">Surface magnetism</span></span>](surface-magnetism.md)