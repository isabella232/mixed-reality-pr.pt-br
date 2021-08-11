---
title: Práticas recomendadas do OpenXR
description: Conheça as práticas recomendadas para qualidade visual, estabilidade e desempenho para seus aplicativos OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Chronos, BasicXRApp, DirectX, aplicativo nativo, nativo, mecanismo personalizado, middleware, práticas recomendadas, desempenho, qualidade, estabilidade
ms.openlocfilehash: 2cbd05417f62f7380b048f692295bbbe98ceba5bce69c4f1dae21aec812ec450
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207844"
---
# <a name="openxr-app-best-practices"></a>Práticas recomendadas do aplicativo OpenXR

Você pode ver um exemplo das práticas recomendadas abaixo no arquivo OpenXRProgram.cpp do <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp.</a> A função Run() no início captura um fluxo de código de aplicativo OpenXR típico da inicialização para o evento e o loop de renderização.

## <a name="best-practices-for-visual-quality-and-stability"></a>Práticas recomendadas para a qualidade e a estabilidade do visual

As práticas recomendadas nesta seção descrevem como obter a melhor qualidade visual e estabilidade em qualquer aplicativo OpenXR.

Para mais recomendações de desempenho específicas HoloLens 2, consulte a seção Práticas recomendadas para desempenho [HoloLens 2](#best-practices-for-performance-on-hololens-2) abaixo.

### <a name="gamma-correct-rendering"></a>Renderização corretamente do gama

É necessário ter cuidado para garantir que o pipeline de renderização seja gama-correto. Ao renderizar para um swapchain, o formato de exibição renderização-destino deve corresponder ao formato de swapchain. Por exemplo, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` para o formato swapchain e a exibição render-target.
Haverá uma exceção se o pipeline de renderização do aplicativo fizer uma conversão sRGB manual no código do sombreador. O aplicativo deve solicitar um formato de swapchain sRGB, mas usar o formato linear para a exibição de destino de renderização. Por exemplo, solicite `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` como o formato de swapchain, mas use como a exibição de destino de renderização para impedir que o conteúdo seja corrigido com gama `DXGI_FORMAT_B8G8R8A8_UNORM` dupla.

### <a name="submit-depth-buffer-for-projection-layers"></a>Enviar buffer de profundidade para camadas de projeção

Sempre use `XR_KHR_composition_layer_depth` a extensão e envie o buffer de profundidade junto com a camada de projeção ao enviar um quadro para `xrEndFrame` .
A habilitação da reprodução de profundidade de hardware no HoloLens 2 melhora a estabilidade do holograma.

### <a name="choose-a-reasonable-depth-range"></a>Escolher um intervalo de profundidade razoável

Prefira um intervalo de profundidade mais estreito para o escopo do conteúdo virtual para ajudar a estabilidade do holograma HoloLens.
Por exemplo, a amostra OpenXrProgram.cpp está usando de 0,1 metros a 20 metros.
Use [reversed-Z](https://developer.nvidia.com/content/depth-precision-visualized) para uma resolução de profundidade mais uniforme.
No HoloLens 2, usar o formato de profundidade preferencial ajudará a obter melhor taxa de quadros e desempenho, embora buffers de profundidade de 16 bits forneçam uma resolução de profundidade menor do que buffers de profundidade de `DXGI_FORMAT_D16_UNORM` 24 bits.
Seguir essas práticas recomendadas para fazer o melhor uso da resolução de profundidade se torna mais importante.

### <a name="prepare-for-different-environment-blend-modes"></a>Preparar-se para diferentes modos de combinação de ambiente

Se seu aplicativo também for executado em headsets imersivos que bloqueiam completamente o mundo, enumere os modos de mesclagem de ambiente com suporte usando a API e prepare o conteúdo de renderização `xrEnumerateEnvironmentBlendModes` corretamente.
Por exemplo, para um sistema com como o HoloLens, o aplicativo deve usar transparente como a cor clara, enquanto para um sistema com , o aplicativo deve renderizar alguma cor opaca ou alguma sala virtual na tela de `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` `XR_ENVIRONMENT_BLEND_MODE_OPAQUE` fundo.

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>Escolher espaço de referência nãobounded como o espaço raiz do aplicativo

Os aplicativos normalmente estabelecem algum espaço de coordenadas do mundo raiz para conectar exibições, ações e hologramas.
Use quando a extensão for suportada para estabelecer um sistema de coordenadas de escala mundial, permitindo que seu aplicativo evite desaparar o holograma indesejável quando o usuário se mover para longe `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` (por exemplo, 5 metros de distância) de onde o aplicativo é [](../../design/coordinate-systems.md#building-a-world-scale-experience)iniciado.
Use `XR_REFERENCE_SPACE_TYPE_LOCAL` como um fallback se a extensão de espaço não estiver disponível.

### <a name="associate-hologram-with-spatial-anchor"></a>Associar holograma à âncora espacial

Ao usar um espaço de referência não ligado, os hologramas que você coloca diretamente nesse espaço de referência podem se desinalo conforme o usuário vai para salas distantes e, em seguida, [volta .](../../design/coordinate-systems.md#building-a-world-scale-experience)
Para usuários de holograma colocarem em um local discreto no mundo, crie uma âncora espacial usando [a](../../design/spatial-anchors.md#best-practices) função de extensão e posicione o `xrCreateSpatialAnchorSpaceMSFT` holograma em sua origem. Isso manterá esse holograma independentemente estável ao longo do tempo.

### <a name="support-mixed-reality-capture"></a>Suporte à captura de realidade misturada

Embora HoloLens exibição primária do HoloLens 2 use a combinação [](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)de ambientes aditivos, quando o usuário iniciar a captura de realidade misturada, o conteúdo de renderização do aplicativo será mesclado alfa com o fluxo de vídeo do ambiente.
Para obter a melhor qualidade visual em vídeos de captura de realidade misturada, é melhor definir o no da camada `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` de `layerFlags` projeção.

## <a name="best-practices-for-performance-on-hololens-2"></a>Práticas recomendadas para o desempenho HoloLens 2

Como um dispositivo móvel com suporte à reprojeção de hardware, o HoloLens 2 tem requisitos mais rígidos para um desempenho ideal.  Há várias maneiras de enviar dados de composição, o que resulta no pós-processamento com uma penalidade de desempenho perceptível.

### <a name="select-a-swapchain-format"></a>Selecionar um formato de permuta

Sempre enumere os formatos de pixel com suporte usando e escolha o primeiro formato de pixel de cor e profundidade do runtime ao qual o aplicativo dá suporte, porque é isso que o runtime prefere para o `xrEnumerateSwapchainFormats` desempenho ideal. Observe que, HoloLens 2 e normalmente é a primeira opção para `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` obter um melhor desempenho de `DXGI_FORMAT_D16_UNORM` renderização. Essa preferência pode ser diferente em headsets VR em execução em um computador desktop, em que buffers de profundidade de 24 bits têm menos impacto no desempenho.
  
**Aviso de desempenho:** O uso de um formato diferente do formato de cor da sequência de permuta primária resultará no pós-processamento do runtime, o que resulta em uma penalidade de desempenho significativa.

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>Renderizar com parâmetros de renderização recomendados e tempo de quadro

Sempre renderizar com a largura/altura da configuração de exibição recomendada ( e de ) e sempre use a API para consultar a pose de exibição recomendada, o FOV e outros parâmetros de renderização antes da `recommendedImageRectWidth` `recommendedImageRectHeight` `XrViewConfigurationView` `xrLocateViews` renderização.
Sempre use o `XrFrameEndInfo.predictedDisplayTime` da chamada mais recente ao consultar `xrWaitFrame` poses e exibições.
Isso permite que HoloLens ajuste a renderização e otimize a qualidade visual para a pessoa que está usando o HoloLens.

### <a name="use-a-single-projection-layer"></a>Usar uma única camada de projeção

HoloLens 2 tem potência de GPU limitada para renderizar conteúdo e um compositor de hardware otimizado para uma única camada de projeção.
Sempre usar uma única camada de projeção pode ajudar a taxa de quadros, a estabilidade do holograma e a qualidade visual do aplicativo.  
  
**Aviso de desempenho:** Enviar qualquer coisa, menos uma única camada de proteção, resultará em pós-processamento em runtime, o que resulta em uma penalidade de desempenho significativa.

### <a name="render-with-texture-array-and-vprt"></a>Renderizar com matriz de textura e VPRT

Crie um `xrSwapchain` para os olhos esquerdo e direito usando para alterno de cores e outro para `arraySize=2` profundidade.
Renderizar o olho esquerdo na fatia 0 e o olho direito na fatia 1.
Use um sombreador com VPRT e chamadas de desenho com instância para renderização estereotipada para minimizar a carga de GPU.
Isso também permite que a otimização do runtime alcance o melhor desempenho HoloLens 2.
Alternativas ao uso de uma matriz de textura, como renderização de largura dupla ou uma alternação separada por olho, resultarão em pós-processamento de runtime, o que resulta em uma penalidade de desempenho significativa.

### <a name="avoid-quad-layers"></a>Evitar camadas quad

Em vez de enviar camadas quad como camadas de composição com `XrCompositionLayerQuad` , renderizar o conteúdo quad diretamente na conjunto de permuta de projeção.

**Aviso de desempenho:** Fornecer camadas adicionais além de uma única camada de projeção, como camadas quad, resultará em pós-processamento de runtime, o que resulta em uma penalidade de desempenho significativa.