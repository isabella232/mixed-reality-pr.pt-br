---
title: Quadro holográfico
description: Saiba como os usuários veem o mundo da realidade misturada por meio do quadro Holographic e como criar melhor a experiência.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/25/2020
ms.topic: article
keywords: HoloLens, realidade misturada do Windows, quadro Holographic, campo de exibição, FOV, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada, interações, navegação, menu
ms.openlocfilehash: 5edab22751b9f2196f02a500279c4de385b57b5d
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196551"
---
# <a name="holographic-frame"></a>Quadro holográfico

Os usuários veem o mundo da realidade misturada por meio de um visor retangular equipado com o headset. No HoloLens, essa área retangular é chamada de quadro holográfico e permite que os usuários vejam o conteúdo digital sobreposto ao mundo real em relação a eles. A criação de experiências otimizadas para o quadro Holographic cria oportunidades, reduz os desafios e aprimora a experiência do usuário de aplicativos de realidade misturada.

## <a name="designing-for-content"></a>Design de conteúdo

Geralmente, os designers sentem a necessidade de limitar o escopo de sua experiência com o que o usuário pode ver imediatamente, sacrificando a escala do mundo real para garantir que o usuário veja sua totalidade. Os designers da mesma forma com aplicativos complexos geralmente sobrecarregam o quadro Holographic com o conteúdo, sobrecarregam os usuários com interações difíceis e interfaces congestionadas. Os designers que criam conteúdo de realidade misturada não precisam limitar a experiência diretamente na frente do usuário e em sua exibição imediata. Se o mundo físico em todo o usuário for mapeado, todas essas superfícies deverão ser consideradas uma tela potencial para conteúdo digital e interações. O design adequado de interações e conteúdo em uma experiência deve incentivar o usuário a se movimentar em seu espaço, direcionando sua atenção para o conteúdo principal e ajudando a ver todo o potencial da realidade misturada.

Talvez a técnica mais importante para incentivar o movimento e a exploração em um aplicativo seja **permitir que os usuários se ajustem à experiência**. Dê aos usuários um curto período de tempo de "tarefa livre" com o dispositivo. Isso pode ser tão simples quanto colocar um objeto no espaço e permitir que os usuários se movam por volta ou narrando uma introdução à experiência. Esse tempo deve ser livre de qualquer tarefa crítica ou de gestos específicos, como toque em ar. A finalidade é permitir que os usuários acomodem para exibir o conteúdo por meio do dispositivo antes de exigir interatividade ou progredir por meio do aplicativo. Isso é especialmente importante para os usuários pela primeira vez, pois eles se sentem à vontade para ver o conteúdo por meio do quadro holográfico e da natureza dos hologramas.

### <a name="large-objects"></a>Objetos grandes

Geralmente, o conteúdo que uma experiência chama, especialmente o conteúdo do mundo real, será maior do que o quadro holográfico. Objetos que normalmente não cabem no quadro holográfico devem ser reduzidos para se ajustarem quando são introduzidos pela primeira vez (em uma escala menor ou a uma distância). A chave é permitir **que os usuários vejam o tamanho completo** do objeto antes que a escala sobrecarregar o quadro. Por exemplo, um asiático holográfico deve ser exibido para caber totalmente dentro do quadro. Isso permite que os usuários formem uma compreensão espacial da forma geral do animal, antes de [dimensioná-lo](scale.md) para escala do mundo real perto do usuário.

Com o tamanho completo do objeto em mente, os usuários têm uma expectativa de onde se mover e procurar partes específicas desse objeto. Em uma experiência com conteúdo imersivo, ajuda a ter uma maneira de fazer referência ao tamanho total desse conteúdo. Por exemplo, se a experiência envolve a localização de um modelo de uma casa virtual, ajuda ter uma versão menor do tamanho da casa da casa para identificar onde eles estão dentro da casa.

