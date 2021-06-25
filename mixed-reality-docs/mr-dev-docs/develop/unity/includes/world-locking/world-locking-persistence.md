---
ms.openlocfilehash: f937b705f10cc4a287600349283ecaed4ae44666
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112908095"
---
# <a name="world-locking-tools-recommended"></a>[World Locking Tools (recomendado)](#tab/wlt)

Por padrão, as Ferramentas de Bloqueio Mundial restaurarão o sistema de coordenadas do Unity em relação ao mundo físico entre as sessões. Isso significa que, para que um holograma apareça no mesmo lugar no mundo físico depois de sair e executar novamente o aplicativo, o holograma só precisa ter a mesma Pose novamente.

![Componente de contexto de bloqueio mundial no inspetor do Unity](../../images/world-locking-tools-img-02.png)

Se o aplicativo precisar de um  controle mais fino, o **Auto-Save** e o Carregamento Automático poderão ser desabilitados no inspetor e a persistência gerenciada de um script, conforme descrito na seção persistência da [documentação](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Uma API adicional chamada **XRAnchorStore** permite que as âncoras sejam persistentes entre as sessões. O XRAnchorStore é uma representação das âncoras salvas em um dispositivo. As âncoras podem ser persistentes de **ARAnchors** na cena do Unity, carregadas do armazenamento em novos **ARAnchors** ou excluídas do armazenamento.

> [!NOTE]
> Essas âncoras devem ser salvas e carregadas no mesmo dispositivo. O armazenamento de âncora entre dispositivos terá suporte por meio das Âncoras Espaciais do Azure em uma versão futura.

### <a name="namespaces"></a>Namespaces

Para **Unity 2020 e OpenXR:** 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

ou **Unity 2019/2020 + Plug-in do Windows XR:** 

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

### <a name="getting-an-anchor-store-reference"></a>Obter uma referência de armazenamento de âncoras 

Para carregar o XRAnchorStore com **Unity 2020 e OpenXR,** use o método de extensão no XRAnchorSubsystem, o subsistema de um ARAnchorManager:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Para carregar o XRAnchorStore com **o Unity 2019/2020** e o Plug-in do Windows XR, use o método de extensão no XRReferencePointSubsystem (Unity 2019) ou XRAnchorSubsystem (Unity 2020), o subsistema de um ARReferencePointManager/ARAnchorManager:

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a>Carregando um armazenamento de âncoras

Para carregar um armazenamento de âncoras **no Unity 2020 e no OpenXR,** acesse-o no subsistema de um ARAnchorManager da seguinte forma:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

ou com **o Unity 2019/2020 e o Plug-in do Windows XR:**

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

Para ver um exemplo completo de âncoras persistentes/não persistentes, confira o script GameObject e AnchorsSample.cs de Exemplo de Âncoras -> AnchorsSample.cs na Cena de exemplo do plug-in OpenXR de Realidade [Misturada:](../../xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2)

![Captura de tela do painel de hierarquia aberto no Editor do Unity com o exemplo de âncoras realçada](../../images/openxr-features-img-04.png)

![Captura de tela do painel inspetor aberto no Editor do Unity com o script de exemplo de âncoras realçada](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

O **WorldAnchorStore** é a chave para criar experiências holográficas em que os hologramas permanecem em posições específicas do mundo real entre instâncias do aplicativo. Os usuários podem fixar hologramas individuais sempre que quiserem e encontrá-los posteriormente no mesmo local em vários usos de seu aplicativo.

**Namespace:** *UnityEngine.XR.WSA.Persistence*<br>
**Classe:** *WorldAnchorStore*

O WorldAnchorStore permitirá que você persista o local do WorldAnchor entre as sessões. Para realmente persistir hologramas entre sessões, você precisará controlar separadamente seus GameObjects que usam uma âncora mundial específica. Geralmente, faz sentido criar uma raiz GameObject com uma âncora mundial e ter hologramas filhos ancorados por ela com um deslocamento de posição local.

Para carregar hologramas de sessões anteriores:

1. Obter o WorldAnchorStore
2. Carregar dados do aplicativo relacionados à âncora mundial, que fornece a ID da âncora do mundo
3. Carregar uma âncora mundial de sua ID

Para salvar hologramas para sessões futuras:

1. Obter o WorldAnchorStore
2. Salvar uma âncora mundial especificando uma ID
3. Salvar dados do aplicativo relacionados à âncora do mundo juntamente com uma ID

### <a name="getting-the-worldanchorstore"></a>Obter o WorldAnchorStore

Você deve manter uma referência ao WorldAnchorStore para saber quando ele está pronto para executar uma operação. Como essa é uma chamada assíncrona, potencialmente assim que iniciar, você deseja chamar:

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded nesse caso é nosso manipulador para quando o WorldAnchorStore tiver concluído o carregamento:

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

Agora temos uma referência ao WorldAnchorStore, que vamos usar para salvar e carregar Âncoras Do Mundo específicas.

### <a name="saving-a-worldanchor"></a>Salvando um WorldAnchor

Para salvar, basta nomear o que estamos salvando e passá-lo no WorldAnchor que temos antes quando queremos salvar. Observação: a tentativa de salvar duas âncoras na mesma cadeia de caracteres falhará (armazenar. Salvar retornará false). Exclua o salvar anteriormente antes de salvar o novo:

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

Além disso, podemos usar o store. Delete() para remover uma âncora que salvamos anteriormente e armazenamos. Clear() para remover todos os dados salvos anteriormente.

### <a name="enumerating-existing-anchors"></a>Enumerando âncoras existentes

Para descobrir âncoras armazenadas anteriormente, chame GetAllIds.

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Persistir hologramas para vários dispositivos

Você pode usar as Âncoras Espaciais do <a href="/azure/spatial-anchors/overview" target="_blank">Azure</a> para criar uma âncora de nuvem durável de um WorldAnchor local, que seu aplicativo pode localizar em vários dispositivos HoloLens, iOS e Android, mesmo que esses dispositivos não estão presentes juntos ao mesmo tempo.  Como as âncoras de nuvem são persistentes, vários dispositivos ao longo do tempo podem ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.

Para começar a criar experiências compartilhadas no Unity, experimente os <a href="/azure/spatial-anchors/unity-overview" target="_blank">inícios rápidos</a>do Unity das Âncoras Espaciais do Azure de 5 minutos.

Quando estiver em execução com as Âncoras Espaciais do Azure, você poderá criar e <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">localizar âncoras no Unity.</a>