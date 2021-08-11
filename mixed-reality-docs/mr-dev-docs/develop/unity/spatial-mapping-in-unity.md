---
title: Mapeamento espacial no Unity
description: Saiba como usar e gerenciar a renderização e a colisão com a geometria do mundo real em aplicativos do Unity Mixed Reality.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, mapeamento espacial, renderizador, colisor, malha, verificação, componente, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, MRTK, realidade misturada Toolkit
ms.openlocfilehash: 4c8d0598898b4717a624562340918f968bd26f1fcde72258907e4fce73bd8489
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223084"
---
# <a name="spatial-mapping-in-unity"></a>Mapeamento espacial no Unity

o [mapeamento espacial](../../design/spatial-mapping.md) permite que você recupere malhas de triângulo que representam as superfícies do mundo em um dispositivo HoloLens. Você pode usar dados de superfície para posicionamento, oclusão e análise de sala para dar a seus projetos de Unity um dose extra de imersão.

O Unity inclui suporte completo para o mapeamento espacial, que é exposto aos desenvolvedores das seguintes maneiras:

1. Componentes de mapeamento espacial disponíveis no MixedRealityToolkit, que fornecem um caminho conveniente e rápido para introdução ao mapeamento espacial
2. APIs de mapeamento espacial de nível inferior, que fornecem controle total e permitem uma personalização mais sofisticada específica do aplicativo

Para usar o mapeamento espacial em seu aplicativo, o recurso spatialPerception precisa ser definido em seu AppxManifest.

## <a name="device-support"></a>Suporte a dispositivos

| Recurso | [HoloLens (primeira gen)](/hololens/hololens1-hardware) | [HoloLens 2](/hololens/hololens2-hardware) | [Headsets imersivos](../../discover/immersive-headset-hardware-details.md) |
| ---- | ---- | ---- | ---- |
| mapeamento espacial | ✔️ | ✔️ | ❌ |

## <a name="setting-the-spatialperception-capability"></a>Configurando o recurso SpatialPerception

Para que um aplicativo consuma dados de mapeamento espacial, o recurso SpatialPerception deve ser habilitado.

Como habilitar o recurso SpatialPerception:

1. no Editor do Unity, abra o painel **"Player Configurações"** (editar > Project Configurações > Player)
2. selecione na guia **"repositório de Windows"**
3. expanda **"Publishing Configurações"** e verifique o recurso **"SpatialPerception"** na lista **"Capabilities"**

