---
title: Como renderizar no DirectX
description: Explica o processamento de Holographic para a realidade mista do Windows.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Realidade mista do Windows, hologramas, renderização, gráficos 3D, HolographicFrame, loop de processamento, loop de atualização, passo a passos, código de exemplo, Direct3D
ms.openlocfilehash: 90d665e8054a185969a95e6ff6415979e728e9ab
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613180"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="75a2a-104">Como renderizar no DirectX</span><span class="sxs-lookup"><span data-stu-id="75a2a-104">Rendering in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="75a2a-105">Este artigo está relacionado às APIs nativas do WinRT herdadas.</span><span class="sxs-lookup"><span data-stu-id="75a2a-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="75a2a-106">Para novos projetos de aplicativos nativos, é recomendável usar a **[API OpenXR](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="75a2a-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="75a2a-107">A realidade mista do Windows se baseia no DirectX para produzir experiências gráficas 3D ricas para os usuários.</span><span class="sxs-lookup"><span data-stu-id="75a2a-107">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="75a2a-108">A abstração de renderização fica logo acima do DirectX, que permite que os aplicativos se deparam com a posição e a orientação dos observadores de cena de Holographic previstos pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="75a2a-108">The rendering abstraction sits just above DirectX, which lets apps reason about the position and orientation of holographic scene observers predicted by the system.</span></span> <span data-ttu-id="75a2a-109">O desenvolvedor pode então localizar seus hologramas com base em cada câmera, permitindo que o aplicativo processe esses hologramas em vários sistemas de coordenadas espaciais à medida que o usuário se movimenta.</span><span class="sxs-lookup"><span data-stu-id="75a2a-109">The developer can then locate their holograms based on each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

<span data-ttu-id="75a2a-110">Observação: este passo a passos descreve a renderização Holographic no Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="75a2a-110">Note: This walkthrough describes holographic rendering in Direct3D 11.</span></span> <span data-ttu-id="75a2a-111">Um modelo de aplicativo de realidade misturada do Windows do Direct3D 12 também é fornecido com a extensão de modelos de aplicativo da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="75a2a-111">A Direct3D 12 Windows Mixed Reality app template is also supplied with the Mixed Reality app templates extension.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="75a2a-112">Atualizar para o quadro atual</span><span class="sxs-lookup"><span data-stu-id="75a2a-112">Update for the current frame</span></span>

<span data-ttu-id="75a2a-113">Para atualizar o estado do aplicativo para hologramas, uma vez por quadro, o aplicativo irá:</span><span class="sxs-lookup"><span data-stu-id="75a2a-113">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="75a2a-114">Obtenha um <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> do sistema de gerenciamento de vídeo.</span><span class="sxs-lookup"><span data-stu-id="75a2a-114">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="75a2a-115">Atualize a cena com a previsão atual de onde a exibição da câmera será quando o processamento for concluído.</span><span class="sxs-lookup"><span data-stu-id="75a2a-115">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="75a2a-116">Observe que pode haver mais de uma câmera para a cena Holographic.</span><span class="sxs-lookup"><span data-stu-id="75a2a-116">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="75a2a-117">Para renderizar para exibições de câmera Holographic, uma vez por quadro, o aplicativo irá:</span><span class="sxs-lookup"><span data-stu-id="75a2a-117">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="75a2a-118">Para cada câmera, processe a cena para o quadro atual, usando a exibição de câmera e as matrizes de projeção do sistema.</span><span class="sxs-lookup"><span data-stu-id="75a2a-118">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="75a2a-119">Criar um novo quadro do Holographic e obter sua previsão</span><span class="sxs-lookup"><span data-stu-id="75a2a-119">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="75a2a-120">O <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> tem informações que o aplicativo precisa para atualizar e renderizar o quadro atual.</span><span class="sxs-lookup"><span data-stu-id="75a2a-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs to update and render the current frame.</span></span> <span data-ttu-id="75a2a-121">O aplicativo começa cada novo quadro chamando o método **CreateNextFrame** .</span><span class="sxs-lookup"><span data-stu-id="75a2a-121">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="75a2a-122">Quando esse método é chamado, as previsões são feitas usando os dados de sensor mais recentes disponíveis e encapsuladas no objeto **CurrentPrediction** .</span><span class="sxs-lookup"><span data-stu-id="75a2a-122">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="75a2a-123">Um novo objeto de quadro deve ser usado para cada quadro renderizado, pois ele só é válido para um instante no tempo.</span><span class="sxs-lookup"><span data-stu-id="75a2a-123">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="75a2a-124">A propriedade **CurrentPrediction** contém informações como a posição da câmera.</span><span class="sxs-lookup"><span data-stu-id="75a2a-124">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="75a2a-125">As informações são extrapoladas para o momento exato no momento em que o quadro deve ficar visível para o usuário.</span><span class="sxs-lookup"><span data-stu-id="75a2a-125">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="75a2a-126">O código a seguir é extraído de **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-126">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="75a2a-127">Processar atualizações da câmera</span><span class="sxs-lookup"><span data-stu-id="75a2a-127">Process camera updates</span></span>

<span data-ttu-id="75a2a-128">Buffers de fundo podem mudar de quadro para quadro.</span><span class="sxs-lookup"><span data-stu-id="75a2a-128">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="75a2a-129">Seu aplicativo precisa validar o buffer de fundo para cada câmera e liberar e recriar exibições de recursos e buffers de profundidade, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="75a2a-129">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="75a2a-130">Observe que o conjunto de poses na previsão é a lista autoritativa de câmeras que estão sendo usadas no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="75a2a-130">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="75a2a-131">Normalmente, você usa essa lista para iterar no conjunto de câmeras.</span><span class="sxs-lookup"><span data-stu-id="75a2a-131">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="75a2a-132">De **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-132">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="75a2a-133">De **DeviceResources:: EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-133">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="75a2a-134">Obter o sistema de coordenadas para usar como base para renderização</span><span class="sxs-lookup"><span data-stu-id="75a2a-134">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="75a2a-135">A realidade mista do Windows permite que seu aplicativo crie vários [sistemas de coordenadas](coordinate-systems-in-directx.md), como quadros de referência anexados e estáticos para rastrear locais no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="75a2a-135">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md), like attached and stationary reference frames for tracking locations in the physical world.</span></span> <span data-ttu-id="75a2a-136">Seu aplicativo pode, então, usar esses sistemas de coordenadas para saber por onde renderizar os hologramas em cada quadro.</span><span class="sxs-lookup"><span data-stu-id="75a2a-136">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="75a2a-137">Ao solicitar coordenadas de uma API, você sempre passará o <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> dentro do qual deseja que essas coordenadas sejam expressas.</span><span class="sxs-lookup"><span data-stu-id="75a2a-137">When requesting coordinates from an API, you'll always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="75a2a-138">De **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-138">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="75a2a-139">Esses sistemas de coordenadas podem ser usados para gerar matrizes de exibição de estéreo ao renderizar o conteúdo em sua cena.</span><span class="sxs-lookup"><span data-stu-id="75a2a-139">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="75a2a-140">De **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-140">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="75a2a-141">Olhar de processo e entrada de gesto</span><span class="sxs-lookup"><span data-stu-id="75a2a-141">Process gaze and gesture input</span></span>

