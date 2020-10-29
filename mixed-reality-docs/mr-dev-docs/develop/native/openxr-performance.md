---
title: Desempenho do OpenXR
description: Depure o desempenho da GPU de seus aplicativos OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware, desempenho, otimização, depuração de GPU, RenderDoc, PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675027"
---
# <a name="openxr-performance"></a>Desempenho do OpenXR

No HoloLens 2, há várias maneiras de enviar dados de composição por meio `xrEndFrame` do qual resultará em pós-processamento que terá uma penalidade de desempenho perceptível.
Para evitar o desempenho penalities, [envie um `XrCompositionProjectionLayer` único](openxr-best-practices.md#use-a-single-projection-layer) com as seguintes características:
* [Usar uma matriz de textura SwapChain](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Usar o formato SwapChain de cor primária](openxr-best-practices.md#select-a-swapchain-format)
* [Usar as dimensões de exibição recomendadas](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Não definir o `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` sinalizador
* Defina `XrCompositionLayerDepthInfoKHR` `minDepth` como 0,0 f e `maxDepth` 1,0 f

Considerações adicionais resultarão em melhor desempenho:
* [Usar o formato de profundidade de 16 bits](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Fazer chamadas de desenho em instância](openxr-best-practices.md#render-with-texture-array-and-vprt)
