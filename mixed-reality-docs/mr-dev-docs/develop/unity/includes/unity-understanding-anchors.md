---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719782"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="da82f-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="da82f-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="da82f-102">O plug-in Mixed Reality OpenXR fornece a funcionalidade de ancoragem básica por meio de uma implementação de ARFoundation **ARAnchorManager** do Unity.</span><span class="sxs-lookup"><span data-stu-id="da82f-102">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="da82f-103">Para aprender as noções básicas sobre o ARAnchors no ARFoundation, visite o [manual do ARFoundation para o gerente de ancoragem ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="da82f-103">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="da82f-104">Plug-in do Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="da82f-104">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="da82f-105">O plug-in Mixed Reality OpenXR fornece a funcionalidade de ancoragem básica por meio de uma implementação de ARFoundation **ARAnchorManager** do Unity.</span><span class="sxs-lookup"><span data-stu-id="da82f-105">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="da82f-106">Para aprender as noções básicas sobre o ARAnchors no ARFoundation, visite o [manual do ARFoundation para o gerente de ancoragem ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="da82f-106">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="da82f-107">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="da82f-107">Legacy WSA</span></span>](#tab/wsa)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="da82f-108">Criando uma experiência de escala mundial</span><span class="sxs-lookup"><span data-stu-id="da82f-108">Building a world-scale experience</span></span>

<span data-ttu-id="da82f-109">**Namespace:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="da82f-109">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="da82f-110">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="da82f-110">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="da82f-111">Para experiências reais em grande **escala** sobre o HoloLens que permitem aos usuários percorrer mais de 5 metros, você precisará de novas técnicas além das usadas para experiências em escala de sala.</span><span class="sxs-lookup"><span data-stu-id="da82f-111">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="da82f-112">Uma técnica importante que você usará é criar uma [âncora espacial](../../../design/coordinate-systems.md#spatial-anchors) para bloquear um cluster de hologramas precisamente no mundo físico, não importa o quanto o usuário está em roaming e, em seguida, [encontrar esses hologramas novamente em sessões posteriores](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="da82f-112">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="da82f-113">No Unity, você cria uma âncora espacial adicionando o componente **WorldAnchor** Unity a um gameobject.</span><span class="sxs-lookup"><span data-stu-id="da82f-113">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="da82f-114">Adicionando uma âncora mundial</span><span class="sxs-lookup"><span data-stu-id="da82f-114">Adding a World Anchor</span></span>

<span data-ttu-id="da82f-115">Para adicionar uma âncora mundial, ligue para `AddComponent<WorldAnchor>()` o objeto Game com a transformação que você deseja ancorar no mundo real.</span><span class="sxs-lookup"><span data-stu-id="da82f-115">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="da82f-116">É isso!</span><span class="sxs-lookup"><span data-stu-id="da82f-116">That's it!</span></span> <span data-ttu-id="da82f-117">Este objeto de jogo agora será ancorado ao seu local atual no mundo físico – você pode ver que suas coordenadas do Unity World se ajustam um pouco ao longo do tempo para garantir que o alinhamento físico.</span><span class="sxs-lookup"><span data-stu-id="da82f-117">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="da82f-118">Consulte [carregando uma âncora mundial](#loading-a-worldanchor) para localizar esse local ancorado novamente em uma sessão de aplicativo futura.</span><span class="sxs-lookup"><span data-stu-id="da82f-118">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="da82f-119">Removendo uma âncora mundial</span><span class="sxs-lookup"><span data-stu-id="da82f-119">Removing a World Anchor</span></span>

<span data-ttu-id="da82f-120">Se você não quiser mais que o gameobject seja bloqueado em um local físico do mundo e não pretenda movê-lo para esse quadro, você pode simplesmente chamar Destroy no componente de âncora mundial.</span><span class="sxs-lookup"><span data-stu-id="da82f-120">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="da82f-121">Se você quiser mover o gameobject para este quadro, precisará chamar DestroyImmediate em vez disso.</span><span class="sxs-lookup"><span data-stu-id="da82f-121">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="da82f-122">Movendo um jogo de jogos ancorado</span><span class="sxs-lookup"><span data-stu-id="da82f-122">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="da82f-123">O gameobject não pode ser movido enquanto uma âncora mundial está nele.</span><span class="sxs-lookup"><span data-stu-id="da82f-123">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="da82f-124">Se você precisar mover o gameobject para este quadro, precisará:</span><span class="sxs-lookup"><span data-stu-id="da82f-124">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="da82f-125">DestroyImmediate o componente de âncora mundial</span><span class="sxs-lookup"><span data-stu-id="da82f-125">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="da82f-126">Mover o gameobject</span><span class="sxs-lookup"><span data-stu-id="da82f-126">Move the GameObject</span></span>
3. <span data-ttu-id="da82f-127">Adicione um novo componente de âncora mundial ao gameobject.</span><span class="sxs-lookup"><span data-stu-id="da82f-127">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="da82f-128">Manipulando alterações de Locatability</span><span class="sxs-lookup"><span data-stu-id="da82f-128">Handling Locatability Changes</span></span>

<span data-ttu-id="da82f-129">Um WorldAnchor pode não ser localizável no mundo físico em um ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="da82f-129">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="da82f-130">Se isso ocorrer, o Unity não atualizará a transformação do objeto ancorado.</span><span class="sxs-lookup"><span data-stu-id="da82f-130">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="da82f-131">Isso também pode ser alterado enquanto um aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="da82f-131">This also can change while an app is running.</span></span> <span data-ttu-id="da82f-132">A falha ao manipular a alteração em locatability fará com que o objeto não apareça no local físico correto do mundo.</span><span class="sxs-lookup"><span data-stu-id="da82f-132">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="da82f-133">Para ser notificado sobre as alterações de locatability:</span><span class="sxs-lookup"><span data-stu-id="da82f-133">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="da82f-134">Assinar o evento onrastreiechanged</span><span class="sxs-lookup"><span data-stu-id="da82f-134">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="da82f-135">Manipular o evento</span><span class="sxs-lookup"><span data-stu-id="da82f-135">Handle the event</span></span>

<span data-ttu-id="da82f-136">O evento **Oncontrolchanged** será chamado sempre que a âncora espacial subjacente for alterada entre o estado de ser localizável versus não ser localizável.</span><span class="sxs-lookup"><span data-stu-id="da82f-136">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="da82f-137">Em seguida, manipule o evento:</span><span class="sxs-lookup"><span data-stu-id="da82f-137">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="da82f-138">Às vezes, as âncoras estão localizadas imediatamente.</span><span class="sxs-lookup"><span data-stu-id="da82f-138">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="da82f-139">Nesse caso, essa propriedade islocalizada da âncora será definida como true quando addComponent <WorldAnchor> () retornar.</span><span class="sxs-lookup"><span data-stu-id="da82f-139">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="da82f-140">Como resultado, o evento onrastreiochanged não será disparado.</span><span class="sxs-lookup"><span data-stu-id="da82f-140">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="da82f-141">Um padrão limpo seria chamar o manipulador oncontrolchanged com o estado inicial IsDeleted depois de anexar uma âncora.</span><span class="sxs-lookup"><span data-stu-id="da82f-141">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```