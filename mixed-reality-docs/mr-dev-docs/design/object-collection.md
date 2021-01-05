---
title: Coleção de objetos
description: A coleção de objetos é um controle de layout, que ajuda você a dispor uma matriz de objetos em uma forma tridimensional predefinida.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, controles, design, headset de realidade misturada, headset da realidade mista do Windows, headset da realidade virtual, HoloLens, coleta de objetos, 2D, 3D, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: a459d03246b8df4c17d523f57ece54997849c209
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847214"
---
# <a name="object-collection"></a><span data-ttu-id="ccfc1-104">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="ccfc1-104">Object collection</span></span>

![Coleção de objetos usada na tabela periódica do aplicativo de elementos](images/UX_Hero_ObjectCollection.jpg)<br>

<span data-ttu-id="ccfc1-106">A coleção de objetos é um controle de layout, que ajuda você a dispor uma matriz de objetos em uma forma tridimensional predefinida.</span><span class="sxs-lookup"><span data-stu-id="ccfc1-106">Object collection is a layout control, which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="ccfc1-107">Ele dá suporte a vários estilos de superfície-\* \* plano, cilindro, esfera e **radial**.</span><span class="sxs-lookup"><span data-stu-id="ccfc1-107">It supports various surface styles - \*\*plane, cylinder, sphere, and **radial**.</span></span> <span data-ttu-id="ccfc1-108">Você pode ajustar o raio e o tamanho dos objetos e o espaço entre eles.</span><span class="sxs-lookup"><span data-stu-id="ccfc1-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="ccfc1-109">A coleção de objetos dá suporte a qualquer objeto do Unity-2D e 3D.</span><span class="sxs-lookup"><span data-stu-id="ccfc1-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="ccfc1-110">No **[Kit de ferramentas de realidade misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, criamos script de Unity e exemplos que o ajudarão a criar uma coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="ccfc1-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="ccfc1-111">Exemplos de coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="ccfc1-111">Object collection examples</span></span>

<span data-ttu-id="ccfc1-112">[A tabela periódica dos elementos](../develop/unity/periodic-table-of-the-elements.md) é um aplicativo de exemplo que demonstra como funciona a coleta de objetos.</span><span class="sxs-lookup"><span data-stu-id="ccfc1-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="ccfc1-113">Ele usa a coleção de objetos para dispor caixas de elementos 3D químicas em formas diferentes.</span><span class="sxs-lookup"><span data-stu-id="ccfc1-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="ccfc1-114">![Exemplos de coleção de objetos mostrados na tabela periódica do aplicativo de elementos](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ccfc1-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="ccfc1-115">*Exemplos de coleção de objetos mostrados na tabela periódica do aplicativo de exemplo de elementos*</span><span class="sxs-lookup"><span data-stu-id="ccfc1-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="ccfc1-116">objetos 3D</span><span class="sxs-lookup"><span data-stu-id="ccfc1-116">3D objects</span></span>

<span data-ttu-id="ccfc1-117">Você pode usar a coleção de objetos para definir o layout de objetos 3D importados.</span><span class="sxs-lookup"><span data-stu-id="ccfc1-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="ccfc1-118">O exemplo a seguir mostra um plano e um layout de cilindro de alguns objetos de cadeira 3D.</span><span class="sxs-lookup"><span data-stu-id="ccfc1-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="ccfc1-119">![Exemplos de layouts de plano e cilíndrico de objetos 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ccfc1-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="ccfc1-120">*Exemplos de layouts de plano e cilíndrico de objetos 3D*</span><span class="sxs-lookup"><span data-stu-id="ccfc1-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="ccfc1-121">objetos 2D</span><span class="sxs-lookup"><span data-stu-id="ccfc1-121">2D objects</span></span>

<span data-ttu-id="ccfc1-122">Você também pode usar imagens 2D com a coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="ccfc1-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="ccfc1-123">Os exemplos a seguir demonstram como as imagens 2D podem ser exibidas em uma grade.</span><span class="sxs-lookup"><span data-stu-id="ccfc1-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Um exemplo de imagens 2D com a coleção de objetos](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="ccfc1-125">![Exemplos de como usar a coleção de objetos com imagens 2D](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="ccfc1-125">![Examples of using object collection with 2D images](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="ccfc1-126">*Exemplos de como usar a coleção de objetos com imagens 2D*</span><span class="sxs-lookup"><span data-stu-id="ccfc1-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="ccfc1-127">Coleção de objetos no MRTK (Kit de ferramentas de realidade misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="ccfc1-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="ccfc1-128">MRTK-coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="ccfc1-128">MRTK - Object collection</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)

<br>

---

## <a name="see-also"></a><span data-ttu-id="ccfc1-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccfc1-129">See also</span></span>

* [<span data-ttu-id="ccfc1-130">Cursores</span><span class="sxs-lookup"><span data-stu-id="ccfc1-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="ccfc1-131">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="ccfc1-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="ccfc1-132">Botão</span><span class="sxs-lookup"><span data-stu-id="ccfc1-132">Button</span></span>](button.md)
* [<span data-ttu-id="ccfc1-133">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="ccfc1-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="ccfc1-134">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="ccfc1-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="ccfc1-135">Manipulação</span><span class="sxs-lookup"><span data-stu-id="ccfc1-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ccfc1-136">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="ccfc1-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="ccfc1-137">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="ccfc1-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="ccfc1-138">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="ccfc1-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="ccfc1-139">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="ccfc1-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="ccfc1-140">Teclado</span><span class="sxs-lookup"><span data-stu-id="ccfc1-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="ccfc1-141">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="ccfc1-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="ccfc1-142">Slate</span><span class="sxs-lookup"><span data-stu-id="ccfc1-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="ccfc1-143">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="ccfc1-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="ccfc1-144">Sombreador</span><span class="sxs-lookup"><span data-stu-id="ccfc1-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="ccfc1-145">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="ccfc1-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="ccfc1-146">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="ccfc1-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="ccfc1-147">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="ccfc1-147">Surface magnetism</span></span>](surface-magnetism.md)
