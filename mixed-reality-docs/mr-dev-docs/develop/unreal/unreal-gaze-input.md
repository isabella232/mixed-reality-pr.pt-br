---
title: Entrada olhar em não real
description: Tutorial sobre como configurar a entrada de olhar para o HoloLens e o mecanismo inreal
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Realidade mista do Windows, hologramas, HoloLens 2, controle de olho, entrada de olhar, exibição montada de cabeçalho, mecanismo inreal, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: a11573d732e739068dca8c42dd8688c0705fc5bb
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925985"
---
# <a name="gaze-input"></a><span data-ttu-id="1b32c-104">Entrada olhar</span><span class="sxs-lookup"><span data-stu-id="1b32c-104">Gaze Input</span></span>

<span data-ttu-id="1b32c-105">A entrada olhar em aplicativos de realidade misturada é como descobrir o que os usuários estão olhando.</span><span class="sxs-lookup"><span data-stu-id="1b32c-105">Gaze input in mixed reality apps is all about finding out what your users are looking at.</span></span> <span data-ttu-id="1b32c-106">Quando as câmeras de acompanhamento de olho em seu dispositivo correspondem a raios no espaço do mundo inreal, a linha de dados de visão do usuário fica disponível.</span><span class="sxs-lookup"><span data-stu-id="1b32c-106">When the eye tracking cameras on your device match up with rays in Unreal's world space, your user's line of sight data becomes available.</span></span> <span data-ttu-id="1b32c-107">O olhar pode ser usado em plantas e em C++ e é um recurso fundamental para a mecânica, como interação de objeto, localização e controles de câmera.</span><span class="sxs-lookup"><span data-stu-id="1b32c-107">Gaze can be used in both blueprints and C++, and is a core feature for mechanics like object interaction, way finding, and camera controls.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="1b32c-108">Habilitando o acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="1b32c-108">Enabling eye tracking</span></span>

- <span data-ttu-id="1b32c-109">Em **configurações do projeto > HoloLens**, habilite o recurso de **entrada olhar** :</span><span class="sxs-lookup"><span data-stu-id="1b32c-109">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![Captura de tela de recursos de configuração do projeto de HoloLens com entrada olhar realçada](images/unreal-gaze-img-01.png)

- <span data-ttu-id="1b32c-111">Criar um novo ator e adicioná-lo à sua cena</span><span class="sxs-lookup"><span data-stu-id="1b32c-111">Create a new actor and add it to your scene</span></span>

> [!NOTE]
> <span data-ttu-id="1b32c-112">O controle de olhos do HoloLens em tempo inreal tem apenas um único olhar Ray para ambos os olhos.</span><span class="sxs-lookup"><span data-stu-id="1b32c-112">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes.</span></span> <span data-ttu-id="1b32c-113">O acompanhamento de estereoscópico, que requer dois raios, não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="1b32c-113">Stereoscopic tracking, which requires two rays, isn't supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="1b32c-114">Como usar o acompanhamento ocular</span><span class="sxs-lookup"><span data-stu-id="1b32c-114">Using eye tracking</span></span>

<span data-ttu-id="1b32c-115">Primeiro, verifique se seu dispositivo dá suporte ao controle de olho com a função **IsEyeTrackerConnected** .</span><span class="sxs-lookup"><span data-stu-id="1b32c-115">First, check that your device supports eye tracking with the **IsEyeTrackerConnected** function.</span></span>  <span data-ttu-id="1b32c-116">Se a função retornar true, chame **GetGazeData** para descobrir onde os olhos do usuário estão olhando no quadro atual:</span><span class="sxs-lookup"><span data-stu-id="1b32c-116">If the function returns true, call **GetGazeData** to find where the user’s eyes are looking at in the current frame:</span></span>

