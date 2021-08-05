---
title: Conceitos básicos de qualidade
description: Saiba mais sobre os Conceitos básicos de qualidade da criação de aplicativos de realidade misturada.
author: qianw211
ms.author: v-qianwen
ms.date: 07/15/2021
ms.topic: article
keywords: conceitos básicos de qualidade, estudo de caso, projeto, exemplo, MRTK, Toolkit de Realidade Misturada, Unity, aplicativos de exemplo, aplicativos de exemplo, open-source, Microsoft Store, HoloLens, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: a8189ca8cb161bb792ad298535c32eac1a47260d8d5559c2383e0322b2cbeb03
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211934"
---
# <a name="quality-fundamentals"></a>Conceitos básicos de qualidade

Conceitos básicos de qualidade HoloLens aplicativo 2 que demonstra os conceitos básicos da criação de uma ótima experiência de realidade misturada.  Em vez de apenas aprender e ler sobre problemas de qualidade na realidade misturada, agora podemos experimentar problemas comuns de ambiente, design e desempenho e soluções em primeira mão selecionando as opções fornecidas no aplicativo.

Para baixar e instalar o aplicativo, acesse a página de download do aplicativo:

> [!div class="nextstepaction"]
> [Conceitos básicos de qualidade](https://www.microsoft.com/p/quality-fundamentals/9mwz852q88fw?activetab=pivot:overviewtab)

![Home page conceitos básicos de qualidade](images\qf-homepage.jpg)

Neste aplicativo de exemplo, aprenderemos sobre:

>[!div class = "checklist"]
> * [E/S do dispositivo e ambiente:](#device-io-and-environment)como os fatores ambientais podem afetar HoloLens desempenho.
> * [Âncoras Espaciais:](#anchor-fundamentals)como alinhar hologramas a um espaço físico usando âncoras espaciais.
> * [Estabilidade holográfica e fidelidade:](#stability-and-fidelity)explore técnicas para ajudar a melhorar a estabilidade e a fidelidade de Hologramas.
> * [Conceitos básicos do ativo 3D:](#3d-asset-fundamentals)como otimizar ativos 3D para manter alta fidelidade visual. 

## <a name="device-io-and-environment"></a>Ambiente e E/S do dispositivo

Inicie o aplicativo Conceitos Básicos de Qualidade HoloLens. Depois que a home page do aplicativo aparecer, selecione **E/S do** dispositivo e Ambiente.  Exploraremos como os sensores HoloLens ambiente ao redor afetam o mapeamento espacial, o acompanhamento e o posicionamento dos hologramas. 

### <a name="surfaces"></a>Surfaces

Espelhos ou superfícies com terminações espelhadas podem confundir HoloLens sensores sobre a forma do objeto.  Os objetos refletidos na superfície podem ser interpretados pelo dispositivo como ambiente de alteração, o que pode fazer com que o dispositivo perca o controle.  Se as superfícies espelhadas estão causando desafios para HoloLens, considere adicionar uma tela ou as blindas que podem ser bloqueadas.

Para obter mais informações, [consulte superfícies em um espaço em HoloLens](/hololens/hololens-environment-considerations#surfaces-in-a-space) de [ambiente.](/hololens/hololens-environment-considerations)

### <a name="lighting"></a>Iluminação

HoloLens desempenho pode ser afetado negativamente por condições de luz muito baixas ou muito brilhante.  Os sensores de rastreamento na HoloLens precisam de cerca de 500 a 1.000 de luz para operar de maneira ideal. Você pode usar um dispositivo móvel ou um aplicativo móvel para medir a quantidade de luz em seu espaço.

Para obter mais informações, consulte [iluminação](/hololens/hololens-environment-considerations?branch=pr-en-us-3071#lighting) em [HoloLens de ambiente.](/hololens/hololens-environment-considerations)

## <a name="anchor-fundamentals"></a>Conceitos básicos de âncora

Para explorar como usar Âncoras Espaciais para alinhar hologramas a um espaço físico, selecione **Âncoras na** home page do aplicativo.

Nesta parte do aplicativo, exploraremos os seguintes cenários de usuário:

>[!div class = "checklist"]
> * O que acontece quando nenhuma âncora está sendo aplicada a um objeto .
> * Quando várias Âncoras Espaciais estão sendo usadas para um grupo de objetos .
> * Compartilhar uma Âncora Espacial entre vários colaboradores usando um código QR.
> * Posicionamento de âncora para objetos muito grandes em um espaço.

Para obter mais informações, consulte [Âncoras espaciais](/windows/mixed-reality/design/spatial-anchors) na [documentação da Realidade Misturada.](/windows/mixed-reality/design/spatial-anchors)

## <a name="stability-and-fidelity"></a>Estabilidade e fidelidade

Na home page do aplicativo, selecione **Estabilidade e Fidelidade** para explorar como melhorar a estabilidade do holograma.

Exploraremos os seguintes conceitos principais:

>[!div class = "checklist"]
> * [Taxa de quadros](#frame-rate).
> * [Reprodução de estágio tardio (LSR)](#late-stage-reprojection-lsr).
> * [Z-fighting](#z-fighting).
> * [Suavização de](#anti-aliasing).

### <a name="frame-rate"></a>Taxa de quadros

Para fornecer a melhor experiência de holograma possível, os desenvolvedores de aplicativos devem manter 60 FPS (quadros por segundo).  Nesta parte do aplicativo, alterne entre diferentes opções de contagem de triângulos para experimentar a diferença com várias taxas de quadros.

![Otimização da contagem de triângulos](images\qf-triangle-count-optimization.png)

Para obter mais informações, consulte [Taxa de quadros](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability#frame-rate) no artigo de estabilidade do [holograma.](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability)

### <a name="late-stage-reprojection-lsr"></a>LSR (reprodução de estágio tardio)

A reprojeção é usada para estabilizar hologramas à medida que os usuários se movem em torno de seu espaço.  Experimente as diferentes opções de reprodução fornecidas por essa parte do aplicativo para ver a diferença na qualidade do holograma.

![Experimente as diferentes opções de reprojeto para experimentar a diferença.](images\qf-lsr-modes.jpg)

Para obter informações detalhadas, consulte [reprojection](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability#reprojection) no artigo [de estabilidade do holograma.](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability)

### <a name="z-fighting"></a>Z-fighting

O Z-fighting ocorre quando o aplicativo de realidade misturada não consegue distinguir qual objeto está na frente do outro.  Você observará a cintilação dos objetos holográficos à medida que eles buscam o mesmo valor de profundidade z.  Experimente os efeitos do z-fighting no aplicativo alterando o posicionamento de um objeto holográfico, o logotipo em uma bicicleta nesse caso.

![Experimente o z-fighting com posicionamentos de objeto.](images\qf-z-fighting.jpg)

Para obter informações detalhadas sobre o z-fighting, confira [habilitar](/windows/mixed-reality/develop/unity/recommended-settings-for-unity#enable-depth-buffer-sharing) o compartilhamento de buffer de profundidade no [artigo configurações recomendadas para o Unity.](/windows/mixed-reality/develop/unity/recommended-settings-for-unity)

### <a name="anti-aliasing"></a>Suavização

A suavização é uma técnica usada para suavizar bordas irregulares em linhas curvadas e diagonais em hologramas.  Nesta parte do aplicativo, experimente os afetações de alias em texto exibido e spokes de bicicleta.  

## <a name="3d-asset-fundamentals"></a>Conceitos básicos do ativo 3D

Na home page do aplicativo, selecione **Conceitos básicos** do ativo 3D para explorar como otimizar os ativos 3D para atender ao requisito de taxa de quadros, mantendo a alta fidelidade visual.

Exploraremos os seguintes conceitos principais:

>[!div class = "checklist"]
> * [Contagem de triângulos](#triangle-count).
> * [O sombreador passa](#shader-passes).
> * [Desenhar chama](#draw-calls).
> * [Finale](#finale).

### <a name="triangle-count"></a>Contagem de triângulos

Selecione o número e a complexidade dos modelos de bicicleta para experimentar a diferença visual com base em FPS.

![Escolha opções de contagem de triângulos diferentes para ver os efeitos na taxa de quadros.](images\qf-3d-asset-visible-triangles.jpg)

Para obter mais informações, consulte [processo de criação de ativos](/windows/mixed-reality/design/asset-creation-process).

### <a name="shader-passes"></a>Passagens do sombreador

Selecione o número de bicicletas e opções de sombreador diferentes para experimentar a diferença visual com base em FPS.

![Escolha diferentes opções de sombreador para ver os efeitos na taxa de quadros.](images\qf-3d-asset-shader-complexity.jpg)

Para obter mais informações, consulte [Sombreador padrão do MRTK.](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

### <a name="draw-calls"></a>Desenhar chamadas

As chamadas de desenho são chamadas com uso intensivo de recursos para a placa gráfica.  Nesta parte do aplicativo, experimente a diferença visual em primeira mão, pois o número de chamadas de desenho afeta o FPS.

![As chamadas de desenho devem ser otimizadas para melhorar o desempenho.](images\qf-3d-asset-draw-calls.jpg)

Confira Recomendações de desempenho [da CPU para GPU.](/windows/mixed-reality/develop/unity/performance-recommendations-for-unity#cpu-to-gpu-performance-recommendations)

### <a name="finale"></a>Final

Aqui, podemos explorar quantas bicicletas totalmente otimizadas podem ser exibidas e o nível de fidelidade possível, considerando as técnicas de otimização.

![Técnicas de otimização usadas.](images\qf-3d-asset-finale.jpg)

## <a name="next-steps"></a>Próximas etapas

Explore outros cenários de exemplo de realidade misturada:

   > [!div class="nextstepaction"]
   > [Exemplos e aplicativos de recursos](../features-and-samples.md)