<span data-ttu-id="75a2a-142">A entrada [olhar](gaze-in-directx.md) e [Hand](hands-and-motion-controllers-in-directx.md) não são baseadas em tempo e não precisam ser atualizadas na função **StepTimer** .</span><span class="sxs-lookup"><span data-stu-id="75a2a-142">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input aren't time-based and don't have to update in the **StepTimer** function.</span></span> <span data-ttu-id="75a2a-143">No entanto, essa entrada é algo que o aplicativo precisa para examinar cada quadro.</span><span class="sxs-lookup"><span data-stu-id="75a2a-143">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="75a2a-144">Processar atualizações baseadas em tempo</span><span class="sxs-lookup"><span data-stu-id="75a2a-144">Process time-based updates</span></span>

<span data-ttu-id="75a2a-145">Qualquer aplicativo de renderização em tempo real precisará de alguma maneira de processar atualizações baseadas em tempo – o modelo de aplicativo Holographic do Windows usa uma implementação **StepTimer** , semelhante à StepTimer fornecida no modelo de aplicativo UWP DirectX 11.</span><span class="sxs-lookup"><span data-stu-id="75a2a-145">Any real-time rendering app will need some way to process time-based updates - the Windows Holographic app template uses a **StepTimer** implementation, similar to the StepTimer provided in the DirectX 11 UWP app template.</span></span> <span data-ttu-id="75a2a-146">Esta classe auxiliar de exemplo StepTimer pode fornecer atualizações de etapa de tempo fixas, atualizações de etapa de tempo variável e o modo padrão são etapas de tempo variável.</span><span class="sxs-lookup"><span data-stu-id="75a2a-146">This StepTimer sample helper class can provide fixed time-step updates, variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="75a2a-147">Para a renderização de Holographic, escolhemos não colocar muito na função de temporizador porque você pode configurá-la para ser uma etapa de tempo fixa.</span><span class="sxs-lookup"><span data-stu-id="75a2a-147">For holographic rendering, we've chosen not to put too much into the timer function because you can configure it to be a fixed time step.</span></span> <span data-ttu-id="75a2a-148">Ele pode ser chamado mais de uma vez por quadro – ou não, para alguns quadros – e nossas atualizações de dados Holographic devem ocorrer uma vez por quadro.</span><span class="sxs-lookup"><span data-stu-id="75a2a-148">It might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="75a2a-149">De **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-149">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="75a2a-150">Posicionar e girar os hologramas em seu sistema de coordenadas</span><span class="sxs-lookup"><span data-stu-id="75a2a-150">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="75a2a-151">Se você estiver operando em um único sistema de coordenadas, como o modelo faz com o **SpatialStationaryReferenceFrame**, esse processo não é diferente do que é usado de outra forma em gráficos 3D.</span><span class="sxs-lookup"><span data-stu-id="75a2a-151">If you're operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="75a2a-152">Aqui, giramos o cubo e definimos a matriz do modelo com base na posição no sistema de coordenadas do imóvel.</span><span class="sxs-lookup"><span data-stu-id="75a2a-152">Here, we rotate the cube and set the model matrix based on the position in the stationary coordinate system.</span></span>