> [!NOTE]
> se você já tiver exportado seu projeto do Unity para uma solução Visual Studio, será necessário exportar para uma nova pasta ou [definir manualmente esse recurso no AppxManifest no Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

O mapeamento espacial também requer um MaxVersionTested de pelo menos 10.0.10586.0:

1. em Visual Studio, clique com o botão direito do mouse em **Package. appxmanifest** na Gerenciador de Soluções e selecione **exibir código**
2. Localize a linha especificando **TargetDeviceFamily** e altere **MaxVersionTested = "10.0.10240.0"** para **MaxVersionTested = "10.0.10586.0"**
3. **Salve** o Package. appxmanifest.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Introdução aos componentes de mapeamento espacial interno do Unity

O Unity oferece dois componentes para adicionar facilmente o mapeamento espacial ao seu aplicativo, o **renderizador de mapeamento espacial** e o **Colisor de mapeamento espacial**.

### <a name="spatial-mapping-renderer"></a>Renderizador de mapeamento espacial

O renderizador de mapeamento espacial permite a visualização da malha de mapeamento espacial.

![Renderizador de mapeamento espacial no Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Colisor de mapeamento espacial

O colisor de mapeamento espacial permite a interação de conteúdo Holographic (ou caractere), como a física, com a malha de mapeamento espacial.

![Colisor de mapeamento espacial no Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Usando os componentes internos de mapeamento espacial

Você pode adicionar ambos os componentes ao seu aplicativo se desejar visualizar e interagir com superfícies físicas.

Para usar esses dois componentes em seu aplicativo do Unity:

1. Selecione um gameobject no centro da área na qual você gostaria de detectar malhas de superfície espacial.
2. Na janela Inspetor, **adicione** o processador de  >    >  **mapeamento espacial** do componente XR ou o **renderizador de mapeamento espacial**.

Você pode encontrar mais detalhes sobre como usar esses componentes no site de <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">documentação do Unity</a>.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Indo além dos componentes internos de mapeamento espacial

Esses componentes o tornam fácil de arrastar e soltar para começar a usar o mapeamento espacial.  Quando quiser ir além, há dois caminhos principais a serem explorados:

* Para fazer seu próprio processamento de malha de nível inferior, consulte a seção abaixo sobre a API de script de mapeamento espacial de baixo nível.
* Para fazer uma análise de malha de nível superior, consulte a seção abaixo sobre a biblioteca SpatialUnderstanding em <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Usando a API de mapeamento espacial do Unity de nível baixo

Se você precisar de mais controle do que o renderizador de mapeamento espacial e a oferta de componentes do colisor de mapeamento espacial, use as APIs de mapeamento espacial de nível baixo.

**Namespace:** *UnityEngine. XR. WSA*<br>
**Tipos**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *surfaceid*

Descrevemos o fluxo sugerido para um aplicativo que usa as APIs de mapeamento espacial nas seções a seguir.

### <a name="set-up-the-surfaceobservers"></a>Configurar SurfaceObserver (s)

Crie uma instância de um objeto SurfaceObserver para cada região de espaço definida pelo aplicativo para a qual você precisa de dados de mapeamento espacial.

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

Especifique a região de espaço para a qual cada objeto SurfaceObserver fornecerá dados chamando SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox ou SetVolumeAsFrustum. Você pode redefinir a região do espaço no futuro simplesmente chamando um desses métodos novamente.

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Ao chamar SurfaceObserver. Update (), você deve fornecer um manipulador para cada superfície espacial na região de espaço do SurfaceObserver para a qual o sistema de mapeamento espacial tem novas informações. O manipulador recebe, para uma superfície espacial:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a>Lidando com alterações de superfície

Há vários casos principais para manipular-adicionados e atualizados, que podem usar o mesmo caminho de código e removidos.

* Nos casos adicionados e atualizados, adicionamos ou obtemos o gameobject que representa essa malha do dicionário, criamos uma estrutura SurfaceData com os componentes necessários e chamamos RequestMeshDataAsync para preencher o gameobject com os dados de malha e a posição na cena.
* No caso removido, removemos o gameobject que representa a malha do dicionário e o destruimos.

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

O manipulador OnDataReady recebe um objeto SurfaceData. Os objetos WorldAnchor, MeshFilter e (opcionalmente) MeshCollider que ele contém refletem o estado mais recente da superfície espacial associada. Opcionalmente, analise e/ou [processe](../../design/spatial-mapping.md#mesh-processing) os dados de malha acessando o membro de malha do objeto MeshFilter. Renderize a superfície espacial com a malha mais recente e (opcionalmente) Use-a para colisões de física e raycasts. É importante confirmar que o conteúdo de SurfaceData não é nulo.

### <a name="start-processing-on-updates"></a>Iniciar processamento em atualizações

SurfaceObserver. Update () deve ser chamado em um atraso, e não em todos os quadros.

```cs
void Start ()
{
    StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while(true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```

## <a name="higher-level-mesh-analysis-spatial-understanding"></a>Análise de malha de nível superior: compreensão espacial

> [!CAUTION]
> A compreensão espacial foi preterida em favor da [compreensão da cena](../../design/scene-understanding.md).

O <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> é uma coleção de código do utilitário para o desenvolvimento do Holographic criado nas APIs Holographic do Unity.

### <a name="spatial-understanding"></a>Compreensão espacial

Ao colocar os hologramas no mundo físico, muitas vezes é desejável ir além dos planos de malha e superfície do mapeamento espacial. Quando o posicionamento é feito de procedimento, um nível mais alto de compreensão ambiental é desejável. Isso geralmente requer tomar decisões sobre o que é andar, teto e paredes. Você também tem a capacidade de otimizar em relação a um conjunto de restrições de posicionamento para determinar a melhor localização física para objetos Holographic.

Durante o desenvolvimento de jovens conkers e fragmentos, Asobo estúdios enfrentou esse problema ao desenvolver um solucionador de sala. Cada um desses jogos teve necessidades específicas do jogo, mas eles compartilharam a tecnologia de compreensão espacial principal. A biblioteca HoloToolkit. SpatialUnderstanding encapsula essa tecnologia, permitindo que você encontre rapidamente espaços vazios nas paredes, coloque os objetos no teto, identifique-os com relação ao caractere a ser colocado e uma infinidade de outras consultas de compreensão espacial.

Todo o código-fonte está incluído, permitindo personalizá-lo às suas necessidades e compartilhar suas melhorias com a Comunidade. O código para o resolvedor de C++ foi encapsulado em uma DLL UWP e exposto ao Unity com uma queda no pré-fabricado contido no MixedRealityToolkit.

### <a name="understanding-modules"></a>Noções básicas sobre módulos

Há três interfaces primárias expostas pelo módulo: topologia para consultas espaciais e de superfície simples, forma de detecção de objeto e o resolvedor de posicionamento de objetos para o posicionamento baseado em restrição de conjuntos de objetos. Veja a descrição das duas maneiras abaixo. Além das três interfaces de módulo principais, uma interface de conversão Ray pode ser usada para recuperar tipos de superfície marcada e uma malha Watertight Playspace personalizada pode ser copiada.

### <a name="ray-casting"></a>Conversão de Ray

Após a conclusão da verificação de sala, os rótulos são gerados internamente para superfícies como o piso, o teto e as paredes. A `PlayspaceRaycast` função usa um raio e retorna se o raio colide com uma superfície conhecida e, nesse caso, informações sobre essa superfície na forma de um `RaycastResult` .

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology,
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface,
                    //  but vertical surface that looks like a
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

Internamente, o Raycast é calculado em relação à representação de VOXEL cúbico de 8 cm computada do Playspace. Cada voxel contém um conjunto de elementos Surface com dados de topologia processados (também conhecido como surfels). As surfels contidas na célula VOXEL interseccionada são comparadas e a melhor correspondência usada para pesquisar as informações de topologia. Esses dados de topologia contêm o rótulo retornado na forma da enumeração "SurfaceTypes", bem como a área de superfície da superfície interseccionada.

No exemplo de Unity, o cursor converte um raio cada quadro. Primeiro, em relação aos conflitantes da Unity. Em segundo lugar, em relação à representação Mundial do módulo de compreensão. E, finalmente, os elementos da interface do usuário. Neste aplicativo, a interface do usuário obtém prioridade, em seguida o resultado da compreensão e, por fim, os coliders do Unity. O SurfaceType é relatado como texto ao lado do cursor.

![O tipo de superfície é rotulado ao lado do cursor](images/su-raycastresults-300px.jpg)<br>
*O tipo de superfície é rotulado ao lado do cursor*

### <a name="topology-queries"></a>Consultas de topologia

Na DLL, o gerenciador de topologia lida com a rotulagem do ambiente. Conforme mencionado acima, grande parte dos dados é armazenada em surfels, contidos em um volume voxel. Além disso, a estrutura "PlaySpaceInfos" é usada para armazenar informações sobre o playspace, incluindo o alinhamento do mundo (mais detalhes sobre isso abaixo), o piso e a altura do teto. Heurística é usada para determinar piso, teto e paredes. Por exemplo, a maior e a menor superfície horizontal com área de superfície maior que 1 m2 é considerada o piso.

> [!NOTE]
> O caminho da câmera durante o processo de verificação também é usado nesse processo.

Um subconjunto das consultas expostas pelo gerenciador de Topologia é exposto por meio da dll. As consultas de topologia expostas são as a seguir.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Cada uma das consultas tem um conjunto de parâmetros, específicos para o tipo de consulta. No exemplo a seguir, o usuário especifica a altura mínima & largura do volume desejado, a altura mínima do posicionamento acima do piso e a quantidade mínima de liberação na frente do volume. Todas as medidas estão em metros.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Cada uma dessas consultas recebe uma matriz pré-alocada de estruturas "TopologyResult". O parâmetro "locationCount" especifica o comprimento da matriz passada. O valor retornado informa o número de locais retornados. Esse número nunca é maior que o passado no parâmetro "locationCount".

O "TopologyResult" contém a posição central do volume retornado, a direção voltada (ou seja, normal) e as dimensões do espaço encontrado.

```cpp
struct TopologyResult
{
    DirectX::XMFLOAT3 position;
    DirectX::XMFLOAT3 normal;
    float width;
    float length;
};
```

> [!NOTE]
> No exemplo do Unity, cada uma dessas consultas é vinculada a um botão no painel de interface do usuário virtual. O exemplo codifica os parâmetros para cada uma dessas consultas para valores razoáveis. Consulte SpaceVisualizer.cs no código de exemplo para obter mais exemplos.

### <a name="shape-queries"></a>Consultas de forma

Na dll, o analisador de forma ("ShapeAnalyzer_W") usa o analisador de topologia para corresponder às formas personalizadas definidas pelo usuário. O exemplo do Unity define um conjunto de formas e expõe os resultados por meio do menu de consulta no aplicativo, dentro da guia forma. A intenção é que o usuário possa definir suas próprias consultas de forma de objeto e usá-los, conforme necessário para seu aplicativo.

A análise de forma funciona apenas em superfícies horizontais. Um diviso, por exemplo, é definido pela superfície do banco simples e pela parte superior plana do diviso. A consulta de forma procura duas superfícies de um tamanho, altura e intervalo de aspecto específicos, com as duas superfícies alinhadas e conectadas. Usando a terminologia de APIs, a mesa do couch e a parte superior são componentes de forma e os requisitos de alinhamento são restrições de componente de forma.

Uma consulta de exemplo definida no exemplo do Unity (ShapeDefinition.cs), para objetos "sittable" é a seguinte.

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

Cada consulta de forma é definida por um conjunto de componentes de forma, cada um com um conjunto de restrições de componente e um conjunto de restrições de forma que lista as dependências entre os componentes. Este exemplo inclui três restrições em uma única definição de componente e nenhuma restrição de forma entre componentes (pois há apenas um componente).

Por outro lado, a forma do diviso tem dois componentes de forma e quatro restrições de forma. Os componentes são identificados pelo índice na lista de componentes do usuário (0 e 1 neste exemplo).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

As funções wrapper são fornecidas no módulo do Unity para facilitar a criação de definições de forma personalizadas. A lista completa de restrições de componente e forma pode ser encontrada em "SpatialUnderstandingDll.cs" nas estruturas "ShapeComponentConstraint" e "ShapeConstraint".

![A forma do retângulo é encontrada nessa superfície](images/su-shapequery-300px.jpg)<br>
*A forma do retângulo é encontrada nessa superfície*

### <a name="object-placement-solver"></a>Solucionador de Posicionamento de Objeto

O solucionador de posicionamento de objeto pode ser usado para identificar os locais ideais na sala física para colocar seus objetos. O solucionador encontrará o local mais adequado, considerando as regras e restrições do objeto. Além disso, as consultas de objeto persistem até que o objeto seja removido com chamadas "Solver_RemoveObject" ou "Solver_RemoveAllObjects", permitindo o posicionamento restrito de vários objetos. As consultas de posicionamento de objetos consistem em três partes: tipo de posicionamento com parâmetros, uma lista de regras e uma lista de restrições. Para executar uma consulta, use a API a seguir.

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

Essa função recebe um nome de objeto, definição de posicionamento e uma lista de regras e restrições. Os wrappers C# fornece funções auxiliares de construção para facilitar a construção de regras e restrições. A definição de posicionamento contém o tipo de consulta , ou seja, um dos seguintes.

```cpp
public enum PlacementType
{
    Place_OnFloor,
    Place_OnWall,
    Place_OnCeiling,
    Place_OnShape,
    Place_OnEdge,
    Place_OnFloorAndCeiling,
    Place_RandomInAir,
    Place_InMidAir,
    Place_UnderFurnitureEdge,
};
```

Cada um dos tipos de posicionamento tem um conjunto de parâmetros exclusivos para o tipo. A estrutura "ObjectPlacementDefinition" contém um conjunto de funções auxiliares estáticas para criar essas definições. Por exemplo, para encontrar um local para colocar um objeto no chão, você pode usar a função a seguir. public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) Além do tipo de posicionamento, você pode fornecer um conjunto de regras e restrições. As regras não podem ser violadas. Os locais de posicionamento possíveis que atendem ao tipo e às regras são otimizados em relação ao conjunto de restrições para selecionar o local de posicionamento ideal. Cada uma das regras e restrições pode ser criada pelas funções de criação estática fornecidas. Uma função de construção de restrição e regra de exemplo é fornecida abaixo.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

A consulta de posicionamento de objeto abaixo está procurando um local para colocar um cubo de meio medidor na borda de uma superfície, longe de outros objetos colocados anteriormente e próximo ao centro da sala.

```cs
List<ObjectPlacementRule> rules =
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints =
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f),
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

Se for bem-sucedida, uma estrutura "ObjectPlacementResult" que contém a posição de posicionamento, as dimensões e a orientação será retornada. Além disso, o posicionamento é adicionado à lista interna de objetos colocados da dll. As consultas de posicionamento subsequentes levarão esse objeto em consideração. O arquivo "LevelSolver.cs" no exemplo do Unity contém mais consultas de exemplo.

![Resultados do posicionamento do objeto](images/su-objectplacement-1000px.jpg)<br>
*Figura 3: As caixas azuis como o resultado de três consultas de piso com regras de posição da câmera distantes*

Ao resolver o local de posicionamento de vários objetos necessários para um cenário de nível ou de aplicativo, primeiro resolva objetos grandes e desamarados para maximizar a probabilidade de que um espaço possa ser encontrado. A ordem de posicionamento é importante. Se não for possível encontrar posicionamentos de objeto, tente configurações menos restritas. Ter um conjunto de configurações de fallback é essencial para dar suporte à funcionalidade em várias configurações de sala.

### <a name="room-scanning-process"></a>Processo de verificação de sala

Embora a solução de mapeamento espacial fornecida pelo HoloLens seja projetada para ser genérica o suficiente para atender às necessidades de toda a gama de espaços de problema, o módulo de compreensão espacial foi criado para dar suporte às necessidades de dois jogos específicos. Sua solução é estruturada em torno de um processo específico e um conjunto de suposições, resumidos abaixo.

```txt
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process –
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace.
    Query functions will not function until after the scan has been finalized.
```

"pintura" do playspace orientado pelo usuário – durante a fase de verificação, o usuário se move e procura o ritmo das peças, pintando efetivamente as áreas que devem ser incluídas. A malha gerada é importante para fornecer comentários do usuário durante essa fase. Configuração interna ou de escritório – as funções de consulta são projetadas em torno de superfícies planas e paredes em ângulos direito. Essa é uma limitação suave. No entanto, durante a fase de verificação, uma análise de eixo primário é concluída para otimizar o mosaico de malha ao longo dos eixos principal e secundário. O arquivo SpatialUnderstanding.cs incluído gerencia o processo de fase de verificação. Ele chama as funções a seguir.

```txt
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan –
    Called each frame to update the scanning process. The camera position and
    orientation is passed in and is used for the playspace painting process,
    described above.

GeneratePlayspace_RequestFinish –
    Called to finalize the playspace. This will use the areas “painted” during
    the scan phase to define and lock the playspace. The application can query
    statistics during the scanning phase as well as query the custom mesh for
    providing user feedback.

Import_UnderstandingMesh –
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by
    the module and placed on the understanding prefab will periodically query the
    custom mesh generated by the process. In addition, this is done once more
    after scanning has been finalized.
```

O fluxo de verificação, orientado pelo comportamento "SpatialUnderstanding", chama InitScan e, em seguida, UpdateScan em cada quadro. Quando a consulta de estatísticas relata uma cobertura razoável, o usuário tem permissão para fazer airtap para chamar RequestFinish para indicar o final da fase de verificação. UpdateScan continuará a ser chamado até que seu valor de retorno indique que a dll concluiu o processamento.

### <a name="understanding-mesh"></a>Noções básicas sobre malha

A dll de compreensão armazena internamente o playspace como uma grade de cubos voxel de tamanho de 8 cm. Durante a parte inicial da verificação, uma análise de componente primário é concluída para determinar os eixos da sala. Internamente, ele armazena seu espaço voxel alinhado a esses eixos. Uma malha é gerada aproximadamente a cada segundo extraindo a isosurface do volume voxel.

![Malha gerada produzida a partir do volume de voxel](images/su-custommesh.jpg)<br>
*Malha gerada produzida a partir do volume de voxel*

## <a name="troubleshooting"></a>Solução de problemas

* Verifique se você definiu a [funcionalidade SpatialPerception](#setting-the-spatialperception-capability)
* Quando o acompanhamento é perdido, o próximo evento OnSurfaceChanged removerá todas as malhas.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Mapeamento espacial em áreas de realidade misturada Toolkit

Para obter mais informações sobre como usar o mapeamento espacial com Toolkit realidade misturada, consulte a seção de reconhecimento [espacial](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) dos documentos do MRTK.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo o percurso de desenvolvimento do Unity que fizemos, você está no meio da exploração dos blocos de construção principais do MRTK. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Confira também

* [Sistemas de coordenadas](../../design/coordinate-systems.md)
* [Sistemas de coordenadas no Unity](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine. Bounds</a>
