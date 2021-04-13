---
title: Sombreador
description: Saiba como o sombreador standard do kit de ferramentas de realidade misturada fornece vários tipos de efeitos visuais que podem ser usados com hologramas em seus aplicativos de realidade misturada.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realidade misturada, controles, interação, interface do usuário, UX, sombreador, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada, efeitos visuais
ms.openlocfilehash: 4bf8205ac9dfbd22a0deb9ffe796fd4e33a96f89
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300381"
---
# <a name="shader"></a><span data-ttu-id="3dd89-104">Sombreador</span><span class="sxs-lookup"><span data-stu-id="3dd89-104">Shader</span></span>

![Sombreador](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="3dd89-106">Como os objetos Holographic são misturados com os físicos no ambiente real, é importante fornecer indicações visuais ao usuário.</span><span class="sxs-lookup"><span data-stu-id="3dd89-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="3dd89-107">O sombreador standard do kit de ferramentas de realidade misturada fornece vários tipos de efeitos visuais para uso com hologramas.</span><span class="sxs-lookup"><span data-stu-id="3dd89-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="3dd89-108">O sistema de sombreamento usa um sombreador único e flexível para obter visuais semelhantes ao sombreador padrão do Unity.</span><span class="sxs-lookup"><span data-stu-id="3dd89-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="3dd89-109">O sombreador implementa [princípios de sistema de design fluente](https://www.microsoft.com/design/fluent/#/) e permanece em bom desempenho em dispositivos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="3dd89-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="3dd89-110">Exemplos de efeitos visuais usando o sombreador padrão MRTK (Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="3dd89-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="3dd89-111">![Mover](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="3dd89-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="3dd89-112">**Luz de proximidade**</span><span class="sxs-lookup"><span data-stu-id="3dd89-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3dd89-113">![Girar](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="3dd89-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="3dd89-114">**Luz de borda**</span><span class="sxs-lookup"><span data-stu-id="3dd89-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="3dd89-115">Sombreador padrão no MRTK para Unity</span><span class="sxs-lookup"><span data-stu-id="3dd89-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="3dd89-116">MRTK-sombreador padrão</span><span class="sxs-lookup"><span data-stu-id="3dd89-116">MRTK - Standard shader</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="3dd89-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="3dd89-117">See also</span></span>

* [<span data-ttu-id="3dd89-118">Cursores</span><span class="sxs-lookup"><span data-stu-id="3dd89-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="3dd89-119">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="3dd89-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="3dd89-120">Botão</span><span class="sxs-lookup"><span data-stu-id="3dd89-120">Button</span></span>](button.md)
* [<span data-ttu-id="3dd89-121">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="3dd89-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="3dd89-122">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="3dd89-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="3dd89-123">Manipulação</span><span class="sxs-lookup"><span data-stu-id="3dd89-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3dd89-124">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="3dd89-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="3dd89-125">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="3dd89-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="3dd89-126">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="3dd89-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="3dd89-127">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="3dd89-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="3dd89-128">Teclado</span><span class="sxs-lookup"><span data-stu-id="3dd89-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="3dd89-129">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="3dd89-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="3dd89-130">Slate</span><span class="sxs-lookup"><span data-stu-id="3dd89-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="3dd89-131">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="3dd89-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="3dd89-132">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="3dd89-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="3dd89-133">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="3dd89-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="3dd89-134">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="3dd89-134">Surface magnetism</span></span>](surface-magnetism.md)
