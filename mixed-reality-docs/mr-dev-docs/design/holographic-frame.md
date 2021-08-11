---
title: Quadro holográfico
description: Saiba como os usuários veem o mundo da realidade misturada por meio do quadro Holographic e como criar melhor a experiência.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/25/2020
ms.topic: article
keywords: HoloLens, Windows Mixed Reality, quadro holographic, campo de exibição, FOV, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, realidade misturada Toolkit, interações, navegação, menu
ms.openlocfilehash: be24f2b583541e6ed0adff25b3d8edd6c3fe5285aea93d0a4d6df8ee61e5c070
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226368"
---
# <a name="holographic-frame"></a>Quadro holográfico

Os usuários veem o mundo da realidade misturada por meio de um visor retangular equipado com o headset. No HoloLens, essa área retangular é chamada de quadro holográfico e permite que os usuários vejam o conteúdo digital sobreposto ao mundo real em relação a eles. A criação de experiências otimizadas para o quadro Holographic cria oportunidades, reduz os desafios e aprimora a experiência do usuário de aplicativos de realidade misturada.

## <a name="designing-for-content"></a>Design de conteúdo

Geralmente, os designers sentem a necessidade de limitar o escopo de sua experiência com o que o usuário pode ver imediatamente, sacrificando a escala do mundo real para garantir que o usuário veja sua totalidade. Os designers da mesma forma com aplicativos complexos geralmente sobrecarregam o quadro Holographic com o conteúdo, sobrecarregam os usuários com interações difíceis e interfaces congestionadas. Os designers que criam conteúdo de realidade misturada não precisam limitar a experiência diretamente na frente do usuário e em sua exibição imediata. Se o mundo físico em todo o usuário for mapeado, todas essas superfícies deverão ser consideradas uma tela potencial para conteúdo digital e interações. O design adequado de interações e conteúdo em uma experiência deve incentivar o usuário a se movimentar em seu espaço, direcionando sua atenção para o conteúdo principal e ajudando a ver todo o potencial da realidade misturada.

Talvez a técnica mais importante para incentivar o movimento e a exploração em um aplicativo seja **permitir que os usuários se ajustem à experiência**. Dê aos usuários um curto período de tempo de "tarefa livre" com o dispositivo. Isso pode ser tão simples quanto colocar um objeto no espaço e permitir que os usuários se movam por volta ou narrando uma introdução à experiência. Esse tempo deve ser livre de qualquer tarefa crítica ou de gestos específicos, como toque em ar. A finalidade é permitir que os usuários acomodem para exibir o conteúdo por meio do dispositivo antes de exigir interatividade ou progredir por meio do aplicativo. Isso é especialmente importante para usuários de primeira hora à medida que se sente confortável ao ver o conteúdo por meio do quadro Holographic e a natureza dos hologramas.

### <a name="large-objects"></a>Objetos grandes

Geralmente, o conteúdo que uma experiência chama, especialmente o conteúdo real, será maior do que o quadro Holographic. Os objetos que normalmente não se ajustam no quadro Holographic devem ser reduzidos quando são introduzidos pela primeira vez (em uma escala menor ou em uma distância). A chave é **permitir que os usuários vejam o tamanho total do objeto** antes que a escala sobrecarregue o quadro. Por exemplo, um elefante Holographic deve ser exibido para se ajustar totalmente dentro do quadro. Isso permite que os usuários formem uma compreensão espacial da forma geral do animal, antes de dimensioná-lo para uma [escala real](scale.md) perto do usuário.

Com o tamanho total do objeto em mente, os usuários têm a expectativa de onde mover e procurar partes específicas desse objeto. Em uma experiência com conteúdo de imersão, ele ajuda a ter uma maneira de referir-se ao tamanho completo desse conteúdo. Por exemplo, se a experiência envolve a movimentação de um modelo de uma casa virtual, ela ajuda a ter uma versão de tamanho menor Doll da experiência para identificar onde elas estão dentro da casa.

