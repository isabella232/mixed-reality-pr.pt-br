---
title: Primitivo de recorte
description: Documentação sobre primitivos de recorte com exemplos em MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, primitivo de recorte,
ms.openlocfilehash: c3331084f87ccc57208426910d84ed7bef457bc1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176740"
---
# <a name="clipping-primitive"></a>Primitivo de recorte

Os [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamentos permitem o alto desempenho [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) , [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) e [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) o recorte de forma com a capacidade de especificar qual lado do primitivo deve ser cortado (dentro ou fora) quando usado com sombreadores MRTK.

![utensílios de recorte primitivo](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) Utilize instruções de [clipe/descarte](https://developer.download.nvidia.com/cg/clip.html) dentro de sombreadores e desabilite a capacidade do Unity para renderizadores recortados em lote. Considere essas implicações de desempenho ao utilizar primitivos de recorte.

[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) e [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) pode ser usado para controlar facilmente as propriedades primitivas de recorte. Use esses componentes com os seguintes sombreadores para aproveitar os cenários de recorte.

- *realidade misturada Toolkit/padrão*
- *realidade misturada Toolkit/TextMeshPro*
- *realidade misturada Toolkit/Text3DShader*

## <a name="examples"></a>Exemplos

Os bastidores **ClippingExamples** e **MaterialGallery** demonstram o uso dos [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamentos e podem ser encontrados em: MRTK/examples/demos/StandardShader/cenas/

## <a name="advanced-usage"></a>Uso Avançado

Por padrão, apenas um [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) pode recortar um [renderizador](https://docs.unity3d.com/ScriptReference/Renderer.html) por vez. Se seu projeto exigir mais de um [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) para influenciar um [processador](https://docs.unity3d.com/ScriptReference/Renderer.html)  , o código de exemplo a seguir demonstra como conseguir isso.

> [!NOTE]
> Ter vários [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clipes um [renderizador](https://docs.unity3d.com/ScriptReference/Renderer.html) aumentará as instruções do sombreador de pixel e afetará o desempenho. Faça o Profile dessas alterações no seu projeto.

*Como fazer com que dois [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clipes diferentes sejam renderizados. Por exemplo [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) , a e [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) ao mesmo tempo:*

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> A alteração acima incorrerá em tempo de compilação de sombreador adicional.

*Como fazer com que dois do mesmo [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clipe sejam renderizados. Por exemplo [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) , dois ao mesmo tempo:*

```C#
// 1) Add the below MonoBehaviour to your project:

[ExecuteInEditMode]
public class SecondClippingBox : ClippingBox
{
    /// <inheritdoc />
    protected override string Keyword
    {
        get { return "_CLIPPING_BOX2"; }
    }

    /// <inheritdoc />
    protected override string ClippingSideProperty
    {
        get { return "_ClipBoxSide2"; }
    }

    /// <inheritdoc />
    protected override void Initialize()
    {
        base.Initialize();

        clipBoxSizeID = Shader.PropertyToID("_ClipBoxSize2");
        clipBoxInverseTransformID = Shader.PropertyToID("_ClipBoxInverseTransform2");
    }
}

// 2) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) add the following multi_compile pragma:

#pragma multi_compile _ _CLIPPING_BOX2

// 3) In the same shader change:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX)

// to:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX) || defined(_CLIPPING_BOX2)

// 4) In the same shader add the following shader variables:

#if defined(_CLIPPING_BOX2)
    fixed _ClipBoxSide2;
    float4 _ClipBoxSize2;
    float4x4 _ClipBoxInverseTransform2;
#endif

// 5) In the same shader change:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif

// to:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif
#if defined(_CLIPPING_BOX2)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize2.xyz, _ClipBoxInverseTransform2) * _ClipBoxSide2);
#endif
```

Por fim, adicione um [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) componente e SecondClippingBox à sua cena e especifique o mesmo renderizador para ambas as caixas. O renderizador agora deve ser recortado por ambas as caixas simultaneamente.

## <a name="see-also"></a>Confira também

- [Sombreador padrão MRTK](mrtk-standard-shader.md)
