---
title: Serviço de transição de cena
description: documentação da Transição de Cena no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, SceneTransition,
ms.openlocfilehash: b645012a055f693fdac794b79e24fd20154fdb65
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176212"
---
# <a name="scene-transition-service"></a><span data-ttu-id="8f035-104">Serviço de transição de cena</span><span class="sxs-lookup"><span data-stu-id="8f035-104">Scene transition service</span></span>

<span data-ttu-id="8f035-105">Essa extensão simplifica o negócio de esbotão de uma cena, exibição de um indicador de progresso, carregamento de uma cena e esbotão de volta.</span><span class="sxs-lookup"><span data-stu-id="8f035-105">This extension simplifies the business of fading out a scene, displaying a progress indicator, loading a scene, then fading back in.</span></span>

<span data-ttu-id="8f035-106">As operações de cena são controladas pelo serviço SceneSystem, mas qualquer operação baseada em tarefa pode ser usada para conduzir uma transição.</span><span class="sxs-lookup"><span data-stu-id="8f035-106">Scene operations are driven by the SceneSystem service, but any Task-based operation can be used to drive a transition.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="8f035-107">Habilitando a extensão</span><span class="sxs-lookup"><span data-stu-id="8f035-107">Enabling the extension</span></span>

<span data-ttu-id="8f035-108">Para habilitar a extensão, abra seu perfil RegisteredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="8f035-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="8f035-109">Clique em Registrar um novo Provedor de Serviços para adicionar uma nova configuração.</span><span class="sxs-lookup"><span data-stu-id="8f035-109">Click Register a new Service Provider to add a new configuration.</span></span> <span data-ttu-id="8f035-110">No campo Tipo de Componente, selecione SceneTransitionService.</span><span class="sxs-lookup"><span data-stu-id="8f035-110">In the Component Type field, select SceneTransitionService.</span></span> <span data-ttu-id="8f035-111">No campo Perfil de Configuração, selecione o perfil de transição de cena padrão incluído na extensão.</span><span class="sxs-lookup"><span data-stu-id="8f035-111">In the Configuration Profile field, select the default scene transition profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="8f035-112">Opções de perfil</span><span class="sxs-lookup"><span data-stu-id="8f035-112">Profile options</span></span>

### <a name="use-default-progress-indicator"></a><span data-ttu-id="8f035-113">Usar indicador de progresso padrão</span><span class="sxs-lookup"><span data-stu-id="8f035-113">Use default progress indicator</span></span>

<span data-ttu-id="8f035-114">Se marcada, o pré-padrão do indicador de progresso padrão será usado quando nenhum objeto indicador de progresso for fornecido ao chamar Se um objeto indicador de progresso for fornecido, o padrão `DoSceneTransition.` será ignorado.</span><span class="sxs-lookup"><span data-stu-id="8f035-114">If checked, the default progress indicator prefab will be used when no progress indicator object is provided when calling `DoSceneTransition.` If a progress indicator object is provided, the default will be ignored.</span></span>

### <a name="use-fade-color"></a><span data-ttu-id="8f035-115">Usar cor esmaeçada</span><span class="sxs-lookup"><span data-stu-id="8f035-115">Use fade color</span></span>

<span data-ttu-id="8f035-116">Se marcada, o serviço de transição aplicará um esmaeçando durante a transição.</span><span class="sxs-lookup"><span data-stu-id="8f035-116">If checked, the transition service will apply a fade during your transition.</span></span> <span data-ttu-id="8f035-117">Essa configuração pode ser alterada em runtime por meio da propriedade do `UseFadeColor` serviço.</span><span class="sxs-lookup"><span data-stu-id="8f035-117">This setting can be changed at runtime via the service's `UseFadeColor` property.</span></span>

### <a name="fade-color"></a><span data-ttu-id="8f035-118">Cor de esmaeçada</span><span class="sxs-lookup"><span data-stu-id="8f035-118">Fade color</span></span>

<span data-ttu-id="8f035-119">Controla a cor do efeito de esmaecer.</span><span class="sxs-lookup"><span data-stu-id="8f035-119">Controls the color of the fade effect.</span></span> <span data-ttu-id="8f035-120">Alfa é ignorado.</span><span class="sxs-lookup"><span data-stu-id="8f035-120">Alpha is ignored.</span></span> <span data-ttu-id="8f035-121">Essa configuração pode ser alterada em runtime antes de uma transição por meio da propriedade do `FadeColor` serviço.</span><span class="sxs-lookup"><span data-stu-id="8f035-121">This setting can be changed at runtime prior to a transition via the service's `FadeColor` property.</span></span>

