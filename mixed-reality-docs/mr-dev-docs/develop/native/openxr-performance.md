---
title: Desempenho do OpenXR
description: Saiba como depurar o desempenho de GPU de seus aplicativos de realidade misturada OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Chronos, BasicXRApp, DirectX, aplicativo nativo, nativo, mecanismo personalizado, middleware, desempenho, otimização, depuração de GPU, RenderDoc, WIDGET
ms.openlocfilehash: f4462da954a3b6093e47f03e75b460671e7638f406b761ad6e05689ab97b3ddc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213170"
---
# <a name="openxr-performance"></a>Desempenho do OpenXR

No HoloLens 2, há várias maneiras de enviar dados de composição por meio do , o que pode resultar em penalidades de desempenho `xrEndFrame` pós-processamento e perceptíveis.

Para evitar um desempenho ruim, [envie um único `XrCompositionProjectionLayer` ](openxr-best-practices.md#use-a-single-projection-layer) com as seguintes características:

* [Usar um conjunto de permuta de matriz de textura](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Usar o formato de permuta de cor primária](openxr-best-practices.md#select-a-swapchain-format)
* [Usar as dimensões de exibição recomendadas](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Não definir o `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` sinalizador
* Definir o `XrCompositionLayerDepthInfoKHR` `minDepth` como 0,0f e `maxDepth` como 1.0f

Para melhorar o desempenho, considere:

* [Usando o formato de profundidade de 16 bits](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Fazendo chamadas de desenho em instâncias](openxr-best-practices.md#render-with-texture-array-and-vprt)
