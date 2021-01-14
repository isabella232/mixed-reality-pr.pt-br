---
ms.openlocfilehash: ad7d530de61864528ae80e4d0086687d282e6b18
ms.sourcegitcommit: 8f9f98342aaf66645fd74dac3fad499f9d799ce7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2021
ms.locfileid: "98109526"
---
# <a name="426"></a>[<span data-ttu-id="8aed5-101">4.26</span><span class="sxs-lookup"><span data-stu-id="8aed5-101">4.26</span></span>](#tab/426) 

## <a name="pv-camera-feed-setup"></a><span data-ttu-id="8aed5-102">Configuração do feed da câmera PV</span><span class="sxs-lookup"><span data-stu-id="8aed5-102">PV Camera Feed Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8aed5-103">A câmera PV é implementada nos plug-ins do Windows Mixed Reality e OpenXR.</span><span class="sxs-lookup"><span data-stu-id="8aed5-103">PV camera is implemented in both Windows Mixed Reality and OpenXR plugins.</span></span> <span data-ttu-id="8aed5-104">No entanto, o OpenXR precisa que o [plug-in do Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal) esteja instalado.</span><span class="sxs-lookup"><span data-stu-id="8aed5-104">However OpenXR needs [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) to be installed.</span></span> <span data-ttu-id="8aed5-105">O OpenXR também tem uma limitação atual: a câmera pode funcionar com o DirectX11 RHI.</span><span class="sxs-lookup"><span data-stu-id="8aed5-105">Also OpenXR has current limitation, camera can work with DirectX11 RHI.</span></span> <span data-ttu-id="8aed5-106">Essa limitação será corrigida em uma versão posterior do Unreal.</span><span class="sxs-lookup"><span data-stu-id="8aed5-106">This limitation will be fixed in a further Unreal version.</span></span> 

- <span data-ttu-id="8aed5-107">Em **Configurações de Projeto > HoloLens**, habilite a funcionalidade **Webcam**:</span><span class="sxs-lookup"><span data-stu-id="8aed5-107">In **Project Settings > HoloLens**, enable the **Webcam** capability:</span></span>

![Captura de tela das configurações de projeto do HoloLens com a propriedade Webcam realçada](../images/unreal-pvc-img-01.png)

- <span data-ttu-id="8aed5-109">Crie um ator chamado “CamCapture” e adicione um plano para renderizar o feed da câmera:</span><span class="sxs-lookup"><span data-stu-id="8aed5-109">Create a new actor called “CamCapture” and add a plane to render the camera feed:</span></span>

![Captura de tela do ator com um plano adicionado](../images/unreal-pvc-img-02.png)

- <span data-ttu-id="8aed5-111">Adicione o ator à cena, crie um material chamado CamTextureMaterial com um parâmetro de objeto de textura e um exemplo de textura.</span><span class="sxs-lookup"><span data-stu-id="8aed5-111">Add the actor to your scene, create a new material called CamTextureMaterial with a Texture Object Parameter, and a texture sample.</span></span>  <span data-ttu-id="8aed5-112">Envie os dados RGB da textura para a cor emissiva de saída:</span><span class="sxs-lookup"><span data-stu-id="8aed5-112">Send the texture’s rgb data to the output emissive color:</span></span>

