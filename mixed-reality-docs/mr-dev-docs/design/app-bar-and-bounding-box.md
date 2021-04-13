---
title: Caixa delimitadora e barra de aplicativos
description: A barra de aplicativos é um menu de nível de objeto que contém uma série de botões exibidos na borda inferior dos limites de um holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Realidade mista do Windows, barra de aplicativos, caixa delimitadora, headset de realidade misturada, headset da realidade mista do Windows, headset da realidade virtual, HoloLens, MRTK, kit de ferramentas da realidade mista
ms.openlocfilehash: 0ccec5240854de9a7db6a79d5b90b97f1e6b81de
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299901"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="594c6-104">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="594c6-104">Bounding box and App bar</span></span>
<span data-ttu-id="594c6-105">![O limite é a interface padrão para a manipulação de objetos em realidade misturada.](images/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="594c6-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="594c6-106">O que é a caixa delimitadora?</span><span class="sxs-lookup"><span data-stu-id="594c6-106">What is the Bounding box?</span></span>

<span data-ttu-id="594c6-107">O limite é a interface padrão para a manipulação de objetos em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="594c6-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="594c6-108">Esse recurso fornece ao usuário uma indicação visual de que o objeto está ajustável no momento.</span><span class="sxs-lookup"><span data-stu-id="594c6-108">This feature provides the user with a visual cue that the object is currently adjustable.</span></span> <span data-ttu-id="594c6-109">No HoloLens 2, a caixa delimitadora funciona com a manipulação direta e responde à proximidade finger's do usuário.</span><span class="sxs-lookup"><span data-stu-id="594c6-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="594c6-110">Ele mostra os comentários visuais para ajudar o usuário a perceber a distância do objeto.</span><span class="sxs-lookup"><span data-stu-id="594c6-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="594c6-111">Dimensionando um objeto</span><span class="sxs-lookup"><span data-stu-id="594c6-111">Scaling an object</span></span><br>
        <span data-ttu-id="594c6-112">Os cantos da caixa delimitadora informam ao usuário que o objeto pode ser dimensionado.</span><span class="sxs-lookup"><span data-stu-id="594c6-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="594c6-113">Os identificadores seguem um padrão amplamente compreendido para ajustar a escala.</span><span class="sxs-lookup"><span data-stu-id="594c6-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="594c6-114">Esta indicação visual mostra aos usuários a área total do objeto – mesmo se ele não estiver visível fora de um modo de ajuste.</span><span class="sxs-lookup"><span data-stu-id="594c6-114">This visual cue shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="594c6-115">Sem esse recurso, um objeto encaixado em outro objeto ou superfície pode parecer se comportando como havia espaço em si que não deveria estar lá.</span><span class="sxs-lookup"><span data-stu-id="594c6-115">Without this feature, an object snapped to another object or surface may appear to behave like there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="594c6-116">*Loop de vídeo: dimensionando um objeto por meio da caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="594c6-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="594c6-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="594c6-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="594c6-118">![Ponto de exibição do HoloLens para dimensionar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="594c6-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="594c6-119">Girando um objeto</span><span class="sxs-lookup"><span data-stu-id="594c6-119">Rotating an object</span></span><br>
        <span data-ttu-id="594c6-120">Os capacidades retangulares verticais nas bordas da caixa delimitadora são indicadores de rotação.</span><span class="sxs-lookup"><span data-stu-id="594c6-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="594c6-121">Isso dá ao usuário um ajuste mais fino sobre seus hologramas posicionados.</span><span class="sxs-lookup"><span data-stu-id="594c6-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="594c6-122">Elas não só podem ser ajustadas e dimensionadas, mas agora giram também.</span><span class="sxs-lookup"><span data-stu-id="594c6-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="594c6-123">*Loop de vídeo: girando um objeto por meio da caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="594c6-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="594c6-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="594c6-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="594c6-125">![Ponto de exibição do HoloLens para girar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="594c6-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="594c6-126">Comentário visual sobre a proximidade no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="594c6-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="594c6-127">No HoloLens 2, há uma indicação visual extra, que pode ajudar a percepção de profundidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="594c6-127">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="594c6-128">Um anel próximo a ele é exibido e escala verticalmente conforme o alcance fica mais próximo do objeto.</span><span class="sxs-lookup"><span data-stu-id="594c6-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="594c6-129">O anel, eventualmente, convergi em um ponto quando o estado pressionado é atingido.</span><span class="sxs-lookup"><span data-stu-id="594c6-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="594c6-130">Essa unificação Visual ajuda o usuário a entender a distância deles do objeto.</span><span class="sxs-lookup"><span data-stu-id="594c6-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="594c6-131">*Loop de vídeo: exemplo de comentários visuais com base na proximidade a uma caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="594c6-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="594c6-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="594c6-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="594c6-133">![Comentário visual sobre a proximidade](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="594c6-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="594c6-134">**Para o desenvolvimento de aplicativos do Unity, consulte [a caixa delimitadora no kit de ferramentas da realidade misturada-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="594c6-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="594c6-135">O que é a barra de aplicativos?</span><span class="sxs-lookup"><span data-stu-id="594c6-135">What is the App bar?</span></span>

<span data-ttu-id="594c6-136">A barra de aplicativos é um menu de nível de objeto, que contém uma série de botões exibidos na borda inferior dos limites de um holograma.</span><span class="sxs-lookup"><span data-stu-id="594c6-136">The App bar is an object-level menu, which contains a series of buttons displayed on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="594c6-137">Esse padrão é comumente usado para permitir que os usuários removam e ajustem os hologramas.</span><span class="sxs-lookup"><span data-stu-id="594c6-137">This pattern is commonly used to let users remove and adjust holograms.</span></span> <span data-ttu-id="594c6-138">A barra de aplicativos foi projetada principalmente como uma maneira de gerenciar objetos posicionados no ambiente de um usuário.</span><span class="sxs-lookup"><span data-stu-id="594c6-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="594c6-139">Junto com a caixa delimitadora, um usuário tem controle total sobre onde e como os objetos são orientados em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="594c6-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="594c6-140">A barra de aplicativos segue o usuário</span><span class="sxs-lookup"><span data-stu-id="594c6-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="594c6-141">Como esse padrão é usado com objetos que são protegidos pelo mundo, à medida que um usuário se move pelo objeto, a barra de aplicativos sempre será exibida no lado dos objetos mais próximo do usuário.</span><span class="sxs-lookup"><span data-stu-id="594c6-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="594c6-142">Embora não seja tecnicamente, esse recurso atinge efetivamente o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="594c6-142">While not technically billboarding, this feature effectively achieves the same result.</span></span> <span data-ttu-id="594c6-143">Impedir que a posição de um usuário occlude ou bloqueie a funcionalidade que, de outra forma, estaria disponível em um local diferente em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="594c6-143">Preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="594c6-144">*Loop de vídeo: percorrendo um holograma, a barra de aplicativos segue*</span><span class="sxs-lookup"><span data-stu-id="594c6-144">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="594c6-145">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="594c6-145">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="594c6-146">![Percorrendo um holograma.</span><span class="sxs-lookup"><span data-stu-id="594c6-146">![Walking around a hologram.</span></span> <span data-ttu-id="594c6-147">A barra de aplicativos é a seguinte.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="594c6-147">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="594c6-148">Caixa delimitadora no MRTK (Kit de ferramentas de realidade misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="594c6-148">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="594c6-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts e pré-fabricados para a caixa delimitadora e a barra de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="594c6-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="594c6-150">Você pode adicionar uma caixa delimitadora atribuindo o script BoundingBox. cs em qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="594c6-150">You can add a Bounding box by assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="594c6-151">MRTK-caixa delimitadora</span><span class="sxs-lookup"><span data-stu-id="594c6-151">MRTK - Bounding Box</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a><span data-ttu-id="594c6-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="594c6-152">See also</span></span>

* [<span data-ttu-id="594c6-153">Cursores</span><span class="sxs-lookup"><span data-stu-id="594c6-153">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="594c6-154">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="594c6-154">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="594c6-155">Botão</span><span class="sxs-lookup"><span data-stu-id="594c6-155">Button</span></span>](button.md)
* [<span data-ttu-id="594c6-156">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="594c6-156">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="594c6-157">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="594c6-157">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="594c6-158">Manipulação</span><span class="sxs-lookup"><span data-stu-id="594c6-158">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="594c6-159">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="594c6-159">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="594c6-160">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="594c6-160">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="594c6-161">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="594c6-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="594c6-162">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="594c6-162">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="594c6-163">Teclado</span><span class="sxs-lookup"><span data-stu-id="594c6-163">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="594c6-164">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="594c6-164">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="594c6-165">Slate</span><span class="sxs-lookup"><span data-stu-id="594c6-165">Slate</span></span>](slate.md)
* [<span data-ttu-id="594c6-166">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="594c6-166">Slider</span></span>](slider.md)
* [<span data-ttu-id="594c6-167">Sombreador</span><span class="sxs-lookup"><span data-stu-id="594c6-167">Shader</span></span>](shader.md)
* [<span data-ttu-id="594c6-168">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="594c6-168">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="594c6-169">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="594c6-169">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="594c6-170">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="594c6-170">Surface magnetism</span></span>](surface-magnetism.md)
