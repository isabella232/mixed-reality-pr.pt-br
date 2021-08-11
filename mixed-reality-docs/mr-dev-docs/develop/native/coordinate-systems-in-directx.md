---
title: Sistemas de coordenadas no DirectX
description: Saiba mais sobre os sistemas de coordenadas no DirectX e na Realidade Misturada com localizadores espaciais, quadros de referência e âncoras espaciais.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: Realidade Misturada, localizador espacial, quadro de referência espacial, sistema de coordenadas espaciais, estágio espacial, código de exemplo, estabilização de imagem, âncora espacial, armazenamento de âncoras espaciais, perda de acompanhamento, passo a passo, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 5da521568ef15f0c512984c96846939bd30063d3485709d4b6568dc9b155052a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196432"
---
# <a name="coordinate-systems-in-directx"></a>Sistemas de coordenadas no DirectX

> [!NOTE]
> Este artigo está relacionado às APIs nativas do WinRT herddas.  Para novos projetos de aplicativo nativo, é recomendável usar a **[API openXR](openxr-getting-started.md)**.

[Os sistemas de](../../design/coordinate-systems.md) coordenadas formam a base para a compreensão espacial oferecida Windows Mixed Reality APIs.

Os dispositivos VR ou VR de sala única de hoje estabelecem um sistema de coordenadas primário para seu espaço rastreado. Dispositivos de Realidade Misturada como HoloLens são projetados para ambientes grandes e indefinido, com o dispositivo descobrindo e aprendendo sobre seus ambientes conforme o usuário percorre. O dispositivo se adapta para aprimorar continuamente o conhecimento sobre as salas do usuário, mas resulta em sistemas de coordenadas que alteram sua relação entre si durante o tempo de vida dos aplicativos. Windows Mixed Reality dá suporte a um amplo espectro de dispositivos, variando de headsets imersivos encaixados até quadros de referência anexados ao mundo.

>[!NOTE]
>Atualmente, os snippets de código neste artigo demonstram o uso do C++/CX em vez do C++17 compatível com C++/WinRT, conforme usado no modelo de projeto [holográfico C++.](creating-a-holographic-directx-project.md)  Os conceitos são equivalentes para um projeto C++/WinRT, embora você precise traduzir o código.

## <a name="spatial-coordinate-systems-in-windows"></a>Sistemas de coordenadas espaciais Windows

O tipo principal usado para fundamentar os sistemas de coordenadas do mundo real Windows é <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem.</a> Uma instância desse tipo representa um sistema de coordenadas arbitrário, fornecendo um método para obter dados de matriz de transformação que você pode usar para transformar entre dois sistemas de coordenadas sem entender os detalhes de cada um.

Métodos que retornam informações espaciais aceitarão um parâmetro SpatialCoordinateSystem para permitir que você decida o sistema de coordenadas no qual é mais útil para essas coordenadas serem retornadas. As informações espaciais são representadas como pontos, raios ou volumes no ambiente do usuário, e as unidades para essas coordenadas sempre estarão em metros.

Um SpatialCoordinateSystem tem uma relação dinâmica com outros sistemas de coordenadas, incluindo aqueles que representam a posição do dispositivo. A qualquer momento, o dispositivo pode localizar alguns sistemas de coordenadas e não outros. Para a maioria dos sistemas de coordenadas, seu aplicativo deve estar pronto para lidar com períodos de tempo durante os quais eles não podem ser localizados.

Seu aplicativo não deve criar SpatialCoordinateSystems diretamente – em vez de consumi-los por meio das APIs do Perception. Há três fontes principais de sistemas de coordenadas nas APIs de Percepção, cada uma mapeada para um conceito descrito na página [Sistemas de coordenadas:](../../design/coordinate-systems.md)
* Para obter um quadro estacionário de referência, crie <a href="/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">um SpatialStationaryFrameOfReference</a> ou obtenha um do <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference atual.</a>
* Para obter uma âncora espacial, crie <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">um SpatialAnchor.</a>
* Para obter um quadro anexado de referência, crie <a href="/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">um SpatialLocatorAttachedFrameOfReference</a>.

Todos os sistemas de coordenadas retornados por esses objetos são de direita, com +y para cima, +x à direita e +z para trás. Você pode se lembrar de qual direção o eixo z positivo aponta apontando os dedos da mão esquerda ou direita na direção x positiva e ondulando-os para a direção y positiva. A direção do seu polegar aponta em sua direção ou para longe de você, é a direção em que o eixo z positivo aponta para esse sistema de coordenadas. A ilustração a seguir mostra esses dois sistemas de coordenadas.

