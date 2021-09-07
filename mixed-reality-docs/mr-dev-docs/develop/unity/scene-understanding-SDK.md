---
title: SDK de compreensão de cena
description: Saiba como instalar e usar o SDK de Compreensão de Cena, incluindo componentes, malhas e objetos em aplicativos de realidade misturada.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Compreensão de cena, mapeamento espacial, Windows Mixed Reality, Unity
ms.openlocfilehash: d7547e1517583e3822a9ac9b54cbf0557cd7780c
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2021
ms.locfileid: "123246278"
---
# <a name="scene-understanding-sdk-overview"></a>Visão geral do SDK de compreensão de cena

A compreensão de cena transforma os dados de sensor de ambiente não estruturados que seu dispositivo de Realidade Misturada captura e os converte em uma representação abstrata poderosa. O SDK atua como a camada de comunicação entre seu aplicativo e o runtime de Compreensão de Cena. Ele tem como objetivo imitar constructos padrão existentes, como grafos de cena 3D para representações 3D e retângulos e painéis 2D para aplicativos 2D. Embora os constructos de Noções básicas de cena mapeiem para estruturas concretas, em geral SceneUnderstanding é uma estrutura agnóstica, permitindo interoperabilidade entre estruturas variadas que interagem com ele. À medida que o Entendimento de Cena evolui, a função do SDK é garantir que novas representações e funcionalidades continuem sendo expostas em uma estrutura unificada. Neste documento, primeiro apresentaremos conceitos de alto nível que ajudarão você a se familiarizar com o ambiente/uso de desenvolvimento e, em seguida, fornecer uma documentação mais detalhada para classes e constructos específicos.

## <a name="where-do-i-get-the-sdk"></a>Onde posso obter o SDK?

O SDK SceneUnderstanding pode ser baixado por meio da [Ferramenta de Recursos de Realidade Misturada](../unity/welcome-to-mr-feature-tool.md).
<!--Unity Note-->
**Observação:** a versão mais recente depende dos pacotes de visualização e você precisará habilitar pacotes de pré-lançamento para vê-los.

Para a versão 0.5.2022-rc e posterior, o Entendimento de Cena dá suporte a projeções de linguagem para C# e C++, permitindo que aplicativos desenvolvam aplicativos para plataformas Win32 ou UWP. A partir desta versão, o SceneUnderstanding dá suporte ao unity no editor, que é usado exclusivamente para se comunicar com o HoloLens2. 
<!-- Unity Note: Since C++ is mentioned, it's not strictly Unity. Not sure about the C#. -->
SceneUnderstanding requer Windows SDK versão 18362 ou superior. 

## <a name="conceptual-overview"></a>Visão geral conceitual

### <a name="the-scene"></a>A cena

