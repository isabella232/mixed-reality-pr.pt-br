---
ms.openlocfilehash: bb2df8c85dd05981c1438bdb076b0aad16c7efd7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719845"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="88364-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="88364-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="88364-102">Uma API adicional chamada **XRAnchorStore** permite que as âncoras sejam persistidas entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="88364-102">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="88364-103">O XRAnchorStore é uma representação das âncoras salvas em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="88364-103">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="88364-104">As âncoras podem persistir de **ARAnchors** na cena do Unity, carregadas do armazenamento para o New **ARAnchors** ou excluídas do armazenamento.</span><span class="sxs-lookup"><span data-stu-id="88364-104">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="88364-105">Essas âncoras devem ser salvas e carregadas no mesmo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="88364-105">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="88364-106">O armazenamento de âncora entre dispositivos terá suporte por meio de âncoras espaciais do Azure em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="88364-106">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="88364-107">Para carregar o XRAnchorStore, o plug-in fornece um método de extensão no XRAnchorSubsystem, o subsistema de um ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="88364-107">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="88364-108">Para usar esse método de extensão, acesse-o de um subsistema de ARAnchorManager da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="88364-108">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="88364-109">Para ver um exemplo completo de persistência/descontinuação de âncoras, confira o script ancoragem-> ancoragems de exemplo Gamesobject e AnchorsSample. cs na [cena de exemplo do plugin OpenXR da realidade misturada](../openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="88364-109">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![Captura de tela do painel hierarquia aberta no editor do Unity com o exemplo âncoras realçado](../images/openxr-features-img-04.png)