Para obter um exemplo de criação de objetos grandes, consulte [carros de Volvo](holographic-frame.md#volvo-cars).

### <a name="many-objects"></a>Muitos objetos

Experiências com muitos objetos ou componentes devem considerar o uso de espaço completo em todo o usuário para evitar a aglomeração do quadro Holographic diretamente na frente do usuário. Recomendamos a introdução de conteúdo a uma experiência, especialmente com experiências que planejam fornecer muitos objetos ao usuário. A chave é **permitir que os usuários compreendam o layout do conteúdo** na experiência, o que os ajuda a obter uma compreensão espacial do que há em relação a eles como atualizações de conteúdo.

Uma técnica para conseguir isso é fornecer pontos persistentes (também conhecidos como pontos de referência) na experiência que ancora o conteúdo ao mundo real. Por exemplo, um ponto de referência pode ser um objeto físico no mundo real, como uma tabela em que o conteúdo digital aparece, ou um objeto digital, como um conjunto de telas digitais em que o conteúdo é exibido com frequência. Os objetos também podem ser colocados no periferia do quadro Holographic para incentivar o usuário a procurar o conteúdo da chave. A descoberta de conteúdo além do periferia pode ser auxiliada por [diretores de atenção](holographic-frame.md#attention-directors).

Colocar objetos no periferia pode encorajar os usuários a olhar para o lado e isso pode ser auxiliado por diretores de atenção, conforme descrito abaixo. Para obter mais informações sobre as considerações de quadro Holographic, consulte a documentação [confortável](comfort.md#holographic-frame-considerations) .

<br>

---

## <a name="interaction-considerations"></a>Considerações sobre interação

Assim como acontece com o conteúdo, as interações em uma experiência de realidade misturada não precisam ser limitadas ao que o usuário pode ver imediatamente. As interações podem ocorrer em qualquer lugar do espaço do mundo real em todo o usuário. Essas interações podem ajudar a incentivar os usuários a se movimentarem e explorarem experiências.

### <a name="attention-directors"></a>Diretores de atenção

Indicar pontos de interesse ou interações de chave pode ser crucial para progredir os usuários por meio de uma experiência. A atenção do usuário e a movimentação do quadro Holographic podem ser direcionadas de formas sutis ou pesadas. Lembre-se de direcionar os diretores de atenção com períodos de exploração gratuita em realidade misturada (especialmente no início de uma experiência) para evitar sobrecarregar o usuário. Em geral, há dois tipos de diretores de atenção:
* **Diretores visuais:** A maneira mais fácil de permitir que o usuário saiba que ele deve se mover em uma direção específica é fornecer uma indicação visual. Isso pode ser feito por meio de um efeito visual (por exemplo, um caminho que o usuário pode seguir visualmente para a próxima parte da experiência) ou até mesmo como setas direcionais simples. Qualquer indicador visual deve ser aterrado dentro do ambiente do usuário, não ' anexado ' ao quadro Holographic ou ao cursor.
* **Diretores de áudio:** o [som espacial](spatial-sound-design.md) pode fornecer uma maneira eficiente de estabelecer objetos em uma cena. Você pode alertar os usuários sobre os objetos que entram em uma experiência ou direcionar a atenção para um ponto específico no espaço, movendo a exibição do usuário para objetos de chave. Usar os diretores de áudio para orientar a atenção do usuário pode ser mais sutil e menos invasivo do que os diretores visuais. Em alguns casos, pode ser melhor começar com um diretor de áudio e, em seguida, passar para um diretor Visual se o usuário não reconhecer a indicação. Os diretores de áudio também podem ser emparelhados com os diretores visuais para dar ênfase adicional.

### <a name="commanding-navigation-and-menus"></a>Comandos, navegação e menus

As interfaces em experiências mistas de realidade são emparelhadas de maneira adequada com o conteúdo digital que eles controlam. Assim, os menus 2D sem flutuação livre geralmente não são ideais para interação e podem ser difíceis para os usuários muito confortavelmente dentro do quadro Holographic. Para experiências que exigem elementos de interface como menus ou campos de texto, considere usar um [método de marca](billboarding-and-tag-along.md) para seguir o quadro Holographic após um pequeno atraso. Evite bloquear conteúdo para o quadro como uma exibição de cabeçotes, pois isso pode ser desorientado para o usuário e quebrar o sentido do imersão para outros objetos digitais na cena.

Você também pode posicionar elementos de interface diretamente no conteúdo específico que eles controlam, permitindo que as interações ocorram naturalmente em relação ao espaço físico do usuário. Por exemplo, quebre um menu complexo em partes separadas, com cada botão ou grupo de controles anexados ao objeto específico que a interação afeta. Para obter esse conceito mais detalhadamente, considere o uso de [objetos que interagem](interactable-object.md).

### <a name="gaze-and-gaze-targeting"></a>Direcionamento de olhar e olhar

O quadro Holographic apresenta uma ferramenta para que o desenvolvedor dispare as interações e avalie onde a atenção de um usuário faz a pesquisa. [olhar](gaze-and-commit.md) é uma das [principais interações em HoloLens](interaction-fundamentals.md), em que olhar pode ser emparelhado com [gestos](gaze-and-commit.md#composite-gestures) (como com toque de ar) ou [voz](voice-input.md) (permitindo interações mais curtas e naturais baseadas em voz). Dessa forma, isso torna o quadro Holographic um espaço para observar o conteúdo digital e interagir com ele. Se a experiência chamar a interação com vários objetos em todo o espaço do usuário (por exemplo, várias seleções de objetos em todo o espaço do usuário com olhar + gesto), considere colocar esses objetos na exibição do usuário ou limitar a quantidade de movimento de cabeçalho necessário para promover o [conforto do usuário](comfort.md).

O olhar também pode ser usado para controlar a atenção do usuário por meio de uma experiência e ver quais objetos ou partes da cena o usuário pagou mais atenção. Isso pode ser usado especialmente para depurar uma experiência, permitindo que ferramentas analíticas como o calor vejam onde os usuários estão gastando mais tempo ou faltam determinados objetos ou interação. O acompanhamento de olhar também pode fornecer uma ferramenta poderosa para os facilitadores em experiências (consulte o exemplo de [cozinha do Lowe](holographic-frame.md#lowes-kitchen) ).

se você quiser ver os conceitos de design de acompanhamento de cabeça e olho em ação, confira nossa demonstração de vídeo de acompanhamento de **cabeça Hologramas e acompanhamento de olho** abaixo:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo foi retirado do aplicativo "Projetando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*

<br>

---

## <a name="performance"></a>Desempenho

O uso adequado do quadro Holographic é fundamental para as experiências de [qualidade de desempenho](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) . Um desafio comum (e usabilidade) é sobrecarregar o quadro do usuário com conteúdo digital, causando degradação do desempenho de renderização. Considere, em vez disso, usar o espaço completo em volta do usuário para organizar o conteúdo digital, usando as técnicas descritas acima, para diminuir a carga da renderização e garantir uma qualidade de exibição ideal.

o conteúdo Digital dentro do quadro do holographic do HoloLens também pode ser emparelhado com o [plano de estabilização](../develop/platform-capabilities-and-apis/case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) para desempenho ideal e [estabilidade do holograma](../develop/platform-capabilities-and-apis/hologram-stability.md).

<br>

---

## <a name="examples"></a>Exemplos

### <a name="volvo-cars"></a>Carros Volvo

<iframe width="940" height="530" src="https://www.youtube.com/embed/DilzwF90vec" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

na experiência do showroom da Volvo carros, os clientes são convidados a aprender sobre os recursos de um novo carro em uma experiência HoloLens guiada por um associado Volvo. Volvo enfrentou um desafio com o quadro Holographic: um carro de tamanho completo é muito grande para ser colocado ao lado de um usuário. A solução era iniciar a experiência com um ponto de referência físico, uma tabela central no showroom, com um modelo digital menor do carro colocado sobre a tabela. Isso garante que o usuário esteja vendo o carro completo quando ele é introduzido, permitindo um entendimento espacial quando o carro cresce para a escala do mundo real posteriormente na experiência.

A experiência do Volvo também usa os directors visuais, criando um efeito visual longo do modelo de carro de pequena escala na tabela para uma parede na sala de apresentação. Isso leva a um efeito de "janela mágica", mostrando a visão completa do carro a uma distância, ilustrando outros recursos do carro em escala do mundo real. O movimento da cabeça é horizontal, sem qualquer interação direta do usuário (em vez de reunir indicações visualmente e da narração da experiência do Volvo Association).

<br>

---

### <a name="lowes-kitchen"></a>Cozinha de Lowe

Uma experiência de armazenamento do Lowe convida os clientes em uma modelo em escala completa de uma cozinha para demonstrar várias oportunidades de reforma, como visto por meio do HoloLens. A cozinha na loja fornece um pano de fundo físico para objetos digitais, uma tela em branco de dispositivos, a tops e os gabinetes para a experiência mista da realidade para desdobrar.

As superfícies físicas atuam como pontos de referência estáticos para que o usuário se baseie na experiência, uma vez que o associado de um Lowe orienta o usuário por meio de diferentes opções de produtos e é concluído. Dessa forma, a associação pode direcionar verbalmente a atenção do usuário para o ' refrigerador ' ou ' centro da cozinha ' para demonstrar o conteúdo digital.

![a associação de um Lowe usa um tablet para guiar os clientes por meio da experiência de HoloLens.](images/loweskitchen-750px.jpg)<br>
*a associação de um Lowe usa um tablet para guiar os clientes por meio da experiência de HoloLens.*

A experiência do usuário é gerenciada, em parte, por uma experiência do Tablet controlada pela associação do Lowe. Parte da função do associado, nesse caso, também seria limitar a movimentação de cabeçalho excessiva, direcionando sua atenção tranqüilamente em todos os pontos de interesse na cozinha. A experiência do Tablet também fornece a associação do Lowe com os dados do olhar na forma de uma exibição calor da cozinha, ajudando a entender onde o usuário está acessando a pesquisa (por exemplo, em uma área específica do gabinete) para fornecê-las com mais precisão com as diretrizes de reforma.

Para obter uma análise mais profunda da experiência de cozinha do Lowe, consulte a [palestra da Microsoft em Ignite 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

<br>

---

### <a name="fragments"></a>Fragmentos

na HoloLens fragmentos de jogo, você fica mais à sua vida para a cena de crimes virtuais, mostrando pistas e evidências, e uma sala de reunião virtual, na qual você conversa com caracteres que ficam em suas cadeiras e que são lean em suas paredes.

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

Como uma experiência de imersão, esses usuários foram incentivados a examinar, mudando seu rumo em todas as direções para ver o cenário de Martian virtual. Embora seja possível garantir o conforto dos usuários, a presença virtual e a narração de Aldrin de repercussão forneceu um ponto focal durante toda a experiência. Esse registro virtual de repercussão (criado pela [estúdios de captura da realidade misturada da Microsoft) foi](https://www.microsoft.com/mixed-reality/capture-studios)orientado a real, de tamanho humano, no canto da sala, permitindo que os usuários o vejam no modo de exibição quase completo. A narração de repercussão direcionou os usuários a se concentrarem em diferentes pontos no ambiente (por exemplo, um conjunto de Martian Rocks no chão ou um intervalo de montanhas na distância) com alterações de cena específicas ou objetos introduzidos por ele.

![Os narradores virtuais mudarão o movimento de um usuário, criando um ponto focal poderoso em toda a experiência.](images/gazereset-750px.png)<br>
*Os narradores virtuais mudarão o movimento de um usuário, criando um ponto focal poderoso em toda a experiência.*

A representação realista de repercussão proporcionou um poderoso ponto focal, completo com técnicas sutis a serem revisadas para que o usuário se sinta como se estivesse lá, falando com você. À medida que o usuário se move sobre a experiência, a repercussão mudará para você até um limite antes de retornar a um estado neutro se o usuário se movimentar muito além de seu periferia. Se o usuário se parecer totalmente (por exemplo, para examinar algo em outro lugar na cena) e voltar para repercussão, a posição direcional do narrador se concentrará novamente no usuário. Técnicas como essa fornecem uma noção poderosa de imersão e criam um ponto focal dentro do quadro Holographic, reduzindo a movimentação de cabeça excessiva e promovendo o [conforto do usuário](comfort.md).

## <a name="see-also"></a>Confira também
* [Interações instinctuais](interaction-fundamentals.md)
* [Conforto](comfort.md)
* [Escala](scale.md)
* [Focar com a cabeça e esperar](gaze-and-dwell.md)
* [Estabilidade do holograma](../develop/platform-capabilities-and-apis/hologram-stability.md)
