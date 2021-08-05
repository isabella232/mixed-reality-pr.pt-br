---
title: Estudo de caso – Usando o som espacial no RoboRaid
description: O som espacial é um dos recursos mais interessantes do Microsoft HoloLens, que permite que os usuários percebam o que está acontecendo ao redor deles quando os objetos estão fora de vista.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, RoboRaid, som espacial, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Toolkit realidade misturada, cpu
ms.openlocfilehash: f4a47fe119dffbd32d264cc8e21ae2b3ade7cfcccef8e7e18fbb4491783d0542
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208986"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Estudo de caso – Usando o som espacial no RoboRaid

Este artigo descreve os desafios enfrentados pela equipe de Microsoft HoloLens experiência ao criar áudio para a primeira pessoa de realidade misturada [roboRaid.](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)

## <a name="the-tech"></a>A tecnologia

[O som espacial](spatial-sound.md) é um dos recursos mais interessantes do Microsoft HoloLens, que permite que os usuários percebam o que está acontecendo ao redor deles quando os objetos não estão na linha de visão.

No RoboRaid, o uso mais óbvio e eficaz do som espacial é alertar o player sobre algo que acontece fora de sua visão periférico. Por exemplo, o Violador pode entrar de qualquer uma das paredes examinadas na sala. Se você não estiver voltada para o local em que ele está inserindo, poderá perder. Para alertá-lo sobre essa situação, você ouvirá um pouco de áudio distinto proveniente de onde o Breacher está inserindo, o que permite que você saiba que precisa agir rapidamente para interdite-lo.

## <a name="behind-the-scenes"></a>Nos bastidores

Criar som espacial para HoloLens aplicativos é tão novo e exclusivo que os problemas podem ser difíceis de resolver porque não há nenhum projeto passado a ser referenciado. Esperamos que esses exemplos dos desafios de áudio enfrentados ao criar o RoboRaid ajudarão você a criar áudio para seus próprios aplicativos.

### <a name="be-mindful-of-taxing-the-cpu"></a>Se esqueça de taxar a CPU

O som espacial pode ser exigente na CPU. Para uma experiência ocupada como o RoboRaid, era crucial manter o número de instâncias de som espacial abaixo de oito em um determinado momento. Normalmente, era tão fácil quanto definir o limite de instâncias para eventos de áudio diferentes. Todas as instâncias que ocorrem depois que o limite é atingido são mortas. Por exemplo, quando os drones são gerados, suas reações são limitadas a três instâncias em um determinado momento. Considerando que apenas cerca de quatro drones podem ser gerados ao mesmo tempo, três encerras são muitos, pois não há como seu cérebro acompanhar esses muitos eventos de áudio semelhantes. Isso liberou recursos para outros eventos de som espacial, como explosão de adversários ou ataques de ataque.

### <a name="rewarding-a-successful-dodge"></a>Recompensando um trabalho bem-sucedido

A mecânica de redging é uma das mecânicas de jogo mais importantes no RoboRaid e também algo que acreditamos ser realmente exclusivo para a experiência HoloLens experiência. Como tal, queríamos tornar os pontos bem-sucedidos muito interessantes para o jogador. Fizemos com que o Doppler "soe atraente" bastante no início do desenvolvimento. Inicialmente, meu plano era usar um loop e manipulá-lo em tempo real usando volume, tom e filtro. A implementação para isso seria muito elaborado. Antes de comprometer os recursos para criar isso, criamos um protótipo barato usando um ativo com o efeito Doppler criado apenas para descobrir como ele se parece. Nosso dev bem-feito fez isso de modo que esse ativo de meio-campo fosse reproduzir exatamente 0,7 segundo antes que o projeto fosse passado pelo ouvido do jogador e os resultados pareceram incríveis! Não é necessário dizer que implementamos a solução mais complexa e implementamos o protótipo.

