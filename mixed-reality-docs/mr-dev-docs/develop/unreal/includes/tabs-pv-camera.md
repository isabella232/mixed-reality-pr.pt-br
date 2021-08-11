---
ms.openlocfilehash: 45b171d3d5856dd17f9223d945a1d0fd46326600b3ed65bc4198c6da5fa524f9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207435"
---
# <a name="426"></a>[4.26](#tab/426) 

## <a name="pv-camera-feed-setup"></a>Configuração do feed da câmera PV

> [!IMPORTANT]
> A câmera PV é implementada nos plug-ins do Windows Mixed Reality e OpenXR. No entanto, o OpenXR precisa que o [plug-in do Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal) esteja instalado. O OpenXR também tem uma limitação atual: a câmera pode funcionar com o DirectX11 RHI. Essa limitação será corrigida em uma versão posterior do Unreal. 

- Em **Configurações de Projeto > HoloLens**, habilite a funcionalidade **Webcam**:

![Captura de tela das configurações de projeto do HoloLens com a propriedade Webcam realçada](../images/unreal-pvc-img-01.png)

- Crie um ator chamado “CamCapture” e adicione um plano para renderizar o feed da câmera:

![Captura de tela do ator com um plano adicionado](../images/unreal-pvc-img-02.png)

- Adicione o ator à cena, crie um material chamado CamTextureMaterial com um parâmetro de objeto de textura e um exemplo de textura.  Envie os dados RGB da textura para a cor emissiva de saída:

![Blueprint de um exemplo de material e de textura](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a>Como renderizar o feed da câmera PV

- No blueprint CamCapture, ligue a Câmera de PV:

![Blueprint da função Alternar ARCapture com a câmera PV ligada](../images/unreal-pvc-img-04.png)

- Crie uma instância de material dinâmico com base em CamTextureMaterial e atribua esse material ao plano do ator:

![Blueprint da função Criar Instância de Material Dinâmico](../images/unreal-pvc-img-05.png)

- Obtenha a textura do feed de câmera e atribua-a ao material dinâmico se ela for válida.  Se a textura não for válida, inicie um temporizador e tente novamente após o tempo limite:

![Blueprint da textura do feed de câmera atribuída ao material dinâmico](../images/unreal-pvc-img-06.png)

- Por fim, escale o plano pela taxa de proporção da imagem da câmera:

![Blueprint do plano escalado em relação à taxa de proporção das imagens da câmera](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a>Localizar posições da câmera no espaço de mundo

A câmera do HoloLens 2 é deslocada verticalmente começando no acompanhamento de cabeça do dispositivo.  Existem algumas funções para localizar a câmera no espaço de mundo para levar em conta o deslocamento.

A função GetPVCameraToWorldTransform obtém a transformação no espaço de mundo da Câmera de PV e será posicionada na lente da câmera:

![Blueprint da função Obter Transformação da PVCamera para o Mundo](../images/unreal-pvc-img-08.png)

A função GetWorldSpaceRayFromCameraPoint converte um raio da lente da câmera na cena em um espaço de mundo do Unreal para localizar o conteúdo de um pixel no quadro da câmera:

![Blueprint da função Obter Raio do Espaço de Mundo do Ponto da Câmera](../images/unreal-pvc-img-09.png)

A função GetPVCameraIntrinsics retorna os valores intrínsecos da câmera, que podem ser usados durante o processamento da pesquisa visual computacional em um quadro da câmera:

![Blueprint das funções Obter Intrínsecos da PVCamera](../images/unreal-pvc-img-10.png)

Para localizar o que existe no espaço de mundo em uma coordenada de pixel específica, use um rastreamento de linha com o raio do espaço de mundo:

![Blueprint do raio do espaço de mundo sendo usado para descobrir o que existe no espaço de mundo em uma coordenada específica](../images/unreal-pvc-img-11.png)

Aqui, converteremos um raio de 2 metros começando na lente da câmera até a posição do espaço da câmera, a ¼ do canto superior esquerdo do quadro.  Em seguida, usaremos o resultado da ocorrência para renderizar algo no local em que o objeto existe no espaço de mundo:

![Blueprint de uma conversão de raio de 2 metros começando na lente da câmera até a posição do espaço da câmera, a 1/4 do canto superior esquerdo do quadro](../images/unreal-pvc-img-12.png)

Quando você usar o mapeamento espacial, a posição dessa ocorrência corresponderá à superfície vista pela câmera.

## <a name="rendering-the-pv-camera-feed-in-c"></a>Como renderizar o feed da câmera PV em C++

- Crie um ator em C++ chamado CamCapture
- No build.cs do projeto, adicione “AugmentedReality” à lista PublicDependencyModuleNames:

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

- Em CamCapture.h, inclua ARBlueprintLibrary.h

```cpp
#include "ARBlueprintLibrary.h"
```

- Você também precisa adicionar variáveis locais à malha e ao material:

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- Em CamCapture.cpp, atualize o construtor para adicionar uma malha estática à cena:

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

Em BeginPlay, crie uma instância de material dinâmico com base no material da câmera do projeto, aplique-a ao componente de malha estática e inicie a câmera do HoloLens. 
 
No editor, clique com o botão direito do mouse em CamTextureMaterial no navegador de conteúdo e selecione “Copiar Referência” para obter a cadeia de caracteres de CameraMatPath.

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMaterial = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

Em Tick, obtenha a textura da câmera, defina-a como o parâmetro de textura no material CamTextureMaterial e escale o componente de malha estática pela taxa de proporção do quadro da câmera:

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

# <a name="425"></a>[4.25](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a>Renderizar da câmera de PV para MRC

> [!NOTE]
> Isso requer o **Unreal Engine 4.25** ou posterior.

O sistema e os gravadores personalizados de MRC criam capturas de realidade misturada combinando a Câmera de PV com os hologramas renderizados pelo aplicativo.

Por padrão, a captura de realidade misturada usa a saída holográfica do olho direito. Se um aplicativo imersivo optar por [fazer a renderização da Câmera de PV](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), isso será usado. A renderização da Câmera de PV aprimora o mapeamento entre o mundo real e os hologramas no vídeo da MRC.

Para aceitar a renderização por meio da Câmera de PV:

1. Chamar **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**
    * Use os valores de **Tamanho X** e **Tamanho Y** para definir as dimensões do vídeo.

![Terceira câmera](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

Em seguida, o Unreal lidará com as solicitações da MRC para renderizar da perspectiva da câmera de PV.

> [!NOTE]
> Somente quando a [Captura de Realidade Misturada](/hololens/holographic-photos-and-videos) for disparada, o aplicativo será solicitado a renderizar partindo da perspectiva da câmera de foto/vídeo.

## <a name="using-the-pv-camera"></a>Usando a câmera de PV

A textura de webcam pode ser recuperada no jogo em runtime, mas precisa ser habilitada no menu **Editar > Configurações de Projeto** do editor:
1. Acesse **Plataformas > HoloLens > Funcionalidades** e marque **Webcam**.
    * Use a função **StartCameraCapture** para usar a webcam em runtime e a função **StopCameraCapture** para interromper a gravação.

![Iniciar/interromper câmera](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>Renderização de uma imagem
Para renderizar a imagem da câmera:
1. Crie uma instância de material dinâmico com base em um material no projeto, nomeado **PVCamMat** na captura de tela abaixo.  
2. Defina a instância de material dinâmico para uma variável de **Referência de Objeto Dinâmico da Instância de Material**.  
3. Defina o material do objeto na cena que renderizará o feed da câmera para essa nova instância de material dinâmico.
    * Inicie um temporizador que será usado para associar a imagem da câmera ao material.

![Renderização da câmera](../images/unreal-camera-render.PNG)

4. Crie uma função para esse temporizador (neste caso, **MaterialTimer**) e chame **GetARCameraImage** para obter a textura da webcam.  
5. Se a textura for válida, defina um parâmetro de textura no sombreador para a imagem.  Caso contrário, inicie o temporizador de material novamente.

![Textura da câmera da webcam](../images/unreal-camera-texture.PNG)

5. Verifique se o material tem um parâmetro que corresponda ao nome em **SetTextureParameterValue** que esteja associado a uma entrada de cor. Sem o parâmetro, a imagem da câmera não pode ser exibida corretamente.

![Textura da câmera](../images/unreal-camera-material.PNG)