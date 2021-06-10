---
title: Caixa delimitadora e barra de aplicativos
description: A barra aplicativo é um menu de nível de objeto que contém uma série de botões exibidos na borda inferior dos limites de um holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra de aplicativos, caixa delimitada, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada
ms.openlocfilehash: 750fb238e5b7f22998a86f71607498c8f6982076
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600515"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="e2aa0-104">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="e2aa0-104">Bounding box and App bar</span></span>
<span data-ttu-id="e2aa0-105">![Delimitação é a interface padrão para manipulação de objetos na Realidade Misturada.](images/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="e2aa0-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="e2aa0-106">O que é a caixa Delimitando?</span><span class="sxs-lookup"><span data-stu-id="e2aa0-106">What is the Bounding box?</span></span>

<span data-ttu-id="e2aa0-107">Delimitação é a interface padrão para manipulação de objetos na Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="e2aa0-108">Esse recurso fornece ao usuário uma indicação visual de que o objeto está atualmente ajustável.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-108">This feature provides the user with a visual cue that the object is currently adjustable.</span></span> <span data-ttu-id="e2aa0-109">No HoloLens 2, a caixa delimitada funciona com manipulação direta da mão e responde à proximidade do dedo do usuário.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="e2aa0-110">Ele mostra comentários visuais para ajudar o usuário a perceber a distância do objeto.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="e2aa0-111">Dimensionamento de um objeto</span><span class="sxs-lookup"><span data-stu-id="e2aa0-111">Scaling an object</span></span><br>
        <span data-ttu-id="e2aa0-112">Os cantos da caixa delimitada dizem ao usuário que o objeto pode ser dimensionado.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="e2aa0-113">Os alças seguem um padrão amplamente compreendido para ajustar a escala.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="e2aa0-114">Essa indicação visual mostra aos usuários a área total do objeto , mesmo que ele não seja visível fora de um modo de ajuste.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-114">This visual cue shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="e2aa0-115">Sem esse recurso, um objeto encaixado em outro objeto ou superfície pode parecer se comportar como se houvesse espaço ao redor dele que não deveria estar lá.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-115">Without this feature, an object snapped to another object or surface may appear to behave like there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="e2aa0-116">*Loop de vídeo: Dimensionamento de um objeto por meio de caixa delimitada*</span><span class="sxs-lookup"><span data-stu-id="e2aa0-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="e2aa0-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="e2aa0-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="e2aa0-118">![Ponto de vista do HoloLens de dimensionamento de um objeto por meio de caixa delimitada](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="e2aa0-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="e2aa0-119">Girar um objeto</span><span class="sxs-lookup"><span data-stu-id="e2aa0-119">Rotating an object</span></span><br>
        <span data-ttu-id="e2aa0-120">As acessível retangulares verticais nas bordas da caixa delimitada são indicadores de rotação.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="e2aa0-121">Isso fornece ao usuário um ajuste mais fino sobre seus hologramas colocados.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="e2aa0-122">Eles não só podem ajustar e dimensionar, mas agora girar também.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="e2aa0-123">*Loop de vídeo: girar um objeto por meio de uma caixa delimitada*</span><span class="sxs-lookup"><span data-stu-id="e2aa0-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="e2aa0-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="e2aa0-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="e2aa0-125">![Ponto de vista do HoloLens da rotação de um objeto por meio de caixa delimitada](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="e2aa0-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="e2aa0-126">Comentários visuais sobre proximidade manual no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e2aa0-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="e2aa0-127">No HoloLens 2, há uma indicação visual extra, que pode ajudar a percepção de profundidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-127">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="e2aa0-128">Um anel próximo à ponta do dedo aparece e é escalado para baixo à medida que a ponta do dedo se aproxima do objeto.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="e2aa0-129">O anel eventualmente convergirá para um ponto quando o estado pressionado for atingido.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="e2aa0-130">Essa governança visual ajuda o usuário a entender a distância do objeto.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="e2aa0-131">*Loop de vídeo: exemplo de comentários visuais com base na proximidade de uma caixa delimitada*</span><span class="sxs-lookup"><span data-stu-id="e2aa0-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="e2aa0-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="e2aa0-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="e2aa0-133">![Comentários visuais sobre proximidade da mão](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="e2aa0-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="e2aa0-134">**Para o desenvolvimento de aplicativos do Unity, consulte Caixa delimitativa no Kit de Ferramentas de [Realidade Misturada –Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="e2aa0-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="e2aa0-135">O que é a barra de aplicativos?</span><span class="sxs-lookup"><span data-stu-id="e2aa0-135">What is the App bar?</span></span>

<span data-ttu-id="e2aa0-136">A barra aplicativo é um menu de nível de objeto, que contém uma série de botões exibidos na borda inferior dos limites de um holograma.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-136">The App bar is an object-level menu, which contains a series of buttons displayed on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="e2aa0-137">Esse padrão é normalmente usado para permitir que os usuários removam e ajustem hologramas.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-137">This pattern is commonly used to let users remove and adjust holograms.</span></span> <span data-ttu-id="e2aa0-138">A barra aplicativo foi projetada principalmente como uma maneira de gerenciar objetos colocados no ambiente de um usuário.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="e2aa0-139">Juntamente com a caixa delimitada, um usuário tem controle total sobre onde e como os objetos são orientados na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="e2aa0-140">A barra aplicativo segue o usuário</span><span class="sxs-lookup"><span data-stu-id="e2aa0-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="e2aa0-141">Como esse padrão é usado com objetos que estão bloqueados pelo mundo, à medida que um usuário se move ao redor do objeto, a barra de aplicativos sempre será exibida no lado dos objetos mais próximos do usuário.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="e2aa0-142">Embora tecnicamente não seja o mesmo, esse recurso efetivamente atinge o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-142">While not technically billboarding, this feature effectively achieves the same result.</span></span> <span data-ttu-id="e2aa0-143">Impedir que a posição de um usuário oclua ou bloqueie a funcionalidade que, de outra forma, estaria disponível em um local diferente em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-143">Preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="e2aa0-144">*Loop de vídeo: passeando em torno de um holograma, a barra de aplicativos segue*</span><span class="sxs-lookup"><span data-stu-id="e2aa0-144">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="e2aa0-145">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="e2aa0-145">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="e2aa0-146">![Passeando em torno de um holograma.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-146">![Walking around a hologram.</span></span> <span data-ttu-id="e2aa0-147">A barra Aplicativo segue.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="e2aa0-147">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="e2aa0-148">Caixa delimitativa no MRTK (Kit de Ferramentas de Realidade Misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="e2aa0-148">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="e2aa0-149">**[O MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts e pré-fabs para a caixa Delimitadores e a barra de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="e2aa0-150">Você pode adicionar uma caixa Delimitando atribuindo o script BoundingBox.cs a qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="e2aa0-150">You can add a Bounding box by assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="e2aa0-151">MRTK – Caixa delimitada</span><span class="sxs-lookup"><span data-stu-id="e2aa0-151">MRTK - Bounding Box</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a><span data-ttu-id="e2aa0-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="e2aa0-152">See also</span></span>

* [<span data-ttu-id="e2aa0-153">Cursores</span><span class="sxs-lookup"><span data-stu-id="e2aa0-153">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="e2aa0-154">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="e2aa0-154">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="e2aa0-155">Botão</span><span class="sxs-lookup"><span data-stu-id="e2aa0-155">Button</span></span>](button.md)
* [<span data-ttu-id="e2aa0-156">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="e2aa0-156">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e2aa0-157">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="e2aa0-157">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="e2aa0-158">Manipulação</span><span class="sxs-lookup"><span data-stu-id="e2aa0-158">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e2aa0-159">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="e2aa0-159">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="e2aa0-160">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="e2aa0-160">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="e2aa0-161">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="e2aa0-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="e2aa0-162">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="e2aa0-162">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="e2aa0-163">Teclado</span><span class="sxs-lookup"><span data-stu-id="e2aa0-163">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="e2aa0-164">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="e2aa0-164">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="e2aa0-165">Slate</span><span class="sxs-lookup"><span data-stu-id="e2aa0-165">Slate</span></span>](slate.md)
* [<span data-ttu-id="e2aa0-166">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="e2aa0-166">Slider</span></span>](slider.md)
* [<span data-ttu-id="e2aa0-167">Sombreador</span><span class="sxs-lookup"><span data-stu-id="e2aa0-167">Shader</span></span>](shader.md)
* [<span data-ttu-id="e2aa0-168">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="e2aa0-168">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="e2aa0-169">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="e2aa0-169">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="e2aa0-170">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="e2aa0-170">Surface magnetism</span></span>](surface-magnetism.md)