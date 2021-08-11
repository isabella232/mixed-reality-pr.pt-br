---
title: Carregamento de conteúdo do sistema de cena
description: Documentação carregando sistema de cena com MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: df4437a0640637328c3f8f0d78be63a492d4bba15acb8a37bdf2dd3c32d89a59
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223024"
---
# <a name="scene-system-content-loading"></a>Carregamento de conteúdo do sistema de cena

Todas as operações de carga de conteúdo são assíncronas e, por padrão, todo o carregamento de conteúdo é aditivo. Os bastidores de gerente e iluminação nunca são afetados pelas operações de carregamento de conteúdo. Para obter informações sobre como monitorar o progresso da carga e a ativação da cena, consulte [monitorando o carregamento de conteúdo](scene-system-load-progress.md).

## <a name="loading-content"></a>Carregando conteúdo

Para carregar cenas de conteúdo, use o `LoadContent` método:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a>Carregamento de uma única cena

O equivalente a uma única carga de cena pode ser obtido por meio do `mode` argumento opcional. `LoadSceneMode.Single` o descarregará primeiro todas as cenas de conteúdo carregado antes de prosseguir com a carga.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// ContentScene1, ContentScene2 and ContentScene3 will be loaded additively
await sceneSystem.LoadContent("ContentScene1");
await sceneSystem.LoadContent("ContentScene2");
await sceneSystem.LoadContent("ContentScene3");

// ContentScene1, ContentScene2 and ContentScene3 will be unloaded
// SingleContentScene will be loaded additively
await sceneSystem.LoadContent("SingleContentScene", LoadSceneMode.Single);
```

## <a name="next--previous-scene-loading"></a>Carregamento de cena próximo/anterior

O conteúdo pode ser carregado de forma única em ordem de índice de compilação. Isso é útil para aplicativos de demonstração que levam os usuários por meio de um conjunto de cenas de demonstração, um por um.

![Cenas atuais nas configurações de Build no Player](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

Observe que o carregamento de conteúdo próximo/anterior usa loadscenemode. Single por padrão para garantir que o conteúdo anterior seja descarregado.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested && sceneSystem.NextContentExists)
{
    await sceneSystem.LoadNextContent();
}

if (prevSceneRequested && sceneSystem.PrevContentExists)
{
    await sceneSystem.LoadPrevContent();
}
```

`PrevContentExists` retornará true se houver pelo menos uma cena de conteúdo que tenha um índice de compilação inferior ao índice de Build mais baixo carregado no momento. `NextContentExists` retornará true se houver pelo menos uma cena de conteúdo que tenha um índice de compilação maior do que o índice de Build mais alto carregado atualmente.

Se o `wrap` argumento for true, o conteúdo fará um loop de volta para o primeiro/último índice de compilação. Isso elimina a necessidade de verificar o conteúdo seguinte/anterior:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested)
{
    await sceneSystem.LoadNextContent(true);
}

if (prevSceneRequested)
{
    await sceneSystem.LoadPrevContent(true);
}
```

## <a name="loading-by-tag"></a>Carregando por marca

![Carregando cenas de conteúdo por marca](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

Às vezes, é desejável carregar cenas de conteúdo em grupos. Por exemplo, um estágio de uma experiência pode ser composto de várias cenas, que devem ser carregadas simultaneamente para funcionar. Para facilitar isso, você pode marcar seus bastidores e, em seguida, carregá-los ou descarregá-los com essa marca.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

O carregamento por marca também pode ser útil se os artistas desejam incorporar/remover elementos de uma experiência sem precisar modificar scripts. Por exemplo, a execução desse script com os dois conjuntos de marcas a seguir produz resultados diferentes:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a>Testando conteúdo

Nome da cena | Marca de cena | Carregado por script
---|---|---
DebugTerrainPhysics | Levo | •
StructureTesting | Estruturas | •
VegetationTools | Vegetação | •
Mountain | Levo | •
Cabine | Estruturas | •
Árvores | Vegetação | •

### <a name="final-content"></a>Conteúdo final

Nome da cena | Marca de cena | Carregado por script
---|---|---
DebugTerrainPhysics | DoNotInclude |
StructureTesting | DoNotInclude |
VegetationTools | DoNotInclude |
Mountain | Levo | •
Cabine | Estruturas | •
Árvores | Vegetação | •

---

## <a name="editor-behavior"></a>Comportamento do editor

Você pode executar todas essas operações no editor e no modo de reprodução usando o [Inspetor de serviço](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) do sistema de cena. No modo de edição, as cargas de cena serão instantâneas, enquanto no modo de reprodução você pode observar o progresso do carregamento e usar [tokens de ativação.](scene-system-load-progress.md)

![Sistema de cena no Inspetor com o carregamento de conteúdo realçado](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
