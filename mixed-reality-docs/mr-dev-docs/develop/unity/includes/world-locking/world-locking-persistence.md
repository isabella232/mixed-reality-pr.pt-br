---
ms.openlocfilehash: 25e42ba872764a98d4cb966b5a4922cc1dea0dc9
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528759"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="9427a-101">Ferramentas de bloqueio Mundial (recomendado)</span><span class="sxs-lookup"><span data-stu-id="9427a-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="9427a-102">Por padrão, as ferramentas de bloqueio mundial irão restaurar o sistema de coordenadas do Unity em relação ao mundo físico entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="9427a-102">By default, World Locking Tools will restore Unity's coordinate system relative to the physical world across sessions.</span></span> <span data-ttu-id="9427a-103">Isso significa que, para que um holograma pareça ser o mesmo local no mundo físico após sair e executar novamente o aplicativo, o holograma só precisa ter a mesma pose novamente.</span><span class="sxs-lookup"><span data-stu-id="9427a-103">This means that to have a hologram appear the same place in the physical world after quitting and re-running the application, the hologram only needs to have the same Pose again.</span></span>

![Componente de contexto de bloqueio mundial no Inspetor do Unity](../../images/world-locking-tools-img-02.png)

<span data-ttu-id="9427a-105">Se o aplicativo precisar de controle mais preciso, o **salvamento automático** e o **carregamento automático** poderão ser desabilitados no Inspetor e a persistência gerenciada de um script, conforme descrito na [seção persistência da documentação](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span><span class="sxs-lookup"><span data-stu-id="9427a-105">If the application needs finer control, **Auto-Save** and **Auto-Load** may be disabled in the inspector, and persistence managed from a script as described in the [persistence section of the documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="9427a-106">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="9427a-106">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="9427a-107">Uma API adicional chamada **XRAnchorStore** permite que as âncoras sejam persistidas entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="9427a-107">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="9427a-108">O XRAnchorStore é uma representação das âncoras salvas em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9427a-108">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="9427a-109">As âncoras podem persistir de **ARAnchors** na cena do Unity, carregadas do armazenamento para o New **ARAnchors** ou excluídas do armazenamento.</span><span class="sxs-lookup"><span data-stu-id="9427a-109">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="9427a-110">Essas âncoras devem ser salvas e carregadas no mesmo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9427a-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="9427a-111">O armazenamento de âncora entre dispositivos terá suporte por meio de âncoras espaciais do Azure em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="9427a-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

### <a name="namespaces"></a><span data-ttu-id="9427a-112">Namespaces</span><span class="sxs-lookup"><span data-stu-id="9427a-112">Namespaces</span></span>

<span data-ttu-id="9427a-113">Para o **Unity 2020 e o OpenXR**:</span><span class="sxs-lookup"><span data-stu-id="9427a-113">For **Unity 2020 and OpenXR**:</span></span> 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

<span data-ttu-id="9427a-114">ou o **plug-in do Unity 2019/2020 + Windows XR**:</span><span class="sxs-lookup"><span data-stu-id="9427a-114">or **Unity 2019/2020 + Windows XR Plugin**:</span></span> 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a><span data-ttu-id="9427a-115">Métodos públicos</span><span class="sxs-lookup"><span data-stu-id="9427a-115">Public methods</span></span>

```cs 
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

### <a name="getting-an-anchor-store-reference"></a><span data-ttu-id="9427a-116">Obtendo uma referência de repositório de âncora</span><span class="sxs-lookup"><span data-stu-id="9427a-116">Getting an anchor store reference</span></span> 

<span data-ttu-id="9427a-117">Para carregar o XRAnchorStore com **Unity 2020 e OpenXR**, use o método de extensão no XRAnchorSubsystem, o subsistema de um ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="9427a-117">To load the XRAnchorStore with **Unity 2020 and OpenXR**, use extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="9427a-118">Para carregar o XRAnchorStore com o **unity 2019/2020 e o plug-in do Windows XR**, use o método de extensão no XRReferencePointSubsystem (Unity 2019) ou XRAnchorSubsystem (Unity 2020), o subsistema de um ARReferencePointManager/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="9427a-118">To load the XRAnchorStore with **Unity 2019/2020 and the Windows XR Plugin**, use the extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a><span data-ttu-id="9427a-119">Carregando um repositório de âncoras</span><span class="sxs-lookup"><span data-stu-id="9427a-119">Loading an anchor store</span></span>

<span data-ttu-id="9427a-120">Para carregar um repositório de âncora no **Unity 2020 e no OpenXR**, acesse-o do subsistema de um ARAnchorManager da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9427a-120">To load an anchor store in **Unity 2020 and OpenXR**, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="9427a-121">ou com **o Unity 2019/2020 e o plug-in do Windows XR**:</span><span class="sxs-lookup"><span data-stu-id="9427a-121">or with **Unity 2019/2020 and the Windows XR Plugin**:</span></span>

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="9427a-122">Para ver um exemplo completo de persistência/descontinuação de âncoras, confira o script ancoragem-> ancoragems de exemplo Gamesobject e AnchorsSample. cs na [cena de exemplo do plugin OpenXR da realidade misturada](../../openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="9427a-122">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../../openxr-getting-started.md#hololens-2-samples):</span></span>

![Captura de tela do painel hierarquia aberta no editor do Unity com o exemplo âncoras realçado](../../images/openxr-features-img-04.png)

![Captura de tela do painel Inspetor aberto no editor do Unity com o script de exemplo âncoras realçado](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[<span data-ttu-id="9427a-125">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="9427a-125">WorldAnchor</span></span>](#tab/worldanchor)

<span data-ttu-id="9427a-126">O **WorldAnchorStore** é a chave para criar experiências de Holographic em que os hologramas permanecem em posições reais específicas entre instâncias do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9427a-126">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="9427a-127">Os usuários podem então fixar os hologramas individuais onde quiserem e encontrá-los mais tarde no mesmo ponto em vários usos de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9427a-127">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="9427a-128">**Namespace:** *UnityEngine. XR. WSA. Persistence*</span><span class="sxs-lookup"><span data-stu-id="9427a-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="9427a-129">**Classe:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="9427a-129">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="9427a-130">O WorldAnchorStore permitirá que você persista o local de WorldAnchor entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="9427a-130">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="9427a-131">Para realmente manter os hologramas entre as sessões, você precisará controlar separadamente seus GameObjects que usam uma âncora mundial específica.</span><span class="sxs-lookup"><span data-stu-id="9427a-131">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="9427a-132">Geralmente faz sentido criar uma raiz gameobject com uma âncora mundial e ter hologramas filhos ancorados por ela com um deslocamento de posição local.</span><span class="sxs-lookup"><span data-stu-id="9427a-132">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="9427a-133">Para carregar os hologramas de sessões anteriores:</span><span class="sxs-lookup"><span data-stu-id="9427a-133">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="9427a-134">Obter o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="9427a-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="9427a-135">Carregar dados de aplicativo relacionados à âncora mundial, que fornece a ID da âncora mundial</span><span class="sxs-lookup"><span data-stu-id="9427a-135">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="9427a-136">Carregar uma âncora mundial de sua ID</span><span class="sxs-lookup"><span data-stu-id="9427a-136">Load a world anchor from its ID</span></span>

<span data-ttu-id="9427a-137">Para salvar os hologramas para sessões futuras:</span><span class="sxs-lookup"><span data-stu-id="9427a-137">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="9427a-138">Obter o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="9427a-138">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="9427a-139">Salvar uma âncora mundial especificando uma ID</span><span class="sxs-lookup"><span data-stu-id="9427a-139">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="9427a-140">Salvar dados de aplicativo relacionados à âncora mundial, juntamente com uma ID</span><span class="sxs-lookup"><span data-stu-id="9427a-140">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="9427a-141">Obtendo o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="9427a-141">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="9427a-142">Você desejará manter uma referência ao WorldAnchorStore para saber quando ele está pronto para executar uma operação.</span><span class="sxs-lookup"><span data-stu-id="9427a-142">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="9427a-143">Como essa é uma chamada assíncrona, possivelmente assim que iniciar, você deseja chamar:</span><span class="sxs-lookup"><span data-stu-id="9427a-143">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="9427a-144">O StoreLoaded nesse caso é nosso manipulador para quando o WorldAnchorStore tiver concluído o carregamento:</span><span class="sxs-lookup"><span data-stu-id="9427a-144">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="9427a-145">Agora temos uma referência para o WorldAnchorStore, que usaremos para salvar e carregar âncoras mundiais específicas.</span><span class="sxs-lookup"><span data-stu-id="9427a-145">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="9427a-146">Salvando um WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="9427a-146">Saving a WorldAnchor</span></span>

<span data-ttu-id="9427a-147">Para economizar, precisamos simplesmente nomear o que estamos salvando e passá-lo no WorldAnchor que temos antes de se desejarmos salvar.</span><span class="sxs-lookup"><span data-stu-id="9427a-147">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="9427a-148">Observação: tentar salvar duas âncoras na mesma cadeia de caracteres falhará (Store. Save retornará false).</span><span class="sxs-lookup"><span data-stu-id="9427a-148">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="9427a-149">Exclua o salvamento anterior antes de salvar o novo:</span><span class="sxs-lookup"><span data-stu-id="9427a-149">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="9427a-150">Carregando um WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="9427a-150">Loading a WorldAnchor</span></span>

<span data-ttu-id="9427a-151">E para carregar:</span><span class="sxs-lookup"><span data-stu-id="9427a-151">And to load:</span></span>

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

<span data-ttu-id="9427a-152">Além disso, podemos usar Store. Delete () para remover uma âncora que salvamos e armazenamos anteriormente. Clear () para remover todos os dados salvos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="9427a-152">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="9427a-153">Enumerando âncoras existentes</span><span class="sxs-lookup"><span data-stu-id="9427a-153">Enumerating Existing Anchors</span></span>

<span data-ttu-id="9427a-154">Para descobrir âncoras armazenadas anteriormente, chame GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="9427a-154">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="9427a-155">Persistendo hologramas para vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="9427a-155">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="9427a-156">Você pode usar <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar uma âncora de nuvem durável a partir de um WorldAnchor local, que seu aplicativo pode localizar em vários dispositivos de HoloLens, Ios e Android, mesmo se esses dispositivos não estiverem presentes juntos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="9427a-156">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="9427a-157">Como as âncoras de nuvem são persistentes, vários dispositivos ao longo do tempo podem ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="9427a-157">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="9427a-158">Para começar a criar experiências compartilhadas no Unity, experimente os guias de início rápido dos separadores <a href="/azure/spatial-anchors/unity-overview" target="_blank">espaciais do Azure</a>de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="9427a-158">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="9427a-159">Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar âncoras no Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="9427a-159">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
