---
title: Sistemas de coordenadas no DirectX
description: Saiba mais sobre os sistemas de coordenadas no DirectX e a realidade misturada com localizadores espaciais, quadros de referência e âncoras espaciais.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: Realidade misturada, localizador espacial, quadro de referência espacial, sistema de coordenadas espaciais, estágio espacial, código de exemplo, estabilização de imagem, âncora espacial, repositório de âncora espacial, perda de controle, passo a passos, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual
ms.openlocfilehash: 7cf463e4c3bb9b2fe06c834376eb46e3ee20c1ee
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581077"
---
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="b5126-104">Sistemas de coordenadas no DirectX</span><span class="sxs-lookup"><span data-stu-id="b5126-104">Coordinate systems in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="b5126-105">Este artigo está relacionado às APIs nativas do WinRT herdadas.</span><span class="sxs-lookup"><span data-stu-id="b5126-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="b5126-106">Para novos projetos de aplicativos nativos, é recomendável usar a **[API OpenXR](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="b5126-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="b5126-107">Os [sistemas de coordenadas](../../design/coordinate-systems.md) formam a base da compreensão espacial oferecida pelas APIs de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="b5126-107">[Coordinate systems](../../design/coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="b5126-108">Os dispositivos VR de hoje em dia ou de salão único estabelecem um sistema de coordenadas primário para seu espaço rastreado.</span><span class="sxs-lookup"><span data-stu-id="b5126-108">Today's seated VR or single-room VR devices establish one primary coordinate system for their tracked space.</span></span> <span data-ttu-id="b5126-109">Dispositivos de realidade misturada, como o HoloLens, são projetados para grandes ambientes indefinidos, com o dispositivo descobrindo e aprendendo sobre seus arredores à medida que o usuário percorre.</span><span class="sxs-lookup"><span data-stu-id="b5126-109">Mixed Reality devices like HoloLens are designed for large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="b5126-110">O dispositivo se adapta ao aprimoramento contínuo do conhecimento sobre as salas do usuário, mas resulta em sistemas de coordenadas que alteram sua relação entre si no tempo de vida dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b5126-110">The device adapts to continually improving knowledge about the user's rooms, but results in coordinate systems that change their relationship to one another over the apps lifetime.</span></span> <span data-ttu-id="b5126-111">O Windows Mixed Reality dá suporte a uma ampla gama de dispositivos, variando de headsets de imersão enfeitas por meio de quadros de referência conectados ao mundo.</span><span class="sxs-lookup"><span data-stu-id="b5126-111">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="b5126-112">Os trechos de código neste artigo demonstram atualmente o uso de C++/CX em vez de c++/WinRT compatível com C + +17, conforme usado no [modelo de projeto do C++ Holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="b5126-112">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="b5126-113">Os conceitos são equivalentes a um projeto/WinRT do C++, embora você precise converter o código.</span><span class="sxs-lookup"><span data-stu-id="b5126-113">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="b5126-114">Sistemas de coordenadas espaciais no Windows</span><span class="sxs-lookup"><span data-stu-id="b5126-114">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="b5126-115">O tipo de núcleo usado para ponderar os sistemas de coordenadas do mundo real no Windows é o <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span><span class="sxs-lookup"><span data-stu-id="b5126-115">The core type used to reason about real-world coordinate systems in Windows is the <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="b5126-116">Uma instância desse tipo representa um sistema de coordenadas arbitrário, fornecendo um método para obter dados de matriz de transformação que você pode usar para transformar entre dois sistemas de coordenadas sem compreender os detalhes de cada um.</span><span class="sxs-lookup"><span data-stu-id="b5126-116">An instance of this type represents an arbitrary coordinate system, providing a method for getting transformation matrix data that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="b5126-117">Os métodos que retornam informações espaciais aceitarão um parâmetro SpatialCoordinateSystem para permitir que você decida o sistema de coordenadas no qual é mais útil para essas coordenadas serem retornadas.</span><span class="sxs-lookup"><span data-stu-id="b5126-117">Methods that return spatial information will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="b5126-118">As informações espaciais são representadas como pontos, raios ou volumes no ambiente do usuário, e as unidades dessas coordenadas sempre estarão em metros.</span><span class="sxs-lookup"><span data-stu-id="b5126-118">Spatial information is represented as points, rays, or volumes in the user's surroundings, and the units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="b5126-119">Um SpatialCoordinateSystem tem uma relação dinâmica com outros sistemas de coordenadas, incluindo aqueles que representam a posição do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b5126-119">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="b5126-120">A qualquer momento, o dispositivo pode localizar alguns sistemas de coordenadas e não outros.</span><span class="sxs-lookup"><span data-stu-id="b5126-120">At any point, the device can locate some coordinate systems and not others.</span></span> <span data-ttu-id="b5126-121">Para a maioria dos sistemas de coordenadas, seu aplicativo deve estar pronto para lidar com períodos de tempo durante os quais eles não podem ser localizados.</span><span class="sxs-lookup"><span data-stu-id="b5126-121">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="b5126-122">Seu aplicativo não deve criar SpatialCoordinateSystems diretamente-em vez disso, eles devem ser consumidos por meio de APIs de percepção.</span><span class="sxs-lookup"><span data-stu-id="b5126-122">Your application shouldn't create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="b5126-123">Há três fontes principais de sistemas de coordenadas nas APIs de percepção, cada uma das quais são mapeadas para um conceito descrito na página de [sistemas de coordenadas](../../design/coordinate-systems.md) :</span><span class="sxs-lookup"><span data-stu-id="b5126-123">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](../../design/coordinate-systems.md) page:</span></span>
* <span data-ttu-id="b5126-124">Para obter um quadro estacionário de referência, crie um <a href="/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> ou obtenha um do <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>atual.</span><span class="sxs-lookup"><span data-stu-id="b5126-124">To get a stationary frame of reference, create a <a href="/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="b5126-125">Para obter uma âncora espacial, crie um <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span><span class="sxs-lookup"><span data-stu-id="b5126-125">To get a spatial anchor, create a <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="b5126-126">Para obter um quadro de referência anexado, crie um <a href="/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span><span class="sxs-lookup"><span data-stu-id="b5126-126">To get an attached frame of reference, create a <a href="/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="b5126-127">Todos os sistemas de coordenadas retornados por esses objetos são destros, com + y up, + x à direita e + z para trás.</span><span class="sxs-lookup"><span data-stu-id="b5126-127">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="b5126-128">Você pode se lembrar de qual direção os pontos positivos do eixo z apontando os dedos de sua mão esquerda ou direita na direção x positiva e enrolando-os para a direção y positiva.</span><span class="sxs-lookup"><span data-stu-id="b5126-128">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="b5126-129">A direção do seu polegar aponta em sua direção ou para longe de você, é a direção em que o eixo z positivo aponta para esse sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="b5126-129">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="b5126-130">A ilustração a seguir mostra esses dois sistemas de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="b5126-130">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="b5126-131">![Sistemas de coordenadas do lado esquerdo e direito](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="b5126-131">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="b5126-132">*Sistemas de coordenadas do lado esquerdo e direito*</span><span class="sxs-lookup"><span data-stu-id="b5126-132">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="b5126-133">Use a classe <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> para criar um quadro de referência anexado ou estacionário para inicializar em um SpatialCoordinateSystem com base na posição do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b5126-133">Use the <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference to bootstrap into a SpatialCoordinateSystem based on the HoloLens position.</span></span> <span data-ttu-id="b5126-134">Continue na próxima seção para saber mais sobre esse processo.</span><span class="sxs-lookup"><span data-stu-id="b5126-134">Continue to the next section to learn more about this process.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="b5126-135">Coloque os hologramas no mundo inteiro usando um estágio espacial</span><span class="sxs-lookup"><span data-stu-id="b5126-135">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="b5126-136">O sistema de coordenadas para headsets de imersão de realidade mista do Windows é acessado usando a propriedade estática <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference:: Current</a> .</span><span class="sxs-lookup"><span data-stu-id="b5126-136">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="b5126-137">Essa API fornece:</span><span class="sxs-lookup"><span data-stu-id="b5126-137">This API provides:</span></span>

* <span data-ttu-id="b5126-138">Um sistema de coordenadas</span><span class="sxs-lookup"><span data-stu-id="b5126-138">A coordinate system</span></span>
* <span data-ttu-id="b5126-139">Informações sobre se o jogador está conectado ou móvel</span><span class="sxs-lookup"><span data-stu-id="b5126-139">Information about whether the player is seated or mobile</span></span>
* <span data-ttu-id="b5126-140">O limite de uma área segura para resolver se o jogador é móvel</span><span class="sxs-lookup"><span data-stu-id="b5126-140">The boundary of a safe area for walking around if the player is mobile</span></span>
* <span data-ttu-id="b5126-141">Uma indicação de se o headset é direcional.</span><span class="sxs-lookup"><span data-stu-id="b5126-141">An indication of whether the headset is directional.</span></span> 
* <span data-ttu-id="b5126-142">Um manipulador de eventos para atualizações no estágio espacial.</span><span class="sxs-lookup"><span data-stu-id="b5126-142">An event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="b5126-143">Primeiro, obtemos o estágio espacial e assinamos atualizações para ele:</span><span class="sxs-lookup"><span data-stu-id="b5126-143">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="b5126-144">Código para **inicialização de estágio espacial**</span><span class="sxs-lookup"><span data-stu-id="b5126-144">Code for **Spatial stage initialization**</span></span>

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

<span data-ttu-id="b5126-145">No método OnCurrentChanged, seu aplicativo deve inspecionar o estágio espacial e atualizar a experiência do jogador.</span><span class="sxs-lookup"><span data-stu-id="b5126-145">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience.</span></span> <span data-ttu-id="b5126-146">Neste exemplo, fornecemos uma visualização do limite de estágio e a posição inicial especificada pelo usuário e o intervalo de exibição e intervalo de propriedades de movimentação do estágio.</span><span class="sxs-lookup"><span data-stu-id="b5126-146">In this example, we provide a visualization of the stage boundary and the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="b5126-147">Também retornamos ao nosso próprio sistema de coordenadas do seu próprio, quando não é possível fornecer um estágio.</span><span class="sxs-lookup"><span data-stu-id="b5126-147">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="b5126-148">Código para **atualização de estágio espacial**</span><span class="sxs-lookup"><span data-stu-id="b5126-148">Code for **Spatial stage update**</span></span>

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

<span data-ttu-id="b5126-149">O conjunto de vértices que definem o limite de estágio é fornecido na ordem horária.</span><span class="sxs-lookup"><span data-stu-id="b5126-149">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="b5126-150">O Shell de realidade mista do Windows desenha um limite no limite quando o usuário se aproxima dele, mas talvez você queira triangular a área de passagem para suas próprias finalidades.</span><span class="sxs-lookup"><span data-stu-id="b5126-150">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it, but you may want to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="b5126-151">O algoritmo a seguir pode ser usado para triangular o palco.</span><span class="sxs-lookup"><span data-stu-id="b5126-151">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="b5126-152">Código para **triangularização de estágio espacial**</span><span class="sxs-lookup"><span data-stu-id="b5126-152">Code for **Spatial stage triangularization**</span></span>

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="b5126-153">Coloque os hologramas no mundo usando um quadro estacionário de referência</span><span class="sxs-lookup"><span data-stu-id="b5126-153">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="b5126-154">A classe [SpatialStationaryFrameOfReference](/uwp/api/Windows.Perception.Spatial.SpatialStationaryFrameOfReference) representa um quadro de referência que [permanece estacionário](../../design/coordinate-systems.md#stationary-frame-of-reference) em relação ao ambiente do usuário à medida que o usuário se movimenta.</span><span class="sxs-lookup"><span data-stu-id="b5126-154">The [SpatialStationaryFrameOfReference](/uwp/api/Windows.Perception.Spatial.SpatialStationaryFrameOfReference) class represents a frame of reference that [remains stationary](../../design/coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="b5126-155">Esse quadro de referência prioriza a manutenção de coordenadas perto do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b5126-155">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="b5126-156">Um uso importante de um SpatialStationaryFrameOfReference é agir como o sistema de coordenadas do mundo subjacente em um mecanismo de renderização ao renderizar hologramas.</span><span class="sxs-lookup"><span data-stu-id="b5126-156">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="b5126-157">Para obter um SpatialStationaryFrameOfReference, use a classe [SpatialLocator](/uwp/api/Windows.Perception.Spatial.SpatialLocator) e chame [CreateStationaryFrameOfReferenceAtCurrentLocation](/uwp/api/Windows.Perception.Spatial.SpatialLocator).</span><span class="sxs-lookup"><span data-stu-id="b5126-157">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](/uwp/api/Windows.Perception.Spatial.SpatialLocator) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](/uwp/api/Windows.Perception.Spatial.SpatialLocator).</span></span>

<span data-ttu-id="b5126-158">No código de modelo do aplicativo Holographic do Windows:</span><span class="sxs-lookup"><span data-stu-id="b5126-158">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="b5126-159">Quadros de referência estacionários são projetados para fornecer uma posição de melhor ajuste em relação ao espaço geral.</span><span class="sxs-lookup"><span data-stu-id="b5126-159">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="b5126-160">Posições individuais dentro desse quadro de referência têm permissão para serem descompassos um pouco.</span><span class="sxs-lookup"><span data-stu-id="b5126-160">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="b5126-161">Isso é normal, pois o dispositivo aprende mais sobre o ambiente.</span><span class="sxs-lookup"><span data-stu-id="b5126-161">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="b5126-162">Quando o posicionamento preciso de hologramas individuais é necessário, um SpatialAnchor deve ser usado para ancorar o holograma individual em uma posição no mundo real – por exemplo, um ponto que o usuário indica para ser de interesse especial.</span><span class="sxs-lookup"><span data-stu-id="b5126-162">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="b5126-163">As posições de ancoragem não são descompassos, mas podem ser corrigidas; a âncora usará a posição corrigida a partir do próximo quadro depois que a correção tiver ocorrido.</span><span class="sxs-lookup"><span data-stu-id="b5126-163">Anchor positions don't drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="b5126-164">Coloque os hologramas no mundo usando âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="b5126-164">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="b5126-165">As [âncoras espaciais](../../design/coordinate-systems.md#spatial-anchors) são uma ótima maneira de posicionar os hologramas em um local específico no mundo real, com o sistema, garantindo que a âncora permaneça em vigor ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="b5126-165">[Spatial anchors](../../design/coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="b5126-166">Este tópico explica como criar e usar uma âncora e como trabalhar com dados de âncora.</span><span class="sxs-lookup"><span data-stu-id="b5126-166">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="b5126-167">Você pode criar um SpatialAnchor em qualquer posição e orientação dentro do SpatialCoordinateSystem de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="b5126-167">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="b5126-168">O dispositivo deve ser capaz de localizar o sistema de coordenadas no momento e o sistema não deve ter atingido seu limite de âncoras espaciais.</span><span class="sxs-lookup"><span data-stu-id="b5126-168">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="b5126-169">Uma vez definido, o sistema de coordenadas de um SpatialAnchor ajusta-se continuamente para manter a posição e a orientação exatas de seu local inicial.</span><span class="sxs-lookup"><span data-stu-id="b5126-169">Once defined, the coordinate system of a SpatialAnchor adjusts continually to keep the precise position and orientation of its initial location.</span></span> <span data-ttu-id="b5126-170">Você pode usar esse SpatialAnchor para renderizar hologramas que aparecerão fixos no ambiente do usuário nesse local exato.</span><span class="sxs-lookup"><span data-stu-id="b5126-170">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="b5126-171">Os efeitos dos ajustes que mantêm a âncora em vigor são ampliados à medida que a distância da âncora aumenta.</span><span class="sxs-lookup"><span data-stu-id="b5126-171">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="b5126-172">Você deve evitar a renderização de conteúdo em relação a uma âncora que seja maior que cerca de 3 metros da origem dessa âncora.</span><span class="sxs-lookup"><span data-stu-id="b5126-172">You should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="b5126-173">A propriedade [CoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) Obtém um sistema de coordenadas que permite que você coloque o conteúdo em relação à âncora, com a atenuação aplicada quando o dispositivo ajusta o local preciso da âncora.</span><span class="sxs-lookup"><span data-stu-id="b5126-173">The [CoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="b5126-174">Use a propriedade [RawCoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) e o evento [RawCoordinateSystemAdjusted](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) correspondente para gerenciar esses ajustes por conta própria.</span><span class="sxs-lookup"><span data-stu-id="b5126-174">Use the [RawCoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) property and the corresponding [RawCoordinateSystemAdjusted](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="b5126-175">Persistir e compartilhar âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="b5126-175">Persist and share spatial anchors</span></span>

<span data-ttu-id="b5126-176">Você pode persistir um SpatialAnchor localmente usando a classe [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore) e, em seguida, colocá-lo novamente em uma sessão de aplicativo futura no mesmo dispositivo de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b5126-176">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="b5126-177">Usando <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a>, você pode criar uma âncora de nuvem durável a partir de um SpatialAnchor local, que seu aplicativo pode localizar em vários dispositivos HoloLens, Ios e Android.</span><span class="sxs-lookup"><span data-stu-id="b5126-177">By using <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="b5126-178">Ao compartilhar uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico em tempo real.</span><span class="sxs-lookup"><span data-stu-id="b5126-178">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location in real time.</span></span> 

<span data-ttu-id="b5126-179">Você também pode usar <a href="/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para a persistência de holograma assíncrona em dispositivos de HoloLens, Ios e Android.</span><span class="sxs-lookup"><span data-stu-id="b5126-179">You can also use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="b5126-180">Ao compartilhar uma âncora espacial de nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo que esses dispositivos não estejam presentes juntos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="b5126-180">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="b5126-181">Para começar a criar experiências compartilhadas em seu aplicativo de HoloLens, experimente o início rápido de 5 minutos <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">do Azure espaciais do hololens</a>.</span><span class="sxs-lookup"><span data-stu-id="b5126-181">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="b5126-182">Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">criar e localizar âncoras no HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="b5126-182">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="b5126-183">Os passo a passos também estão disponíveis para <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e Ios</a> , permitindo que você compartilhe as mesmas âncoras em todos os dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b5126-183">Walkthroughs are available for <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="b5126-184">Criar SpatialAnchors para conteúdo Holographic</span><span class="sxs-lookup"><span data-stu-id="b5126-184">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="b5126-185">Para este exemplo de código, modificamos o modelo de aplicativo Holographic do Windows para criar âncoras quando o gesto **pressionado** é detectado.</span><span class="sxs-lookup"><span data-stu-id="b5126-185">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="b5126-186">Em seguida, o cubo é colocado na âncora durante a passagem de renderização.</span><span class="sxs-lookup"><span data-stu-id="b5126-186">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="b5126-187">Como há suporte para várias âncoras na classe auxiliar, podemos posicionar tantos cubos quanto desejarmos usar este exemplo de código!</span><span class="sxs-lookup"><span data-stu-id="b5126-187">Since multiple anchors are supported by the helper class, we can place as many cubes as we want to use this code sample!</span></span>

> [!NOTE]
> <span data-ttu-id="b5126-188">As IDs para âncoras são algo que você controla em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b5126-188">The IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="b5126-189">Neste exemplo, criamos um esquema de nomenclatura sequencial com base no número de âncoras atualmente armazenados na coleção de âncoras do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b5126-189">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="b5126-190">Carga assíncrona e cache, o SpatialAnchorStore</span><span class="sxs-lookup"><span data-stu-id="b5126-190">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="b5126-191">Vejamos como escrever uma classe SampleSpatialAnchorHelper que ajuda a lidar com essa persistência, incluindo:</span><span class="sxs-lookup"><span data-stu-id="b5126-191">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="b5126-192">Armazenamento de uma coleção de âncoras na memória, indexados por uma chave Platform:: String.</span><span class="sxs-lookup"><span data-stu-id="b5126-192">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="b5126-193">Carregando âncoras do SpatialAnchorStore do sistema, que é mantido separado da coleção na memória local.</span><span class="sxs-lookup"><span data-stu-id="b5126-193">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="b5126-194">Salvar a coleção na memória local de âncoras para o SpatialAnchorStore quando o aplicativo opta por fazer isso.</span><span class="sxs-lookup"><span data-stu-id="b5126-194">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="b5126-195">Veja como salvar objetos [SpatialAnchor](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) no [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore).</span><span class="sxs-lookup"><span data-stu-id="b5126-195">Here's how to save [SpatialAnchor](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) objects in the [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore).</span></span>

<span data-ttu-id="b5126-196">Quando a classe é iniciada, solicitamos o SpatialAnchorStore de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="b5126-196">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="b5126-197">Isso envolve a e/s do sistema à medida que a API carrega o armazenamento de âncoras, e essa API é assíncrona para que a e/s seja sem bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b5126-197">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

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

<span data-ttu-id="b5126-198">Você receberá um SpatialAnchorStore que pode ser usado para salvar as âncoras.</span><span class="sxs-lookup"><span data-stu-id="b5126-198">You'll be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="b5126-199">Esse é um IMapView que associa os valores de chave que são cadeias de caracteres, com valores de dados que são SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="b5126-199">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="b5126-200">Em nosso código de exemplo, armazenamos isso em uma variável de membro de classe privada que pode ser acessada por meio de uma função pública de nossa classe auxiliar.</span><span class="sxs-lookup"><span data-stu-id="b5126-200">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="b5126-201">Não se esqueça de conectar os eventos suspender/retomar para salvar e carregar o repositório de âncoras.</span><span class="sxs-lookup"><span data-stu-id="b5126-201">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

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

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="b5126-202">Salvar conteúdo no repositório de âncora</span><span class="sxs-lookup"><span data-stu-id="b5126-202">Save content to the anchor store</span></span>

<span data-ttu-id="b5126-203">Quando o sistema suspende seu aplicativo, você precisa salvar suas âncoras espaciais no repositório de âncora.</span><span class="sxs-lookup"><span data-stu-id="b5126-203">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="b5126-204">Você também pode optar por salvar âncoras no repositório de âncora em outros momentos, pois você deve ser necessário para a implementação do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b5126-204">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="b5126-205">Quando estiver pronto para tentar salvar as âncoras na memória para o SpatialAnchorStore, você poderá executar um loop por meio de sua coleção e tentar salvar cada uma delas.</span><span class="sxs-lookup"><span data-stu-id="b5126-205">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="b5126-206">Carregar conteúdo do repositório de âncora quando o aplicativo for retomado</span><span class="sxs-lookup"><span data-stu-id="b5126-206">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="b5126-207">Você pode restaurar âncoras salvas no AnchorStore transferindo-as do IMapView do repositório de ancoragem para seu próprio banco de dados na memória de SpatialAnchors quando seu aplicativo for retomado ou a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="b5126-207">You can restore saved anchors in the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors when your app resumes or at any time.</span></span>

<span data-ttu-id="b5126-208">Para restaurar âncoras do SpatialAnchorStore, restaure cada uma das quais você está interessado em sua própria coleção na memória.</span><span class="sxs-lookup"><span data-stu-id="b5126-208">To restore anchors from the SpatialAnchorStore, restore each one that you're interested in to your own in-memory collection.</span></span>

<span data-ttu-id="b5126-209">Você precisa de seu próprio banco de dados na memória de SpatialAnchors para associar cadeias de caracteres com o SpatialAnchors que você criar.</span><span class="sxs-lookup"><span data-stu-id="b5126-209">You need your own in-memory database of SpatialAnchors to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="b5126-210">Em nosso código de exemplo, optamos por usar um Windows:: Foundation:: Collections:: IMap para armazenar as âncoras, o que facilita o uso da mesma chave e valor de dados para o SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="b5126-210">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="b5126-211">Uma âncora restaurada pode não ser localizável imediatamente.</span><span class="sxs-lookup"><span data-stu-id="b5126-211">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="b5126-212">Por exemplo, pode ser uma âncora em uma sala separada ou em um prédio diferente.</span><span class="sxs-lookup"><span data-stu-id="b5126-212">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="b5126-213">As âncoras recuperadas do AnchorStore devem ser testadas para locatability antes de usá-las.</span><span class="sxs-lookup"><span data-stu-id="b5126-213">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="b5126-214">Neste código de exemplo, recuperamos todas as âncoras do AnchorStore.</span><span class="sxs-lookup"><span data-stu-id="b5126-214">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="b5126-215">Isso não é um requisito; seu aplicativo também poderia escolher um determinado subconjunto de âncoras usando valores de chave de cadeia de caracteres que são significativos para sua implementação.</span><span class="sxs-lookup"><span data-stu-id="b5126-215">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

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

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="b5126-216">Limpar o repositório de âncora, quando necessário</span><span class="sxs-lookup"><span data-stu-id="b5126-216">Clear the anchor store, when needed</span></span>

<span data-ttu-id="b5126-217">Às vezes, você precisa limpar o estado do aplicativo e gravar novos dados.</span><span class="sxs-lookup"><span data-stu-id="b5126-217">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="b5126-218">Veja como fazer isso com o [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore).</span><span class="sxs-lookup"><span data-stu-id="b5126-218">Here's how you do that with the [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore).</span></span>

<span data-ttu-id="b5126-219">Usando nossa classe auxiliar, é quase desnecessário encapsular a função Clear.</span><span class="sxs-lookup"><span data-stu-id="b5126-219">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="b5126-220">Optamos por fazer isso em nossa implementação de exemplo, porque nossa classe auxiliar recebe a responsabilidade de possuir a instância SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="b5126-220">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="b5126-221">Exemplo: relacionando sistemas de coordenadas de âncora a sistemas de coordenadas de quadros de referência de estacionários</span><span class="sxs-lookup"><span data-stu-id="b5126-221">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="b5126-222">Digamos que você tenha uma âncora e queira relacionar algo no sistema de coordenadas da âncora ao SpatialStationaryReferenceFrame que você já está usando para o outro conteúdo.</span><span class="sxs-lookup"><span data-stu-id="b5126-222">Let's say you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame you’re already using for your other content.</span></span> <span data-ttu-id="b5126-223">Você pode usar [TryGetTransformTo](/uwp/api/Windows.Perception.Spatial.SpatialCoordinateSystem) para obter uma transformação do sistema de coordenadas da âncora para aquela do quadro de referência estacionário:</span><span class="sxs-lookup"><span data-stu-id="b5126-223">You can use [TryGetTransformTo](/uwp/api/Windows.Perception.Spatial.SpatialCoordinateSystem) to get a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

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

<span data-ttu-id="b5126-224">Esse processo é útil de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="b5126-224">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="b5126-225">Ele informa se os dois quadros de referência podem ser compreendidos em relação uns aos outros, e;</span><span class="sxs-lookup"><span data-stu-id="b5126-225">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="b5126-226">Nesse caso, ele fornece uma transformação para ir diretamente de um sistema de coordenadas para o outro.</span><span class="sxs-lookup"><span data-stu-id="b5126-226">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="b5126-227">Com essas informações, você tem uma compreensão da relação espacial entre objetos entre os dois quadros de referência.</span><span class="sxs-lookup"><span data-stu-id="b5126-227">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="b5126-228">Para a renderização, muitas vezes você pode obter resultados melhores agrupando objetos de acordo com seu quadro de referência original ou âncora.</span><span class="sxs-lookup"><span data-stu-id="b5126-228">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="b5126-229">Execute uma passagem de desenho separada para cada grupo.</span><span class="sxs-lookup"><span data-stu-id="b5126-229">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="b5126-230">As matrizes de exibição são mais precisas para objetos com transformações de modelo que são criadas inicialmente usando o mesmo sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="b5126-230">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="b5126-231">Criar hologramas usando um quadro de referência anexado ao dispositivo</span><span class="sxs-lookup"><span data-stu-id="b5126-231">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="b5126-232">Há ocasiões em que você deseja renderizar um holograma que [permanece anexado](../../design/coordinate-systems.md#attached-frame-of-reference) ao local do dispositivo, por exemplo, um painel com informações de depuração ou uma mensagem informativa quando o dispositivo só consegue determinar sua orientação e não sua posição no espaço.</span><span class="sxs-lookup"><span data-stu-id="b5126-232">There are times when you want to render a hologram that [remains attached](../../design/coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="b5126-233">Para fazer isso, usamos um quadro de referência anexado.</span><span class="sxs-lookup"><span data-stu-id="b5126-233">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="b5126-234">A classe SpatialLocatorAttachedFrameOfReference define os sistemas de coordenadas, que são relativos ao dispositivo, e não ao mundo real.</span><span class="sxs-lookup"><span data-stu-id="b5126-234">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems, which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="b5126-235">Esse quadro tem um título fixo em relação ao ambiente do usuário que aponta na direção em que o usuário estava voltado quando o quadro de referência foi criado.</span><span class="sxs-lookup"><span data-stu-id="b5126-235">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="b5126-236">A partir desse momento, todas as orientações nesse quadro de referência são relativas a esse cabeçalho fixo, mesmo quando o usuário gira o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b5126-236">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="b5126-237">Para o HoloLens, a origem do sistema de coordenadas deste quadro está localizada no centro da rotação do cabeçalho do usuário, para que sua posição não seja afetada pela rotação de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="b5126-237">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="b5126-238">Seu aplicativo pode especificar um deslocamento relativo a esse ponto para posicionar os hologramas na frente do usuário.</span><span class="sxs-lookup"><span data-stu-id="b5126-238">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="b5126-239">Para obter um SpatialLocatorAttachedFrameOfReference, use a classe SpatialLocator e chame CreateAttachedFrameOfReferenceAtCurrentHeading.</span><span class="sxs-lookup"><span data-stu-id="b5126-239">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="b5126-240">Isso se aplica a todo o intervalo de dispositivos do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b5126-240">This applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="b5126-241">Usar um quadro de referência anexado ao dispositivo</span><span class="sxs-lookup"><span data-stu-id="b5126-241">Use a reference frame attached to the device</span></span>

<span data-ttu-id="b5126-242">Estas seções falam sobre o que alteramos no modelo de aplicativo Holographic do Windows para habilitar um quadro de referência anexado ao dispositivo usando essa API.</span><span class="sxs-lookup"><span data-stu-id="b5126-242">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="b5126-243">Esse holograma "anexado" funcionará junto com hologramas fixos ou ancorados e também poderá ser usado quando o dispositivo estiver temporariamente incapaz de encontrar sua posição no mundo.</span><span class="sxs-lookup"><span data-stu-id="b5126-243">This "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="b5126-244">Primeiro, alteramos o modelo para armazenar um SpatialLocatorAttachedFrameOfReference em vez de um SpatialStationaryFrameOfReference:</span><span class="sxs-lookup"><span data-stu-id="b5126-244">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="b5126-245">De **HolographicTagAlongSampleMain. h**:</span><span class="sxs-lookup"><span data-stu-id="b5126-245">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="b5126-246">De **HolographicTagAlongSampleMain. cpp**:</span><span class="sxs-lookup"><span data-stu-id="b5126-246">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="b5126-247">Durante a atualização, agora obtemos o sistema de coordenadas no carimbo de data/hora obtido com a previsão de quadros.</span><span class="sxs-lookup"><span data-stu-id="b5126-247">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="b5126-248">Obter uma pose de ponteiro espacial e seguir o olhar do usuário</span><span class="sxs-lookup"><span data-stu-id="b5126-248">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="b5126-249">Queremos que nosso holograma de exemplo siga o [olhar](../../design/gaze-and-commit.md)do usuário, semelhante a como o Shell Holographic pode seguir o olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="b5126-249">We want our example hologram to follow the user's [gaze](../../design/gaze-and-commit.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="b5126-250">Para isso, precisamos obter o SpatialPointerPose do mesmo carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="b5126-250">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="b5126-251">Esse SpatialPointerPose tem as informações necessárias para posicionar o holograma de acordo com o [cabeçalho atual do usuário](gaze-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="b5126-251">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze-in-directx.md).</span></span>

<span data-ttu-id="b5126-252">Para o conforto do usuário, usamos interpolação linear ("Lerp") para suavizar a alteração na posição em um período de tempo.</span><span class="sxs-lookup"><span data-stu-id="b5126-252">For user comfort, we use linear interpolation ("lerp") to smooth the change in position over a period of time.</span></span> <span data-ttu-id="b5126-253">Isso é mais confortável para o usuário do que bloquear o holograma para seu olhar.</span><span class="sxs-lookup"><span data-stu-id="b5126-253">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="b5126-254">Lerping a posição da marca no holograma também nos permite estabilizar o holograma ao retardar o movimento.</span><span class="sxs-lookup"><span data-stu-id="b5126-254">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement.</span></span> <span data-ttu-id="b5126-255">Se não fizermos esse retardamento, o usuário veria a tremulação do holograma por causa do que normalmente é considerado como movimentos imperceptívels do cabeçalho do usuário.</span><span class="sxs-lookup"><span data-stu-id="b5126-255">If we didn't do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="b5126-256">De **StationaryQuadRenderer::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="b5126-256">From **StationaryQuadRenderer::PositionHologram**:</span></span>

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
><span data-ttu-id="b5126-257">No caso de um painel de depuração, você pode optar por reposicionar o holograma no lado um pouco para que ele não obstrua o seu modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="b5126-257">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it doesn't obstruct your view.</span></span> <span data-ttu-id="b5126-258">Aqui está um exemplo de como você pode fazer isso.</span><span class="sxs-lookup"><span data-stu-id="b5126-258">Here's an example of how you might do that.</span></span>

<span data-ttu-id="b5126-259">Para **StationaryQuadRenderer::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="b5126-259">For **StationaryQuadRenderer::PositionHologram**:</span></span>

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

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="b5126-260">Girar o holograma para encarar a câmera</span><span class="sxs-lookup"><span data-stu-id="b5126-260">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="b5126-261">Não é suficiente posicionar o holograma, que neste caso é um quádruplo; também devemos girar o objeto para que ele fique à frente do usuário.</span><span class="sxs-lookup"><span data-stu-id="b5126-261">It isn't enough to position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="b5126-262">Essa rotação ocorre no espaço de mundo, pois esse tipo de mensagem permite que o holograma permaneça como parte do ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="b5126-262">This rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="b5126-263">Exibição-o mural de espaço não é tão confortável porque o holograma se torna bloqueado para a orientação de exibição; Nesse caso, você também precisaria fazer a interpolação entre as matrizes de exibição esquerda e direita para adquirir uma transformação de apresentação de espaço de exibição que não interrompa a renderização de estéreo.</span><span class="sxs-lookup"><span data-stu-id="b5126-263">View-space billboarding isn't as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices to acquire a view-space billboard transform that doesn't disrupt stereo rendering.</span></span> <span data-ttu-id="b5126-264">Aqui, giramos nos eixos X e Z para enfrentar o usuário.</span><span class="sxs-lookup"><span data-stu-id="b5126-264">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="b5126-265">De **StationaryQuadRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="b5126-265">From **StationaryQuadRenderer::Update**:</span></span>

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

### <a name="render-the-attached-hologram"></a><span data-ttu-id="b5126-266">Renderizar o holograma anexado</span><span class="sxs-lookup"><span data-stu-id="b5126-266">Render the attached hologram</span></span>

<span data-ttu-id="b5126-267">Para este exemplo, também optamos por renderizar o holograma no sistema de coordenadas do SpatialLocatorAttachedReferenceFrame, que é onde posicionamos o holograma.</span><span class="sxs-lookup"><span data-stu-id="b5126-267">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="b5126-268">(Se tivéssemos decidido renderizar usando outro sistema de coordenadas, precisaremos adquirir uma transformação do sistema de coordenadas do quadro de referência anexado ao dispositivo para esse sistema de coordenadas.)</span><span class="sxs-lookup"><span data-stu-id="b5126-268">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="b5126-269">De **HolographicTagAlongSampleMain:: render**:</span><span class="sxs-lookup"><span data-stu-id="b5126-269">From **HolographicTagAlongSampleMain::Render**:</span></span>

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

<span data-ttu-id="b5126-270">Pronto!</span><span class="sxs-lookup"><span data-stu-id="b5126-270">That's it!</span></span> <span data-ttu-id="b5126-271">O holograma agora "colocará" uma posição que seja de 2 metros na frente da direção do olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="b5126-271">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="b5126-272">Este exemplo também carrega conteúdo adicional-consulte StationaryQuadRenderer. cpp.</span><span class="sxs-lookup"><span data-stu-id="b5126-272">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="b5126-273">Lidando com a perda de controle</span><span class="sxs-lookup"><span data-stu-id="b5126-273">Handling tracking loss</span></span>

<span data-ttu-id="b5126-274">Quando o dispositivo não consegue se localizar no mundo, o aplicativo tem "perda de rastreamento".</span><span class="sxs-lookup"><span data-stu-id="b5126-274">When the device can't locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="b5126-275">Os aplicativos de realidade mista do Windows devem ser capazes de lidar com essas interrupções no sistema de controle posicional.</span><span class="sxs-lookup"><span data-stu-id="b5126-275">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="b5126-276">Essas interrupções podem ser observadas e as respostas criadas usando o evento LocatabilityChanged no SpatialLocator padrão.</span><span class="sxs-lookup"><span data-stu-id="b5126-276">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="b5126-277">De **AppMain:: SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="b5126-277">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="b5126-278">Quando seu aplicativo recebe um evento LocatabilityChanged, ele pode alterar o comportamento conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="b5126-278">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="b5126-279">Por exemplo, no estado PositionalTrackingInhibited, seu aplicativo pode pausar a operação normal e renderizar um [holograma de marca](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) que exibe uma mensagem de aviso.</span><span class="sxs-lookup"><span data-stu-id="b5126-279">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="b5126-280">O modelo de aplicativo Holographic do Windows vem com um manipulador de LocatabilityChanged já criado para você.</span><span class="sxs-lookup"><span data-stu-id="b5126-280">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="b5126-281">Por padrão, ele exibe um aviso no console de depuração quando o controle posicional está indisponível.</span><span class="sxs-lookup"><span data-stu-id="b5126-281">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="b5126-282">Você pode adicionar código a esse manipulador para fornecer uma resposta, conforme necessário, do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b5126-282">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="b5126-283">De **AppMain. cpp:**</span><span class="sxs-lookup"><span data-stu-id="b5126-283">From **AppMain.cpp:**</span></span>

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

## <a name="spatial-mapping"></a><span data-ttu-id="b5126-284">mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="b5126-284">Spatial mapping</span></span>

<span data-ttu-id="b5126-285">As APIs de [mapeamento espacial](spatial-mapping-in-directx.md) fazem uso de sistemas de coordenadas para obter transformações de modelo para malhas de superfície.</span><span class="sxs-lookup"><span data-stu-id="b5126-285">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5126-286">Confira também</span><span class="sxs-lookup"><span data-stu-id="b5126-286">See also</span></span>
* [<span data-ttu-id="b5126-287">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="b5126-287">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="b5126-288">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="b5126-288">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* <span data-ttu-id="b5126-289"><a href="/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a></span><span class="sxs-lookup"><span data-stu-id="b5126-289"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="b5126-290">Olhar fixo com cabeça e olhos no DirectX</span><span class="sxs-lookup"><span data-stu-id="b5126-290">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="b5126-291">Controladores de mãos e emovimento no DirectX</span><span class="sxs-lookup"><span data-stu-id="b5126-291">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="b5126-292">Mapeamento espacial no DirectX</span><span class="sxs-lookup"><span data-stu-id="b5126-292">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)