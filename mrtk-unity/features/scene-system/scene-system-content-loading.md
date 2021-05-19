---
title: Carregamento de conteúdo do sistema de cena
description: Documentação carregando o sistema de cena com o MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: f310b3687a6773404c7a998a3764163daf159857
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145147"
---
# <a name="content-scene-loading"></a>Carregamento de cena de conteúdo

Todas as operações de carregamento de conteúdo são assíncronas e, por padrão, todo o carregamento de conteúdo é aditivo. As cenas de iluminação e gerente nunca são afetadas por operações de carregamento de conteúdo. Para obter informações sobre como monitorar o progresso da carga e a ativação de cena, [consulte Monitorando o carregamento de conteúdo.](scene-system-load-progress.md)

## <a name="loading-content"></a>Carregando conteúdo

Para carregar cenas de conteúdo, use o `LoadContent` método :

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a>Carregamento de cena única

O equivalente a uma única carga de cena pode ser obtido por meio do argumento `mode` opcional. `LoadSceneMode.Single` primeiro descarregará todas as cenas de conteúdo carregadas antes de continuar com a carga.

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

## <a name="next--previous-scene-loading"></a>Carregamento de cena seguinte/anterior

O conteúdo pode ser carregado de forma cansada na ordem do índice de build. Isso é útil para demonstrar aplicativos que levam os usuários por meio de um conjunto de cenas de demonstração um por um.

![Cenas atuais no build nas configurações do player](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

Observe que o carregamento de conteúdo next/prev usa LoadSceneMode.Single por padrão para garantir que o conteúdo anterior seja descarregado.

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

`PrevContentExists` retornará true se houver pelo menos uma cena de conteúdo que tenha um índice de build inferior ao índice de build mais baixo carregado no momento. `NextContentExists` retornará true se houver pelo menos uma cena de conteúdo que tenha um índice de build maior do que o índice de build mais alto carregado no momento.

Se o `wrap` argumento for true, o conteúdo retornará um loop para o primeiro/último índice de build. Isso remove a necessidade de verificar se há conteúdo próximo/anterior:

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
ToolsTools | DoNotInclude |
Mountain | Terreno | •
Cabine | Estruturas | •
Árvores | Vegetação | •

---

## <a name="editor-behavior"></a>Comportamento do editor

Você pode executar todas essas operações no editor e no modo de reprodução usando o inspetor de serviço do Sistema [de Cena.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) No modo de edição, as cargas de cena serão instantâneas, enquanto no modo de reprodução você pode observar o progresso do carregamento e usar [tokens de ativação.](scene-system-load-progress.md)

![Sistema de cena no inspetor com carregamento de conteúdo realçada](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
