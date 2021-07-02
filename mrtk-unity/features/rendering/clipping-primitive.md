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
# <a name="clipping-primitive"></a><span data-ttu-id="b9e64-104">Primitivo de recorte</span><span class="sxs-lookup"><span data-stu-id="b9e64-104">Clipping primitive</span></span>

<span data-ttu-id="b9e64-105">Os [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamentos permitem o alto desempenho [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) , [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) e [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) o recorte de forma com a capacidade de especificar qual lado do primitivo deve ser cortado (dentro ou fora) quando usado com sombreadores MRTK.</span><span class="sxs-lookup"><span data-stu-id="b9e64-105">The [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors allow for performant [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) shape clipping with the ability to specify which side of the primitive to clip against (inside or outside) when used with MRTK shaders.</span></span>

![utensílios de recorte primitivo](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> <span data-ttu-id="b9e64-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) Utilize instruções de [clipe/descarte](https://developer.download.nvidia.com/cg/clip.html) dentro de sombreadores e desabilite a capacidade do Unity para renderizadores recortados em lote.</span><span class="sxs-lookup"><span data-stu-id="b9e64-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) utilize [clip/discard](https://developer.download.nvidia.com/cg/clip.html) instructions within shaders and disable Unity's ability to batch clipped renderers.</span></span> <span data-ttu-id="b9e64-108">Considere essas implicações de desempenho ao utilizar primitivos de recorte.</span><span class="sxs-lookup"><span data-stu-id="b9e64-108">Take these performance implications in mind when utilizing clipping primitives.</span></span>

<span data-ttu-id="b9e64-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) e [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) pode ser usado para controlar facilmente as propriedades primitivas de recorte.</span><span class="sxs-lookup"><span data-stu-id="b9e64-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) can be used to easily control clipping primitive properties.</span></span> <span data-ttu-id="b9e64-110">Use esses componentes com os seguintes sombreadores para aproveitar os cenários de recorte.</span><span class="sxs-lookup"><span data-stu-id="b9e64-110">Use these components with the following shaders to leverage clipping scenarios.</span></span>

- <span data-ttu-id="b9e64-111">*realidade misturada Toolkit/padrão*</span><span class="sxs-lookup"><span data-stu-id="b9e64-111">*Mixed Reality Toolkit/Standard*</span></span>
- <span data-ttu-id="b9e64-112">*realidade misturada Toolkit/TextMeshPro*</span><span class="sxs-lookup"><span data-stu-id="b9e64-112">*Mixed Reality Toolkit/TextMeshPro*</span></span>
- <span data-ttu-id="b9e64-113">*realidade misturada Toolkit/Text3DShader*</span><span class="sxs-lookup"><span data-stu-id="b9e64-113">*Mixed Reality Toolkit/Text3DShader*</span></span>

## <a name="examples"></a><span data-ttu-id="b9e64-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b9e64-114">Examples</span></span>

<span data-ttu-id="b9e64-115">Os bastidores **ClippingExamples** e **MaterialGallery** demonstram o uso dos [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamentos e podem ser encontrados em: MRTK/examples/demos/StandardShader/cenas/</span><span class="sxs-lookup"><span data-stu-id="b9e64-115">The **ClippingExamples** and **MaterialGallery** scenes demonstrate usage of the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="b9e64-116">Uso Avançado</span><span class="sxs-lookup"><span data-stu-id="b9e64-116">Advanced Usage</span></span>

<span data-ttu-id="b9e64-117">Por padrão, apenas um [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) pode recortar um [renderizador](https://docs.unity3d.com/ScriptReference/Renderer.html) por vez.</span><span class="sxs-lookup"><span data-stu-id="b9e64-117">By default only one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) can clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) at a time.</span></span> <span data-ttu-id="b9e64-118">Se seu projeto exigir mais de um [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) para influenciar um [processador](https://docs.unity3d.com/ScriptReference/Renderer.html)  , o código de exemplo a seguir demonstra como conseguir isso.</span><span class="sxs-lookup"><span data-stu-id="b9e64-118">If your project requires more than one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) to influence a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html)  the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="b9e64-119">Ter vários [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clipes um [renderizador](https://docs.unity3d.com/ScriptReference/Renderer.html) aumentará as instruções do sombreador de pixel e afetará o desempenho.</span><span class="sxs-lookup"><span data-stu-id="b9e64-119">Having multiple [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="b9e64-120">Faça o Profile dessas alterações no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="b9e64-120">Please profile these changes within your project.</span></span>

<span data-ttu-id="b9e64-121">*Como fazer com que dois [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clipes diferentes sejam renderizados. Por exemplo [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) , a e [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) ao mesmo tempo:*</span><span class="sxs-lookup"><span data-stu-id="b9e64-121">*How to have two different [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example a [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) and [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> <span data-ttu-id="b9e64-122">A alteração acima incorrerá em tempo de compilação de sombreador adicional.</span><span class="sxs-lookup"><span data-stu-id="b9e64-122">The above change will incur additional shader compilation time.</span></span>

<span data-ttu-id="b9e64-123">*Como fazer com que dois do mesmo [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clipe sejam renderizados. Por exemplo [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) , dois ao mesmo tempo:*</span><span class="sxs-lookup"><span data-stu-id="b9e64-123">*How to have two of the same [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example two [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

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

<span data-ttu-id="b9e64-124">Por fim, adicione um [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) componente e SecondClippingBox à sua cena e especifique o mesmo renderizador para ambas as caixas.</span><span class="sxs-lookup"><span data-stu-id="b9e64-124">Finally, add a [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) and SecondClippingBox component to your scene and specify the same renderer for both boxes.</span></span> <span data-ttu-id="b9e64-125">O renderizador agora deve ser recortado por ambas as caixas simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="b9e64-125">The renderer should now be clipped by both boxes simultaneously.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9e64-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="b9e64-126">See also</span></span>

- [<span data-ttu-id="b9e64-127">Sombreador padrão MRTK</span><span class="sxs-lookup"><span data-stu-id="b9e64-127">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
