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
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="816a0-104">Mapeamento espacial no Unreal</span><span class="sxs-lookup"><span data-stu-id="816a0-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="816a0-105">O mapeamento espacial torna possível posicionar objetos em superfícies no mundo físico, mostrando o mundo em todo o HoloLens, o que torna os hologramas mais reais para o usuário.</span><span class="sxs-lookup"><span data-stu-id="816a0-105">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="816a0-106">O mapeamento espacial também ancora objetos no mundo do usuário, tirando proveito de indicações de profundidade do mundo real. Isso ajuda a convencer o usuário de que esses hologramas estão na verdade no espaço dele; hologramas que flutuam no espaço ou se movem com o usuário não parecem tão reais.</span><span class="sxs-lookup"><span data-stu-id="816a0-106">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="816a0-107">Sempre que possível, convém que você posicione os itens a fim de obter um maior conforto.</span><span class="sxs-lookup"><span data-stu-id="816a0-107">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="816a0-108">No documento [Mapeamento espacial](../../design/spatial-mapping.md), você pode encontrar mais informações sobre posicionamento, oclusão, renderização e qualidade do mapeamento espacial, além de outras informações.</span><span class="sxs-lookup"><span data-stu-id="816a0-108">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](../../design/spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="816a0-109">Como habilitar o mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="816a0-109">Enabling Spatial Mapping</span></span>

<span data-ttu-id="816a0-110">Para habilitar o mapeamento espacial no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="816a0-110">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="816a0-111">Abra **Editar > Configurações do Projeto** e role para baixo até a seção **Plataformas**.</span><span class="sxs-lookup"><span data-stu-id="816a0-111">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="816a0-112">Selecione **HoloLens** e marque **Percepção Espacial**.</span><span class="sxs-lookup"><span data-stu-id="816a0-112">Select **HoloLens** and check **Spatial Perception**.</span></span>

![Captura de tela das funcionalidades de configurações de projeto do HoloLens com a percepção espacial realçada](images/unreal-spatial-mapping-img-01.png)