### <a name="fade-targets"></a><span data-ttu-id="8f035-122">Destinos de esmaeçamento</span><span class="sxs-lookup"><span data-stu-id="8f035-122">Fade targets</span></span>

<span data-ttu-id="8f035-123">Controla quais câmeras terão um efeito de esmaeamento aplicado a elas.</span><span class="sxs-lookup"><span data-stu-id="8f035-123">Controls which cameras will have a fade effect applied to them.</span></span> <span data-ttu-id="8f035-124">Essa configuração pode ser alterada em runtime por meio da propriedade do `FadeTargets` serviço.</span><span class="sxs-lookup"><span data-stu-id="8f035-124">This setting can be changed at runtime via the service's `FadeTargets` property.</span></span>

<span data-ttu-id="8f035-125">Configuração</span><span class="sxs-lookup"><span data-stu-id="8f035-125">Setting</span></span> | <span data-ttu-id="8f035-126">Câmeras direcionadas</span><span class="sxs-lookup"><span data-stu-id="8f035-126">Targeted Cameras</span></span>
--- | --- | ---
<span data-ttu-id="8f035-127">Principal</span><span class="sxs-lookup"><span data-stu-id="8f035-127">Main</span></span> | <span data-ttu-id="8f035-128">Aplica o efeito de esmaecer à câmera principal.</span><span class="sxs-lookup"><span data-stu-id="8f035-128">Applies fade effect to the main camera.</span></span>
<span data-ttu-id="8f035-129">Interface do usuário</span><span class="sxs-lookup"><span data-stu-id="8f035-129">UI</span></span> | <span data-ttu-id="8f035-130">Aplica o efeito de esmaecer às câmeras na camada da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="8f035-130">Applies fade effect to cameras on the UI layer.</span></span> <span data-ttu-id="8f035-131">(Não afeta a interface do usuário de sobreposição)</span><span class="sxs-lookup"><span data-stu-id="8f035-131">(Does not affect overlay UI)</span></span>
<span data-ttu-id="8f035-132">Todos</span><span class="sxs-lookup"><span data-stu-id="8f035-132">All</span></span> | <span data-ttu-id="8f035-133">Aplica-se a câmeras principais e de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="8f035-133">Applies to both main and UI cameras.</span></span>
<span data-ttu-id="8f035-134">Personalizado</span><span class="sxs-lookup"><span data-stu-id="8f035-134">Custom</span></span> | <span data-ttu-id="8f035-135">Aplica-se a um conjunto personalizado de câmeras fornecido por meio de `SetCustomFadeTargetCameras`</span><span class="sxs-lookup"><span data-stu-id="8f035-135">Applies to a custom set of cameras provided via `SetCustomFadeTargetCameras`</span></span>

### <a name="fade-out-time--fade-in-time"></a><span data-ttu-id="8f035-136">Esmaeça o tempo/esmaeça no tempo</span><span class="sxs-lookup"><span data-stu-id="8f035-136">Fade out time / fade in time</span></span>

<span data-ttu-id="8f035-137">Configurações padrão para a duração de um esmaeçamento ao entrar/sair de uma transição.</span><span class="sxs-lookup"><span data-stu-id="8f035-137">Default settings for the duration of a fade on entering / exiting a transition.</span></span> <span data-ttu-id="8f035-138">Essas configurações podem ser alteradas em runtime por meio das propriedades `FadeOutTime` e do `FadeInTime` serviço.</span><span class="sxs-lookup"><span data-stu-id="8f035-138">These settings can be changed at runtime via the service's `FadeOutTime` and `FadeInTime` properties.</span></span>

### <a name="camera-fader-type"></a><span data-ttu-id="8f035-139">Tipo de esmaeçador de câmera</span><span class="sxs-lookup"><span data-stu-id="8f035-139">Camera fader type</span></span>

<span data-ttu-id="8f035-140">Qual `ICameraFader` classe usar para aplicar um efeito de esmaecer às câmeras.</span><span class="sxs-lookup"><span data-stu-id="8f035-140">Which `ICameraFader` class to use for applying a fade effect to cameras.</span></span> <span data-ttu-id="8f035-141">A classe padrão instalita um quad com um material transparente na frente da `CameraFaderQuad` câmera de destino perto do plano de clipe.</span><span class="sxs-lookup"><span data-stu-id="8f035-141">The default `CameraFaderQuad` class instantiates a quad with a transparent material in front of the target camera close to the clip plane.</span></span> <span data-ttu-id="8f035-142">Outra abordagem pode ser usar um sistema de pós-efeitos.</span><span class="sxs-lookup"><span data-stu-id="8f035-142">Another approach might be to use a post effects system.</span></span>