![Sistemas de coordenadas à esquerda e à direita](images/left-hand-right-hand.gif)<br>
*Sistemas de coordenadas à esquerda e à direita*

Use a <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">classe SpatialLocator</a> para criar um quadro anexado ou estacionário de referência para inicializar em um SpatialCoordinateSystem com base na HoloLens posição. Continue para a próxima seção para saber mais sobre esse processo.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Colocar hologramas no mundo usando um estágio espacial

O sistema de coordenadas para headsets Windows Mixed Reality imersivos opacos é acessado usando a propriedade <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">spatialStageFrameOfReference::Current</a> estática. Essa API fornece:

* Um sistema de coordenadas
* Informações sobre se o player está em um site ou móvel
* O limite de uma área segura para a viagem se o jogador for móvel
* Uma indicação de se o headset é direcional. 
* Um manipulador de eventos para atualizações no estágio espacial.

Primeiro, podemos obter o estágio espacial e assinar atualizações nele: 

Código para **inicialização de estágio espacial**

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

No método OnCurrentChanged, seu aplicativo deve inspecionar o estágio espacial e atualizar a experiência do player. Neste exemplo, fornecemos uma visualização do limite de estágio e da posição inicial especificada pelo usuário e o intervalo de exibição e intervalo de propriedades de movimentação do estágio. Também fazemos fall back para nosso próprio sistema de coordenadas estacionário, quando um estágio não pode ser fornecido.


Código para **atualização de estágio espacial**

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

O conjunto de vértices que definem o limite de estágio é fornecido em ordem horário. O Windows Mixed Reality shell desenha um limite no limite quando o usuário se aproxima dela, mas talvez você queira triangular a área que pode ser explicada para suas próprias finalidades. O algoritmo a seguir pode ser usado para triangular o estágio.


Código para a **triangularização de estágio espacial**

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Colocar hologramas no mundo usando um quadro estacionário de referência

