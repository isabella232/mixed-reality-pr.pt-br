---
title: Visão geral do desenvolvimento nativo
description: Saiba como criar um mecanismo de realidade misturada baseado em DirectX usando as APIs de realidade mista do Windows diretamente.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, renderização Holographic, nativo, aplicativo nativo, WinRT, aplicativo WinRT, APIs de plataforma, mecanismo personalizado, middleware, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: b137fad12740542deb4995485201a9bd0d1d7662
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581046"
---
# <a name="native-development-overview"></a><span data-ttu-id="693b7-104">Visão geral do desenvolvimento nativo</span><span class="sxs-lookup"><span data-stu-id="693b7-104">Native development overview</span></span>

![Logotipo de faixa nativa](../images/native_logo_banner.png)

<span data-ttu-id="693b7-106">mecanismos 3D como [Unity](../unity/unity-development-overview.md) ou [inreal](../unreal/unreal-development-overview.md) não são os únicos caminhos de desenvolvimento de realidade misturados abertos para você.</span><span class="sxs-lookup"><span data-stu-id="693b7-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="693b7-107">Você também pode criar aplicativos de realidade misturada usando as APIs de realidade mista do Windows com DirectX 11 ou DirectX 12.</span><span class="sxs-lookup"><span data-stu-id="693b7-107">You can also create Mixed Reality apps using the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="693b7-108">Acessando a origem da plataforma, você está basicamente criando seu próprio middleware ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="693b7-108">By going to the platform source, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="693b7-109">Se você tiver um projeto WinRT existente que gostaria de manter, vá para nossa documentação principal do [winrt](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="693b7-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="693b7-110">Pontos de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="693b7-110">Development checkpoints</span></span>

<span data-ttu-id="693b7-111">Use os pontos de verificação a seguir para levar seus jogos e aplicativos do Unity para o mundo da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="693b7-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="693b7-112">1. Introdução</span><span class="sxs-lookup"><span data-stu-id="693b7-112">1. Getting started</span></span>

