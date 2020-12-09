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
# <a name="gaze-input"></a>Entrada olhar

A entrada olhar em aplicativos de realidade misturada é como descobrir o que os usuários estão olhando. Quando as câmeras de acompanhamento de olho em seu dispositivo correspondem a raios no espaço do mundo inreal, a linha de dados de visão do usuário fica disponível. O olhar pode ser usado em plantas e em C++ e é um recurso fundamental para a mecânica, como interação de objeto, localização e controles de câmera.

## <a name="enabling-eye-tracking"></a>Habilitando o acompanhamento de olho

- Em **configurações do projeto > HoloLens**, habilite o recurso de **entrada olhar** :

![Captura de tela de recursos de configuração do projeto de HoloLens com entrada olhar realçada](images/unreal-gaze-img-01.png)

- Criar um novo ator e adicioná-lo à sua cena

> [!NOTE]
> O controle de olhos do HoloLens em tempo inreal tem apenas um único olhar Ray para ambos os olhos. O acompanhamento de estereoscópico, que requer dois raios, não tem suporte.

## <a name="using-eye-tracking"></a>Como usar o acompanhamento ocular

Primeiro, verifique se seu dispositivo dá suporte ao controle de olho com a função **IsEyeTrackerConnected** .  Se a função retornar true, chame **GetGazeData** para descobrir onde os olhos do usuário estão olhando no quadro atual:

![Plano gráfico da função conectada de acompanhamento de olho](images/unreal-gaze-img-02.png)

> [!NOTE]
> O ponto fixação da e o valor de confiança não estão disponíveis no HoloLens.

Use a origem e a direção do olhar em um rastreamento de linha para descobrir exatamente onde os usuários estão olhando.  O valor de olhar é um vetor, começando na origem de olhar e terminando na origem mais a direção de olhar multiplicada pela distância de rastreamento de linha:

![Plano gráfico da função obter dados olhar](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>Obtendo orientação de cabeçalho

Você também pode usar a rotação da exibição montada de cabeçalho (HMD) para representar a direção do cabeçalho do usuário. Você pode obter a direção do cabeçalho dos usuários sem habilitar a funcionalidade de entrada olhar, mas não terá nenhuma informação de acompanhamento de olho.  Adicione uma referência ao plano gráfico como o contexto mundial para obter os dados de saída corretos:

> [!NOTE]
> Obter dados de HMD só está disponível em versões inreals de 4,26 e em diante.

![Plano gráfico da função Get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>Usando C++

- No arquivo **Build.cs** do jogo, adicione **EyeTracker** à lista **PublicDependencyModuleNames** :

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

- Em **arquivo/nova classe c++**, crie um novo ator de C++ chamado **EyeTracker**
    - Uma solução do Visual Studio abrirá a nova classe EyeTracker. Compile e execute para abrir o jogo não real com o novo ator EyeTracker.  Pesquise "EyeTracker" na janela **posicionar atores** e arraste e solte a classe na janela do jogo para adicioná-la ao projeto:

![Captura de tela de um ator com a janela local do ator aberta](images/unreal-gaze-img-06.png)

- Em **EyeTracker. cpp**, adicione inclusões para **EyeTrackerFunctionLibrary** e **DrawDebugHelpers**:

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

Verifique se seu dispositivo dá suporte ao acompanhamento de olho com **UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected** antes de tentar obter qualquer dado de olhar.  Se o acompanhamento de olho tiver suporte, localize o início e o fim de um raio para um rastreamento de linha de **UEyeTrackerFunctionLibrary:: GetGazeData**. A partir daí, você pode construir um vetor olhar e passar seu conteúdo para **LineTraceSingleByChannel** para depurar todos os resultados de Ray clique:

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

Se você estiver seguindo a jornada de desenvolvimento inreal que apresentamos, você está no meio da exploração dos blocos de construção do MRTK Core. A partir daqui, você pode continuar para o próximo bloco de construção:

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
