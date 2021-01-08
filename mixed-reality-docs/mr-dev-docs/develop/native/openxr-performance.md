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
# <a name="openxr-performance"></a>Desempenho do OpenXR

No HoloLens 2, há várias maneiras de enviar dados de composição `xrEndFrame` , o que pode resultar em penalidades de desempenho de pós-processamento e perceptíveis.

Para evitar o mau desempenho, [envie um `XrCompositionProjectionLayer` único](openxr-best-practices.md#use-a-single-projection-layer) com as seguintes características:

* [Usar uma matriz de textura SwapChain](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Usar o formato SwapChain de cor primária](openxr-best-practices.md#select-a-swapchain-format)
* [Usar as dimensões de exibição recomendadas](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Não definir o `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` sinalizador
* Defina `XrCompositionLayerDepthInfoKHR` `minDepth` como 0,0 f e `maxDepth` 1,0 f

Para obter um melhor desempenho, considere:

* [Usando o formato de profundidade de 16 bits](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Fazendo chamadas de desenho em instância](openxr-best-practices.md#render-with-texture-array-and-vprt)