<span data-ttu-id="75a2a-153">De **SpinningCubeRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-153">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="75a2a-154">**Observação sobre cenários avançados:** O cubo girando é um exemplo simples de como posicionar um holograma em um único quadro de referência.</span><span class="sxs-lookup"><span data-stu-id="75a2a-154">**Note about advanced scenarios:** The spinning cube is a simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="75a2a-155">Também é possível [usar vários SpatialCoordinateSystems](coordinate-systems-in-directx.md) no mesmo quadro renderizado, ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="75a2a-155">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="75a2a-156">Atualizar dados de buffer constante</span><span class="sxs-lookup"><span data-stu-id="75a2a-156">Update constant buffer data</span></span>

<span data-ttu-id="75a2a-157">As transformações de modelo para conteúdo são atualizadas como de costume.</span><span class="sxs-lookup"><span data-stu-id="75a2a-157">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="75a2a-158">Agora, você terá transformações válidas computadas para o sistema de coordenadas em que será renderizado.</span><span class="sxs-lookup"><span data-stu-id="75a2a-158">By now, you'll have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="75a2a-159">De **SpinningCubeRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-159">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="75a2a-160">E quanto às transformações de exibição e projeção?</span><span class="sxs-lookup"><span data-stu-id="75a2a-160">What about view and projection transforms?</span></span> <span data-ttu-id="75a2a-161">Para obter melhores resultados, queremos esperar até que esteja quase pronto para nossas chamadas de desenho antes de obtê-las.</span><span class="sxs-lookup"><span data-stu-id="75a2a-161">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="75a2a-162">Renderizar o quadro atual</span><span class="sxs-lookup"><span data-stu-id="75a2a-162">Render the current frame</span></span>

<span data-ttu-id="75a2a-163">A renderização na realidade mista do Windows não é muito diferente da renderização em uma exibição mono 2D, mas há algumas diferenças:</span><span class="sxs-lookup"><span data-stu-id="75a2a-163">Rendering on Windows Mixed Reality isn't much different from rendering on a 2D mono display, but there are a few differences:</span></span>
* <span data-ttu-id="75a2a-164">As previsões de quadros Holographic são importantes.</span><span class="sxs-lookup"><span data-stu-id="75a2a-164">Holographic frame predictions are important.</span></span> <span data-ttu-id="75a2a-165">Quanto mais próximo a previsão for quando seu quadro for apresentado, melhor será o seu holograma.</span><span class="sxs-lookup"><span data-stu-id="75a2a-165">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="75a2a-166">A realidade mista do Windows controla as exibições da câmera.</span><span class="sxs-lookup"><span data-stu-id="75a2a-166">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="75a2a-167">Renderize para cada um porque o quadro Holographic será apresentado para você posteriormente.</span><span class="sxs-lookup"><span data-stu-id="75a2a-167">Render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="75a2a-168">É recomendável fazer a renderização de estéreo usando o desenho em instância para uma matriz de destino de renderização.</span><span class="sxs-lookup"><span data-stu-id="75a2a-168">We recommend doing stereo rendering using instanced drawing to a render target array.</span></span> <span data-ttu-id="75a2a-169">O modelo de aplicativo Holographic usa a abordagem recomendada de desenho em instância para uma matriz de destino de renderização, que usa uma exibição de destino de renderização em um **Texture2DArray**.</span><span class="sxs-lookup"><span data-stu-id="75a2a-169">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="75a2a-170">Se você quiser renderizar sem usar a instanciação de estéreo, será necessário criar duas RenderTargetViews não matrizes, uma para cada olho.</span><span class="sxs-lookup"><span data-stu-id="75a2a-170">If you want to render without using stereo instancing, you'll need to create two non-array RenderTargetViews, one for each eye.</span></span> <span data-ttu-id="75a2a-171">Cada RenderTargetViews faz referência a uma das duas fatias no **Texture2DArray** fornecido ao aplicativo do sistema.</span><span class="sxs-lookup"><span data-stu-id="75a2a-171">Each RenderTargetViews references one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="75a2a-172">Isso não é recomendado, pois normalmente é mais lento do que usar a instanciação.</span><span class="sxs-lookup"><span data-stu-id="75a2a-172">This isn't recommended, as it's typically slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="75a2a-173">Obter uma previsão HolographicFrame atualizada</span><span class="sxs-lookup"><span data-stu-id="75a2a-173">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="75a2a-174">A atualização da previsão de quadros melhora a eficácia da estabilização da imagem.</span><span class="sxs-lookup"><span data-stu-id="75a2a-174">Updating the frame prediction enhances the effectiveness of image stabilization.</span></span> <span data-ttu-id="75a2a-175">Você Obtém um posicionamento mais preciso de hologramas devido ao tempo mais curto entre a previsão e quando o quadro fica visível para o usuário.</span><span class="sxs-lookup"><span data-stu-id="75a2a-175">You get more accurate positioning of holograms because of the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="75a2a-176">Idealmente, atualize sua previsão de quadros logo antes da renderização.</span><span class="sxs-lookup"><span data-stu-id="75a2a-176">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="75a2a-177">Renderizar para cada câmera</span><span class="sxs-lookup"><span data-stu-id="75a2a-177">Render to each camera</span></span>

