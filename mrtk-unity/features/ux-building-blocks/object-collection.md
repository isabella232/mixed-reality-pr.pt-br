---
title: Coleção de objetos
description: Visão geral da coleta de objetos no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, coleção de objetos,
ms.openlocfilehash: 6705bd7093dbcd81912153872e4fd07c703fc5c0b9c081e0287589a7c8e959ac
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197496"
---
# <a name="object-collection"></a>Coleção de objetos

![Coleção de objetos](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

A coleção de objetos é um script para ajudar a dispor uma matriz de objetos em formas tridimensionais predefinidas. Ele dá suporte a vários estilos de superfície, incluindo plano, cilindro, esfera e radial. Como ele dá suporte a qualquer objeto no Unity, ele pode ser usado para fazer layout de objetos 2D e 3D.

## <a name="object-collection-scripts"></a>Scripts da coleção de objetos

- [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) dá suporte aos tipos de superfície de cilindro, plano, esfera e radial
- [`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) dá suporte à coleta de estilo dispersão  
- [`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) fornece algumas opções adicionais para GridObjectCollection. **Observação:** TileGridObjectCollection não se estende [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) e tem vários bugs (consulte o [problema 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)). Portanto, é recomendável usar [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .

|![Coleção de objetos de grade-cilindro](../images/object-collection/MRTK_ObjectCollectionCylinder.png) Coleção de objetos de grade-cilindro | ![Coleção de objetos de grade-Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) Coleção de objetos de grade-Sphere |
|:--- | :--- |
|![Coleção de objetos de grade-radial](../images/object-collection/MRTK_ObjectCollectionRadial.png) Coleção de objetos de grade-radial | ![Coleção de objetos de grade-plano](../images/object-collection/MRTK_ObjectCollectionPlane.png) Coleção de objetos de grade-plano |
|![Coleção de objetos dispersos](../images/object-collection/MRTK_ObjectCollectionScattered.png) Coleção de objetos dispersos | ![Coleção de objetos de grade de blocos](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) Coleção de objetos de grade de blocos |

## <a name="how-to-use-an-object-collection"></a>Como usar uma coleção de objetos

Para criar uma coleção, crie um gameobject vazio e atribua um dos scripts da coleção de objetos a ele. Qualquer objeto pode ser adicionado como um filho do gameobject. Depois de concluir a adição de objetos filho, clique no botão *Atualizar coleção* no painel inspetor para gerar a coleção de objetos. Os objetos serão dispostos na cena de acordo com os parâmetros da coleção. A coleção Update também pode ser acessada por meio do código.

![Script de coleção de objetos](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a>`GridObjectCollection` alinhamento de conteúdo

O conteúdo em um GridObjectCollection pode ser alinhado de forma que o objeto pai seja ancorado ao alto/médio/inferior e à esquerda/central/direita da coleção. Use a propriedade **Anchor** para especificar o alinhamento do conteúdo.

## <a name="gridobjectcollection-layout-order"></a>`GridObjectCollection` ordem de layout

Use o campo **layout** para especificar a ordem de linha/coluna que os filhos são dispostos:

**Em seguida** , a coluna-Children é disposta pela primeira vez por horizontal (por coluna) e, em seguida, verticalmente (por linha). Use **colunas num** (ou propriedade Columns no código) para especificar o número de colunas na grade.

![Layout de coluna e linha](../images/object-collection/MRTK_ColumnThenRow.png)

A **linha, em seguida** , a coluna-Children é inicialmente disposta verticalmente (por linha) e, em seguida, horizontalmente (por colunas). Use **linhas num** (ou propriedade Rows no código) para especificar o número de linhas na grade.

![Layout de linha e coluna](../images/object-collection/MRTK_RowThenColumn.png)

**Horizontal** -os filhos são dispostos em uma única linha usando apenas colunas

**Vertical** -os filhos são dispostos em uma única coluna usando somente linhas.

## <a name="object-collection-examples"></a>Exemplos de coleção de objetos

A `ObjectCollectionExamples` cena de exemplo (ativos/MRTK/exemplos/demos/UX/Collections/cenas/ObjectCollectionExamples. Unity) contém vários exemplos de tipos de coleção de objetos.

[A tabela periódica dos elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) é um exemplo de aplicativo que demonstra como as coleções de objetos funcionam. Ele usa a coleção de objetos para fazer layout das caixas do elemento 3D em formas diferentes.

## <a name="object-collection-types"></a>Tipos de coleção de objetos

**objetos 3D**

Uma coleção de objetos pode ser usada para layout de objetos 3D importados. O exemplo a seguir mostra os layouts de plano e cilíndrico de objetos de modelo de cadeira 3D usando uma coleção.

![Coleção de objetos 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

**Objetos 2D**

Uma coleção de objetos também pode ser criado a partir de imagens 2D. Por exemplo, várias imagens podem ser colocadas em um estilo de grade.

![Coleção de objetos 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
