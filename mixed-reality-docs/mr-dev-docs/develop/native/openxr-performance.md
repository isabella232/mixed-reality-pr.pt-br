---
title: Desempenho do OpenXR
description: Depure o desempenho da GPU de seus aplicativos OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware, desempenho, otimização, depuração de GPU, RenderDoc, PIX
ms.openlocfilehash: 7199b29067094d402348f00a9d26b93cf7e5393e
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613170"
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
