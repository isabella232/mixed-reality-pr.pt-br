---
title: Usando o WebXR com o Windows Mixed Reality
description: Aprenda as noções básicas de como usar e desenvolver para aplicativos WebXR executados em headsets de imersão de realidade mista do Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web ar, 360, 360 vídeo, 360 vídeos, 360 Photo, 360 fotos, 360 Content, imersão Web, immersiveweb, IW
ms.openlocfilehash: 99cf5cf151c41252e43c6051c0d6281d33fe695a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582899"
---
# <a name="webxr-overview"></a><span data-ttu-id="1477a-104">Visão geral do WebXR</span><span class="sxs-lookup"><span data-stu-id="1477a-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="1477a-105">O que é WebXR</span><span class="sxs-lookup"><span data-stu-id="1477a-105">What is WebXR</span></span>

<span data-ttu-id="1477a-106">A **API do dispositivo WebXR** é para acessar os dispositivos **VR (realidade virtual)** e **ar (realidade aumentada)** , incluindo **sensores** e **exibições montadas no cabeçalho** na **Web**.</span><span class="sxs-lookup"><span data-stu-id="1477a-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="1477a-107">A API do dispositivo WebXR está disponível atualmente no Microsoft Edge, e o Chrome versão 79 e versões posteriores dão suporte a WebXR como padrão.</span><span class="sxs-lookup"><span data-stu-id="1477a-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="1477a-108">Você pode verificar o status de suporte do navegador mais recente para WebXR em [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="1477a-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="1477a-109">Saiba mais sobre a [realidade mista do Windows e o novo Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)na seção [o que há de novo](/windows/mixed-reality/mrtk-porting-guide) .</span><span class="sxs-lookup"><span data-stu-id="1477a-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="1477a-110">Exibindo WebXR</span><span class="sxs-lookup"><span data-stu-id="1477a-110">Viewing WebXR</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1477a-111">O Microsoft Edge (Herdado) só dá suporte a WebVR, uma API preterida que não está disponível em navegadores atuais.</span><span class="sxs-lookup"><span data-stu-id="1477a-111">Microsoft Edge (Legacy) only supports WebVR, a deprecated API that is not available in current browsers.</span></span> <span data-ttu-id="1477a-112">No entanto, o novo **[navegador de borda baseado em Chromium](../../whats-new/new-microsoft-edge.md)** dá suporte a WebXR e está disponível para o protótipo de VR no Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1477a-112">However, the new **[Chromium-based Edge browser](../../whats-new/new-microsoft-edge.md)** supports WebXR and is available for VR prototyping in Windows Mixed Reality.</span></span> <span data-ttu-id="1477a-113">O WebVR não estará disponível no novo navegador de borda baseado em Chromium.</span><span class="sxs-lookup"><span data-stu-id="1477a-113">WebVR will not be available in the new Chromium-based Edge browser.</span></span>
> 
> <span data-ttu-id="1477a-114">Se você estiver procurando uma maneira de protótipo WebXR no HoloLens 2 hoje, confira a [realidade do Firefox](https://mixedreality.mozilla.org/firefox-reality/).</span><span class="sxs-lookup"><span data-stu-id="1477a-114">If you're looking for a way to prototype WebXR on HoloLens 2 today, check out [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>

<span data-ttu-id="1477a-115">Para testar se o navegador dá suporte a WebXR, você pode navegar até [exemplos de WebXR](https://immersive-web.github.io/webxr-samples/) no navegador.</span><span class="sxs-lookup"><span data-stu-id="1477a-115">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="1477a-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="1477a-116">See Also</span></span>

* [<span data-ttu-id="1477a-117">Especificação de API do dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="1477a-117">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="1477a-118">Documentação da API do dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="1477a-118">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="1477a-119">Immersiveweb. dev</span><span class="sxs-lookup"><span data-stu-id="1477a-119">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="1477a-120">Exemplos de WebXR</span><span class="sxs-lookup"><span data-stu-id="1477a-120">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="1477a-121">Realidade mista do Windows e o novo Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="1477a-121">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="1477a-122">GitHub W3C da Web de imersão</span><span class="sxs-lookup"><span data-stu-id="1477a-122">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="1477a-123">[API WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1477a-123">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="1477a-124">[API de gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [extensões de gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="1477a-124">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="1477a-125">Manipulando o contexto perdido no WebGL</span><span class="sxs-lookup"><span data-stu-id="1477a-125">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="1477a-126">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="1477a-126">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="1477a-127">glTF</span><span class="sxs-lookup"><span data-stu-id="1477a-127">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="1477a-128">Usando Babylon.js para criar experiências de WebXR</span><span class="sxs-lookup"><span data-stu-id="1477a-128">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="1477a-129">Grupo de comunidades da Web de imersão</span><span class="sxs-lookup"><span data-stu-id="1477a-129">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)