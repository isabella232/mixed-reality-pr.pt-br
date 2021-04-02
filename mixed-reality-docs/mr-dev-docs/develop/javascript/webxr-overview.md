---
title: Usando o WebXR com o Windows Mixed Reality
description: Aprenda as noções básicas de como usar e desenvolver para aplicativos WebXR executados em headsets de imersão de realidade mista do Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web ar, 360, 360 vídeo, 360 vídeos, 360 Photo, 360 fotos, 360 Content, imersão Web, immersiveweb, IW
ms.openlocfilehash: 0954d6554acea8474548a3703de35971a76f7770
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088475"
---
# <a name="webxr-overview"></a><span data-ttu-id="da713-104">Visão geral do WebXR</span><span class="sxs-lookup"><span data-stu-id="da713-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="da713-105">O que é WebXR</span><span class="sxs-lookup"><span data-stu-id="da713-105">What is WebXR</span></span>

<span data-ttu-id="da713-106">A [**API do dispositivo WebXR**](https://www.w3.org/TR/webxr/) é para acessar os dispositivos **VR (realidade virtual)** e **ar (realidade aumentada)** , incluindo **sensores** e **exibições montadas no cabeçalho** na **Web**.</span><span class="sxs-lookup"><span data-stu-id="da713-106">The [**WebXR Device API**](https://www.w3.org/TR/webxr/) is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="da713-107">A API do dispositivo WebXR está disponível atualmente no Microsoft Edge, e o Chrome versão 79 e versões posteriores dão suporte a WebXR como padrão.</span><span class="sxs-lookup"><span data-stu-id="da713-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="da713-108">Você pode verificar o status de suporte do navegador mais recente para WebXR em [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="da713-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="da713-109">Exibindo WebXR</span><span class="sxs-lookup"><span data-stu-id="da713-109">Viewing WebXR</span></span>

<span data-ttu-id="da713-110">Você pode exibir WebXR experinces no [Windows Mixed Reality e a nova realidade do Microsoft Edge e do](/windows/mixed-reality/whats-new/new-microsoft-edge) [Firefox](https://mixedreality.mozilla.org/firefox-reality/).</span><span class="sxs-lookup"><span data-stu-id="da713-110">You can view WebXR experinces on [Windows Mixed Reality and the new Microsoft Edge](/windows/mixed-reality/whats-new/new-microsoft-edge) and [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>
<span data-ttu-id="da713-111">Para testar se o navegador dá suporte a WebXR, você pode navegar até [exemplos de WebXR](https://immersive-web.github.io/webxr-samples/) no navegador.</span><span class="sxs-lookup"><span data-stu-id="da713-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="da713-112">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="da713-112">See Also</span></span>

* [<span data-ttu-id="da713-113">Usando Babylon.js para criar experiências de WebXR</span><span class="sxs-lookup"><span data-stu-id="da713-113">Using Babylon.js to create WebXR experiences</span></span>](/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-helloworld/introduction-01)
* [<span data-ttu-id="da713-114">Especificação de API do dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="da713-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="da713-115">Documentação da API do dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="da713-115">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="da713-116">Immersiveweb.dev</span><span class="sxs-lookup"><span data-stu-id="da713-116">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="da713-117">Exemplos de WebXR</span><span class="sxs-lookup"><span data-stu-id="da713-117">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="da713-118">Realidade mista do Windows e o novo Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="da713-118">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/whats-new/new-microsoft-edge)
* [<span data-ttu-id="da713-119">GitHub W3C da Web de imersão</span><span class="sxs-lookup"><span data-stu-id="da713-119">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="da713-120">[API WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="da713-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="da713-121">[API de gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [extensões de gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="da713-121">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="da713-122">Manipulando o contexto perdido no WebGL</span><span class="sxs-lookup"><span data-stu-id="da713-122">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="da713-123">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="da713-123">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="da713-124">glTF</span><span class="sxs-lookup"><span data-stu-id="da713-124">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="da713-125">Grupo de comunidades da Web de imersão</span><span class="sxs-lookup"><span data-stu-id="da713-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
