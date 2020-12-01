---
title: Entrada olhar em não real
description: Tutorial sobre como configurar a entrada de olhar para o HoloLens e o mecanismo inreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realidade mista do Windows, hologramas, HoloLens 2, controle de olho, entrada de olhar, exibição montada de cabeçalho, mecanismo inreal, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: f89638cef6b90e004f097c701c3df13edaf74fac
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354304"
---
# <a name="gaze-input"></a><span data-ttu-id="47e0f-104">Entrada olhar</span><span class="sxs-lookup"><span data-stu-id="47e0f-104">Gaze Input</span></span>

<span data-ttu-id="47e0f-105">Olhar é usado para indicar o que o usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="47e0f-105">Gaze is used to indicate what the user is looking at.</span></span>  <span data-ttu-id="47e0f-106">Isso usa as câmeras de controle de olho no dispositivo para encontrar um raio de espaço do mundo inreal correspondente ao que o usuário está vendo no momento.</span><span class="sxs-lookup"><span data-stu-id="47e0f-106">This uses the eye tracking cameras on the device to find a ray in Unreal world space matching what the user is currently looking at.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="47e0f-107">Habilitando o acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="47e0f-107">Enabling eye tracking</span></span>

- <span data-ttu-id="47e0f-108">Em **configurações do projeto > HoloLens**, habilite o recurso de **entrada olhar** :</span><span class="sxs-lookup"><span data-stu-id="47e0f-108">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![Captura de tela de recursos de configuração do projeto de HoloLens com entrada olhar realçada](images/unreal-gaze-img-01.png)

- <span data-ttu-id="47e0f-110">Criar um novo ator e adicioná-lo à sua cena</span><span class="sxs-lookup"><span data-stu-id="47e0f-110">Create a new actor and add it to your scene</span></span>

> [!NOTE] 
> <span data-ttu-id="47e0f-111">O controle de olhos do HoloLens em tempo inreal tem apenas um único olhar Ray para ambos os olhos, em vez dos dois raios necessários para o acompanhamento do estereoscópico, o que não é suportado.</span><span class="sxs-lookup"><span data-stu-id="47e0f-111">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="47e0f-112">Como usar o acompanhamento ocular</span><span class="sxs-lookup"><span data-stu-id="47e0f-112">Using eye tracking</span></span>

<span data-ttu-id="47e0f-113">Primeiro, verifique se o dispositivo dá suporte ao acompanhamento de olho com a função IsEyeTrackerConnected.</span><span class="sxs-lookup"><span data-stu-id="47e0f-113">First check that the device supports eye tracking with the IsEyeTrackerConnected function.</span></span>  <span data-ttu-id="47e0f-114">Se isso retornar true, chame GetGazeData para descobrir onde os olhos do usuário estão olhando durante o quadro atual:</span><span class="sxs-lookup"><span data-stu-id="47e0f-114">If this returns true, call GetGazeData to find where the user’s eyes are looking at during the current frame:</span></span>

