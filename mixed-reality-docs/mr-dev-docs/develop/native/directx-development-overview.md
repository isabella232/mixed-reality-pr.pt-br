---
title: Visão geral do desenvolvimento nativo
description: Crie um mecanismo de realidade mista com base em DirectX usando as APIs de realidade mista do Windows diretamente.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, renderização Holographic, nativo, aplicativo nativo, WinRT, aplicativo WinRT, APIs de plataforma, mecanismo personalizado, middleware
ms.openlocfilehash: fb51dfe15de26b80db255f0daca69e913f9ad35c
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903126"
---
# <a name="native-development-overview"></a><span data-ttu-id="8afa5-104">Visão geral do desenvolvimento nativo</span><span class="sxs-lookup"><span data-stu-id="8afa5-104">Native development overview</span></span>

![Logotipo de faixa nativa](../images/native_logo_banner.png)

<span data-ttu-id="8afa5-106">mecanismos 3D como [Unity](../unity/unity-development-overview.md) ou [inreal](../unreal/unreal-development-overview.md) não são os únicos caminhos de desenvolvimento de realidade misturados abertos para você.</span><span class="sxs-lookup"><span data-stu-id="8afa5-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="8afa5-107">Você também pode criar aplicativos de realidade misturada codificando diretamente para as APIs de realidade mista do Windows com DirectX 11 ou DirectX 12.</span><span class="sxs-lookup"><span data-stu-id="8afa5-107">You can also create Mixed Reality apps by directly coding to the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="8afa5-108">Ao aproveitar a plataforma diretamente, você está essencialmente criando seu próprio middleware ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="8afa5-108">By leveraging the platform directly, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="8afa5-109">Se você tiver um projeto WinRT existente que gostaria de manter, vá para nossa documentação principal do [winrt](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="8afa5-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="8afa5-110">Pontos de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="8afa5-110">Development checkpoints</span></span>

<span data-ttu-id="8afa5-111">Use os pontos de verificação a seguir para levar seus jogos e aplicativos do Unity para o mundo da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="8afa5-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="8afa5-112">1. Introdução</span><span class="sxs-lookup"><span data-stu-id="8afa5-112">1. Getting started</span></span>

