---
title: Progresso do carregamento do sistema de cena
description: Documentação sobre o carregamento de conteúdo de cenas no MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 51b5d4d00d65491a0476068bbdc256ffce67412b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144407"
---
# <a name="monitoring-content-loading"></a><span data-ttu-id="ff8bd-104">Monitorando o carregamento de conteúdo</span><span class="sxs-lookup"><span data-stu-id="ff8bd-104">Monitoring content loading</span></span>

## <a name="scene-operation-progress"></a><span data-ttu-id="ff8bd-105">Progresso da operação de cena</span><span class="sxs-lookup"><span data-stu-id="ff8bd-105">Scene operation progress</span></span>

<span data-ttu-id="ff8bd-106">Quando o conteúdo está sendo carregado ou descarregado, a `SceneOperationInProgress` propriedade retornará true.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-106">When content is being loaded or unloaded, the `SceneOperationInProgress` property will return true.</span></span> <span data-ttu-id="ff8bd-107">Você pode monitorar o progresso dessa operação por meio da `SceneOperationProgress` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-107">You can monitor the progress of this operation via the `SceneOperationProgress` property.</span></span>

<span data-ttu-id="ff8bd-108">O `SceneOperationProgress` valor é a média de todas as operações de cena assíncronas atuais.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-108">The `SceneOperationProgress` value is the average of all current async scene operations.</span></span> <span data-ttu-id="ff8bd-109">No início de uma carga de conteúdo, `SceneOperationProgress` será zero.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-109">At the start of a content load, `SceneOperationProgress` will be zero.</span></span> <span data-ttu-id="ff8bd-110">Após a conclusão completa, `SceneOperationProgress` será definido como 1 e permanecerá em 1 até que a próxima operação ocorra.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-110">Once fully completed, `SceneOperationProgress` will be set to 1 and will remain at 1 until the next operation takes place.</span></span> <span data-ttu-id="ff8bd-111">Observe que apenas as operações de cena de conteúdo afetam essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-111">Note that only content scene operations affect these properties.</span></span>

<span data-ttu-id="ff8bd-112">Essas propriedades refletem o estado de uma *operação inteira* do início ao fim, mesmo que essa operação inclua várias etapas:</span><span class="sxs-lookup"><span data-stu-id="ff8bd-112">These properties reflect the state of an *entire operation* from start to finish, even if that operation includes multiple steps:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// First do an additive scene load
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
await sceneSystem.LoadContent("ContentScene1");

// Now do a single scene load
// This will result in two actions back-to-back
// First "ContentScene1" will be unloaded
// Then "ContentScene2" will be loaded
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
sceneSystem.LoadContent("ContentScene2", LoadSceneMode.Single)
```

### <a name="progress-examples"></a><span data-ttu-id="ff8bd-113">Exemplos de progresso</span><span class="sxs-lookup"><span data-stu-id="ff8bd-113">Progress examples</span></span>

<span data-ttu-id="ff8bd-114">`SceneOperationInProgress` pode ser útil se a atividade deve ser suspensa enquanto o conteúdo está sendo carregado:</span><span class="sxs-lookup"><span data-stu-id="ff8bd-114">`SceneOperationInProgress` can be useful if activity should be suspended while content is being loaded:</span></span>

```c#
public class FooManager : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        // Don't update foos while a scene operation is in progress
        if (sceneSystem.SceneOperationInProgress)
        {
            return;
        }

        // Update foos
        ...
    }
    ...
}
```

<span data-ttu-id="ff8bd-115">`SceneOperationProgress` pode ser usado para exibir caixas de diálogo de progresso:</span><span class="sxs-lookup"><span data-stu-id="ff8bd-115">`SceneOperationProgress` can be used to display progress dialogs:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        if (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
        }
        else
        {
            HideProgressIndicator();
        }
    }
    ...
}
```

---

## <a name="monitoring-with-actions"></a><span data-ttu-id="ff8bd-116">Monitoramento com ações</span><span class="sxs-lookup"><span data-stu-id="ff8bd-116">Monitoring with actions</span></span>

<span data-ttu-id="ff8bd-117">O sistema de cena fornece várias ações para permitir que você saiba quando as cenas estão sendo carregadas ou descarregadas.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-117">The Scene System provides several actions to let you know when scenes are being loaded or unloaded.</span></span> <span data-ttu-id="ff8bd-118">Cada ação retransmite o nome da cena afetada.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-118">Each action relays the name of the affected scene.</span></span>

<span data-ttu-id="ff8bd-119">Se uma operação de carregamento ou descarregamento envolver várias cenas, as ações relevantes serão invocadas uma vez por cena afetada.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-119">If a load or unload operation involves multiple scenes, the relevant actions will be invoked once per affected scene.</span></span> <span data-ttu-id="ff8bd-120">Eles também são invocados de uma só vez quando a operação de carregamento ou descarregamento está *totalmente concluída.*</span><span class="sxs-lookup"><span data-stu-id="ff8bd-120">They are also invoked all at once when the load or unload operation is *fully completed.*</span></span> <span data-ttu-id="ff8bd-121">Por esse motivo, é recomendável que você use ações de *OnWillUnload* para detectar o conteúdo que *será* destruído, em oposição ao uso de ações *onunloadd* para detectar conteúdo destruído após o fato.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-121">For this reason it's recommended that you use *OnWillUnload* actions to detect content that *will* be destroyed, as opposed to using *OnUnloaded* actions to detect destroyed content after the fact.</span></span>

