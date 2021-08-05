---
title: Como renderizar no DirectX
description: Saiba como atualizar e renderizar conteúdo em aplicativos DirectX para Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, renderização, gráficos 3d, HolographicFrame, loop de processamento, loop de atualização, passo a passos, código de exemplo, Direct3D
ms.openlocfilehash: 2c3dd32f5782d6096c6560ec6db55ef1cc7bb533dddb0a4b5fe87cd91bb2f81b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209444"
---
# <a name="rendering-in-directx"></a>Como renderizar no DirectX

> [!NOTE]
> Este artigo está relacionado às APIs nativas do WinRT herdadas.  Para novos projetos de aplicativos nativos, é recomendável usar a **[API OpenXR](openxr-getting-started.md)**.

o Windows Mixed Reality se baseia no DirectX para produzir experiências gráficas 3d ricas para os usuários. A abstração de renderização fica logo acima do DirectX, que permite que os aplicativos se deparam com a posição e a orientação dos observadores de cena de Holographic previstos pelo sistema. O desenvolvedor pode então localizar seus hologramas com base em cada câmera, permitindo que o aplicativo processe esses hologramas em vários sistemas de coordenadas espaciais à medida que o usuário se movimenta.

Observação: este passo a passos descreve a renderização Holographic no Direct3D 11. um modelo de aplicativo do Direct3D 12 Windows Mixed Reality também é fornecido com a extensão de modelos de aplicativo da realidade misturada.

## <a name="update-for-the-current-frame"></a>Atualizar para o quadro atual

Para atualizar o estado do aplicativo para hologramas, uma vez por quadro, o aplicativo irá:
* Obtenha um <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> do sistema de gerenciamento de vídeo.
* Atualize a cena com a previsão atual de onde a exibição da câmera será quando o processamento for concluído. Observe que pode haver mais de uma câmera para a cena Holographic.

Para renderizar para exibições de câmera Holographic, uma vez por quadro, o aplicativo irá:
* Para cada câmera, processe a cena para o quadro atual, usando a exibição de câmera e as matrizes de projeção do sistema.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>Criar um novo quadro do Holographic e obter sua previsão

O <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> tem informações que o aplicativo precisa para atualizar e renderizar o quadro atual. O aplicativo começa cada novo quadro chamando o método **CreateNextFrame** . Quando esse método é chamado, as previsões são feitas usando os dados de sensor mais recentes disponíveis e encapsuladas no objeto **CurrentPrediction** .

Um novo objeto de quadro deve ser usado para cada quadro renderizado, pois ele só é válido para um instante no tempo. A propriedade **CurrentPrediction** contém informações como a posição da câmera. As informações são extrapoladas para o momento exato no momento em que o quadro deve ficar visível para o usuário.

O código a seguir é extraído de **AppMain:: Update**:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>Processar atualizações da câmera

Buffers de fundo podem mudar de quadro para quadro. Seu aplicativo precisa validar o buffer de fundo para cada câmera e liberar e recriar exibições de recursos e buffers de profundidade, conforme necessário. Observe que o conjunto de poses na previsão é a lista autoritativa de câmeras que estão sendo usadas no quadro atual. Normalmente, você usa essa lista para iterar no conjunto de câmeras.

De **AppMain:: Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

De **DeviceResources:: EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>Obter o sistema de coordenadas para usar como base para renderização

Windows Mixed Reality permite que seu aplicativo crie vários [sistemas de coordenadas](coordinate-systems-in-directx.md), como quadros de referência anexados e estáticos para rastrear locais no mundo físico. Seu aplicativo pode, então, usar esses sistemas de coordenadas para saber por onde renderizar os hologramas em cada quadro. Ao solicitar coordenadas de uma API, você sempre passará o <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> dentro do qual deseja que essas coordenadas sejam expressas.

De **AppMain:: Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

Esses sistemas de coordenadas podem ser usados para gerar matrizes de exibição de estéreo ao renderizar o conteúdo em sua cena.

De **CameraResources:: UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>Olhar de processo e entrada de gesto

