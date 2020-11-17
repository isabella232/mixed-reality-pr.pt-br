---
title: Foco no Unity
description: Olhar é uma maneira primária para os usuários direcionarem os hologramas que seu aplicativo cria em realidade misturada.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: olho-olhar, cabeça-olhar, Unity, holograma, realidade misturada, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: 0c62de9cb1b7ea892831ea2cedbeb23be5ea7b37
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677505"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="be623-104">Cabeça-olhar no Unity</span><span class="sxs-lookup"><span data-stu-id="be623-104">Head-gaze in Unity</span></span>

<span data-ttu-id="be623-105">[Olhar](../../design/gaze-and-commit.md) é uma maneira primária para os usuários direcionarem os [hologramas](../../discover/hologram.md) que seu aplicativo cria em [realidade misturada](../../discover/mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="be623-105">[Gaze](../../design/gaze-and-commit.md) is a primary way for users to target the [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="be623-106">Implementando o Head-olhar</span><span class="sxs-lookup"><span data-stu-id="be623-106">Implementing head-gaze</span></span>

<span data-ttu-id="be623-107">Conceitualmente, o [Head-olhar](../../design/gaze-and-commit.md) é implementado projetando um raio a partir da cabeça do usuário onde o headset está, na direção de encaminhamento que estão enfrentando e determinando o que o raio colide com.</span><span class="sxs-lookup"><span data-stu-id="be623-107">Conceptually, [head-gaze](../../design/gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span>
<span data-ttu-id="be623-108">No Unity, a posição e a direção da cabeça do usuário são expostas por meio da [câmera](camera-in-unity.md)principal do Unity, especificamente [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="be623-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="be623-109">Chamar o [física. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) resulta em uma estrutura [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) que contém informações sobre a colisão, incluindo o ponto 3D em que ocorreu a colisão e o outro gameobject com o cabeçalho-olhar Ray colisado.</span><span class="sxs-lookup"><span data-stu-id="be623-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="be623-110">Exemplo: implementar Head-olhar</span><span class="sxs-lookup"><span data-stu-id="be623-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="be623-111">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="be623-111">Best practices</span></span>

<span data-ttu-id="be623-112">Embora o exemplo acima demonstre como fazer um único Raycast em um loop de atualização para localizar o destino dos pontos de partida do usuário em, é recomendável fazer isso em um único objeto Gerenciando Head-olhar em vez de fazer isso em qualquer objeto que esteja potencialmente interessado no objeto sendo gazed.</span><span class="sxs-lookup"><span data-stu-id="be623-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="be623-113">Isso permite que seu aplicativo salve o processamento fazendo apenas uma cabeça-olhar Raycast cada quadro.</span><span class="sxs-lookup"><span data-stu-id="be623-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="be623-114">Visualizando a cabeça-olhar</span><span class="sxs-lookup"><span data-stu-id="be623-114">Visualizing head-gaze</span></span>

<span data-ttu-id="be623-115">Assim como no desktop em que você usa um ponteiro do mouse para direcionar e interagir com o conteúdo, você deve implementar um [cursor](../../design/cursors.md) que represente o olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="be623-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="be623-116">Isso dá ao usuário confiança no que eles estão prestes a interagir.</span><span class="sxs-lookup"><span data-stu-id="be623-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="be623-117">Head-olhar no kit de ferramentas da realidade misturada v2</span><span class="sxs-lookup"><span data-stu-id="be623-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="be623-118">Você pode acessar o Head-olhar do [Gerenciador de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) no MRTK v2.</span><span class="sxs-lookup"><span data-stu-id="be623-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="be623-119">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="be623-119">Next Development Checkpoint</span></span>

<span data-ttu-id="be623-120">Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unity, você está no meio da exploração dos principais blocos de construção do MRTK.</span><span class="sxs-lookup"><span data-stu-id="be623-120">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="be623-121">De lá, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="be623-121">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be623-122">Gestos e controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="be623-122">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)

<span data-ttu-id="be623-123">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="be623-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be623-124">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="be623-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="be623-125">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="be623-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="be623-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="be623-126">See also</span></span>
* [<span data-ttu-id="be623-127">Câmera</span><span class="sxs-lookup"><span data-stu-id="be623-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="be623-128">Cursores</span><span class="sxs-lookup"><span data-stu-id="be623-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="be623-129">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="be623-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