<span data-ttu-id="75a2a-178">O loop no conjunto da câmera representa a previsão e renderizado para cada câmera nesse conjunto.</span><span class="sxs-lookup"><span data-stu-id="75a2a-178">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="75a2a-179">**Configurar sua passagem de renderização**</span><span class="sxs-lookup"><span data-stu-id="75a2a-179">**Set up your rendering pass**</span></span>

<span data-ttu-id="75a2a-180">A realidade mista do Windows usa a renderização estereoscópico para aprimorar a ilusão de profundidade e para renderizar stereoscopically, para que ambas as exibições à esquerda e à direita estejam ativas.</span><span class="sxs-lookup"><span data-stu-id="75a2a-180">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="75a2a-181">Com a renderização estereoscópico, há um deslocamento entre as duas exibições, que o cérebro pode reconciliar como profundidade real.</span><span class="sxs-lookup"><span data-stu-id="75a2a-181">With stereoscopic rendering, there's an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="75a2a-182">Esta seção aborda a renderização de estereoscópico usando a instanciação, usando código do modelo de aplicativo do Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="75a2a-182">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="75a2a-183">Cada câmera tem seu próprio destino de renderização (buffer de fundo) e matrizes de exibição e projeção no espaço Holographic.</span><span class="sxs-lookup"><span data-stu-id="75a2a-183">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="75a2a-184">Seu aplicativo precisará criar outros recursos baseados em câmera, como o buffer de profundidade, por câmera.</span><span class="sxs-lookup"><span data-stu-id="75a2a-184">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="75a2a-185">No modelo de aplicativo Holographic do Windows, fornecemos uma classe auxiliar para agrupar esses recursos em DX:: CameraResources.</span><span class="sxs-lookup"><span data-stu-id="75a2a-185">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="75a2a-186">Comece configurando as exibições de destino de renderização:</span><span class="sxs-lookup"><span data-stu-id="75a2a-186">Start by setting up the render target views:</span></span>

