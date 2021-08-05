---
title: Diretrizes de design do inicializador de aplicativos 3D
description: Um iniciador de aplicativo 3D é um objeto "físico" na casa de realidade misturada do usuário que pode selecionar para iniciar um aplicativo.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, iniciador de aplicativos 3d, headsets de imersão, cubos ao vivo, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, UWP, Win32, iluminação, cor
ms.openlocfilehash: 2d93930d63b251aa91d77c96b4d5250baba54c51de50388f690b3588b1580761
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188466"
---
# <a name="3d-app-launcher-design-guidance"></a>Diretrizes de design do inicializador de aplicativos 3D

quando você coloca em um headset de Windows Mixed Reality de imersão (VR), entra na página inicial do Windows Mixed Reality. A página inicial é visualizada como uma casa em uma Cliff cercada por montanhas e água, mas você pode [escolher outros ambientes e até mesmo criar seus próprios](../design/add-custom-home-environments.md). No espaço da Home, um usuário é livre para organizar e organizar os objetos 3D e os aplicativos que eles se preocupam de qualquer forma que desejarem. Um **iniciador de aplicativo 3D** é um objeto "físico" na casa de realidade misturada do usuário que pode selecionar para iniciar um aplicativo.

![Exemplo: inicializador de aplicativo 3D de pássaro flutuante](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Exemplo de inicializador de aplicativo 3D de pássaro flutuante (aplicativo fictício)*

## <a name="3d-app-launcher-creation-process"></a>processo de criação do inicializador de aplicativo 3D

Há três etapas para criar um iniciador de aplicativo 3D:

1. Design e conceito (este artigo)
2. [Modelagem e exportação](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrando-o em seu aplicativo:
    * [Aplicativos UWP](implementing-3d-app-launchers.md)
    * [Aplicativos Win32](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Conceitos de design

### <a name="fantastic-yet-familiar"></a>Fantástico ainda familiar

o ambiente de Windows Mixed Reality no qual o iniciador de aplicativo reside é parte familiar, parte fantástica/sci-fi. Os melhores iniciadores seguem as regras deste mundo. Imagine como você pode pegar um objeto familiar e representativo de seu aplicativo, mas dobre algumas das regras da realidade real. A mágica será resultado.

### <a name="intuitive"></a>Simples

Ao examinar seu iniciador de aplicativo, sua finalidade-para iniciar seu aplicativo-deve ser óbvio e não deve causar qualquer confusão. Por exemplo, certifique-se de que o iniciador é um representante óbvio o suficiente do seu aplicativo que não será confundido por uma parte do décor na casa Cliff. Seu iniciador de aplicativo deve convidar pessoas para tocar/selecionar.

![Exemplo: inicializador de aplicativo 3D de anotação atualizada](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Observação de novo exemplo de inicializador de aplicativo 3D (aplicativo fictício)*

### <a name="home-scale"></a>Escala inicial

os iniciadores de aplicativos 3D residem na casa Cliff e seu tamanho padrão deve fazer sentido com os outros objetos "físicos" no espaço. Se você colocar seu iniciador ao lado de, digamos, uma planta de casa ou em algumas mobílias, deverá sentir em casa, com tamanho próprio. Um bom ponto de partida é ver como ele analisa 30 centímetros cúbicos, mas lembre-se de que os usuários podem escalá-los ou diminuí-los se quiserem.

### <a name="own-able"></a>Com capacidade própria

O inicializador de aplicativos deve se parecer com um objeto que uma pessoa estaria empolgando em seu espaço. Eles estarão praticamente circundando-se com essas coisas, portanto, o iniciador deve se sentir como algo que o usuário pensava o suficiente para buscar e manter o próximo.

![Exemplo: inicializador de aplicativo 3D Astro Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Exemplo de inicializador de aplicativo 3D Astro Warp (aplicativo fictício)*

### <a name="recognizable"></a>Reconhecível

Seu iniciador de aplicativo 3D deve expressar instantaneamente "a marca do aplicativo" para as pessoas que a veem. Se você tiver um caractere de estrela ou um objeto especialmente identificável em seu aplicativo, é recomendável usá-lo como uma parte significativa do design. Em um mundo de realidade misturada, um objeto desenhará mais interesse dos usuários do que apenas um logotipo. Os objetos reconhecíveis comunicam a marca de forma rápida e clara.

### <a name="volumetric"></a>Volumétricos

Seu aplicativo merece mais do que apenas colocar seu logotipo em um plano plano e chamá-lo por dia. Seu iniciador deve parecer um objeto físico empolgante e 3D no espaço do usuário. Uma boa abordagem é imaginar que seu aplicativo terá um balão no dia de graças do Macy liderança. Pergunte-se, o que realmente seria Wow quando ele chegou à rua? O que pareceria muito com todos os ângulos de exibição?

:::row:::
    :::column:::
        ![Somente ](images/20171016-140436-mixedreality-640px.jpg) *logotipo* do logotipo
    :::column-end:::
    :::column:::
        ![Mais reconhecível com um caractere ](images/20171016-140557-mixedreality-640px.jpg) *mais reconhecível com um caractere*
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Abordagem simples, não surpreendentemente, sente-se uma ](images/20171016-155101-mixedreality-640px.jpg) *abordagem simples e simples, não surpreendentemente, parece simples*
    :::column-end:::
    :::column:::
        ![A abordagem de volumétricos melhor apresenta melhor a ](images/20171016-161407-mixedreality-640px.jpg) *abordagem de volumétricos* do seu aplicativo
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a>Dicas para bons modelos 3d

* Ao planejar dimensões para seu inicializador de aplicativo, tenha em seguida um cubo de 30 cm. Portanto, uma proporção de tamanho de 1:1:1.
* Os modelos devem estar abaixo de 10.000 polígonos. [Saiba mais sobre contagens de triângulos e níveis de detalhes (LODs)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Teste em um headset de imersão.
* Crie detalhes na geometria do modelo quando possível – não confie em texturas para obter detalhes.
* Crie uma geometria de "água justa" fechada. Não há buracos que não sejam modelados.
* Use materiais naturais em seu objeto. Imagine criá-lo no mundo real.
* Certifique-se de que seu modelo Leia bem em diferentes distâncias e tamanhos.
* Quando seu modelo estiver pronto para começar, leia as [diretrizes de exportação de ativos](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).

![Modelo com detalhes sutis na textura](images/20171013-143334-mixedreality-640px.jpg)<br>
*Modelo com detalhes sutis na textura*

### <a name="what-to-avoid"></a>O que evitar

* Não use detalhes de alto contraste ou padrões e texturas pequenos e ocupados.
* Não use a geometria fina – ela não funciona bem em uma distância e terá alias incorreto.
* Não deixe que partes do seu modelo estendam muito além da proporção de tamanho de 1:1:1. Ele criará problemas de dimensionamento.

![Evitar padrões de alto contraste e pequenos ocupados](images/20171013-143603-mixedreality-640px.jpg)<br>
*Evitar padrões de alto contraste, pequenos e ocupados*

## <a name="how-to-handle-type"></a>Como tratar o tipo

* Recomendamos que seu tipo ocupe cerca de 1/3 de seu iniciador de aplicativo (ou mais). O tipo é o principal coisa que dá às pessoas uma ideia de que seu iniciador é, na verdade, um iniciador, portanto, é bom se for substancial.
* Evite fazer o tipo superlargo – tente mantê-lo dentro dos limites das dimensões principais de iniciadores de aplicativo (mais ou menos).
* O tipo flat pode funcionar, mas pode ser difícil de Exibir de determinados ângulos e em determinados ambientes. Você pode considerar colocá-lo em um objeto sólido ou fazer um pano por trás dele para ajudar com isso.
* A adição de dimensão ao seu tipo é agradável em 3D. Sombreamento dos lados do tipo uma cor diferente e mais escura pode ajudar na legibilidade.

:::row:::
    :::column:::
        ![Um tipo simples sem um pano de fundo pode ser difícil de ser exibido a partir de determinados ângulos e, em determinados ambientes, ](images/flattype-640px.png) *o tipo simples sem uma tela de fundo pode ser difícil de Exibir de determinados ângulos e em determinados ambientes*
    :::column-end:::
    :::column:::
        ![O tipo com um pano de fundo interno pode funcionar bem ](images/flattypeandbkg-640px.png) *com um pano de fundo interno que pode funcionar bem*
    :::column-end:::
    :::column:::
        ![O tipo de extrusão pode funcionar bem se você Sombrear os lados ](images/20171016-160221-mixedreality-640px.jpg) *tipo de extrusão pode funcionar bem se você Sombrear os lados*
    :::column-end:::
:::row-end:::

**Digitar cores que funcionam**

* Branca
* Preto
* Cor semisaturada brilhante

![Digite as cores que funcionam.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Digitar cores que funcionam*

### <a name="colors-to-avoid"></a>Cores a serem evitadas

As cores de tipo que causam problemas incluem:

* Tons médios
* Cinza
* Cores sobresaturadas ou cores dessaturadas

![Digite as cores que causam problemas.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Digitar cores que causam problemas*

## <a name="lighting"></a>Iluminação

A iluminação para o launcher do aplicativo vem do ambiente Casa no Penhasco aplicativo. Certifique-se de testar o launcher em vários locais em toda a casa para que ele tenha uma boa aparência na luz e nas sombras. A boa notícia é que, se você seguiu as outras diretrizes de design neste documento, o launcher deve estar em boa forma para a maioria das iluminação no Casa no Penhasco.

Bons locais para testar a aparência do seu launcher nas várias luzes no ambiente são o Studio, a Sala de Mídia, em qualquer lugar fora e no Back Patio (a área concreta com a casa). Outro bom teste é colocá-lo na metade da luz e meia sombra e ver a aparência dele.

![Certifique-se de que o launcher tenha uma boa aparência tanto na luz quanto nas sombras.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Certifique-se de que o launcher tenha uma boa aparência tanto na luz quanto nas sombras*

## <a name="texturing"></a>Texturização

### <a name="authoring-your-textures"></a>Como autor de suas texturas

O formato final do seu launcher de aplicativo 3D será um arquivo .glb, que é feito usando o pipeline PBR (Renderização Baseada Fisicamente). Esse pode ser um processo complicado – agora é um bom momento para empregar um artista técnico, caso ainda não tenha feito isso. Se você for um diY-er, aproveitar o tempo para pesquisar e aprender a terminologia de [PBR](https://wiki.polycount.com/wiki/PBR) e o que está acontecendo nos fundos antes de começar ajudará a evitar erros comuns. 

![Exemplo: novo aplicativo de observação](images/pbr-freshnote1-640px-500px.png)<br>
*Exemplo de iniciador de aplicativo 3D da Nova Observação (aplicativo fictício)*

### <a name="recommended-authoring-tool"></a>Ferramenta de autor recomendada

É recomendável [usar o Decodados](https://www.allegorithmic.com/products/substance-painter) por Allegorithmic para a autor do arquivo final. Se você não estiver familiarizado com a adoção de sombreadores PBR em Ressalvação de Cinzas, aqui está um [tutorial.](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)

(Como alternativa, [3D-Seletor,](https://3dcoat.com/home/) [Quixel Suite 2](https://quixel.se/suite2/)ou [Marmoset Toolbag](https://www.marmoset.co/toolbag/) também funcionaria se você estiver mais familiarizado com um deles.)

### <a name="best-practices"></a>Práticas recomendadas

* Se o objeto do launcher do aplicativo foi autor para PBR, deve ser simples convertê-lo para o ambiente Casa no Penhasco aplicativo.
* Nosso sombreador está esperando um fluxo de trabalho metal/aproximação – o sombreador do Unreal PBR é um facsimile próximo.
* Ao exportar suas texturas, tenha em mente os [tamanhos de textura recomendados.](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines)
* Certifique-se de criar seus objetos para iluminação em tempo real— isso significa:
  * Evitar sombras assadas – ou sombras pintadas
  * Evitar iluminação assada nas texturas
  * Use um dos pacotes de autor do material PBR para obter os mapas corretos gerados para nosso sombreador

## <a name="see-also"></a>Consulte também

* [Criar modelos 3D para uso na casa de realidade misturada](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementar inicializadores de aplicativos 3D (aplicativos UWP)](implementing-3d-app-launchers.md)
* [Implementar inicializadores de aplicativos 3D (aplicativos Win32)](implementing-3d-app-launchers-win32.md)