![Plano gráfico da função conectada de acompanhamento de olho](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="47e0f-116">O ponto fixação da e o valor de confiança não estão disponíveis no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="47e0f-116">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="47e0f-117">Para localizar o que o usuário está olhando, use a origem e a direção do olhar em um rastreamento de linha.</span><span class="sxs-lookup"><span data-stu-id="47e0f-117">To find what the user is looking at, use the gaze origin and direction in a line trace.</span></span>  <span data-ttu-id="47e0f-118">O início desse vetor é a origem olhar e o final é a origem mais a direção olhar multiplicada pela distância desejada:</span><span class="sxs-lookup"><span data-stu-id="47e0f-118">The start of this vector is the gaze origin and the end is the origin plus the gaze direction multiplied by the desired distance:</span></span>

![Plano gráfico da função obter dados olhar](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="47e0f-120">Obtendo orientação de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="47e0f-120">Getting head orientation</span></span>

<span data-ttu-id="47e0f-121">Como alternativa, a rotação HMD pode ser usada para representar a direção do cabeçalho do usuário.</span><span class="sxs-lookup"><span data-stu-id="47e0f-121">Alternatively, the HMD rotation can be used to represent the direction of the user’s head.</span></span>  <span data-ttu-id="47e0f-122">Isso não exige o recurso de entrada do olhar, mas não lhe dará informações de controle de olho.</span><span class="sxs-lookup"><span data-stu-id="47e0f-122">This does not require the Gaze Input capability but won't give you any eye tracking information.</span></span>  <span data-ttu-id="47e0f-123">Uma referência ao plano gráfico deve ser adicionada como o contexto mundial para obter os dados de saída corretos:</span><span class="sxs-lookup"><span data-stu-id="47e0f-123">A reference to the blueprint must be added as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="47e0f-124">Obter dados de HMD só está disponível em versões inreals de 4,26 e em diante.</span><span class="sxs-lookup"><span data-stu-id="47e0f-124">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Plano gráfico da função Get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="47e0f-126">Usando C++</span><span class="sxs-lookup"><span data-stu-id="47e0f-126">Using C++</span></span> 

- <span data-ttu-id="47e0f-127">No arquivo build.cs do jogo, adicione "EyeTracker" à lista PublicDependencyModuleNames:</span><span class="sxs-lookup"><span data-stu-id="47e0f-127">In your game’s build.cs file, add “EyeTracker” to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "EyeTracker"
});
```

- <span data-ttu-id="47e0f-128">Em "arquivo/nova classe C++", crie um novo ator de C++ chamado "EyeTracker"</span><span class="sxs-lookup"><span data-stu-id="47e0f-128">In “File/ New C++ Class”, Create a new C++ actor called “EyeTracker”</span></span>
    - <span data-ttu-id="47e0f-129">Uma solução do Visual Studio será aberta para a nova classe EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="47e0f-129">A Visual Studio solution will open to the new EyeTracker class.</span></span> <span data-ttu-id="47e0f-130">Compile e execute para abrir o jogo não real com o novo ator EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="47e0f-130">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="47e0f-131">Pesquise "EyeTracker" na janela "posicionar atores".</span><span class="sxs-lookup"><span data-stu-id="47e0f-131">Search for “EyeTracker” in the “Place Actors” window.</span></span>  <span data-ttu-id="47e0f-132">Arraste e solte essa classe na janela do jogo para adicioná-la ao projeto:</span><span class="sxs-lookup"><span data-stu-id="47e0f-132">Drag and drop this class into the game window to add it to the project:</span></span>

![Captura de tela de um ator com a janela local do ator aberta](images/unreal-gaze-img-06.png)

- <span data-ttu-id="47e0f-134">Em EyeTracker. cpp, adicione inclusões para EyeTrackerFunctionLibrary e DrawDebugHelpers:</span><span class="sxs-lookup"><span data-stu-id="47e0f-134">In EyeTracker.cpp, add includes for EyeTrackerFunctionLibrary, and DrawDebugHelpers:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="47e0f-135">Em tique, verifique se o dispositivo dá suporte ao acompanhamento de olho com UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected.</span><span class="sxs-lookup"><span data-stu-id="47e0f-135">In Tick, check that the device supports eye tracking with UEyeTrackerFunctionLibrary::IsEyeTrackerConnected.</span></span>  <span data-ttu-id="47e0f-136">Em seguida, localize o início e o final de um raio para um rastreamento de linha de UEyeTrackerFunctionLibrary:: GetGazeData:</span><span class="sxs-lookup"><span data-stu-id="47e0f-136">Then find the start and end of a ray for a line trace from UEyeTrackerFunctionLibrary::GetGazeData:</span></span>

```cpp
void AEyeTracker::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    if(UEyeTrackerFunctionLibrary::IsEyeTrackerConnected())
    {
        FEyeTrackerGazeData GazeData;
        if(UEyeTrackerFunctionLibrary::GetGazeData(GazeData))
        {
            FVector Start = GazeData.GazeOrigin;
            FVector End = GazeData.GazeOrigin + GazeData.GazeDirection * 100;

            FHitResult Hit Result;
            if (GWorld->LineTraceSingleByChannel(HitResult, Start, End, ECollisionChannel::ECC_Visiblity))
            {
                DrawDebugCoordinateSystem(GWorld, HitResult.Location, FQuat::Identity.Rotator(), 10);
            }
        }
    }
}
```

## <a name="next-development-checkpoint"></a><span data-ttu-id="47e0f-137">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="47e0f-137">Next Development Checkpoint</span></span>

<span data-ttu-id="47e0f-138">Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unreal, você está no meio da exploração dos principais blocos de construção do MRTK.</span><span class="sxs-lookup"><span data-stu-id="47e0f-138">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="47e0f-139">De lá, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="47e0f-139">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="47e0f-140">Acompanhamento da mão</span><span class="sxs-lookup"><span data-stu-id="47e0f-140">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="47e0f-141">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="47e0f-141">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="47e0f-142">Câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="47e0f-142">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="47e0f-143">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="47e0f-143">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="47e0f-144">Veja também</span><span class="sxs-lookup"><span data-stu-id="47e0f-144">See also</span></span>
* [<span data-ttu-id="47e0f-145">Calibragem</span><span class="sxs-lookup"><span data-stu-id="47e0f-145">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="47e0f-146">Conforto</span><span class="sxs-lookup"><span data-stu-id="47e0f-146">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="47e0f-147">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="47e0f-147">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="47e0f-148">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="47e0f-148">Voice input</span></span>](../../out-of-scope/voice-design.md)
