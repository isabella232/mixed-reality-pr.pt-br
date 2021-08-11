---
title: Cenas de iluminação do sistema de cena
description: Documentação sobre iluminação na cena.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 407813f52044d3405e5045f64817d87c4f3e4b59ddfd87308586ac2d81924674
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202564"
---
# <a name="lighting-scene-operations"></a>Operações de cena de iluminação

A cena de iluminação padrão definida em seu perfil é carregada na inicialização. Essa cena de iluminação permanece carregada até que `SetLightingScene` seja chamada.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a>Transições de configuração de iluminação

`transitionType` controla o estilo da transição para a nova cena de iluminação.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

Os estilos disponíveis são:

Tipo | Description | Duração
--- | --- | ---
Nenhum | A cena de iluminação anterior está descarregada, a nova cena de iluminação é carregada. Sem transição. | Ignored
FadeToBlack | A cena de iluminação anterior esmaece para preto. A nova cena de iluminação é carregada e, em seguida, esmaecida de preto. Útil para transições suaves entre locais. | Usado
Fading cruzado | A cena de iluminação anterior desaparece conforme a nova cena de iluminação esmaece. Útil para transições suaves entre as configurações de iluminação no mesmo local. | Usado

Observe que algumas configurações de iluminação não podem ser interpoladas durante as transições. Se você quiser uma transição Visual suave, essas configurações precisarão permanecer consistentes entre as cenas de iluminação.

Configuração | Transição do Smooth FadeToBlack | Transição de fading cruzado suave
--- | --- | ---
Skybox | Não | Não
Reflexos personalizados | Não | Não
Sombras do sol em tempo real | Sim | Não
