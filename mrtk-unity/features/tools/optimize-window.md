---
title: Otimizar janela
description: Janela Otimizar Documentação no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 7ffc2173cc55c83f126f66002d9240cb349d7f59
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144314"
---
# <a name="optimize-window"></a>Janela Otimizar

A Janela de Otimização do MRTK é um utilitário para ajudar a automatizar e informar no processo de configuração de um projeto de realidade misturada para melhorar [o](../../performance/perf-getting-started.md) desempenho no Unity. Essa ferramenta geralmente se concentra em configurações de renderização que, quando definidas como a predefinição correta, podem salvar milissegundos de processamento.

O *Destino de Build Ativo* é a plataforma de build atualmente [direcionada](https://docs.unity3d.com/Manual/BuildSettings.html) pelo projeto para compilação.

O *Destino de Desempenho* instrui a ferramenta de otimização sobre o tipo de ponto de extremidade do dispositivo a ser destinado.

- *Headsets AR* são dispositivos de classe móvel, como o HoloLens
- *VR Autônomo são dispositivos* de classe móvel, como o Oculus Go ou o Quest
- *VR Tethered* são dispositivos com pc, como SamsungSeyy, Oculus Dimensional ou HTC Vive etc.

![Destino de Desempenho da Janela de Otimização do MRTK](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a>Definindo otimizações

A guia otimização de configurações aborda algumas das configurações de renderização importantes para um projeto do Unity. Esta seção pode ajudar a automatizar e informar quais configurações devem ser alteradas para os resultados com melhor desempenho.

Um ícone de verificação verde significa que um valor ideal foi configurado no projeto/cena para essa configuração específica. Um ícone de aviso amarelo indica que a configuração atual pode ser aprimorada. Clicar no botão associado em uma determinada seção configurará automaticamente essa configuração no projeto/cena do Unity para um valor mais ideal.

![Configurações da janela Otimizar MRTK](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a>Renderização de Instância de Passagem Única

[A renderização de instância de passagem única](https://docs.unity3d.com/Manual/SinglePassInstancing.html) é o caminho de renderização mais eficiente para aplicativos de realidade misturada. Essa configuração garante que o pipeline de renderização seja executado apenas uma vez para ambos os olhos e que as chamadas de desenho sejam instânciadas em ambos os olhos.

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

![MRTK otimizar configurações de janela análise de cena](../images/performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a>Análise de iluminação

Esta seção examinará o número de luzes atualmente na cena, bem como as luzes que devem desabilitar sombras. A conversão de sombra é uma operação muito cara.

### <a name="polygon-count-analysis"></a>Análise de contagem de polígonos

A ferramenta também fornece estatísticas de contagem de polígonos. Pode ser muito útil identificar rapidamente quais GameObjects têm a maior complexidade de polígono em uma determinada cena para direcionar para otimizações.

### <a name="unity-ui-raycast-analysis"></a>Análise de raycast da interface do usuário do Unity

As operações de raycast de gráficos são executadas por ponteiro no MRTK para determinar se algum elemento de interface do usuário do Unity está em foco. Esses raycasts podem ser muito caros e, para ajudar a melhorar o desempenho, os elementos de interface do usuário que não precisam ser retornados nos resultados devem ser desabilitados como destinos de raycast. Cada [elemento Gráfico](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) tem uma propriedade [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) . Essa ferramenta pesquisa elementos de interface do usuário de texto que têm essa propriedade habilitada e, portanto, são prováveis candidatos a serem desabilitados.

## <a name="shader-analysis"></a>Análise do sombreador

O sombreador Padrão do [Unity](https://docs.unity3d.com/Manual/shader-StandardShader.html) pode produzir resultados visuais de alta qualidade para jogos, mas geralmente não é mais adequado para as necessidades de desempenho de aplicativos de realidade misturada, especialmente porque esses aplicativos geralmente são limitados por GPU. Portanto, é recomendável que os desenvolvedores utilizem o sombreador [padrão do MRTK](../rendering/mrtk-standard-shader.md) para equilibrar a & recursos gráficos com o desempenho.

A *guia Análise de Sombreador* examina a pasta Ativo do projeto atual em busca de materiais usando o sombreador Padrão do Unity ou, se desejado, todos os materiais que não usam sombreadores fornecidos pelo Kit de Ferramentas de Realidade Misturada. Depois de descobertos, os desenvolvedores podem converter todos os materiais ou convertê-los individualmente usando os botões apropriados.

![Análise de sombreador de configurações de janela de otimização do MRTK](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a>Veja também

- [Desempenho](../../performance/perf-getting-started.md)
- [Estabilização de holograma](../../performance/hologram-stabilization.md)
