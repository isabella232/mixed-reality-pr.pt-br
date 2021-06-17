---
title: Coleção de objetos
description: A coleção de objetos é um controle de layout, que ajuda você a estabelecer uma matriz de objetos em uma forma tridimensional predefinida.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, controles, design, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, coleção de objetos, 2D, 3D, MRTK, Kit de Ferramentas de Realidade Misturada
ms.openlocfilehash: fd5629f58e092b33410c833885037582ba5ca4a1
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110134"
---
# <a name="object-collection"></a><span data-ttu-id="8b7b9-104">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="8b7b9-104">Object collection</span></span>

![Coleção de objetos usada na Tabela Periódica do aplicativo Elements](images/UX_Hero_ObjectCollection.jpg)<br>

<span data-ttu-id="8b7b9-106">A coleção de objetos é um controle de layout, que ajuda você a estabelecer uma matriz de objetos em uma forma tridimensional predefinida.</span><span class="sxs-lookup"><span data-stu-id="8b7b9-106">Object collection is a layout control, which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="8b7b9-107">Ele dá suporte a vários estilos de superfície – \*\*plano, cilindro, esfera e **radial.**</span><span class="sxs-lookup"><span data-stu-id="8b7b9-107">It supports various surface styles - \*\*plane, cylinder, sphere, and **radial**.</span></span> <span data-ttu-id="8b7b9-108">Você pode ajustar o raio e o tamanho dos objetos e o espaço entre eles.</span><span class="sxs-lookup"><span data-stu-id="8b7b9-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="8b7b9-109">A coleção de objetos dá suporte a qualquer objeto do Unity – 2D e 3D.</span><span class="sxs-lookup"><span data-stu-id="8b7b9-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="8b7b9-110">No Kit **[de Ferramentas de Realidade](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)** Misturada , criamos o script do Unity e exemplos que ajudarão você a criar uma coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="8b7b9-110">In the **[Mixed Reality Toolkit](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)**, we have created Unity script and examples that will help you create an object collection.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="8b7b9-111">Exemplos de coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="8b7b9-111">Object collection examples</span></span>

<span data-ttu-id="8b7b9-112">[Tabela periódica dos elementos é um](../develop/unity/periodic-table-of-the-elements.md) aplicativo de exemplo que demonstra como a coleção de objetos funciona.</span><span class="sxs-lookup"><span data-stu-id="8b7b9-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="8b7b9-113">Ele usa a Coleção de objetos para estabelecer caixas de elementos 3D de elementos 3D em formas diferentes.</span><span class="sxs-lookup"><span data-stu-id="8b7b9-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="8b7b9-114">![Exemplos de coleção de objetos mostrados na Tabela Periódica do aplicativo Elements](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8b7b9-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="8b7b9-115">*Exemplos de coleção de objetos mostrados na Tabela Periódica do aplicativo de exemplo Elements*</span><span class="sxs-lookup"><span data-stu-id="8b7b9-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="8b7b9-116">Objetos 3D</span><span class="sxs-lookup"><span data-stu-id="8b7b9-116">3D objects</span></span>

<span data-ttu-id="8b7b9-117">Você pode usar a Coleção de objetos para estabelecer objetos 3D importados.</span><span class="sxs-lookup"><span data-stu-id="8b7b9-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="8b7b9-118">O exemplo a seguir mostra um plano e um layout de cilindro de alguns objetos de mesa 3D.</span><span class="sxs-lookup"><span data-stu-id="8b7b9-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="8b7b9-119">![Exemplos de layouts cilíndricos e plano de objetos 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8b7b9-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="8b7b9-120">*Exemplos de layouts cilíndricos e plano de objetos 3D*</span><span class="sxs-lookup"><span data-stu-id="8b7b9-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="8b7b9-121">Objetos 2D</span><span class="sxs-lookup"><span data-stu-id="8b7b9-121">2D objects</span></span>

<span data-ttu-id="8b7b9-122">Você também pode usar imagens 2D com a coleção Object.</span><span class="sxs-lookup"><span data-stu-id="8b7b9-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="8b7b9-123">Os exemplos a seguir demonstram como imagens 2D podem ser exibidas em uma grade.</span><span class="sxs-lookup"><span data-stu-id="8b7b9-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Um exemplo de imagens 2D com a coleção Object](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="8b7b9-125">![Exemplos de como usar a coleção de objetos com imagens 2D](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="8b7b9-125">![Examples of using object collection with 2D images](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="8b7b9-126">*Exemplos de como usar a coleção de objetos com imagens 2D*</span><span class="sxs-lookup"><span data-stu-id="8b7b9-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="8b7b9-127">Coleção de objetos no MRTK (Kit de Ferramentas de Realidade Misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="8b7b9-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="8b7b9-128">MRTK – Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="8b7b9-128">MRTK - Object collection</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)

<br>

---

## <a name="see-also"></a><span data-ttu-id="8b7b9-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="8b7b9-129">See also</span></span>

* [<span data-ttu-id="8b7b9-130">Cursores</span><span class="sxs-lookup"><span data-stu-id="8b7b9-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="8b7b9-131">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="8b7b9-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="8b7b9-132">Botão</span><span class="sxs-lookup"><span data-stu-id="8b7b9-132">Button</span></span>](button.md)
* [<span data-ttu-id="8b7b9-133">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="8b7b9-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="8b7b9-134">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="8b7b9-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="8b7b9-135">Manipulação</span><span class="sxs-lookup"><span data-stu-id="8b7b9-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8b7b9-136">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="8b7b9-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="8b7b9-137">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="8b7b9-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="8b7b9-138">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="8b7b9-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="8b7b9-139">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="8b7b9-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="8b7b9-140">Teclado</span><span class="sxs-lookup"><span data-stu-id="8b7b9-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="8b7b9-141">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="8b7b9-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="8b7b9-142">Slate</span><span class="sxs-lookup"><span data-stu-id="8b7b9-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="8b7b9-143">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="8b7b9-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="8b7b9-144">Sombreador</span><span class="sxs-lookup"><span data-stu-id="8b7b9-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="8b7b9-145">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="8b7b9-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="8b7b9-146">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="8b7b9-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="8b7b9-147">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="8b7b9-147">Surface magnetism</span></span>](surface-magnetism.md)