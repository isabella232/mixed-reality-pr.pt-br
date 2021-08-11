---
title: Módulo lunar
description: Saiba como estender os gestos HoloLens base com acompanhamento de duas mãos e entrada do controlador Xbox, criar objetos reativos e implementar sistemas de menu.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Aplicativos de exemplo, Design, MRTK, Toolkit de Realidade Misturada, Unity, aplicativos de exemplo, aplicativos de exemplo, open-source, Microsoft Store, HoloLens, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 2afa40a31a5105bfe0ae674942e2bf88fd16f232b40827efb2446c2b4ad849ba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196572"
---
# <a name="lunar-module"></a>Módulo lunar

>[!NOTE]
>Este artigo aborda um exemplo exploratório que criamos nos [Laboratórios](https://github.com/Microsoft/MRDesignLabs_Unity)de Design de Realidade Misturada, um local em que compartilhamos nossos aprendizados e sugestões para o desenvolvimento de aplicativos de realidade misturada. Nossos artigos e código relacionados ao design evoluirão à medida que fazemos novas descobertas.

[O Módulo Lunar](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) é um aplicativo de exemplo de software livre dos Laboratórios de Design de Realidade Misturada da Microsoft. Saiba como estender os gestos base HoloLens com acompanhamento de duas mãos e entrada do controlador Xbox, criar objetos que são reativos para mapeamento de superfície e localização de plano e implementar sistemas de menu simples. Todos os componentes do projeto estão disponíveis para uso em suas próprias experiências de aplicativo de realidade misturada.

## <a name="demo-video"></a>Vídeo de demonstração 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IcIP]

Gravado com HoloLens 2 usando Captura de Realidade Misturada

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Repensando experiências clássicas para Windows Mixed Reality

No alto da atmosfera, um pequeno navio que não faz parte do módulo Apollo pesquisa metodicamente o terreno irregular abaixo. Nosso piloto de insuício vê uma área de aterrissagem adequada. O descendente é árduo, mas felizmente, esse percurso foi feito muitas vezes antes...

![Interface original da Interface Lunar de 1979 da Atari](images/640px-atari-lunar-lander.png)<br>
*Interface original da Interface Lunar de 1979 da Atari*

[Lunar Meio é](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) um clássico clássico do clássico em que os jogadores tentam fazer um piloto de uma lua em um ponto plano do terreno lunar. Qualquer pessoa que tenha filhos nos anos 1970 provavelmente passou horas em uma casa com os olhos colados nesse vetor que cai do céu. À medida que um jogador navega em sua nave até uma área de aterrissagem, o terreno é escalado para revelar progressivamente mais detalhes. Sucesso significa aterrissagem dentro do limite seguro de velocidade horizontal e vertical. Os pontos são concedidos pelo tempo gasto na aterrissagem e pelo combustível restante, com um multiplicador com base no tamanho da área de aterrissagem.

Além da gameplay, a era dos jogos de jogos traz uma inovação constante de esquemas de controle. Desde as configurações de botão e de quatro vias mais simples (vistas no [Pac-Man)](https://en.wikipedia.org/wiki/Pac-Man)até os esquemas altamente específicos e complicados vistos no final dos anos 90 e 00 (como aqueles em simuladores de carro e trilhos de trilho). O esquema de entrada usado no computador Lunar Popular é insuportado por dois motivos: redução e imersão.

![Console de console do Lunar Ika da Atari](images/atariconsole.png)<br>
*Console de console lunar da Atari*

Por que a Atari e muitas outras empresas de jogos decidiram repensar a entrada?

Naturalmente, uma mulher passeando por uma trilha será desaqueada pelo computador mais recente e mais chamativo. Mas o Lunar Meio apresenta uma nova versão de entrada que sai da grande público.

O Lunar Meio usa dois botões para girar **a** nave para a esquerda e para a direita e uma alavanca de força para controlar a quantidade de pressão que a nave produz. Essa alavanca fornece aos usuários um determinado nível de finesse que um periodo regular não pode fornecer. Ele também é um componente comum a cabines de piloto modernas. A Atari queria que o Lunar Lunar Meio-Mundo desse ao usuário a sensação de que ele estava, na verdade, pilotando um módulo lunar. Esse conceito é conhecido **como imersão tactile.**

A imersão de tactile é a experiência de comentários sensoriais de fazer ações repetitivas. Nesse caso, a ação repetitiva de ajustar a alavanca de aceleração e a rotação, que nossos olhos veem e nossos olhos escutam, ajuda a conectar o jogador ao ato de aterrissagem de um navio na superfície da Lua. Esse conceito pode ser vinculado ao conceito conceitual de "fluxo". Em que um usuário é totalmente absorta em uma tarefa que tem a combinação certa de desafio e recompensa, ou simplificando, ele está "na zona".

Indiscutivelmente, o tipo mais proeminente de imersão na realidade misturada é a imersão espacial. O ponto completo da realidade misturada é nos enganarmos quanto à ideia de que esses objetos digitais existem no mundo real. Estamos sintetizando hologramas em nosso ambiente, espacialmente imersos em ambientes e experiências inteiros. Isso não significa que ainda não podemos empregar outros tipos de imersão em nossas experiências, assim como o Atari fez com a imersão de tactile em Lunar Conforme o uso.

## <a name="designing-with-immersion"></a>Projetando com imersão

Como podemos aplicar a imersão de tactile a uma versão atualizada e volumosa ao clássico do Atari? Antes de lidar com o esquema de entrada, a construção do jogo para o espaço tridimensional precisa ser resolvida.

![Visualizando o mapeamento de superfície HoloLens](images/surfacemapping.png)<br>
*Visualizando o mapeamento espacial HoloLens*

Aproveitando o ambiente de um usuário, efetivamente temos infinitas opções de terreno para aterrissagem de nosso módulo lunar. Para tornar o jogo mais parecido com o título original, um usuário poderia potencialmente manipular e colocar os painel de aterrissagem de diversas dificuldades em seu ambiente.

![Pilotando o módulo lunar](images/640px-lm-hero.jpg)<br>
*Pilotando o módulo lunar*

Exigir que o usuário aprenda o esquema de entrada, controle a nave e tenha um pequeno destino para chegar é muito para perguntar. Uma experiência de jogo bem-sucedida apresenta a combinação certa de desafio e recompensa. O usuário pode escolher um nível de dificuldade, com o modo mais fácil simplesmente exigindo que o usuário seja lançado com êxito em uma área definida pelo usuário em uma superfície digitalizada pelo HoloLens. Depois que um usuário obtém o trava do jogo, ele pode, então, aumentar a dificuldade que quiser.

### <a name="adding-input-for-hand-gestures"></a>Adicionando entrada para gestos de mão

HoloLens entrada base tem apenas dois gestos : Toque [no Ar e Abrir.](../../design/gaze-and-commit.md#composite-gestures) Os usuários não precisam se lembrar de nuances contextuais ou de uma lista de gestos específicos que torna a interface da plataforma versátil e fácil de aprender. Embora o sistema só possa expor esses dois gestos, HoloLens como um dispositivo é pode acompanhar duas mãos de uma só vez. Nossa ode a Lunar Xtender é um [aplicativo imersivo, o que significa que podemos estender o conjunto base de gestos para aproveitar duas mãos e adicionar nossos próprios meios de tactile de forma agradável para a navegação do módulo lunar.

Ao olhar para o esquema de controle original, **precisávamos resolver para o movimento e a rotação.** A ressalva é a rotação no novo contexto adiciona um eixo adicional (tecnicamente dois, mas o eixo Y é menos importante para aterrissagem). Os dois movimentos distintos de navio naturalmente se prestam a serem mapeados para cada mão:

![Toque e arraste o gesto para girar a tela em todos os três eixos](images/module-handdrag.gif)<br>
*Toque e arraste o gesto para girar a tela em todos os três eixos*

**Impulso**

A alavanca na máquina original mapeada para uma escala de valores, quanto mais alta a alavanca foi movida, mais força foi aplicada à nave. Uma nuance importante a ser destacada aqui é como o usuário pode tirar a mão do controle e manter um valor desejado. Podemos usar efetivamente o comportamento de toque e arrastar para obter o mesmo resultado. O valor da força começa em zero. O usuário toca e arrasta para aumentar o valor. Nesse ponto, eles poderiam deixar de ir para a manutenção. Qualquer alteração de valor de gesto de toque e arrastar seria o delta do valor original.

**Rotação**

Isso é um pouco mais complicado. Ter botões holográficos "girar" para tocar torna uma experiência ruim. Não há um controle físico a ser aproveitado, portanto, o comportamento deve vir da manipulação de um objeto que representa a estrutura ou com o próprio meio. Encontramos um método usando tap-and-drag, que permite que um usuário o "esmige e pull" efetivamente na direção em que deseja que ele seja faceado. Sempre que um usuário toca e mantém, o ponto no espaço em que o gesto foi iniciado se torna a origem da rotação. Arrastar da origem converte o delta da tradução da mão (X,Y,Z) e o aplica ao delta dos valores de rotação da meio. Ou, mais simples, arrastar <-> à direita, para cima *<-> para baixo, encaminhar <->* de volta em espaços gira a nave de acordo.

Como o HoloLens pode acompanhar duas mãos, a rotação pode ser atribuída à mão direita enquanto a pressão é controlada pela esquerda. Finesse é o fator determinante para o sucesso neste jogo. A *sensação* dessas interações é a prioridade mais alta absoluta. Especialmente no contexto de imersão de tactile. Um navio que reage muito rapidamente seria difícil de conduzir, enquanto um muito lento exigiria que o usuário "esmo e pull" no navio por um período de tempo muito longo.

### <a name="adding-input-for-game-controllers"></a>Adicionando entrada para controladores de jogo

Embora os gestos de mão no HoloLens forneçam um novo método de controle de granulação fina, ainda há uma certa falta de comentários de tactile 'true' que você recebe de controles análogos. Conectar um controlador de jogos do Xbox nos permite trazer de volta essa noção de física, aproveitando os controles para manter o controle de granulação fina.

Há várias maneiras de aplicar o esquema de controle relativamente simples ao controlador Xbox. Como estamos tentando ficar o mais próximo possível da configuração original do original, **a Opção** é mapeada melhor para o botão de gatilho. Esses botões são controles análogos, o que significa que eles têm mais do que estados simples de ligar e desligar, eles realmente respondem ao grau de pressão sobre eles.  Isso nos dá um constructo semelhante ao **da alavanca de controle**. Ao contrário do jogo original e do gesto de mão, esse controle reduzirá a pressão da nave quando um usuário parar de pressionar o gatilho. Ele ainda fornece ao usuário o mesmo grau de finesse que o jogo original do game de futebol.

![O thumbstick esquerdo é mapeado para Yaw e Roll, o thumbstick direito é mapeado para Apresentação e Rolagem](images/thumbsticksidebyside.gif)<br>
*O thumbstick esquerdo é mapeado para yaw e roll; o thumbstick direito é mapeado para a apresentação e a rolagem*

Os thumbsticks duplos naturalmente se prestam a controlar a rotação da nave. Infelizmente, há três eixos nos quais a nave pode girar e dois thumbsticks que suportam dois eixos. Essa incompatibilidade significa que um Thumbstick controla um eixo; ou há sobreposição de eixos para o Thumbsticks. A solução anterior acabou de se sentir "quebrada", já que Thumbsticks de forma inerente mesclar seus valores X e Y locais. A última solução exigiu algum teste para descobrir quais eixos redundantes se sentem mais naturais. O exemplo final usa a *guinada* e *roll* (eixos Y e x) para o Thumbstick esquerdo, e *pitch* e *roll* (eixos Z e x) para a Thumbstick direita. Isso parecia que a *rolagem* mais natural parece ser bem emparelhada com *desvio* e *inclinação*. Como uma observação adicional, o uso de Thumbsticks para *roll* também ocorre para dobrar o valor de rotação; é muito divertido ter os loops Lander.

este aplicativo de exemplo demonstra como o reconhecimento espacial e tactile imersão podem alterar significativamente uma experiência graças às modalidades de entrada extensível de Windows Mixed Reality. Embora o lunar Lander possa estar perto de 40 anos de idade, os conceitos expostos com esse pequeno octógono-com-pernas residirão sempre. Ao imaginar o futuro, por que não examinar o passado?

## <a name="technical-details"></a>Detalhes técnicos

Você pode encontrar scripts e pré-fabricados para o aplicativo de exemplo de módulo lunar nos [laboratórios de design da realidade misturada GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Linville de Addison</b><br>Designer de UX @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Confira também

* [Hub de Exemplos do MRTK](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tabela periódica dos elementos 2.0](periodic-table-of-the-elements-2.md)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)