---
title: Primitivo de recorte
description: Documentação sobre primitivos de recorte com exemplos no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, primitivo de recorte,
ms.openlocfilehash: 35b7166045986df34eaf2c23161efc6379160ead
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145201"
---
# <a name="clipping-primitive"></a><span data-ttu-id="4d68c-104">Primitivo de recorte</span><span class="sxs-lookup"><span data-stu-id="4d68c-104">Clipping Primitive</span></span>

<span data-ttu-id="4d68c-105">Os comportamentos permitem o recorte de forma, , e de desempenho com a capacidade de especificar em qual lado do primitivo se recortar (dentro ou fora) quando usado com sombreadores [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) do [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) MRTK.</span><span class="sxs-lookup"><span data-stu-id="4d68c-105">The [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors allow for performant [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) shape clipping with the ability to specify which side of the primitive to clip against (inside or outside) when used with MRTK shaders.</span></span>

![buges de recorte primitivo](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> <span data-ttu-id="4d68c-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) utilize [instruções de recortar/descartar](https://developer.download.nvidia.com/cg/clip.html) em sombreadores e desabilitar a capacidade do Unity de renderizar em lotes recortados.</span><span class="sxs-lookup"><span data-stu-id="4d68c-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) utilize [clip/discard](https://developer.download.nvidia.com/cg/clip.html) instructions within shaders and disable Unity's ability to batch clipped renderers.</span></span> <span data-ttu-id="4d68c-108">Leve essas implicações de desempenho em mente ao utilizar primitivos de recorte.</span><span class="sxs-lookup"><span data-stu-id="4d68c-108">Take these performance implications in mind when utilizing clipping primitives.</span></span>

<span data-ttu-id="4d68c-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) e podem ser usados para controlar [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) facilmente as propriedades primitivas de recorte.</span><span class="sxs-lookup"><span data-stu-id="4d68c-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) can be used to easily control clipping primitive properties.</span></span> <span data-ttu-id="4d68c-110">Use esses componentes com os sombreadores a seguir para aproveitar cenários de recorte.</span><span class="sxs-lookup"><span data-stu-id="4d68c-110">Use these components with the following shaders to leverage clipping scenarios.</span></span>

- <span data-ttu-id="4d68c-111">*Kit de Ferramentas de Realidade Misturada/Standard*</span><span class="sxs-lookup"><span data-stu-id="4d68c-111">*Mixed Reality Toolkit/Standard*</span></span>
- <span data-ttu-id="4d68c-112">*Kit de Ferramentas de Realidade Misturada/TextMeshPro*</span><span class="sxs-lookup"><span data-stu-id="4d68c-112">*Mixed Reality Toolkit/TextMeshPro*</span></span>
- <span data-ttu-id="4d68c-113">*Kit de Ferramentas de Realidade Misturada/Text3DShader*</span><span class="sxs-lookup"><span data-stu-id="4d68c-113">*Mixed Reality Toolkit/Text3DShader*</span></span>

## <a name="examples"></a><span data-ttu-id="4d68c-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4d68c-114">Examples</span></span>

<span data-ttu-id="4d68c-115">As **cenas ClippingExamples** e **MaterialGallery** demonstram o uso dos comportamentos e podem ser [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) encontradas em: MRTK/Examples/Demos/StandardShader/Scenes/</span><span class="sxs-lookup"><span data-stu-id="4d68c-115">The **ClippingExamples** and **MaterialGallery** scenes demonstrate usage of the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="4d68c-116">Uso Avançado</span><span class="sxs-lookup"><span data-stu-id="4d68c-116">Advanced Usage</span></span>

<span data-ttu-id="4d68c-117">Por padrão, apenas [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) um pode cortar um [renderador](https://docs.unity3d.com/ScriptReference/Renderer.html) por vez.</span><span class="sxs-lookup"><span data-stu-id="4d68c-117">By default only one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) can clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) at a time.</span></span> <span data-ttu-id="4d68c-118">Se o projeto exigir mais de um [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) para influenciar um [renderista,](https://docs.unity3d.com/ScriptReference/Renderer.html)  o código de exemplo abaixo demonstrará como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="4d68c-118">If your project requires more than one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) to influence a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html)  the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="4d68c-119">Ter vários [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clipes em [um renderdor](https://docs.unity3d.com/ScriptReference/Renderer.html) aumentará as instruções do sombreador de pixel e afetará o desempenho.</span><span class="sxs-lookup"><span data-stu-id="4d68c-119">Having multiple [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="4d68c-120">Faça o perfil dessas alterações em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="4d68c-120">Please profile these changes within your project.</span></span>

<span data-ttu-id="4d68c-121">*Como ter dois clipes [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) diferentes em uma renderização. Por exemplo, [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) um e ao mesmo [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) tempo:*</span><span class="sxs-lookup"><span data-stu-id="4d68c-121">*How to have two different [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example a [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) and [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> <span data-ttu-id="4d68c-122">A alteração acima incorre em tempo de compilação adicional do sombreador.</span><span class="sxs-lookup"><span data-stu-id="4d68c-122">The above change will incur additional shader compilation time.</span></span>

<span data-ttu-id="4d68c-123">*Como ter dois dos mesmos [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clipes em uma renderização. Por exemplo, [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) dois ao mesmo tempo:*</span><span class="sxs-lookup"><span data-stu-id="4d68c-123">*How to have two of the same [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example two [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

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

<span data-ttu-id="4d68c-124">Por fim, adicione um [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) componente e SecondClippingBox à cena e especifique o mesmo renderador para ambas as caixas.</span><span class="sxs-lookup"><span data-stu-id="4d68c-124">Finally, add a [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) and SecondClippingBox component to your scene and specify the same renderer for both boxes.</span></span> <span data-ttu-id="4d68c-125">O renderizador agora deve ser recortado por ambas as caixas simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="4d68c-125">The renderer should now be clipped by both boxes simultaneously.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d68c-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="4d68c-126">See also</span></span>

- [<span data-ttu-id="4d68c-127">Sombreador padrão MRTK</span><span class="sxs-lookup"><span data-stu-id="4d68c-127">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
