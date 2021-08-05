---
title: Progresso do carregamento do sistema de cena
description: Documentação sobre o carregamento de conteúdo de cenas no MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 1d2382e11092b20aca5bf8480ade521ffb94a70a325540e70487d7f581e8cf15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186612"
---
# <a name="monitoring-content-loading"></a>Monitorando o carregamento de conteúdo

## <a name="scene-operation-progress"></a>Progresso da operação de cena

Quando o conteúdo estiver sendo carregado ou descarregado, a `SceneOperationInProgress` propriedade retornará true. Você pode monitorar o progresso dessa operação por meio da `SceneOperationProgress` propriedade .

O `SceneOperationProgress` valor é a média de todas as operações de cena assíncronas atuais. No início de uma carga de conteúdo, `SceneOperationProgress` será zero. Depois de concluído, `SceneOperationProgress` será definido como 1 e permanecerá em 1 até que a próxima operação seja realizada. Observe que somente as operações de cena de conteúdo afetam essas propriedades.

Essas propriedades refletem o estado de uma *operação inteira* do início ao fim, mesmo que essa operação inclua várias etapas:

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

### <a name="progress-examples"></a>Exemplos de progresso

`SceneOperationInProgress` pode ser útil se a atividade deve ser suspensa enquanto o conteúdo está sendo carregado:

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

`SceneOperationProgress` pode ser usado para exibir diálogos de progresso:

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

## <a name="monitoring-with-actions"></a>Monitoramento com ações

O Sistema de Cena fornece várias ações para que você saiba quando as cenas estão sendo carregadas ou descarregadas. Cada ação retransmite o nome da cena afetada.

Se uma operação de carregamento ou descarregamento envolver várias cenas, as ações relevantes serão invocadas uma vez por cena afetada. Eles também são invocados de uma só vez quando a operação de carregamento ou descarregamento *é totalmente concluída.* Por esse motivo, é recomendável que você use ações  *OnWillUnload* para detectar o conteúdo que será destruído, em vez de usar ações *OnUnloaded* para detectar o conteúdo destruído após o fato.

Por outro lado, como as ações *OnLoaded* só são invocadas quando todas as cenas são ativadas e totalmente carregadas, é garantido que o uso de ações *OnLoaded* para detectar e usar o novo conteúdo seja seguro.

Ação | Quando ele é invocado | Cenas de conteúdo | Cenas de iluminação | Cenas do gerente
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | Logo antes de uma carga de cena de conteúdo | • | |  
`OnContentLoaded` | Depois que todas as cenas de conteúdo em uma operação de carregamento foram totalmente carregadas e ativadas | • | |
`OnWillUnloadContent` | Logo antes de uma operação de descarregamento de cena de conteúdo | • | |
`OnContentUnloaded` | Depois que todas as cenas de conteúdo em uma operação de descarregamento foram totalmente descarregadas | • | |
`OnWillLoadLighting` | Logo antes de uma carga de cena de iluminação | | • |
`OnLightingLoaded` | Depois que uma cena de iluminação tiver sido totalmente carregada e ativada| | • |
`OnWillUnloadLighting` | Logo antes de um descarregamento de cena de iluminação | | • |
`OnLightingUnloaded` | Depois que uma cena de iluminação tiver sido totalmente descarregada | | • |
`OnWillLoadScene` | Logo antes de uma carga de cena | • | • | •
`OnSceneLoaded` | Depois que todas as cenas em uma operação são totalmente carregadas e ativadas | • | • | •
`OnWillUnloadScene` | Logo antes de um descarregamento de cena | • | • | •
`OnSceneUnloaded` | Depois que uma cena é totalmente descarregada |  • | • | •

### <a name="action-examples"></a>Exemplos de ação

Outro exemplo de caixa de diálogo de progresso usando ações e uma coroutine em vez de Atualizar:

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

## <a name="controlling-scene-activation"></a>Controlando a ativação de cena

Por padrão, as cenas de conteúdo são definidas para ativar quando carregadas. Se você quiser controlar a ativação de cena manualmente, poderá passar um para `SceneActivationToken` qualquer método de carregamento de conteúdo. Se várias cenas de conteúdo estão sendo carregadas por uma única operação, esse token de ativação será aplicado a todas as cenas.

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

## <a name="checking-which-content-is-loaded"></a>Verificando qual conteúdo é carregado

A `ContentSceneNames` propriedade fornece uma matriz de cenas de conteúdo disponíveis na ordem do índice de build. Você pode verificar se essas cenas são carregadas por meio de `IsContentLoaded(string contentName)` .

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
