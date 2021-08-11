---
title: Mapeamento espacial no DirectX
description: Saiba como implementar o mapeamento espacial em seu aplicativo DirectX e como usar o aplicativo de exemplo de mapeamento espacial no SDK da Plataforma Windows Universal.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows realidade misturada, mapeamento espacial, ambiente, interação, directx, winrt, API, código de exemplo, UWP, SDK, passo a passo
ms.openlocfilehash: e7f0735ea28703d3a9f18198901ffa5f06676f78b7b8962bf20824e05f793061
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198842"
---
# <a name="spatial-mapping-in-directx"></a>Mapeamento espacial no DirectX

> [!NOTE]
> Este artigo está relacionado às APIs nativas do WinRT herddas.  Para novos projetos de aplicativo nativo, é recomendável usar a **[API openXR](openxr-getting-started.md)**.

Este tópico descreve como [](../../design/spatial-mapping.md) implementar o mapeamento espacial em seu aplicativo DirectX, incluindo uma explicação detalhada do aplicativo de exemplo de mapeamento espacial empacotado com o SDK da Plataforma Windows Universal.

Este tópico usa o código do exemplo de código [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP.

>[!NOTE]
>Atualmente, os snippets de código neste artigo demonstram o uso do C++/CX em vez do C++17 compatível com C++/WinRT, conforme usado no modelo de projeto [holográfico C++.](creating-a-holographic-directx-project.md)  Os conceitos são equivalentes para um projeto C++/WinRT, embora você precise traduzir o código.

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>mapeamento espacial</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a>Visão geral de desenvolvimento do DirectX

O desenvolvimento de aplicativos nativos para mapeamento espacial usa as APIs no [Windows. Namespace Perception.Spatial.](/uwp/api/Windows.Perception.Spatial) Essas APIs dão a você controle total da funcionalidade de mapeamento espacial, da mesma forma que as APIs de mapeamento espacial são expostas pelo [Unity.](../unity/spatial-mapping-in-unity.md)

### <a name="perception-apis"></a>APIs de Percepção

Os principais tipos fornecidos para o desenvolvimento de mapeamento espacial são os seguinte:
* [SpatialSurfaceObserver](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) fornece informações sobre superfícies em regiões de espaço especificadas pelo aplicativo perto do usuário, na forma de objetos SpatialSurfaceInfo.
* [SpatialSurfaceInfo](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) descreve uma única superfície espacial existente, incluindo uma ID exclusiva, volume delimitador e hora da última alteração. Ele fornecerá um SpatialSurfaceMesh de forma assíncrona mediante solicitação.
* [SpatialSurfaceMeshOptions](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMeshOptions) contém parâmetros usados para personalizar os objetos SpatialSurfaceMesh solicitados de SpatialSurfaceInfo.
* [SpatialSurfaceMesh representa](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh) os dados de malha para uma única superfície espacial. Os dados para posições de vértice, normais de vértice e índices de triângulo estão contidos em objetos SpatialSurfaceMeshBuffer do membro.
* [SpatialSurfaceMeshBuffer](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMeshBuffer) envolve um único tipo de dados de malha.

Ao desenvolver um aplicativo usando essas APIs, seu fluxo de programa básico terá esta aparência (conforme demonstrado no aplicativo de exemplo descrito abaixo):
- **Configurar seu SpatialSurfaceObserver**
  - Chame [RequestAccessAsync](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver)para garantir que o usuário tenha dado permissão para seu aplicativo usar os recursos de mapeamento espacial do dispositivo.
  - Insinue um objeto SpatialSurfaceObserver.
  - Chame [SetBoundingVolumes](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) para especificar as regiões de espaço nas quais você deseja obter informações sobre superfícies espaciais. Você pode modificar essas regiões no futuro chamando essa função novamente. Cada região é especificada usando [um SpatialBoundingVolume.](/uwp/api/Windows.Perception.Spatial.SpatialBoundingVolume)
  - Registre-se para o evento [ObservedSurfacesChanged,](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) que será a incêndio sempre que novas informações estão disponíveis sobre as superfícies espaciais nas regiões de espaço que você especificou.
- **Processar eventos ObservedSurfacesChanged**
  - No manipulador de eventos, chame [GetObservedSurfaces para](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) receber um mapa de objetos SpatialSurfaceInfo. Usando esse mapa, você pode atualizar seus registros de quais superfícies espaciais [existem no ambiente do usuário.](../../design/spatial-mapping.md#mesh-caching)
  - Para cada objeto SpatialSurfaceInfo, você pode consultar [TryGetBounds](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) para determinar as [](../../design/coordinate-systems.md) extensão espaciais da superfície, expressas em um sistema de coordenadas espaciais de sua escolha.
  - Se você decidir solicitar a malha para uma superfície espacial, chame [TryComputeLatestMeshAsync](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo). Você pode fornecer opções que especificam a densidade de triângulos e o formato dos dados de malha retornados.
- **Receber e processar malha**
  - Cada chamada para TryComputeLatestMeshAsync retornará de forma assíncrona um objeto SpatialSurfaceMesh.
  - Desse objeto, você pode acessar os objetos SpatialSurfaceMeshBuffer contidos, que lhe dão acesso aos índices de triângulo, posições de vértice e normais de vértice da malha se você solicitá-los. Esses dados estarão em um formato diretamente compatível com as [APIs do Direct3D 11](/windows/win32/api/d3d11/nf-d3d11-id3d11device-createbuffer) usadas para renderizar malhas.
  - A partir daqui, seu [](../../design/spatial-mapping.md#mesh-processing) aplicativo pode, opcionalmente, analisar [](../../design/spatial-mapping.md#rendering) ou processar os dados da malha e usá-los para renderização e [raycasting de física e colisão.](../../design/spatial-mapping.md#raycasting-and-collision)
  - Um detalhe importante a ser anotado é que você deve aplicar uma escala às posições do vértice de malha (por exemplo, no sombreador de vértice usado para renderizar as malhas), para convertê-las das unidades de inteiro otimizadas nas quais estão armazenadas no buffer, em metros. Você pode recuperar essa escala chamando [VertexPositionScale](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh).

### <a name="troubleshooting"></a>Solução de problemas
* Não se esqueça de dimensionar posições de vértice de malha no sombreador de vértice, usando a escala retornada por [SpatialSurfaceMesh.VertexPositionScale](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh)

## <a name="spatial-mapping-code-sample-walkthrough"></a>Passo a passo de exemplo de código de mapeamento espacial

O [exemplo de](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) código de Mapeamento Espacial Holográfico inclui o código que você pode usar para começar a carregar malhas de superfície em seu aplicativo, incluindo a infraestrutura para gerenciar e renderizar malhas de superfície.

Agora, explicamos como adicionar a funcionalidade de mapeamento de superfície ao seu aplicativo DirectX. Você pode adicionar esse código ao Windows modelo de aplicativo [holográfico](creating-a-holographic-directx-project.md) ou pode acompanhar navegando pelo exemplo de código mencionado acima. Este exemplo de código é baseado no modelo Windows aplicativo Holographic.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configurar seu aplicativo para usar a funcionalidade spatialPerception

Seu aplicativo pode usar a funcionalidade de mapeamento espacial. Isso é necessário porque a malha espacial é uma representação do ambiente do usuário, que pode ser considerada dados privados. Declare essa funcionalidade no arquivo package.appxmanifest para seu aplicativo. Veja um exemplo:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

A funcionalidade vem do namespace **uap2.** Para obter acesso a esse namespace em seu manifesto, inclua-o como um atributo *xlmns* no &lt; elemento Package>. Veja um exemplo:

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Verificar o suporte ao recurso de mapeamento espacial

Windows Mixed Reality dá suporte a uma ampla variedade de dispositivos, incluindo dispositivos, que não são compatíveis com mapeamento espacial. Se seu aplicativo puder usar o mapeamento espacial ou for necessário usar o mapeamento espacial para fornecer funcionalidade, ele deverá verificar se há suporte para o mapeamento espacial antes de tentar usá-lo. Por exemplo, se o mapeamento espacial for exigido pelo seu aplicativo de realidade misturada, ele deverá exibir uma mensagem para esse efeito se um usuário tentar executar em um dispositivo sem mapeamento espacial. Ou seu aplicativo pode renderizar seu próprio ambiente virtual no lugar do ambiente do usuário, fornecendo uma experiência semelhante ao que aconteceria se o mapeamento espacial estivesse disponível. Em qualquer caso, essa API permite que seu aplicativo esteja ciente de quando ele não obterá dados de mapeamento espacial e responderá da maneira apropriada.

Para verificar o dispositivo atual quanto ao suporte ao mapeamento espacial, primeiro verifique se o contrato UWP está no nível 4 ou superior e, em seguida, chame SpatialSurfaceObserver::IsSupported(). Veja como fazer isso no contexto do exemplo de código [mapeamento](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) espacial holográfico. O suporte é verificado logo antes de solicitar acesso.

A API SpatialSurfaceObserver::IsSupported() está disponível a partir do SDK versão 15063. Se necessário, reaqueça o projeto para a plataforma versão 15063 antes de usar essa API.

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

Quando o contrato UWP for menor que o nível 4, o aplicativo deverá continuar como se o dispositivo fosse capaz de fazer mapeamento espacial.

### <a name="request-access-to-spatial-mapping-data"></a>Solicitar acesso aos dados de mapeamento espacial

Seu aplicativo precisa solicitar permissão para acessar dados de mapeamento espacial antes de tentar criar observadores de superfície. Veja um exemplo com base em nosso exemplo de código do Mapeamento de Superfície, com mais detalhes fornecidos posteriormente nesta página:

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a>Criar um observador de superfície

O namespace **Windows::P erception::Spatial::Surfaces** inclui a [classe SpatialSurfaceObserver,](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) que observa um ou mais volumes especificados em [um SpatialCoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialCoordinateSystem). Use uma [instância SpatialSurfaceObserver](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) para acessar dados de malha da superfície em tempo real.

De **AppMain.h:**

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Conforme visto na seção anterior, você deve solicitar acesso aos dados de mapeamento espacial antes que seu aplicativo possa usá-los. Esse acesso é concedido automaticamente no HoloLens.

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

Em seguida, você precisa configurar o observador de superfície para observar um volume delimitado específico. Aqui, observamos uma caixa de 20x20x5 metros, centralizada na origem do sistema de coordenadas.

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

Em vez disso, você pode definir vários volumes delimitados.

*Este é o pseudocódigo:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

Também é possível usar outras formas delimitadores , como uma exibição frustum ou uma caixa delimitada que não está alinhada ao eixo.

*Este é o pseudocódigo:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Se seu aplicativo precisar fazer algo diferente quando os dados de mapeamento de superfície não estão disponíveis, você poderá escrever código  para responder ao caso em que [SpatialPerceptionAccessStatus](/uwp/api/Windows.Perception.Spatial.SpatialPerceptionAccessStatus) não é Permitido – por exemplo, ele não será permitido em PCs com dispositivos imersivos anexados porque esses dispositivos não têm hardware para mapeamento espacial. Para esses dispositivos, você deve depender do estágio espacial para obter informações sobre o ambiente e a configuração do dispositivo do usuário.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Inicializar e atualizar a coleção de malha de superfície

Se o observador da superfície foi criado com êxito, podemos continuar inicializando nossa coleção de malha de superfície. Aqui, usamos a API do modelo de pull para obter o conjunto atual de superfícies observadas imediatamente:

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

Também há um modelo de push disponível para obter dados de malha da superfície. Você pode criar seu aplicativo para usar apenas o modelo de pull se escolher, caso em que você sonda os dados com frequência , digamos, uma vez por quadro ou durante um período de tempo específico, como durante a configuração do jogo. Se sim, o código acima é o que você precisa.

Em nosso exemplo de código, optamos por demonstrar o uso de ambos os modelos para fins de responsabilidade. Aqui, assinamos um evento para receber dados atualizados da malha da superfície sempre que o sistema reconhecer uma alteração.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

Nosso exemplo de código também está configurado para responder a esses eventos. Vamos ver como fazer isso.

**OBSERVAÇÃO:** Essa pode não ser a maneira mais eficiente para seu aplicativo lidar com dados de malha. Esse código é escrito para maior clareza e não é otimizado.

Os dados da malha da superfície são fornecidos em um mapa somente leitura que armazena objetos [SpatialSurfaceInfo](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) usando [Platform::Guids como](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) valores de chave.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Para processar esses dados, primeiro procuraremos valores de chave que não estão em nossa coleção. Detalhes sobre como os dados são armazenados em nosso aplicativo de exemplo serão apresentados posteriormente neste tópico.

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

Também precisamos remover malhas de superfície que estão em nossa coleção de malhas de superfície, mas que não estão mais na coleção do sistema. Para fazer isso, precisamos fazer algo semelhante ao oposto do que mostramos apenas para adicionar e atualizar malhas; fazemos um loop na coleção do nosso aplicativo e verificamos se o **Guid** que temos está na coleção do sistema. Se não estiver na coleção do sistema, a removeremos da nossa.

De nosso manipulador de eventos em AppMain.cpp:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

A implementação da remoção de malha em RealtimeSurfaceMeshRenderer.cpp:

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Adquirir e usar buffers de dados da malha da superfície

Obter as informações da malha da superfície era tão fácil quanto efetuar o esvação de uma coleta de dados e processar atualizações para essa coleção. Agora, entraremos em detalhes sobre como você pode usar os dados.

Em nosso exemplo de código, optamos por usar as malhas de superfície para renderização. Esse é um cenário comum para a oclusão de hologramas por trás de superfícies do mundo real. Você também pode renderizar as malhas ou renderizar versões processadas delas para mostrar ao usuário quais áreas da sala são examinadas antes de começar a fornecer funcionalidade de aplicativo ou jogo.

O exemplo de código inicia o processo quando recebe atualizações da malha da superfície do manipulador de eventos que descrevemos na seção anterior. A linha de código importante nessa função é a chamada para atualizar a malha da *superfície:* neste momento, já processamos as informações da malha e estamos prestes a obter os dados de vértice e índice para uso conforme entendermos.

De RealtimeSurfaceMeshRenderer.cpp:

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

Nosso código de exemplo foi projetado para que uma classe de dados, **SurfaceMesh**, processe o processamento e a renderização de dados de malha. Essas malhas são o que **o RealtimeSurfaceMeshRenderer** realmente mantém um mapa. Cada um tem uma referência ao SpatialSurfaceMesh de onde veio, para que você possa usá-lo sempre que precisar acessar o vértice de malha ou buffers de índice ou obter uma transformação para a malha. Por enquanto, sinalizamos a malha como que precisa de uma atualização.

De SurfaceMesh.cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

Na próxima vez que a malha for convidada a desenhar a si mesma, ela verificará o sinalizador primeiro. Se uma atualização for necessária, os buffers de vértice e índice serão atualizados na GPU.

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

Primeiro, adquirimos os buffers de dados brutos:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

Em seguida, criamos buffers de dispositivo Direct3D com os dados de malha fornecidos pelo HoloLens:

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

**OBSERVAÇÃO:** Para a função auxiliar CreateDirectXBuffer usada no snippet anterior, consulte o exemplo de código de Mapeamento de Superfície: SurfaceMesh.cpp, GetDataFromIBuffer.h. Agora a criação de recursos do dispositivo foi concluída e a malha é considerada carregada e pronta para atualização e renderização.

### <a name="update-and-render-surface-meshes"></a>Atualizar e renderizar malhas de superfície

Nossa classe SurfaceMesh tem uma função de atualização especializada. Cada [SpatialSurfaceMesh](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh) tem sua própria transformação e nosso exemplo usa o sistema de coordenadas atual para nosso **SpatialStationaryReferenceFrame** adquirir a transformação. Em seguida, ele atualiza o buffer constante do modelo na GPU.

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

Quando é hora de renderizar malhas de superfície, fazemos algum trabalho de preparação antes de renderizar a coleção. Configuramos o pipeline do sombreador para a configuração de renderização atual e configuramos o estágio do assembler de entrada. A classe auxiliar de câmera holográfica **CameraResources.cpp** já definiu o buffer constante de exibição/projeção agora.

De **RealtimeSurfaceMeshRenderer::Render**:

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

Quando isso for feito, vamos fazer um loop em nossas malhas e dizer a cada uma delas para desenhar a si mesma. **OBSERVAÇÃO:** Esse código de exemplo não é otimizado para usar nenhum tipo de ressalto, mas você deve incluir esse recurso em seu aplicativo.

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

As malhas individuais são responsáveis por configurar o buffer de vértice e índice, o stride e o buffer constante de transformação de modelo. Assim como com o cubo giratório no modelo Windows aplicativo Holographic, renderizamos em buffers estereográficos usando a instancing.

De **SurfaceMesh::D raw:**

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a>Opções de renderização com Mapeamento de Superfície

O exemplo de código de Mapeamento de Superfície oferece código para renderização somente de oclusão de dados de malha de superfície e para renderização na tela de dados da malha da superfície. Qual caminho você escolher – ou ambos – depende do seu aplicativo. Vamos ver as duas configurações neste documento.

**Renderização de buffers de oclusão para efeito holográfico**

Comece limpando a exibição de destino de renderização para a câmera virtual atual.

De AppMain.cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Essa é uma passagem de "pré-renderização". Aqui, criamos um buffer de oclusão solicitando que o renderista de malha renderizar apenas a profundidade. Nessa configuração, não anexamos uma exibição de destino de renderização e o renderização de malha define o estágio do sombreador de pixel como **nullptr** para que a GPU não se preocupe em desenhar pixels. A geometria será rasterizada para o buffer de profundidade e o pipeline de gráficos será parar por lá.

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

Podemos desenhar hologramas com um teste de profundidade extra no buffer de oclusão do Mapeamento de Superfície. Neste exemplo de código, renderizamos pixels no cubo de uma cor diferente se eles estão atrás de uma superfície.

De AppMain.cpp:

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

Com base no código de SpecialEffectPixelShader.hlsl:

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

**Observação:** Para nossa **rotina GatherDepthLess,** consulte o exemplo de código mapeamento de superfície: SpecialEffectPixelShader.hlsl.

**Renderização de dados de malha da superfície para a exibição**

Também podemos apenas desenhar as malhas de superfície para os buffers de exibição estéreo. Optamos por desenhar rostos completos com iluminação, mas você pode desenhar wireframe, processar malhas antes de renderizar, aplicar um mapa de textura e assim por diante.

Aqui, nosso exemplo de código informa ao renderador de malha para desenhar a coleção. Desta vez, não especificamos uma passagem somente de profundidade, ela anexa um sombreador de pixel e conclui o pipeline de renderização usando os destinos que especificamos para a câmera virtual atual.

```cpp
// Spatial Mapping mesh rendering pass: Draw Spatial Mapping mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>Confira também
* [Como criar um projeto holográfico do DirectX](creating-a-holographic-directx-project.md)
* [Windows. Perception.Spatial API](/uwp/api/Windows.Perception.Spatial)