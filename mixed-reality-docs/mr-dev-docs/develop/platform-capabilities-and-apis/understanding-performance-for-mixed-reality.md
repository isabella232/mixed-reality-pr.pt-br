---
title: Noções básicas sobre o desempenho da realidade misturada
description: Saiba mais sobre informações e detalhes avançados para analisar e otimizar Windows Mixed Reality desempenho do aplicativo.
author: hferrone
ms.author: v-hferrone
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, Desempenho, Otimização, CPU, GPU
ms.openlocfilehash: 394198011c40f0b90e2c5579f7e0ad8c4019b2a8cefcb1859c544afcbce47df6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193550"
---
# <a name="understanding-performance-for-mixed-reality"></a>Noções básicas sobre o desempenho da realidade misturada

Este artigo é uma introdução à compreensão da importância do desempenho para seu aplicativo de Realidade Misturada.  A experiência do usuário poderá ser bastante degradada se o aplicativo não for executado com uma taxa de quadros ideal. Hologramas será exibido instável e o acompanhamento de cabeça do ambiente será impreciso, levando a uma experiência ruim para o usuário. O desempenho deve ser considerado um recurso de primeira classe para o desenvolvimento de realidade misturada e não uma tarefa de polimento.

Recentemente, lançamos um aplicativo chamado Conceitos Básicos de Qualidade que aborda problemas comuns de desempenho, design e ambiente e soluções para HoloLens 2 aplicativos. Este aplicativo é uma ótima demonstração visual para o conteúdo a seguir.