A entrada [olhar](gaze-in-directx.md) e [Hand](hands-and-motion-controllers-in-directx.md) não são baseadas em tempo e não precisam ser atualizadas na função **StepTimer** . No entanto, essa entrada é algo que o aplicativo precisa para examinar cada quadro.

### <a name="process-time-based-updates"></a>Processar atualizações baseadas em tempo

qualquer aplicativo de renderização em tempo real precisará de alguma maneira de processar atualizações baseadas em tempo – o modelo de aplicativo Windows Holographic usa uma implementação **StepTimer** , semelhante à StepTimer fornecida no modelo de aplicativo UWP DirectX 11. Esta classe auxiliar de exemplo StepTimer pode fornecer atualizações de etapa de tempo fixas, atualizações de etapa de tempo variável e o modo padrão são etapas de tempo variável.

Para a renderização de Holographic, escolhemos não colocar muito na função de temporizador porque você pode configurá-la para ser uma etapa de tempo fixa. Ele pode ser chamado mais de uma vez por quadro – ou não, para alguns quadros – e nossas atualizações de dados Holographic devem ocorrer uma vez por quadro.


De **AppMain:: Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>Posicionar e girar os hologramas em seu sistema de coordenadas

Se você estiver operando em um único sistema de coordenadas, como o modelo faz com o **SpatialStationaryReferenceFrame**, esse processo não é diferente do que é usado de outra forma em gráficos 3D. Aqui, giramos o cubo e definimos a matriz do modelo com base na posição no sistema de coordenadas do imóvel.

De **SpinningCubeRenderer:: Update**:

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

**Observação sobre cenários avançados:** O cubo girando é um exemplo simples de como posicionar um holograma em um único quadro de referência. Também é possível [usar vários SpatialCoordinateSystems](coordinate-systems-in-directx.md) no mesmo quadro renderizado, ao mesmo tempo.

### <a name="update-constant-buffer-data"></a>Atualizar dados de buffer constante

As transformações de modelo para conteúdo são atualizadas como de costume. Agora, você terá transformações válidas computadas para o sistema de coordenadas em que será renderizado.

De **SpinningCubeRenderer:: Update**:

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

E quanto às transformações de exibição e projeção? Para obter melhores resultados, queremos esperar até que esteja quase pronto para nossas chamadas de desenho antes de obtê-las.

## <a name="render-the-current-frame"></a>Renderizar o quadro atual

a renderização em Windows Mixed Reality não é muito diferente da renderização em uma exibição mono 2d, mas há algumas diferenças:
* As previsões de quadros Holographic são importantes. Quanto mais próximo a previsão for quando seu quadro for apresentado, melhor será o seu holograma.
* Windows Mixed Reality controla as exibições da câmera. Renderize para cada um porque o quadro Holographic será apresentado para você posteriormente.
* É recomendável fazer a renderização de estéreo usando o desenho em instância para uma matriz de destino de renderização. O modelo de aplicativo Holographic usa a abordagem recomendada de desenho em instância para uma matriz de destino de renderização, que usa uma exibição de destino de renderização em um **Texture2DArray**.
* Se você quiser renderizar sem usar a instanciação de estéreo, será necessário criar duas RenderTargetViews não matrizes, uma para cada olho. Cada RenderTargetViews faz referência a uma das duas fatias no **Texture2DArray** fornecido ao aplicativo do sistema. Isso não é recomendado, pois normalmente é mais lento do que usar a instanciação.

### <a name="get-an-updated-holographicframe-prediction"></a>Obter uma previsão HolographicFrame atualizada

A atualização da previsão de quadros melhora a eficácia da estabilização da imagem. Você Obtém um posicionamento mais preciso de hologramas devido ao tempo mais curto entre a previsão e quando o quadro fica visível para o usuário. Idealmente, atualize sua previsão de quadros logo antes da renderização.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>Renderizar para cada câmera

O loop no conjunto da câmera representa a previsão e renderizado para cada câmera nesse conjunto.

**Configurar sua passagem de renderização**

