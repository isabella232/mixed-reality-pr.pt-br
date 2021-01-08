---
title: Foco no Unity
description: Saiba como usar a entrada olhar como uma maneira primária para os usuários visarem os hologramas que seu aplicativo cria em realidade misturada.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: olho-olhar, cabeça-olhar, Unity, holograma, realidade misturada, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: 5dab8cb38aaa4b9a4547f4bf494afb093b6d8058
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009886"
---
# <a name="head-gaze-in-unity"></a>Cabeça-olhar no Unity

[Olhar](../../design/gaze-and-commit.md) é a principal maneira para os usuários direcionarem os [hologramas](../../discover/hologram.md) que seu aplicativo cria em [realidade misturada](../../discover/mixed-reality.md).

## <a name="implementing-head-gaze"></a>Implementando o Head-olhar

Conceitualmente, você determina o [Head-olhar](../../design/gaze-and-commit.md) projetando um Ray forward do headset do usuário para ver o que ele atinge. No Unity, a posição e a direção da cabeça do usuário são expostas por meio da [câmera](camera-in-unity.md), especificamente [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

Chamar [física. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) fornece a você um [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) que contém informações sobre a colisão, incluindo o ponto de colisão 3D e o outro gameobject com o cabeçalho Head-olhar Ray.

### <a name="example-implement-head-gaze"></a>Exemplo: implementar Head-olhar

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>Práticas recomendadas

Enquanto o exemplo acima dispara um único Raycast do loop de atualização para localizar o destino dos pontos de partida do usuário em, recomendamos usar um único objeto para gerenciar todos os processos olhar. A combinação da lógica Head-olhar economizará a capacidade de processamento precioso do aplicativo e limitará seu raycasting a um por quadro.

## <a name="visualizing-head-gaze"></a>Visualizando a cabeça-olhar

Assim como com um ponteiro do mouse em um computador, você deve implementar um [cursor](../../design/cursors.md) que represente o olhar do usuário. Saber qual conteúdo um usuário está direcionando aumenta a confiança no que eles estão prestes a interagir.

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>Head-olhar no kit de ferramentas da realidade misturada 
Você pode acessar o Head-olhar do [Gerenciador de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) no MRTK.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos blocos de construção do MRTK Core. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Gestos e controladores de movimentos](gestures-and-motion-controllers-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Veja também
* [Câmera](camera-in-unity.md)
* [Cursores](../../design/cursors.md)
* [Focar com a cabeça e confirmar](../../design/gaze-and-commit.md)
