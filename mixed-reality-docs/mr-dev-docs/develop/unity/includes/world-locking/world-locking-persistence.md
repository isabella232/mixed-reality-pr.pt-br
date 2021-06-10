---
ms.openlocfilehash: 96da41f28533c227fb106d8842907747f34098ec
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110349743"
---
# <a name="world-locking-tools-recommended"></a>[Ferramentas de bloqueio Mundial (recomendado)](#tab/wlt)

Por padrão, as ferramentas de bloqueio mundial irão restaurar o sistema de coordenadas do Unity em relação ao mundo físico entre as sessões. Isso significa que, para que um holograma pareça ser o mesmo local no mundo físico após sair e executar novamente o aplicativo, o holograma só precisa ter a mesma pose novamente.

![Componente de contexto de bloqueio mundial no Inspetor do Unity](../../images/world-locking-tools-img-02.png)

Se o aplicativo precisar de controle mais preciso, o **salvamento automático** e o **carregamento automático** poderão ser desabilitados no Inspetor e a persistência gerenciada de um script, conforme descrito na [seção persistência da documentação](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Uma API adicional chamada **XRAnchorStore** permite que as âncoras sejam persistidas entre as sessões. O XRAnchorStore é uma representação das âncoras salvas em um dispositivo. As âncoras podem persistir de **ARAnchors** na cena do Unity, carregadas do armazenamento para o New **ARAnchors** ou excluídas do armazenamento.

> [!NOTE]
> Essas âncoras devem ser salvas e carregadas no mesmo dispositivo. O armazenamento de âncora entre dispositivos terá suporte por meio de âncoras espaciais do Azure em uma versão futura.

### <a name="namespaces"></a>Namespaces

Para o **Unity 2020 e o OpenXR**: 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

ou o **plug-in do Unity 2019/2020 + Windows XR**: 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a>Métodos públicos

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

### <a name="getting-an-anchor-store-reference"></a>Obtendo uma referência de repositório de âncora 

Para carregar o XRAnchorStore com **Unity 2020 e OpenXR**, use o método de extensão no XRAnchorSubsystem, o subsistema de um ARAnchorManager:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Para carregar o XRAnchorStore com o **unity 2019/2020 e o plug-in do Windows XR**, use o método de extensão no XRReferencePointSubsystem (Unity 2019) ou XRAnchorSubsystem (Unity 2020), o subsistema de um ARReferencePointManager/ARAnchorManager:

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a>Carregando um repositório de âncoras

Para carregar um repositório de âncora no **Unity 2020 e no OpenXR**, acesse-o do subsistema de um ARAnchorManager da seguinte maneira:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

ou com **o Unity 2019/2020 e o plug-in do Windows XR**:

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

Para ver um exemplo completo de persistência/descontinuação de âncoras, confira o script ancoragem-> ancoragems de exemplo Gamesobject e AnchorsSample. cs na [cena de exemplo do plugin OpenXR da realidade misturada](../../openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2):

![Captura de tela do painel hierarquia aberta no editor do Unity com o exemplo âncoras realçado](../../images/openxr-features-img-04.png)

![Captura de tela do painel Inspetor aberto no editor do Unity com o script de exemplo âncoras realçado](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

O **WorldAnchorStore** é a chave para criar experiências de Holographic em que os hologramas permanecem em posições reais específicas entre instâncias do aplicativo. Os usuários podem então fixar os hologramas individuais onde quiserem e encontrá-los mais tarde no mesmo ponto em vários usos de seu aplicativo.

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

## <a name="persisting-holograms-for-multiple-devices"></a>Persistendo hologramas para vários dispositivos

Você pode usar <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar uma âncora de nuvem durável a partir de um WorldAnchor local, que seu aplicativo pode localizar em vários dispositivos de HoloLens, Ios e Android, mesmo se esses dispositivos não estiverem presentes juntos ao mesmo tempo.  Como as âncoras de nuvem são persistentes, vários dispositivos ao longo do tempo podem ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.

Para começar a criar experiências compartilhadas no Unity, experimente os guias de início rápido dos separadores <a href="/azure/spatial-anchors/unity-overview" target="_blank">espaciais do Azure</a>de 5 minutos.

Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar âncoras no Unity</a>.