> [!div class="nextstepaction"]
> [Baixar o aplicativo Conceitos Básicos de Qualidade](https://www.microsoft.com/en-us/p/quality-fundamentals/9mwz852q88fw)

Os valores de taxa de quadros de desempenho para cada plataforma de destino são listados abaixo.

| Plataforma | Taxa de quadros de destino |
|----------|-------------------|
| [HoloLens](/hololens/hololens1-hardware) | 60 FPS |
| [Windows Mixed Reality Ultra Pcs](../../discover/immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality Pcs](../../discover/immersive-headset-hardware-details.md) | 60 FPS |

A estrutura a seguir descreve as práticas recomendadas para atingir as taxas de quadros de destino. Recomendamos ler o [artigo recomendações de desempenho do Unity](../unity/performance-recommendations-for-unity.md) para dicas sobre como medir e melhorar a taxa de quadros no ambiente do Unity.

## <a name="understanding-performance-bottlenecks"></a>Noções básicas sobre gargalos de desempenho

Se seu aplicativo tiver uma taxa de quadros de baixo desempenho, a primeira etapa será analisar e entender onde seu aplicativo é computacionalmente intensivo. Há dois processadores principais responsáveis pelo trabalho para renderizar sua cena: a CPU e a GPU, cada um tratando diferentes aspectos de seu aplicativo de Realidade Misturada. Os três locais principais em que podem ocorrer gargalos são: 

1. **Thread do Aplicativo – CPU** -
    Responsável pela lógica do aplicativo, incluindo processamento de entrada, animações, física e outras lógicas de aplicativo.
2. **Renderizar Thread – CPU para GPU** – responsável por enviar suas chamadas de desenho para a GPU. Quando seu aplicativo deseja renderizar um objeto como um cubo ou modelo, esse thread envia uma solicitação para a GPU para fazer as operações.
3. **GPU** – geralmente lida com o pipeline de gráficos do seu aplicativo para transformar dados 3D (modelos, texturas e assim por diante) em pixels. Em última análise, ele produz uma imagem 2D para enviar para a tela do dispositivo.

![Tempo de vida de um quadro](images/lifetime-of-a-frame.png)

Em geral, HoloLens aplicativos serão vinculados à GPU, mas nem sempre. Use as ferramentas e as técnicas abaixo para entender onde seu aplicativo específico está gargalo.

## <a name="how-to-analyze-your-application"></a>Como analisar seu aplicativo

Há muitas ferramentas que permitem que você entenda o perfil de desempenho e possíveis gargalos em seu aplicativo de realidade misturada. 

Abaixo estão algumas ferramentas comuns para ajudá-lo a coletar informações de criação de perfil profundas para seu aplicativo:
- [Analisadores de desempenho de gráficos intel](https://software.intel.com/gpa)
- [Visual Studio Depurador de gráficos](/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Depurador de quadros do Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)
- [Unreal Insights](../unreal/unreal-insights.md)
- [Pix](https://devblogs.microsoft.com/pix/)
- [Pofiling de GPU no Unreal](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/GPU/index.html)

### <a name="how-to-profile-in-any-environment"></a>Como fazer o perfil em qualquer ambiente

Uma maneira de determinar se o aplicativo está vinculado à GPU ou à CPU é reduzir a resolução da saída de destino de renderização. Ao reduzir o número de pixels a calcular, você reduzirá a carga da GPU. O dispositivo será renderizar para uma textura menor e, em seguida, para cima para exibir sua imagem final.

Depois de reduzir a resolução de renderização, se:
1) A taxa de **quadros do aplicativo aumenta** e, em seguida, você provavelmente está vinculado à **GPU**
1) Taxa de quadros do **aplicativo inalterada** e, em seguida, você provavelmente será vinculado **à CPU**

>[!NOTE]
>O Unity fornece a capacidade de modificar facilmente a resolução de destino de renderização do aplicativo em runtime por meio da *[propriedade XRSettings.renderViewportScale.](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* A imagem final apresentada no dispositivo tem uma resolução fixa. A plataforma amostra a saída de resolução inferior para criar uma imagem de resolução mais alta para renderização em exibições. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Como melhorar seu aplicativo

### <a name="cpu-performance-recommendations"></a>Recomendações de desempenho da CPU

Geralmente, a maioria dos trabalhos em um aplicativo de realidade misturada na CPU envolve fazer a "simulação" da cena e processar a lógica do aplicativo. As seguintes áreas são direcionadas para otimização:

- Animações
- Física
- Alocações de memória
- Algoritmos complexos (ou seja, kinematics inversa, path-finding)

### <a name="gpu-performance-recommendations"></a>Recomendações de desempenho da GPU

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Noções básicas sobre largura de banda versus taxa de preenchimento
Ao renderizar um quadro na GPU, um aplicativo é limitado por largura de banda de memória ou taxa de preenchimento.

- **Largura de** banda de memória é a taxa de leituras e gravações que a GPU pode fazer da memória
    - Para identificar limitações de largura de banda, reduza a qualidade da textura e verifique se a taxa de quadros melhorou.
    - No Unity, altere **a Qualidade da** Textura em **Editar**  >  **Project Configurações**  >  **[Qualidade Configurações](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.
- **Taxa de** preenchimento refere-se aos pixels que podem ser desenhados por segundo pela GPU.
    - Para identificar as limitações da taxa de preenchimento, reduza a resolução de exibição e verifique se a taxa de quadros melhorou. 
    - No Unity, use a *[propriedade XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*

A largura de banda de memória geralmente envolve otimizações para:
1) Resoluções de textura inferiores
2) Usar menos texturas (normais, especular e assim por diante)

A taxa de preenchimento se concentra em reduzir o número de operações que precisam ser computadas para um pixel renderizado final, incluindo:
1) Número de objetos a renderizar/processar
2) Número de operações por sombreador
3) Número de estágios de GPU para o resultado final (sombreadores de geometria, efeitos pós-processamento e assim por diante)
4) Número de pixels a renderizar (resolução de exibição)

#### <a name="reduce-polygon-count"></a>Reduzir a contagem de polígonos

Contagens de polígonos mais altas resultam em mais operações para a GPU, portanto, reduzir o número de [polígonos](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) em sua cena reduz o tempo de renderização. Há outros fatores que tornam o sombreamento da geometria caro, mas a contagem de polígonos é a métrica mais simples para determinar quanto trabalho será preciso para renderizar uma cena.