*(Para obter mais informações sobre como criar um ativo de áudio com o efeito Doppler integrado, consulte [100 Whopplees em 2 minutos](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/).)* 
<br>
![A reação bem-sucedida do projeto de um adversário recompensa o jogador com um som de satisfação.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Inging ineffective sounds

Originalmente, queríamos tocar um som de explosão por trás do jogador depois que ele tivesse sido bem-sucedido no projeto do adversário, mas decidimos resolver isso por vários motivos. Primeiro, ele não se parece tão eficaz quanto o SFX que utilizamos para o carro. Quando o projeto atinge uma parede atrás de você, algo mais teria ocorrido no jogo que mascararia esse som. Em segundo lugar, não houve colisão no chão, portanto, não conseguimos obter a explosão para reproduzir quando o projeto atingiu o chão em vez das paredes. E, por fim, houve o custo de CPU do som espacial. O adversário de Elite (um que pode rastrear dentro da parede) tem um ataque especial que dispara cerca de oito projetos. Isso não apenas causava uma grande confusão na combinação, mas também introduziu uma grande confusão porque estava atingindo a CPU com muita força.

### <a name="communicating-a-hit"></a>Comunicando um acerto

Um problema interessante que encontramos no HoloLens era a dificuldade de comunicar efetivamente que um jogador foi atingido. O que torna uma experiência de realidade misturada bem-sucedida é a sensação de que a história está acontecendo com você. Isso significa que você precisa acreditar que está morando com um robô robô em sua própria sala de estar.

Os jogadores obviamente não sentirão nada quando são atingidos, portanto, precisamos encontrar uma maneira de convencer o jogador de que algo ruim aconteceu com eles. Em jogos convencionais, você pode ver uma animação que permite que você saiba que seu caractere recebeu um hit, ou a tela pode piscar vermelho e seu caractere pode ser um pouco pesado. Como esses tipos de responsabilidades não funcionam em uma experiência de realidade misturada, decidimos combinar a indicação visual com um som confuso que indica que você causou danos. Criei um som grande e o destaquei tanto na combinação que ele abaixou tudo. Em seguida, para torná-lo ainda mais importante, adicionamos um breve som de aviso como se um sub fosse sinking. 
<br>
![Quando um jogador é atingido no RoboRaid, ele vê uma indicação visual, mas também obtém uma indicação de áudio que informa que ele causou danos.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Obter um grande som de alto-falantes pequenos

HoloLens alto-falantes são pequenos e leves para atender às necessidades do dispositivo, portanto, você não pode esperar ouvir muito baixo-end. Semelhante ao desenvolvimento para smartphones ou dispositivos de jogos portáteis, os criadores e designers de som devem estar atentos ao conteúdo de frequência de seu áudio. Eu sempre projete sons ou escreva música com intervalo de frequência total porque usar fones de ouvido é uma opção para os usuários. No entanto, para garantir a compatibilidade com HoloLens alto-falantes, eu executarei um teste ocasionalmente colocando um EQ no mestre de qualquer DAW em que estou trabalhando. A configuração de EQ consiste em um filtro de passagem alta em torno de 600 Hz a 700 Hz (não muito alto) e filtro de baixa passagem em cerca de 10 mil (íngremes). Isso deve lhe dar uma ideia aproximada de como seus sons serão reproduzir no dispositivo.

Se você estiver contando com o rock para dar a noção de alteração de ordem em sua música, talvez você descubra que sua música perde completamente a noção de raiz ao aplicar essa configuração de EQ. Para corrigir isso, adicionei outra camada ao velinha que é um octave mais alto (com alguns poderosos) e a misture para obter a noção de raiz de volta. Às vezes, o uso de distorção para ampliar os harmônicos dará conteúdo de frequência suficiente no intervalo superior para fazer com que nosso cérebro pense que há algo sob ele. Isso é verdadeiro para SFX, como impactos, explosão ou sons para momentos especiais, como super ataques de um chefe. Você realmente não pode contar com o low-end para dar ao jogador uma noção de impacto ou peso. Assim como com a música, usar distorção para dar alguma coisa definitivamente ajudada.

### <a name="making-your-audio-cues-stand-out"></a>Como destacar suas sugestões de áudio

Naturalmente, todos na equipe quiseram música desambiente, música barulhenta e explosão enormes; mas eles também quiseram ser capazes de ouvir o voiceover ou qualquer outra indicação de áudio crítica do jogo.

Em um jogo de console com uma gama completa de frequência, você tem mais opções para dividir frequências dependendo da importância do som. Para RoboRaid, eu era limitado no número de intervalos de frequências que eu podia curvar de sons. Se você usar filtro de passagem baixa e a curva se sair muito da extremidade superior do espectro, não terá mais nada no som porque não há muito de baixo-end.

Para fazer com que o RoboRaid soe tão grande quanto puder no dispositivo, precisamos reduzir o intervalo dinâmico de toda a experiência e fazer uso extensivo da redução criando uma hierarquia clara de importância para diferentes tipos de sons. Des definido o de -2 dB para -6 dB, dependendo da importância. Eu pessoalmente não gosto de desajuste óbvio em jogos, portanto, eu gastava muito tempo ajustando o tempo de esmaeçamento dentro/fora e a quantidade de atenuação de volume. Configuramos barramentos separados para som espacial, som não espacial, VO e barramento dry sem reverb para música. Em seguida, criamos barramentos de alta prioridade, críticos e não críticos para que os ativos fossem definidos para ir para seus barramentos apropriados.

Espero que os profissionais de áudio tenham tanto trabalho divertido e divertido em seus próprios aplicativos quanto no RoboRaid. Mal posso esperar para ver (e ouvir!) o que as pessoas de fora da Microsoft terão para HoloLens.

## <a name="do-it-yourself"></a>Faça você mesmo

Um truque que descobri para fazer com que determinados eventos (como explosão) pareçam "maiores", como eles estão preenchendo a sala, foi criar um ativo mono para o som espacial e misturá-lo com um ativo estéreo 2D, a ser tocado novamente em 3D. É preciso algum ajuste, pois ter muitas informações no conteúdo estéreo diminuirá a direcionalidade dos ativos mono. No entanto, obter o equilíbrio correto resultará em sons enormes que fará com que os jogadores girem a cabeça na direção certa.

Você mesmo pode experimentar grandes sons usando os ativos de áudio abaixo:

**Cenário 1**
1. Baixe [roboraid_enemy_explo_mono.wav e](images/roboraid-enemy-explo-mono.wav) de definido para reproduzir o som espacial e atribuí-lo a um evento.
2. Baixe [roboraid_enemy_explo_stereo.wav e](images/roboraid-enemy-explo-stereo.wav) de definido para reproduzir em estéreo 2D e atribua ao mesmo evento acima. Como esses ativos são normalizados para o Unity, atenuar o volume de ambos os ativos para que ele não seja clip.
3. Reproduza os dois sons juntos. Mova a cabeça para sentir como parece espacial.

**Cenário 2**
1. Baixe [roboraid_enemy_explo_summed.wav e](images/roboraid-enemy-explo-summed.wav) de definido para reproduzir o som espacial e atribua a um evento.
2. Reproduza esse ativo sozinho e compare-o com o evento do Cenário 1.
3. Tente um equilíbrio diferente de arquivos mono e estéreo.

## <a name="see-also"></a>Confira também

* [Som espacial](spatial-sound.md)
* [RoboRaid para Microsoft HoloLens](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