<span data-ttu-id="ff8bd-122">No lado do inverso, como as ações não *carregadas* são invocadas apenas quando todas as cenas são ativadas e totalmente carregadas, o uso de ações *descarregadas* para detectar e usar um novo conteúdo é garantido como seguro.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-122">On the flip side, because *OnLoaded* actions are only invoked when all scenes are activated and fully loaded, using *OnLoaded* actions to detect and use new content is guaranteed to be safe.</span></span>

<span data-ttu-id="ff8bd-123">Ação</span><span class="sxs-lookup"><span data-stu-id="ff8bd-123">Action</span></span> | <span data-ttu-id="ff8bd-124">Quando é invocado</span><span class="sxs-lookup"><span data-stu-id="ff8bd-124">When it's invoked</span></span> | <span data-ttu-id="ff8bd-125">Cenas de conteúdo</span><span class="sxs-lookup"><span data-stu-id="ff8bd-125">Content Scenes</span></span> | <span data-ttu-id="ff8bd-126">Cenas de iluminação</span><span class="sxs-lookup"><span data-stu-id="ff8bd-126">Lighting Scenes</span></span> | <span data-ttu-id="ff8bd-127">Cenas do gerente</span><span class="sxs-lookup"><span data-stu-id="ff8bd-127">Manager Scenes</span></span>
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | <span data-ttu-id="ff8bd-128">Logo antes da carga de uma cena de conteúdo</span><span class="sxs-lookup"><span data-stu-id="ff8bd-128">Just prior to a content scene load</span></span> | <span data-ttu-id="ff8bd-129">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-129">•</span></span> | |  
`OnContentLoaded` | <span data-ttu-id="ff8bd-130">Depois que todos os bastidores de conteúdo em uma operação de carregamento tiverem sido totalmente carregados e ativados</span><span class="sxs-lookup"><span data-stu-id="ff8bd-130">After all content scenes in a load operation have been fully loaded and activated</span></span> | <span data-ttu-id="ff8bd-131">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-131">•</span></span> | |
`OnWillUnloadContent` | <span data-ttu-id="ff8bd-132">Logo antes de uma operação de descarregamento de cena de conteúdo</span><span class="sxs-lookup"><span data-stu-id="ff8bd-132">Just prior to a content scene unload operation</span></span> | <span data-ttu-id="ff8bd-133">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-133">•</span></span> | |
`OnContentUnloaded` | <span data-ttu-id="ff8bd-134">Depois que todos os bastidores de conteúdo em uma operação de descarregamento tiverem sido totalmente descarregados</span><span class="sxs-lookup"><span data-stu-id="ff8bd-134">After all content scenes in an unload operation have been fully unloaded</span></span> | <span data-ttu-id="ff8bd-135">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-135">•</span></span> | |
`OnWillLoadLighting` | <span data-ttu-id="ff8bd-136">Logo antes da carga da cena de iluminação</span><span class="sxs-lookup"><span data-stu-id="ff8bd-136">Just prior to a lighting scene load</span></span> | | <span data-ttu-id="ff8bd-137">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-137">•</span></span> |
`OnLightingLoaded` | <span data-ttu-id="ff8bd-138">Depois que uma cena de iluminação tiver sido totalmente carregada e ativada</span><span class="sxs-lookup"><span data-stu-id="ff8bd-138">After a lighting scene has been fully loaded and activated</span></span>| | <span data-ttu-id="ff8bd-139">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-139">•</span></span> |
`OnWillUnloadLighting` | <span data-ttu-id="ff8bd-140">Logo antes de um descarregamento da cena de iluminação</span><span class="sxs-lookup"><span data-stu-id="ff8bd-140">Just prior to a lighting scene unload</span></span> | | <span data-ttu-id="ff8bd-141">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-141">•</span></span> |
`OnLightingUnloaded` | <span data-ttu-id="ff8bd-142">Depois que uma cena de iluminação tiver sido totalmente descarregada</span><span class="sxs-lookup"><span data-stu-id="ff8bd-142">After a lighting scene has been fully unloaded</span></span> | | <span data-ttu-id="ff8bd-143">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-143">•</span></span> |
`OnWillLoadScene` | <span data-ttu-id="ff8bd-144">Logo antes de uma carga de cena</span><span class="sxs-lookup"><span data-stu-id="ff8bd-144">Just prior to a scene load</span></span> | <span data-ttu-id="ff8bd-145">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-145">•</span></span> | <span data-ttu-id="ff8bd-146">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-146">•</span></span> | <span data-ttu-id="ff8bd-147">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-147">•</span></span>
`OnSceneLoaded` | <span data-ttu-id="ff8bd-148">Depois que todas as cenas em uma operação são totalmente carregadas e ativadas</span><span class="sxs-lookup"><span data-stu-id="ff8bd-148">After all scenes in an operation are fully loaded and activated</span></span> | <span data-ttu-id="ff8bd-149">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-149">•</span></span> | <span data-ttu-id="ff8bd-150">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-150">•</span></span> | <span data-ttu-id="ff8bd-151">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-151">•</span></span>
`OnWillUnloadScene` | <span data-ttu-id="ff8bd-152">Logo antes do descarregamento de uma cena</span><span class="sxs-lookup"><span data-stu-id="ff8bd-152">Just prior to a scene unload</span></span> | <span data-ttu-id="ff8bd-153">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-153">•</span></span> | <span data-ttu-id="ff8bd-154">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-154">•</span></span> | <span data-ttu-id="ff8bd-155">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-155">•</span></span>
`OnSceneUnloaded` | <span data-ttu-id="ff8bd-156">Depois que uma cena é totalmente descarregada</span><span class="sxs-lookup"><span data-stu-id="ff8bd-156">After a scene is fully unloaded</span></span> |  <span data-ttu-id="ff8bd-157">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-157">•</span></span> | <span data-ttu-id="ff8bd-158">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-158">•</span></span> | <span data-ttu-id="ff8bd-159">•</span><span class="sxs-lookup"><span data-stu-id="ff8bd-159">•</span></span>

