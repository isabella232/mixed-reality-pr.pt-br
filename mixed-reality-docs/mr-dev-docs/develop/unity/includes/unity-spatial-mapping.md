---
ms.openlocfilehash: 271116683c94e051f61b78c0db3974ee843afdbd
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905709"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="spatial-awareness-system"></a>Sistema de conscientização espacial

No MRTK, confira o Guia de início [do reconhecimento](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) espacial para obter informações sobre como configurar vários observadores de malha espacial.

Para obter informações sobre observadores no dispositivo, confira o [guia Configurando](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/configuring-spatial-awareness-mesh-observer) observadores de malha para dispositivos.

Para obter informações sobre observadores de compreensão de cena, confira o Guia do observador [noções básicas de](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) cena.

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)

## <a name="armeshmanager"></a>ARMeshManager

O ARFoundation do Unity fornece um componente ARMeshManager para visualização interna de malhas espaciais. Confira [a documentação do Unity para](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/mesh-manager.html) obter mais informações sobre o uso.

## <a name="xrmeshsubsystem"></a>XRMeshSubsystem

Se você preferir trabalhar diretamente com o [XRMeshSubsystem](https://docs.unity3d.com/ScriptReference/XR.XRMeshSubsystem.html) do Unity, confira a documentação do [Unity](https://docs.unity3d.com/Manual/xrsdk-meshing.html) para obter mais informações sobre o uso.

## <a name="windows-xr-plugin"></a>Windows Plug-in XR

Windows O Plug-in XR fornece alguns métodos de extensão adicionais para configurar o XRMeshSubsystem, como definir uma esfera delimitador ou acessar a representação de malha da plataforma subjacente. Todas essas outras extensões podem ser encontradas [na documentação do Unity.](https://docs.unity3d.com/Packages/com.unity.xr.windowsmr@5.3/api/UnityEngine.XR.WindowsMR.WindowsMRExtensions.html)

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Como começar a trabalhar com os componentes de mapeamento espacial internos do Unity

O Unity oferece dois componentes para adicionar facilmente o mapeamento espacial ao seu aplicativo, o **Renderador** de Mapeamento Espacial e **o Colisor de Mapeamento Espacial.**

### <a name="spatial-mapping-renderer"></a>Renderdor de Mapeamento Espacial

O Renderador de Mapeamento Espacial permite a visualização da malha de mapeamento espacial.

![Renderdor de Mapeamento Espacial no Unity](../images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Colisor de mapeamento espacial

O Colisor de Mapeamento Espacial permite a interação de conteúdo holográfico (ou caractere), como física, com a malha de mapeamento espacial.

![Colisor de mapeamento espacial no Unity](../images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Usando os componentes internos de mapeamento espacial

Você pode adicionar ambos os componentes ao seu aplicativo se quiser visualizar e interagir com superfícies físicas.

Para usar esses dois componentes em seu aplicativo Unity:

1. Selecione um GameObject no centro da área na qual você gostaria de detectar malhas de superfície espacial.
2. Na janela Inspetor, Adicione **Colisor**  >  **de Mapeamento Espacial XR** do Componente  >  **ou**   **Renderador de Mapeamento Espacial**.

Você pode encontrar mais detalhes sobre como usar esses componentes no <a href="https://docs.unity3d.com/2018.4/Documentation/Manual/SpatialMappingComponents.html" target="_blank">site de documentação do Unity</a>.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Ir além dos componentes internos de mapeamento espacial

Esses componentes facilitam a começar a trabalhar com o Mapeamento Espacial. Quando você quiser ir além, há dois caminhos principais a serem explorados:

* Para fazer seu próprio processamento de malha de nível inferior, consulte a seção abaixo sobre a API de script de mapeamento espacial de baixo nível.
* Para fazer uma análise de malha de nível superior, consulte a seção abaixo sobre a biblioteca SpatialUnderstanding no [MixedRealityToolkit.](https://github.com/microsoft/MixedRealityToolkit/tree/master/SpatialUnderstanding)

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Usando a API de mapeamento espacial do Unity de baixo nível

Se você precisar de mais controle do que os componentes renderista de mapeamento espacial e colisor de mapeamento espacial oferecem, use as APIs de mapeamento espacial de baixo nível.

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipos:** *SurfaceObserver,* *SurfaceChange,* *SurfaceData,* *SurfaceId*

Descrevemos o fluxo sugerido para um aplicativo que usa as APIs de mapeamento espacial nas seções abaixo.

### <a name="set-up-the-surfaceobservers"></a>Configurar o(s) SurfaceObserver(s)

Insinue um objeto SurfaceObserver para cada região de espaço definida pelo aplicativo para a qual você precisa de dados de mapeamento espacial.

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

Especifique a região do espaço para a qual cada objeto SurfaceObserver fornece dados chamando SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox ou SetVolumeAsFrustum. Você pode redefinir a região do espaço no futuro chamando um desses métodos novamente.

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Ao chamar SurfaceObserver.Update(), você deve fornecer um manipulador para cada superfície espacial na região de espaço do SurfaceObserver para a que o sistema de mapeamento espacial tenha novas informações. O manipulador recebe, para uma superfície espacial:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a>Manipulando alterações na superfície

Há vários casos principais para lidar: adicionados e atualizados, que podem usar o mesmo caminho de código e removidos.

* Nos casos adicionados e atualizados, adicionamos ou obteremos o GameObject que representa essa malha do dicionário. Criamos um struct SurfaceData com os componentes necessários e, em seguida, chamamos RequestMeshDataAsync para preencher o GameObject com os dados da malha e posicioná-lo na cena.
* No caso removido, removemos o GameObject que representa essa malha do dicionário e a destrói.

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects =
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    switch (changeType)
    {
        case SurfaceChange.Added:
        case SurfaceChange.Updated:
            if (!spatialMeshObjects.ContainsKey(surfaceId))
            {
                spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                spatialMeshObjects[surfaceId].transform.parent = this.transform;
                spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
            }
            GameObject target = spatialMeshObjects[surfaceId];
            SurfaceData sd = new SurfaceData(
                // the surface id returned from the system
                surfaceId,
                // the mesh filter that is populated with the spatial mapping data for this mesh
                target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                // the world anchor used to position the spatial mapping mesh in the world
                target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                // the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                // triangles per cubic meter requested for this mesh
                1000,
                // bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                true
            );

            SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
            break;
        case SurfaceChange.Removed:
            var obj = spatialMeshObjects[surfaceId];
            spatialMeshObjects.Remove(surfaceId);
            if (obj != null)
            {
                GameObject.Destroy(obj);
            }
            break;
        default:
            break;
    }
}
```

### <a name="handling-data-ready"></a>Manipulando dados prontos

O manipulador OnDataReady recebe um objeto SurfaceData. Os objetos WorldAnchor, MeshFilter e (opcionalmente) MeshCollider que ele contém refletem o estado mais recente da superfície espacial associada. Opcionalmente, analise e/ou [processe](../../../design/spatial-mapping.md#mesh-processing) os dados da malha acessando o membro da Malha do objeto MeshFilter. Renderizar a superfície espacial com a malha mais recente e (opcionalmente) usá-la para colisões físicas e raycasts. É importante confirmar se o conteúdo do SurfaceData não é nulo.

### <a name="start-processing-on-updates"></a>Iniciar o processamento em atualizações

SurfaceObserver.Update() deve ser chamado com um atraso, não todos os quadros.

```cs
void Start ()
{
    StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while (true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```
