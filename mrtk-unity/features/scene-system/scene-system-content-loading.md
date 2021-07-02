---
title: Carregamento de conteúdo do sistema de cena
description: Documentação carregando o sistema de cena com o MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: c6bc6474afd50fe265853e53c0f29009d816cf51
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177583"
---
# <a name="scene-system-content-loading"></a>Carregamento de conteúdo do sistema de cena

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

Às vezes, é desejável carregar cenas de conteúdo em grupos. Por exemplo, um estágio de uma experiência pode ser composto por várias cenas, todas elas devem ser carregadas simultaneamente para funcionar. Para facilitar isso, você pode marcar suas cenas e carregá-las ou descarregá-las com essa marca.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

Carregar por marca também poderá ser útil se os canhões quiserem incorporar/remover elementos de uma experiência sem precisar modificar scripts. Por exemplo, executar esse script com os dois conjuntos de marcas a seguir produz resultados diferentes:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a>Testar conteúdo

Nome da cena | Marca de cena | Carregado por script
---|---|---
DebugTerrainPhysics | Terreno | •
StructureTesting | Estruturas | •
ToolsTools | Vegetação | •
Mountain | Terreno | •
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
