---
title: Módulo lunar
description: saiba como estender os gestos de base de HoloLens com acompanhamento de duas mãos e entrada do controlador Xbox, criar objetos reativos e implementar sistemas de menus.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, aplicativos de exemplo, Design, MRTK, realidade misturada Toolkit, Unity, aplicativos de amostra, aplicativos de exemplo, código-fonte aberto, Microsoft Store, HoloLens, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 4a736990a94d7f5c97a1bfc2edf998e327071bcb
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757218"
---
# <a name="lunar-module"></a>Módulo lunar

>[!NOTE]
>Este artigo discute um exemplo exploratório que criamos nos laboratórios de [design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity), um lugar onde compartilhamos nossas aprendeções e sugestões para o desenvolvimento de aplicativos de realidade misturada. Nossos artigos e códigos relacionados ao design irão evoluir à medida que fizermos novas descobertas.

O [módulo lunar](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) é um aplicativo de exemplo de código-fonte aberto dos laboratórios de design de realidade misturada da Microsoft. saiba como estender gestos de base de HoloLens com acompanhamento de duas mãos e entrada do controlador Xbox, criar objetos que são reativos para mapeamento de superfície e localização de plano e implementar sistemas de menu simples. Todos os componentes do projeto estão disponíveis para uso em suas próprias experiências de aplicativo de realidade misturada.

## <a name="demo-video"></a>Vídeo de demonstração 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IcIP]

registrado com HoloLens 2 usando a captura de realidade misturada

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Relembrando experiências clássicas para Windows Mixed Reality

Alto na atmosfera, uma pequena que sobrou de remessa do módulo Apollo pesquisa metodicamente o terreno irregular abaixo. Nosso piloto Fearless é uma área de aterrissagem adequada. A descendente é árdua, mas felizmente, essa jornada foi feita muitas vezes antes...

![Interface original da Atari lander lunar 1979](images/640px-atari-lunar-lander.png)<br>
*Interface original da Atari lander lunar 1979*

[Lunar Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) é um clássico, em que os jogadores tentam fazer um piloto de uma lua Lander em um ponto simples de terreno lunar. Qualquer pessoa nasceu na 70 tem mais chances de horas em um horário comercial com seus olhos colados com esse vetor entregue plummeting do céu. Como um jogador navega pelo seu envio para uma área de aterrissagem, o terreno é dimensionado para revelar cada vez mais detalhes. Sucesso significa o patamar dentro do limite seguro de velocidade horizontal e vertical. Os pontos são concedidos para o tempo gasto e o combustível restante, com um multiplicador com base no tamanho da área de aterrissagem.