Seu dispositivo de realidade misturada está constantemente integrando informações sobre o que ele vê em seu ambiente. O Entendimento de Cena funila todas essas fontes de dados e produz uma única abstração coesiva. O Entendimento de Cena gera Cenas, que são uma composição de [SceneObjects](scene-understanding-SDK.md#sceneobjects) que representam uma instância de uma única coisa (por exemplo, uma parede/teto/piso).) Os próprios Objetos de Cena são uma composição de [SceneComponents, que representam partes mais granulares que compõe esse SceneObject. Exemplos de componentes são quads e malhas, mas no futuro podem representar caixas delimitadores, malhas de colisão, metadados etc.

O processo de conversão dos dados brutos do sensor em uma cena é uma operação potencialmente cara que pode levar segundos para espaços médios (~10x10m) em minutos para espaços grandes (~50 x 50 m) e, portanto, não é algo que está sendo calculado pelo dispositivo sem solicitação de aplicativo. Em vez disso, a geração de cena é disparada pelo aplicativo sob demanda. A classe SceneObserver tem métodos estáticos que podem computar ou desserializar uma cena, com a qual você pode enumerar/interagir. A ação "Computação" é executada sob demanda e executada na CPU, mas em um processo separado (o Driver de Realidade Misturada). No entanto, enquanto fazemos a computação em outro processo, os dados de Cena resultantes são armazenados e mantidos em seu aplicativo no objeto Scene. 

Veja abaixo um diagrama que ilustra esse fluxo de processo e mostra exemplos de dois aplicativos intercalando com o runtime de Compreensão de Cena. 

![Diagrama de processo](images/SU-ProcessFlow.png)

No lado esquerdo, há um diagrama do runtime de realidade misturada, que está sempre ligado e em execução em seu próprio processo. Esse runtime é responsável por executar o rastreamento de dispositivos, o mapeamento espacial e outras operações que o Entendimento de Cena usa para entender e a razão sobre o mundo ao seu redor. No lado direito do diagrama, mostramos dois aplicativos teóricos que usam o Entendimento de Cena. As primeiras interfaces de aplicativo com o MRTK<!--Unity Note-->, que usa o SDK de Compreensão de Cena internamente, o segundo aplicativo calcula e usa duas instâncias de cena separadas. Todas as três cenas neste diagrama geram instâncias distintas das cenas, o driver não está acompanhando o estado global que é compartilhado entre aplicativos e objetos de cena em uma cena não são encontrados em outra. O Entendimento de Cena fornece um mecanismo para acompanhar ao longo do tempo, mas isso é feito usando o SDK. O código de acompanhamento já está em execução no SDK no processo do aplicativo.

Como cada Cena armazena seus dados no espaço de memória do aplicativo, você pode supor que todas as funções do objeto Scene ou seus dados internos sempre são executadas no processo do aplicativo.

### <a name="layout"></a>Layout

Para trabalhar com o Entendimento de Cena, pode ser valioso saber e entender como o runtime representa componentes logicamente e fisicamente. A Cena representa dados com um layout específico que foi escolhido para ser simples, mantendo uma estrutura subjacente que é responsável por atender aos requisitos futuros sem a necessidade de revisões principais. A cena faz isso ao armazenar todos os Componentes (blocos de construção para todos os Objetos de Cena) em uma lista simples e definir hierarquia e composição por meio de referências em que componentes específicos referenciam outros.

Abaixo, apresentamos um exemplo de uma estrutura em sua forma simples e lógica.

<table>
<tr><th>Layout lógico</th><th>Layout Físico</th></tr>
<tr>
<td>
<ul>
  Cena
  <ul>
  <li>SceneObject_1
    <ul>
      <li>SceneMesh_1</li>
      <li>SceneQuad_1</li>
      <li>SceneQuad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>SceneQuad_1</li>
      <li>SceneQuad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>SceneMesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>SceneQuad_1</li>
  <li>SceneQuad_2</li>
  <li>SceneQuad_3</li>
  <li>SceneMesh_1</li>
  <li>SceneMesh_2</li>
</ul>
</td>
</tr>
</table>

Esta ilustração destaca a diferença entre o layout físico e lógico da cena. À esquerda, vemos o layout hierárquico dos dados que seu aplicativo vê ao enumerar a cena. À direita, vemos que a cena é composta por 12 componentes distintos que podem ser acessados individualmente, se necessário. Ao processar uma nova cena, esperamos que os aplicativos andem nessa hierarquia logicamente, no entanto, ao acompanhar entre atualizações de cena, alguns aplicativos só podem estar interessados em direcionar componentes específicos que são compartilhados entre duas cenas.

## <a name="api-overview"></a>Visão geral da API

A seção a seguir fornece uma visão geral de alto nível dos constructos no Entendimento de Cena. Ler esta seção lhe dará uma compreensão de como as cenas são representadas e para que os vários componentes fazem/são usados. A próxima seção fornecerá exemplos de código concreto e detalhes adicionais que são relemplados nesta visão geral.

Todos os tipos descritos abaixo residem no `Microsoft.MixedReality.SceneUnderstanding` namespace .

### <a name="scenecomponents"></a>SceneComponents

Agora que você entende o layout lógico das cenas, podemos apresentar o conceito de SceneComponents e como eles são usados para compor a hierarquia. SceneComponents são as decomposições mais granulares em SceneUnderstanding representando uma única coisa de núcleo, por exemplo, uma malha ou um quad ou uma caixa delimitador. SceneComponents são coisas que podem ser atualizadas independentemente e podem ser referenciadas por outros SceneComponents, portanto, eles têm uma única propriedade global, uma ID exclusiva, que permitem esse tipo de mecanismo de acompanhamento/referência. As IDs são usadas para a composição lógica da hierarquia de cena, bem como para persistência de objeto (o ato de atualizar uma cena em relação à outra).

Se você estiver tratando cada cena computada recentemente como distinta e simplesmente enumerando todos os dados dentro dela, as IDs serão amplamente transparentes para você. No entanto, se você estiver planejando acompanhar componentes em várias atualizações, usará as IDs para indexar e localizar SceneComponents entre objetos Scene.

### <a name="sceneobjects"></a>SceneObjects

Um SceneObject é um SceneComponent que representa uma instância de uma "coisa", por exemplo, uma parede, um piso, um teto etc.... expressa por sua propriedade Kind. SceneObjects são geométricos e, portanto, têm funções e propriedades que representam sua localização no espaço, no entanto, eles não contêm nenhuma estrutura geométrica ou lógica. Em vez disso, SceneObjects fazem referência a outros SceneComponents, especificamente SceneQuads e SceneMeshes, que fornecem as diversas representações com suporte pelo sistema. Quando uma nova cena é computada, seu aplicativo provavelmente enumerará os SceneObjects da cena para processar o que ele está interessado.

SceneObjects pode ter qualquer um dos seguintes:

<table>
<tr>
<th>SceneObjectKind</th> <th>Descrição</th>
</tr>
<tr><td>Segundo plano</td><td>O SceneObject é conhecido por não <b>ser</b> um dos outros tipos reconhecidos de objeto de cena. Essa classe não deve ser confundida com Desconhecido, em que Background é conhecido por não ser parede/piso/forro etc.... embora desconhecido ainda não seja categorizado.</b></td></tr>
<tr><td>Parede</td><td>Uma parede física. Supõe-se que as paredes sejam estruturas ambientais removíveis.</td></tr>
<tr><td>Piso</td><td>Os pisos são qualquer superfície na qual se pode andar. Observação: os pisos não são pisos. Observe também que os pisos assumem qualquer superfície walkable e, portanto, não há suposição explícita de um piso singular. Estruturas de vários níveis, rampas etc.... deve todos classificar como andar.</td></tr>
<tr><td>Ceiling</td><td>A superfície superior de uma sala.</td></tr>
<tr><td>Plataforma</td><td>Uma grande superfície plana na qual você pode posicionar os hologramas. Elas tendem a representar tabelas, pertops e outras superfícies horizontais grandes.</td></tr>
<tr><td>World (Mundo)</td><td>Um rótulo reservado para dados geométricos que são independentes de rotulagem. A malha gerada pela configuração do sinalizador de atualização EnableWorldMesh seria classificada como mundo.</td></tr>
<tr><td>Unknown</td><td>Este objeto de cena ainda deve ser classificado e atribuído a um tipo. Isso não deve ser confundido com o plano de fundo, pois esse objeto pode ser qualquer coisa, o sistema simplesmente não surgiu com uma classificação suficientemente forte para ele.</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

Um SceneMesh é um SceneComponent que aproxima a geometria de objetos geométricos arbitrários usando uma lista de triângulos. SceneMeshes são usados em vários contextos diferentes; Eles podem representar componentes da estrutura de célula Watertight ou como WorldMesh, que representa a malha de mapeamento espacial não associado associada à cena. Os dados de índice e vértice fornecidos com cada malha usam o mesmo layout familiar que os [buffers de vértice e de índice](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) usados para renderizar malhas de triângulo em todas as APIs de renderização modernas. Na compreensão da cena, as malhas usam índices de 32 bits e talvez precisem ser divididas em partes para determinados mecanismos de renderização.

#### <a name="winding-order-and-coordinate-systems"></a>Sistemas de ordem e coordenação de enrolamento

Todas as malhas produzidas pela compreensão da cena devem retornar malhas em um sistema de coordenadas Right-Handed usando a ordem de enrolamento no sentido horário. 

Observação: as compilações do sistema operacional anteriores a. 191105 podem ter um bug conhecido onde as malhas "mundo" estivessem retornando na ordem de enrolamento Counter-Clockwise, que, subsequentemente, foi corrigida.

### <a name="scenequad"></a>SceneQuad

Um SceneQuad é um SceneComponent que representa superfícies 2D que ocupam o mundo 3D. SceneQuads pode ser usado de forma semelhante aos planos ARKit ARPlaneAnchor ou ARCore, mas eles oferecem uma funcionalidade de nível mais alto como telas 2D a serem usadas por aplicativos simples ou UX aumentada. as APIs específicas de 2D são fornecidas para quatro processadores que tornam o posicionamento e o layout simples de usar, e o desenvolvimento (com exceção de renderização) com quádruplos deve se sentir mais parecido com o trabalho com telas 2D do que com malhas 3D.

#### <a name="scenequad-shape"></a>Forma SceneQuad

SceneQuads definir uma superfície retangular limitada em 2D. No entanto, SceneQuads estão representando superfícies com formas arbitrárias e potencialmente complexas (por exemplo, uma tabela com formato de rosca.) Para representar a forma complexa da superfície de um quádruplo, você pode usar a API GetSurfaceMask para renderizar a forma da superfície em um buffer de imagem que você fornece. Se o Sceneobject que tem o quad também tiver uma malha, os triângulos de malha devem ser equivalentes a essa imagem renderizada, ambos representam a geometria real da superfície, seja em coordenadas 2D ou 3D.

## <a name="scene-understanding-sdk-details-and-reference"></a>Detalhes do SDK de compreensão da cena e referência

> [!NOTE] 
> <!--Unity Note-->Ao usar o MRTK, observe que você estará interagindo com MRTK [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) e, portanto, poderá ignorar esta seção na maioria das circunstâncias. Consulte os documentos de [compreensão do MRTK Scene](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) para obter mais informações.

A seção a seguir ajudará você a se familiarizar com os conceitos básicos do SceneUnderstanding. Esta seção deve fornecer as noções básicas, em que ponto você deve ter contexto suficiente para navegar pelos aplicativos de exemplo para ver como o SceneUnderstanding é usado de forma holística.

### <a name="initialization"></a>Inicialização

A primeira etapa para trabalhar com SceneUnderstanding é para seu aplicativo obter referência a um objeto de cena. Isso pode ser feito de duas maneiras, uma cena pode ser computada pelo driver ou uma cena existente que foi computada no passado pode ser desserializada. O último é útil para trabalhar com SceneUnderstanding durante o desenvolvimento, em que aplicativos e experiências podem ser protótipos rapidamente sem um dispositivo de realidade misturada.

As cenas são computadas usando um SceneObserver. Antes de criar uma cena, seu aplicativo deve consultar seu dispositivo para garantir que ele dê suporte a SceneUnderstanding, bem como solicitar acesso de usuário para obter informações de que o SceneUnderstanding precisa.
<!--Unity Note-->
```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

Se RequestAccessAsync () não for chamado, a computação de uma nova cena falhará. Em seguida, computaremos uma nova cena com raiz em relação ao headset da realidade misturada e que tem um raio de 10 medidores.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a>Inicialização a partir de dados (também conhecido como. o caminho do PC)

Embora as cenas possam ser computadas para consumo direto, elas também podem ser computadas em formato serializado para uso posterior. Isso provou ser útil para o desenvolvimento, pois permite que os desenvolvedores trabalhem e testem a compreensão da cena sem a necessidade de um dispositivo. O ato de serializar uma cena é quase idêntico a computar a ti, os dados são retornados ao seu aplicativo em vez de serem desserializados localmente pelo SDK. Você pode desserializá-lo por conta própria ou salvá-lo para uso futuro.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a>Enumeração de sceneobject

Agora que seu aplicativo tem uma cena, seu aplicativo irá examinar e interagir com o SceneObjects. Isso é feito acessando a propriedade **SceneObjects** :

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a>Atualização de componente e relocalização de componentes

Há outra função que recupera componentes na cena chamada ***FindComponent***. Essa função é útil ao atualizar objetos de acompanhamento e localizá-los em cenas posteriores. O código a seguir calculará uma nova cena em relação a uma cena anterior e, em seguida, encontrará o andar na nova cena.

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>Acessando malhas e quatros de objetos de cena

Depois que SceneObjects tiver sido localizado, o aplicativo provavelmente desejará acessar os dados contidos nos quatro processadores/malhas dos quais ele é composto. Esses dados são acessados com as propriedades ***quádruplos** _ e _ *_malhas_**. O código a seguir enumerará todos os quádruplos e malhas do nosso objeto Floor.

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

Observe que é o Sceneobject que tem a transformação relativa à origem da cena. Isso ocorre porque o Sceneobject representa uma instância de "coisa" e é localizável no espaço, as quádruplas e as malhas representam a geometria transformada em relação ao seu pai. É possível que SceneObjects separadas referenciem o mesmo SceneMesh/SceneQuad SceneComponents, e também é possível que um Sceneobject tenha mais de um SceneMesh/SceneQuad.

### <a name="dealing-with-transforms"></a>Lidando com transformações

A compreensão da cena fez uma tentativa deliberada de se alinhar com as representações tradicionais de cena 3D ao lidar com transformações. Portanto, cada cena é confinada a um único sistema de coordenadas, assim como as representações de ambiente 3D mais comuns. SceneObjects cada um fornece seu local relativo a esse sistema de coordenadas. Se seu aplicativo estiver lidando com cenas que ampliam o limite do que uma única origem fornece, ela pode ancorar SceneObjects para SpatialAnchors ou gerar várias cenas e mesclá-las, mas para simplificar, vamos supor que as cenas de Watertight existam em sua própria origem localizada por um NodeId definido por Scene. OriginSpatialGraphNodeId.
<!--Unity Note-->
o seguinte código de unity, por exemplo, mostra como usar Windows percepção e APIs do Unity para alinhar os sistemas de coordenadas. consulte [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) e [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) para obter detalhes sobre as APIs de percepção de Windows e [objetos nativos de realidade misturada no Unity](/windows/mixed-reality/unity-xrdevice-advanced) para obter detalhes sobre como obter um SpatialCoordinateSystem que corresponde à origem mundial do unity.

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

Cada `SceneObject` um tem uma transformação, que é então aplicada a esse objeto. No Unity, convertemos para as coordenadas da mão direita e atribuímos transformações locais da seguinte forma:

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a>Quadra

Os quatro processadores foram projetados para ajudar os cenários de posicionamento de 2D e devem ser considerados como extensões para elementos de UX de tela 2D. Embora os quatro processadores sejam componentes de SceneObjects e possam ser renderizados em 3D, as APIs quádruplas em si pressupõem que as quatro são estruturas 2D. Eles oferecem informações como extensão, forma e fornecem APIs para posicionamento.

Os quatro processadores têm extensões retangulares, mas representam superfícies 2D com formato arbitrário. Para habilitar o posicionamento nessas superfícies 2D que interagem com o ambiente 3D, as quatro ofertas oferecem utilitários para tornar essa interação possível. Atualmente, a compreensão da cena fornece duas funções desse tipo, **FindCentermostPlacement** e **GetSurfaceMask**. FindCentermostPlacement é uma API de alto nível que localiza uma posição no Quad em que um objeto pode ser colocado e tentará encontrar o melhor local para seu objeto, garantindo que a caixa delimitadora que você fornece permanecerá na superfície subjacente.

> [!NOTE]
> As coordenadas da saída são relativas ao quádruplo em "espaço quádruplo" com o canto superior esquerdo (x = 0, y = 0), assim como seria com outros tipos de RECT do Windows. Lembre-se de levar isso em conta ao trabalhar com as origens de seus próprios objetos. 

O exemplo a seguir mostra como localizar o local centermost posicionável e ancorar um holograma para o quad.

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

As etapas 1-4 são altamente dependentes de sua estrutura/implementação específica, mas os temas devem ser semelhantes. É importante observar que o quad simplesmente representa um plano 2D limitado que é localizado no espaço. Tendo seu mecanismo/estrutura sabendo onde o Quad é e criando a raiz de seus objetos em relação ao Quad, seus hologramas estarão localizados corretamente em relação ao mundo real. 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a>Malha

As malhas representam representações geométricas de objetos ou ambientes. Assim como o [mapeamento espacial](../../design/spatial-mapping.md), o índice de malha e os dados de vértice fornecidos com cada malha de superfície espacial usam o mesmo layout familiar que os buffers de vértice e de índice usados para renderizar malhas de triângulo em todas as APIs de renderização modernas. As posições de vértice são fornecidas no sistema de coordenadas do `Scene` . As APIs específicas usadas para fazer referência a esses dados são as seguintes:

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

O código a seguir fornece um exemplo de como gerar uma lista de triângulos a partir da estrutura de malha:

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

Os buffers de índice/vértice devem ser >= as contagens de índice/vértice, mas, caso contrário, podem ser arbitrariamente dimensionados permitindo uma reutilização de memória eficiente.

### <a name="collidermesh"></a>ColliderMesh

Os objetos de cena fornecem acesso aos dados de malha e de teleColliderMeshes de malha por meio das propriedades de malhas e de propriedade. Essas malhas sempre serão correspondentes, o que significa que o índice i'th da propriedade meshes representa a mesma geometria que o índice i'th da propriedade ColliderMeshes. Se o tempo de execução/objeto der suporte a malhas de colisor, você terá a garantia de obter o polígono mais baixo, a aproximação de ordem mais alta e é uma prática recomendada usar ColliderMeshes onde o aplicativo usaria os colisors. Se o sistema não oferecer suporte a coistores, o objeto de malha retornado em ColliderMeshes será o mesmo objeto que a malha reduzindo as restrições de memória.

## <a name="developing-with-scene-understanding"></a>Desenvolvendo com compreensão da cena

Neste ponto, você deve entender os principais blocos de construção da cena que compreendem o tempo de execução e o SDK. A maior parte do poder e da complexidade está em padrões de acesso, interação com estruturas 3D e ferramentas que podem ser escritas sobre essas APIs para realizar tarefas mais avançadas como planejamento espacial, análise de sala, navegação, física e assim por diante. Esperamos capturá-los em exemplos que esperamos orientá-lo na direção correta para fazer seus cenários brilharem. Se houver amostras ou cenários que não estamos abordando, fale conosco e tentaremos documentar/criar um protótipo do que você precisa.

### <a name="where-can-i-get-sample-code"></a>Onde posso obter o código de exemplo?
<!--Unity Note-->
O código de exemplo de compreensão da cena para Unity pode ser encontrado em nossa página [da página de exemplo do Unity](https://github.com/sceneunderstanding-microsoft/unitysample) . Este aplicativo permitirá que você se comunique com seu dispositivo e processe os vários objetos de cena, ou ele permitirá que você carregue uma cena serializada em seu PC e permita que você experimente a compreensão da cena sem um dispositivo.

### <a name="where-can-i-get-sample-scenes"></a>Onde posso obter exemplos de cenas?

Se você tiver um HoloLens2, poderá salvar qualquer cena capturada salvando a saída de ComputeSerializedAsync em arquivo e desserializando-a de sua própria conveniência. 

Se você não tiver um dispositivo HoloLens2, mas quiser brincar com a compreensão da cena, você precisará baixar uma cena previamente capturada. A amostra de compreensão da cena é fornecida atualmente com cenas serializadas que podem ser baixadas e usadas por sua própria conveniência. Você pode encontrá-los aqui:

[Cenas de exemplo de compreensão de cena](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a>Veja também

* [Mapeamento espacial](../../design/spatial-mapping.md)
* [Reconhecimento de cena](../../design/scene-understanding.md)
* [Exemplo de Unity](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)