Windows Mixed Reality usa a renderização estereoscópico para aprimorar a ilusão de profundidade e para renderizar stereoscopically, para que as exibições esquerda e direita estejam ativas. Com a renderização estereoscópico, há um deslocamento entre as duas exibições, que o cérebro pode reconciliar como profundidade real. esta seção aborda a renderização de estereoscópico usando a instanciação, usando código do modelo de aplicativo Windows Holographic.

Cada câmera tem seu próprio destino de renderização (buffer de fundo) e matrizes de exibição e projeção no espaço Holographic. Seu aplicativo precisará criar outros recursos baseados em câmera, como o buffer de profundidade, por câmera. no modelo de aplicativo Windows Holographic, fornecemos uma classe auxiliar para agrupar esses recursos em DX:: CameraResources. Comece configurando as exibições de destino de renderização:

De **AppMain:: render**:

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

**Usar a previsão para obter as matrizes de exibição e projeção da câmera**

As matrizes de exibição e projeção para cada câmera Holographic serão alteradas em todos os quadros. Atualize os dados no buffer de constantes para cada câmera Holographic. Faça isso depois de atualizar a previsão e antes de fazer qualquer chamada de desenho para essa câmera.

De **AppMain:: render**:

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

Aqui, mostramos como as matrizes são adquiridas da pose da câmera. Durante esse processo, também obtemos o visor atual para a câmera. Observe como fornecemos um sistema de coordenadas: esse é o mesmo sistema de coordenadas que usamos para entender olhar e é o mesmo que usamos para posicionar o cubo girando.


De **CameraResources:: UpdateViewProjectionBuffer**:

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

O visor deve ser definido em cada quadro. Seu sombreador de vértice (pelo menos) geralmente precisará de acesso aos dados de exibição/projeção.


De **CameraResources:: AttachViewProjectionBuffer**:

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

**Renderizar para o buffer de fundo da câmera e confirmar o buffer de profundidade**:

É uma boa ideia verificar se **TryGetViewTransform** foi bem-sucedido antes de tentar usar os dados de exibição/projeção, porque se o sistema de coordenadas não for localizado (por exemplo, o acompanhamento foi interrompido), seu aplicativo não poderá renderizar com ele para esse quadro. O modelo só **chamará Render** no cubo giratório se a **classe CameraResources** indicar uma atualização bem-sucedida.

Windows Mixed Reality inclui recursos para [estabilização](../platform-capabilities-and-apis/hologram-stability.md) de imagem para manter os hologramas posicionados em que um desenvolvedor ou usuário os coloca no mundo. A estabilização de imagem ajuda a ocultar a latência inerente em um pipeline de renderização para garantir as melhores experiências holográficas para os usuários. Um ponto de foco pode ser especificado para aprimorar ainda mais a estabilização da imagem ou um buffer de profundidade pode ser fornecido para calcular a estabilização otimizada da imagem em tempo real.

Para melhores resultados, seu aplicativo deve fornecer um buffer de profundidade usando a API <a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer.</a> Windows Mixed Reality pode usar informações de geometria do buffer de profundidade para otimizar a estabilização da imagem em tempo real. O Windows modelo holográfico confirma o buffer de profundidade do aplicativo por padrão, ajudando a otimizar a estabilidade do holograma.

De **AppMain::Render**:

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
>Windows processará a textura de profundidade na GPU, portanto, deve ser possível usar o buffer de profundidade como um recurso de sombreador. O ID3D11Texture2D que você cria deve estar em um formato sem tipo e deve ser vinculado como uma exibição de recurso de sombreador. Aqui está um exemplo de como criar uma textura de profundidade que pode ser comprometida para estabilização de imagem.

Código para **criação de recursos de buffer de profundidade para CommitDirect3D11DepthBuffer:**

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

**Desenhar conteúdo holográfico**

O Windows modelo de aplicativo Holographic renderiza o conteúdo em estéreo usando a técnica recomendada de desenhar geometria em instâncias em uma Texture2DArray de tamanho 2. Vamos dar uma olhada na parte de instanciamento disso e como ela funciona Windows Mixed Reality.

De **SpinningCubeRenderer::Render:**

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

Cada instância acessa uma matriz de exibição/projeção diferente do buffer constante. Esta é a estrutura de buffer constante, que é apenas uma matriz de duas matrizes.

