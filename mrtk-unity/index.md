---
title: Documentação do desenvolvedor do MRTK-Unity
description: Saiba mais sobre o Kit de Ferramentas de Realidade Misturada para Unity.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK
ms.openlocfilehash: 85a203f22c62871265f7775c364f5388194b53a1
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550966"
---
# <a name="what-is-the-mixed-reality-toolkit"></a><span data-ttu-id="cab60-104">O que é o Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="cab60-104">What is the Mixed Reality Toolkit</span></span>

![Kit de ferramentas de realidade misturada](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="cab60-106">MRTK-Unity é um projeto conduzido pela Microsoft que fornece um conjunto de componentes e recursos usados para acelerar o desenvolvimento de aplicativos MR de plataforma cruzada no Unity.</span><span class="sxs-lookup"><span data-stu-id="cab60-106">MRTK-Unity is a Microsoft-driven project that provides a set of components and features, used to accelerate cross-platform MR app development in Unity.</span></span> <span data-ttu-id="cab60-107">Confira algumas funções dele abaixo:</span><span class="sxs-lookup"><span data-stu-id="cab60-107">Here are some of its functions:</span></span>

* <span data-ttu-id="cab60-108">Fornece o **sistema de entrada multiplataforma e os blocos de construção para interações espaciais e interface do usuário**.</span><span class="sxs-lookup"><span data-stu-id="cab60-108">Provides the **cross-platform input system and building blocks for spatial interactions and UI**.</span></span>
* <span data-ttu-id="cab60-109">Habilita a **prototipagem rápida** por meio de simulação no editor, que permite ver as alterações imediatamente.</span><span class="sxs-lookup"><span data-stu-id="cab60-109">Enables **rapid prototyping** via in-editor simulation that allows you to see changes immediately.</span></span>
* <span data-ttu-id="cab60-110">Opera como uma **estrutura extensível** que fornece aos desenvolvedores a capacidade de trocar componentes principais.</span><span class="sxs-lookup"><span data-stu-id="cab60-110">Operates as an **extensible framework** that provides developers the ability to swap out core components.</span></span>
* <span data-ttu-id="cab60-111">**Dá suporte a uma ampla gama de plataformas**, incluindo</span><span class="sxs-lookup"><span data-stu-id="cab60-111">**Supports a wide range of platforms**, including</span></span>
  * <span data-ttu-id="cab60-112">OpenXR (Unity 2020.2 ou mais recente)</span><span class="sxs-lookup"><span data-stu-id="cab60-112">OpenXR (Unity 2020.2 or newer)</span></span>
    * <span data-ttu-id="cab60-113">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cab60-113">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="cab60-114">Headsets do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="cab60-114">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="cab60-115">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="cab60-115">Windows Mixed Reality</span></span>
    * <span data-ttu-id="cab60-116">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="cab60-116">Microsoft HoloLens</span></span>
    * <span data-ttu-id="cab60-117">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cab60-117">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="cab60-118">Headsets do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="cab60-118">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="cab60-119">Oculus (Unity 2019.3 ou mais recente)</span><span class="sxs-lookup"><span data-stu-id="cab60-119">Oculus (Unity 2019.3 or newer)</span></span>
    * <span data-ttu-id="cab60-120">Solicitação Oculus</span><span class="sxs-lookup"><span data-stu-id="cab60-120">Oculus Quest</span></span>
  * <span data-ttu-id="cab60-121">OpenVR</span><span class="sxs-lookup"><span data-stu-id="cab60-121">OpenVR</span></span>
    * <span data-ttu-id="cab60-122">Headsets do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="cab60-122">Windows Mixed Reality headsets</span></span>
    * <span data-ttu-id="cab60-123">HTC Vive</span><span class="sxs-lookup"><span data-stu-id="cab60-123">HTC Vive</span></span>
    * <span data-ttu-id="cab60-124">Oculus Rift</span><span class="sxs-lookup"><span data-stu-id="cab60-124">Oculus Rift</span></span>
  * <span data-ttu-id="cab60-125">Acompanhamento de mãos Ultraleap</span><span class="sxs-lookup"><span data-stu-id="cab60-125">Ultraleap Hand Tracking</span></span>
  * <span data-ttu-id="cab60-126">Dispositivos móveis, como iOS e Android</span><span class="sxs-lookup"><span data-stu-id="cab60-126">Mobile devices such as iOS and Android</span></span>

## <a name="getting-started-with-mrtk"></a><span data-ttu-id="cab60-127">Introdução ao MRTK</span><span class="sxs-lookup"><span data-stu-id="cab60-127">Getting started with MRTK</span></span>

<span data-ttu-id="cab60-128">Se você for novo no MRTK ou no desenvolvimento de realidade misturada no Unity, recomendamos que instale as ferramentas necessárias e siga a série de tutoriais do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cab60-128">If you're new to MRTK or Mixed Reality development in Unity, we recommend you install the necessary tools and then follow the HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cab60-129">Instalar as ferramentas</span><span class="sxs-lookup"><span data-stu-id="cab60-129">Install the Tools</span></span>](install-the-tools.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="cab60-130">Série de tutoriais do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cab60-130">HoloLens 2 Tutorial Series</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

<span data-ttu-id="cab60-131">Quer ver o que está acontecendo nos bastidores?</span><span class="sxs-lookup"><span data-stu-id="cab60-131">Want to see what's going on under the hood?</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="cab60-132">Explorar o MRTK no GitHub</span><span class="sxs-lookup"><span data-stu-id="cab60-132">Explore MRTK on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a><span data-ttu-id="cab60-133">Documentação</span><span class="sxs-lookup"><span data-stu-id="cab60-133">Documentation</span></span>

| <span data-ttu-id="cab60-134">[![Notas de Versão](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-134">[![Release notes](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span></span><br/>[<span data-ttu-id="cab60-135">Notas sobre a versão</span><span class="sxs-lookup"><span data-stu-id="cab60-135">Release Notes</span></span>](release-notes/mrtk-26-release-notes.md)| <span data-ttu-id="cab60-136">[![Visão geral do MRTK](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-136">[![MRTK Overview](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span></span><br/>[<span data-ttu-id="cab60-137">Visão geral do MRTK</span><span class="sxs-lookup"><span data-stu-id="cab60-137">MRTK Overview</span></span>](architecture/overview.md)|<span data-ttu-id="cab60-138">[![Referência de API](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span><span class="sxs-lookup"><span data-stu-id="cab60-138">[![API Reference](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span></span><br/>[<span data-ttu-id="cab60-139">Referência da API</span><span class="sxs-lookup"><span data-stu-id="cab60-139">API Reference</span></span>](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a><span data-ttu-id="cab60-140">Status do Build</span><span class="sxs-lookup"><span data-stu-id="cab60-140">Build status</span></span>

| <span data-ttu-id="cab60-141">Branch</span><span class="sxs-lookup"><span data-stu-id="cab60-141">Branch</span></span> | <span data-ttu-id="cab60-142">Status de CI</span><span class="sxs-lookup"><span data-stu-id="cab60-142">CI Status</span></span> | <span data-ttu-id="cab60-143">Status dos documentos</span><span class="sxs-lookup"><span data-stu-id="cab60-143">Docs Status</span></span> |
|---|---|---|
| `mrtk_development` |<span data-ttu-id="cab60-144">[![Status de CI](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span><span class="sxs-lookup"><span data-stu-id="cab60-144">[![CI Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span></span>|<span data-ttu-id="cab60-145">[![Status dos documentos](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span><span class="sxs-lookup"><span data-stu-id="cab60-145">[![Docs Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span></span>

## <a name="feature-areas"></a><span data-ttu-id="cab60-146">Áreas de recursos</span><span class="sxs-lookup"><span data-stu-id="cab60-146">Feature areas</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="cab60-147">[![Sistema de entrada](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-147">[![Input System](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="cab60-148">**[Sistema de entrada](features/input/overview.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-148">**[Input System](features/input/overview.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-149">[![Acompanhamento da Mão (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-149">[![Hand Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="cab60-150">**[Acompanhamento da Mão <br> (HoloLens 2)](features/input/hand-tracking.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-150">**[Hand Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-151">[![Acompanhamento Ocular (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-151">[![Eye Tracking (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span></span><br>
        <span data-ttu-id="cab60-152">**[Acompanhamento Ocular <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-152">**[Eye Tracking <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-153">[![Perfis](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-153">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span></span><br>
        <span data-ttu-id="cab60-154">**[Perfis](configuration/mixed-reality-configuration-guide.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-154">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="cab60-155">[![Acompanhamento da Mão (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-155">[![Hand Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span></span><br>
        <span data-ttu-id="cab60-156">**[Acompanhamento da Mão <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-156">**[Hand Tracking <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-157">[![Controles de interface do usuário](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="cab60-157">[![UI Controls](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span></span><br>
        <span data-ttu-id="cab60-158">**[Controles de interface do usuário](#ux-building-blocks)**</span><span class="sxs-lookup"><span data-stu-id="cab60-158">**[UI Controls](#ux-building-blocks)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-159">[![Solucionadores](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-159">[![Solvers](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span></span><br>
        <span data-ttu-id="cab60-160">**[Solucionadores](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-160">**[Solvers](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-161">[![Gerenciador de várias cenas](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-161">[![Multi-Scene Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="cab60-162">**[Gerenciador<br/> de várias cenas](features/scene-system/scene-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-162">**[Multi-Scene<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="cab60-163">[![Conscientização espacial](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-163">[![Spatial Awareness](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span></span><br>
        <span data-ttu-id="cab60-164">**[Conscientização <br/> espacial](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-164">**[Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-165">[![Ferramenta de diagnóstico](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-165">[![Diagnostic Tool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="cab60-166">**[Ferramenta <br/> de diagnóstico](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-166">**[Diagnostic <br/> Tool](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-167">[![Exibição do Sombreador Padrão do MRTK](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span><span class="sxs-lookup"><span data-stu-id="cab60-167">[![MRTK Standard Shader View](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span></span><br>
        <span data-ttu-id="cab60-168">**[Exibição de exemplo do Sombreador Padrão do MRTK](features/rendering/mrtk-standard-shader.md?q=shader)**</span><span class="sxs-lookup"><span data-stu-id="cab60-168">**[MRTK Standard Shader Example View](features/rendering/mrtk-standard-shader.md?q=shader)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-169">[![Fala e Ditado](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-169">[![Speech & Dictation](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="cab60-170">**[Fala](features/input/speech.md)<br/> & [Ditado](features/input/dictation.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-170">**[Speech](features/input/speech.md)<br/> & [Dictation](features/input/dictation.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="cab60-171">[![Sistema de limite](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-171">[![Boundary System](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span></span><br>
        <span data-ttu-id="cab60-172">**[Sistema <br/>de limite](features/boundary/boundary-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-172">**[Boundary <br/>System](features/boundary/boundary-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-173">[![Simulação no Editor](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-173">[![In-Editor Simulation](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="cab60-174">**[Simulação <br/> no Editor](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-174">**[In-Editor <br/> Simulation](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-175">[![Recursos experimentais](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-175">[![Experimental Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span></span><br>
        <span data-ttu-id="cab60-176">**[Recursos <br/> experimentais](contributing/experimental-features.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-176">**[Experimental <br/> Features](contributing/experimental-features.md)**</span></span><br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a><span data-ttu-id="cab60-177">Blocos de construção de experiência do usuário</span><span class="sxs-lookup"><span data-stu-id="cab60-177">UX building blocks</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="cab60-178">[![Botão](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Botão](features/ux-building-blocks/button.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-178">[![Button](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Button](features/ux-building-blocks/button.md)**</span></span><br>
        <span data-ttu-id="cab60-179">Um controle de botão que dá suporte a vários métodos de entrada, incluindo a mão articulada do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cab60-179">A button control which supports various input methods, including HoloLens 2's articulated hand</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-180">[![Controle de limites](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Controle de limites](features/ux-building-blocks/bounds-control.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-180">[![Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds Control](features/ux-building-blocks/bounds-control.md)**</span></span><br>
        <span data-ttu-id="cab60-181">Interface do usuário padrão para manipular objetos no espaço 3D</span><span class="sxs-lookup"><span data-stu-id="cab60-181">Standard UI for manipulating objects in 3D space</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-182">[![Manipulador de objetos](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Manipulador de objetos](features/ux-building-blocks/object-manipulator.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-182">[![Object Manipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Object Manipulator](features/ux-building-blocks/object-manipulator.md)**</span></span><br>
        <span data-ttu-id="cab60-183">Script para manipular objetos com uma ou duas mãos</span><span class="sxs-lookup"><span data-stu-id="cab60-183">Script for manipulating objects with one or two hands</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="cab60-184">[![Ardósia](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Ardósia](features/ux-building-blocks/slate.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-184">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span></span><br>
        <span data-ttu-id="cab60-185">Plano de estilo 2D que dá suporte à rolagem com entrada de mão articulada</span><span class="sxs-lookup"><span data-stu-id="cab60-185">2D style plane which supports scrolling with articulated hand input</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-186">[![Teclado do sistema](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[Teclado do sistema](features/ux-building-blocks/system-keyboard.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-186">[![System Keyboard](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[System Keyboard](features/ux-building-blocks/system-keyboard.md)**</span></span><br>
        <span data-ttu-id="cab60-187">Exemplo de script de uso do teclado do sistema no Unity</span><span class="sxs-lookup"><span data-stu-id="cab60-187">Example script of using the system keyboard in Unity</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-188">[![Interativo](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interativo](features/ux-building-blocks/interactable.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-188">[![Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**</span></span><br>
        <span data-ttu-id="cab60-189">Um script para tornar os objetos interativos com os estados visuais e o suporte a temas</span><span class="sxs-lookup"><span data-stu-id="cab60-189">A script for making objects interactable with visual states and theme support</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="cab60-190">[![Solucionador](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solucionador](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-190">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
        <span data-ttu-id="cab60-191">Vários comportamentos de posicionamento de objeto, como marca, bloqueio de corpo, tamanho de exibição constante e magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="cab60-191">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-192">[![Coleção de objetos](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Coleção de objetos](features/ux-building-blocks/object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-192">[![Object Collection](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Object Collection](features/ux-building-blocks/object-collection.md)**</span></span><br>
        <span data-ttu-id="cab60-193">Script para dispor uma matriz de objetos em uma forma tridimensional</span><span class="sxs-lookup"><span data-stu-id="cab60-193">Script for laying out an array of objects in a three-dimensional shape</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-194">[![Dica de ferramenta](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Dica de ferramenta](features/ux-building-blocks/tooltip.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-194">[![Tooltip](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Tooltip](features/ux-building-blocks/tooltip.md)**</span></span><br>
        <span data-ttu-id="cab60-195">A interface do usuário de anotações com um sistema de âncora/dinâmico flexível, que pode ser usado para rotular controladores de movimento e objetos</span><span class="sxs-lookup"><span data-stu-id="cab60-195">Annotation UI with a flexible anchor/pivot system, which can be used for labeling motion controllers and objects</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="cab60-196">[![Controle deslizante](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Controle deslizante](features/ux-building-blocks/sliders.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-196">[![Slider](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Slider](features/ux-building-blocks/sliders.md)**</span></span><br>
        <span data-ttu-id="cab60-197">Interface do usuário do controle deslizante para ajustar valores que dão suporte à interação direta de acompanhamento da mão</span><span class="sxs-lookup"><span data-stu-id="cab60-197">Slider UI for adjusting values supporting direct hand tracking interaction</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-198">[![Sombreador padrão do MRTK](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[Sombreador padrão do MRTK](features/rendering/mrtk-standard-shader.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-198">[![MRTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**</span></span><br>
        <span data-ttu-id="cab60-199">O sombreador padrão do MRTK dá suporte a vários elementos de Fluent Design com desempenho</span><span class="sxs-lookup"><span data-stu-id="cab60-199">MRTK's Standard shader supports various Fluent design elements with performance</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-200">[![Menu lateral](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Menu lateral](features/ux-building-blocks/hand-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-200">[![Hand Menu](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Hand Menu](features/ux-building-blocks/hand-menu.md)**</span></span><br>
        <span data-ttu-id="cab60-201">Interface do usuário protegida por mão para acesso rápido, usando o solucionador de restrição de mão</span><span class="sxs-lookup"><span data-stu-id="cab60-201">Hand-locked UI for quick access, using the Hand Constraint Solver</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="cab60-202">[![Barra de aplicativos](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[Barra de aplicativos](features/ux-building-blocks/app-bar.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-202">[![App Bar](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App Bar](features/ux-building-blocks/app-bar.md)**</span></span><br>
        <span data-ttu-id="cab60-203">Interface do usuário para ativação manual do controle de limites</span><span class="sxs-lookup"><span data-stu-id="cab60-203">UI for Bounds Control's manual activation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-204">[![Ponteiros](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Ponteiros](features/input/pointers.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-204">[![Pointers](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointers](features/input/pointers.md)**</span></span><br>
        <span data-ttu-id="cab60-205">Saiba mais sobre os vários tipos de ponteiros</span><span class="sxs-lookup"><span data-stu-id="cab60-205">Learn about various types of pointers</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-206">[![Visualização da ponta do dedo](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Visualização da ponta do dedo](features/ux-building-blocks/fingertip-visualization.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-206">[![Fingertip Visualization](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip Visualization](features/ux-building-blocks/fingertip-visualization.md)**</span></span><br>
        <span data-ttu-id="cab60-207">A funcionalidade visual na ponta do dedo, que aprimora a confiança da interação direta</span><span class="sxs-lookup"><span data-stu-id="cab60-207">Visual affordance on the fingertip which improves the confidence for the direct interaction</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="cab60-208">[![Menu próximo](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Menu próximo](features/ux-building-blocks/near-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-208">[![Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near Menu](features/ux-building-blocks/near-menu.md)**</span></span><br>
        <span data-ttu-id="cab60-209">Interface do usuário do menu flutuante para as interações próximas</span><span class="sxs-lookup"><span data-stu-id="cab60-209">Floating menu UI for the near interactions</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-210">[![Introdução à conscientização espacial](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Exibição da conscientização espacial](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-210">[![Spatial Awareness Getting started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial Awareness View](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
        <span data-ttu-id="cab60-211">Fazer com que seus objetos holográficos interajam com os ambientes físicos</span><span class="sxs-lookup"><span data-stu-id="cab60-211">Make your holographic objects interact with the physical environments</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-212">[![Comando de voz](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Comando de voz](features/input/speech.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-212">[![Voice Command](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Voice Command](features/input/speech.md)**</span></span><br>
        <span data-ttu-id="cab60-213">Scripts e exemplos para integrar a entrada de fala</span><span class="sxs-lookup"><span data-stu-id="cab60-213">Scripts and examples for integrating speech input</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="cab60-214">[![Indicador de progresso](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Indicador de progresso](features/ux-building-blocks/progress-indicator.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-214">[![Progress Indicator](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Progress Indicator](features/ux-building-blocks/progress-indicator.md)**</span></span><br>
        <span data-ttu-id="cab60-215">Indicador visual para comunicação do processo de dados ou operação</span><span class="sxs-lookup"><span data-stu-id="cab60-215">Visual indicator for communicating data process or operation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-216">[![Caixa de diálogo](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Caixa de diálogo](features/ux-building-blocks/dialog.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-216">[![Dialog](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialog](features/ux-building-blocks/dialog.md)**</span></span><br>
        <span data-ttu-id="cab60-217">Interface de usuário para solicitar confirmação ou reconhecimento do usuário</span><span class="sxs-lookup"><span data-stu-id="cab60-217">UI for asking for user's confirmation or acknowledgement</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-218">[![Orientador de mão](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Orientador de mão](features/ux-building-blocks/hand-coach.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-218">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span></span><br>
        <span data-ttu-id="cab60-219">Componente que ajuda a orientar o usuário quando o gesto não foi ensinado</span><span class="sxs-lookup"><span data-stu-id="cab60-219">Component that helps guide the user when the gesture has not been taught</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="cab60-220">[![Serviço de física de mão](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Serviço de física de mão [Experimental]](features/experimental/hand-physics-service.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-220">[![Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Hand Physics Service [Experimental]](features/experimental/hand-physics-service.md)**</span></span><br>
        <span data-ttu-id="cab60-221">O serviço de física de mão permite eventos de colisão de corpo rígido e interações com mãos articuladas</span><span class="sxs-lookup"><span data-stu-id="cab60-221">The hand physics service enables rigid body collision events and interactions with articulated hands</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-222">[![Rolagem da coleção](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Rolagem da coleção](features/ux-building-blocks/scrolling-object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-222">[![Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling Collection](features/ux-building-blocks/scrolling-object-collection.md)**</span></span><br>
        <span data-ttu-id="cab60-223">Uma coleção de objetos que rola nativamente objetos 3D</span><span class="sxs-lookup"><span data-stu-id="cab60-223">An Object Collection that natively scrolls 3D objects</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-224">[![Doca](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Doca [Experimental]](features/experimental/dock.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-224">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimental]](features/experimental/dock.md)**</span></span><br>
        <span data-ttu-id="cab60-225">A Doca permite que os objetos sejam movidos para dentro e para fora das posições predeterminadas</span><span class="sxs-lookup"><span data-stu-id="cab60-225">The Dock allows objects to be moved in and out of predetermined positions</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="cab60-226">[![Acompanhamento ocular: seleção de destino](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Acompanhamento ocular: seleção de destino](features/input/eye-tracking/eye-tracking-target-selection.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-226">[![Eye Tracking: Target Selection](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eye Tracking: Target Selection](features/input/eye-tracking/eye-tracking-target-selection.md)**</span></span><br>
        <span data-ttu-id="cab60-227">Combine a entrada de olhos, voz e mão para selecionar com rapidez e facilidade os hologramas em sua cena</span><span class="sxs-lookup"><span data-stu-id="cab60-227">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-228">[![Acompanhamento ocular: navegação](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Acompanhamento ocular: navegação](features/input/eye-tracking/eye-tracking-navigation.md)**</span><span class="sxs-lookup"><span data-stu-id="cab60-228">[![Eye Tracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eye Tracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span></span><br>
        <span data-ttu-id="cab60-229">Saiba como rolar automaticamente o texto ou ampliar de maneira fluente o conteúdo focado com base no que você está vendo</span><span class="sxs-lookup"><span data-stu-id="cab60-229">Learn how to auto-scroll text or fluently zoom into focused content based on what you are looking at</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cab60-230">[![Acompanhamento ocular: mapa de calor](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Acompanhamento ocular: mapa de calor](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span><span class="sxs-lookup"><span data-stu-id="cab60-230">[![Eye Tracking: Heat Map](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eye Tracking: Heat Map](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span></span><br>
        <span data-ttu-id="cab60-231">Exemplos de registro em log, carregamento e visualização do que os usuários estão olhando em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="cab60-231">Examples for logging, loading and visualizing what users have been looking at in your app</span></span>
    :::column-end:::
:::row-end:::

## <a name="tools"></a><span data-ttu-id="cab60-232">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="cab60-232">Tools</span></span>

|  <span data-ttu-id="cab60-233">[![Otimizar janela](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Otimizar janela](features/tools/optimize-window.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-233">[![Optimize Window](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimize Window](features/tools/optimize-window.md)</span></span> | <span data-ttu-id="cab60-234">[![Janela de dependência](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Janela de dependência](features/tools/dependency-window.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-234">[![Dependency Window](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Dependency Window](features/tools/dependency-window.md)</span></span> | ![Janela de compilação](features/images/MRTK_Icon_BuildWindow.png) <span data-ttu-id="cab60-236">Janela de compilação</span><span class="sxs-lookup"><span data-stu-id="cab60-236">Build Window</span></span> | <span data-ttu-id="cab60-237">[![Gravação de entrada](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Gravação de entrada](features/input-simulation/input-animation-recording.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-237">[![Input recording](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Input recording](features/input-simulation/input-animation-recording.md)</span></span> |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="cab60-238">Automatizar a configuração de projetos de realidade misturada para otimizações de desempenho</span><span class="sxs-lookup"><span data-stu-id="cab60-238">Automate configuration of Mixed Reality projects for performance optimizations</span></span> | <span data-ttu-id="cab60-239">Analisar dependências entre ativos e identificar ativos não utilizados</span><span class="sxs-lookup"><span data-stu-id="cab60-239">Analyze dependencies between assets and identify unused assets</span></span> |  <span data-ttu-id="cab60-240">Configurar e executar um processo de compilação de ponta a ponta para aplicativos de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="cab60-240">Configure and execute an end-to-end build process for Mixed Reality applications</span></span> | <span data-ttu-id="cab60-241">Movimentação de cabeçotes de gravação e reprodução e dados de acompanhamento da mão no editor</span><span class="sxs-lookup"><span data-stu-id="cab60-241">Record and playback head movement and hand tracking data in editor</span></span> |

## <a name="example-scenes"></a><span data-ttu-id="cab60-242">Cenas de exemplo</span><span class="sxs-lookup"><span data-stu-id="cab60-242">Example scenes</span></span>

<span data-ttu-id="cab60-243">Explore os vários tipos de interações e controles de interface do usuário do MRTK nesta [cena de exemplo](features/example-scenes/hand-interaction-examples.md).</span><span class="sxs-lookup"><span data-stu-id="cab60-243">Explore MRTK's various types of interactions and UI controls in [this example scene](features/example-scenes/hand-interaction-examples.md).</span></span>

<span data-ttu-id="cab60-244">[![Cena de exemplo 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-244">[![Example Scene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="mrtk-examples-hub"></a><span data-ttu-id="cab60-245">Hub de exemplos do MRTK</span><span class="sxs-lookup"><span data-stu-id="cab60-245">MRTK examples hub</span></span>

<span data-ttu-id="cab60-246">Com o Hub de exemplos do MRTK, você pode experimentar várias cenas de exemplo no MRTK.</span><span class="sxs-lookup"><span data-stu-id="cab60-246">With the MRTK Examples Hub, you can try various example scenes in MRTK.</span></span>
<span data-ttu-id="cab60-247">Você pode baixar pacotes de aplicativos pré-criados para o HoloLens (x86), o HoloLens 2(ARM) e os headsets imersivos do Windows Mixed Reality (x64) selecionando o pacote "Exemplos do Kit de Ferramentas de Realidade Misturada" na [ferramenta de recurso de MR](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span><span class="sxs-lookup"><span data-stu-id="cab60-247">You can download pre-built app packages for HoloLens(x86), HoloLens 2(ARM), and Windows Mixed Reality immersive headsets(x64) by selecting the "Mixed Reality Toolkit Examples" package in the [MR Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span></span> <span data-ttu-id="cab60-248">[Use o Portal de Dispositivos do Windows para instalar aplicativos no HoloLens (1ª geração).](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)</span><span class="sxs-lookup"><span data-stu-id="cab60-248">Make sure to [use the Windows Device Portal to install apps on HoloLens (1st gen)](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span></span> <span data-ttu-id="cab60-249">No HoloLens 2, você pode baixar e instalar o [Hub de exemplos do MRTK por meio do aplicativo Microsoft Store](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span><span class="sxs-lookup"><span data-stu-id="cab60-249">On HoloLens 2, you can download and install [MRTK Examples Hub through the Microsoft Store app](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span></span>

<span data-ttu-id="cab60-250">Confira a [página LEIAME do hub de exemplos](features/example-scenes/example-hub.md) para saber mais sobre os detalhes de como criar um hub de várias cenas com o sistema de cena do MRTK e o serviço de transição de cena.</span><span class="sxs-lookup"><span data-stu-id="cab60-250">See [Examples Hub README page](features/example-scenes/example-hub.md) to learn about the details on creating a multi-scene hub with MRTK's scene system and scene transition service.</span></span>

<span data-ttu-id="cab60-251">[![Hub de cena de exemplo](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="cab60-251">[![Example Scene Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="sample-apps-made-with-mrtk"></a><span data-ttu-id="cab60-252">Aplicativos de exemplo feitos com o MRTK</span><span class="sxs-lookup"><span data-stu-id="cab60-252">Sample apps made with MRTK</span></span>

| <span data-ttu-id="cab60-253">[![Tabela periódica dos elementos](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="cab60-253">[![Periodic Table of the Elements](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span>| <span data-ttu-id="cab60-254">[![Explorador da galáxia](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="cab60-254">[![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span></span>| <span data-ttu-id="cab60-255">[![Aplicativo de exemplo Surfaces](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span><span class="sxs-lookup"><span data-stu-id="cab60-255">[![Surfaces sample app](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="cab60-256">[A tabela periódica dos elementos](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) é um aplicativo de exemplo de software livre que demonstra como usar o sistema de entrada e os blocos de construção do MRTK a fim de criar uma experiência de aplicativo para o HoloLens e os headsets imersivos.</span><span class="sxs-lookup"><span data-stu-id="cab60-256">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) is an open-source sample app which demonstrates how to use MRTK's input system and building blocks to create an app experience for HoloLens and Immersive headsets.</span></span> <span data-ttu-id="cab60-257">Leia a história de portagem: [Como trazer o aplicativo Tabela periódica dos elementos para o HoloLens 2 com o MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="cab60-257">Read the porting story: [Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span> |<span data-ttu-id="cab60-258">O [Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) é um aplicativo de exemplo de software livre originalmente desenvolvido em março de 2016 como parte da campanha 'Compartilhe sua ideia' do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cab60-258">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app that was originally developed in March 2016 as part of the HoloLens 'Share Your Idea' campaign.</span></span> <span data-ttu-id="cab60-259">O Galaxy Explorer foi atualizado com novos recursos para o HoloLens 2, usando o MRTK v2.</span><span class="sxs-lookup"><span data-stu-id="cab60-259">Galaxy Explorer has been updated with new features for HoloLens 2, using MRTK v2.</span></span> <span data-ttu-id="cab60-260">Leia a história: [A criação do Galaxy Explorer para o HoloLens 2](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="cab60-260">Read the story: [The Making of Galaxy Explorer for HoloLens 2](/windows/mixed-reality/galaxy-explorer-update)</span></span> |<span data-ttu-id="cab60-261">O [Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) é um aplicativo de exemplo de software livre para o HoloLens 2, que explora como podemos criar uma sensação tátil com visual, áudio e acompanhamento da mão totalmente articulado.</span><span class="sxs-lookup"><span data-stu-id="cab60-261">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) is an open-source sample app for HoloLens 2 which explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span> <span data-ttu-id="cab60-262">Confira a sessão do Microsoft MR Dev Days [Aprendizados com o aplicativo Surfaces](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) para ver o design detalhado e a história de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="cab60-262">Check out Microsoft MR Dev Days session [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) for the detailed design and development story.</span></span> |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a><span data-ttu-id="cab60-263">Vídeos de sessão do evento Mixed Reality Dev Days 2020</span><span class="sxs-lookup"><span data-stu-id="cab60-263">Session videos from Mixed Reality Dev Days 2020</span></span>

| <span data-ttu-id="cab60-264">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="cab60-264">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>| <span data-ttu-id="cab60-265">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span><span class="sxs-lookup"><span data-stu-id="cab60-265">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>| <span data-ttu-id="cab60-266">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span><span class="sxs-lookup"><span data-stu-id="cab60-266">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="cab60-267">Tutorial sobre como criar um aplicativo MRTK simples do início ao fim.</span><span class="sxs-lookup"><span data-stu-id="cab60-267">Tutorial on how to create a simple MRTK app from start to finish.</span></span> <span data-ttu-id="cab60-268">Saiba mais sobre os conceitos de interação e os recursos multiplataforma do MRTK.</span><span class="sxs-lookup"><span data-stu-id="cab60-268">Learn about interaction concepts and MRTK’s multi-platform capabilities.</span></span> | <span data-ttu-id="cab60-269">Aprofunde-se nos blocos de construção de experiência do usuário do MRTK que ajudam você a criar belas experiências de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="cab60-269">Deep dive on the MRTK’s UX building blocks that help you build beautiful mixed reality experiences.</span></span> | <span data-ttu-id="cab60-270">Uma introdução a ferramentas de desempenho, no MRTK e externas, assim como uma visão geral do Sombreador Padrão do MRTK.</span><span class="sxs-lookup"><span data-stu-id="cab60-270">An introduction to performance tools, both in MRTK and external, as well as an overview of the MRTK Standard Shader.</span></span> |

<span data-ttu-id="cab60-271">Confira o evento [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) para explorar mais vídeos de sessão.</span><span class="sxs-lookup"><span data-stu-id="cab60-271">See [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) to explore more session videos.</span></span>

## <a name="engage-with-the-community"></a><span data-ttu-id="cab60-272">Envolva-se com a comunidade</span><span class="sxs-lookup"><span data-stu-id="cab60-272">Engage with the community</span></span>

* <span data-ttu-id="cab60-273">Junte-se à conversa sobre MRTK no [Slack](https://holodevelopers.slack.com/).</span><span class="sxs-lookup"><span data-stu-id="cab60-273">Join the conversation around MRTK on [Slack](https://holodevelopers.slack.com/).</span></span> <span data-ttu-id="cab60-274">Você pode ingressar na comunidade do Slack por meio do [remetente de convite automático](https://holodevelopersslack.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="cab60-274">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

* <span data-ttu-id="cab60-275">Faça perguntas sobre como usar o MRTK no [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) usando a marca **MRTK**.</span><span class="sxs-lookup"><span data-stu-id="cab60-275">Ask questions about using MRTK on [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) using the **MRTK** tag.</span></span>

* <span data-ttu-id="cab60-276">Procure [problemas conhecidos](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) ou registre [um novo problema](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) se você encontrar algo errado no código MRTK.</span><span class="sxs-lookup"><span data-stu-id="cab60-276">Search for [known issues](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) or file a [new issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) if you find something broken in MRTK code.</span></span>

* <span data-ttu-id="cab60-277">Para dúvidas sobre como contribuir com o MRTK, vá para o canal [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) no Slack.</span><span class="sxs-lookup"><span data-stu-id="cab60-277">For questions about contributing to MRTK, go to the [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) channel on slack.</span></span>

<span data-ttu-id="cab60-278">Este projeto adotou o [Código de Conduta de Software Livre da Microsoft](https://opensource.microsoft.com/codeofconduct/).</span><span class="sxs-lookup"><span data-stu-id="cab60-278">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="cab60-279">Para saber mais, confira as [Perguntas frequentes sobre o Código de Conduta](https://opensource.microsoft.com/codeofconduct/faq/) ou contate o [opencode@microsoft.com](mailto:opencode@microsoft.com) caso tenha outras dúvidas ou comentários.</span><span class="sxs-lookup"><span data-stu-id="cab60-279">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a><span data-ttu-id="cab60-280">Recursos úteis no Centro de Desenvolvimento de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="cab60-280">Useful resources on the Mixed Reality Dev Center</span></span>

| <span data-ttu-id="cab60-281">![Descobrir](features/images/mrdevcenter/icon-discover.png) [Descobrir](/windows/mixed-reality/)</span><span class="sxs-lookup"><span data-stu-id="cab60-281">![Discover](features/images/mrdevcenter/icon-discover.png) [Discover](/windows/mixed-reality/)</span></span>| <span data-ttu-id="cab60-282">![Projetar](features/images/mrdevcenter/icon-design.png) [Projetar](/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="cab60-282">![Design](features/images/mrdevcenter/icon-design.png) [Design](/windows/mixed-reality/design)</span></span>| <span data-ttu-id="cab60-283">![Desenvolver](features/images/mrdevcenter/icon-develop.png) [Desenvolver](/windows/mixed-reality/development)</span><span class="sxs-lookup"><span data-stu-id="cab60-283">![Develop](features/images/mrdevcenter/icon-develop.png) [Develop](/windows/mixed-reality/development)</span></span>| <span data-ttu-id="cab60-284">![Distribuir](features/images/mrdevcenter/icon-distribute.png) [Distribuir](/windows/mixed-reality/implementing-3d-app-launchers)</span><span class="sxs-lookup"><span data-stu-id="cab60-284">![Distribute)](features/images/mrdevcenter/icon-distribute.png) [Distribute](/windows/mixed-reality/implementing-3d-app-launchers)</span></span>|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| <span data-ttu-id="cab60-285">Saiba como criar experiências de realidade misturada para o HoloLens e headsets imersivos (VR).</span><span class="sxs-lookup"><span data-stu-id="cab60-285">Learn to build mixed reality experiences for HoloLens and immersive headsets (VR).</span></span>          | <span data-ttu-id="cab60-286">Obtenha guias de design.</span><span class="sxs-lookup"><span data-stu-id="cab60-286">Get design guides.</span></span> <span data-ttu-id="cab60-287">Crie interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="cab60-287">Build user interface.</span></span> <span data-ttu-id="cab60-288">Saiba mais sobre as interações e a entrada.</span><span class="sxs-lookup"><span data-stu-id="cab60-288">Learn interactions and input.</span></span>     | <span data-ttu-id="cab60-289">Obtenha guias de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="cab60-289">Get development guides.</span></span> <span data-ttu-id="cab60-290">Conheça a tecnologia.</span><span class="sxs-lookup"><span data-stu-id="cab60-290">Learn the technology.</span></span> <span data-ttu-id="cab60-291">Entenda a ciência.</span><span class="sxs-lookup"><span data-stu-id="cab60-291">Understand the science.</span></span>       | <span data-ttu-id="cab60-292">Prepare seu aplicativo para outras pessoas e considere a criação de um iniciador 3D.</span><span class="sxs-lookup"><span data-stu-id="cab60-292">Get your app ready for others and consider creating a 3D launcher.</span></span> |

## <a name="useful-resources-on-azure"></a><span data-ttu-id="cab60-293">Recursos úteis no Azure</span><span class="sxs-lookup"><span data-stu-id="cab60-293">Useful resources on Azure</span></span>

| <span data-ttu-id="cab60-294">![Âncoras Espaciais](features/images/mrdevcenter/icon-azurespatialanchors.png)</span><span class="sxs-lookup"><span data-stu-id="cab60-294">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span></span><br> [<span data-ttu-id="cab60-295">Âncoras Espaciais</span><span class="sxs-lookup"><span data-stu-id="cab60-295">Spatial Anchors</span></span>](/azure/spatial-anchors/)| <span data-ttu-id="cab60-296">![Serviços de Fala](features/images/mrdevcenter/icon-azurespeechservices.png) [Serviços de Fala](/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="cab60-296">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](/azure/cognitive-services/speech-service/)</span></span>| <span data-ttu-id="cab60-297">![Serviços de visão](features/images/mrdevcenter/icon-azurevisionservices.png) [Serviços de visão](/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="cab60-297">![Vision Services](features/images/mrdevcenter/icon-azurevisionservices.png) [Vision Services](/azure/cognitive-services/computer-vision/)</span></span>|
| :------------------------| :--------------------- | :---------------------- |
| <span data-ttu-id="cab60-298">As Âncoras Espaciais são um serviço multiplataforma que permite que você crie experiências de Realidade Misturada usando objetos que mantêm seu local em todos os dispositivos ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="cab60-298">Spatial Anchors is a cross-platform service that allows you to create Mixed Reality experiences using objects that persist their location across devices over time.</span></span>| <span data-ttu-id="cab60-299">Descubra e integre as funcionalidades de fala habilitadas para Azure como conversão de fala em texto, reconhecimento de locutor ou tradução de fala em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cab60-299">Discover and integrate Azure powered speech capabilities like speech to text, speaker recognition or speech translation into your application.</span></span>| <span data-ttu-id="cab60-300">Identifique e analise seu conteúdo de imagem ou de vídeo usando os Serviços de Visão como pesquisa visual computacional, detecção facial, reconhecimento de emoções ou video indexer.</span><span class="sxs-lookup"><span data-stu-id="cab60-300">Identify and analyze your image or video content using Vision Services like computer vision, face detection, emotion recognition or video indexer.</span></span> |

## <a name="how-to-contribute"></a><span data-ttu-id="cab60-301">Como contribuir</span><span class="sxs-lookup"><span data-stu-id="cab60-301">How to contribute</span></span>

<span data-ttu-id="cab60-302">Saiba como contribuir com o MRTK em [Como contribuir](contributing/contributing.md).</span><span class="sxs-lookup"><span data-stu-id="cab60-302">Learn how you can contribute to MRTK at [Contributing](contributing/contributing.md).</span></span>

## <a name="getting-help"></a><span data-ttu-id="cab60-303">Obtendo ajuda</span><span class="sxs-lookup"><span data-stu-id="cab60-303">Getting help</span></span>

<span data-ttu-id="cab60-304">Se você tiver problemas causados pelo MRTK ou tiver dúvidas sobre como fazer algo, há alguns recursos que podem ajudar:</span><span class="sxs-lookup"><span data-stu-id="cab60-304">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="cab60-305">Para relatórios de bugs, [registre um problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) no repositório GitHub.</span><span class="sxs-lookup"><span data-stu-id="cab60-305">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="cab60-306">Se tiver dúvidas, entre em contato com [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) ou com o [canal mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) no Slack.</span><span class="sxs-lookup"><span data-stu-id="cab60-306">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="cab60-307">Você pode ingressar na comunidade do Slack por meio do [remetente de convite automático](https://holodevelopersslack.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="cab60-307">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>