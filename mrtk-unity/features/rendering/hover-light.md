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
# <a name="hover-light"></a>Luz de foco

Um [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) é um paradigma de [sistema de design fluente](https://www.microsoft.com/design/fluent/) que imita uma [luz de ponto](https://docs.unity3d.com/Manual/Lighting.html) focalizando perto da superfície de um objeto. Geralmente usado para interações distantes, o aplicativo pode controlar as propriedades de uma luz de foco por meio do [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) componente.

Para que um material seja influenciado por [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) um *Kit de ferramentas de realidade misturada/Standard* , o sombreador padrão deve ser usado e a propriedade de *luz de foco* deve ser habilitada.

> [!Note]
> O sombreador MRTK/Standard dá suporte a até dois [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) por padrão, mas será dimensionado para dar suporte a quatro e dez, pois mais luzes serão adicionadas à cena.

## <a name="examples"></a>Exemplos

A maioria das cenas no MRTK utiliza um [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) . O caso de uso mais comum pode ser encontrado no MRTK/SDK/Features/UX/pré-fabricados/Cursors/DefaultCursor. pré-fabricado

A cena **HoverLightExamples** também demonstra o uso de [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) comportamentos e pode ser encontrada em: MRTK/exemplos/demos/StandardShader/cenas/

## <a name="advanced-usage"></a>Uso Avançado

Somente dez [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) podem iluminar um [material](https://docs.unity3d.com/ScriptReference/Material.html) por vez. Se seu projeto exigir mais de dez [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) para influenciar um [material](https://docs.unity3d.com/ScriptReference/Material.html) , o código de exemplo abaixo demonstra como fazer isso.

> [!Note]
> Ter muitas [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) iluminar um [material](https://docs.unity3d.com/ScriptReference/Material.html) aumentará as instruções do sombreador de pixel e afetará o desempenho. **Faça o Profile dessas alterações no seu projeto.**

*Como aumentar o número de [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) dez para doze.*

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
> Se o Unity registrar um aviso semelhante a abaixo, você deverá reiniciar o Unity antes que suas alterações entrem em vigor.
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a>Confira também

* [Sombreador padrão MRTK](mrtk-standard-shader.md)
