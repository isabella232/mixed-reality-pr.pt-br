---
title: Luz de proximidade
description: Documentação sobre luz de proximidade com exemplos no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 6e57a76d54d0f3f63ce8dcb80582e178effa39d9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176380"
---
# <a name="proximity-light"></a><span data-ttu-id="c6a65-104">Luz de proximidade</span><span class="sxs-lookup"><span data-stu-id="c6a65-104">Proximity light</span></span>

<span data-ttu-id="c6a65-105">Um é um Sistema Fluent Design paradigma que imita uma "luz de ponto inverso do gradiente" que se aproxima da [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) superfície de um objeto. [](https://www.microsoft.com/design/fluent/)</span><span class="sxs-lookup"><span data-stu-id="c6a65-105">A [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a "gradient inverse point light" hovering near the surface of an object.</span></span> <span data-ttu-id="c6a65-106">Geralmente usado para interações próximas, o aplicativo pode controlar as propriedades de uma Luz de Proximidade por meio do [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) componente.</span><span class="sxs-lookup"><span data-stu-id="c6a65-106">Often used for near interactions, the application can control the properties of a Proximity Light via the [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) component.</span></span>

<span data-ttu-id="c6a65-107">Para que um material seja influenciado por um sombreador de Toolkit/Standard deve ser usado e a propriedade Luz de Proximidade [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) deve ser  habilitada. </span><span class="sxs-lookup"><span data-stu-id="c6a65-107">For a material to be influenced by a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Proximity Light* property must be enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="c6a65-108">Há suporte [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) para até dois por padrão.</span><span class="sxs-lookup"><span data-stu-id="c6a65-108">Up to two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) are supported by default.</span></span>

## <a name="examples"></a><span data-ttu-id="c6a65-109">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c6a65-109">Examples</span></span>

<span data-ttu-id="c6a65-110">A maioria das cenas no MRTK utiliza um [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) .</span><span class="sxs-lookup"><span data-stu-id="c6a65-110">Most scenes within the MRTK utilize a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight).</span></span> <span data-ttu-id="c6a65-111">O caso de uso mais comum pode ser encontrado no MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span><span class="sxs-lookup"><span data-stu-id="c6a65-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="c6a65-112">Uso Avançado</span><span class="sxs-lookup"><span data-stu-id="c6a65-112">Advanced Usage</span></span>

<span data-ttu-id="c6a65-113">Por padrão, apenas [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) dois podem ilustrar [um material](https://docs.unity3d.com/ScriptReference/Material.html) por vez.</span><span class="sxs-lookup"><span data-stu-id="c6a65-113">By default only two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="c6a65-114">Se o projeto exigir mais de dois [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) para influenciar um [material,](https://docs.unity3d.com/ScriptReference/Material.html) o código de exemplo abaixo demonstrará como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="c6a65-114">If your project requires more than two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="c6a65-115">Ter muitos [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) luzes em um material [aumentará](https://docs.unity3d.com/ScriptReference/Material.html) as instruções do sombreador de pixel e afetará o desempenho.</span><span class="sxs-lookup"><span data-stu-id="c6a65-115">Having many [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="c6a65-116">Faça o perfil dessas alterações em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c6a65-116">Please profile these changes within your project.</span></span>

<span data-ttu-id="c6a65-117">*Como aumentar o número de disponíveis de [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) dois para quatro.*</span><span class="sxs-lookup"><span data-stu-id="c6a65-117">*How to increase the number of available [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) from two to four.*</span></span>

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#define PROXIMITY_LIGHT_COUNT 2

// to:

#define PROXIMITY_LIGHT_COUNT 4

// 2) Within MRTK/Core/Utilities/StandardShader/ProximityLight.cs change:

private const int proximityLightCount = 2;

// to:

private const int proximityLightCount = 4;
```

> [!NOTE]
> <span data-ttu-id="c6a65-118">Se o Unity registra um aviso semelhante ao abaixo, você deve reiniciar o Unity antes que as alterações entre em vigor.</span><span class="sxs-lookup"><span data-stu-id="c6a65-118">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a><span data-ttu-id="c6a65-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="c6a65-119">See also</span></span>

* [<span data-ttu-id="c6a65-120">Sombreador padrão MRTK</span><span class="sxs-lookup"><span data-stu-id="c6a65-120">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