![Plano gráfico da função conectada de acompanhamento de olho](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="1b32c-118">O ponto fixação da e o valor de confiança não estão disponíveis no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1b32c-118">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="1b32c-119">Use a origem e a direção do olhar em um rastreamento de linha para descobrir exatamente onde os usuários estão olhando.</span><span class="sxs-lookup"><span data-stu-id="1b32c-119">Use the gaze origin and direction in a line trace to find out exactly where your users are looking.</span></span>  <span data-ttu-id="1b32c-120">O valor de olhar é um vetor, começando na origem de olhar e terminando na origem mais a direção de olhar multiplicada pela distância de rastreamento de linha:</span><span class="sxs-lookup"><span data-stu-id="1b32c-120">The gaze value is a vector, starting at the gaze origin and ending at the origin plus the gaze direction multiplied by the line trace distance:</span></span>

![Plano gráfico da função obter dados olhar](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="1b32c-122">Obtendo orientação de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="1b32c-122">Getting head orientation</span></span>

<span data-ttu-id="1b32c-123">Você também pode usar a rotação da exibição montada de cabeçalho (HMD) para representar a direção do cabeçalho do usuário.</span><span class="sxs-lookup"><span data-stu-id="1b32c-123">You can also use the rotation of the Head Mounted Display (HMD) to represent the direction of the user’s head.</span></span> <span data-ttu-id="1b32c-124">Você pode obter a direção do cabeçalho dos usuários sem habilitar a funcionalidade de entrada olhar, mas não terá nenhuma informação de acompanhamento de olho.</span><span class="sxs-lookup"><span data-stu-id="1b32c-124">You can get the users head direction without enabling the Gaze Input capability, but you won't get you any eye tracking information.</span></span>  <span data-ttu-id="1b32c-125">Adicione uma referência ao plano gráfico como o contexto mundial para obter os dados de saída corretos:</span><span class="sxs-lookup"><span data-stu-id="1b32c-125">Add a reference to the blueprint as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="1b32c-126">Obter dados de HMD só está disponível em versões inreals de 4,26 e em diante.</span><span class="sxs-lookup"><span data-stu-id="1b32c-126">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Plano gráfico da função Get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="1b32c-128">Usando C++</span><span class="sxs-lookup"><span data-stu-id="1b32c-128">Using C++</span></span>

- <span data-ttu-id="1b32c-129">No arquivo **Build.cs** do jogo, adicione **EyeTracker** à lista **PublicDependencyModuleNames** :</span><span class="sxs-lookup"><span data-stu-id="1b32c-129">In your game’s **build.cs** file, add **EyeTracker** to the **PublicDependencyModuleNames** list:</span></span>

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

- <span data-ttu-id="1b32c-130">Em **arquivo/nova classe c++**, crie um novo ator de C++ chamado **EyeTracker**</span><span class="sxs-lookup"><span data-stu-id="1b32c-130">In **File/ New C++ Class**, create a new C++ actor called **EyeTracker**</span></span>
    - <span data-ttu-id="1b32c-131">Uma solução do Visual Studio abrirá a nova classe EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="1b32c-131">A Visual Studio solution will open up the new EyeTracker class.</span></span> <span data-ttu-id="1b32c-132">Compile e execute para abrir o jogo não real com o novo ator EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="1b32c-132">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="1b32c-133">Pesquise "EyeTracker" na janela **posicionar atores** e arraste e solte a classe na janela do jogo para adicioná-la ao projeto:</span><span class="sxs-lookup"><span data-stu-id="1b32c-133">Search for “EyeTracker” in the **Place Actors** window and drag and drop the class into the game window to add it to the project:</span></span>

![Captura de tela de um ator com a janela local do ator aberta](images/unreal-gaze-img-06.png)

- <span data-ttu-id="1b32c-135">Em **EyeTracker. cpp**, adicione inclusões para **EyeTrackerFunctionLibrary** e **DrawDebugHelpers**:</span><span class="sxs-lookup"><span data-stu-id="1b32c-135">In **EyeTracker.cpp**, add includes for **EyeTrackerFunctionLibrary**, and **DrawDebugHelpers**:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="1b32c-136">Verifique se seu dispositivo dá suporte ao acompanhamento de olho com **UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected** antes de tentar obter qualquer dado de olhar.</span><span class="sxs-lookup"><span data-stu-id="1b32c-136">Check that your device supports eye tracking with **UEyeTrackerFunctionLibrary::IsEyeTrackerConnected** before trying to get any gaze data.</span></span>  <span data-ttu-id="1b32c-137">Se o acompanhamento de olho tiver suporte, localize o início e o fim de um raio para um rastreamento de linha de **UEyeTrackerFunctionLibrary:: GetGazeData**.</span><span class="sxs-lookup"><span data-stu-id="1b32c-137">If eye tracking is supported, find the start and end of a ray for a line trace from **UEyeTrackerFunctionLibrary::GetGazeData**.</span></span> <span data-ttu-id="1b32c-138">A partir daí, você pode construir um vetor olhar e passar seu conteúdo para **LineTraceSingleByChannel** para depurar todos os resultados de Ray clique:</span><span class="sxs-lookup"><span data-stu-id="1b32c-138">From there, you can construct a gaze vector and pass its contents to **LineTraceSingleByChannel** to debug any ray hit results:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="1b32c-139">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="1b32c-139">Next Development Checkpoint</span></span>

<span data-ttu-id="1b32c-140">Se você estiver seguindo a jornada de desenvolvimento inreal que apresentamos, você está no meio da exploração dos blocos de construção do MRTK Core.</span><span class="sxs-lookup"><span data-stu-id="1b32c-140">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="1b32c-141">A partir daqui, você pode continuar para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="1b32c-141">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1b32c-142">Acompanhamento da mão</span><span class="sxs-lookup"><span data-stu-id="1b32c-142">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="1b32c-143">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="1b32c-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1b32c-144">Câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="1b32c-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="1b32c-145">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="1b32c-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b32c-146">Veja também</span><span class="sxs-lookup"><span data-stu-id="1b32c-146">See also</span></span>
* [<span data-ttu-id="1b32c-147">Calibragem</span><span class="sxs-lookup"><span data-stu-id="1b32c-147">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="1b32c-148">Conforto</span><span class="sxs-lookup"><span data-stu-id="1b32c-148">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="1b32c-149">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="1b32c-149">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="1b32c-150">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="1b32c-150">Voice input</span></span>](../../out-of-scope/voice-design.md)
