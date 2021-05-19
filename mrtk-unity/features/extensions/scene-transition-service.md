---
title: Visão geral do serviço de transição de cena
description: documentação da Transição de Cena no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, SceneTransition,
ms.openlocfilehash: 5ea76b572b3cddc097e8266d3c31f152b63a13aa
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144281"
---
# <a name="scene-transition-service"></a>Serviço de transição de cena

Essa extensão simplifica o negócio de esbotão de uma cena, exibição de um indicador de progresso, carregamento de uma cena e esbotão de volta.

As operações de cena são controladas pelo serviço SceneSystem, mas qualquer operação baseada em tarefa pode ser usada para conduzir uma transição.

## <a name="enabling-the-extension"></a>Habilitando a extensão

Para habilitar a extensão, abra seu perfil RegisteredServiceProvider. Clique em Registrar um novo Provedor de Serviços para adicionar uma nova configuração. No campo Tipo de Componente, selecione SceneTransitionService. No campo Perfil de Configuração, selecione o perfil de transição de cena padrão incluído na extensão.

## <a name="profile-options"></a>Opções de perfil

### <a name="use-default-progress-indicator"></a>Usar indicador de progresso padrão

Se marcada, o pré-padrão do indicador de progresso padrão será usado quando nenhum objeto indicador de progresso for fornecido ao chamar Se um objeto indicador de progresso for fornecido, o padrão `DoSceneTransition.` será ignorado.

### <a name="use-fade-color"></a>Usar cor esmaeçada

Se marcada, o serviço de transição aplicará um esmaeçando durante a transição. Essa configuração pode ser alterada em runtime por meio da propriedade do `UseFadeColor` serviço.

### <a name="fade-color"></a>Cor de esmaeçada

Controla a cor do efeito de esmaecer. Alfa é ignorado. Essa configuração pode ser alterada em runtime antes de uma transição por meio da propriedade do `FadeColor` serviço.

### <a name="fade-targets"></a>Desbotar destinos

Controla quais câmeras terão um efeito de esmaecimento aplicado a elas. Essa configuração pode ser alterada em tempo de execução por meio da Propriedade do serviço `FadeTargets` .

Configuração | Câmeras de destino
--- | --- | ---
Principal | Aplica o efeito de esmaecimento à câmera principal.
Interface do usuário | Aplica o efeito de esmaecimento a câmeras na camada de interface do usuário. (Não afeta a sobreposição da interface do usuário)
Todos | Aplica-se às câmeras principal e da interface do usuário.
Personalizado | Aplica-se a um conjunto personalizado de câmeras fornecidas por meio do `SetCustomFadeTargetCameras`

### <a name="fade-out-time--fade-in-time"></a>Fade out do tempo/esmaecimento no tempo

Configurações padrão para a duração de um fade ao entrar/sair de uma transição. Essas configurações podem ser alteradas em tempo de execução por meio das `FadeOutTime` Propriedades e do serviço `FadeInTime` .

### <a name="camera-fader-type"></a>Tipo de Fader da câmera

Qual `ICameraFader` classe usar para aplicar um efeito de esmaecimento a câmeras. A `CameraFaderQuad` classe padrão instancia um quad com um material transparente na frente da câmera de destino perto do plano de corte. Outra abordagem pode ser usar um sistema de efeitos de postagem.

## <a name="using-the-extension"></a>Usar a extensão

Você usa o serviço de transição passando tarefas que são executadas enquanto a câmera está desbotada.

### <a name="using-scene-system-tasks"></a>Usando tarefas do sistema de cena

Na maioria dos casos, você usará as tarefas fornecidas pelo serviço SceneSystem:

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Runs LoadContent task
    // Fades back in
    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}
```

### <a name="using-custom-tasks"></a>Usando tarefas personalizadas

Em outros casos, talvez você queira executar uma transição sem realmente carregar uma cena:

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Resets scene
    // Fades back in
    await transition.DoSceneTransition(
            () => ResetScene()
        );
}

private async Task ResetScene()
{
    // Go through all enemies in the current scene and move them back to starting positions
}
```

Ou talvez você queira carregar uma cena sem usar o serviço SceneSystem:

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Loads scene using Unity's scene manager
    // Fades back in
    await transition.DoSceneTransition(
            () => LoadScene("TestScene1")
        );
}

private async Task LoadScene(string sceneName)
{
    AsyncOperation asyncOp = SceneManager.LoadSceneAsync(sceneName, LoadSceneMode.Additive);
    while (!asyncOp.isDone)
    {
        await Task.Yield();
    }
}
```

### <a name="using-multiple-tasks"></a>Usando várias tarefas

Você também pode fornecer várias tarefas, que serão executadas na ordem:

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Sets time scale to 0
    // Fades out audio to 0
    // Loads TestScene1
    // Fades in audio to 1
    // Sets time scale to 1
    // Fades back in
    await transition.DoSceneTransition(
            () => SetTimescale(0f),
            () => FadeAudio(0f, 1f),
            () => sceneSystem.LoadContent("TestScene1"),
            () => FadeAudio(1f, 1f),
            () => SetTimescale(1f)
        );
}

private async Task SetTimescale(float targetTime)
{
    Time.timeScale = targetTime;
    await Task.Yield();
}

private async Task FadeAudio(float targetVolume, float duration)
{
    float startTime = Time.realtimeSinceStartup;
    float startVolume = AudioListener.volume;
    while (Time.realtimeSinceStartup < startTime + duration)
    {
        AudioListener.volume = Mathf.Lerp(startVolume, targetVolume, Time.realtimeSinceStartup - startTime / duration);
        await Task.Yield();
       }
       AudioListener.volume = targetVolume;
}
```

## <a name="using-the-progress-indicator"></a>Usando o indicador de progresso

Um indicador de progresso é qualquer coisa que implemente a `IProgressIndicator` interface. Isso pode assumir a forma de uma tela inicial, um indicador de carregamento de que 3D ou qualquer outra coisa que forneça comentários sobre o progresso da transição.

Se `UseDefaultProgressIndicator` o for verificado no perfil SceneTransitionService, um indicador de progresso será instanciado quando uma transição for iniciada. Para a duração da transição, esse indicador `Progress` e `Message` as propriedades podem ser acessados por meio desse serviço `SetProgressValue` e `SetProgressMessage` métodos.

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    ListenToSceneTransition(sceneSystem, transition);

    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}

private async void ListenToSceneTransition(IMixedRealitySceneSystem sceneSystem, ISceneTransitionService transition)
{
    transition.SetProgressMessage("Starting transition...");

    while (transition.TransitionInProgress)
    {
        if (sceneSystem.SceneOperationInProgress)
        {
            transition.SetProgressMessage("Loading scene...");
            transition.SetProgressValue(sceneSystem.SceneOperationProgress);
        }
        else
        {
            transition.SetProgressMessage("Finished loading scene...");
            transition.SetProgressValue(1);
        }

        await Task.Yield();
    }
}
```

Como alternativa, ao chamar, `DoSceneTransition` você pode fornecer seu próprio indicador de progresso por meio do `progressIndicator` argumento opcional. Isso substituirá o indicador de progresso padrão.
