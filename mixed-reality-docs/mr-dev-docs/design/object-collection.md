---
title: Coleção de objetos
description: A coleção de objetos é um controle de layout que ajuda você a dispor uma matriz de objetos em uma forma tridimensional predefinida.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, controles, design
ms.openlocfilehash: 5859f7141e8fa0ea27f142981e2cbd05b8da53bf
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675091"
---
# <a name="object-collection"></a><span data-ttu-id="43cce-104">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="43cce-104">Object collection</span></span>

![Coleção de objetos usada na tabela periódica do aplicativo de elementos](images/UX_Hero_ObjectCollection.jpg)<br>


<span data-ttu-id="43cce-106">A coleção de objetos é um controle de layout que ajuda você a dispor uma matriz de objetos em uma forma tridimensional predefinida.</span><span class="sxs-lookup"><span data-stu-id="43cce-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="43cce-107">Ele dá suporte a vários estilos de superfície- **plano, cilindro, esfera** e **radial** .</span><span class="sxs-lookup"><span data-stu-id="43cce-107">It supports various surface styles - **plane, cylinder, sphere** and **radial** .</span></span> <span data-ttu-id="43cce-108">Você pode ajustar o raio e o tamanho dos objetos e o espaço entre eles.</span><span class="sxs-lookup"><span data-stu-id="43cce-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="43cce-109">A coleção de objetos dá suporte a qualquer objeto do Unity-2D e 3D.</span><span class="sxs-lookup"><span data-stu-id="43cce-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="43cce-110">No **[Kit de ferramentas de realidade misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** , criamos script de Unity e exemplos que o ajudarão a criar uma coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="43cce-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** , we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="43cce-111">Exemplos de coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="43cce-111">Object collection examples</span></span>

<span data-ttu-id="43cce-112">[A tabela periódica dos elementos](../develop/unity/periodic-table-of-the-elements.md) é um aplicativo de exemplo que demonstra como funciona a coleta de objetos.</span><span class="sxs-lookup"><span data-stu-id="43cce-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="43cce-113">Ele usa a coleção de objetos para dispor caixas de elementos 3D químicas em formas diferentes.</span><span class="sxs-lookup"><span data-stu-id="43cce-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="43cce-114">![Exemplos de coleção de objetos mostrados na tabela periódica do aplicativo de elementos](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="43cce-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="43cce-115">*Exemplos de coleção de objetos mostrados na tabela periódica do aplicativo de exemplo de elementos*</span><span class="sxs-lookup"><span data-stu-id="43cce-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="43cce-116">objetos 3D</span><span class="sxs-lookup"><span data-stu-id="43cce-116">3D objects</span></span>

<span data-ttu-id="43cce-117">Você pode usar a coleção de objetos para definir o layout de objetos 3D importados.</span><span class="sxs-lookup"><span data-stu-id="43cce-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="43cce-118">O exemplo a seguir mostra um plano e um layout de cilindro de alguns objetos de cadeira 3D.</span><span class="sxs-lookup"><span data-stu-id="43cce-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="43cce-119">![Exemplos de layouts de plano e cilíndrico de objetos 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="43cce-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="43cce-120">*Exemplos de layouts de plano e cilíndrico de objetos 3D*</span><span class="sxs-lookup"><span data-stu-id="43cce-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="43cce-121">objetos 2D</span><span class="sxs-lookup"><span data-stu-id="43cce-121">2D objects</span></span>

<span data-ttu-id="43cce-122">Você também pode usar imagens 2D com a coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="43cce-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="43cce-123">Os exemplos a seguir demonstram como as imagens 2D podem ser exibidas em uma grade.</span><span class="sxs-lookup"><span data-stu-id="43cce-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Um exemplo de imagens 2D com a coleção de objetos](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="43cce-125">![Um exemplo de imagens 2D com a coleção de objetos](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="43cce-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="43cce-126">*Exemplos de como usar a coleção de objetos com imagens 2D*</span><span class="sxs-lookup"><span data-stu-id="43cce-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="43cce-127">Coleção de objetos no MRTK (Kit de ferramentas de realidade misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="43cce-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="43cce-128">MRTK-coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="43cce-128">MRTK - Object collection</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="43cce-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43cce-129">See also</span></span>

* [<span data-ttu-id="43cce-130">Cursores</span><span class="sxs-lookup"><span data-stu-id="43cce-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="43cce-131">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="43cce-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="43cce-132">Botão</span><span class="sxs-lookup"><span data-stu-id="43cce-132">Button</span></span>](button.md)
* [<span data-ttu-id="43cce-133">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="43cce-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="43cce-134">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="43cce-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="43cce-135">Manipulação</span><span class="sxs-lookup"><span data-stu-id="43cce-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="43cce-136">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="43cce-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="43cce-137">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="43cce-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="43cce-138">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="43cce-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="43cce-139">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="43cce-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="43cce-140">Teclado</span><span class="sxs-lookup"><span data-stu-id="43cce-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="43cce-141">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="43cce-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="43cce-142">Slate</span><span class="sxs-lookup"><span data-stu-id="43cce-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="43cce-143">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="43cce-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="43cce-144">Sombreador</span><span class="sxs-lookup"><span data-stu-id="43cce-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="43cce-145">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="43cce-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="43cce-146">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="43cce-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="43cce-147">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="43cce-147">Surface magnetism</span></span>](surface-magnetism.md)
