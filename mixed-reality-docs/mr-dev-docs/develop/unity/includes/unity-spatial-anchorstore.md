---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603366"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="43fcc-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="43fcc-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

> [!NOTE]
> <span data-ttu-id="43fcc-102">Essas âncoras devem ser salvas e carregadas no mesmo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="43fcc-102">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="43fcc-103">O armazenamento de âncora entre dispositivos terá suporte por meio de âncoras espaciais do Azure em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="43fcc-103">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="43fcc-104">Para carregar o XRAnchorStore, o plug-in fornece um método de extensão no XRAnchorSubsystem, o subsistema de um ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="43fcc-104">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="43fcc-105">Para usar esse método de extensão, acesse-o de um subsistema de ARAnchorManager da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="43fcc-105">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="43fcc-106">Para ver um exemplo completo de persistência/descontinuação de âncoras, confira o exemplo âncoras-> ancoras Games e o script AnchorsSample.cs na [cena de exemplo do plugin OpenXR de realidade misturada](../openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="43fcc-106">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![Captura de tela do painel hierarquia aberta no editor do Unity com o exemplo âncoras realçado](../images/openxr-features-img-04.png)

![Captura de tela do painel Inspetor aberto no editor do Unity com o script de exemplo âncoras realçado](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="43fcc-109">Plug-in do Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="43fcc-109">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

> [!NOTE]
> <span data-ttu-id="43fcc-110">Essas âncoras devem ser salvas e carregadas no mesmo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="43fcc-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="43fcc-111">O armazenamento de âncora entre dispositivos terá suporte por meio de âncoras espaciais do Azure em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="43fcc-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class UnityEngine.XR.WindowsMR.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(TrackableId id, string name);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="43fcc-112">Para carregar o XRAnchorStore, o plug-in fornece um método de extensão no XRReferencePointSubsystem (Unity 2019) ou XRAnchorSubsystem (Unity 2020), o subsistema de um ARReferencePointManager/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="43fcc-112">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="43fcc-113">Para usar esse método de extensão, acesse-o do subsistema de um ARAnchorManager da seguinte maneira para o Unity 2019:</span><span class="sxs-lookup"><span data-stu-id="43fcc-113">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="43fcc-114">ou para o Unity 2020:</span><span class="sxs-lookup"><span data-stu-id="43fcc-114">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="43fcc-115">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="43fcc-115">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="43fcc-116">**Namespace:** *UnityEngine. XR. WSA. Persistence*</span><span class="sxs-lookup"><span data-stu-id="43fcc-116">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="43fcc-117">**Classe:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="43fcc-117">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="43fcc-118">O WorldAnchorStore permitirá que você persista o local de WorldAnchor entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="43fcc-118">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="43fcc-119">Para realmente manter os hologramas entre as sessões, você precisará controlar separadamente seus GameObjects que usam uma âncora mundial específica.</span><span class="sxs-lookup"><span data-stu-id="43fcc-119">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="43fcc-120">Geralmente faz sentido criar uma raiz gameobject com uma âncora mundial e ter hologramas filhos ancorados por ela com um deslocamento de posição local.</span><span class="sxs-lookup"><span data-stu-id="43fcc-120">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="43fcc-121">Para carregar os hologramas de sessões anteriores:</span><span class="sxs-lookup"><span data-stu-id="43fcc-121">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="43fcc-122">Obter o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="43fcc-122">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="43fcc-123">Carregar dados de aplicativo relacionados à âncora mundial, que fornece a ID da âncora mundial</span><span class="sxs-lookup"><span data-stu-id="43fcc-123">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="43fcc-124">Carregar uma âncora mundial de sua ID</span><span class="sxs-lookup"><span data-stu-id="43fcc-124">Load a world anchor from its ID</span></span>

<span data-ttu-id="43fcc-125">Para salvar os hologramas para sessões futuras:</span><span class="sxs-lookup"><span data-stu-id="43fcc-125">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="43fcc-126">Obter o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="43fcc-126">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="43fcc-127">Salvar uma âncora mundial especificando uma ID</span><span class="sxs-lookup"><span data-stu-id="43fcc-127">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="43fcc-128">Salvar dados de aplicativo relacionados à âncora mundial, juntamente com uma ID</span><span class="sxs-lookup"><span data-stu-id="43fcc-128">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="43fcc-129">Obtendo o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="43fcc-129">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="43fcc-130">Você desejará manter uma referência ao WorldAnchorStore para saber quando ele está pronto para executar uma operação.</span><span class="sxs-lookup"><span data-stu-id="43fcc-130">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="43fcc-131">Como essa é uma chamada assíncrona, possivelmente assim que iniciar, você deseja chamar:</span><span class="sxs-lookup"><span data-stu-id="43fcc-131">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="43fcc-132">O StoreLoaded nesse caso é nosso manipulador para quando o WorldAnchorStore tiver concluído o carregamento:</span><span class="sxs-lookup"><span data-stu-id="43fcc-132">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="43fcc-133">Agora temos uma referência para o WorldAnchorStore, que usaremos para salvar e carregar âncoras mundiais específicas.</span><span class="sxs-lookup"><span data-stu-id="43fcc-133">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="43fcc-134">Salvando um WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="43fcc-134">Saving a WorldAnchor</span></span>

<span data-ttu-id="43fcc-135">Para economizar, precisamos simplesmente nomear o que estamos salvando e passá-lo no WorldAnchor que temos antes de se desejarmos salvar.</span><span class="sxs-lookup"><span data-stu-id="43fcc-135">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="43fcc-136">Observação: tentar salvar duas âncoras na mesma cadeia de caracteres falhará (Store. Save retornará false).</span><span class="sxs-lookup"><span data-stu-id="43fcc-136">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="43fcc-137">Exclua o salvamento anterior antes de salvar o novo:</span><span class="sxs-lookup"><span data-stu-id="43fcc-137">Delete the previous save before saving the new one:</span></span>

```cs
private void SaveGame()
{
    // Save data about holograms positioned by this world anchor
    if (!this.savedRoot) // Only Save the root once
    {
           this.savedRoot = this.store.Save("rootGameObject", anchor);
           Assert(this.savedRoot);
    }
}
```

### <a name="loading-a-worldanchor"></a><span data-ttu-id="43fcc-138">Carregando um WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="43fcc-138">Loading a WorldAnchor</span></span>

<span data-ttu-id="43fcc-139">E para carregar:</span><span class="sxs-lookup"><span data-stu-id="43fcc-139">And to load:</span></span>

```cs
private void LoadGame()
{
    // Save data about holograms positioned by this world anchor
    this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
    if (!this.savedRoot)
    {
        s// We didn't actually have the game root saved! We have to re-place our objects or start over
    }
}
```

<span data-ttu-id="43fcc-140">Além disso, podemos usar Store. Delete () para remover uma âncora que salvamos e armazenamos anteriormente. Clear () para remover todos os dados salvos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="43fcc-140">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="43fcc-141">Enumerando âncoras existentes</span><span class="sxs-lookup"><span data-stu-id="43fcc-141">Enumerating Existing Anchors</span></span>

<span data-ttu-id="43fcc-142">Para descobrir âncoras armazenadas anteriormente, chame GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="43fcc-142">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="43fcc-143">Criando uma experiência de escala mundial</span><span class="sxs-lookup"><span data-stu-id="43fcc-143">Building a world-scale experience</span></span>

<span data-ttu-id="43fcc-144">**Namespace:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="43fcc-144">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="43fcc-145">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="43fcc-145">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="43fcc-146">Para experiências reais em grande **escala** sobre o HoloLens que permitem aos usuários percorrer mais de 5 metros, você precisará de novas técnicas além das usadas para experiências em escala de sala.</span><span class="sxs-lookup"><span data-stu-id="43fcc-146">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="43fcc-147">Uma técnica importante que você usará é criar uma [âncora espacial](../../../design/coordinate-systems.md#spatial-anchors) para bloquear um cluster de hologramas precisamente no mundo físico, não importa o quanto o usuário está em roaming e, em seguida, [encontrar esses hologramas novamente em sessões posteriores](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="43fcc-147">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="43fcc-148">No Unity, você cria uma âncora espacial adicionando o componente **WorldAnchor** Unity a um gameobject.</span><span class="sxs-lookup"><span data-stu-id="43fcc-148">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="43fcc-149">Adicionando uma âncora mundial</span><span class="sxs-lookup"><span data-stu-id="43fcc-149">Adding a World Anchor</span></span>

<span data-ttu-id="43fcc-150">Para adicionar uma âncora mundial, ligue para `AddComponent<WorldAnchor>()` o objeto Game com a transformação que você deseja ancorar no mundo real.</span><span class="sxs-lookup"><span data-stu-id="43fcc-150">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="43fcc-151">É isso!</span><span class="sxs-lookup"><span data-stu-id="43fcc-151">That's it!</span></span> <span data-ttu-id="43fcc-152">Este objeto de jogo agora será ancorado ao seu local atual no mundo físico – você pode ver que suas coordenadas do Unity World se ajustam um pouco ao longo do tempo para garantir que o alinhamento físico.</span><span class="sxs-lookup"><span data-stu-id="43fcc-152">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="43fcc-153">Consulte [carregando uma âncora mundial](#loading-a-worldanchor) para localizar esse local ancorado novamente em uma sessão de aplicativo futura.</span><span class="sxs-lookup"><span data-stu-id="43fcc-153">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="43fcc-154">Removendo uma âncora mundial</span><span class="sxs-lookup"><span data-stu-id="43fcc-154">Removing a World Anchor</span></span>

<span data-ttu-id="43fcc-155">Se você não quiser mais que o gameobject seja bloqueado em um local físico do mundo e não pretenda movê-lo para esse quadro, você pode simplesmente chamar Destroy no componente de âncora mundial.</span><span class="sxs-lookup"><span data-stu-id="43fcc-155">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="43fcc-156">Se você quiser mover o gameobject para este quadro, precisará chamar DestroyImmediate em vez disso.</span><span class="sxs-lookup"><span data-stu-id="43fcc-156">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="43fcc-157">Movendo um jogo de jogos ancorado</span><span class="sxs-lookup"><span data-stu-id="43fcc-157">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="43fcc-158">O gameobject não pode ser movido enquanto uma âncora mundial está nele.</span><span class="sxs-lookup"><span data-stu-id="43fcc-158">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="43fcc-159">Se você precisar mover o gameobject para este quadro, precisará:</span><span class="sxs-lookup"><span data-stu-id="43fcc-159">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="43fcc-160">DestroyImmediate o componente de âncora mundial</span><span class="sxs-lookup"><span data-stu-id="43fcc-160">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="43fcc-161">Mover o gameobject</span><span class="sxs-lookup"><span data-stu-id="43fcc-161">Move the GameObject</span></span>
3. <span data-ttu-id="43fcc-162">Adicione um novo componente de âncora mundial ao gameobject.</span><span class="sxs-lookup"><span data-stu-id="43fcc-162">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="43fcc-163">Manipulando alterações de Locatability</span><span class="sxs-lookup"><span data-stu-id="43fcc-163">Handling Locatability Changes</span></span>

<span data-ttu-id="43fcc-164">Um WorldAnchor pode não ser localizável no mundo físico em um ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="43fcc-164">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="43fcc-165">Se isso ocorrer, o Unity não atualizará a transformação do objeto ancorado.</span><span class="sxs-lookup"><span data-stu-id="43fcc-165">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="43fcc-166">Isso também pode ser alterado enquanto um aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="43fcc-166">This also can change while an app is running.</span></span> <span data-ttu-id="43fcc-167">A falha ao manipular a alteração em locatability fará com que o objeto não apareça no local físico correto do mundo.</span><span class="sxs-lookup"><span data-stu-id="43fcc-167">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="43fcc-168">Para ser notificado sobre as alterações de locatability:</span><span class="sxs-lookup"><span data-stu-id="43fcc-168">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="43fcc-169">Assinar o evento onrastreiechanged</span><span class="sxs-lookup"><span data-stu-id="43fcc-169">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="43fcc-170">Manipular o evento</span><span class="sxs-lookup"><span data-stu-id="43fcc-170">Handle the event</span></span>

<span data-ttu-id="43fcc-171">O evento **Oncontrolchanged** será chamado sempre que a âncora espacial subjacente for alterada entre o estado de ser localizável versus não ser localizável.</span><span class="sxs-lookup"><span data-stu-id="43fcc-171">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="43fcc-172">Em seguida, manipule o evento:</span><span class="sxs-lookup"><span data-stu-id="43fcc-172">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="43fcc-173">Às vezes, as âncoras estão localizadas imediatamente.</span><span class="sxs-lookup"><span data-stu-id="43fcc-173">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="43fcc-174">Nesse caso, essa propriedade islocalizada da âncora será definida como true quando addComponent <WorldAnchor> () retornar.</span><span class="sxs-lookup"><span data-stu-id="43fcc-174">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="43fcc-175">Como resultado, o evento onrastreiochanged não será disparado.</span><span class="sxs-lookup"><span data-stu-id="43fcc-175">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="43fcc-176">Um padrão limpo seria chamar o manipulador oncontrolchanged com o estado inicial IsDeleted depois de anexar uma âncora.</span><span class="sxs-lookup"><span data-stu-id="43fcc-176">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="43fcc-177">Persistendo hologramas para vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="43fcc-177">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="43fcc-178">Você pode usar <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar uma âncora de nuvem durável a partir de um WorldAnchor local, que seu aplicativo pode localizar em vários dispositivos de HoloLens, Ios e Android, mesmo se esses dispositivos não estiverem presentes juntos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="43fcc-178">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="43fcc-179">Como as âncoras de nuvem são persistentes, vários dispositivos ao longo do tempo podem ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="43fcc-179">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="43fcc-180">Para começar a criar experiências compartilhadas no Unity, experimente os guias de início rápido dos separadores <a href="/azure/spatial-anchors/unity-overview" target="_blank">espaciais do Azure</a>de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="43fcc-180">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="43fcc-181">Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar âncoras no Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="43fcc-181">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
