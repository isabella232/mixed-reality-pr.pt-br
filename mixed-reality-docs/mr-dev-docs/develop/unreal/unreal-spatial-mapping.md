---
title: Mapeamento espacial no Unreal
description: Guia para usar o mapeamento espacial no Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, mapeamento espacial, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 878eae5f5fd0b7a1630511faa23c1477455ed988
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354364"
---
# <a name="spatial-mapping-in-unreal"></a>Mapeamento espacial no Unreal

O mapeamento espacial torna possível posicionar objetos em superfícies no mundo físico, mostrando o mundo em todo o HoloLens, o que torna os hologramas mais reais para o usuário. O mapeamento espacial também ancora objetos no mundo do usuário, tirando proveito de indicações de profundidade do mundo real. Isso ajuda a convencer o usuário de que esses hologramas estão na verdade no espaço dele; hologramas que flutuam no espaço ou se movem com o usuário não parecem tão reais. Sempre que possível, convém que você posicione os itens a fim de obter um maior conforto.

No documento [Mapeamento espacial](../../design/spatial-mapping.md), você pode encontrar mais informações sobre posicionamento, oclusão, renderização e qualidade do mapeamento espacial, além de outras informações.

## <a name="enabling-spatial-mapping"></a>Como habilitar o mapeamento espacial

Para habilitar o mapeamento espacial no HoloLens:
- Abra **Editar > Configurações do Projeto** e role para baixo até a seção **Plataformas**.    
    + Selecione **HoloLens** e marque **Percepção Espacial**.

![Captura de tela das funcionalidades de configurações de projeto do HoloLens com a percepção espacial realçada](images/unreal-spatial-mapping-img-01.png)

Para aceitar o mapeamento espacial e depurar o **MRMesh** em um jogo do HoloLens:
1. Abra o **ARSessionConfig** e expanda a seção **ARSettings > Mapeamento do Mundo**. 

2. Verifique **Gerar Dados de Malha de Geometria Rastreada**, que diz ao plug-in do HoloLens para iniciar a obtenção assíncrona de dados de mapeamento espacial e exibi-los no Unreal por meio do **MRMesh**. 
3. Marque **Renderizar Dados de Malha em Grade de Linhas** para mostrar um contorno de grade de linhas branco de todos os triângulos no **MRMesh**. 

![Armazenamento de âncoras espaciais pronto](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>Mapeamento espacial em runtime
Você pode modificar os seguintes parâmetros para atualizar o comportamento do runtime de mapeamento espacial:

- Abra **Editar > Configurações de Projeto**, role para baixo até a seção **Plataformas** e selecione **HoloLens > Mapeamento Espacial**: 

![Configurações do projeto de âncoras espaciais](images/unreal-spatialmapping-projectsettings.PNG)

- A opção **Máximo de Triângulos por Metro Cúbico** atualiza a densidade dos triângulos na malha de mapeamento espacial.  
- A opção **Tamanho do Volume de Malha Espacial** é o tamanho do cubo em volta do jogador para renderizar e atualizar os dados de mapeamento espacial.  
    + Se for previsto que o ambiente do runtime do aplicativo será grande, esse valor precisará ser grande para corresponder ao espaço do mundo real.  Por outro lado, se o aplicativo precisar apenas posicionar hologramas nas superfícies imediatamente próximas do usuário, esse campo poderá ser menor. À medida que o usuário se movimenta pelo mundo, o volume de mapeamento espacial se moverá com ele. 

## <a name="working-with-mrmesh"></a>Como trabalhar com o MRMesh

Primeiro, você precisa iniciar o mapeamento espacial:

![Blueprint da função ToggleARCapture com o tipo de captura do mapeamento espacial realçado](images/unreal-spatial-mapping-img-02.png)

Depois que o mapeamento espacial é capturado para o espaço, recomendamos desativá-lo.  O mapeamento espacial poderá ser concluído após determinado período ou quando as conversões de raio em cada direção retornarem colisões na MRMesh.

Para obter acesso ao **MRMesh** em runtime:
1. Adicione um componente **ARTrackableNotify** a um ator do Blueprint. 

![AR Trackable Notify de âncoras espaciais](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Selecione o componente **ARTrackableNotify** e expanda a seção **Eventos** no painel **Detalhes**. 
    - Clique no botão **+** nos eventos que você deseja monitorar. 

![Eventos de âncoras espaciais](images/unreal-spatialmapping-events.PNG)

Nesse caso, o evento **adicionar geometria rastreada** está sendo monitorado, o qual procura malhas válidas do mundo que correspondem aos dados de mapeamento espacial. Você pode encontrar a lista completa de eventos na API do componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html). 

Você pode alterar o material da malha no Gráfico de Eventos do Blueprint ou no C++. A captura de tela a seguir mostra a rota de Blueprint: 

![Exemplo de âncoras espaciais](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a>Mapeamento espacial em C++

No arquivo build.cs do jogo, adicione **AugmentedReality** e **MRMesh** à lista PublicDependencyModuleNames:

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",    
        "EyeTracker",
        "AugmentedReality",
        "MRMesh"
});
```

Para acessar a MRMesh, assine os delegados de **OnTrackableAdded**:

```cpp
#include "ARBlueprintLibrary.h"
#include "MRMeshComponent.h"

void AARTrackableMonitor::BeginPlay()
{
    Super::BeginPlay();

    // Subscribe to Tracked Geometry delegates
    UARBlueprintLibrary::AddOnTrackableAddedDelegate_Handle(
        FOnTrackableAddedDelegate::CreateUObject(this, &AARTrackableMonitor::OnTrackableAdded)
    );
}

void AARTrackableMonitor::OnTrackableAdded(UARTrackedGeometry* Added)
{
    // When tracked geometry is received, check that it's from spatial mapping
    if(Added->GetObjectClassification() == EARObjectClassification::World)
    {
        UMRMeshComponent* MRMesh = Added->GetUnderlyingMesh();
    }
}
```

> [!NOTE]
> Há delegados semelhantes para eventos atualizados e removidos, **AddOnTrackableUpdatedDelegate_Handle** e **AddOnTrackableRemovedDelegate_Handle**, respectivamente.
>
> Você pode encontrar a lista completa de eventos na API de [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).

## <a name="see-also"></a>Veja também
* [Mapeamento espacial](../../design/spatial-mapping.md)
