---
title: Foco no Unity
description: Saiba como usar a entrada de foco como uma maneira principal para os usuários direcionarem os hologramas que seu aplicativo cria na realidade misturada.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: eye-gaze, head-gaze, unity, holograma, realidade misturada, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, MRTK, Kit de Ferramentas de Realidade Misturada
ms.openlocfilehash: f10079d36f737e5d8a2ee74a88ca0f8b2b3d791c
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600145"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="60f01-104">Olhar com a cabeça no Unity</span><span class="sxs-lookup"><span data-stu-id="60f01-104">Head-gaze in Unity</span></span>

<span data-ttu-id="60f01-105">[O foco](../../design/gaze-and-commit.md) é a principal maneira para os usuários [direcionarem hologramas que](../../discover/hologram.md) seu aplicativo cria na [Realidade Misturada.](../../discover/mixed-reality.md)</span><span class="sxs-lookup"><span data-stu-id="60f01-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="60f01-106">Implementando o olhar com a cabeça</span><span class="sxs-lookup"><span data-stu-id="60f01-106">Implementing head-gaze</span></span>

<span data-ttu-id="60f01-107">Conceitualmente, você determina [o olhar com](../../design/gaze-and-commit.md) a cabeça projetando um raio para frente do headset do usuário para ver o que ele atinge.</span><span class="sxs-lookup"><span data-stu-id="60f01-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="60f01-108">No Unity, a posição e a direção da cabeça do usuário são expostas por meio da [Câmera,](camera-in-unity.md)especificamente [UnityEngine.Camera.main.](https://docs.unity3d.com/ScriptReference/Camera-main.html) [transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine.Camera.main.](https://docs.unity3d.com/ScriptReference/Camera-main.html) [transform.position.](https://docs.unity3d.com/ScriptReference/Transform-position.html)</span><span class="sxs-lookup"><span data-stu-id="60f01-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="60f01-109">Chamar [o Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) fornece um [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) contendo informações sobre a colisão, incluindo o ponto de colisão 3D e o outro GameObject que o raio de olhar de cabeça atingiu.</span><span class="sxs-lookup"><span data-stu-id="60f01-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="60f01-110">Exemplo: Implementar o olhar com a cabeça</span><span class="sxs-lookup"><span data-stu-id="60f01-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="60f01-111">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="60f01-111">Best practices</span></span>

<span data-ttu-id="60f01-112">Embora o exemplo acima a dispara um único raycast do loop de atualização para encontrar o destino em que os pontos de cabeça do usuário estão, recomendamos usar um único objeto para gerenciar todos os processos de foco com a cabeça.</span><span class="sxs-lookup"><span data-stu-id="60f01-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="60f01-113">Combinar sua lógica de olhar para a cabeça economizará o poder de processamento valioso do aplicativo e limitará o raycasting a um por quadro.</span><span class="sxs-lookup"><span data-stu-id="60f01-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="60f01-114">Visualizando o olhar com a cabeça</span><span class="sxs-lookup"><span data-stu-id="60f01-114">Visualizing head-gaze</span></span>

<span data-ttu-id="60f01-115">Assim como com um ponteiro do mouse em um computador, você deve implementar um [cursor](../../design/cursors.md) que representa o olhar com a cabeça do usuário.</span><span class="sxs-lookup"><span data-stu-id="60f01-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="60f01-116">Saber com qual conteúdo um usuário está direcionando aumenta a confiança no que ele está prestes a interagir.</span><span class="sxs-lookup"><span data-stu-id="60f01-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="60f01-117">Olhar com a cabeça no Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="60f01-117">Head-gaze in the Mixed Reality Toolkit</span></span>

<span data-ttu-id="60f01-118">Você pode acessar o olhar com a cabeça do [Gerenciador de Entrada](/windows/mixed-reality/mrtk-unity/features/input/overview) no MRTK.</span><span class="sxs-lookup"><span data-stu-id="60f01-118">You can access head-gaze from the [Input Manager](/windows/mixed-reality/mrtk-unity/features/input/overview) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="60f01-119">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="60f01-119">Next Development Checkpoint</span></span>

<span data-ttu-id="60f01-120">Se você estiver seguindo o percurso de desenvolvimento do Unity que fizemos, você está no meio da exploração dos blocos de construção principais do MRTK.</span><span class="sxs-lookup"><span data-stu-id="60f01-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="60f01-121">Deste ponto, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="60f01-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="60f01-122">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="60f01-122">Motion controllers</span></span>](motion-controllers-in-unity.md)

<span data-ttu-id="60f01-123">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="60f01-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="60f01-124">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="60f01-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="60f01-125">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="60f01-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="60f01-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="60f01-126">See also</span></span>
* [<span data-ttu-id="60f01-127">Câmera</span><span class="sxs-lookup"><span data-stu-id="60f01-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="60f01-128">Cursores</span><span class="sxs-lookup"><span data-stu-id="60f01-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="60f01-129">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="60f01-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)