---
title: Janela de otimização
description: Documentação otimizar janela no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 8b8928e9c723ffa9fd08d22866b8ee5748e38ace
ms.sourcegitcommit: 78746bef0e1ffe1480e89fed8cd30f6f8b389e8d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/27/2021
ms.locfileid: "114713576"
---
# <a name="optimize-window"></a>Janela de otimização

A janela de otimização do MRTK é um utilitário para ajudar a automatizar e informar o processo de configuração de um projeto de realidade misturada para o melhor [desempenho](../../performance/perf-getting-started.md) no Unity. Essa ferramenta geralmente se concentra na renderização de configurações que, quando definidas para a predefinição correta, podem economizar milissegundos de processamento.

> [!NOTE]
> A **janela otimizar** pode ser aberta navegando até **Mixed Reality**  >  **Utilities**  >  **otimizar janela** no menu de barra superior no editor do Unity.

O *destino de Build ativo* é a [plataforma de compilação atualmente destinada](https://docs.unity3d.com/Manual/BuildSettings.html) ao projeto para compilação.

O *destino de desempenho* instrui a ferramenta otimizar em que tipo de pontos de extremidade do dispositivo deve ser direcionado.

- *Headsets do ar* são dispositivos de classe móvel, como HoloLens
- *VR autônomo* são dispositivos de classe móvel, como o Oculus go ou Quest
- O *VR* conectado são dispositivos com PC, como o Samsung Odyssey, o Oculus Rift ou o HTC naopak, etc.

![MRTK otimizar o destino de desempenho de janela](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a>Definindo otimizações

A guia otimização de configurações aborda algumas das configurações de renderização importantes para um projeto do Unity. Esta seção pode ajudar a automatizar e informá-lo sobre quais configurações devem ser alteradas para os melhores resultados de desempenho.

Um ícone de verificação verde significa que um valor ideal foi configurado no projeto/cena para essa configuração específica. Um ícone de aviso amarelo indica que a configuração atual pode ser aprimorada. Clicar no botão associado em uma determinada seção irá configurar automaticamente essa configuração no projeto/cena do Unity para um valor ideal.

![MRTK otimizar Configurações de janela](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a>Renderização de passagem única em instância

A [renderização de passagem única em instância](https://docs.unity3d.com/Manual/SinglePassInstancing.html) é o caminho de renderização mais eficiente para aplicativos de realidade misturada. Essa configuração garante que o pipeline de renderização seja executado apenas uma vez para ambos os olhos e que as chamadas de desenho sejam modeladas em ambos os olhos.

### <a name="depth-buffer-sharing"></a>Compartilhamento de buffer de profundidade

Para melhorar a [estabilização do holograma](../../performance/hologram-Stabilization.md), os desenvolvedores podem compartilhar o buffer de profundidade do aplicativo, que fornece as informações da plataforma sobre onde e quais hologramas se estabilizam na cena renderizada.

### <a name="depth-buffer-format"></a>Formato de buffer de profundidade

Além disso, para *headsets de ar*, é recomendável utilizar um formato de profundidade de 16 bits ao habilitar o compartilhamento de buffer de profundidade em comparação com o de 24 bits. Isso significa menor precisão, mas economiza desempenho. Se o [combate ao z](https://en.wikipedia.org/wiki/Z-fighting) ocorrer porque há menos precisão no cálculo de profundidade para pixels, é recomendável mover o plano de [clipe distante](https://docs.unity3d.com/Manual/class-Camera.html) mais perto da câmera (ex: 50 milhões em vez de 1000m).

> [!NOTE]
> Se você estiver usando o *formato de profundidade de 16 bits*, os efeitos necessários do buffer de estêncil não funcionarão porque [o Unity não cria um buffer de estêncil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) nessa configuração. A seleção de *formato de profundidade de 24 bits, por* outro lado, geralmente criará um [buffer de estêncil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html), se aplicável na plataforma de gráficos do ponto de extremidade.
>
> Se estiver usando um [componente de máscara](https://docs.unity3d.com/Manual/script-Mask.html) que requer o buffer de estêncil, considere usar [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) em vez disso, que não requer o buffer de estêncil e, portanto, pode ser usado em conjunto com um formato de *profundidade de 16 bits*.

### <a name="real-time-global-illumination"></a>Iluminação global em tempo real

A [iluminação global em tempo real](https://docs.unity3d.com/Manual/GIIntro.html) no Unity pode fornecer resultados estéticos fantásticos, mas com um custo muito alto. A luminosidade de iluminação global é muito cara em realidade misturada e, portanto, é recomendável desabilitar esse recurso no desenvolvimento.

> [!NOTE]
> As configurações de iluminação global no Unity são definidas por cena e não uma vez em todo o projeto.

## <a name="scene-analysis"></a>Análise de cena

A guia *análise de cena* foi projetada para informar aos desenvolvedores sobre quais elementos atualmente na cena provavelmente terão o maior impacto no desempenho.

![MRTK otimizar janela Configurações análise de cena](../images/performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a>Análise de iluminação

Esta seção examinará o número de luzes atualmente na cena, bem como as luzes que devem desabilitar sombras. A conversão de sombra é uma operação muito cara.

### <a name="polygon-count-analysis"></a>Análise de contagem de polígonos

A ferramenta também fornece estatísticas de contagem de polígonos. Pode ser muito útil identificar rapidamente quais GameObjects têm a maior complexidade do polígono em uma determinada cena para o destino de otimizações.

### <a name="unity-ui-raycast-analysis"></a>Análise de Raycast da interface do usuário do Unity

As operações de Raycast de gráficos são executadas por ponteiro em MRTK para determinar se os elementos da interface do usuário do Unity estão em foco. Esses raycasts podem ser bastante caros e ajudar a melhorar o desempenho, os elementos da interface do usuário que não precisam ser retornados nos resultados devem ser desabilitados como destinos do Raycast. Cada elemento [gráfico](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) tem uma [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) propriedade. Essa ferramenta pesquisará os elementos da interface do usuário de texto que têm essa propriedade habilitada e, portanto, são prováveis candidatos a serem desabilitados.

## <a name="shader-analysis"></a>Análise de sombreador

O [sombreador padrão do Unity](https://docs.unity3d.com/Manual/shader-StandardShader.html) pode produzir resultados visuais de alta qualidade para jogos, mas geralmente não é mais adequado para as necessidades de desempenho de aplicativos de realidade misturada, especialmente porque esses aplicativos geralmente são vinculados à GPU. Portanto, é recomendável aos desenvolvedores utilizar o [sombreador padrão MRTK](../rendering/mrtk-standard-shader.md) para equilibrar estética & recursos gráficos com desempenho.

a guia *análise de sombreador* examina a pasta de ativos do projeto atual em busca de materiais usando o sombreador padrão do Unity ou, se desejado, todos os materiais que não usam realidade misturada Toolkit sombreadores fornecidos. Depois de descoberto, os desenvolvedores podem converter todos os materiais ou converter individualmente usando os botões apropriados.

![MRTK otimizar a janela Configurações o sombreador](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a>Veja também

- [Desempenho](../../performance/perf-getting-started.md)
- [Estabilização de holograma](../../performance/hologram-stabilization.md)
