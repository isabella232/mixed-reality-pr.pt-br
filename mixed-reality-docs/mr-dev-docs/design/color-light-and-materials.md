---
title: Cor, luz e materiais
description: A criação de conteúdo para realidade misturada requer uma consideração cuidadosa de cor, iluminação e materiais para todos os ativos visuais.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, cor, luz, materiais, headset de realidade misturada, headset da realidade mista do Windows, headset da realidade virtual, HoloLens, MRTK, kit de ferramentas da realidade misturada
ms.openlocfilehash: 5d99941f068e808ba14d97084ef840a66aded2a9
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848061"
---
# <a name="color-light-and-materials"></a>Cor, luz e materiais

![Cor, luz e materiais](images/RemoteRendering.jpg)

A criação de conteúdo para realidade misturada requer uma consideração cuidadosa de cor, iluminação e materiais para todos os seus ativos virtuais. As finalidades estética podem incluir o uso de luz e material para definir o tom de um ambiente de imersão, enquanto a finalidade funcional pode incluir cores surpreendentes para alertar os usuários de uma ação iminente. Cada uma dessas decisões deve ser avaliada em relação às oportunidades e restrições do dispositivo de destino de sua experiência.

Veja abaixo as diretrizes específicas para renderizar ativos em headsets de imersão e Holographic. Muitos deles estão fortemente ligados a outras áreas técnicas e uma lista de assuntos relacionados pode ser encontrada na seção [Consulte também](color-light-and-materials.md#see-also) no final deste artigo.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Renderização em dispositivos de imersão versus Holographic

O conteúdo renderizado em headsets de imersão aparecerá visualmente diferente quando comparado ao conteúdo renderizado em headsets Holographic. Embora os headsets de imersão geralmente processem o conteúdo como você esperaria em uma tela 2D, os headsets Holographic como o HoloLens usam a seqüência de cores, consulte o RGB é exibido para renderizar hologramas.

Sempre Reserve um tempo para testar suas experiências de Holographic em um headset Holographic. A aparência do conteúdo, mesmo que seja criado especificamente para dispositivos Holographic, será diferente, como visto nos monitores secundários, instantâneos e na exibição do Spectator. Lembre-se de acompanhar experiências com um dispositivo, testar a iluminação de hologramas e observar de todos os lados (bem como de acima e abaixo) como seu conteúdo é renderizado. Certifique-se de testar com um intervalo de configurações de brilho no dispositivo. É improvável que todos os usuários compartilhem um padrão presumido e um conjunto diversificado de condições de iluminação.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Conceitos básicos de renderização em dispositivos Holographic

* **Dispositivos Holographic têm exibições aditivas** – os hologramas são criados com a adição de luz à luz do mundo real – o branco aparecerá com brilho, enquanto preto aparecerá transparente.

* **O impacto das cores varia de acordo com o ambiente do usuário** – há muitas condições de iluminação diferentes na sala do usuário. Crie conteúdo com níveis apropriados de contraste para ajudar com a clareza.

* **Evite a iluminação dinâmica** – os hologramas que são acesos uniformemente em experiências de Holographic são os mais eficientes. Usando a luminosidade avançada, a iluminação dinâmica provavelmente excederá os recursos de dispositivos móveis. Quando a iluminação dinâmica é necessária, é recomendável usar o [sombreador standard do kit de ferramentas da realidade misturada](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md). 

## <a name="designing-with-color"></a>Criando com cor

Devido à natureza de exibições aditivas, determinadas cores podem aparecer diferentes em exibições de Holographic. Algumas cores serão exibidas em ambientes de iluminação, enquanto outras aparecerão menos impactantes. As cores legais tendem a receder em segundo plano enquanto cores quentes saltam para o primeiro plano. Considere esses fatores à medida que explorar a cor em suas experiências:

* **Renderizando cores claras** -branco parece brilhante e deve ser usado com moderação. Na maioria dos casos, considere um valor branco em volta de R 235 G 235 B 235. Grandes áreas brilhantes podem causar discomfort do usuário. Para a placa traseira da janela da interface do usuário, é recomendável usar cores escuras.

* **Renderizando cores escuras** – devido à natureza de exibições aditivas, as cores escuras aparecem transparentes. Um objeto preto sólido não aparecerá de forma diferente do mundo real. Consulte canal alfa abaixo. Para dar a aparência de "preto", experimente um valor RGB cinza muito escuro, como 16, 16, 16.

* **Uniformidade de cores** -normalmente, os hologramas são renderizados com brilho suficiente para que mantenham a uniformidade de cores, seja qual for o plano de fundo. Áreas grandes podem se tornar blotchy. Evite grandes regiões de cores brilhantes e sólidas.

* Os benefícios da **gama** -HoloLens de uma "ampla gama" de cores, conceitualmente semelhante ao Adobe RGB. Como resultado, algumas cores podem mostrar qualidades e representação diferentes no dispositivo.

* **Gama** -o brilho e o contraste da imagem renderizada irão variar entre os dispositivos de imersão e Holographic. Essas diferenças de dispositivo geralmente parecem tornar áreas escuras de cores e sombras, mais ou menos brilhantes.

* **Separação de cores** – também chamada de "cor divisão" ou "borda colorida", a separação de cores geralmente ocorre com o movimento de holograma (incluindo o cursor) quando um usuário rastreia objetos com seus olhos.

## <a name="technical-considerations"></a>Considerações técnicas

* **Alias** -seja considerem de alias, denteado ou "etapas da escada", em que a borda da geometria de um holograma atende ao mundo real. O uso de texturas com alto detalhe pode aggravate esse efeito. As texturas devem ser mapeadas e habilitadas para filtragem. Considere desbotar as bordas de hologramas ou adicionar uma textura que cria uma borda de borda preta em torno de objetos. Evite a geometria fina sempre que possível.

* **Canal alfa** -você deve limpar o canal alfa para totalmente transparente para todas as partes em que você não está renderizando um holograma. Deixar o alfa não definido leva a artefatos visuais ao tirar imagens/vídeos do dispositivo ou com a exibição Spectator.

* **Suavização de textura** -como a luz é aditiva nas exibições de Holographic, é melhor evitar grandes regiões de cores sólidas e brilhantes, pois elas geralmente não produzem o efeito visual pretendido.

## <a name="design-guidelines-for-holographic-display"></a>Diretrizes de design para a exibição do Holographic

![Oclusão de cor e mão](images/color_handocclusion.jpg)

Ao criar conteúdo para exibições do Holographic, há vários elementos que você precisa considerar para obter a melhor experiência. Visite a [tela criando conteúdo para Holographic](designing-content-for-holographic-display.md) para obter as diretrizes e recomendações.

## <a name="storytelling-with-light-and-color"></a>Narração com luz e cor

A luz e a cor podem ajudar a tornar seus hologramas mais naturalmente no ambiente de um usuário e oferecer orientação e ajuda para o usuário. Para experiências de Holographic, considere esses fatores ao explorar a iluminação e a cor:

:::row:::
    :::column:::
* **Vignetting** -um efeito ' Vignette ' para escurecer materiais pode ajudar a concentrar a atenção do usuário no centro do campo de exibição. Esse efeito escurece o material do holograma em algum raio do vetor olhar do usuário. Isso também é eficaz quando o usuário exibe os hologramas de um ângulo oblíquo ou glancing.

* **Ênfase** -desenhando a atenção para objetos ou pontos de interação por contraste com cores, brilho e iluminação. Para obter uma visão mais detalhada dos métodos de iluminação no narração, consulte [pixel Cinematography-uma abordagem de iluminação para gráficos de computador](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).<br>
        <br>
        *Imagem: uso de cor para mostrar ênfase para elementos narração, mostrados aqui em uma cena de [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*
    :::column-end:::
        :::column:::
        ![Uso de cor para mostrar ênfase para elementos narração, mostrados aqui em uma cena de fragmentos.](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a>Materiais

:::row:::
    :::column:::
Os materiais são elementos cruciais para fazer hologramas realistas. Ao fornecer as características visuais adequadas, você pode criar objetos Holographic atraentes que podem misturar bem com o ambiente físico. Os materiais também são importantes para fornecer comentários visuais para os vários tipos de interações de entrada do usuário.  

O [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece um sombreador padrão MRTK com várias opções de efeito visual que podem ser usadas para comentários visuais. Por exemplo, você pode usar a propriedade ' proximidade clara ' para fornecer um efeito de iluminação quando o dedo do usuário estiver se aproximando da superfície do objeto. Saiba mais sobre o [sombreador padrão do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)
    :::column-end:::
        :::column:::
    *Loop de vídeo: exemplo de comentários visuais com base na proximidade a uma caixa* 
     ![ delimitadora Comentário visual sobre a proximidade](images/HoloLens2_Proximity.gif)

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a>Consulte também
* [Criar conteúdo para exibição holográfica](designing-content-for-holographic-display.md)
* [Separação de cores](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [Hologramas](../discover/hologram.md)
* [Linguagem de design da Microsoft-cor](https://www.microsoft.com/design/color)
* [Plataforma Universal do Windows-cor](https://docs.microsoft.com/windows/uwp/style/color)