<span data-ttu-id="75a2a-187">De **AppMain:: render**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-187">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="75a2a-188">**Usar a previsão para obter as matrizes de exibição e projeção da câmera**</span><span class="sxs-lookup"><span data-stu-id="75a2a-188">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="75a2a-189">As matrizes de exibição e projeção para cada câmera Holographic serão alteradas em todos os quadros.</span><span class="sxs-lookup"><span data-stu-id="75a2a-189">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="75a2a-190">Atualize os dados no buffer de constantes para cada câmera Holographic.</span><span class="sxs-lookup"><span data-stu-id="75a2a-190">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="75a2a-191">Faça isso depois de atualizar a previsão e antes de fazer qualquer chamada de desenho para essa câmera.</span><span class="sxs-lookup"><span data-stu-id="75a2a-191">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="75a2a-192">De **AppMain:: render**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-192">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="75a2a-193">Aqui, mostramos como as matrizes são adquiridas da pose da câmera.</span><span class="sxs-lookup"><span data-stu-id="75a2a-193">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="75a2a-194">Durante esse processo, também obtemos o visor atual para a câmera.</span><span class="sxs-lookup"><span data-stu-id="75a2a-194">During this process, we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="75a2a-195">Observe como fornecemos um sistema de coordenadas: esse é o mesmo sistema de coordenadas que usamos para entender olhar e é o mesmo que usamos para posicionar o cubo girando.</span><span class="sxs-lookup"><span data-stu-id="75a2a-195">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="75a2a-196">De **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-196">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="75a2a-197">O visor deve ser definido em cada quadro.</span><span class="sxs-lookup"><span data-stu-id="75a2a-197">The viewport should be set each frame.</span></span> <span data-ttu-id="75a2a-198">Seu sombreador de vértice (pelo menos) geralmente precisará de acesso aos dados de exibição/projeção.</span><span class="sxs-lookup"><span data-stu-id="75a2a-198">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="75a2a-199">De **CameraResources:: AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-199">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="75a2a-200">**Renderizar para o buffer de fundo da câmera e confirmar o buffer de profundidade**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-200">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="75a2a-201">É uma boa ideia verificar se o **TryGetViewTransform** foi bem-sucedido antes de tentar usar os dados de exibição/projeção, porque se o sistema de coordenadas não for localizável (por exemplo, o controle foi interrompido), seu aplicativo não poderá renderizar com ele para esse quadro.</span><span class="sxs-lookup"><span data-stu-id="75a2a-201">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system isn't locatable (for example, tracking was interrupted) your app can't render with it for that frame.</span></span> <span data-ttu-id="75a2a-202">O modelo só chamará **render** no cubo girando se a classe **CameraResources** indicar uma atualização bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="75a2a-202">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="75a2a-203">O Windows Mixed Reality inclui recursos para [estabilização de imagem](../platform-capabilities-and-apis/hologram-stability.md) para manter os hologramas posicionados onde um desenvolvedor ou usuário os coloca no mundo.</span><span class="sxs-lookup"><span data-stu-id="75a2a-203">Windows Mixed Reality includes features for [image stabilization](../platform-capabilities-and-apis/hologram-stability.md) to keep holograms positioned where a developer or user puts them in the world.</span></span> <span data-ttu-id="75a2a-204">A estabilização de imagem ajuda a ocultar a latência inerente em um pipeline de renderização para garantir as melhores experiências de Holographic para os usuários.</span><span class="sxs-lookup"><span data-stu-id="75a2a-204">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users.</span></span> <span data-ttu-id="75a2a-205">Um ponto de foco pode ser especificado para aprimorar ainda mais a estabilização de imagem ou um buffer de profundidade pode ser fornecido para computar a estabilização de imagem otimizada em tempo real.</span><span class="sxs-lookup"><span data-stu-id="75a2a-205">A focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="75a2a-206">Para obter melhores resultados, seu aplicativo deve fornecer um buffer de profundidade usando a API <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> .</span><span class="sxs-lookup"><span data-stu-id="75a2a-206">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="75a2a-207">A realidade mista do Windows pode usar informações de geometria do buffer de profundidade para otimizar a estabilização de imagem em tempo real.</span><span class="sxs-lookup"><span data-stu-id="75a2a-207">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="75a2a-208">O modelo de aplicativo Holographic do Windows confirma o buffer de profundidade do aplicativo por padrão, ajudando a otimizar a estabilidade do holograma.</span><span class="sxs-lookup"><span data-stu-id="75a2a-208">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="75a2a-209">De **AppMain:: render**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-209">From **AppMain::Render**:</span></span>

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
><span data-ttu-id="75a2a-210">O Windows processará sua textura de profundidade na GPU, portanto, deve ser possível usar o buffer de profundidade como um recurso de sombreador.</span><span class="sxs-lookup"><span data-stu-id="75a2a-210">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="75a2a-211">O ID3D11Texture2D que você cria deve estar em um formato sem tipo e deve ser associado como um modo de exibição de recurso de sombreador.</span><span class="sxs-lookup"><span data-stu-id="75a2a-211">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="75a2a-212">Aqui está um exemplo de como criar uma textura de profundidade que pode ser confirmada para estabilização de imagem.</span><span class="sxs-lookup"><span data-stu-id="75a2a-212">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="75a2a-213">Código para a **criação de recursos de buffer de profundidade para CommitDirect3D11DepthBuffer**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-213">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

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

<span data-ttu-id="75a2a-214">**Desenhar conteúdo do Holographic**</span><span class="sxs-lookup"><span data-stu-id="75a2a-214">**Draw holographic content**</span></span>

<span data-ttu-id="75a2a-215">O modelo de aplicativo Holographic do Windows renderiza o conteúdo em estéreo usando a técnica recomendada de desenho de geometria de instância para um Texture2DArray de tamanho 2.</span><span class="sxs-lookup"><span data-stu-id="75a2a-215">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="75a2a-216">Vamos examinar a parte de instanciação disso e como ela funciona no Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="75a2a-216">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="75a2a-217">De **SpinningCubeRenderer:: render**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-217">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="75a2a-218">Cada instância acessa uma matriz de exibição/projeção diferente do buffer de constantes.</span><span class="sxs-lookup"><span data-stu-id="75a2a-218">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="75a2a-219">Aqui está a estrutura de buffer constante, que é apenas uma matriz de duas matrizes.</span><span class="sxs-lookup"><span data-stu-id="75a2a-219">Here's the constant buffer structure, which is just an array of two matrices.</span></span>

