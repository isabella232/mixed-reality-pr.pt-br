---
title: Cenas de iluminação do sistema de cena
description: Documentação sobre iluminação na cena.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: fa7442bc968710a31ce3ca379c7fd73928e6e324
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144411"
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

Tipo | Descrição | Duration
--- | --- | ---
Nenhum | A cena de iluminação anterior está descarregada, a nova cena de iluminação é carregada. Sem transição. | Ignored
FadeToBlack | A cena de iluminação anterior esmaece para preto. A nova cena de iluminação é carregada e, em seguida, esmaecida de preto. Útil para transições suaves entre locais. | Usado
Fading cruzado | A cena de iluminação anterior desaparece conforme a nova cena de iluminação esmaece. Útil para transições suaves entre as configurações de iluminação no mesmo local. | Usado

Observe que algumas configurações de iluminação não podem ser interpoladas durante as transições. Se você quiser uma transição Visual suave, essas configurações precisarão permanecer consistentes entre as cenas de iluminação.

Configuração | Transição do Smooth FadeToBlack | Transição de fading cruzado suave
--- | --- | ---
Skybox | Não | Não
Reflexões personalizadas | Não | Não
Sombras em tempo real de luz solar | Sim | Não
