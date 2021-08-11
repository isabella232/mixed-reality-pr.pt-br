---
title: Luz de foco
description: Documentação sobre HoverLight com exemplos no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Luz de Foco,
ms.openlocfilehash: 948a0772cd2fad667984d8d5507664e4346a507e84b03c873eccf8d3f1e66532
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198578"
---
# <a name="hover-light"></a>Luz de foco

Um é um Sistema Fluent Design paradigma que imita uma luz de ponto que se aproxima [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) da superfície de um objeto. [](https://www.microsoft.com/design/fluent/) [](https://docs.unity3d.com/Manual/Lighting.html) Geralmente usado para interações distantes, o aplicativo pode controlar as propriedades de uma Luz de Foco por meio do [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) componente.

Para que um material seja influenciado por um sombreador Toolkit/Standard de Realidade Misturada deve ser usado e a propriedade Luz de Foco [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) deve ser  habilitada. 

> [!Note]
> O sombreador MRTK/Standard dá suporte a até dois por padrão, mas será dimensionado para dar suporte a quatro e dez à medida que mais luzes são adicionadas [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) à cena.

## <a name="examples"></a>Exemplos

A maioria das cenas no MRTK utiliza um [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) . O caso de uso mais comum pode ser encontrado no MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab

A **cena HoverLightExamples** também demonstra o uso de comportamentos e pode ser encontrada [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) em: MRTK/Examples/Demos/StandardShader/Scenes/

## <a name="advanced-usage"></a>Uso Avançado

Somente dez [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) podem ilustrar [um material](https://docs.unity3d.com/ScriptReference/Material.html) por vez. Se seu projeto exigir mais de dez para influenciar um material, o código de exemplo abaixo [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) demonstrará como fazer isso. [](https://docs.unity3d.com/ScriptReference/Material.html)

> [!Note]
> Ter muitos [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) luzes em um material [aumentará](https://docs.unity3d.com/ScriptReference/Material.html) as instruções do sombreador de pixel e afetará o desempenho. **Faça o perfil dessas alterações em seu projeto.**

*Como aumentar o número de disponíveis de dez para [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) doze.*

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
> Se o Unity registra um aviso semelhante ao abaixo, você deve reiniciar o Unity antes que as alterações entre em vigor.
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a>Confira também

* [Sombreador Padrão do MRTK](mrtk-standard-shader.md)