Para ver um exemplo de design para objetos grandes, consulte [Cars Dem.](holographic-frame.md#volvo-cars)

### <a name="many-objects"></a>Muitos objetos

As experiências com muitos objetos ou componentes devem considerar o uso do espaço completo ao redor do usuário para evitar a desorganização do quadro holográfico diretamente na frente do usuário. É recomendável reduzir a introdução do conteúdo a uma experiência, especialmente com experiências que planejam servir muitos objetos ao usuário. A chave é permitir que os usuários entendam o **layout** de conteúdo na experiência, o que os ajuda a obter uma compreensão espacial do que está ao redor deles como atualizações de conteúdo.

Uma técnica para fazer isso é fornecer pontos persistentes (também conhecidos como pontos de referência) na experiência que ancora o conteúdo para o mundo real. Por exemplo, um ponto de referência pode ser um objeto físico no mundo real, como uma tabela em que o conteúdo digital aparece, ou um objeto digital, como um conjunto de telas digitais em que o conteúdo é exibido com frequência. Os objetos também podem ser colocados no periferia do quadro Holographic para incentivar o usuário a procurar o conteúdo da chave. A descoberta de conteúdo além do periferia pode ser auxiliada por [diretores de atenção](holographic-frame.md#attention-directors).

Colocar objetos no periferia pode encorajar os usuários a olhar para o lado e isso pode ser auxiliado por diretores de atenção, conforme descrito abaixo. Para obter mais informações sobre as considerações de quadro Holographic, consulte a documentação [confortável](comfort.md#holographic-frame-considerations) .

<br>

---

## <a name="interaction-considerations"></a>Considerações sobre interação

Assim como acontece com o conteúdo, as interações em uma experiência de realidade misturada não precisam ser limitadas ao que o usuário pode ver imediatamente. As interações podem ocorrer em qualquer lugar do espaço do mundo real em todo o usuário. Essas interações podem ajudar a incentivar os usuários a se movimentarem e explorarem experiências.

### <a name="attention-directors"></a>Diretores de atenção

Indicar pontos de interesse ou interações de chave pode ser crucial para progredir os usuários por meio de uma experiência. A atenção do usuário e a movimentação do quadro Holographic podem ser direcionadas de formas sutis ou pesadas. Lembre-se de direcionar os diretores de atenção com períodos de exploração gratuita em realidade misturada (especialmente no início de uma experiência) para evitar sobrecarregar o usuário. Em geral, há dois tipos de diretores de atenção:
* **Diretores visuais:** A maneira mais fácil de permitir que o usuário saiba que ele deve se mover em uma direção específica é fornecer uma indicação visual. Isso pode ser feito por meio de um efeito visual (por exemplo, um caminho que o usuário pode seguir visualmente para a próxima parte da experiência) ou até mesmo como setas direcionais simples. Qualquer indicador visual deve ser aterrado dentro do ambiente do usuário, não ' anexado ' ao quadro Holographic ou ao cursor.
* **Diretores de áudio:** o [som espacial](spatial-sound-design.md) pode fornecer uma maneira eficiente de estabelecer objetos em uma cena. Você pode alertar os usuários sobre objetos que entram em uma experiência ou direcionar a atenção para um ponto específico no espaço movendo a exibição do usuário para objetos-chave. O uso de diretores de áudio para orientar a atenção do usuário pode ser mais sutil e menos invasivo do que os diretores visuais. Em alguns casos, pode ser melhor começar com um diretor de áudio e passar para um diretor visual se o usuário não reconhecer a indicação. Os diretores de áudio também podem ser emparelhados com diretores visuais para maior ênfase.

### <a name="commanding-navigation-and-menus"></a>Comando, navegação e menus

As interfaces em experiências de realidade misturada são idealmente emparelhadas com o conteúdo digital que eles controlam. Dessa forma, menus 2D flutuantes gratuitos geralmente não são ideais para interação e podem ser difíceis para os usuários com muito cuidado dentro do quadro holográfico. Para experiências que exigem elementos de interface, como menus ou campos de texto, considere usar um método [tag-along](billboarding-and-tag-along.md) para seguir o quadro holográfico após um pequeno atraso. Evite bloquear o conteúdo para o quadro como uma exibição de cabeça para cima, pois isso pode ser confuso para o usuário e quebrar a noção de imersão para outros objetos digitais na cena.

Você também pode colocar elementos de interface diretamente no conteúdo específico que eles controlam, permitindo que as interações ocorram naturalmente em torno do espaço físico do usuário. Por exemplo, quebre um menu complexo em partes separadas, com cada botão ou grupo de controles anexado ao objeto específico que a interação afeta. Para levar esse conceito adiante, considere o uso de [objetos interajantes.](interactable-object.md)

### <a name="gaze-and-gaze-targeting"></a>Direcionamento de olhar e de olhar

O quadro holográfico apresenta uma ferramenta para o desenvolvedor disparar interações e avaliar onde a atenção do usuário está. [O](gaze-and-commit.md) olhar é uma das principais interações no [HoloLens,](interaction-fundamentals.md)em que o olhar pode ser emparelhado com [gestos](gaze-and-commit.md#composite-gestures) (como tocar no ar) ou voz [(permitindo](voice-input.md) interações mais curtas e naturais baseadas em voz). Assim, isso torna o quadro holográfico um espaço para observar o conteúdo digital e interagir com ele. Se a experiência chamar a interação com vários objetos em todo o espaço do usuário (por exemplo, várias seleções de objetos em todo o espaço do usuário com olhar + gesto), considere colocar esses objetos na exibição do usuário ou limitar a quantidade de movimento de cabeçalho necessário para promover o [conforto do usuário](comfort.md).

O olhar também pode ser usado para controlar a atenção do usuário por meio de uma experiência e ver quais objetos ou partes da cena o usuário pagou mais atenção. Isso pode ser usado especialmente para depurar uma experiência, permitindo que ferramentas analíticas como o calor vejam onde os usuários estão gastando mais tempo ou faltam determinados objetos ou interação. O acompanhamento de olhar também pode fornecer uma ferramenta poderosa para os facilitadores em experiências (consulte o exemplo de [cozinha do Lowe](holographic-frame.md#lowes-kitchen) ).

Se você gostaria de ver os conceitos de design de acompanhamento de cabeça e olho em ação, Confira nossa demonstração de vídeo **de acompanhamento de holograma e** acompanhamento de cabeça abaixo:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo foi tirado do aplicativo "criando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*

<br>

---

## <a name="performance"></a>Desempenho

O uso adequado do quadro Holographic é fundamental para as experiências de [qualidade de desempenho](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) . Um desafio comum (e usabilidade) é sobrecarregar o quadro do usuário com conteúdo digital, causando degradação do desempenho de renderização. Considere, em vez disso, usar o espaço completo em volta do usuário para organizar o conteúdo digital, usando as técnicas descritas acima, para diminuir a carga da renderização e garantir uma qualidade de exibição ideal.

O conteúdo digital dentro do quadro Holographic do HoloLens também pode ser emparelhado com o [plano de estabilização](../develop/platform-capabilities-and-apis/case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) para obter o desempenho ideal e a [estabilidade do holograma](../develop/platform-capabilities-and-apis/hologram-stability.md).

<br>

---

## <a name="examples"></a>Exemplos

### <a name="volvo-cars"></a>Carros Volvo

<iframe width="940" height="530" src="https://www.youtube.com/embed/DilzwF90vec" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Na experiência do showroom da Volvo carros, os clientes são convidados a aprender sobre os novos recursos de carros em uma experiência de HoloLens guiada por um associado Volvo. Volvo enfrentou um desafio com o quadro Holographic: um carro de tamanho completo é muito grande para ser colocado ao lado de um usuário. A solução era começar a experiência com um ponto de referência físico, uma tabela central na sala de show, com um modelo digital menor do carro colocado na parte superior da tabela. Isso garante que o usuário está vendo o carro completo quando ele é introduzido, permitindo uma noção de compreensão espacial quando o carro cresce para sua escala do mundo real posteriormente na experiência.

A experiência de Paulo também usa diretores visuais, criando um efeito visual longo do modelo de carro de pequena escala na tabela para uma parede na sala de show. Isso leva a um efeito de "janela mágica", mostrando a exibição completa do carro à distância, ilustrando mais recursos do carro em escala do mundo real. O movimento da cabeça é horizontal, sem nenhuma interação direta do usuário (em vez disso, coletando sinais visualmente e da narração da experiência pelo associado Deia).

<br>

---

### <a name="lowes-kitchen"></a>Cozinha do Lowe

Uma experiência de loja do Lowe convida os clientes para uma simulação em grande escala de uma cozinha para demonstrar várias oportunidades de remodelagem, como visto por meio do HoloLens. A cozinha na loja fornece um pano de fundo físico para objetos digitais, uma tela em branco de dispositivos, contratops e gabinetes para a experiência de realidade misturada se desenrolar.

As superfícies físicas atuam como pontos de referência estáticos para o usuário se basear na experiência, pois o associado de um Lowe orienta o usuário por diferentes opções de produto e termina. Dessa forma, o associado pode direcionar a atenção do usuário para o 'refrigerador' ou 'centro da cozinha' para demonstrar o conteúdo digital.

![Um associado do Lowe usa um tablet para orientar os clientes pela experiência do HoloLens.](images/loweskitchen-750px.jpg)<br>
*Um associado do Lowe usa um tablet para orientar os clientes pela experiência do HoloLens.*

A experiência do usuário é gerenciada, em parte, por uma experiência de tablet controlada pelo associado do Lowe. Parte da função do associado nesse caso também seria limitar o movimento excessivo da cabeça, direcionando sua atenção sem problemas entre os pontos de interesse na cozinha. A experiência do Tablet também fornece a associação do Lowe com os dados do olhar na forma de uma exibição calor da cozinha, ajudando a entender onde o usuário está acessando a pesquisa (por exemplo, em uma área específica do gabinete) para fornecê-las com mais precisão com as diretrizes de reforma.

Para obter uma análise mais profunda da experiência de cozinha do Lowe, consulte a [palestra da Microsoft em Ignite 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

<br>

---

### <a name="fragments"></a>Fragmentos

Nos fragmentos de jogos do HoloLens, a sala de vida é transformada em uma cena de crimes virtuais mostrando pistas e evidências, e uma sala de reunião virtual, em que você conversa com caracteres que ficam em suas cadeiras e fala sobre suas paredes.

![Os fragmentos foram projetados para ocorrer na casa de um usuário, com caracteres que interagem com objetos e superfícies do mundo real.](images/fragments-750px.jpg)<br>
*Os fragmentos foram projetados para ocorrer na casa de um usuário, com caracteres que interagem com objetos e superfícies do mundo real.*

Quando os usuários iniciam inicialmente a experiência, eles recebem um curto período de ajuste com pouca ou nenhuma interação. Em vez disso, eles são incentivados a examinar e se orientarem e garantem que a sala esteja mapeada corretamente para o conteúdo interativo do jogo.

Durante toda a experiência, os caracteres se tornam pontos focal e atuam como diretores visuais (movimentos de cabeçalho entre caracteres, voltando à aparência ou ao gesto para áreas de interesse). O jogo também se baseia em indicações visuais mais proeminentes quando um usuário leva muito tempo para localizar um objeto ou evento e faz uso intenso de áudio espacial (especialmente com caracteres vozes ao inserir uma cena).

<br>

---

### <a name="destination-mars"></a>Destino: Mars

Na experiência de destino: Mars em destaque no [centro de espaço Kennedy da NASA](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/), os visitantes foram convidados em uma corrida de imersão para a superfície do Mars, guiado pela representação virtual de lendárias Astronaut de repercussão Aldrin.

![Um Aldrin de repercussão virtual se torna o ponto focal para os usuários no destino: Mars.](images/destinationmars-750px.png)<br>
*Um Aldrin de repercussão virtual se torna o ponto focal para os usuários no destino: Mars.*

Como uma experiência imersiva, esses usuários foram incentivados a dar uma olhada, movendo a cabeça em todas as direções para ver a paisagem virtual de Paisagem de Paisagem. Embora para garantir o conforto dos usuários, a narração e a presença virtual de Buzz Aldrin proporcionam um ponto focal em toda a experiência. Essa gravação virtual do Buzz (criada pela [Captura de Realidade Misturada Estúdios](https://www.microsoft.com/mixed-reality/capture-studios)da Microsoft) em tamanho real e humano, no canto da sala, permitindo que os usuários o vejam em uma exibição quase completa. A narração de Paulo levou os usuários a se concentrarem em diferentes pontos no ambiente (por exemplo, um conjunto de rochas Demão no chão ou uma cadeia de rochas à distância) com alterações de cena ou objetos específicos introduzidos por ele.

![Os narradores virtuais se voltarão para seguir o movimento de um usuário, criando um ponto focal poderoso em toda a experiência.](images/gazereset-750px.png)<br>
*Os narradores virtuais se voltarão para seguir o movimento de um usuário, criando um ponto focal poderoso em toda a experiência.*

A representação realista do Buzz forneceu um ponto focal poderoso, completo com técnicas sutis para transformar o Buzz em direção ao usuário para se sentir como se ele estava lá, falando com você. À medida que o usuário se move sobre a experiência, o Buzz vai mudar para você para um limite antes de retornar para um estado neutro se o usuário se mover muito além de sua periférico. Se o usuário olhar completamente do Buzz (por exemplo, para ver algo em outro lugar na cena) e voltar para o Buzz, a posição direcional do narrador se concentrará novamente no usuário. Técnicas como essa fornecem uma poderosa noção de imersão e criam um ponto focal dentro do quadro holográfico, reduzindo o movimento excessivo da cabeça e promovendo o conforto [do usuário.](comfort.md)

## <a name="see-also"></a>Confira também
* [Interações instinctuais](interaction-fundamentals.md)
* [Conforto](comfort.md)
* [Escala](scale.md)
* [Focar com a cabeça e esperar](gaze-and-dwell.md)
* [Estabilidade do holograma](../develop/platform-capabilities-and-apis/hologram-stability.md)