<span data-ttu-id="75a2a-220">De **VertexShaderShared. HLSL**, incluído por **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-220">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="75a2a-221">O índice de matriz de destino de renderização deve ser definido para cada pixel.</span><span class="sxs-lookup"><span data-stu-id="75a2a-221">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="75a2a-222">No trecho a seguir, output. ViewId é mapeado para a semântica de **SV_RenderTargetArrayIndex** .</span><span class="sxs-lookup"><span data-stu-id="75a2a-222">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="75a2a-223">Isso requer suporte para um recurso de Direct3D 11,3 opcional, que permite que a semântica de índice de matriz de destino de renderização seja definida em qualquer estágio do sombreador.</span><span class="sxs-lookup"><span data-stu-id="75a2a-223">This requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="75a2a-224">De **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-224">From **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="75a2a-225">De **VertexShaderShared. HLSL**, incluído por **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-225">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="75a2a-226">Se você quiser usar suas técnicas de desenho com instância existente com esse método de desenho em uma matriz de destino de renderização estéreo, desenhe duas vezes o número de instâncias que você normalmente tem.</span><span class="sxs-lookup"><span data-stu-id="75a2a-226">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, draw twice the number of instances you normally have.</span></span> <span data-ttu-id="75a2a-227">No sombreador, divida **Input. Instid** por 2 para obter a ID da instância original, que pode ser indexada em (por exemplo) um buffer de dados por objeto: `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="75a2a-227">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="75a2a-228">Observação importante sobre o processamento de conteúdo estéreo no HoloLens</span><span class="sxs-lookup"><span data-stu-id="75a2a-228">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="75a2a-229">O Windows Mixed Reality dá suporte à capacidade de definir o índice de matriz de destino de renderização de qualquer estágio do sombreador.</span><span class="sxs-lookup"><span data-stu-id="75a2a-229">Windows Mixed Reality supports the ability to set the render target array index from any shader stage.</span></span> <span data-ttu-id="75a2a-230">Normalmente, essa é uma tarefa que pode ser feita apenas no estágio do sombreador Geometry devido à maneira como a semântica é definida para o Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="75a2a-230">Normally, this is a task that could only be done in the geometry shader stage because of the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="75a2a-231">Aqui, mostramos um exemplo completo de como configurar um pipeline de renderização apenas com os estágios do vértice e do sombreador de pixel definidos.</span><span class="sxs-lookup"><span data-stu-id="75a2a-231">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="75a2a-232">O código do sombreador é conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="75a2a-232">The shader code is as described above.</span></span>

<span data-ttu-id="75a2a-233">De **SpinningCubeRenderer:: render**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-233">From **SpinningCubeRenderer::Render**:</span></span>

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="75a2a-234">Observação importante sobre a renderização em dispositivos não HoloLens</span><span class="sxs-lookup"><span data-stu-id="75a2a-234">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="75a2a-235">Definir o índice de matriz de destino de renderização no sombreador de vértice requer que o driver de gráficos dê suporte a um recurso de Direct3D 11,3 opcional, ao qual o HoloLens oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="75a2a-235">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="75a2a-236">Seu aplicativo pode implementar com segurança apenas essa técnica para renderização e todos os requisitos serão atendidos para execução no Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="75a2a-236">Your app may can safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="75a2a-237">Pode ser o caso em que você também deseja usar o emulador do HoloLens, que pode ser uma poderosa ferramenta de desenvolvimento para seu aplicativo Holographic e dar suporte a dispositivos de headset de imersão de realidade mista do Windows que estão conectados a PCs com Windows 10.</span><span class="sxs-lookup"><span data-stu-id="75a2a-237">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="75a2a-238">O suporte para o caminho de renderização não HoloLens-para toda a realidade mista do Windows – também é incorporado ao modelo de aplicativo Holographic do Windows.</span><span class="sxs-lookup"><span data-stu-id="75a2a-238">Support for the non-HoloLens rendering path - for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="75a2a-239">No código do modelo, você encontrará código para permitir que seu aplicativo Holographic seja executado na GPU em seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="75a2a-239">In the template code, you'll find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="75a2a-240">Veja como a classe **DeviceResources** verifica esse suporte de recurso opcional.</span><span class="sxs-lookup"><span data-stu-id="75a2a-240">Here's how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="75a2a-241">De **DeviceResources:: CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-241">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="75a2a-242">Para dar suporte à renderização sem esse recurso opcional, seu aplicativo deve usar um sombreador de geometria para definir o índice de matriz de destino de renderização.</span><span class="sxs-lookup"><span data-stu-id="75a2a-242">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="75a2a-243">Esse trecho de código seria adicionado *após* **VSSetConstantBuffers**, e *antes* de **PSSetShader** no exemplo de códigos mostrado na seção anterior que explica como renderizar o estéreo no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="75a2a-243">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="75a2a-244">De **SpinningCubeRenderer:: render**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-244">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="75a2a-245">**HLSL observação**: nesse caso, você também deve carregar um sombreador de vértice ligeiramente modificado que passa o índice de matriz de destino de renderização para o sombreador de geometria usando uma semântica de sombreador sempre permitido, como TEXCOORD0.</span><span class="sxs-lookup"><span data-stu-id="75a2a-245">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="75a2a-246">O sombreador de geometria não precisa fazer nenhum trabalho; o sombreador de geometria de modelo passa por todos os dados, com exceção do índice de matriz de destino de renderização, que é usado para definir a semântica de SV_RenderTargetArrayIndex.</span><span class="sxs-lookup"><span data-stu-id="75a2a-246">The geometry shader doesn't have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="75a2a-247">Código de modelo de aplicativo para **GeometryShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-247">App template code for **GeometryShader.hlsl**:</span></span>

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

