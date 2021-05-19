---
title: Luz de foco
description: Documentação no HoverLight com exemplos em MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, luz de foco,
ms.openlocfilehash: b98dff0dd3ff0312f6ce607a5fb8a26f94959ff2
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145174"
---
# <a name="hover-light"></a><span data-ttu-id="72cab-104">Luz de foco</span><span class="sxs-lookup"><span data-stu-id="72cab-104">Hover Light</span></span>

<span data-ttu-id="72cab-105">Um [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) é um paradigma de [sistema de design fluente](https://www.microsoft.com/design/fluent/) que imita uma [luz de ponto](https://docs.unity3d.com/Manual/Lighting.html) focalizando perto da superfície de um objeto.</span><span class="sxs-lookup"><span data-stu-id="72cab-105">A [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a [point light](https://docs.unity3d.com/Manual/Lighting.html) hovering near the surface of an object.</span></span> <span data-ttu-id="72cab-106">Geralmente usado para interações distantes, o aplicativo pode controlar as propriedades de uma luz de foco por meio do [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) componente.</span><span class="sxs-lookup"><span data-stu-id="72cab-106">Often used for far away interactions, the application can control the properties of a Hover Light via the [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) component.</span></span>

<span data-ttu-id="72cab-107">Para que um material seja influenciado por [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) um *Kit de ferramentas de realidade misturada/Standard* , o sombreador padrão deve ser usado e a propriedade de *luz de foco* deve ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="72cab-107">For a material to be influenced by a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Hover Light* property must be enabled.</span></span>

> [!Note]
> <span data-ttu-id="72cab-108">O sombreador MRTK/Standard dá suporte a até dois [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) por padrão, mas será dimensionado para dar suporte a quatro e dez, pois mais luzes serão adicionadas à cena.</span><span class="sxs-lookup"><span data-stu-id="72cab-108">The MRTK/Standard shader supports up to two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) by default, but will scale to support four and then ten as more lights are added to the scene.</span></span>

## <a name="examples"></a><span data-ttu-id="72cab-109">Exemplos</span><span class="sxs-lookup"><span data-stu-id="72cab-109">Examples</span></span>

<span data-ttu-id="72cab-110">A maioria das cenas no MRTK utiliza um [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) .</span><span class="sxs-lookup"><span data-stu-id="72cab-110">Most scenes within the MRTK utilize a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight).</span></span> <span data-ttu-id="72cab-111">O caso de uso mais comum pode ser encontrado no MRTK/SDK/Features/UX/pré-fabricados/Cursors/DefaultCursor. pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="72cab-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab</span></span>

<span data-ttu-id="72cab-112">A cena **HoverLightExamples** também demonstra o uso de [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) comportamentos e pode ser encontrada em: MRTK/exemplos/demos/StandardShader/cenas/</span><span class="sxs-lookup"><span data-stu-id="72cab-112">The **HoverLightExamples** scene also demonstrates usage of [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="72cab-113">Uso Avançado</span><span class="sxs-lookup"><span data-stu-id="72cab-113">Advanced Usage</span></span>

<span data-ttu-id="72cab-114">Somente dez [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) podem iluminar um [material](https://docs.unity3d.com/ScriptReference/Material.html) por vez.</span><span class="sxs-lookup"><span data-stu-id="72cab-114">Only ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="72cab-115">Se seu projeto exigir mais de dez [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) para influenciar um [material](https://docs.unity3d.com/ScriptReference/Material.html) , o código de exemplo abaixo demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="72cab-115">If your project requires more than ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!Note]
> <span data-ttu-id="72cab-116">Ter muitas [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) iluminar um [material](https://docs.unity3d.com/ScriptReference/Material.html) aumentará as instruções do sombreador de pixel e afetará o desempenho.</span><span class="sxs-lookup"><span data-stu-id="72cab-116">Having many [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="72cab-117">**Faça o Profile dessas alterações no seu projeto.**</span><span class="sxs-lookup"><span data-stu-id="72cab-117">**Please profile these changes within your project.**</span></span>

<span data-ttu-id="72cab-118">*Como aumentar o número de [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) dez para doze.*</span><span class="sxs-lookup"><span data-stu-id="72cab-118">*How to increase the number of available [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) from ten to twelve.*</span></span>

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 10

// to:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 12

// 2) Within MRTK/Core/Utilities/StandardShader/HoverLight.cs change:

private const int hoverLightCountHigh = 10;

// to:

private const int hoverLightCountHigh = 12;
```

> [!NOTE]
> <span data-ttu-id="72cab-119">Se o Unity registrar um aviso semelhante a abaixo, você deverá reiniciar o Unity antes que suas alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="72cab-119">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a><span data-ttu-id="72cab-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="72cab-120">See also</span></span>

* [<span data-ttu-id="72cab-121">Sombreador padrão MRTK</span><span class="sxs-lookup"><span data-stu-id="72cab-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
