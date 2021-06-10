---
title: Botão
description: Saiba como disparar uma ação imediata com botões, que é um dos componentes fundamentais da realidade misturada.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realidade misturada, controles, interação, interface do usuário, UX, headset de realidade misturada, headset da realidade mista do Windows, headset da realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada, botão
ms.openlocfilehash: ddad8b23950bddd03dd4024497c212d1cc950fb0
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600365"
---
# <a name="button"></a><span data-ttu-id="6a022-104">Botão</span><span class="sxs-lookup"><span data-stu-id="6a022-104">Button</span></span>

![Botão](images/UX_Hero_Button.jpg)

<span data-ttu-id="6a022-106">Um botão permite que os usuários disparem ações imediatas em uma experiência de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="6a022-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="6a022-107">No HoloLens 2, os botões têm indicações visuais e capacidades que ajudam a aumentar a confiança de interação com os usuários.</span><span class="sxs-lookup"><span data-stu-id="6a022-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="6a022-108">![Botão com efeito de luz de proximidade mostrado](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="6a022-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="6a022-109">**Luz de proximidade**</span><span class="sxs-lookup"><span data-stu-id="6a022-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6a022-110">![Botão selecionado com o efeito de realce de foco mostrado](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="6a022-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="6a022-111">**Realce de foco**</span><span class="sxs-lookup"><span data-stu-id="6a022-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="6a022-112">![Botão sendo pressionado com o efeito de compartimento de compactação mostrado](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="6a022-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="6a022-113">**Compactando o compartimento**</span><span class="sxs-lookup"><span data-stu-id="6a022-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6a022-114">![Botão sendo pressionado com efeito de pulso de gatilho mostrado](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="6a022-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="6a022-115">**Pulso no gatilho**</span><span class="sxs-lookup"><span data-stu-id="6a022-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="6a022-116">Botão no MRTK (Kit de ferramentas de realidade misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="6a022-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="6a022-117">O **[MRTK para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece vários tipos de pré-fabricados de botão, incluindo botões de estilo de Shell para o hololens 2 e o hololens (1ª gen).</span><span class="sxs-lookup"><span data-stu-id="6a022-117">**[MRTK for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="6a022-118">O botão do HoloLens 2 pré-fabricado contém vários capacidades detalhados que ajudam a melhorar a confiança do usuário:</span><span class="sxs-lookup"><span data-stu-id="6a022-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="6a022-119">Realce baseado em proximidade</span><span class="sxs-lookup"><span data-stu-id="6a022-119">Proximity-based highlight</span></span>
* <span data-ttu-id="6a022-120">Compactando o front-end</span><span class="sxs-lookup"><span data-stu-id="6a022-120">Compressing front cage</span></span>
* <span data-ttu-id="6a022-121">Efeito de pulso no gatilho.</span><span class="sxs-lookup"><span data-stu-id="6a022-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="6a022-122">Confira o [botão MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) para obter mais instruções e exemplos personalizados.</span><span class="sxs-lookup"><span data-stu-id="6a022-122">Check out the [MRTK - Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="6a022-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="6a022-123">See also</span></span>

* [<span data-ttu-id="6a022-124">Cursores</span><span class="sxs-lookup"><span data-stu-id="6a022-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="6a022-125">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="6a022-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="6a022-126">Botão</span><span class="sxs-lookup"><span data-stu-id="6a022-126">Button</span></span>](button.md)
* [<span data-ttu-id="6a022-127">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="6a022-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="6a022-128">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="6a022-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="6a022-129">Manipulação</span><span class="sxs-lookup"><span data-stu-id="6a022-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6a022-130">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="6a022-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="6a022-131">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="6a022-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="6a022-132">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="6a022-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="6a022-133">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="6a022-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="6a022-134">Teclado</span><span class="sxs-lookup"><span data-stu-id="6a022-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="6a022-135">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="6a022-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="6a022-136">Slate</span><span class="sxs-lookup"><span data-stu-id="6a022-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="6a022-137">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="6a022-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="6a022-138">Sombreador</span><span class="sxs-lookup"><span data-stu-id="6a022-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="6a022-139">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="6a022-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="6a022-140">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="6a022-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="6a022-141">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="6a022-141">Surface magnetism</span></span>](surface-magnetism.md)