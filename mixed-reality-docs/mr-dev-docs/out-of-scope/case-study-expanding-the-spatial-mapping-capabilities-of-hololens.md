---
title: Estudo de caso – expandindo os recursos de mapeamento espacial do HoloLens
description: ao criar nossos primeiros aplicativos para Microsoft HoloLens, estávamos ansiosos para ver a distância com que poderíamos enviar os limites do mapeamento espacial no dispositivo.
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, mapeamento espacial
ms.openlocfilehash: f0438990c39570f9188e2e150a8cbe7907d72f7e2be260c72e41646565b8d89e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210426"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>Estudo de caso – expandindo os recursos de mapeamento espacial do HoloLens

ao criar nossos primeiros aplicativos para Microsoft HoloLens, estávamos ansiosos para ver a distância com que poderíamos enviar os limites do mapeamento espacial no dispositivo. Jeff Evertt, engenheiro de software da Microsoft estúdios, explica como uma nova tecnologia foi desenvolvida fora da necessidade de mais controle sobre como os hologramas são colocados no ambiente real do usuário.

> [!NOTE]
> o HoloLens 2 implementa uma nova [cena que entende o tempo de execução](../design/scene-understanding.md), que fornece aos desenvolvedores de realidade misturada uma representação de ambiente estruturada e de alto nível projetada para tornar o desenvolvimento para aplicativos com reconhecimento de ambiente intuitivo. 

## <a name="watch-the-video"></a>Assista ao vídeo

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>Além do mapeamento espacial

enquanto estávamos trabalhando em [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8) e [jovens Conkers](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), dois dos primeiros jogos para HoloLens, descobrimos que, ao fazer o posicionamento de procedimentos de hologramas no mundo físico, precisávamos de um nível mais alto de compreensão sobre o ambiente do usuário. Cada jogo teve suas próprias necessidades de posicionamento específicas: em fragmentos, por exemplo, queríamos ser capaz de distinguir entre diferentes superfícies, como o piso ou uma tabela, para colocar pistas em locais relevantes. Também queríamos ser capazes de identificar superfícies em que os caracteres Holographic de tamanho de vida pudessem se sentar, como um sofá ou uma cadeira. Em Conker jovem, queríamos que Conker e seus adversários consigam usar superfícies levantadas na sala de um jogador como plataformas.

