---
title: Entrada olhar em não real
description: Tutorial sobre como configurar a entrada de olhar para o HoloLens e o mecanismo inreal
author: hferrone
ms.author: jacksonf
ms.date: 06/10/2020
ms.topic: article
keywords: Realidade mista do Windows, hologramas, HoloLens 2, controle de olho, entrada de olhar, exibição montada de cabeçalho, mecanismo inreal, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: d0470c5abbefce797254aa9f2030519d3347aaab
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96578885"
---
# <a name="gaze-input"></a>Entrada olhar

Olhar é usado para indicar o que o usuário está olhando.  Isso usa as câmeras de controle de olho no dispositivo para encontrar um raio de espaço do mundo inreal correspondente ao que o usuário está vendo no momento.

## <a name="enabling-eye-tracking"></a>Habilitando o acompanhamento de olho

- Em **configurações do projeto > HoloLens**, habilite o recurso de **entrada olhar** :

![Captura de tela de recursos de configuração do projeto de HoloLens com entrada olhar realçada](images/unreal-gaze-img-01.png)

- Criar um novo ator e adicioná-lo à sua cena

> [!NOTE] 
> O controle de olhos do HoloLens em tempo inreal tem apenas um único olhar Ray para ambos os olhos, em vez dos dois raios necessários para o acompanhamento do estereoscópico, o que não é suportado.

## <a name="using-eye-tracking"></a>Como usar o acompanhamento ocular

Primeiro, verifique se o dispositivo dá suporte ao acompanhamento de olho com a função IsEyeTrackerConnected.  Se isso retornar true, chame GetGazeData para descobrir onde os olhos do usuário estão olhando durante o quadro atual:

![Plano gráfico da função conectada de acompanhamento de olho](images/unreal-gaze-img-02.png)

> [!NOTE]
> O ponto fixação da e o valor de confiança não estão disponíveis no HoloLens.

Para localizar o que o usuário está olhando, use a origem e a direção do olhar em um rastreamento de linha.  O início desse vetor é a origem olhar e o final é a origem mais a direção olhar multiplicada pela distância desejada:

![Plano gráfico da função obter dados olhar](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>Obtendo orientação de cabeçalho

Como alternativa, a rotação HMD pode ser usada para representar a direção do cabeçalho do usuário.  Isso não exige o recurso de entrada do olhar, mas não lhe dará informações de controle de olho.  Uma referência ao plano gráfico deve ser adicionada como o contexto mundial para obter os dados de saída corretos:

> [!NOTE]
> Obter dados de HMD só está disponível em versões inreals de 4,26 e em diante.

![Plano gráfico da função Get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>Usando C++ 

- No arquivo build.cs do jogo, adicione "EyeTracker" à lista PublicDependencyModuleNames:

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

- Em "arquivo/nova classe C++", crie um novo ator de C++ chamado "EyeTracker"
    - Uma solução do Visual Studio será aberta para a nova classe EyeTracker. Compile e execute para abrir o jogo não real com o novo ator EyeTracker.  Pesquise "EyeTracker" na janela "posicionar atores".  Arraste e solte essa classe na janela do jogo para adicioná-la ao projeto:

![Captura de tela de um ator com a janela local do ator aberta](images/unreal-gaze-img-06.png)

- Em EyeTracker. cpp, adicione inclusões para EyeTrackerFunctionLibrary e DrawDebugHelpers:

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

Em tique, verifique se o dispositivo dá suporte ao acompanhamento de olho com UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected.  Em seguida, localize o início e o final de um raio para um rastreamento de linha de UEyeTrackerFunctionLibrary:: GetGazeData:

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

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unreal, você está no meio da exploração dos principais blocos de construção do MRTK. De lá, você pode prosseguir para o próximo bloco de construção: 

> [!div class="nextstepaction"]
> [Acompanhamento da mão](unreal-hand-tracking.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Câmera do HoloLens](unreal-hololens-camera.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Veja também
* [Calibragem](../../calibration.md)
* [Conforto](../../design/comfort.md)
* [Focar e confirmar](../../design/gaze-and-commit.md)
* [Entrada de voz](../../out-of-scope/voice-design.md)