### <a name="action-examples"></a><span data-ttu-id="ff8bd-160">Exemplos de ação</span><span class="sxs-lookup"><span data-stu-id="ff8bd-160">Action examples</span></span>

<span data-ttu-id="ff8bd-161">Outro exemplo de caixa de diálogo de progresso usando ações e uma corrotina em vez de atualizar:</span><span class="sxs-lookup"><span data-stu-id="ff8bd-161">Another progress dialog example using actions and a coroutine instead of Update:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private bool displayingProgress = false;

    private void Start()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
        sceneSystem.OnWillLoadContent += HandleSceneOperation;
        sceneSystem.OnWillUnloadContent += HandleSceneOperation;
    }

    private void HandleSceneOperation (string sceneName)
    {
        // This may be invoked multiple times per frame - once per scene being loaded or unloaded.
        // So filter the events appropriately.
        if (displayingProgress)
        {
            return;
        }

        displayingProgress = true;
        StartCoroutine(DisplayProgress());
    }

    private IEnumerator DisplayProgress()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        while (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
            yield return null;
        }

        HideProgressIndicator();
        displayingProgress = false;
    }

    ...
}
```

---

## <a name="controlling-scene-activation"></a><span data-ttu-id="ff8bd-162">Controlando a ativação de cena</span><span class="sxs-lookup"><span data-stu-id="ff8bd-162">Controlling scene activation</span></span>

<span data-ttu-id="ff8bd-163">Por padrão, as cenas de conteúdo são definidas como ativar quando carregadas.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-163">By default content scenes are set to activate when loaded.</span></span> <span data-ttu-id="ff8bd-164">Se você quiser controlar a ativação de cena manualmente, poderá passar um para `SceneActivationToken` qualquer método de carregamento de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-164">If you want to control scene activation manually, you can pass a `SceneActivationToken` to any content load method.</span></span> <span data-ttu-id="ff8bd-165">Se várias cenas de conteúdo estão sendo carregadas por uma única operação, esse token de ativação será aplicado a todas as cenas.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-165">If multiple content scenes are being loaded by a single operation, this activation token will apply to all scenes.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

SceneActivationToken activationToken = new SceneActivationToken();

// Load the content and pass the activation token
sceneSystem.LoadContent(new string[] { "ContentScene1", "ContentScene2", "ContentScene3" }, LoadSceneMode.Additive, activationToken);

// Wait until all users have joined the experience
while (!AllUsersHaveJoinedExperience())
{
    await Task.Yield();
}

// Let scene system know we're ready to activate all scenes
activationToken.AllowSceneActivation = true;

// Wait for all scenes to be fully loaded and activated
while (sceneSystem.SceneOperationInProgress)
{
    await Task.Yield();
}

// Proceed with experience
```

---

## <a name="checking-which-content-is-loaded"></a><span data-ttu-id="ff8bd-166">Verificando qual conteúdo é carregado</span><span class="sxs-lookup"><span data-stu-id="ff8bd-166">Checking which content is loaded</span></span>

<span data-ttu-id="ff8bd-167">A `ContentSceneNames` propriedade fornece uma matriz de cenas de conteúdo disponíveis na ordem do índice de build.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-167">The `ContentSceneNames` property provides an array of available content scenes in order of build index.</span></span> <span data-ttu-id="ff8bd-168">Você pode verificar se essas cenas são carregadas por meio de `IsContentLoaded(string contentName)` .</span><span class="sxs-lookup"><span data-stu-id="ff8bd-168">You can check whether these scenes are loaded via `IsContentLoaded(string contentName)`.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