![Captura de tela do painel Inspetor aberto no editor do Unity com o script de exemplo âncoras realçado](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="88364-112">Plug-in do Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="88364-112">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="88364-113">Uma API chamada **XRAnchorStore** permite que as âncoras sejam persistidas entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="88364-113">An API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="88364-114">O XRAnchorStore é uma representação das âncoras salvas em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="88364-114">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="88364-115">As âncoras podem persistir de **ARAnchors** na cena do Unity, carregadas do armazenamento para o New **ARAnchors** ou excluídas do armazenamento.</span><span class="sxs-lookup"><span data-stu-id="88364-115">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="88364-116">Essas âncoras devem ser salvas e carregadas no mesmo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="88364-116">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="88364-117">O armazenamento de âncora entre dispositivos terá suporte por meio de âncoras espaciais do Azure em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="88364-117">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="88364-118">Para carregar o XRAnchorStore, o plug-in fornece um método de extensão no XRReferencePointSubsystem (Unity 2019) ou XRAnchorSubsystem (Unity 2020), o subsistema de um ARReferencePointManager/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="88364-118">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="88364-119">Para usar esse método de extensão, acesse-o do subsistema de um ARAnchorManager da seguinte maneira para o Unity 2019:</span><span class="sxs-lookup"><span data-stu-id="88364-119">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="88364-120">ou para o Unity 2020:</span><span class="sxs-lookup"><span data-stu-id="88364-120">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="88364-121">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="88364-121">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="88364-122">O **WorldAnchorStore** é a chave para criar experiências de Holographic em que os hologramas permanecem em posições reais específicas entre instâncias do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88364-122">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="88364-123">Os usuários podem então fixar os hologramas individuais onde quiserem e encontrá-los mais tarde no mesmo ponto em vários usos de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88364-123">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="88364-124">**Namespace:** *UnityEngine. XR. WSA. Persistence*</span><span class="sxs-lookup"><span data-stu-id="88364-124">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="88364-125">**Classe:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="88364-125">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="88364-126">O WorldAnchorStore permitirá que você persista o local de WorldAnchor entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="88364-126">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="88364-127">Para realmente manter os hologramas entre as sessões, você precisará controlar separadamente seus GameObjects que usam uma âncora mundial específica.</span><span class="sxs-lookup"><span data-stu-id="88364-127">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="88364-128">Geralmente faz sentido criar uma raiz gameobject com uma âncora mundial e ter hologramas filhos ancorados por ela com um deslocamento de posição local.</span><span class="sxs-lookup"><span data-stu-id="88364-128">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="88364-129">Para carregar os hologramas de sessões anteriores:</span><span class="sxs-lookup"><span data-stu-id="88364-129">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="88364-130">Obter o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="88364-130">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="88364-131">Carregar dados de aplicativo relacionados à âncora mundial, que fornece a ID da âncora mundial</span><span class="sxs-lookup"><span data-stu-id="88364-131">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="88364-132">Carregar uma âncora mundial de sua ID</span><span class="sxs-lookup"><span data-stu-id="88364-132">Load a world anchor from its ID</span></span>

<span data-ttu-id="88364-133">Para salvar os hologramas para sessões futuras:</span><span class="sxs-lookup"><span data-stu-id="88364-133">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="88364-134">Obter o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="88364-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="88364-135">Salvar uma âncora mundial especificando uma ID</span><span class="sxs-lookup"><span data-stu-id="88364-135">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="88364-136">Salvar dados de aplicativo relacionados à âncora mundial, juntamente com uma ID</span><span class="sxs-lookup"><span data-stu-id="88364-136">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="88364-137">Obtendo o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="88364-137">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="88364-138">Você desejará manter uma referência ao WorldAnchorStore para saber quando ele está pronto para executar uma operação.</span><span class="sxs-lookup"><span data-stu-id="88364-138">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="88364-139">Como essa é uma chamada assíncrona, possivelmente assim que iniciar, você deseja chamar:</span><span class="sxs-lookup"><span data-stu-id="88364-139">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="88364-140">O StoreLoaded nesse caso é nosso manipulador para quando o WorldAnchorStore tiver concluído o carregamento:</span><span class="sxs-lookup"><span data-stu-id="88364-140">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="88364-141">Agora temos uma referência para o WorldAnchorStore, que usaremos para salvar e carregar âncoras mundiais específicas.</span><span class="sxs-lookup"><span data-stu-id="88364-141">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="88364-142">Salvando um WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="88364-142">Saving a WorldAnchor</span></span>

<span data-ttu-id="88364-143">Para economizar, precisamos simplesmente nomear o que estamos salvando e passá-lo no WorldAnchor que temos antes de se desejarmos salvar.</span><span class="sxs-lookup"><span data-stu-id="88364-143">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="88364-144">Observação: tentar salvar duas âncoras na mesma cadeia de caracteres falhará (Store. Save retornará false).</span><span class="sxs-lookup"><span data-stu-id="88364-144">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="88364-145">Exclua o salvamento anterior antes de salvar o novo:</span><span class="sxs-lookup"><span data-stu-id="88364-145">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="88364-146">Carregando um WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="88364-146">Loading a WorldAnchor</span></span>

<span data-ttu-id="88364-147">E para carregar:</span><span class="sxs-lookup"><span data-stu-id="88364-147">And to load:</span></span>

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

<span data-ttu-id="88364-148">Além disso, podemos usar Store. Delete () para remover uma âncora que salvamos e armazenamos anteriormente. Clear () para remover todos os dados salvos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="88364-148">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="88364-149">Enumerando âncoras existentes</span><span class="sxs-lookup"><span data-stu-id="88364-149">Enumerating Existing Anchors</span></span>

<span data-ttu-id="88364-150">Para descobrir âncoras armazenadas anteriormente, chame GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="88364-150">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="88364-151">Persistendo hologramas para vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="88364-151">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="88364-152">Você pode usar <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar uma âncora de nuvem durável a partir de um WorldAnchor local, que seu aplicativo pode localizar em vários dispositivos de HoloLens, Ios e Android, mesmo se esses dispositivos não estiverem presentes juntos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="88364-152">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="88364-153">Como as âncoras de nuvem são persistentes, vários dispositivos ao longo do tempo podem ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="88364-153">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="88364-154">Para começar a criar experiências compartilhadas no Unity, experimente os guias de início rápido dos separadores <a href="/azure/spatial-anchors/unity-overview" target="_blank">espaciais do Azure</a>de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="88364-154">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="88364-155">Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar âncoras no Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="88364-155">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