## <a name="present"></a><span data-ttu-id="75a2a-248">Presente</span><span class="sxs-lookup"><span data-stu-id="75a2a-248">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="75a2a-249">Habilitar o quadro Holographic para apresentar a cadeia de permuta</span><span class="sxs-lookup"><span data-stu-id="75a2a-249">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="75a2a-250">Com a realidade mista do Windows, o sistema controla a cadeia de permuta.</span><span class="sxs-lookup"><span data-stu-id="75a2a-250">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="75a2a-251">Em seguida, o sistema gerencia a apresentação de quadros para cada câmera Holographic para garantir uma experiência de usuário de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="75a2a-251">The system then manages presenting frames to each holographic camera to ensure a high-quality user experience.</span></span> <span data-ttu-id="75a2a-252">Ele também fornece uma atualização de visor a cada quadro, para cada câmera, para otimizar aspectos do sistema, como estabilização de imagem ou captura de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="75a2a-252">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="75a2a-253">Portanto, um aplicativo Holographic usando o DirectX não chama a **presente** em uma cadeia de permuta dxgi.</span><span class="sxs-lookup"><span data-stu-id="75a2a-253">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="75a2a-254">Em vez disso, você usa a classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> para apresentar todos os permuta de um quadro depois de terminar de desenhá-lo.</span><span class="sxs-lookup"><span data-stu-id="75a2a-254">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="75a2a-255">De **DeviceResources::P reenviada**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-255">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="75a2a-256">Por padrão, essa API aguarda a conclusão do quadro antes de retornar.</span><span class="sxs-lookup"><span data-stu-id="75a2a-256">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="75a2a-257">Os aplicativos Holographic devem aguardar até que o quadro anterior seja concluído antes de iniciar o trabalho em um novo quadro, pois isso reduz a latência e permite resultados melhores de previsões de quadro Holographic.</span><span class="sxs-lookup"><span data-stu-id="75a2a-257">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="75a2a-258">Essa não é uma regra difícil e, se você tiver quadros que demoram mais de uma atualização de tela para renderização, você pode desabilitar essa espera passando o parâmetro HolographicFramePresentWaitBehavior para <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span><span class="sxs-lookup"><span data-stu-id="75a2a-258">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="75a2a-259">Nesse caso, você provavelmente usaria um thread de renderização assíncrono para manter uma carga contínua na GPU.</span><span class="sxs-lookup"><span data-stu-id="75a2a-259">In this case, you would likely use an asynchronous rendering thread to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="75a2a-260">A taxa de atualização do dispositivo HoloLens é de 60 Hz, em que um quadro tem uma duração de aproximadamente 16 ms.</span><span class="sxs-lookup"><span data-stu-id="75a2a-260">The refresh rate of the HoloLens device is 60 hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="75a2a-261">Os dispositivos de headset de imersão podem variar de 60 Hz a 90 Hz; ao atualizar a exibição em 90 Hz, cada quadro terá uma duração de aproximadamente 11 MS.</span><span class="sxs-lookup"><span data-stu-id="75a2a-261">Immersive headset devices can range from 60 hz to 90 hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="75a2a-262">Manipule cenários DeviceLost em cooperação com o HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="75a2a-262">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="75a2a-263">Os aplicativos DirectX 11 normalmente desejariam verificar o HRESULT retornado pela função **presente** da cadeia de permuta dxgi para descobrir se houve um erro de **DeviceLost** .</span><span class="sxs-lookup"><span data-stu-id="75a2a-263">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="75a2a-264">A classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> lida com isso para você.</span><span class="sxs-lookup"><span data-stu-id="75a2a-264">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="75a2a-265">Inspecione o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> retornado para descobrir se você precisa liberar e recriar o dispositivo Direct3D e os recursos baseados em dispositivo.</span><span class="sxs-lookup"><span data-stu-id="75a2a-265">Inspect the returned <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

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