De **VertexShaderShared.hlsl**, incluído por **VPRTVertexShader.hlsl**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

O índice da matriz de destino de renderização deve ser definido para cada pixel. No snippet de código a seguir, output.viewId é mapeado para a **semântica SV_RenderTargetArrayIndex** dados. Isso requer suporte para um recurso opcional do Direct3D 11.3, que permite que a semântica de índice da matriz de destino de renderização seja definida de qualquer estágio do sombreador.

De **VPRTVertexShader.hlsl**:

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

De **VertexShaderShared.hlsl**, incluído por **VPRTVertexShader.hlsl**:

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

Se você quiser usar suas técnicas de desenho em instâncias existentes com esse método de desenho para uma matriz de destino de renderização estéreo, desenhe duas vezes o número de instâncias que você normalmente tem. No sombreador, divida **input.instId** por 2 para obter a ID da instância original, que pode ser indexada em (por exemplo) um buffer de dados por objeto: `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>Observação importante sobre a renderização de conteúdo estéreo HoloLens

Windows Mixed Reality dá suporte à capacidade de definir o índice da matriz de destino de renderização de qualquer estágio do sombreador. Normalmente, essa é uma tarefa que só poderia ser feita no estágio do sombreador de geometria devido à maneira como a semântica é definida para o Direct3D 11. Aqui, mostramos um exemplo completo de como configurar um pipeline de renderização com apenas os estágios de sombreador de vértice e pixel definidos. O código do sombreador é conforme descrito acima.

De **SpinningCubeRenderer::Render:**

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>Observação importante sobre a renderização em dispositivos HoloLens não conectados

Definir o índice da matriz de destino de renderização no sombreador de vértice requer que o driver gráfico seja compatível com um recurso opcional do Direct3D 11.3, que HoloLens dá suporte. Seu aplicativo pode implementar com segurança apenas essa técnica para renderização e todos os requisitos serão atendidos para execução no Microsoft HoloLens.

Pode ser o caso em que você também deseja usar o emulador HoloLens, que pode ser uma ferramenta de desenvolvimento poderosa para seu aplicativo Windows Mixed Reality holográfico e dar suporte a dispositivos de headset imersivos que estão anexados a PCs Windows 10. O suporte para o caminho de renderização HoloLens não HoloLens , para todos os Windows Mixed Reality, também é integrado ao modelo de aplicativo Windows Holographic. No código do modelo, você encontrará código para permitir que seu aplicativo holográfico seja executado na GPU em seu computador de desenvolvimento. Veja como a classe **DeviceResources** verifica se há suporte para esse recurso opcional.

De **DeviceResources::CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

Para dar suporte à renderização sem esse recurso opcional, seu aplicativo deve usar um sombreador de geometria para definir o índice da matriz de destino de renderização. Esse snippet seria  adicionado após **VSSetConstantBuffers** e antes de  **PSSetShader** no exemplo de código mostrado na seção anterior que explica como renderizar estéreo em HoloLens.

De **SpinningCubeRenderer::Render:**

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

**HLSL OBSERVAÇÃO:** nesse caso, você também deve carregar um sombreador de vértice ligeiramente modificado que passa o índice da matriz de destino de renderização para o sombreador de geometria usando uma semântica de sombreador sempre permitida, como TEXCOORD0. O sombreador de geometria não precisa fazer nenhum trabalho; o sombreador de geometria do modelo passa por todos os dados, com exceção do índice da matriz de destino de renderização, que é usado para definir a semântica SV_RenderTargetArrayIndex dados.

Código do modelo de aplicativo **para GeometryShader.hlsl**:

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint instId         : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint rtvId          : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a>Presente

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>Habilitar o quadro holográfico para apresentar a cadeia de permuta

Com Windows Mixed Reality, o sistema controla a cadeia de permuta. Em seguida, o sistema gerencia a apresentação de quadros para cada câmera holográfica para garantir uma experiência do usuário de alta qualidade. Ele também fornece uma atualização de viewport de cada quadro, para cada câmera, para otimizar aspectos do sistema, como estabilização de imagem ou Captura de Realidade Misturada. Portanto, um aplicativo holográfico usando o DirectX não chama **Present em** uma cadeia de permuta DXGI. Em vez disso, você usa a <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">classe HolographicFrame</a> para apresentar todas as swapchains para um quadro quando terminar de desenhá-lo.

De **DeviceResources::P resent:**

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

Por padrão, essa API aguarda a finalização do quadro antes de ser retornada. Os aplicativos holográficos devem aguardar a finalização do quadro anterior antes de iniciar o trabalho em um novo quadro, pois isso reduz a latência e permite melhores resultados de previsões de quadro holográfico. Essa não é uma regra difícil e, se você tiver quadros que levam mais de uma atualização de tela para renderizar, poderá desabilitar essa espera passando o parâmetro HolographicFramePresentWaitBehavior para <a href="/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>. Nesse caso, você provavelmente usaria um thread de renderização assíncrona para manter uma carga contínua na GPU. A taxa de atualização do HoloLens dispositivo é de 60 hz, em que um quadro tem uma duração de aproximadamente 16 ms. Os dispositivos de headset imersivo podem variar de 60 hz a 90 hz; Ao atualizar a exibição em 90 hz, cada quadro terá uma duração de aproximadamente 11 ms.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>Manipular cenários deviceLost em cooperação com o HolographicFrame

Os aplicativos DirectX 11 normalmente querem verificar o HRESULT retornado  pela função Present da cadeia de permuta DXGI para descobrir se houve um erro **DeviceLost.** A <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">classe HolographicFrame</a> lida com isso para você. Inspecione <a href="/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">o HolographicFramePresentResult</a> retornado para descobrir se você precisa liberar e recriar os recursos baseados em dispositivo e dispositivo do Direct3D.

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

Se o dispositivo Direct3D foi perdido e você o recriou, você precisa dizer ao <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> para começar a usar o novo dispositivo. A cadeia de permuta será recriada para esse dispositivo.

De **DeviceResources::InitializeUsingHolographicSpace:**

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

Depois que o quadro for apresentado, você poderá retornar ao loop do programa principal e permitir que ele continue para o próximo quadro.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>PCs gráficos híbridos e aplicativos de realidade misturada

Atualização do Windows 10 para Criadores Os PCs podem ser **configurados** com GPUs discretas e integradas. Com esses tipos de computadores, Windows escolherá o adaptador ao qual o headset está conectado. Os aplicativos devem garantir que o dispositivo DirectX que ele cria use o mesmo adaptador.

O código de exemplo mais geral do Direct3D demonstra a criação de um dispositivo DirectX usando o adaptador de hardware padrão, que em um sistema híbrido pode não ser o mesmo usado para o headset.

Para resolver problemas, use <a href="/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">o HolographicAdapterID</a> do <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace.</a> PrimaryAdapterId() ou <a href="/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay.</a> AdapterId(). Essa adapterId pode ser usada para selecionar o DXGIAdapter correto usando IDXGIFactory4.EnumAdapterByLuid.

De **DeviceResources::InitializeUsingHolographicSpace:**

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

Código para **atualizar DeviceResources::CreateDeviceResources para usar IDXGIAdapter**

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

**Gráficos híbridos e Media Foundation**

Usar Media Foundation em sistemas híbridos pode causar problemas em que o vídeo não renderizará ou a textura do vídeo está corrompida porque Media Foundation padrão é um comportamento do sistema. Em alguns cenários, a criação de um ID3D11Device separado é necessária para dar suporte a vários threads e os sinalizadores de criação corretos são definidos.

Ao inicializar o ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT sinalizador deve ser definido como parte do D3D11_CREATE_DEVICE_FLAG. Depois que o dispositivo e o contexto são criados, chame <a href="/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> para habilitar multithreading. Para associar o dispositivo ao <a href="/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager,</a>use a função <a href="/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice.</a>

Código para **associar um ID3D11Device a IMFDXGIDeviceManager:**

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a>Confira também
* [Sistemas de coordenadas no DirectX](coordinate-systems-in-directx.md)
* [Usando o emulador do HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)