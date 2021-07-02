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
# <a name="scene-system-content-loading"></a><span data-ttu-id="85a38-104">Carregamento de conteúdo do sistema de cena</span><span class="sxs-lookup"><span data-stu-id="85a38-104">Scene system content loading</span></span>

<span data-ttu-id="85a38-105">Todas as operações de carregamento de conteúdo são assíncronas e, por padrão, todo o carregamento de conteúdo é aditivo.</span><span class="sxs-lookup"><span data-stu-id="85a38-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="85a38-106">As cenas de iluminação e gerente nunca são afetadas por operações de carregamento de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="85a38-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="85a38-107">Para obter informações sobre como monitorar o progresso da carga e a ativação de cena, [consulte Monitorando o carregamento de conteúdo.](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="85a38-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](scene-system-load-progress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="85a38-108">Carregando conteúdo</span><span class="sxs-lookup"><span data-stu-id="85a38-108">Loading content</span></span>

<span data-ttu-id="85a38-109">Para carregar cenas de conteúdo, use o `LoadContent` método :</span><span class="sxs-lookup"><span data-stu-id="85a38-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="85a38-110">Carregamento de cena única</span><span class="sxs-lookup"><span data-stu-id="85a38-110">Single scene loading</span></span>

<span data-ttu-id="85a38-111">O equivalente a uma única carga de cena pode ser obtido por meio do argumento `mode` opcional.</span><span class="sxs-lookup"><span data-stu-id="85a38-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="85a38-112">`LoadSceneMode.Single` primeiro descarregará todas as cenas de conteúdo carregadas antes de continuar com a carga.</span><span class="sxs-lookup"><span data-stu-id="85a38-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

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

## <a name="next--previous-scene-loading"></a><span data-ttu-id="85a38-113">Carregamento de cena seguinte/anterior</span><span class="sxs-lookup"><span data-stu-id="85a38-113">Next / previous scene loading</span></span>

<span data-ttu-id="85a38-114">O conteúdo pode ser carregado de forma cansada na ordem do índice de build.</span><span class="sxs-lookup"><span data-stu-id="85a38-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="85a38-115">Isso é útil para demonstrar aplicativos que levam os usuários por meio de um conjunto de cenas de demonstração um por um.</span><span class="sxs-lookup"><span data-stu-id="85a38-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

![Cenas atuais no build nas configurações do player](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="85a38-117">Observe que o carregamento de conteúdo next/prev usa LoadSceneMode.Single por padrão para garantir que o conteúdo anterior seja descarregado.</span><span class="sxs-lookup"><span data-stu-id="85a38-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

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

<span data-ttu-id="85a38-118">`PrevContentExists` retornará true se houver pelo menos uma cena de conteúdo que tenha um índice de build inferior ao índice de build mais baixo carregado no momento.</span><span class="sxs-lookup"><span data-stu-id="85a38-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="85a38-119">`NextContentExists` retornará true se houver pelo menos uma cena de conteúdo que tenha um índice de build maior do que o índice de build mais alto carregado no momento.</span><span class="sxs-lookup"><span data-stu-id="85a38-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="85a38-120">Se o `wrap` argumento for true, o conteúdo retornará um loop para o primeiro/último índice de build.</span><span class="sxs-lookup"><span data-stu-id="85a38-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="85a38-121">Isso remove a necessidade de verificar se há conteúdo próximo/anterior:</span><span class="sxs-lookup"><span data-stu-id="85a38-121">This removes the need to check for next / previous content:</span></span>

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

## <a name="loading-by-tag"></a><span data-ttu-id="85a38-122">Carregando por marca</span><span class="sxs-lookup"><span data-stu-id="85a38-122">Loading by tag</span></span>

![Carregando cenas de conteúdo por marca](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="85a38-124">Às vezes, é desejável carregar cenas de conteúdo em grupos.</span><span class="sxs-lookup"><span data-stu-id="85a38-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="85a38-125">Por exemplo, um estágio de uma experiência pode ser composto por várias cenas, todas elas devem ser carregadas simultaneamente para funcionar.</span><span class="sxs-lookup"><span data-stu-id="85a38-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="85a38-126">Para facilitar isso, você pode marcar suas cenas e carregá-las ou descarregá-las com essa marca.</span><span class="sxs-lookup"><span data-stu-id="85a38-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="85a38-127">Carregar por marca também poderá ser útil se os canhões quiserem incorporar/remover elementos de uma experiência sem precisar modificar scripts.</span><span class="sxs-lookup"><span data-stu-id="85a38-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="85a38-128">Por exemplo, executar esse script com os dois conjuntos de marcas a seguir produz resultados diferentes:</span><span class="sxs-lookup"><span data-stu-id="85a38-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="85a38-129">Testar conteúdo</span><span class="sxs-lookup"><span data-stu-id="85a38-129">Testing content</span></span>

<span data-ttu-id="85a38-130">Nome da cena</span><span class="sxs-lookup"><span data-stu-id="85a38-130">Scene Name</span></span> | <span data-ttu-id="85a38-131">Marca de cena</span><span class="sxs-lookup"><span data-stu-id="85a38-131">Scene Tag</span></span> | <span data-ttu-id="85a38-132">Carregado por script</span><span class="sxs-lookup"><span data-stu-id="85a38-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="85a38-133">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="85a38-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="85a38-134">Terreno</span><span class="sxs-lookup"><span data-stu-id="85a38-134">Terrain</span></span> | <span data-ttu-id="85a38-135">•</span><span class="sxs-lookup"><span data-stu-id="85a38-135">•</span></span>
<span data-ttu-id="85a38-136">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="85a38-136">StructureTesting</span></span> | <span data-ttu-id="85a38-137">Estruturas</span><span class="sxs-lookup"><span data-stu-id="85a38-137">Structures</span></span> | <span data-ttu-id="85a38-138">•</span><span class="sxs-lookup"><span data-stu-id="85a38-138">•</span></span>
<span data-ttu-id="85a38-139">ToolsTools</span><span class="sxs-lookup"><span data-stu-id="85a38-139">VegetationTools</span></span> | <span data-ttu-id="85a38-140">Vegetação</span><span class="sxs-lookup"><span data-stu-id="85a38-140">Vegetation</span></span> | <span data-ttu-id="85a38-141">•</span><span class="sxs-lookup"><span data-stu-id="85a38-141">•</span></span>
<span data-ttu-id="85a38-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="85a38-142">Mountain</span></span> | <span data-ttu-id="85a38-143">Terreno</span><span class="sxs-lookup"><span data-stu-id="85a38-143">Terrain</span></span> | <span data-ttu-id="85a38-144">•</span><span class="sxs-lookup"><span data-stu-id="85a38-144">•</span></span>
<span data-ttu-id="85a38-145">Cabine</span><span class="sxs-lookup"><span data-stu-id="85a38-145">Cabin</span></span> | <span data-ttu-id="85a38-146">Estruturas</span><span class="sxs-lookup"><span data-stu-id="85a38-146">Structures</span></span> | <span data-ttu-id="85a38-147">•</span><span class="sxs-lookup"><span data-stu-id="85a38-147">•</span></span>
<span data-ttu-id="85a38-148">Árvores</span><span class="sxs-lookup"><span data-stu-id="85a38-148">Trees</span></span> | <span data-ttu-id="85a38-149">Vegetação</span><span class="sxs-lookup"><span data-stu-id="85a38-149">Vegetation</span></span> | <span data-ttu-id="85a38-150">•</span><span class="sxs-lookup"><span data-stu-id="85a38-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="85a38-151">Conteúdo final</span><span class="sxs-lookup"><span data-stu-id="85a38-151">Final content</span></span>

<span data-ttu-id="85a38-152">Nome da cena</span><span class="sxs-lookup"><span data-stu-id="85a38-152">Scene Name</span></span> | <span data-ttu-id="85a38-153">Marca de cena</span><span class="sxs-lookup"><span data-stu-id="85a38-153">Scene Tag</span></span> | <span data-ttu-id="85a38-154">Carregado por script</span><span class="sxs-lookup"><span data-stu-id="85a38-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="85a38-155">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="85a38-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="85a38-156">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="85a38-156">DoNotInclude</span></span> |
<span data-ttu-id="85a38-157">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="85a38-157">StructureTesting</span></span> | <span data-ttu-id="85a38-158">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="85a38-158">DoNotInclude</span></span> |
<span data-ttu-id="85a38-159">ToolsTools</span><span class="sxs-lookup"><span data-stu-id="85a38-159">VegetationTools</span></span> | <span data-ttu-id="85a38-160">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="85a38-160">DoNotInclude</span></span> |
<span data-ttu-id="85a38-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="85a38-161">Mountain</span></span> | <span data-ttu-id="85a38-162">Terreno</span><span class="sxs-lookup"><span data-stu-id="85a38-162">Terrain</span></span> | <span data-ttu-id="85a38-163">•</span><span class="sxs-lookup"><span data-stu-id="85a38-163">•</span></span>
<span data-ttu-id="85a38-164">Cabine</span><span class="sxs-lookup"><span data-stu-id="85a38-164">Cabin</span></span> | <span data-ttu-id="85a38-165">Estruturas</span><span class="sxs-lookup"><span data-stu-id="85a38-165">Structures</span></span> | <span data-ttu-id="85a38-166">•</span><span class="sxs-lookup"><span data-stu-id="85a38-166">•</span></span>
<span data-ttu-id="85a38-167">Árvores</span><span class="sxs-lookup"><span data-stu-id="85a38-167">Trees</span></span> | <span data-ttu-id="85a38-168">Vegetação</span><span class="sxs-lookup"><span data-stu-id="85a38-168">Vegetation</span></span> | <span data-ttu-id="85a38-169">•</span><span class="sxs-lookup"><span data-stu-id="85a38-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="85a38-170">Comportamento do editor</span><span class="sxs-lookup"><span data-stu-id="85a38-170">Editor behavior</span></span>

<span data-ttu-id="85a38-171">Você pode executar todas essas operações no editor e no modo de reprodução usando o inspetor de serviço do Sistema [de Cena.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span><span class="sxs-lookup"><span data-stu-id="85a38-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="85a38-172">No modo de edição, as cargas de cena serão instantâneas, enquanto no modo de reprodução você pode observar o progresso do carregamento e usar [tokens de ativação.](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="85a38-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](scene-system-load-progress.md)</span></span>

![Sistema de cena no inspetor com carregamento de conteúdo realçada](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