![Blueprint de um exemplo de material e de textura](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a><span data-ttu-id="8aed5-114">Como renderizar o feed da câmera PV</span><span class="sxs-lookup"><span data-stu-id="8aed5-114">Rendering the PV Camera Feed</span></span>

- <span data-ttu-id="8aed5-115">No blueprint CamCapture, ligue a Câmera de PV:</span><span class="sxs-lookup"><span data-stu-id="8aed5-115">In the CamCapture blueprint, turn on the PV Camera:</span></span>

![Blueprint da função Alternar ARCapture com a câmera PV ligada](../images/unreal-pvc-img-04.png)

- <span data-ttu-id="8aed5-117">Crie uma instância de material dinâmico com base em CamTextureMaterial e atribua esse material ao plano do ator:</span><span class="sxs-lookup"><span data-stu-id="8aed5-117">Create a dynamic material instance from CamTextureMaterial and assign this material to the actor’s plane:</span></span>

![Blueprint da função Criar Instância de Material Dinâmico](../images/unreal-pvc-img-05.png)

- <span data-ttu-id="8aed5-119">Obtenha a textura do feed de câmera e atribua-a ao material dinâmico se ela for válida.</span><span class="sxs-lookup"><span data-stu-id="8aed5-119">Get the texture from the camera feed and assign it to the dynamic material if it's valid.</span></span>  <span data-ttu-id="8aed5-120">Se a textura não for válida, inicie um temporizador e tente novamente após o tempo limite:</span><span class="sxs-lookup"><span data-stu-id="8aed5-120">If the texture isn't valid, start a timer and try again after the timeout:</span></span>

![Blueprint da textura do feed de câmera atribuída ao material dinâmico](../images/unreal-pvc-img-06.png)

- <span data-ttu-id="8aed5-122">Por fim, escale o plano pela taxa de proporção da imagem da câmera:</span><span class="sxs-lookup"><span data-stu-id="8aed5-122">Finally, scale the plane by the camera image’s aspect ratio:</span></span>

![Blueprint do plano escalado em relação à taxa de proporção das imagens da câmera](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a><span data-ttu-id="8aed5-124">Localizar posições da câmera no espaço de mundo</span><span class="sxs-lookup"><span data-stu-id="8aed5-124">Find Camera Positions in World Space</span></span>

<span data-ttu-id="8aed5-125">A câmera do HoloLens 2 é deslocada verticalmente começando no acompanhamento de cabeça do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8aed5-125">The camera on the HoloLens 2 is offset vertically from the device’s head tracking.</span></span>  <span data-ttu-id="8aed5-126">Existem algumas funções para localizar a câmera no espaço de mundo para levar em conta o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="8aed5-126">A few functions exist to locate the camera in world space to account for the offset.</span></span>

<span data-ttu-id="8aed5-127">A função GetPVCameraToWorldTransform obtém a transformação no espaço de mundo da Câmera de PV e será posicionada na lente da câmera:</span><span class="sxs-lookup"><span data-stu-id="8aed5-127">GetPVCameraToWorldTransform gets the transform in world space of the PV Camera and will be positioned on the camera lens:</span></span>

![Blueprint da função Obter Transformação da PVCamera para o Mundo](../images/unreal-pvc-img-08.png)

<span data-ttu-id="8aed5-129">A função GetWorldSpaceRayFromCameraPoint converte um raio da lente da câmera na cena em um espaço de mundo do Unreal para localizar o conteúdo de um pixel no quadro da câmera:</span><span class="sxs-lookup"><span data-stu-id="8aed5-129">GetWorldSpaceRayFromCameraPoint casts a ray from the camera lens into the scene in Unreal world space to find a pixel's content in the camera frame:</span></span>

![Blueprint da função Obter Raio do Espaço de Mundo do Ponto da Câmera](../images/unreal-pvc-img-09.png)

<span data-ttu-id="8aed5-131">A função GetPVCameraIntrinsics retorna os valores intrínsecos da câmera, que podem ser usados durante o processamento da pesquisa visual computacional em um quadro da câmera:</span><span class="sxs-lookup"><span data-stu-id="8aed5-131">GetPVCameraIntrinsics returns the camera intrinsic values, which can be used when doing computer vision processing on a camera frame:</span></span>

![Blueprint das funções Obter Intrínsecos da PVCamera](../images/unreal-pvc-img-10.png)

<span data-ttu-id="8aed5-133">Para localizar o que existe no espaço de mundo em uma coordenada de pixel específica, use um rastreamento de linha com o raio do espaço de mundo:</span><span class="sxs-lookup"><span data-stu-id="8aed5-133">To find what exists in world space at a particular pixel coordinate, use a line trace with the world space ray:</span></span>

![Blueprint do raio do espaço de mundo sendo usado para descobrir o que existe no espaço de mundo em uma coordenada específica](../images/unreal-pvc-img-11.png)

<span data-ttu-id="8aed5-135">Aqui, converteremos um raio de 2 metros começando na lente da câmera até a posição do espaço da câmera, a ¼ do canto superior esquerdo do quadro.</span><span class="sxs-lookup"><span data-stu-id="8aed5-135">Here we cast a 2-meter ray from the camera lens to the camera-space position ¼ from the top left of the frame.</span></span>  <span data-ttu-id="8aed5-136">Em seguida, usaremos o resultado da ocorrência para renderizar algo no local em que o objeto existe no espaço de mundo:</span><span class="sxs-lookup"><span data-stu-id="8aed5-136">Then use the hit result to render something where the object exists in world space:</span></span>

![Blueprint de uma conversão de raio de 2 metros começando na lente da câmera até a posição do espaço da câmera, a 1/4 do canto superior esquerdo do quadro](../images/unreal-pvc-img-12.png)

<span data-ttu-id="8aed5-138">Quando você usar o mapeamento espacial, a posição dessa ocorrência corresponderá à superfície vista pela câmera.</span><span class="sxs-lookup"><span data-stu-id="8aed5-138">When using spatial mapping, this hit position will match the surface that the camera is seeing.</span></span>

## <a name="rendering-the-pv-camera-feed-in-c"></a><span data-ttu-id="8aed5-139">Como renderizar o feed da câmera PV em C++</span><span class="sxs-lookup"><span data-stu-id="8aed5-139">Rendering the PV Camera Feed in C++</span></span>

- <span data-ttu-id="8aed5-140">Crie um ator em C++ chamado CamCapture</span><span class="sxs-lookup"><span data-stu-id="8aed5-140">Create a new C++ actor called CamCapture</span></span>
- <span data-ttu-id="8aed5-141">No build.cs do projeto, adicione “AugmentedReality” à lista PublicDependencyModuleNames:</span><span class="sxs-lookup"><span data-stu-id="8aed5-141">In the project’s build.cs, add “AugmentedReality” to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "AugmentedReality"
});
```

- <span data-ttu-id="8aed5-142">Em CamCapture.h, inclua ARBlueprintLibrary.h</span><span class="sxs-lookup"><span data-stu-id="8aed5-142">In CamCapture.h, include ARBlueprintLibrary.h</span></span>

```cpp
#include "ARBlueprintLibrary.h"
```

- <span data-ttu-id="8aed5-143">Você também precisa adicionar variáveis locais à malha e ao material:</span><span class="sxs-lookup"><span data-stu-id="8aed5-143">You also need to add local variables for the mesh and material:</span></span>

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- <span data-ttu-id="8aed5-144">Em CamCapture.cpp, atualize o construtor para adicionar uma malha estática à cena:</span><span class="sxs-lookup"><span data-stu-id="8aed5-144">In CamCapture.cpp, update the constructor to add a static mesh to the scene:</span></span>

```cpp
ACamCapture::ACamCapture()
{
    PrimaryActorTick.bCanEverTick = true;

    // Load a mesh from the engine to render the camera feed to.
    StaticMesh = LoadObject<UStaticMesh>(nullptr, TEXT("/Engine/EngineMeshes/Cube.Cube"), nullptr, LOAD_None, nullptr);

    // Create a static mesh component to render the static mesh
    StaticMeshComponent = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("CameraPlane"));
    StaticMeshComponent->SetStaticMesh(StaticMesh);

    // Scale and add to the scene
    StaticMeshComponent->SetWorldScale3D(FVector(0.1f, 1, 1));
    this->SetRootComponent(StaticMeshComponent);
}
```

<span data-ttu-id="8aed5-145">Em BeginPlay, crie uma instância de material dinâmico com base no material da câmera do projeto, aplique-a ao componente de malha estática e inicie a câmera do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8aed5-145">In BeginPlay create a dynamic material instance from the project’s camera material, apply it to the static mesh component, and start the HoloLens camera.</span></span> 
 
<span data-ttu-id="8aed5-146">No editor, clique com o botão direito do mouse em CamTextureMaterial no navegador de conteúdo e selecione “Copiar Referência” para obter a cadeia de caracteres de CameraMatPath.</span><span class="sxs-lookup"><span data-stu-id="8aed5-146">In the editor, right-click on the CamTextureMaterial in the content browser and select “Copy Reference” to get the string for CameraMatPath.</span></span>

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMateriall = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

<span data-ttu-id="8aed5-147">Em Tick, obtenha a textura da câmera, defina-a como o parâmetro de textura no material CamTextureMaterial e escale o componente de malha estática pela taxa de proporção do quadro da câmera:</span><span class="sxs-lookup"><span data-stu-id="8aed5-147">In Tick get the texture from the camera, set it to the texture parameter in the CamTextureMaterial material, and scale the static mesh component by the camera frame’s aspect ratio:</span></span>

```cpp
void ACamCapture::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    // Dynamic material instance only needs to be set once.
    if(IsTextureParamSet)
    {
        return;
    }

    // Get the texture from the camera.
    UARTexture* ARTexture = UARBlueprintLibrary::GetARTexture(EARTextureType::CameraImage);
    if(ARTexture != nullptr)
    {
        // Set the shader's texture parameter (named "Param") to the camera image.
        DynamicMaterial->SetTextureParameterValue("Param", ARTexture);
        IsTextureParamSet = true;

        // Get the camera instrincs
        FARCameraIntrinsics Intrinsics;
        UARBlueprintLibrary::GetCameraIntrinsics(Intrinsics);

        // Scale the camera mesh by the aspect ratio.
        float R = (float)Intrinsics.ImageResolution.X / (float)Intrinsics.ImageResolution.Y;
        StaticMeshComponent->SetWorldScale3D(FVector(0.1f, R, 1));
    }
}
```

# <a name="425"></a>[<span data-ttu-id="8aed5-148">4.25</span><span class="sxs-lookup"><span data-stu-id="8aed5-148">4.25</span></span>](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="8aed5-149">Renderizar da câmera de PV para MRC</span><span class="sxs-lookup"><span data-stu-id="8aed5-149">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="8aed5-150">Isso requer o **Unreal Engine 4.25** ou posterior.</span><span class="sxs-lookup"><span data-stu-id="8aed5-150">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="8aed5-151">O sistema e os gravadores personalizados de MRC criam capturas de realidade misturada combinando a Câmera de PV com os hologramas renderizados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8aed5-151">The system and custom MRC recorders create mixed reality captures by combining the PV Camera with holograms rendered by the app.</span></span>

<span data-ttu-id="8aed5-152">Por padrão, a captura de realidade misturada usa a saída holográfica do olho direito.</span><span class="sxs-lookup"><span data-stu-id="8aed5-152">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="8aed5-153">Se um aplicativo imersivo optar por [fazer a renderização da Câmera de PV](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), isso será usado.</span><span class="sxs-lookup"><span data-stu-id="8aed5-153">If an immersive app chooses to [render from the PV Camera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), then that will be used instead.</span></span> <span data-ttu-id="8aed5-154">A renderização da Câmera de PV aprimora o mapeamento entre o mundo real e os hologramas no vídeo da MRC.</span><span class="sxs-lookup"><span data-stu-id="8aed5-154">Rendering from the PV Camera improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="8aed5-155">Para aceitar a renderização por meio da Câmera de PV:</span><span class="sxs-lookup"><span data-stu-id="8aed5-155">To opt in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="8aed5-156">Chamar **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="8aed5-156">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="8aed5-157">Use os valores de **Tamanho X** e **Tamanho Y** para definir as dimensões do vídeo.</span><span class="sxs-lookup"><span data-stu-id="8aed5-157">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Terceira câmera](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="8aed5-159">Em seguida, o Unreal lidará com as solicitações da MRC para renderizar da perspectiva da câmera de PV.</span><span class="sxs-lookup"><span data-stu-id="8aed5-159">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="8aed5-160">Somente quando a [Captura de Realidade Misturada](../../../mixed-reality-capture.md) for disparada, o aplicativo será solicitado a renderizar partindo da perspectiva da câmera de foto/vídeo.</span><span class="sxs-lookup"><span data-stu-id="8aed5-160">Only when [Mixed Reality Capture](../../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="8aed5-161">Usando a câmera de PV</span><span class="sxs-lookup"><span data-stu-id="8aed5-161">Using the PV Camera</span></span>

<span data-ttu-id="8aed5-162">A textura de webcam pode ser recuperada no jogo em runtime, mas precisa ser habilitada no menu **Editar > Configurações de Projeto** do editor:</span><span class="sxs-lookup"><span data-stu-id="8aed5-162">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="8aed5-163">Acesse **Plataformas > HoloLens > Funcionalidades** e marque **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="8aed5-163">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="8aed5-164">Use a função **StartCameraCapture** para usar a webcam em runtime e a função **StopCameraCapture** para interromper a gravação.</span><span class="sxs-lookup"><span data-stu-id="8aed5-164">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Iniciar/interromper câmera](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="8aed5-166">Renderização de uma imagem</span><span class="sxs-lookup"><span data-stu-id="8aed5-166">Rendering an image</span></span>
<span data-ttu-id="8aed5-167">Para renderizar a imagem da câmera:</span><span class="sxs-lookup"><span data-stu-id="8aed5-167">To render the camera image:</span></span>
1. <span data-ttu-id="8aed5-168">Crie uma instância de material dinâmico com base em um material no projeto, nomeado **PVCamMat** na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="8aed5-168">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="8aed5-169">Defina a instância de material dinâmico para uma variável de **Referência de Objeto Dinâmico da Instância de Material**.</span><span class="sxs-lookup"><span data-stu-id="8aed5-169">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="8aed5-170">Defina o material do objeto na cena que renderizará o feed da câmera para essa nova instância de material dinâmico.</span><span class="sxs-lookup"><span data-stu-id="8aed5-170">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="8aed5-171">Inicie um temporizador que será usado para associar a imagem da câmera ao material.</span><span class="sxs-lookup"><span data-stu-id="8aed5-171">Start a timer that will be used to bind the camera image to the material.</span></span>

![Renderização da câmera](../images/unreal-camera-render.PNG)

4. <span data-ttu-id="8aed5-173">Crie uma função para esse temporizador (neste caso, **MaterialTimer**) e chame **GetARCameraImage** para obter a textura da webcam.</span><span class="sxs-lookup"><span data-stu-id="8aed5-173">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="8aed5-174">Se a textura for válida, defina um parâmetro de textura no sombreador para a imagem.</span><span class="sxs-lookup"><span data-stu-id="8aed5-174">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="8aed5-175">Caso contrário, inicie o temporizador de material novamente.</span><span class="sxs-lookup"><span data-stu-id="8aed5-175">Otherwise, start the material timer again.</span></span>

![Textura da câmera da webcam](../images/unreal-camera-texture.PNG)

5. <span data-ttu-id="8aed5-177">Verifique se o material tem um parâmetro que corresponda ao nome em **SetTextureParameterValue** que esteja associado a uma entrada de cor.</span><span class="sxs-lookup"><span data-stu-id="8aed5-177">Make sure the material has a parameter that matches the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="8aed5-178">Sem o parâmetro, a imagem da câmera não pode ser exibida corretamente.</span><span class="sxs-lookup"><span data-stu-id="8aed5-178">Without the parameter, the camera image can't be displayed properly.</span></span>

![Textura da câmera](../images/unreal-camera-material.PNG)

