---
title: Luz de proximidade
description: Documentação sobre a luz de proximidade com exemplos em MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 1be58cd22228258d51f63b2a4db0294bceaec1320640ecbbfa2795edde5e39bd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208316"
---
# <a name="proximity-light"></a>Luz de proximidade

um [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) é um paradigma de [Sistema Fluent Design](https://www.microsoft.com/design/fluent/) que imita uma "luz de ponto inverso gradual" ao focalizar perto da superfície de um objeto. Geralmente usado para interações próximas, o aplicativo pode controlar as propriedades de uma luz de proximidade por meio do [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) componente.

para que um material seja influenciado por [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) uma *realidade misturada Toolkit* o sombreador/padrão deve ser usado e a propriedade *luz de proximidade* deve ser habilitada.

> [!NOTE]
> Há suporte para até dois [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) por padrão.

## <a name="examples"></a>Exemplos

A maioria das cenas no MRTK utiliza um [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) . O caso de uso mais comum pode ser encontrado em MRTK/SDK/Features/UX/pré-fabricados/Cursors/FingerCursor. pré-fabricado

## <a name="advanced-usage"></a>Uso Avançado

Por padrão, somente dois [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) podem iluminar um [material](https://docs.unity3d.com/ScriptReference/Material.html) por vez. Se o seu projeto exigir mais de dois [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) para influenciar um [material](https://docs.unity3d.com/ScriptReference/Material.html) , o código de exemplo abaixo demonstra como conseguir isso.

> [!NOTE]
> Ter muitas [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) iluminar um [material](https://docs.unity3d.com/ScriptReference/Material.html) aumentará as instruções do sombreador de pixel e afetará o desempenho. Faça o Profile dessas alterações no seu projeto.

*Como aumentar o número de [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) duas para quatro disponíveis.*

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
> Se o Unity registrar um aviso semelhante a abaixo, você deverá reiniciar o Unity antes que suas alterações entrem em vigor.
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a>Confira também

* [Sombreador padrão MRTK](mrtk-standard-shader.md)
