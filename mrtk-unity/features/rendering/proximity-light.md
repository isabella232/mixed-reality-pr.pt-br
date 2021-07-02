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
# <a name="proximity-light"></a>Luz de proximidade

Um é um Sistema Fluent Design paradigma que imita uma "luz de ponto inverso do gradiente" que se aproxima da [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) superfície de um objeto. [](https://www.microsoft.com/design/fluent/) Geralmente usado para interações próximas, o aplicativo pode controlar as propriedades de uma Luz de Proximidade por meio do [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) componente.

Para que um material seja influenciado por um sombreador de Toolkit/Standard deve ser usado e a propriedade Luz de Proximidade [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) deve ser  habilitada. 

> [!NOTE]
> Há suporte [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) para até dois por padrão.

## <a name="examples"></a>Exemplos

A maioria das cenas no MRTK utiliza um [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) . O caso de uso mais comum pode ser encontrado no MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab

## <a name="advanced-usage"></a>Uso Avançado

Por padrão, apenas [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) dois podem ilustrar [um material](https://docs.unity3d.com/ScriptReference/Material.html) por vez. Se o projeto exigir mais de dois [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) para influenciar um [material,](https://docs.unity3d.com/ScriptReference/Material.html) o código de exemplo abaixo demonstrará como fazer isso.

> [!NOTE]
> Ter muitos [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) luzes em um material [aumentará](https://docs.unity3d.com/ScriptReference/Material.html) as instruções do sombreador de pixel e afetará o desempenho. Faça o perfil dessas alterações em seu projeto.

*Como aumentar o número de disponíveis de [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) dois para quatro.*

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
> Se o Unity registra um aviso semelhante ao abaixo, você deve reiniciar o Unity antes que as alterações entre em vigor.
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a>Confira também

* [Sombreador padrão MRTK](mrtk-standard-shader.md)
