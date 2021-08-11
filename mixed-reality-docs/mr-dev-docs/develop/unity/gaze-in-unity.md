---
title: Foco no Unity
description: Saiba como usar a entrada de foco como uma maneira principal para os usuários direcionarem os hologramas que seu aplicativo cria na realidade misturada.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: eye-gaze, head-gaze, unity, holograma, realidade misturada, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, MRTK, realidade misturada Toolkit
ms.openlocfilehash: c6a435e958a92adeed6cd965bebd0b8829e00da735bd193ca72a68acb9e0d6aa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200104"
---
# <a name="head-gaze-in-unity"></a>Olhar com a cabeça no Unity

[O foco](../../design/gaze-and-commit.md) é a principal maneira para os usuários [direcionarem hologramas que](../../discover/hologram.md) seu aplicativo cria na [Realidade Misturada.](../../discover/mixed-reality.md)

## <a name="implementing-head-gaze"></a>Implementando o olhar com a cabeça

Conceitualmente, você determina [o olhar com](../../design/gaze-and-commit.md) a cabeça projetando um raio para frente do headset do usuário para ver o que ele atinge. No Unity, a posição e a direção da cabeça do usuário são expostas por meio da [Câmera,](camera-in-unity.md)especificamente [UnityEngine.Camera.main.](https://docs.unity3d.com/ScriptReference/Camera-main.html) [transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine.Camera.main.](https://docs.unity3d.com/ScriptReference/Camera-main.html) [transform.position.](https://docs.unity3d.com/ScriptReference/Transform-position.html)

Chamar [o Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) fornece um [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) contendo informações sobre a colisão, incluindo o ponto de colisão 3D e o outro GameObject que o raio de olhar de cabeça atingiu.

### <a name="example-implement-head-gaze"></a>Exemplo: Implementar o olhar com a cabeça

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

Embora o exemplo acima a dispara um único raycast do loop de atualização para encontrar o destino em que os pontos de cabeça do usuário estão, recomendamos usar um único objeto para gerenciar todos os processos de foco com a cabeça. Combinar sua lógica de olhar para a cabeça economizará o poder de processamento valioso do aplicativo e limitará o raycasting a um por quadro.

## <a name="visualizing-head-gaze"></a>Visualizando o olhar com a cabeça

Assim como com um ponteiro do mouse em um computador, você deve implementar um [cursor](../../design/cursors.md) que representa o olhar com a cabeça do usuário. Saber com qual conteúdo um usuário está direcionando aumenta a confiança no que ele está prestes a interagir.

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>Olhar com a cabeça na área de Realidade Misturada Toolkit

Você pode acessar o olhar com a cabeça do [Gerenciador de Entrada](/windows/mixed-reality/mrtk-unity/features/input/overview) no MRTK.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo o percurso de desenvolvimento do Unity que fizemos, você está no meio da exploração dos blocos de construção principais do MRTK. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Controladores de movimentos](motion-controllers-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Confira também
* [Câmera](camera-in-unity.md)
* [Cursores](../../design/cursors.md)
* [Focar com a cabeça e confirmar](../../design/gaze-and-commit.md)