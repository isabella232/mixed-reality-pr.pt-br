---
title: Coleção de objetos
description: Visão geral da coleção de objetos no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Coleção de objetos,
ms.openlocfilehash: 8390e9c4a7bd419f99a5c8c4af7e7a2eca1d8f3f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177051"
---
# <a name="object-collection"></a><span data-ttu-id="3f787-104">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="3f787-104">Object collection</span></span>

![Coleção de objetos](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

<span data-ttu-id="3f787-106">A coleção de objetos é um script para ajudar a estabelecer uma matriz de objetos em formas tridimensionais predefinidos.</span><span class="sxs-lookup"><span data-stu-id="3f787-106">Object collection is a script to help lay out an array of objects in predefined three-dimensional shapes.</span></span> <span data-ttu-id="3f787-107">Ele dá suporte a vários estilos de superfície, incluindo plano, cilindro, esfera e radial.</span><span class="sxs-lookup"><span data-stu-id="3f787-107">It supports various surface styles including plane, cylinder, sphere, and radial.</span></span> <span data-ttu-id="3f787-108">Como ele dá suporte a qualquer objeto no Unity, ele pode ser usado para layout de objetos 2D e 3D.</span><span class="sxs-lookup"><span data-stu-id="3f787-108">Since it supports any object in Unity, it can be used to layout both 2D and 3D objects.</span></span>

## <a name="object-collection-scripts"></a><span data-ttu-id="3f787-109">Scripts de coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="3f787-109">Object collection scripts</span></span>

- <span data-ttu-id="3f787-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) dá suporte a tipos de superfície de cilindro, plano, esfera, radial</span><span class="sxs-lookup"><span data-stu-id="3f787-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supports Cylinder, Plane, Sphere, Radial surface types</span></span>
- <span data-ttu-id="3f787-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) dá suporte à coleção de estilos dispersos</span><span class="sxs-lookup"><span data-stu-id="3f787-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supports scattered style collection</span></span>  
- <span data-ttu-id="3f787-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) fornece algumas opções adicionais para GridObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="3f787-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) provides some additional options to GridObjectCollection.</span></span> <span data-ttu-id="3f787-113">**Observação:** TileGridObjectCollection não estende e tem [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) vários bugs (consulte [o problema 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span><span class="sxs-lookup"><span data-stu-id="3f787-113">**Note:** TileGridObjectCollection does not extend [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection), and has several bugs (see [issue 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span></span> <span data-ttu-id="3f787-114">Portanto, é recomendável usar [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .</span><span class="sxs-lookup"><span data-stu-id="3f787-114">Therefore, it is recommended to use [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection).</span></span>

|![Coleção de objetos de grade – Cilindro](../images/object-collection/MRTK_ObjectCollectionCylinder.png) <span data-ttu-id="3f787-116">Coleção de objetos de grade – Cilindro</span><span class="sxs-lookup"><span data-stu-id="3f787-116">Grid Object Collection - Cylinder</span></span> | ![Coleção de objetos de grade – Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) <span data-ttu-id="3f787-118">Coleção de objetos de grade – Sphere</span><span class="sxs-lookup"><span data-stu-id="3f787-118">Grid Object Collection - Sphere</span></span> |
|:--- | :--- |
|![Coleção de Objetos de Grade – Radial](../images/object-collection/MRTK_ObjectCollectionRadial.png) <span data-ttu-id="3f787-120">Coleção de Objetos de Grade – Radial</span><span class="sxs-lookup"><span data-stu-id="3f787-120">Grid Object Collection - Radial</span></span> | ![Coleção de Objetos de Grade – Plano](../images/object-collection/MRTK_ObjectCollectionPlane.png) <span data-ttu-id="3f787-122">Coleção de Objetos de Grade – Plano</span><span class="sxs-lookup"><span data-stu-id="3f787-122">Grid Object Collection - Plane</span></span> |
|![Coleção de objetos dispersos](../images/object-collection/MRTK_ObjectCollectionScattered.png) <span data-ttu-id="3f787-124">Coleção de objetos dispersos</span><span class="sxs-lookup"><span data-stu-id="3f787-124">Scattered Object Collection</span></span> | ![Coleção de objetos de grade de tile](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) <span data-ttu-id="3f787-126">Coleção de objetos de grade de tile</span><span class="sxs-lookup"><span data-stu-id="3f787-126">Tile Grid Object Collection</span></span> |

## <a name="how-to-use-an-object-collection"></a><span data-ttu-id="3f787-127">Como usar uma coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="3f787-127">How to use an object collection</span></span>

<span data-ttu-id="3f787-128">Para criar uma coleção, crie um GameObject vazio e atribua um dos scripts da Coleção de Objetos a ela.</span><span class="sxs-lookup"><span data-stu-id="3f787-128">To create a collection, create an empty GameObject and assign one of the Object Collection scripts to it.</span></span> <span data-ttu-id="3f787-129">Qualquer objeto pode ser adicionado como um filho do GameObject.</span><span class="sxs-lookup"><span data-stu-id="3f787-129">Any object(s) can be added as a child of the GameObject.</span></span> <span data-ttu-id="3f787-130">Depois de terminar de adicionar objetos filho, clique no *botão Atualizar Coleção* no painel inspetor para gerar a coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="3f787-130">Once finished adding child objects, click the *Update Collection* button in the inspector panel to generate the object collection.</span></span> <span data-ttu-id="3f787-131">Os objetos serão colocados na cena de acordo com os parâmetros de coleção.</span><span class="sxs-lookup"><span data-stu-id="3f787-131">The objects will be laid out in the scene according to the collection parameters.</span></span> <span data-ttu-id="3f787-132">A Coleção de Atualizações também pode ser acessada por meio do código.</span><span class="sxs-lookup"><span data-stu-id="3f787-132">Update Collection can be accessed through the code too.</span></span>

![Script de coleção de objetos](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a><span data-ttu-id="3f787-134">`GridObjectCollection` alinhamento de conteúdo</span><span class="sxs-lookup"><span data-stu-id="3f787-134">`GridObjectCollection` content alignment</span></span>

<span data-ttu-id="3f787-135">O conteúdo em uma GridObjectCollection pode ser alinhado para que o objeto pai seja ancorado na parte superior/intermediária/inferior e esquerda/centro/direita da coleção.</span><span class="sxs-lookup"><span data-stu-id="3f787-135">The content in a GridObjectCollection can be aligned so that the parent object is anchored to the top/middle/bottom and left/center/right of the collection.</span></span> <span data-ttu-id="3f787-136">Use a propriedade **de** âncora para especificar o alinhamento do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3f787-136">Use the **anchor** property to specify content alignment.</span></span>

## <a name="gridobjectcollection-layout-order"></a><span data-ttu-id="3f787-137">`GridObjectCollection` ordem de layout</span><span class="sxs-lookup"><span data-stu-id="3f787-137">`GridObjectCollection` layout order</span></span>

<span data-ttu-id="3f787-138">Use o **campo Layout** para especificar a ordem de linha/coluna que os filhos são colocados:</span><span class="sxs-lookup"><span data-stu-id="3f787-138">Use the **Layout** field to specify the row / column order that children are laid out:</span></span>

<span data-ttu-id="3f787-139">**Coluna Em Seguida Linha** – Os filhos são primeiro colocados horizontalmente (por coluna) e, em seguida, verticalmente (por linha).</span><span class="sxs-lookup"><span data-stu-id="3f787-139">**Column Then Row** - Children are first laid out by horizontally (by column), then vertically (by row).</span></span> <span data-ttu-id="3f787-140">Use **a propriedade Num Columns** (ou Columns no código) para especificar o número de colunas na grade.</span><span class="sxs-lookup"><span data-stu-id="3f787-140">Use **Num Columns** (or Columns property in code) to specify the number of columns in the grid.</span></span>

![Coluna e layout de linha](../images/object-collection/MRTK_ColumnThenRow.png)

<span data-ttu-id="3f787-142">**Linha e Coluna** – Os filhos são primeiro colocados verticalmente (por linha) e, em seguida, horizontalmente (por colunas).</span><span class="sxs-lookup"><span data-stu-id="3f787-142">**Row Then Column** - Children are first laid out vertically (by row), then horizontally (by columns).</span></span> <span data-ttu-id="3f787-143">Use **a propriedade Num Rows** (ou Rows no código) para especificar o número de linhas na grade.</span><span class="sxs-lookup"><span data-stu-id="3f787-143">Use **Num Rows** (or Rows property in code) to specify the number of rows in the grid.</span></span>

![Layout de linha e coluna](../images/object-collection/MRTK_RowThenColumn.png)

<span data-ttu-id="3f787-145">**Horizontal** – os filhos são colocados em uma única linha usando apenas colunas</span><span class="sxs-lookup"><span data-stu-id="3f787-145">**Horizontal** - Children are laid out in a single row using columns only</span></span>

<span data-ttu-id="3f787-146">**Vertical** – os filhos são colocados em uma única coluna usando apenas linhas.</span><span class="sxs-lookup"><span data-stu-id="3f787-146">**Vertical** - Children are laid out in a single column using rows only.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="3f787-147">Exemplos de coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="3f787-147">Object collection examples</span></span>

<span data-ttu-id="3f787-148">A cena de exemplo `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) contém vários exemplos de tipos de coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="3f787-148">The `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) example scene contains various examples of object collection types.</span></span>

<span data-ttu-id="3f787-149">[A tabela periódica dos elementos é](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) um aplicativo de exemplo que demonstra como as coleções de objetos funcionam.</span><span class="sxs-lookup"><span data-stu-id="3f787-149">[Periodic table of the elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an example app that demonstrates how object collections work.</span></span> <span data-ttu-id="3f787-150">Ele usa a coleção de objetos para layout das caixas de elemento 3D em formas diferentes.</span><span class="sxs-lookup"><span data-stu-id="3f787-150">It uses object collection to layout the 3D element boxes in different shapes.</span></span>

## <a name="object-collection-types"></a><span data-ttu-id="3f787-151">Tipos de coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="3f787-151">Object collection types</span></span>

<span data-ttu-id="3f787-152">**Objetos 3D**</span><span class="sxs-lookup"><span data-stu-id="3f787-152">**3D objects**</span></span>

<span data-ttu-id="3f787-153">Uma coleção de objetos pode ser usada para layout de objetos 3D importados.</span><span class="sxs-lookup"><span data-stu-id="3f787-153">An object collection can be used to layout imported 3D objects.</span></span> <span data-ttu-id="3f787-154">O exemplo a seguir mostra o plano e os layouts cilíndricos de objetos de modelo de mesa 3D usando uma coleção.</span><span class="sxs-lookup"><span data-stu-id="3f787-154">The example below shows the plane and cylindrical layouts of 3D chair model objects using a collection.</span></span>

![Coleção de objetos 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

<span data-ttu-id="3f787-156">**Objetos 2D**</span><span class="sxs-lookup"><span data-stu-id="3f787-156">**2D Objects**</span></span>

<span data-ttu-id="3f787-157">Uma coleção de objetos também pode ser engradada de imagens 2D.</span><span class="sxs-lookup"><span data-stu-id="3f787-157">An object collection can also be crated from 2D images.</span></span> <span data-ttu-id="3f787-158">Por exemplo, várias imagens podem ser colocadas em um estilo de grade.</span><span class="sxs-lookup"><span data-stu-id="3f787-158">For example, multiple images can be placed in a grid style.</span></span>

![Coleção de objetos 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
