---
title: Primitivo de recorte
description: Documentação sobre primitivos de recorte com exemplos no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, primitivo de recorte,
ms.openlocfilehash: 1feecbbd51eb80ff6113e66d053f032acb3005b9c7d1debbd5dfd46da0925798
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214404"
---
# <a name="clipping-primitive"></a>Primitivo de recorte

Os comportamentos permitem o recorte de forma, , e de desempenho com a capacidade de especificar em qual lado do primitivo se recortar (dentro ou fora) quando usado com sombreadores [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) do [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) MRTK.

![buges de recorte primitivo](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) utilize [instruções de recortar/descartar](https://developer.download.nvidia.com/cg/clip.html) em sombreadores e desabilitar a capacidade do Unity de renderizar em lotes recortados. Leve essas implicações de desempenho em mente ao utilizar primitivos de recorte.

[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) e podem ser usados para controlar [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) facilmente as propriedades primitivas de recorte. Use esses componentes com os sombreadores a seguir para aproveitar cenários de recorte.

- *Realidade Misturada Toolkit/Standard*
- *Mixed Reality Toolkit/TextMeshPro*
- *Mixed Reality Toolkit/Text3DShader*

## <a name="examples"></a>Exemplos

As **cenas ClippingExamples** e **MaterialGallery** demonstram o uso dos comportamentos e podem ser [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) encontradas em: MRTK/Examples/Demos/StandardShader/Scenes/

## <a name="advanced-usage"></a>Uso Avançado

Por padrão, apenas [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) um pode cortar um [renderador](https://docs.unity3d.com/ScriptReference/Renderer.html) por vez. Se o projeto exigir mais de um [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) para influenciar um [renderista,](https://docs.unity3d.com/ScriptReference/Renderer.html)  o código de exemplo abaixo demonstrará como fazer isso.

> [!NOTE]
> Ter vários [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clipes em [um renderdor](https://docs.unity3d.com/ScriptReference/Renderer.html) aumentará as instruções do sombreador de pixel e afetará o desempenho. Faça o perfil dessas alterações em seu projeto.

*Como ter dois clipes [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) diferentes em uma renderização. Por exemplo, [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) um e ao mesmo [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) tempo:*

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> A alteração acima incorre em tempo de compilação adicional do sombreador.

*Como ter dois dos mesmos [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clipes em uma renderização. Por exemplo, [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) dois ao mesmo tempo:*

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

Por fim, adicione um [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) componente e SecondClippingBox à cena e especifique o mesmo renderador para ambas as caixas. O renderador agora deve ser recortado por ambas as caixas simultaneamente.

## <a name="see-also"></a>Confira também

- [Sombreador Padrão do MRTK](mrtk-standard-shader.md)
