---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603366"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

> [!NOTE]
> Essas âncoras devem ser salvas e carregadas no mesmo dispositivo. O armazenamento de âncora entre dispositivos terá suporte por meio de âncoras espaciais do Azure em uma versão futura.

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

Para carregar o XRAnchorStore, o plug-in fornece um método de extensão no XRAnchorSubsystem, o subsistema de um ARAnchorManager:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Para usar esse método de extensão, acesse-o de um subsistema de ARAnchorManager da seguinte maneira:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

Para ver um exemplo completo de persistência/descontinuação de âncoras, confira o exemplo âncoras-> ancoras Games e o script AnchorsSample.cs na [cena de exemplo do plugin OpenXR de realidade misturada](../openxr-getting-started.md#hololens-2-samples):

![Captura de tela do painel hierarquia aberta no editor do Unity com o exemplo âncoras realçado](../images/openxr-features-img-04.png)

![Captura de tela do painel Inspetor aberto no editor do Unity com o script de exemplo âncoras realçado](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[Plug-in do Unity 2019/2020 + Windows XR](#tab/winxr)

> [!NOTE]
> Essas âncoras devem ser salvas e carregadas no mesmo dispositivo. O armazenamento de âncora entre dispositivos terá suporte por meio de âncoras espaciais do Azure em uma versão futura.

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

Para carregar o XRAnchorStore, o plug-in fornece um método de extensão no XRReferencePointSubsystem (Unity 2019) ou XRAnchorSubsystem (Unity 2020), o subsistema de um ARReferencePointManager/ARAnchorManager:

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

Para usar esse método de extensão, acesse-o do subsistema de um ARAnchorManager da seguinte maneira para o Unity 2019:

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

ou para o Unity 2020:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

**Namespace:** *UnityEngine. XR. WSA. Persistence*<br>
**Classe:** *WorldAnchorStore*

O WorldAnchorStore permitirá que você persista o local de WorldAnchor entre as sessões. Para realmente manter os hologramas entre as sessões, você precisará controlar separadamente seus GameObjects que usam uma âncora mundial específica. Geralmente faz sentido criar uma raiz gameobject com uma âncora mundial e ter hologramas filhos ancorados por ela com um deslocamento de posição local.

Para carregar os hologramas de sessões anteriores:

1. Obter o WorldAnchorStore
2. Carregar dados de aplicativo relacionados à âncora mundial, que fornece a ID da âncora mundial
3. Carregar uma âncora mundial de sua ID

Para salvar os hologramas para sessões futuras:

1. Obter o WorldAnchorStore
2. Salvar uma âncora mundial especificando uma ID
3. Salvar dados de aplicativo relacionados à âncora mundial, juntamente com uma ID

### <a name="getting-the-worldanchorstore"></a>Obtendo o WorldAnchorStore

Você desejará manter uma referência ao WorldAnchorStore para saber quando ele está pronto para executar uma operação. Como essa é uma chamada assíncrona, possivelmente assim que iniciar, você deseja chamar:

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

O StoreLoaded nesse caso é nosso manipulador para quando o WorldAnchorStore tiver concluído o carregamento:

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

Agora temos uma referência para o WorldAnchorStore, que usaremos para salvar e carregar âncoras mundiais específicas.

### <a name="saving-a-worldanchor"></a>Salvando um WorldAnchor

Para economizar, precisamos simplesmente nomear o que estamos salvando e passá-lo no WorldAnchor que temos antes de se desejarmos salvar. Observação: tentar salvar duas âncoras na mesma cadeia de caracteres falhará (Store. Save retornará false). Exclua o salvamento anterior antes de salvar o novo:

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

### <a name="loading-a-worldanchor"></a>Carregando um WorldAnchor

E para carregar:

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

Além disso, podemos usar Store. Delete () para remover uma âncora que salvamos e armazenamos anteriormente. Clear () para remover todos os dados salvos anteriormente.

### <a name="enumerating-existing-anchors"></a>Enumerando âncoras existentes

Para descobrir âncoras armazenadas anteriormente, chame GetAllIds.

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a>Criando uma experiência de escala mundial

**Namespace:** *UnityEngine. XR. WSA*<br>
**Tipo:** *WorldAnchor*

Para experiências reais em grande **escala** sobre o HoloLens que permitem aos usuários percorrer mais de 5 metros, você precisará de novas técnicas além das usadas para experiências em escala de sala. Uma técnica importante que você usará é criar uma [âncora espacial](../../../design/coordinate-systems.md#spatial-anchors) para bloquear um cluster de hologramas precisamente no mundo físico, não importa o quanto o usuário está em roaming e, em seguida, [encontrar esses hologramas novamente em sessões posteriores](../../../design/coordinate-systems.md#spatial-anchor-persistence).

No Unity, você cria uma âncora espacial adicionando o componente **WorldAnchor** Unity a um gameobject.

### <a name="adding-a-world-anchor"></a>Adicionando uma âncora mundial

Para adicionar uma âncora mundial, ligue para `AddComponent<WorldAnchor>()` o objeto Game com a transformação que você deseja ancorar no mundo real.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

É isso! Este objeto de jogo agora será ancorado ao seu local atual no mundo físico – você pode ver que suas coordenadas do Unity World se ajustam um pouco ao longo do tempo para garantir que o alinhamento físico. Consulte [carregando uma âncora mundial](#loading-a-worldanchor) para localizar esse local ancorado novamente em uma sessão de aplicativo futura.

### <a name="removing-a-world-anchor"></a>Removendo uma âncora mundial

Se você não quiser mais que o gameobject seja bloqueado em um local físico do mundo e não pretenda movê-lo para esse quadro, você pode simplesmente chamar Destroy no componente de âncora mundial.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Se você quiser mover o gameobject para este quadro, precisará chamar DestroyImmediate em vez disso.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Movendo um jogo de jogos ancorado

O gameobject não pode ser movido enquanto uma âncora mundial está nele. Se você precisar mover o gameobject para este quadro, precisará:

1. DestroyImmediate o componente de âncora mundial
2. Mover o gameobject
3. Adicione um novo componente de âncora mundial ao gameobject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Manipulando alterações de Locatability

Um WorldAnchor pode não ser localizável no mundo físico em um ponto no tempo. Se isso ocorrer, o Unity não atualizará a transformação do objeto ancorado. Isso também pode ser alterado enquanto um aplicativo está em execução. A falha ao manipular a alteração em locatability fará com que o objeto não apareça no local físico correto do mundo.

Para ser notificado sobre as alterações de locatability:

1. Assinar o evento onrastreiechanged
2. Manipular o evento

O evento **Oncontrolchanged** será chamado sempre que a âncora espacial subjacente for alterada entre o estado de ser localizável versus não ser localizável.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Em seguida, manipule o evento:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Às vezes, as âncoras estão localizadas imediatamente. Nesse caso, essa propriedade islocalizada da âncora será definida como true quando addComponent <WorldAnchor> () retornar. Como resultado, o evento onrastreiochanged não será disparado. Um padrão limpo seria chamar o manipulador oncontrolchanged com o estado inicial IsDeleted depois de anexar uma âncora.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a>Persistendo hologramas para vários dispositivos

Você pode usar <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar uma âncora de nuvem durável a partir de um WorldAnchor local, que seu aplicativo pode localizar em vários dispositivos de HoloLens, Ios e Android, mesmo se esses dispositivos não estiverem presentes juntos ao mesmo tempo.  Como as âncoras de nuvem são persistentes, vários dispositivos ao longo do tempo podem ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.

Para começar a criar experiências compartilhadas no Unity, experimente os guias de início rápido dos separadores <a href="/azure/spatial-anchors/unity-overview" target="_blank">espaciais do Azure</a>de 5 minutos.

Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar âncoras no Unity</a>.
