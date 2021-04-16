---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528772"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="72751-101">Ferramentas de bloqueio Mundial (recomendado)</span><span class="sxs-lookup"><span data-stu-id="72751-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="72751-102">Recomendamos instalar as ferramentas de bloqueio mundial usando a nova ferramenta de funcionalidade de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="72751-102">We recommend installing World Locking Tools using the new Mixed Reality Feature Tool.</span></span> <span data-ttu-id="72751-103">Depois de baixar a ferramenta de recurso de realidade misturada do link abaixo, selecione a versão mais recente do **WLT Core** na seção de **ferramentas de bloqueio mundial** :</span><span class="sxs-lookup"><span data-stu-id="72751-103">Once you've downloaded the Mixed Reality Feature Tool from the link below, select the latest version of **WLT Core** from the **World Locking Tools** section:</span></span>

![Janela de seleção de recursos da ferramenta de recurso de realidade misturada com ferramentas de bloqueio mundial selecionadas](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="72751-105">Instalar ferramentas de bloqueio mundial com a ferramenta de recurso MR</span><span class="sxs-lookup"><span data-stu-id="72751-105">Install World Locking Tools with the MR Feature Tool</span></span>](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a><span data-ttu-id="72751-106">Configuração automatizada</span><span class="sxs-lookup"><span data-stu-id="72751-106">Automated setup</span></span>

<span data-ttu-id="72751-107">Quando seu projeto estiver pronto para começar, execute o utilitário configurar cena do **Kit de ferramentas de realidade misturada > utilitários > ferramentas de bloqueio mundial**:</span><span class="sxs-lookup"><span data-stu-id="72751-107">When your project is ready to go, run the configure scene utility from **Mixed Reality Toolkit > Utilities > World Locking Tools**:</span></span>

![Editor Unity com o menu do kit de ferramentas da realidade misturada selecionado](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> <span data-ttu-id="72751-109">O utilitário configurar cena pode ser executado novamente a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="72751-109">The Configure scene utility can be rerun at any time.</span></span> <span data-ttu-id="72751-110">Por exemplo, ele deve ser executado novamente se o destino AR tiver sido alterado de herdado para o SDK do XR.</span><span class="sxs-lookup"><span data-stu-id="72751-110">For example, it should be rerun if the AR target has been changed from Legacy to XR SDK.</span></span> <span data-ttu-id="72751-111">Se a cena já estiver configurada corretamente, a execução do utilitário não terá nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="72751-111">If the scene is already properly configured, running the utility has no effect.</span></span>

### <a name="visualizers"></a><span data-ttu-id="72751-112">Visualizadores</span><span class="sxs-lookup"><span data-stu-id="72751-112">Visualizers</span></span>

<span data-ttu-id="72751-113">Durante o desenvolvimento antecipado, adicionar visualizadores pode ser útil para garantir que o WLT esteja configurado e funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="72751-113">During early development, adding visualizers can be helpful to ensure WLT is setup and working properly.</span></span> <span data-ttu-id="72751-114">Eles podem ser removidos para o desempenho de produção ou se por qualquer motivo não forem mais necessários, usando o utilitário remover visualizadores.</span><span class="sxs-lookup"><span data-stu-id="72751-114">They can be removed for production performance, or if for any reason are no longer needed, using the Remove visualizers utility.</span></span> <span data-ttu-id="72751-115">Mais detalhes sobre os visualizadores podem ser encontrados na [documentação de ferramentas](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span><span class="sxs-lookup"><span data-stu-id="72751-115">More details on the visualizers can be found in the [Tools documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="72751-116">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="72751-116">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="72751-117">O plug-in Mixed Reality OpenXR fornece a funcionalidade de ancoragem básica por meio de uma implementação de ARFoundation **ARAnchorManager** do Unity.</span><span class="sxs-lookup"><span data-stu-id="72751-117">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="72751-118">Para aprender as noções básicas sobre o ARAnchors no ARFoundation, visite o [manual do ARFoundation para o gerente de ancoragem ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="72751-118">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="worldanchor"></a>[<span data-ttu-id="72751-119">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="72751-119">WorldAnchor</span></span>](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="72751-120">Criando uma experiência de escala mundial</span><span class="sxs-lookup"><span data-stu-id="72751-120">Building a world-scale experience</span></span>

<span data-ttu-id="72751-121">**Namespace:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="72751-121">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="72751-122">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="72751-122">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="72751-123">Para experiências reais em grande **escala** sobre o HoloLens que permitem aos usuários percorrer mais de 5 metros, você precisará de novas técnicas além das usadas para experiências em escala de sala.</span><span class="sxs-lookup"><span data-stu-id="72751-123">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="72751-124">Uma técnica importante que você usará é criar uma [âncora espacial](../../../../design/coordinate-systems.md#spatial-anchors) para bloquear um cluster de hologramas precisamente no mundo físico, não importa o quanto o usuário está em roaming e, em seguida, [encontrar esses hologramas novamente em sessões posteriores](../../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="72751-124">One key technique you'll use is to create a [spatial anchor](../../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="72751-125">No Unity, você cria uma âncora espacial adicionando o componente **WorldAnchor** Unity a um gameobject.</span><span class="sxs-lookup"><span data-stu-id="72751-125">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="72751-126">Adicionando uma âncora mundial</span><span class="sxs-lookup"><span data-stu-id="72751-126">Adding a World Anchor</span></span>

<span data-ttu-id="72751-127">Para adicionar uma âncora mundial, ligue para `AddComponent<WorldAnchor>()` o objeto Game com a transformação que você deseja ancorar no mundo real.</span><span class="sxs-lookup"><span data-stu-id="72751-127">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="72751-128">É isso!</span><span class="sxs-lookup"><span data-stu-id="72751-128">That's it!</span></span> <span data-ttu-id="72751-129">Este objeto de jogo agora será ancorado ao seu local atual no mundo físico – você pode ver que suas coordenadas do Unity World se ajustam um pouco ao longo do tempo para garantir que o alinhamento físico.</span><span class="sxs-lookup"><span data-stu-id="72751-129">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="72751-130">Consulte [carregando uma âncora mundial](#loading-a-worldanchor) para localizar esse local ancorado novamente em uma sessão de aplicativo futura.</span><span class="sxs-lookup"><span data-stu-id="72751-130">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="72751-131">Removendo uma âncora mundial</span><span class="sxs-lookup"><span data-stu-id="72751-131">Removing a World Anchor</span></span>

<span data-ttu-id="72751-132">Se você não quiser mais que o gameobject seja bloqueado em um local físico do mundo e não pretenda movê-lo para esse quadro, você pode simplesmente chamar Destroy no componente de âncora mundial.</span><span class="sxs-lookup"><span data-stu-id="72751-132">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="72751-133">Se você quiser mover o gameobject para este quadro, precisará chamar DestroyImmediate em vez disso.</span><span class="sxs-lookup"><span data-stu-id="72751-133">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="72751-134">Movendo um jogo de jogos ancorado</span><span class="sxs-lookup"><span data-stu-id="72751-134">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="72751-135">O gameobject não pode ser movido enquanto uma âncora mundial está nele.</span><span class="sxs-lookup"><span data-stu-id="72751-135">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="72751-136">Se você precisar mover o gameobject para este quadro, precisará:</span><span class="sxs-lookup"><span data-stu-id="72751-136">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="72751-137">DestroyImmediate o componente de âncora mundial</span><span class="sxs-lookup"><span data-stu-id="72751-137">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="72751-138">Mover o gameobject</span><span class="sxs-lookup"><span data-stu-id="72751-138">Move the GameObject</span></span>
3. <span data-ttu-id="72751-139">Adicione um novo componente de âncora mundial ao gameobject.</span><span class="sxs-lookup"><span data-stu-id="72751-139">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="72751-140">Manipulando alterações de Locatability</span><span class="sxs-lookup"><span data-stu-id="72751-140">Handling Locatability Changes</span></span>

<span data-ttu-id="72751-141">Um WorldAnchor pode não ser localizável no mundo físico em um ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="72751-141">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="72751-142">Se isso ocorrer, o Unity não atualizará a transformação do objeto ancorado.</span><span class="sxs-lookup"><span data-stu-id="72751-142">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="72751-143">Isso também pode ser alterado enquanto um aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="72751-143">This also can change while an app is running.</span></span> <span data-ttu-id="72751-144">A falha ao manipular a alteração em locatability fará com que o objeto não apareça no local físico correto do mundo.</span><span class="sxs-lookup"><span data-stu-id="72751-144">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="72751-145">Para ser notificado sobre as alterações de locatability:</span><span class="sxs-lookup"><span data-stu-id="72751-145">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="72751-146">Assinar o evento onrastreiechanged</span><span class="sxs-lookup"><span data-stu-id="72751-146">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="72751-147">Manipular o evento</span><span class="sxs-lookup"><span data-stu-id="72751-147">Handle the event</span></span>

<span data-ttu-id="72751-148">O evento **Oncontrolchanged** será chamado sempre que a âncora espacial subjacente for alterada entre o estado de ser localizável versus não ser localizável.</span><span class="sxs-lookup"><span data-stu-id="72751-148">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="72751-149">Em seguida, manipule o evento:</span><span class="sxs-lookup"><span data-stu-id="72751-149">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="72751-150">Às vezes, as âncoras estão localizadas imediatamente.</span><span class="sxs-lookup"><span data-stu-id="72751-150">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="72751-151">Nesse caso, essa propriedade islocalizada da âncora será definida como true quando addComponent <WorldAnchor> () retornar.</span><span class="sxs-lookup"><span data-stu-id="72751-151">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="72751-152">Como resultado, o evento onrastreiochanged não será disparado.</span><span class="sxs-lookup"><span data-stu-id="72751-152">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="72751-153">Um padrão limpo seria chamar o manipulador oncontrolchanged com o estado inicial IsDeleted depois de anexar uma âncora.</span><span class="sxs-lookup"><span data-stu-id="72751-153">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```