Além do jogo, a época de partida dos jogos trouxe inovação constante de esquemas de controle. Do joystick de quatro vias e das configurações de botão mais simples (visto no icônico [Pac-Man](https://en.wikipedia.org/wiki/Pac-Man)) para os esquemas altamente específicos e complicados vistos nas últimas 90 s e 00s (como aquelas em simuladores de golfe e trilhos de trilho). O esquema de entrada usado na máquina lander lunar é intrigante por dois motivos: moderada e imersão.

![Console de Atari lunar Lander](images/atariconsole.png)<br>
*Console Atari lunar Lander*

Por que Atari e tantas outras empresas de jogos decidem reconsiderar a entrada?

Um criança percorrendo um intrigada será naturalmente o mais novo computador flashiest. Mas o lunar Lander apresenta um mecânico de entrada romance que me esgotou da sua escala.

O lander lunar usa dois botões para girar o envio para a esquerda e para a direita e uma **alavanca de Thrustmaster** para controlar a quantidade de Thrustmaster que o navio produz. Essa alavanca dá aos usuários um determinado nível de astúcia que um joystick regular não pode fornecer. Também é um componente comum às ferramentas cockpit de aviação moderna. Atari queria lander lunar para aprofundar o usuário na sensação de que eles estavam na verdade, realizando um piloto de um módulo lunar. Esse conceito é conhecido como **tactile imersão**.

TACTILE imersão é a experiência de comentários de sensor de fazer ações repetitivas. Nesse caso, a ação repetitiva de ajustar a alavanca de limitação e a rotação, que nossos olhos veem e nossos ouvidos Ouve, ajuda a conectar o jogador ao ato de pouso de uma entrega na superfície da lua. Esse conceito pode ser vinculado ao conceito de psicológica de "Flow". Onde um usuário é totalmente absorvido em uma tarefa que tem a combinação certa de desafio e recompensa, ou ainda mais simplesmente, eles estão "na zona".

De forma improvada, o tipo mais proeminente de imersão em realidade misturada é imersão espacial. O ponto total da realidade misturada é nos enganar a acreditar que esses objetos digitais existem no mundo real. Estamos sintetizando hologramas em nossos arredores, imersos espacialmente em ambientes e experiências inteiros. Isso não significa que ainda podemos empregar outros tipos de imersão em nossas experiências, assim como Atari fez com tactile imersão no lunar Lander.

## <a name="designing-with-immersion"></a>Criando com imersão

Como podemos aplicar tactile imersão a uma atualização volumétricos sequência para o Atari clássico? Antes de lidar com o esquema de entrada, a construção do jogo para o espaço tridimensional precisa ser resolvida.

![Visualizando o mapeamento de superfície no HoloLens](images/surfacemapping.png)<br>
*Visualizando o mapeamento espacial no HoloLens*

Aproveitando o ambiente de um usuário, nós efetivamente temos opções de terrenos infinitas para o patamar do nosso módulo lunar. Para tornar o jogo mais parecido com o título original, um usuário poderia potencialmente manipular e colocar os pads de pouso de diversas dificuldades em seu ambiente.

![Pilotando o módulo lunar](images/640px-lm-hero.jpg)<br>
*Pilotando o módulo lunar*

Exigir que o usuário Aprenda o esquema de entrada, controle a remessa e faça com que um pequeno destino seja um grande alvo é muito a ser solicitado. Uma experiência de jogo bem-sucedida apresenta a combinação certa de desafio e recompensa. O usuário pode escolher um nível de dificuldade, com o modo mais fácil simplesmente exigindo que o usuário alcance com êxito uma área definida pelo usuário em uma superfície digitalizada pelo HoloLens. Quando um usuário sai do jogo, ele pode então se ajustar à dificuldade que eles veem.

### <a name="adding-input-for-hand-gestures"></a>Adicionando entrada para gestos de mão

HoloLens entrada de base tem apenas dois gestos – [toque e flor do ar](../../design/gaze-and-commit.md#composite-gestures). Os usuários não precisam lembrar nuances contextuais ou uma lista lavanderia de gestos específicos que tornam a interface da plataforma versátil e fácil de aprender. embora o sistema possa expor apenas esses dois gestos, HoloLens como um dispositivo pode acompanhar duas mãos ao mesmo tempo. Nosso ode para lunar Lander é um aplicativo de "imersão", o que significa que podemos estender o conjunto base de gestos para aproveitar duas mãos e adicionar nossa própria agradavelmente tactile significa para a navegação de módulo lunar.

Voltando ao esquema de controle original, **precisávamos resolver para Thrustmaster e Rotation**. A limitação é a rotação no novo contexto adiciona um eixo adicional (tecnicamente, dois, mas o eixo Y é menos importante para a aterrissagem). Os dois movimentos de envio distintos naturalmente se prestam para serem mapeados para cada mão:

![Gesto de tocar e arrastar para girar Lander em todos os três eixos](images/module-handdrag.gif)<br>
*Gesto de tocar e arrastar para girar Lander em todos os três eixos*

**Thrustmaster**

A alavanca no computador original de alta prioridade mapeada para uma escala de valores, quanto mais alta a alavanca foi movida, mais o ThrustMaster foi aplicado à remessa. Uma nuance importante para destacar aqui é como o usuário pode tirar seu alcance do controle e manter um valor desejado. Podemos usar efetivamente o comportamento de toque e arrastar para obter o mesmo resultado. O valor de Thrustmaster começa em zero. O usuário toca e arrasta para aumentar o valor. Nesse ponto, eles poderiam deixar de continuar a mantê-lo. Qualquer alteração de valor de gesto de toque e arrastar seria o Delta do valor original.

**Rotação**

Isso é um pouco mais complicado. Ter os botões "girar" de Holographic para tocar para uma experiência terrível. Não há um controle físico para aproveitar, portanto, o comportamento deve vir da manipulação de um objeto que representa o Lander ou com o próprio Lander. Nós reunimos um método usando TAP-and-arraste, que permite que um usuário "empurre e empurre" com eficiência na direção que desejam que ele tenha uma face. A qualquer momento que um usuário toca e se mantém, o ponto no espaço em que o gesto foi iniciado se torna a origem da rotação. Arrastar da origem converte o Delta da tradução do lado (X, Y, Z) e o aplica ao Delta dos valores de rotação do Lander. Ou, mais simplesmente, *arrastando para a esquerda <-> direito, < > para baixo, encaminhar <-> de volta em espaços gira a remessa de acordo*.

como o HoloLens pode acompanhar duas mãos, a rotação pode ser atribuída à mão à direita enquanto o thrustmaster é controlado pela esquerda. Astúcia é o fator determinante para o sucesso neste jogo. A *sensação* dessas interações é a prioridade mais alta absoluta. Especialmente no contexto de tactile imersão. Um envio que reage muito rapidamente seria difícil de ser direcionado, enquanto um pouco lento exigiria que o usuário "Envie por push e puxe" na entrega por um longo período de tempo estranha.

### <a name="adding-input-for-game-controllers"></a>Adicionando entrada para controladores de jogo

os gestos de mão no HoloLens fornecem um método romance de controle refinado, ainda há uma certa falta de comentários de tactile "verdadeiro" que você obtém de controles analógicos. Conectar um controlador de jogo do Xbox nos permite voltar essa sensação de física, aproveitando os pentes de controle para manter o controle refinado.

Há várias maneiras de aplicar o esquema de controle relativamente direto ao controlador Xbox. Como estamos tentando permanecer o mais próximo possível da configuração original, o **Thrustmaster** mapeia melhor para o botão disparador. Esses botões são controles analógicos, o que significa que eles têm mais do que Estados simples *e desligados* , eles realmente respondem ao grau de pressão colocados neles. Isso nos dá um constructo semelhante à **alavanca de Thrustmaster**. Ao contrário do jogo original e do gesto de mão, esse controle recortará a Thrustmaster do navio quando um usuário parar de colocar a pressão no gatilho. Ele ainda dá ao usuário o mesmo grau de astúcia que o jogo de Altova original.

![Thumbstick à esquerda é mapeada para guinada e roll, a Thumbstick direita é mapeada para pitch e roll](images/thumbsticksidebyside.gif)<br>
*O Thumbstick esquerdo é mapeado para guinada e roll; o Thumbstick direito é mapeado para pitch e roll*

O Thumbsticks duplo se presta naturalmente ao controle da rotação de remessa. Infelizmente, há três eixos nos quais a remessa pode girar e duas Thumbsticks que dão suporte a dois eixos. Essa incompatibilidade significa que um dos controles de um eixo; ou há sobreposição de eixos para os thumbsticks. A solução anterior acabou se sentido "interrompida", pois os thumbsticks mesclam inerentemente seus valores X e Y locais. A última solução exigia alguns testes para descobrir quais eixos redundantes são mais naturais. O exemplo final usa *yaw* e roll *(eixos* Y e  X) para o thumbstick esquerdo e a apresentação e a rolagem *(eixos* Z e X) para o thumbstick direito. Isso parece mais natural, pois *o roll* parece emparelhar-se independentemente bem com *yaw* e *pitch.* Como uma observação lateral, o uso de ambos os thumbsticks para *roll* também acontece para duplicar o valor de rotação; É muito divertido ter os loops do meio.

Este aplicativo de exemplo demonstra como o reconhecimento espacial e a imersão de tactile podem alterar significativamente uma experiência graças às Windows Mixed Reality de entrada extensível. Embora o Lunar Ltda possa estar se aproximando de 40 anos de idade, os conceitos expostos com esse pequeno octagono com os pés continuarão para sempre. Ao entender o futuro, por que não olhar para o passado?

## <a name="technical-details"></a>Detalhes técnicos

Você pode encontrar scripts e pré-fabs para o aplicativo de exemplo do Módulo Lunar nos Laboratórios de Design de [Realidade Misturada GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Euclidn Linville</b><br>Designer de UX @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Confira também

* [Hub de Exemplos do MRTK](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tabela periódica dos elementos 2.0](periodic-table-of-the-elements-2.md)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)