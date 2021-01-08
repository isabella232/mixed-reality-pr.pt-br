---
title: Desempenho do OpenXR
description: Saiba como depurar o desempenho da GPU de seus aplicativos de realidade mista do OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware, desempenho, otimização, depuração de GPU, RenderDoc, PIX
ms.openlocfilehash: 158bd2eef8f38f16a1fb5299d64335aca33a3b7f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006756"
---
# <a name="openxr-performance"></a><span data-ttu-id="03dd6-104">Desempenho do OpenXR</span><span class="sxs-lookup"><span data-stu-id="03dd6-104">OpenXR performance</span></span>

<span data-ttu-id="03dd6-105">No HoloLens 2, há várias maneiras de enviar dados de composição `xrEndFrame` , o que pode resultar em penalidades de desempenho de pós-processamento e perceptíveis.</span><span class="sxs-lookup"><span data-stu-id="03dd6-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame`, which can result in post-processing and noticeable performance penalties.</span></span>

<span data-ttu-id="03dd6-106">Para evitar o mau desempenho, [envie um `XrCompositionProjectionLayer` único](openxr-best-practices.md#use-a-single-projection-layer) com as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="03dd6-106">To avoid poor performance, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>

* [<span data-ttu-id="03dd6-107">Usar uma matriz de textura SwapChain</span><span class="sxs-lookup"><span data-stu-id="03dd6-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="03dd6-108">Usar o formato SwapChain de cor primária</span><span class="sxs-lookup"><span data-stu-id="03dd6-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="03dd6-109">Usar as dimensões de exibição recomendadas</span><span class="sxs-lookup"><span data-stu-id="03dd6-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="03dd6-110">Não definir o `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` sinalizador</span><span class="sxs-lookup"><span data-stu-id="03dd6-110">Don't set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="03dd6-111">Defina `XrCompositionLayerDepthInfoKHR` `minDepth` como 0,0 f e `maxDepth` 1,0 f</span><span class="sxs-lookup"><span data-stu-id="03dd6-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="03dd6-112">Para obter um melhor desempenho, considere:</span><span class="sxs-lookup"><span data-stu-id="03dd6-112">For better performance, consider:</span></span>

* [<span data-ttu-id="03dd6-113">Usando o formato de profundidade de 16 bits</span><span class="sxs-lookup"><span data-stu-id="03dd6-113">Using the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="03dd6-114">Fazendo chamadas de desenho em instância</span><span class="sxs-lookup"><span data-stu-id="03dd6-114">Making instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