<span data-ttu-id="693b7-113">O Windows Mixed Reality dá suporte a [dois tipos de aplicativos](../../design/app-views.md):</span><span class="sxs-lookup"><span data-stu-id="693b7-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="693b7-114">Aplicativos UWP ou Win32 **mistos de realidade** que usam a [API HOLOGRAPHICSPACE](getting-a-holographicspace.md) ou a [API OpenXR](openxr.md) para processar uma [exibição imersiva](../../design/app-views.md) que preenche a tela do headset</span><span class="sxs-lookup"><span data-stu-id="693b7-114">UWP or Win32 **Mixed Reality applications** that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) that fills the headset display</span></span>
* <span data-ttu-id="693b7-115">**aplicativos 2D** (UWP) que usam DirectX, XAML ou outra estrutura para renderizar [exibições 2D](../../design/app-views.md#2d-views) em slates na página inicial do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="693b7-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="693b7-116">As diferenças entre o desenvolvimento DirectX para [exibições 2D e exibições de imersão](../../design/app-views.md) envolvem principalmente a renderização Holographic e a entrada espacial.</span><span class="sxs-lookup"><span data-stu-id="693b7-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="693b7-117">O [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) do seu aplicativo UWP ou o HWND do seu aplicativo Win32 são necessários e permanecem basicamente os mesmos.</span><span class="sxs-lookup"><span data-stu-id="693b7-117">Your UWP application's [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="693b7-118">O mesmo é verdadeiro para as APIs do WinRT que estão disponíveis para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="693b7-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="693b7-119">Mas você deve usar um subconjunto diferente dessas APIs para aproveitar os recursos do Holographic.</span><span class="sxs-lookup"><span data-stu-id="693b7-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="693b7-120">Por exemplo, o sistema para aplicativos Holographic gerencia o SwapChain e o quadro presente para habilitar um loop de quadro previsto para pose.</span><span class="sxs-lookup"><span data-stu-id="693b7-120">For example, the system for holographic applications manages the swapchain and frame present to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="693b7-121">2. Blocos principais de construção</span><span class="sxs-lookup"><span data-stu-id="693b7-121">2. Core building blocks</span></span>

<span data-ttu-id="693b7-122">Os aplicativos do Windows Mixed Reality usam as seguintes APIs para criar experiências de [realidade mista](../../discover/mixed-reality.md) para o HoloLens e outros headsets de imersão:</span><span class="sxs-lookup"><span data-stu-id="693b7-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="693b7-123">Recurso</span><span class="sxs-lookup"><span data-stu-id="693b7-123">Feature</span></span>  |  <span data-ttu-id="693b7-124">Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="693b7-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="693b7-125">Foco</span><span class="sxs-lookup"><span data-stu-id="693b7-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="693b7-126">Permitir que os usuários direcionem hologramas olhando para eles</span><span class="sxs-lookup"><span data-stu-id="693b7-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="693b7-127">Gesto</span><span class="sxs-lookup"><span data-stu-id="693b7-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="693b7-128">Adicionar ações espaciais aos seus aplicativos</span><span class="sxs-lookup"><span data-stu-id="693b7-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="693b7-129">Renderização holográfica</span><span class="sxs-lookup"><span data-stu-id="693b7-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="693b7-130">Desenhe um holograma em um local preciso no mundo em seus usuários</span><span class="sxs-lookup"><span data-stu-id="693b7-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="693b7-131">Controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="693b7-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="693b7-132">Permitir que os usuários executem ações em seus ambientes de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="693b7-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="693b7-133">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="693b7-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="693b7-134">Mapear seu espaço físico com uma sobreposição de malha virtual para marcar os limites do seu ambiente</span><span class="sxs-lookup"><span data-stu-id="693b7-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="693b7-135">Voz</span><span class="sxs-lookup"><span data-stu-id="693b7-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="693b7-136">Capturar palavras-chave e frases faladas e ditado dos seus usuários</span><span class="sxs-lookup"><span data-stu-id="693b7-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="693b7-137">Você pode encontrar recursos centrais futuros e no desenvolvimento na documentação do [mapa](openxr.md#roadmap) do OpenXR.</span><span class="sxs-lookup"><span data-stu-id="693b7-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="693b7-138">3. implantação e teste</span><span class="sxs-lookup"><span data-stu-id="693b7-138">3. Deploying and testing</span></span>

<span data-ttu-id="693b7-139">Você pode desenvolver em um desktop usando OpenXR em um fone de ouvido de imersão 2 ou Windows Mixed realm.</span><span class="sxs-lookup"><span data-stu-id="693b7-139">You can develop on a desktop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset.</span></span>  <span data-ttu-id="693b7-140">Se você não tiver acesso a um headset, poderá usar o [emulador do HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou o [simulador de realidade mista do Windows](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) .</span><span class="sxs-lookup"><span data-stu-id="693b7-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="693b7-141">E agora?</span><span class="sxs-lookup"><span data-stu-id="693b7-141">What's next?</span></span>

<span data-ttu-id="693b7-142">O trabalho de um desenvolvedor nunca termina, especialmente ao aprender uma nova ferramenta ou um SDK.</span><span class="sxs-lookup"><span data-stu-id="693b7-142">A developer's job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="693b7-143">As seções a seguir podem levá-lo para áreas além do material de nível de iniciante que você já concluiu.</span><span class="sxs-lookup"><span data-stu-id="693b7-143">The following sections can take you into areas beyond the beginner level material you've already completed.</span></span> <span data-ttu-id="693b7-144">Esses tópicos e recursos não estão em nenhuma ordem sequencial, então fique à vontade para pular e explorar!</span><span class="sxs-lookup"><span data-stu-id="693b7-144">These topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="693b7-145">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="693b7-145">Additional resources</span></span>

<span data-ttu-id="693b7-146">Se você pretende nivelar o jogo do OpenXR, confira os links abaixo:</span><span class="sxs-lookup"><span data-stu-id="693b7-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="693b7-147">Práticas recomendadas do OpenXR</span><span class="sxs-lookup"><span data-stu-id="693b7-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="693b7-148">Desempenho do OpenXR</span><span class="sxs-lookup"><span data-stu-id="693b7-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="693b7-149">Solução de problemas do OpenXR</span><span class="sxs-lookup"><span data-stu-id="693b7-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="693b7-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="693b7-150">See also</span></span>
* [<span data-ttu-id="693b7-151">Modelo de aplicativo</span><span class="sxs-lookup"><span data-stu-id="693b7-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="693b7-152">Modos de exibição do aplicativo</span><span class="sxs-lookup"><span data-stu-id="693b7-152">App views</span></span>](../../design/app-views.md)