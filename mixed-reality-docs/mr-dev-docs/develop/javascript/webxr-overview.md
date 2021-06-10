---
title: Usando o WebXR com Windows Mixed Reality
description: Conheça as noções básicas de como usar e desenvolver aplicativos WebXR em execução Windows Mixed Reality headsets imersivos.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, web vr, web xr, web mr, web ar, 360, 360 vídeo, 360 vídeos, 360 fotos, 360 fotos, 360 conteúdo, web imersiva, immersiveweb, IW
ms.openlocfilehash: fa4d11fac59e25f43d9d55de16d3b0c35e8166b7
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600105"
---
# <a name="webxr-overview"></a><span data-ttu-id="45881-104">Visão geral do WebXR</span><span class="sxs-lookup"><span data-stu-id="45881-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="45881-105">O que é o WebXR</span><span class="sxs-lookup"><span data-stu-id="45881-105">What is WebXR</span></span>

<span data-ttu-id="45881-106">A [**API de Dispositivo WebXR**](https://www.w3.org/TR/webxr/) é para acessar dispositivos de VR  **(realidade virtual)** e **AR (realidade** aumentada), incluindo sensores e exibições **montadas** com a cabeça na **Web.**</span><span class="sxs-lookup"><span data-stu-id="45881-106">The [**WebXR Device API**](https://www.w3.org/TR/webxr/) is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="45881-107">Atualmente, a API do dispositivo WebXR está disponível no Microsoft Edge e chrome versão 79 e versões posteriores dá suporte ao WebXR como padrão.</span><span class="sxs-lookup"><span data-stu-id="45881-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="45881-108">Você pode verificar o status de suporte mais recente do navegador para WebXR [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="45881-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="45881-109">Exibindo o WebXR</span><span class="sxs-lookup"><span data-stu-id="45881-109">Viewing WebXR</span></span>

<span data-ttu-id="45881-110">Você pode exibir as experiências do WebXR Windows Mixed Reality [e as](../../whats-new/new-microsoft-edge.md) novas Microsoft Edge e [Firefox Reality.](https://mixedreality.mozilla.org/firefox-reality/)</span><span class="sxs-lookup"><span data-stu-id="45881-110">You can view WebXR experinces on [Windows Mixed Reality and the new Microsoft Edge](../../whats-new/new-microsoft-edge.md) and [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>
<span data-ttu-id="45881-111">Para testar se o navegador dá suporte ao WebXR, você pode navegar até [Exemplos do WebXR](https://immersive-web.github.io/webxr-samples/) em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="45881-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="45881-112">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="45881-112">See Also</span></span>

* [<span data-ttu-id="45881-113">Usando Babylon.js para criar experiências webXR</span><span class="sxs-lookup"><span data-stu-id="45881-113">Using Babylon.js to create WebXR experiences</span></span>](./tutorials/babylonjs-webxr-helloworld/introduction-01.md)
* [<span data-ttu-id="45881-114">Especificação da API de Dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="45881-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="45881-115">Documentação da API de Dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="45881-115">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="45881-116">Immersiveweb.dev</span><span class="sxs-lookup"><span data-stu-id="45881-116">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="45881-117">Exemplos do WebXR</span><span class="sxs-lookup"><span data-stu-id="45881-117">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="45881-118">Windows Mixed Reality e o novo Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="45881-118">Windows Mixed Reality and the new Microsoft Edge</span></span>](../../whats-new/new-microsoft-edge.md)
* [<span data-ttu-id="45881-119">Github web imersivo W3C</span><span class="sxs-lookup"><span data-stu-id="45881-119">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="45881-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="45881-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="45881-121">[Api do Gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [Extensões do Gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="45881-121">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="45881-122">Manipulando contexto perdido no WebGL</span><span class="sxs-lookup"><span data-stu-id="45881-122">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="45881-123">Ponteiro de ponteiro</span><span class="sxs-lookup"><span data-stu-id="45881-123">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="45881-124">glTF</span><span class="sxs-lookup"><span data-stu-id="45881-124">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="45881-125">Grupo de comunidade da Web imersivo</span><span class="sxs-lookup"><span data-stu-id="45881-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)