<span data-ttu-id="8afa5-113">O Windows Mixed Reality dá suporte a [dois tipos de aplicativos](../../design/app-views.md):</span><span class="sxs-lookup"><span data-stu-id="8afa5-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="8afa5-114">**Aplicativos de realidade mista** (UWP ou Win32) que usam a API do [HOLOGRAPHICSPACE](getting-a-holographicspace.md) ou a [API do OpenXR](openxr.md) para processar uma exibição de [imersão](../../design/app-views.md) para o usuário que preenche a tela do headset</span><span class="sxs-lookup"><span data-stu-id="8afa5-114">**Mixed-reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) to the user that fills the headset display</span></span>
* <span data-ttu-id="8afa5-115">**aplicativos 2D** (UWP) que usam DirectX, XAML ou outra estrutura para renderizar [exibições 2D](../../design/app-views.md#2d-views) em slates na página inicial do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8afa5-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="8afa5-116">As diferenças entre o desenvolvimento DirectX para [exibições 2D e exibições de imersão](../../design/app-views.md) envolvem principalmente a renderização Holographic e a entrada espacial.</span><span class="sxs-lookup"><span data-stu-id="8afa5-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="8afa5-117">O [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) do seu aplicativo UWP ou o HWND do seu aplicativo Win32 são necessários e permanecem basicamente os mesmos.</span><span class="sxs-lookup"><span data-stu-id="8afa5-117">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="8afa5-118">O mesmo é verdadeiro para as APIs do WinRT que estão disponíveis para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8afa5-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="8afa5-119">Mas você deve usar um subconjunto diferente dessas APIs para aproveitar os recursos do Holographic.</span><span class="sxs-lookup"><span data-stu-id="8afa5-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="8afa5-120">Por exemplo, o SwapChain e o quadro presente são gerenciados pelo sistema para aplicativos Holographic a fim de habilitar um loop de quadro previsto para pose.</span><span class="sxs-lookup"><span data-stu-id="8afa5-120">For example, the swapchain and frame present is managed by the system for holographic applications in order to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="8afa5-121">2. Blocos principais de construção</span><span class="sxs-lookup"><span data-stu-id="8afa5-121">2. Core building blocks</span></span>

<span data-ttu-id="8afa5-122">Os aplicativos do Windows Mixed Reality usam as seguintes APIs para criar experiências de [realidade mista](../../discover/mixed-reality.md) para o HoloLens e outros headsets de imersão:</span><span class="sxs-lookup"><span data-stu-id="8afa5-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="8afa5-123">Recurso</span><span class="sxs-lookup"><span data-stu-id="8afa5-123">Feature</span></span>  |  <span data-ttu-id="8afa5-124">Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="8afa5-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="8afa5-125">Foco</span><span class="sxs-lookup"><span data-stu-id="8afa5-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="8afa5-126">Permita que os usuários direcionem os hologramas olhando para eles</span><span class="sxs-lookup"><span data-stu-id="8afa5-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="8afa5-127">Gesto</span><span class="sxs-lookup"><span data-stu-id="8afa5-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="8afa5-128">Adicionar ações espaciais aos seus aplicativos</span><span class="sxs-lookup"><span data-stu-id="8afa5-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="8afa5-129">Renderização holográfica</span><span class="sxs-lookup"><span data-stu-id="8afa5-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="8afa5-130">Desenhe um holograma em um local preciso no mundo em seus usuários</span><span class="sxs-lookup"><span data-stu-id="8afa5-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="8afa5-131">Controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="8afa5-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="8afa5-132">Permitir que os usuários executem ações em seus ambientes de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="8afa5-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="8afa5-133">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="8afa5-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="8afa5-134">Mapeie seu espaço físico com uma sobreposição de malha virtual para marcar os limites do seu ambiente</span><span class="sxs-lookup"><span data-stu-id="8afa5-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="8afa5-135">Voz</span><span class="sxs-lookup"><span data-stu-id="8afa5-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="8afa5-136">Capture ditado, palavras-chave e frases faladas dos seus usuários</span><span class="sxs-lookup"><span data-stu-id="8afa5-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="8afa5-137">Você pode encontrar recursos centrais futuros e no desenvolvimento na documentação do [mapa](openxr.md#roadmap) do OpenXR.</span><span class="sxs-lookup"><span data-stu-id="8afa5-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="8afa5-138">3. implantação e teste</span><span class="sxs-lookup"><span data-stu-id="8afa5-138">3. Deploying and testing</span></span>

<span data-ttu-id="8afa5-139">Faça o desenvolvimento com o OpenXR em um headset imersivo do HoloLens 2 ou do Windows Mixed Reality na área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8afa5-139">You can develop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset on the desktop.</span></span>  <span data-ttu-id="8afa5-140">Se você não tiver acesso a um headset, poderá usar o [emulador do HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou o [simulador de realidade mista do Windows](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) .</span><span class="sxs-lookup"><span data-stu-id="8afa5-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="8afa5-141">E agora?</span><span class="sxs-lookup"><span data-stu-id="8afa5-141">What's next?</span></span>

<span data-ttu-id="8afa5-142">O trabalho dos desenvolvedores nunca termina, especialmente ao aprender uma nova ferramenta ou um SDK.</span><span class="sxs-lookup"><span data-stu-id="8afa5-142">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="8afa5-143">As seções a seguir podem levar você para áreas que vão além do material de nível de iniciante que você já concluiu, juntamente com recursos úteis se você não conseguir avançar.</span><span class="sxs-lookup"><span data-stu-id="8afa5-143">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="8afa5-144">Observe que esses tópicos e recursos não estão em nenhuma ordem sequencial, então fique à vontade para mergulhar neles e explorá-los!</span><span class="sxs-lookup"><span data-stu-id="8afa5-144">Note that these topics and resources are not in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="8afa5-145">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="8afa5-145">Additional resources</span></span>

<span data-ttu-id="8afa5-146">Se você pretende nivelar o jogo do OpenXR, confira os links abaixo:</span><span class="sxs-lookup"><span data-stu-id="8afa5-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="8afa5-147">Práticas recomendadas do OpenXR</span><span class="sxs-lookup"><span data-stu-id="8afa5-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="8afa5-148">Desempenho do OpenXR</span><span class="sxs-lookup"><span data-stu-id="8afa5-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="8afa5-149">Solução de problemas do OpenXR</span><span class="sxs-lookup"><span data-stu-id="8afa5-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="8afa5-150">Veja também</span><span class="sxs-lookup"><span data-stu-id="8afa5-150">See also</span></span>
* [<span data-ttu-id="8afa5-151">Modelo de aplicativo</span><span class="sxs-lookup"><span data-stu-id="8afa5-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="8afa5-152">Modos de exibição do aplicativo</span><span class="sxs-lookup"><span data-stu-id="8afa5-152">App views</span></span>](../../design/app-views.md)
