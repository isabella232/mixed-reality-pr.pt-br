---
title: Foco no Unity
description: Saiba como usar a entrada olhar como uma maneira primária para os usuários visarem os hologramas que seu aplicativo cria em realidade misturada.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: olho-olhar, cabeça-olhar, Unity, holograma, realidade misturada, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: 7602eb27da19dc77e4eab1c1a428dc9a1cf8b252
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759682"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="100dd-104">Cabeça-olhar no Unity</span><span class="sxs-lookup"><span data-stu-id="100dd-104">Head-gaze in Unity</span></span>

<span data-ttu-id="100dd-105">[Olhar](../../design/gaze-and-commit.md) é a principal maneira para os usuários direcionarem os [hologramas](../../discover/hologram.md) que seu aplicativo cria em [realidade misturada](../../discover/mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="100dd-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="100dd-106">Implementando o Head-olhar</span><span class="sxs-lookup"><span data-stu-id="100dd-106">Implementing head-gaze</span></span>

<span data-ttu-id="100dd-107">Conceitualmente, você determina o [Head-olhar](../../design/gaze-and-commit.md) projetando um Ray forward do headset do usuário para ver o que ele atinge.</span><span class="sxs-lookup"><span data-stu-id="100dd-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="100dd-108">No Unity, a posição e a direção da cabeça do usuário são expostas por meio da [câmera](camera-in-unity.md), especificamente [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="100dd-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="100dd-109">Chamar [física. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) fornece a você um [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) que contém informações sobre a colisão, incluindo o ponto de colisão 3D e o outro gameobject com o cabeçalho Head-olhar Ray.</span><span class="sxs-lookup"><span data-stu-id="100dd-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="100dd-110">Exemplo: implementar Head-olhar</span><span class="sxs-lookup"><span data-stu-id="100dd-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="100dd-111">Melhores práticas</span><span class="sxs-lookup"><span data-stu-id="100dd-111">Best practices</span></span>

<span data-ttu-id="100dd-112">Enquanto o exemplo acima dispara um único Raycast do loop de atualização para localizar o destino dos pontos de partida do usuário em, recomendamos usar um único objeto para gerenciar todos os processos olhar.</span><span class="sxs-lookup"><span data-stu-id="100dd-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="100dd-113">A combinação da lógica Head-olhar economizará a capacidade de processamento precioso do aplicativo e limitará seu raycasting a um por quadro.</span><span class="sxs-lookup"><span data-stu-id="100dd-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="100dd-114">Visualizando a cabeça-olhar</span><span class="sxs-lookup"><span data-stu-id="100dd-114">Visualizing head-gaze</span></span>

<span data-ttu-id="100dd-115">Assim como com um ponteiro do mouse em um computador, você deve implementar um [cursor](../../design/cursors.md) que represente o olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="100dd-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="100dd-116">Saber qual conteúdo um usuário está direcionando aumenta a confiança no que eles estão prestes a interagir.</span><span class="sxs-lookup"><span data-stu-id="100dd-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="100dd-117">Head-olhar no kit de ferramentas da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="100dd-117">Head-gaze in the Mixed Reality Toolkit</span></span> 
<span data-ttu-id="100dd-118">Você pode acessar o Head-olhar do [Gerenciador de entrada](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md) no MRTK.</span><span class="sxs-lookup"><span data-stu-id="100dd-118">You can access head-gaze from the [Input Manager](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="100dd-119">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="100dd-119">Next Development Checkpoint</span></span>

<span data-ttu-id="100dd-120">Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos blocos de construção do MRTK Core.</span><span class="sxs-lookup"><span data-stu-id="100dd-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="100dd-121">Deste ponto, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="100dd-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="100dd-122">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="100dd-122">Motion controllers</span></span>](motion-controllers-in-unity.md)

<span data-ttu-id="100dd-123">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="100dd-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="100dd-124">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="100dd-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="100dd-125">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="100dd-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="100dd-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="100dd-126">See also</span></span>
* [<span data-ttu-id="100dd-127">Câmera</span><span class="sxs-lookup"><span data-stu-id="100dd-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="100dd-128">Cursores</span><span class="sxs-lookup"><span data-stu-id="100dd-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="100dd-129">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="100dd-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
