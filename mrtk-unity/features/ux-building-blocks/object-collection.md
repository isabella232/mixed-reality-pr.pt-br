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
# <a name="object-collection"></a>Coleção de objetos

![Coleção de objetos](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

A coleção de objetos é um script para ajudar a estabelecer uma matriz de objetos em formas tridimensionais predefinidos. Ele dá suporte a vários estilos de superfície, incluindo plano, cilindro, esfera e radial. Como ele dá suporte a qualquer objeto no Unity, ele pode ser usado para layout de objetos 2D e 3D.

## <a name="object-collection-scripts"></a>Scripts de coleção de objetos

- [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) dá suporte a tipos de superfície de cilindro, plano, esfera, radial
- [`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) dá suporte à coleção de estilos dispersos  
- [`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) fornece algumas opções adicionais para GridObjectCollection. **Observação:** TileGridObjectCollection não estende e tem [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) vários bugs (consulte [o problema 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)). Portanto, é recomendável usar [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .

|![Coleção de objetos de grade – Cilindro](../images/object-collection/MRTK_ObjectCollectionCylinder.png) Coleção de objetos de grade – Cilindro | ![Coleção de objetos de grade – Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) Coleção de objetos de grade – Sphere |
|:--- | :--- |
|![Coleção de Objetos de Grade – Radial](../images/object-collection/MRTK_ObjectCollectionRadial.png) Coleção de Objetos de Grade – Radial | ![Coleção de Objetos de Grade – Plano](../images/object-collection/MRTK_ObjectCollectionPlane.png) Coleção de Objetos de Grade – Plano |
|![Coleção de objetos dispersos](../images/object-collection/MRTK_ObjectCollectionScattered.png) Coleção de objetos dispersos | ![Coleção de objetos de grade de tile](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) Coleção de objetos de grade de tile |

## <a name="how-to-use-an-object-collection"></a>Como usar uma coleção de objetos

Para criar uma coleção, crie um GameObject vazio e atribua um dos scripts da Coleção de Objetos a ela. Qualquer objeto pode ser adicionado como um filho do GameObject. Depois de terminar de adicionar objetos filho, clique no *botão Atualizar Coleção* no painel inspetor para gerar a coleção de objetos. Os objetos serão colocados na cena de acordo com os parâmetros de coleção. A Coleção de Atualizações também pode ser acessada por meio do código.

![Script de coleção de objetos](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a>`GridObjectCollection` alinhamento de conteúdo

O conteúdo em uma GridObjectCollection pode ser alinhado para que o objeto pai seja ancorado na parte superior/intermediária/inferior e esquerda/centro/direita da coleção. Use a propriedade **de** âncora para especificar o alinhamento do conteúdo.

## <a name="gridobjectcollection-layout-order"></a>`GridObjectCollection` ordem de layout

Use o **campo Layout** para especificar a ordem de linha/coluna que os filhos são colocados:

**Coluna Em Seguida Linha** – Os filhos são primeiro colocados horizontalmente (por coluna) e, em seguida, verticalmente (por linha). Use **a propriedade Num Columns** (ou Columns no código) para especificar o número de colunas na grade.

![Coluna e layout de linha](../images/object-collection/MRTK_ColumnThenRow.png)

**Linha e Coluna** – Os filhos são primeiro colocados verticalmente (por linha) e, em seguida, horizontalmente (por colunas). Use **a propriedade Num Rows** (ou Rows no código) para especificar o número de linhas na grade.

![Layout de linha e coluna](../images/object-collection/MRTK_RowThenColumn.png)

**Horizontal** – os filhos são colocados em uma única linha usando apenas colunas

**Vertical** – os filhos são colocados em uma única coluna usando apenas linhas.

## <a name="object-collection-examples"></a>Exemplos de coleção de objetos

A cena de exemplo `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) contém vários exemplos de tipos de coleção de objetos.

[A tabela periódica dos elementos é](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) um aplicativo de exemplo que demonstra como as coleções de objetos funcionam. Ele usa a coleção de objetos para layout das caixas de elemento 3D em formas diferentes.

## <a name="object-collection-types"></a>Tipos de coleção de objetos

**Objetos 3D**

Uma coleção de objetos pode ser usada para layout de objetos 3D importados. O exemplo a seguir mostra o plano e os layouts cilíndricos de objetos de modelo de mesa 3D usando uma coleção.

![Coleção de objetos 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

**Objetos 2D**

Uma coleção de objetos também pode ser engradada de imagens 2D. Por exemplo, várias imagens podem ser colocadas em um estilo de grade.

![Coleção de objetos 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