## <a name="using-the-extension"></a><span data-ttu-id="8f035-143">Usar a extensão</span><span class="sxs-lookup"><span data-stu-id="8f035-143">Using the extension</span></span>

<span data-ttu-id="8f035-144">Use o serviço de transição passando Tarefas que são executadas enquanto a câmera fica esbotada.</span><span class="sxs-lookup"><span data-stu-id="8f035-144">You use the transition service by passing Tasks that are run while the camera is faded out.</span></span>

### <a name="using-scene-system-tasks"></a><span data-ttu-id="8f035-145">Usando tarefas do sistema de cena</span><span class="sxs-lookup"><span data-stu-id="8f035-145">Using scene system tasks</span></span>

<span data-ttu-id="8f035-146">Na maioria dos casos, você estará usando tarefas fornecidas pelo serviço SceneSystem:</span><span class="sxs-lookup"><span data-stu-id="8f035-146">In most cases you will be using Tasks supplied by the SceneSystem service:</span></span>

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

### <a name="using-custom-tasks"></a><span data-ttu-id="8f035-147">Usando tarefas personalizadas</span><span class="sxs-lookup"><span data-stu-id="8f035-147">Using custom tasks</span></span>

<span data-ttu-id="8f035-148">Em outros casos, talvez você queira executar uma transição sem realmente carregar uma cena:</span><span class="sxs-lookup"><span data-stu-id="8f035-148">In other cases you may want to perform a transition without actually loading a scene:</span></span>

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

<span data-ttu-id="8f035-149">Ou talvez você queira carregar uma cena sem usar o serviço SceneSystem:</span><span class="sxs-lookup"><span data-stu-id="8f035-149">Or you may want to load a scene without using the SceneSystem service:</span></span>

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

### <a name="using-multiple-tasks"></a><span data-ttu-id="8f035-150">Usando várias tarefas</span><span class="sxs-lookup"><span data-stu-id="8f035-150">Using multiple tasks</span></span>

<span data-ttu-id="8f035-151">Você também pode fornecer várias tarefas, que serão executadas na ordem:</span><span class="sxs-lookup"><span data-stu-id="8f035-151">You can also supply multiple tasks, which will be executed in order:</span></span>

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

## <a name="using-the-progress-indicator"></a><span data-ttu-id="8f035-152">Usando o indicador de progresso</span><span class="sxs-lookup"><span data-stu-id="8f035-152">Using the progress indicator</span></span>

<span data-ttu-id="8f035-153">Um indicador de progresso é qualquer coisa que implementa a `IProgressIndicator` interface .</span><span class="sxs-lookup"><span data-stu-id="8f035-153">A progress indicator is anything that implements the `IProgressIndicator` interface.</span></span> <span data-ttu-id="8f035-154">Isso pode assumir a forma de uma tela inicial, um indicador de carregamento 3D tagalong ou qualquer outra coisa que fornece comentários sobre o progresso da transição.</span><span class="sxs-lookup"><span data-stu-id="8f035-154">This can take the form of a splash screen, a 3D tagalong loading indicator, or anything else that provides feedback about transition progress.</span></span>

<span data-ttu-id="8f035-155">Se `UseDefaultProgressIndicator` estiver marcado no perfil SceneTransitionService, um indicador de progresso será instariado quando uma transição for iniciada.</span><span class="sxs-lookup"><span data-stu-id="8f035-155">If `UseDefaultProgressIndicator` is checked in the SceneTransitionService profile, a progress indicator will be instantiated when a transition begins.</span></span> <span data-ttu-id="8f035-156">Durante a transição, as propriedades e desse indicador podem ser acessadas por meio dos `Progress` `Message` métodos e desse `SetProgressValue` `SetProgressMessage` serviço.</span><span class="sxs-lookup"><span data-stu-id="8f035-156">For the duration of the transition this indicator's `Progress` and `Message` properties can be accessed via that service's `SetProgressValue` and `SetProgressMessage` methods.</span></span>

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

<span data-ttu-id="8f035-157">Como alternativa, ao `DoSceneTransition` chamar, você pode fornecer seu próprio indicador de progresso por meio do argumento `progressIndicator` opcional.</span><span class="sxs-lookup"><span data-stu-id="8f035-157">Alternatively, when calling `DoSceneTransition` you can supply your own progress indicator via the optional `progressIndicator` argument.</span></span> <span data-ttu-id="8f035-158">Isso substituirá o indicador de progresso padrão.</span><span class="sxs-lookup"><span data-stu-id="8f035-158">This will override the default progress indicator.</span></span>