<span data-ttu-id="75a2a-266">Se o dispositivo Direct3D foi perdido e você o recriou, precisa dizer ao <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> para começar a usar o novo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="75a2a-266">If the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="75a2a-267">A cadeia de permuta será recriada para este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="75a2a-267">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="75a2a-268">De **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-268">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="75a2a-269">Depois que o quadro for apresentado, você poderá retornar ao loop do programa principal e permitir que ele continue para o próximo quadro.</span><span class="sxs-lookup"><span data-stu-id="75a2a-269">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="75a2a-270">PCs de gráficos híbridos e aplicativos de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="75a2a-270">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="75a2a-271">**Os** PCs de atualização do Windows 10 para criadores podem ser configurados com GPUs discretas e integradas.</span><span class="sxs-lookup"><span data-stu-id="75a2a-271">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="75a2a-272">Com esses tipos de computadores, o Windows escolherá o adaptador ao qual o headset está conectado.</span><span class="sxs-lookup"><span data-stu-id="75a2a-272">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="75a2a-273">Os aplicativos devem garantir que o dispositivo DirectX criado por ele use o mesmo adaptador.</span><span class="sxs-lookup"><span data-stu-id="75a2a-273">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="75a2a-274">O código de exemplo de Direct3D mais geral demonstra como criar um dispositivo DirectX usando o adaptador de hardware padrão, que em um sistema híbrido pode não ser o mesmo usado para o headset.</span><span class="sxs-lookup"><span data-stu-id="75a2a-274">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="75a2a-275">Para solucionar problemas, use o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterID</a> de <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId () ou <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. Adaptadorid ().</span><span class="sxs-lookup"><span data-stu-id="75a2a-275">To work around any issues, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterID</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="75a2a-276">Esse adaptadorid pode então ser usado para selecionar o DXGIAdapter correto usando IDXGIFactory4. EnumAdapterByLuid.</span><span class="sxs-lookup"><span data-stu-id="75a2a-276">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="75a2a-277">De **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-277">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

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

<span data-ttu-id="75a2a-278">Código para **Atualizar DeviceResources:: CreateDeviceResources para usar IDXGIAdapter**</span><span class="sxs-lookup"><span data-stu-id="75a2a-278">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

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

<span data-ttu-id="75a2a-279">**Gráficos híbridos e Media Foundation**</span><span class="sxs-lookup"><span data-stu-id="75a2a-279">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="75a2a-280">O uso de Media Foundation em sistemas híbridos pode causar problemas em que o vídeo não será renderizado ou a textura de vídeo está corrompida porque Media Foundation está padronizando o comportamento do sistema.</span><span class="sxs-lookup"><span data-stu-id="75a2a-280">Using Media Foundation on hybrid systems may cause issues where video won't render or video texture are corrupt because Media Foundation is defaulting to a system behavior.</span></span> <span data-ttu-id="75a2a-281">Em alguns cenários, a criação de um ID3D11Device separado é necessária para dar suporte a vários threads e os sinalizadores de criação corretos são definidos.</span><span class="sxs-lookup"><span data-stu-id="75a2a-281">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="75a2a-282">Ao inicializar o ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT sinalizador deve ser definido como parte do D3D11_CREATE_DEVICE_FLAG.</span><span class="sxs-lookup"><span data-stu-id="75a2a-282">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="75a2a-283">Depois que o dispositivo e o contexto forem criados, chame <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> para habilitar multithreading.</span><span class="sxs-lookup"><span data-stu-id="75a2a-283">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="75a2a-284">Para associar o dispositivo ao <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use a função <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager:: ResetDevice</a> .</span><span class="sxs-lookup"><span data-stu-id="75a2a-284">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="75a2a-285">Código para **associar um ID3D11Device com IMFDXGIDeviceManager**:</span><span class="sxs-lookup"><span data-stu-id="75a2a-285">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="75a2a-286">Confira também</span><span class="sxs-lookup"><span data-stu-id="75a2a-286">See also</span></span>
* [<span data-ttu-id="75a2a-287">Sistemas de coordenadas no DirectX</span><span class="sxs-lookup"><span data-stu-id="75a2a-287">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="75a2a-288">Usando o emulador do HoloLens</span><span class="sxs-lookup"><span data-stu-id="75a2a-288">Using the HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