<span data-ttu-id="816a0-114">Para aceitar o mapeamento espacial e depurar o **MRMesh** em um jogo do HoloLens:</span><span class="sxs-lookup"><span data-stu-id="816a0-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="816a0-115">Abra o **ARSessionConfig** e expanda a seção **ARSettings > Mapeamento do Mundo**.</span><span class="sxs-lookup"><span data-stu-id="816a0-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="816a0-116">Verifique **Gerar Dados de Malha de Geometria Rastreada**, que diz ao plug-in do HoloLens para iniciar a obtenção assíncrona de dados de mapeamento espacial e exibi-los no Unreal por meio do **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="816a0-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="816a0-117">Marque **Renderizar Dados de Malha em Grade de Linhas** para mostrar um contorno de grade de linhas branco de todos os triângulos no **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="816a0-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![Armazenamento de âncoras espaciais pronto](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="816a0-119">Mapeamento espacial em runtime</span><span class="sxs-lookup"><span data-stu-id="816a0-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="816a0-120">Você pode modificar os seguintes parâmetros para atualizar o comportamento do runtime de mapeamento espacial:</span><span class="sxs-lookup"><span data-stu-id="816a0-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="816a0-121">Abra **Editar > Configurações de Projeto**, role para baixo até a seção **Plataformas** e selecione **HoloLens > Mapeamento Espacial**:</span><span class="sxs-lookup"><span data-stu-id="816a0-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![Configurações do projeto de âncoras espaciais](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="816a0-123">A opção **Máximo de Triângulos por Metro Cúbico** atualiza a densidade dos triângulos na malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="816a0-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="816a0-124">A opção **Tamanho do Volume de Malha Espacial** é o tamanho do cubo em volta do jogador para renderizar e atualizar os dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="816a0-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="816a0-125">Se for previsto que o ambiente do runtime do aplicativo será grande, esse valor precisará ser grande para corresponder ao espaço do mundo real.</span><span class="sxs-lookup"><span data-stu-id="816a0-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="816a0-126">Por outro lado, se o aplicativo precisar apenas posicionar hologramas nas superfícies imediatamente próximas do usuário, esse campo poderá ser menor.</span><span class="sxs-lookup"><span data-stu-id="816a0-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="816a0-127">À medida que o usuário se movimenta pelo mundo, o volume de mapeamento espacial se moverá com ele.</span><span class="sxs-lookup"><span data-stu-id="816a0-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="816a0-128">Como trabalhar com o MRMesh</span><span class="sxs-lookup"><span data-stu-id="816a0-128">Working with MRMesh</span></span>

<span data-ttu-id="816a0-129">Primeiro, você precisa iniciar o mapeamento espacial:</span><span class="sxs-lookup"><span data-stu-id="816a0-129">First, you need to start Spatial Mapping:</span></span>

![Blueprint da função ToggleARCapture com o tipo de captura do mapeamento espacial realçado](images/unreal-spatial-mapping-img-02.png)

<span data-ttu-id="816a0-131">Depois que o mapeamento espacial é capturado para o espaço, recomendamos desativá-lo.</span><span class="sxs-lookup"><span data-stu-id="816a0-131">Once spatial mapping has been captured for the space, we recommend toggling spatial mapping off.</span></span>  <span data-ttu-id="816a0-132">O mapeamento espacial poderá ser concluído após determinado período ou quando as conversões de raio em cada direção retornarem colisões na MRMesh.</span><span class="sxs-lookup"><span data-stu-id="816a0-132">The spatial mapping may be completed either after a certain amount of time, or when raycasts in each direction return collisions against the MRMesh.</span></span>

<span data-ttu-id="816a0-133">Para obter acesso ao **MRMesh** em runtime:</span><span class="sxs-lookup"><span data-stu-id="816a0-133">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="816a0-134">Adicione um componente **ARTrackableNotify** a um ator do Blueprint.</span><span class="sxs-lookup"><span data-stu-id="816a0-134">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![AR Trackable Notify de âncoras espaciais](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="816a0-136">Selecione o componente **ARTrackableNotify** e expanda a seção **Eventos** no painel **Detalhes**.</span><span class="sxs-lookup"><span data-stu-id="816a0-136">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="816a0-137">Clique no botão **+** nos eventos que você deseja monitorar.</span><span class="sxs-lookup"><span data-stu-id="816a0-137">Click the **+** button on the events you want to monitor.</span></span> 

![Eventos de âncoras espaciais](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="816a0-139">Nesse caso, o evento **adicionar geometria rastreada** está sendo monitorado, o qual procura malhas válidas do mundo que correspondem aos dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="816a0-139">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="816a0-140">Você pode encontrar a lista completa de eventos na API do componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="816a0-140">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="816a0-141">Você pode alterar o material da malha no Gráfico de Eventos do Blueprint ou no C++.</span><span class="sxs-lookup"><span data-stu-id="816a0-141">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="816a0-142">A captura de tela a seguir mostra a rota de Blueprint:</span><span class="sxs-lookup"><span data-stu-id="816a0-142">The screenshot below shows the Blueprint route:</span></span> 

![Exemplo de âncoras espaciais](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a><span data-ttu-id="816a0-144">Mapeamento espacial em C++</span><span class="sxs-lookup"><span data-stu-id="816a0-144">Spatial Mapping in C++</span></span>

<span data-ttu-id="816a0-145">No arquivo build.cs do jogo, adicione **AugmentedReality** e **MRMesh** à lista PublicDependencyModuleNames:</span><span class="sxs-lookup"><span data-stu-id="816a0-145">In your game's build.cs file, add **AugmentedReality** and **MRMesh** to the PublicDependencyModuleNames list:</span></span>

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

<span data-ttu-id="816a0-146">Para acessar a MRMesh, assine os delegados de **OnTrackableAdded**:</span><span class="sxs-lookup"><span data-stu-id="816a0-146">To access the MRMesh, subscribe to the **OnTrackableAdded** delegates:</span></span>

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
> <span data-ttu-id="816a0-147">Há delegados semelhantes para eventos atualizados e removidos, **AddOnTrackableUpdatedDelegate_Handle** e **AddOnTrackableRemovedDelegate_Handle**, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="816a0-147">There are similar delegates for updated and removed events, **AddOnTrackableUpdatedDelegate_Handle** and **AddOnTrackableRemovedDelegate_Handle** respectively.</span></span>
>
> <span data-ttu-id="816a0-148">Você pode encontrar a lista completa de eventos na API de [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).</span><span class="sxs-lookup"><span data-stu-id="816a0-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="816a0-149">Veja também</span><span class="sxs-lookup"><span data-stu-id="816a0-149">See also</span></span>
* [<span data-ttu-id="816a0-150">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="816a0-150">Spatial mapping</span></span>](../../design/spatial-mapping.md)