A [classe SpatialStationaryFrameOfReference](/uwp/api/Windows.Perception.Spatial.SpatialStationaryFrameOfReference) representa um [](../../design/coordinate-systems.md#stationary-frame-of-reference) quadro de referência que permanece estacionário em relação ao ambiente do usuário à medida que o usuário se move. Esse quadro de referência prioriza a manutenção das coordenadas estáveis perto do dispositivo. Um uso fundamental de um SpatialStationaryFrameOfReference é atuar como o sistema de coordenadas do mundo subjacente em um mecanismo de renderização ao renderizar hologramas.

Para obter um SpatialStationaryFrameOfReference, use a [classe SpatialLocator](/uwp/api/Windows.Perception.Spatial.SpatialLocator) e chame [CreateStationaryFrameOfReferenceAtCurrentLocation](/uwp/api/Windows.Perception.Spatial.SpatialLocator).

No código Windows modelo de aplicativo holográfico:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* Quadros de referência estacionários são projetados para fornecer uma posição de melhor ajuste em relação ao espaço geral. As posições individuais dentro desse quadro de referência têm permissão para desmamar um pouco. Isso é normal, pois o dispositivo aprende mais sobre o ambiente.
* Quando um posicionamento preciso de hologramas individuais é necessário, um SpatialAnchor deve ser usado para ancorar o holograma individual em uma posição no mundo real, por exemplo, um ponto que o usuário indica ser de interesse especial. As posições de âncora não são desacordas, mas podem ser corrigidas; A âncora usará a posição corrigida começando no próximo quadro depois que a correção tiver ocorrido.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Colocar hologramas no mundo usando âncoras espaciais

[Âncoras espaciais](../../design/coordinate-systems.md#spatial-anchors) são uma ótima maneira de colocar hologramas em um local específico no mundo real, com o sistema garantindo que a âncora permaneça no local ao longo do tempo. Este tópico explica como criar e usar uma âncora e como trabalhar com dados de âncora.

Você pode criar um SpatialAnchor em qualquer posição e orientação dentro do SpatialCoordinateSystem de sua escolha. O dispositivo deve ser capaz de localizar esse sistema de coordenadas no momento e o sistema não deve ter atingido seu limite de âncoras espaciais.

Depois de definido, o sistema de coordenadas de um SpatialAnchor é ajustado continuamente para manter a posição e a orientação precisas de seu local inicial. Em seguida, você pode usar esse SpatialAnchor para renderizar hologramas que aparecerão fixos no ambiente do usuário nesse local exato.

Os efeitos dos ajustes que mantêm a âncora no local são ampliados à medida que a distância da âncora aumenta. Você deve evitar renderizar o conteúdo em relação a uma âncora que está a mais de 3 metros da origem dessa âncora.

A [propriedade CoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) obtém um sistema de coordenadas que permite colocar o conteúdo em relação à âncora, com a easing aplicada quando o dispositivo ajusta o local preciso da âncora.

Use a [propriedade RawCoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) e o evento [RawCoordinateSystemAdjusted](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) correspondente para gerenciar esses ajustes por conta própria.

### <a name="persist-and-share-spatial-anchors"></a>Persistir e compartilhar âncoras espaciais

Você pode persistir um SpatialAnchor localmente usando a classe [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore) e, em seguida, obter novamente em uma sessão de aplicativo futura no mesmo HoloLens dispositivo.

Usando <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure,</a>você pode criar uma âncora de nuvem durável de um SpatialAnchor local, que seu aplicativo pode localizar em vários dispositivos HoloLens, iOS e Android.  Ao compartilhar uma âncora espacial comum entre vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico em tempo real. 

Você também pode usar as Âncoras Espaciais do <a href="/azure/spatial-anchors/overview" target="_blank">Azure</a> para persistência de holograma assíncrona em HoloLens, iOS e Dispositivos Android.  Ao compartilhar uma âncora espacial de nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo se esses dispositivos não estão presentes juntos ao mesmo tempo.

Para começar a criar experiências compartilhadas em seu aplicativo HoloLens, experimente as Âncoras Espaciais do <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure de</a>5 minutos HoloLens início rápido .

Quando estiver em execução com as Âncoras Espaciais do Azure, você poderá criar e localizar <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">âncoras no HoloLens</a>.  Os passo a passo também estão disponíveis para Android e <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">iOS,</a> permitindo que você compartilhe as mesmas âncoras em todos os dispositivos.

### <a name="create-spatialanchors-for-holographic-content"></a>Criar SpatialAnchors para conteúdo holográfico

Para este exemplo de código, modificamos o modelo Windows aplicativo Holographic para criar âncoras quando o **gesto Pressionado** é detectado. O cubo é colocado na âncora durante a passagem de renderização.

Como várias âncoras são suportadas pela classe auxiliar, podemos colocar quantos cubos quisermos usar este exemplo de código!

> [!NOTE]
> As IDs para âncoras são algo que você controla em seu aplicativo. Neste exemplo, criamos um esquema de nomeação sequencial com base no número de âncoras atualmente armazenadas na coleção de âncoras do aplicativo.

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>Carregar e armazenar em cache de forma assíncrona o SpatialAnchorStore

Vamos ver como escrever uma classe SampleSpatialAnchorHelper que ajuda a lidar com essa persistência, incluindo:
* Armazenar uma coleção de âncoras na memória, indexadas por uma chave Platform::String.
* Carregar âncoras do SpatialAnchorStore do sistema, que é mantido separado da coleção local na memória.
* Salvar a coleção local de âncoras na memória no SpatialAnchorStore quando o aplicativo optar por fazer isso.

Veja como salvar objetos [SpatialAnchor](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) no [SpatialAnchorStore.](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore)

Quando a classe é iniciada, solicitamos SpatialAnchorStore de forma assíncrona. Isso envolve a E/S do sistema conforme a API carrega o armazenamento de âncoras e essa API se tornou assíncrona para que a E/S não seja de bloqueio.

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

Você verá um SpatialAnchorStore que pode ser usado para salvar as âncoras. Este é um IMapView que associa valores de chave que são Cadeias de Caracteres, com valores de dados que são SpatialAnchors. Em nosso código de exemplo, armazenamos isso em uma variável de membro de classe privada acessível por meio de uma função pública de nossa classe auxiliar.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>Não se esqueça de conectar os eventos de suspensão/retomada para salvar e carregar o armazenamento de âncoras.

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>Salvar conteúdo no armazenamento de âncoras

Quando o sistema suspende seu aplicativo, você precisa salvar suas âncoras espaciais no armazenamento de âncoras. Você também pode optar por salvar âncoras no armazenamento de âncoras em outros momentos, conforme achar necessário para a implementação do aplicativo.

Quando estiver pronto para tentar salvar as âncoras na memória no SpatialAnchorStore, você poderá fazer um loop em sua coleção e tentar salvar cada uma delas.

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Carregar conteúdo do armazenamento de âncoras quando o aplicativo for retomado

Você pode restaurar âncoras salvas no AnchorStore transferindo-as do IMapView do repositório de âncoras para seu próprio banco de dados na memória de SpatialAnchors quando seu aplicativo for retomado ou a qualquer momento.

Para restaurar âncoras do SpatialAnchorStore, restaure cada uma das que você está interessado em sua própria coleção na memória.

Você precisa de seu próprio banco de dados na memória de SpatialAnchors para associar Cadeias de Caracteres aos SpatialAnchors que você criar. Em nosso código de exemplo, optemos por usar um Windows::Foundation::Collections::IMap para armazenar as âncoras, o que facilita o uso da mesma chave e valor de dados para SpatialAnchorStore.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Uma âncora restaurada pode não ser localizado imediatamente. Por exemplo, pode ser uma âncora em uma sala separada ou em um prédio completamente diferente. As âncoras recuperadas do AnchorStore devem ser testadas quanto à capacidade de locatabilidade antes de usá-las.

<br>

>[!NOTE]
>Neste código de exemplo, recuperamos todas as âncoras do AnchorStore. Isso não é um requisito; seu aplicativo também pode escolher e escolher um determinado subconjunto de âncoras usando valores de chave de cadeia de caracteres que são significativos para sua implementação.

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>Limpe o armazenamento de âncoras, quando necessário

Às vezes, você precisa limpar o estado do aplicativo e gravar novos dados. Veja como fazer isso com [SpatialAnchorStore.](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore)

Usando nossa classe auxiliar, é quase desnecessário envolver a função Clear. Optemos por fazer isso em nossa implementação de exemplo, porque nossa classe auxiliar recebe a responsabilidade de ser a propriedade da instância SpatialAnchorStore.

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Exemplo: relacionar sistemas de coordenadas de âncora a sistemas de coordenadas de quadro de referência estacionários

Digamos que você tenha uma âncora e queira relacionar algo no sistema de coordenadas da âncora ao SpatialStationaryReferenceFrame que você já está usando para seu outro conteúdo. Você pode usar [TryGetTransformTo](/uwp/api/Windows.Perception.Spatial.SpatialCoordinateSystem) para obter uma transformação do sistema de coordenadas da âncora para a do quadro de referência estacionário:

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

Esse processo é útil para você de duas maneiras:
1. Ele informa se os dois quadros de referência podem ser compreendidos em relação um ao outro e;
2. Em caso afirmativo, ele fornece uma transformação para ir diretamente de um sistema de coordenadas para o outro.

Com essas informações, você tem uma compreensão da relação espacial entre objetos entre os dois quadros de referência.

Para renderização, geralmente você pode obter melhores resultados agrupando objetos de acordo com seu quadro de referência original ou âncora. Execute uma passagem de desenho separada para cada grupo. As matrizes de exibição são mais precisas para objetos com transformaçãos de modelo criadas inicialmente usando o mesmo sistema de coordenadas.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Criar hologramas usando um quadro de referência anexado ao dispositivo

Há ocasiões em que você [](../../design/coordinate-systems.md#attached-frame-of-reference) deseja renderizar um holograma que permanece anexado ao local do dispositivo, por exemplo, um painel com informações de depuração ou uma mensagem informacional quando o dispositivo só é capaz de determinar sua orientação e não sua posição no espaço. Para fazer isso, usamos um quadro anexado de referência.

A classe SpatialLocatorAttachedFrameOfReference define sistemas de coordenadas, que são relativos ao dispositivo em vez do mundo real. Esse quadro tem um título fixo em relação ao ambiente do usuário que aponta para a direção que o usuário estava enfrentando quando o quadro de referência foi criado. A partir daí, todas as orientações nesse quadro de referência são relativas a esse título fixo, mesmo quando o usuário gira o dispositivo.

Por HoloLens, a origem do sistema de coordenadas desse quadro está localizada no centro de rotação da cabeça do usuário, de modo que sua posição não seja afetada pela rotação da cabeça. Seu aplicativo pode especificar um deslocamento em relação a esse ponto para posicionar hologramas na frente do usuário.

Para obter um SpatialLocatorAttachedFrameOfReference, use a classe SpatialLocator e chame CreateAttachedFrameOfReferenceAtCurrentHeading.

Isso se aplica a todo o intervalo de Windows Mixed Reality dispositivos.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Usar um quadro de referência anexado ao dispositivo

Essas seções falam sobre o que mudamos no modelo Windows aplicativo Holographic para habilitar um quadro de referência anexado ao dispositivo usando essa API. Esse holograma "anexado" funcionará junto com hologramas estacionários ou ancorados e também poderá ser usado quando o dispositivo não puder encontrar temporariamente sua posição no mundo.

Primeiro, mudamos o modelo para armazenar um SpatialLocatorAttachedFrameOfReference em vez de um SpatialStationaryFrameOfReference:

De **HolographicTagAlongSampleMain.h:**

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

De **HolographicTagAlongSampleMain.cpp:**

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

Durante a atualização, agora obtemos o sistema de coordenadas no carimbo de data/hora obtido com a previsão do quadro.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Obter uma pose de ponteiro espacial e seguir o Olhar do usuário

Queremos que nosso holograma de exemplo siga o olhar do [usuário,](../../design/gaze-and-commit.md)semelhante a como o shell holográfico pode seguir o olhar do usuário. Para isso, precisamos obter SpatialPointerPose do mesmo carimbo de data/hora.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

Esse SpatialPointerPose tem as informações necessárias para posicionar o holograma de acordo com [o título atual do usuário.](gaze-in-directx.md)

Para conforto do usuário, usamos interpolação linear ("lerp") para suavizar a alteração na posição durante um período de tempo. Isso é mais confortável para o usuário do que bloquear o holograma ao seu olhar. Ler a posição do holograma de marcação também nos permite estabilizar o holograma com a reação do movimento. Se não fizemos isso, o usuário verá a tremedagem do holograma devido ao que normalmente são considerados movimentos imperceptíveis da cabeça do usuário.

De **StationaryQuadRenderer::P ositionHologram:**

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>No caso de um painel de depuração, você pode optar por reposicionar o holograma para o lado um pouco para que ele não pregue sua exibição. Aqui está um exemplo de como você pode fazer isso.

Para **StationaryQuadRenderer::P ositionHologram:**

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>Girar o holograma para enfrentar a câmera

Não é suficiente posicionar o holograma, que, nesse caso, é um quad; também devemos girar o objeto para enfrentar o usuário. Essa rotação ocorre no espaço do mundo, porque esse tipo de migragem permite que o holograma permaneça parte do ambiente do usuário. O espaço de exibição não é tão confortável porque o holograma fica bloqueado para a orientação de exibição; nesse caso, você também teria que interpolar entre as matrizes de exibição esquerda e direita para adquirir uma transformação de espaço de exibição que não interrompe a renderização estéreo. Aqui, giramos nos eixos X e Z para enfrentar o usuário.

De **StationaryQuadRenderer::Update:**

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>Renderizar o holograma anexado

Para este exemplo, também escolhemos renderizar o holograma no sistema de coordenadas do SpatialLocatorAttachedReferenceFrame, que é onde posicionámos o holograma. (Se decidirmos renderizar usando outro sistema de coordenadas, precisaríamos adquirir uma transformação do sistema de coordenadas do quadro de referência anexado ao dispositivo para esse sistema de coordenadas.)

De **HolographicTagAlongSampleMain::Render:**

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

É isso! O holograma agora vai "buscar" uma posição que está a 2 metros na frente da direção do olhar do usuário.

>[!NOTE]
>Este exemplo também carrega conteúdo adicional – consulte StationaryQuadRenderer.cpp.

## <a name="handling-tracking-loss"></a>Manipulando a perda de acompanhamento

Quando o dispositivo não consegue se localizar no mundo, o aplicativo passa por "perda de acompanhamento". Windows Mixed Reality aplicativos devem ser capazes de lidar com essas interrupções no sistema de acompanhamento posicional. Essas interrupções podem ser observadas e respostas criadas usando o evento LocatabilityChanged no SpatialLocator padrão.

De **AppMain::SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Quando seu aplicativo recebe um evento LocatabilityChanged, ele pode alterar o comportamento conforme necessário. Por exemplo, no estado PositionalTrackingInhibited, seu aplicativo pode pausar a operação normal e renderizar um [holograma](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) de marcação que exibe uma mensagem de aviso.

O Windows modelo de aplicativo holográfico vem com um manipulador LocatabilityChanged já criado para você. Por padrão, ele exibe um aviso no console de depuração quando o acompanhamento posicional não está disponível. Você pode adicionar código a esse manipulador para fornecer uma resposta conforme necessário do seu aplicativo.

De **AppMain.cpp:**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>mapeamento espacial

As APIs [de mapeamento](spatial-mapping-in-directx.md) espacial usam sistemas de coordenadas para obter transformaçãos de modelo para malhas de superfície.

## <a name="see-also"></a>Confira também
* [Sistemas de coordenadas](../../design/coordinate-systems.md)
* [Âncoras espaciais](../../design/spatial-anchors.md)
* <a href="/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* [Olhar fixo com cabeça e olhos no DirectX](gaze-in-directx.md)
* [Controladores de mãos e emovimento no DirectX](hands-and-motion-controllers-in-directx.md)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)