---
title: Cor, luz e materiais
description: A criação de conteúdo para realidade misturada requer uma consideração cuidadosa de cores, iluminação e materiais para todos os ativos visuais.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, cor, luz, materiais, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Realidade Misturada Toolkit
ms.openlocfilehash: 50789faa44e6786c0d9fd0b146daa84f459df451bedc52f06073e742ea8064a0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219848"
---
# <a name="color-light-and-materials"></a>Cor, luz e materiais

![Cor, luz e materiais](images/RemoteRendering.jpg)

A criação de conteúdo para realidade misturada requer uma consideração cuidadosa da cor, da iluminação e dos materiais para todos os seus ativos virtuais. As finalidades funcionais podem incluir o uso de luz e material para definir o tom de um ambiente imersivo, enquanto as finalidades funcionais podem incluir o uso de cores impressionantes para alertar os usuários de uma ação pendente. Cada uma dessas decisões deve ser ponderada em relação às oportunidades e restrições do dispositivo de destino da sua experiência.

Abaixo estão diretrizes específicas para renderizar ativos em headsets imersivos e holográficos. Muitos deles estão intimamente vinculados a outras áreas técnicas e [](color-light-and-materials.md#see-also) uma lista de assuntos relacionados pode ser encontrada na seção Ver também no final deste artigo.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Renderização em dispositivos imersivos versus holográficos

O conteúdo renderizado em headsets imersivos aparecerá visualmente diferente quando comparado ao conteúdo renderizado em headsets holográficos. Embora os headsets imersivos geralmente renderizarem conteúdo da mesma forma que você esperaria em uma tela 2D, headsets holográficos como HoloLens usam exibições RGB sequenciais de cores e verão para renderizar hologramas.

Sempre leve tempo para testar suas experiências holográficas em um headset holográfico. A aparência do conteúdo, mesmo que ele seja criado especificamente para dispositivos holográficos, será diferente como visto em monitores secundários, instantâneos e na exibição de espectador. Lembre-se de dar uma olhada nas experiências com um dispositivo, testando a iluminação dos hologramas e observando de todos os lados (bem como acima e abaixo) como o conteúdo é renderizar. Certifique-se de testar com uma variedade de configurações de brilho no dispositivo. É improvável que todos os usuários compartilhem um padrão assumido e um conjunto diversificado de condições de iluminação.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Conceitos básicos da renderização em dispositivos holográficos

* **Os dispositivos holográficos** têm exibições aditivas – Hologramas são criados adicionando luz à luz do mundo real – o branco aparecerá brilhante, enquanto preto aparecerá transparente.

* **O impacto das cores varia de** acordo com o ambiente do usuário – há muitas condições de iluminação diversificadas no quarto do usuário. Crie conteúdo com níveis apropriados de contraste para ajudar com clareza.

* **Evite iluminação dinâmica** – Hologramas que são uniformemente acesos em experiências holográficas são as mais eficientes. O uso da iluminação dinâmica avançada provavelmente excederá os recursos dos dispositivos móveis. Quando a iluminação dinâmica é necessária, é recomendável usar o sombreador [de Realidade Misturada Toolkit Standard.](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) 

## <a name="designing-with-color"></a>Projetando com cor

Devido à natureza das exibições aditivas, determinadas cores podem aparecer diferentes em exibições holográficas. Algumas cores serão exibidas em ambientes de iluminação, enquanto outras aparecerão como menos impactante. As cores es frias tendem a cair na plano de fundo enquanto as cores quentes vão para o primeiro plano. Considere esses fatores conforme você explora a cor em suas experiências:

* **Renderizar cores claras** – branco aparece brilhante e deve ser usado com moderação. Para a maioria dos casos, considere um valor em branco em torno de R 235 G 235 B 235. Grandes áreas brilhante podem causar o mal-estar do usuário. Para o backplate da janela da interface do usuário, é recomendável usar cores escuras.

* **Renderização de cores** escuras – devido à natureza das exibições aditivas, as cores escuras aparecem transparentes. Um objeto preto sólido não será diferente do mundo real. Confira Canal alfa abaixo. Para dar a aparência de "preto", tente um valor RGB cinza muito escuro, como 16,16,16.

* **Uniformidade de cores** – normalmente os hologramas são renderizados com brilho suficiente para que mantenham a uniformidade de cores, seja qual for a tela de fundo. Áreas grandes podem se tornar blotchy. Evite grandes regiões de cor brilhante e sólida.

* **Gamut** – HoloLens se beneficia de uma "ampla gama" de cores, conceitualmente semelhante ao Adobe RGB. Como resultado, algumas cores podem mostrar diferentes qualidades e representação no dispositivo.

* **Gama** – o brilho e o contraste da imagem renderizada variam entre dispositivos imersivos e holográficos. Essas diferenças de dispositivo geralmente parecem tornar áreas escuras de cores e sombras, mais ou menos brilhante.

* **Separação** de cores – também chamada de "color quedas" ou "color fringing", a separação de cores geralmente ocorre com a movimentação de hologramas (incluindo cursor) quando um usuário rastreia objetos com os olhos.

## <a name="technical-considerations"></a>Considerações técnicas

* **Aliasing** – seja considerado o alias, as "etapas de alias" ou "etapas irregulares" em que a borda da geometria de um holograma atende ao mundo real. O uso de texturas com detalhes altos pode levar a esse efeito. As texturas devem ser mapeadas e a filtragem habilitada. Considere esbotar as bordas dos hologramas ou adicionar uma textura que cria uma borda preta ao redor de objetos. Evite geometria fina sempre que possível.

* **Canal alfa** – você deve limpar seu canal alfa para ser totalmente transparente para todas as partes em que não estiver renderizar um holograma. Deixar o alfa indefinido leva a artefatos visuais ao tirar imagens/vídeos do dispositivo ou com o Modo de Exibição de Espectador.

* **Suavização de** textura – como a luz é aditiva em exibições holográficas, é melhor evitar grandes regiões de cor brilhante e sólida, pois elas geralmente não produzem o efeito visual pretendido.

## <a name="design-guidelines-for-holographic-display"></a>Diretrizes de design para exibição holográfica

![Oclusão de cor e mão](images/color_handocclusion.jpg)

Ao projetar conteúdo para exibições holográficas, há vários elementos que você precisa considerar para obter a melhor experiência. Visite [Projetando conteúdo para exibição holográfica](designing-content-for-holographic-display.md) para ver as diretrizes e recomendações.

## <a name="storytelling-with-light-and-color"></a>Storytelling com luz e cor

A luz e a cor podem ajudar a fazer com que seus hologramas apareçam mais naturalmente no ambiente de um usuário e ofereçam orientação e ajuda para o usuário. Para experiências holográficas, considere esses fatores conforme você explora a iluminação e a cor:

:::row:::
    :::column:::
* **Vitting –** um efeito "vigette" para materiais mais escuros pode ajudar a concentrar a atenção do usuário no centro do campo de exibição. Esse efeito escurece o material do holograma em algum raio do vetor de olhar do usuário. Isso também é eficaz quando o usuário visualiza hologramas de um ângulo oblíqua ou de deslutamento.

* **Ênfase** – chama a atenção para objetos ou pontos de interação contrastando cores, brilho e iluminação. Para obter uma análise mais detalhada dos métodos de iluminação em storytelling, consulte [Pixel Filmetography – A Lighting Approach for Computer Graphics](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).<br>
        <br>
        *Imagem: uso de cor para mostrar ênfase para elementos de storytelling, mostrados aqui em uma cena de [Fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*
    :::column-end:::
        :::column:::
        ![Uso de cor para mostrar ênfase para elementos de storytelling, mostrados aqui em uma cena de Fragmentos.](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a>Materiais

:::row:::
    :::column:::
Os materiais são elementos cruciais para tornar hologramas realistas. Ao fornecer características visuais adequadas, você pode fazer objetos holográficos atraentes que podem se combinar bem com o ambiente físico. Os materiais também são importantes para fornecer comentários visuais para os vários tipos de interações de entrada do usuário.  

[O MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece um Sombreador Padrão do MRTK com várias opções de efeito visual que podem ser usadas para comentários visuais. Por exemplo, você pode usar a propriedade 'Luz de Proximidade' para fornecer um efeito de iluminação quando o dedo do usuário estiver se aproximando da superfície do objeto. Saiba mais sobre o [Sombreador Padrão do MRTK](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)
    :::column-end:::
        :::column:::
    *Loop de vídeo: exemplo de comentários visuais com base na proximidade de uma caixa delimitada* 
     ![ Comentários visuais sobre proximidade da mão](images/HoloLens2_Proximity.gif)

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a>Confira também
* [Criar conteúdo para exibição holográfica](designing-content-for-holographic-display.md)
* [Separação de cores](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [Hologramas](../discover/hologram.md)
* [Linguagem de Design da Microsoft – cor](https://www.microsoft.com/design/color)
* [Plataforma de Windows Universal – cor](/windows/uwp/style/color)