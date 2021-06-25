---
ms.openlocfilehash: f937b705f10cc4a287600349283ecaed4ae44666
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112908095"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="f301b-101">World Locking Tools (recomendado)</span><span class="sxs-lookup"><span data-stu-id="f301b-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="f301b-102">Por padrão, as Ferramentas de Bloqueio Mundial restaurarão o sistema de coordenadas do Unity em relação ao mundo físico entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="f301b-102">By default, World Locking Tools will restore Unity's coordinate system relative to the physical world across sessions.</span></span> <span data-ttu-id="f301b-103">Isso significa que, para que um holograma apareça no mesmo lugar no mundo físico depois de sair e executar novamente o aplicativo, o holograma só precisa ter a mesma Pose novamente.</span><span class="sxs-lookup"><span data-stu-id="f301b-103">This means that to have a hologram appear the same place in the physical world after quitting and re-running the application, the hologram only needs to have the same Pose again.</span></span>

![Componente de contexto de bloqueio mundial no inspetor do Unity](../../images/world-locking-tools-img-02.png)

<span data-ttu-id="f301b-105">Se o aplicativo precisar de um  controle mais fino, o **Auto-Save** e o Carregamento Automático poderão ser desabilitados no inspetor e a persistência gerenciada de um script, conforme descrito na seção persistência da [documentação](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span><span class="sxs-lookup"><span data-stu-id="f301b-105">If the application needs finer control, **Auto-Save** and **Auto-Load** may be disabled in the inspector, and persistence managed from a script as described in the [persistence section of the documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="f301b-106">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="f301b-106">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="f301b-107">Uma API adicional chamada **XRAnchorStore** permite que as âncoras sejam persistentes entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="f301b-107">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="f301b-108">O XRAnchorStore é uma representação das âncoras salvas em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f301b-108">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="f301b-109">As âncoras podem ser persistentes de **ARAnchors** na cena do Unity, carregadas do armazenamento em novos **ARAnchors** ou excluídas do armazenamento.</span><span class="sxs-lookup"><span data-stu-id="f301b-109">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="f301b-110">Essas âncoras devem ser salvas e carregadas no mesmo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f301b-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="f301b-111">O armazenamento de âncora entre dispositivos terá suporte por meio das Âncoras Espaciais do Azure em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="f301b-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

### <a name="namespaces"></a><span data-ttu-id="f301b-112">Namespaces</span><span class="sxs-lookup"><span data-stu-id="f301b-112">Namespaces</span></span>

<span data-ttu-id="f301b-113">Para **Unity 2020 e OpenXR:**</span><span class="sxs-lookup"><span data-stu-id="f301b-113">For **Unity 2020 and OpenXR**:</span></span> 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

<span data-ttu-id="f301b-114">ou **Unity 2019/2020 + Plug-in do Windows XR:**</span><span class="sxs-lookup"><span data-stu-id="f301b-114">or **Unity 2019/2020 + Windows XR Plugin**:</span></span> 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a><span data-ttu-id="f301b-115">Métodos públicos</span><span class="sxs-lookup"><span data-stu-id="f301b-115">Public methods</span></span>

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

### <a name="getting-an-anchor-store-reference"></a><span data-ttu-id="f301b-116">Obter uma referência de armazenamento de âncoras</span><span class="sxs-lookup"><span data-stu-id="f301b-116">Getting an anchor store reference</span></span> 

<span data-ttu-id="f301b-117">Para carregar o XRAnchorStore com **Unity 2020 e OpenXR,** use o método de extensão no XRAnchorSubsystem, o subsistema de um ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="f301b-117">To load the XRAnchorStore with **Unity 2020 and OpenXR**, use extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="f301b-118">Para carregar o XRAnchorStore com **o Unity 2019/2020** e o Plug-in do Windows XR, use o método de extensão no XRReferencePointSubsystem (Unity 2019) ou XRAnchorSubsystem (Unity 2020), o subsistema de um ARReferencePointManager/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="f301b-118">To load the XRAnchorStore with **Unity 2019/2020 and the Windows XR Plugin**, use the extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a><span data-ttu-id="f301b-119">Carregando um armazenamento de âncoras</span><span class="sxs-lookup"><span data-stu-id="f301b-119">Loading an anchor store</span></span>

<span data-ttu-id="f301b-120">Para carregar um armazenamento de âncoras **no Unity 2020 e no OpenXR,** acesse-o no subsistema de um ARAnchorManager da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="f301b-120">To load an anchor store in **Unity 2020 and OpenXR**, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="f301b-121">ou com **o Unity 2019/2020 e o Plug-in do Windows XR:**</span><span class="sxs-lookup"><span data-stu-id="f301b-121">or with **Unity 2019/2020 and the Windows XR Plugin**:</span></span>

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="f301b-122">Para ver um exemplo completo de âncoras persistentes/não persistentes, confira o script GameObject e AnchorsSample.cs de Exemplo de Âncoras -> AnchorsSample.cs na Cena de exemplo do plug-in OpenXR de Realidade [Misturada:](../../xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2)</span><span class="sxs-lookup"><span data-stu-id="f301b-122">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../../xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2):</span></span>

![Captura de tela do painel de hierarquia aberto no Editor do Unity com o exemplo de âncoras realçada](../../images/openxr-features-img-04.png)

![Captura de tela do painel inspetor aberto no Editor do Unity com o script de exemplo de âncoras realçada](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[<span data-ttu-id="f301b-125">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="f301b-125">WorldAnchor</span></span>](#tab/worldanchor)

<span data-ttu-id="f301b-126">O **WorldAnchorStore** é a chave para criar experiências holográficas em que os hologramas permanecem em posições específicas do mundo real entre instâncias do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f301b-126">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="f301b-127">Os usuários podem fixar hologramas individuais sempre que quiserem e encontrá-los posteriormente no mesmo local em vários usos de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f301b-127">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="f301b-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="f301b-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="f301b-129">**Classe:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="f301b-129">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="f301b-130">O WorldAnchorStore permitirá que você persista o local do WorldAnchor entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="f301b-130">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="f301b-131">Para realmente persistir hologramas entre sessões, você precisará controlar separadamente seus GameObjects que usam uma âncora mundial específica.</span><span class="sxs-lookup"><span data-stu-id="f301b-131">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="f301b-132">Geralmente, faz sentido criar uma raiz GameObject com uma âncora mundial e ter hologramas filhos ancorados por ela com um deslocamento de posição local.</span><span class="sxs-lookup"><span data-stu-id="f301b-132">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="f301b-133">Para carregar hologramas de sessões anteriores:</span><span class="sxs-lookup"><span data-stu-id="f301b-133">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="f301b-134">Obter o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="f301b-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="f301b-135">Carregar dados do aplicativo relacionados à âncora mundial, que fornece a ID da âncora do mundo</span><span class="sxs-lookup"><span data-stu-id="f301b-135">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="f301b-136">Carregar uma âncora mundial de sua ID</span><span class="sxs-lookup"><span data-stu-id="f301b-136">Load a world anchor from its ID</span></span>

<span data-ttu-id="f301b-137">Para salvar hologramas para sessões futuras:</span><span class="sxs-lookup"><span data-stu-id="f301b-137">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="f301b-138">Obter o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="f301b-138">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="f301b-139">Salvar uma âncora mundial especificando uma ID</span><span class="sxs-lookup"><span data-stu-id="f301b-139">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="f301b-140">Salvar dados do aplicativo relacionados à âncora do mundo juntamente com uma ID</span><span class="sxs-lookup"><span data-stu-id="f301b-140">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="f301b-141">Obter o WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="f301b-141">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="f301b-142">Você deve manter uma referência ao WorldAnchorStore para saber quando ele está pronto para executar uma operação.</span><span class="sxs-lookup"><span data-stu-id="f301b-142">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="f301b-143">Como essa é uma chamada assíncrona, potencialmente assim que iniciar, você deseja chamar:</span><span class="sxs-lookup"><span data-stu-id="f301b-143">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="f301b-144">StoreLoaded nesse caso é nosso manipulador para quando o WorldAnchorStore tiver concluído o carregamento:</span><span class="sxs-lookup"><span data-stu-id="f301b-144">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="f301b-145">Agora temos uma referência ao WorldAnchorStore, que vamos usar para salvar e carregar Âncoras Do Mundo específicas.</span><span class="sxs-lookup"><span data-stu-id="f301b-145">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="f301b-146">Salvando um WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="f301b-146">Saving a WorldAnchor</span></span>

<span data-ttu-id="f301b-147">Para salvar, basta nomear o que estamos salvando e passá-lo no WorldAnchor que temos antes quando queremos salvar.</span><span class="sxs-lookup"><span data-stu-id="f301b-147">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="f301b-148">Observação: a tentativa de salvar duas âncoras na mesma cadeia de caracteres falhará (armazenar. Salvar retornará false).</span><span class="sxs-lookup"><span data-stu-id="f301b-148">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="f301b-149">Exclua o salvar anteriormente antes de salvar o novo:</span><span class="sxs-lookup"><span data-stu-id="f301b-149">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="f301b-150">Carregando um WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="f301b-150">Loading a WorldAnchor</span></span>

<span data-ttu-id="f301b-151">E para carregar:</span><span class="sxs-lookup"><span data-stu-id="f301b-151">And to load:</span></span>

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

<span data-ttu-id="f301b-152">Além disso, podemos usar o store. Delete() para remover uma âncora que salvamos anteriormente e armazenamos. Clear() para remover todos os dados salvos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f301b-152">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="f301b-153">Enumerando âncoras existentes</span><span class="sxs-lookup"><span data-stu-id="f301b-153">Enumerating Existing Anchors</span></span>

<span data-ttu-id="f301b-154">Para descobrir âncoras armazenadas anteriormente, chame GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="f301b-154">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="f301b-155">Persistir hologramas para vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="f301b-155">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="f301b-156">Você pode usar as Âncoras Espaciais do <a href="/azure/spatial-anchors/overview" target="_blank">Azure</a> para criar uma âncora de nuvem durável de um WorldAnchor local, que seu aplicativo pode localizar em vários dispositivos HoloLens, iOS e Android, mesmo que esses dispositivos não estão presentes juntos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="f301b-156">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="f301b-157">Como as âncoras de nuvem são persistentes, vários dispositivos ao longo do tempo podem ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="f301b-157">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="f301b-158">Para começar a criar experiências compartilhadas no Unity, experimente os <a href="/azure/spatial-anchors/unity-overview" target="_blank">inícios rápidos</a>do Unity das Âncoras Espaciais do Azure de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="f301b-158">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="f301b-159">Quando estiver em execução com as Âncoras Espaciais do Azure, você poderá criar e <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">localizar âncoras no Unity.</a></span><span class="sxs-lookup"><span data-stu-id="f301b-159">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>