#### <a name="limit-overdraw"></a>Limitar a sobreposição

O alto redesenho ocorre quando vários objetos são renderizados, mas não mostrados na tela, pois eles são ocultos por um objeto de oclusão. Imagine uma parede que tem objetos atrás dela. Toda a geometria seria processada para renderização, mas apenas a parede opaca precisa ser renderizada, o que resulta em operações desnecessárias.

#### <a name="shaders"></a>Sombreadores

Sombreadores são programas pequenos que são executados na GPU e fazem duas etapas importantes na renderização:
1) Determinando quais vértices devem ser desenhados e onde eles estão no espaço da tela (o sombreador de vértice)
    - O sombreador de vértice é executado por vértice para cada malha.
2) Determinando a cor de cada pixel (o sombreador de pixel)
    - O sombreador pixel é executado por pixel e renderizado pela geometria para a textura de renderização de destino.

Normalmente, os sombreadores fazem muitas transformações e cálculos de iluminação. Embora modelos de iluminação complexos, sombras e outras operações possam gerar resultados ótimos, eles também vêm com um preço. Reduzir o número de operações computadas em sombreadores pode reduzir consideravelmente o trabalho necessário para a GPU por quadro.

##### <a name="shader-coding-recommendations"></a>Recomendações de codificação do sombreador

- Usar filtragem bilinear sempre que possível
- Reorganizar expressões para usar intrínsecos de MAD para multiplicar e adicionar ao mesmo tempo
- Pré-calar o máximo possível na CPU e passar as constantes para o material
- **Favorecer operações de movimentação do sombreador de pixel para o sombreador de vértice**
    - Em geral, o número de vértices é muito menor do que o número de pixels (720p é de 921.600 pixels, 1080p é de 2.073.600 pixels e assim por diante)

#### <a name="remove-gpu-stages"></a>Remover estágios de GPU

Os efeitos de pós-processamento podem ser caros e aumentar a taxa de preenchimento do seu aplicativo, incluindo técnicas de suavização de alias, como a MSAA. em HoloLens, recomendamos evitar essas técnicas e outros estágios de sombreador, como geometry, envoltória e sombreadores de computação.

## <a name="memory-recommendations"></a>Recomendações de memória

As operações de alocação e desalocação de memória excessivas podem resultar em desempenho inconsistente, quadros congelados e outros comportamentos prejudiciais. É especialmente importante entender as considerações de memória ao desenvolver no Unity, pois o gerenciamento de memória é controlado pelo coletor de lixo.

#### <a name="object-pooling"></a>Pool de objetos

O pool de objetos é uma técnica popular para reduzir o custo de alocações e desalocações contínuas de objetos. Isso é feito pela alocação de um grande pool de objetos idênticos e pela reutilização das instâncias disponíveis inativas desse pool em vez da criação e da destruição constantes de objetos ao longo do tempo. Os pools de objetos são ótimos para componentes reutilizados que têm um tempo de vida variável durante um aplicativo.

## <a name="see-also"></a>Confira também
- [Recomendações de desempenho para Unity](../unity/performance-recommendations-for-unity.md)
- [Configurações recomendadas do Unity](../unity/recommended-settings-for-unity.md)
- [Recomendações de desempenho para o Unreal](../unreal/performance-recommendations-for-unreal.md)
- [Recomendações de material no Unreal](../unreal/unreal-materials.md)
- [Otimizar modelos 3D](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Práticas recomendadas para converter e otimizar modelos 3D em tempo real](/dynamics365/mixed-reality/import-tool/best-practices)
- [Diretrizes de desempenho para artistas e designers para não real](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/Guidelines/index.html)
- [Práticas recomendadas VR para inreal](https://docs.unrealengine.com/en-US/SharingAndReleasing/XRDevelopment/VR/DevelopVR/ContentSetup/index.html)