[Asobo estúdios](https://www.asobostudio.com/index.html), nosso parceiro de desenvolvimento para esses jogos, enfrentou esse problema e criou uma tecnologia que estende os recursos de mapeamento espacial de HoloLens. Usando isso, poderíamos analisar a sala de um jogador e identificar superfícies como paredes, tabelas, cadeiras e andares. Ele também nos forneceu a capacidade de otimizar em relação a um conjunto de restrições para determinar o melhor posicionamento para objetos Holographic.

## <a name="the-spatial-understanding-code"></a>O código de compreensão espacial

Pegamos o código original de Asobo e criamos uma biblioteca que encapsula essa tecnologia. A Microsoft e o Asobo agora têm o código-fonte aberto e disponibilizado no [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) para você usar em seus próprios projetos. Todo o código-fonte está incluído, permitindo personalizá-lo às suas necessidades e compartilhar suas melhorias com a Comunidade. O código para o resolvedor de C++ foi encapsulado em uma DLL UWP e exposto ao Unity com um [pré-fabricado de distribuição contido no MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).

Há muitas consultas úteis incluídas no exemplo de Unity que permitirão que você encontre espaços vazios em paredes, coloque objetos no teto ou em espaços grandes no chão, identifique os locais para os caracteres a serem colocados e uma infinidade de outras consultas de compreensão espacial.

embora a solução de mapeamento espacial fornecida pelo HoloLens seja projetada para ser genérica o suficiente para atender às necessidades de toda a gama de espaços problemáticos, o módulo de compreensão espacial foi criado para dar suporte às necessidades de dois jogos específicos. Dessa forma, sua solução é estruturada em um processo específico e um conjunto de suposições:
* **Tamanho fixo Playspace**: o usuário especifica o tamanho máximo de Playspace na chamada de inicialização.
* **Processo de verificação única**: o processo requer uma fase de verificação discreta na qual o usuário percorra, definindo o Playspace. As funções de consulta não funcionarão até que a verificação seja finalizada.
* **Playspace controlado pelo usuário "pintando**": durante a fase de verificação, o usuário se move e procura o Playspace, pintando efetivamente as áreas que devem ser incluídas. A malha gerada é importante para fornecer comentários do usuário durante essa fase.
* **Inportações domésticas ou de instalação do Office**: as funções de consulta são projetadas em relação a superfícies simples e paredes em ângulos retos. Essa é uma limitação flexível. No entanto, durante a fase de verificação, uma análise de eixo primário é concluída para otimizar o mosaico de malha ao longo do eixo principal e secundário.

### <a name="room-scanning-process"></a>Processo de verificação de sala

Ao carregar o módulo de compreensão espacial, a primeira coisa que você fará é digitalizar seu espaço, de modo que todas as superfícies utilizáveis — como piso, teto e paredes — sejam identificadas e rotuladas. Durante o processo de verificação, você examina sua sala e "pinta" as áreas que devem ser incluídas na verificação.

A malha vista durante essa fase é uma parte importante dos comentários visuais que permite aos usuários saber quais partes da sala estão sendo examinadas. A DLL para o módulo de compreensão espacial armazena internamente o Playspace como uma grade de cubos VOXEL dimensionados 8cm. Durante a parte inicial da verificação, uma análise de componente primário é concluída para determinar os eixos da sala. Internamente, ele armazena seu espaço VOXEL alinhado a esses eixos. Uma malha é gerada aproximadamente a cada segundo, extraindo o isosurface do volume VOXEL.

![Malha de mapeamento espacial em branco e entendendo a malha Playspace em verde](images/spatial-mapping-500px.png)

Malha de mapeamento espacial em branco e entendendo a malha Playspace em verde



O arquivo SpatialUnderstanding. cs incluído gerencia o processo da fase de verificação. Ele chama as seguintes funções:
* **SpatialUnderstanding_Init**: chamado uma vez no início.
* **GeneratePlayspace_InitScan**: indica que a fase de verificação deve começar.
* **GeneratePlayspace_UpdateScan_DynamicScan**: chamado cada quadro para atualizar o processo de verificação. A posição e a orientação da câmera são passadas e são usadas para o processo de pintura Playspace, descrito acima.
* **GeneratePlayspace_RequestFinish**: chamado para finalizar o Playspace. Isso usará as áreas "pintadas" durante a fase de verificação para definir e bloquear o Playspace. O aplicativo pode consultar estatísticas durante a fase de verificação, bem como consultar a malha personalizada para fornecer comentários do usuário.
* **Import_UnderstandingMesh**: durante a verificação, o comportamento de **SpatialUnderstandingCustomMesh** fornecido pelo módulo e colocado no pré-fabricado de compreensão consultará periodicamente a malha personalizada gerada pelo processo. Além disso, isso é feito mais uma vez após a verificação ter sido finalizada.

O fluxo de verificação, orientado pelo comportamento **SpatialUnderstanding** , chama **InitScan** e, em seguida, **UpdateScan** cada quadro. Quando a consulta de estatísticas relata cobertura razoável, o usuário pode airtap chamar **RequestFinish** para indicar o fim da fase de verificação. **UpdateScan** continua sendo chamado até que o valor de retorno indique que a dll concluiu o processamento.

## <a name="the-queries"></a>As consultas

Quando a verificação for concluída, você poderá acessar três tipos diferentes de consultas na interface:
* **Consultas de topologia**: essas são consultas rápidas que se baseiam na topologia da sala digitalizada.
* **Consultas de forma**: elas utilizam os resultados de suas consultas de topologia para localizar superfícies horizontais que são uma boa correspondência para formas personalizadas que você define.
* **Consultas de posicionamento de objeto**: são consultas mais complexas que encontram o local de melhor ajuste com base em um conjunto de regras e restrições para o objeto.

Além das três consultas principais, há uma interface raycasting que pode ser usada para recuperar tipos de superfície marcada e uma malha de sala Watertight personalizada pode ser copiada.

### <a name="topology-queries"></a>Consultas de topologia

Dentro da DLL, o Gerenciador de topologia lida com a rotulagem do ambiente. Conforme mencionado acima, grande parte dos dados é armazenada em surfels, que estão contidos em um volume VOXEL. Além disso, a estrutura **PlaySpaceInfos** é usada para armazenar informações sobre o Playspace, incluindo o alinhamento Mundial (mais detalhes sobre isso abaixo), piso e altura do teto.

A heurística é usada para determinar piso, teto e paredes. Por exemplo, a maior e menor superfície horizontal com uma área de superfície maior que 1 m2 é considerada a base. Observe que o caminho da câmera durante o processo de verificação também é usado nesse processo.

Um subconjunto das consultas expostas pelo Gerenciador de topologia é exposto por meio da DLL. As consultas de topologia expostas são as seguintes:
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

Cada uma das consultas tem um conjunto de parâmetros, específico ao tipo de consulta. No exemplo a seguir, o usuário especifica a altura mínima & largura do volume desejado, a altura mínima de posicionamento acima do andar e a quantidade mínima de espaço livre na frente do volume. Todas as medidas estão em metros.




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

Cada uma dessas consultas usa uma matriz pré-configurada de estruturas **TopologyResult** . O parâmetro **locationCount** especifica o comprimento da matriz passada. O valor de retorno informa o número de locais retornados. Esse número nunca é maior que o parâmetro **locationCount** passado.

O **TopologyResult** contém a posição central do volume retornado, a direção oposta (ou seja, normal) e as dimensões do espaço encontrado.




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Observe que, no exemplo de Unity, cada uma dessas consultas é vinculada a um botão no painel de interface do usuário virtual. Os códigos de exemplo codificam os parâmetros de cada uma dessas consultas para valores razoáveis. Consulte *SpaceVisualizer. cs* no código de exemplo para obter mais exemplos.

### <a name="shape-queries"></a>Consultas de forma

Dentro da DLL, o analisador de forma (**ShapeAnalyzer_W**) usa o analisador de topologia para corresponder às formas personalizadas definidas pelo usuário. O exemplo de Unity tem um conjunto predefinido de formas que são mostradas no menu consulta, na guia forma.

Observe que a análise de forma funciona apenas em superfícies horizontais. Um sofá, por exemplo, é definido pela superfície de estação plana e a parte superior do sofá de volta. A consulta de forma procura duas superfícies de um tamanho, altura e intervalo de aspecto específicos, com as duas superfícies alinhadas e conectadas. Usando a terminologia de APIs, a estação de sofá e a parte superior do sofá são componentes de forma e os requisitos de alinhamento são restrições de componente de forma.

Uma consulta de exemplo definida no exemplo de Unity (**ShapeDefinition. cs**), para objetos "sittable", é a seguinte:




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

Cada consulta de forma é definida por um conjunto de componentes de forma, cada um com um conjunto de restrições de componente e um conjunto de restrições de forma que lista as dependências entre os componentes. Este exemplo inclui três restrições em uma única definição de componente e nenhuma restrição de forma entre os componentes (já que há apenas um componente).

Por outro lado, a forma de sofá tem dois componentes Shape e quatro restrições Shape. Observe que os componentes são identificados por seu índice na lista de componentes do usuário (0 e 1 neste exemplo).




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

As funções de wrapper são fornecidas no módulo do Unity para facilitar a criação de definições de formas personalizadas. A lista completa de restrições de componente e forma pode ser encontrada em **SpatialUnderstandingDll. cs** nas estruturas **ShapeComponentConstraint** e **ShapeConstraint** .

![O retângulo azul realça os resultados da consulta de forma de cadeira.](images/chair-shape-query-500px.png)

O retângulo azul realça os resultados da consulta de forma de cadeira.



### <a name="object-placement-solver"></a>Resolvedor de posicionamento de objeto

As consultas de posicionamento de objeto podem ser usadas para identificar locais ideais no espaço físico para colocar seus objetos. O resolvedor encontrará o local de melhor ajuste, considerando as regras e restrições do objeto. Além disso, as consultas de objeto persistem até que o objeto seja removido com chamadas **Solver_RemoveObject** ou **Solver_RemoveAllObjects** , permitindo o posicionamento restrito de vários objetos.

As consultas de posicionamento de objeto consistem em três partes: tipo de posicionamento com parâmetros, uma lista de regras e uma lista de restrições. Para executar uma consulta, use a seguinte API:




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
Essa função usa um nome de objeto, uma definição de posicionamento e uma lista de regras e restrições. Os wrappers do C# fornecem funções auxiliares de construção para facilitar a construção da regra e da restrição. A definição de posicionamento contém o tipo de consulta, ou seja, uma das seguintes opções:




```
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

Cada um dos tipos de posicionamento tem um conjunto de parâmetros exclusivos para o tipo. A estrutura **ObjectPlacementDefinition** contém um conjunto de funções auxiliares estáticas para criar essas definições. Por exemplo, para encontrar um local para colocar um objeto no chão, você pode usar a seguinte função: 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

Além do tipo de posicionamento, você pode fornecer um conjunto de regras e restrições. As regras não podem ser violadas. Os locais de posicionamento possíveis que atendem ao tipo e às regras são então otimizados em relação ao conjunto de restrições para selecionar o local de posicionamento ideal. Cada uma das regras e restrições pode ser criada pelas funções de criação estática fornecidas. Uma regra de exemplo e uma função de construção de restrição são fornecidas abaixo.




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

A consulta de posicionamento de objeto abaixo está procurando um local para colocar um cubo de meio medidor na borda de uma superfície, longe de outros objetos anteriormente posicionados e perto do centro da sala.




```
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

Se for bem-sucedida, uma estrutura **ObjectPlacementResult** que contém a posição de posicionamento, dimensões e orientação será retornada. Além disso, o posicionamento é adicionado à lista interna de objetos posicionados da DLL. As consultas de posicionamento subsequentes levarão esse objeto à conta. O arquivo **LevelSolver. cs** no exemplo de Unity contém mais consultas de exemplo.

![As caixas azuis mostram o resultado de três lugares em consultas de piso com as regras "distantes da posição da câmera".](images/away-from-camera-position-500px.png)

As caixas azuis mostram o resultado de três lugares em consultas de piso com as regras "distantes da posição da câmera".


**Dicas:**
* Ao resolver o local de posicionamento de vários objetos necessários para um cenário de nível ou aplicativo, primeiro resolva os objetos indispensável e grandes para maximizar a probabilidade de que um espaço possa ser encontrado.
* A ordem de posicionamento é importante. Se os posicionamentos de objeto não puderem ser encontrados, tente configurações menos restritas. Ter um conjunto de configurações de fallback é essencial para dar suporte à funcionalidade em várias configurações de sala.

### <a name="ray-casting"></a>Conversão de Ray

Além das três consultas principais, uma interface de conversão de Ray pode ser usada para recuperar tipos de superfície marcada e uma malha Watertight Playspace personalizada pode ser copiada após o espaço ter sido examinado e finalizado, os rótulos são gerados internamente para superfícies como piso, teto e paredes. A função **PlayspaceRaycast** usa um Ray e retorna se o raio colide com uma superfície conhecida e, nesse caso, informações sobre essa superfície na forma de um **RaycastResult**. 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

Internamente, o Raycast é calculado em relação à representação computada 8cm cúbico VOXEL do Playspace. Cada voxel contém um conjunto de elementos Surface com dados de topologia processados (também conhecidos como surfels). As surfels contidas na célula VOXEL interseccionada são comparadas e a melhor correspondência usada para pesquisar as informações de topologia. Esses dados de topologia contêm o rótulo retornado na forma da enumeração **SurfaceTypes** , bem como a área de superfície da superfície interseccionada.

No exemplo de Unity, o cursor converte um raio cada quadro. Primeiro, em relação aos colisors da Unity; segundo, em relação à representação Mundial do módulo de compreensão; e, finalmente, nos elementos da interface do usuário. Neste aplicativo, a interface do usuário obtém prioridade, então o resultado da compreensão e, finalmente, os colisors do Unity. O **surfacetype** é relatado como texto ao lado do cursor.

![Interseção de relatório de resultados Raycast com o piso.](images/raycast-result-500px.jpg)

Interseção de relatório de resultados Raycast com o piso.


## <a name="get-the-code"></a>Obter o código

O código-fonte aberto está disponível em [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity). informe-nos nos [fóruns do HoloLens developer](https://forums.hololens.com/) se você usar o código em um projeto. Não podemos esperar para ver o que você faz com!

## <a name="about-the-author"></a>Sobre o autor

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b> é um líder de engenharia de software que trabalhou em HoloLens desde o início dos dias, da incubação para a experiência de desenvolvimento. antes de HoloLens, ele trabalhou na Kinect do Xbox e no setor de jogos em uma ampla variedade de plataformas e jogos. Jeff é apaixonado por robótica, gráficos e coisas com luzes piscantes que vão soar. Ele gosta de aprender novas coisas e trabalhar com software, hardware e, particularmente, no espaço em que os dois interseccionam.</td>
</tr>
</table>



## <a name="see-also"></a>Veja também
* [Mapeamento espacial](../design/spatial-mapping.md)
* [Reconhecimento de cena](../design/scene-understanding.md)
* [Visualização de varredura do ambiente](../design/room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio: lições da frente do desenvolvimento de HoloLens](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
