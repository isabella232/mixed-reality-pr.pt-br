---
title: Conforto
description: Durante a visualização natural, o sistema visual humano conta com várias fontes de informações, ou “indicações”, para interpretar formas 3D e a posição relativa de objetos.
author: erickjpaul
ms.author: erpau
ms.date: 06/25/2020
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, design, conforto, HoloLens 2, HoloLens (1ª geração), headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada, locomoção
ms.openlocfilehash: 87cf45628a530da65d9feb29556afb7c4a8ee1d3f13385cbf521d2621ac0c2ae
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226418"
---
# <a name="comfort"></a>Conforto

Durante a visualização natural, o sistema visual humano conta com várias fontes de informações, ou “indicações”, para interpretar formas 3D e as posições relativas de objetos. Algumas indicações dependem apenas de um olho (ou indicação monocular), incluindo:

* [Perspectiva linear](https://en.wikipedia.org/wiki/Perspective_(graphical))
* [Tamanho familiar](https://en.wikipedia.org/wiki/Size#Perception_of_size)
* Oclusão
* [Desfoque de profundidade do campo](https://en.wikipedia.org/wiki/Depth_of_field)
* [Acomodação](https://en.wikipedia.org/wiki/Accommodation_(eye)). 

Outras indicações dependem dos dois olhos (ou indicações binoculares), e incluem:

* [Vergência](https://en.wikipedia.org/wiki/Vergence): essencialmente, as rotações relativas dos olhos necessárias para examinar um objeto
* [Disparidade binocular](https://en.wikipedia.org/wiki/Stereopsis): o padrão de diferenças entre as projeções da cena na parte posterior dos dois olhos 

Para garantir o máximo de conforto em capacetes de realidade virtual, é importante criar e apresentar o conteúdo de modo que ele imite as indicações no mundo natural. Da perspectiva física, também é importante projetar um conteúdo que não exija movimentos cansativos do pescoço ou dos braços. Neste artigo, abordaremos as principais considerações que você deve ter em mente para atingir essas metas.

## <a name="vergence-accommodation-conflict"></a>Conflito entre vergência e acomodação

Para ver objetos com nitidez, os humanos precisam [acomodar](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) ou ajustar o foco dos olhos à distância do objeto. Ao mesmo tempo, a rotação dos dois olhos precisa [convergir](https://en.wikipedia.org/wiki/Convergence_(eye)) para a distância do objeto, a fim de evitar uma visualização de imagens duplas. Na visualização natural, a vergência e a acomodação estão vinculadas. Quando você vê algo próximo (por exemplo, uma mosca doméstica perto do nariz), seus olhos se cruzam e se acomodam a um ponto próximo. Por outro lado, se você vê algo em um infinito óptico (começando a aproximadamente 6 m ou a uma distância maior para uma visão normal), as linhas de visão dos olhos se tornam paralelas, e as lentes dos olhos se acomodam ao infinito. 

Na maioria dos capacetes de realidade virtual, os usuários sempre se acomodarão à distância focal do capacete para obter uma imagem nítida, mas convergirão para a distância do objeto de interesse para obter uma só imagem. Quando os usuários se acomodam a distâncias diferentes e convergem para elas, o vínculo natural entre as duas indicações é desfeito, levando ao desconforto ou à fadiga visual.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/-606oZKLa_s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="guidance-for-holographic-devices"></a>Diretrizes para dispositivos holográficos

Os capacetes do HoloLens são fixados a uma distância óptica de aproximadamente 2,0 m do usuário. Os usuários sempre precisam se acomodar próximo a 2,0 m para manter uma imagem nítida no dispositivo. Os desenvolvedores de aplicativos podem orientar o local de convergência dos olhos dos usuários colocando o conteúdo e os hologramas em várias profundidades. O desconforto do conflito entre a vergência e a acomodação pode ser evitado ou minimizado, mantendo o conteúdo ao qual os usuários convergem o mais próximo possível de 2,0 m. Por exemplo, em uma cena com muita profundidade, coloque as áreas de interesse próximo a 2,0 m do usuário quando possível. Quando o conteúdo não pode ser colocado próximo a 2,0 m, o desconforto do conflito entre vergência e acomodação é maior quando o foco do usuário alterna entre distâncias diferentes. Em outras palavras, é muito mais confortável olhar para um holograma fixo a 50 cm de distância do que para um holograma a 50 cm que se move para frente e para longe de você com o tempo.

![Distância ideal para colocação dos hologramas partindo do usuário.](images/distanceguiderendering-950px.png)<br>
*Distância ideal para colocação dos hologramas partindo do usuário*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>Melhores práticas do HoloLens (1ª geração) e do HoloLens 2

Para obter o máximo de conforto, **a zona ideal para posicionamento do holograma é entre 1,25 m e 5 m**. Em todos os casos, os designers devem tentar estruturar cenas de conteúdo para encorajar os usuários a interagir a um 1 m de distância ou mais do conteúdo (por exemplo, ajuste o [tamanho do conteúdo e os parâmetros de posicionamento padrão](gaze-and-commit.md)). 

Embora o conteúdo possa ocasionalmente precisar ser visto a uma distância inferior a 1 m, recomendamos que você nunca apresente hologramas a uma distância inferior a 40 cm. Portanto, recomendamos começar a **esmaecer o conteúdo a 40 cm e colocar um plano de recorte de renderização a 30 cm** para evitar objetos mais próximos.

É mais provável que os objetos que se movem em profundidade produzam desconforto, devido ao conflito entre vergência e acomodação, em comparação com os objetos fixos. Da mesma forma, exigir que os usuários alternem rapidamente entre o foco próximo e o foco distante (por exemplo, devido a um holograma pop-up que exija uma interação direta) pode causar desconforto e fadiga visuais. **É necessário tomar cuidado extra para minimizar a frequência com que os usuários: veem o conteúdo que se move em profundidade; ou alternam rapidamente o foco entre os hologramas próximos e distantes**. 

### <a name="other-considerations-for-hololens-2-and-near-interaction-distances"></a>Outras considerações sobre o HoloLens 2 e distâncias de interação próxima

Ao criar um conteúdo para interação direta (próxima) no HoloLens 2 ou **em qualquer aplicativo no qual o conteúdo precise ser posicionado a uma distância inferior a 1 m, é necessário tomar cuidado extra para garantir o conforto do usuário**. As chances de desconforto devido ao conflito entre vergência e acomodação aumentam exponencialmente com a redução da distância de visualização. Além disso, os usuários podem sentir um aumento do desfoque ao ver um conteúdo em distâncias de interação próxima; portanto, recomendamos testar o conteúdo renderizado na zona de posicionamento ideal de holograma e em uma distância mais curta (a menos de 1,0 m até o plano de recorte) para verificar se ele permanece nítido e confortável para visualização. 

**Recomendamos criar um “orçamento de profundidade” para aplicativos com base no tempo em que um usuário deverá ver o conteúdo que está próximo (a menos de 1,0 m) e que se move em profundidade**. Um exemplo é evitar colocar o usuário nessas situações mais de 25% do tempo. Se o orçamento de profundidade for excedido, recomendaremos um teste de usuário cuidadoso para garantir que ela continue sendo uma experiência confortável. 

Em geral, também recomendamos um teste cuidadoso para garantir que todos os requisitos de interação (por exemplo, velocidade de movimento, acessibilidade etc.) em distâncias de interação próxima continuem sendo confortáveis para os usuários. 

### <a name="guidance-for-immersive-devices"></a>Diretrizes para dispositivos imersivos

Para dispositivos imersivos, as diretrizes e as melhores práticas do HoloLens ainda se aplicam, mas os valores específicos da zona de conforto são deslocados, dependendo da distância focal do capacete. Em geral, as distâncias focais para esses capacetes ficam entre 1,25 m e 2,5 m. Em caso de dúvida, evite renderizar objetos de interesse muito próximo aos usuários e, em vez disso, tente manter a maior parte do conteúdo a 1 m de distância ou mais.

## <a name="interpupillary-distance-and-vertical-offset"></a>Distância interpupilar e deslocamento vertical

Ao ver o conteúdo digital em HMDs (capacetes de realidade virtual), a posição dos olhos de um visualizador em relação à posição do capacete de conteúdo digital é crítica. Especificamente, a [DIP](https://en.wikipedia.org/wiki/Pupillary_distance) (distância interpupilar) e o DV (deslocamento vertical) são importantes para a visualização confortável de conteúdo digital em HMDs. 

DIP refere-se à distância entre as pupilas ou a parte central dos olhos de um indivíduo. DV refere-se ao deslocamento vertical potencial do conteúdo digital mostrado para cada olho relativo ao eixo horizontal dos olhos do visualizador (particularmente, isso NÃO é o mesmo que deslocamento horizontal ou disparidade binocular). Uma correspondência incorreta entre um ou ambos os fatores e um usuário individual pode agravar os efeitos do desconforto causado pelo conflito entre vergência e acomodação, podendo, até mesmo, causar desconforto quando esse conflito é minimizado (por exemplo, para o conteúdo exibido na distância focal de 2,0 m do HoloLens). 

### <a name="guidance-for-holographic-devices"></a>Diretrizes para dispositivos holográficos

#### <a name="hololens-1st-gen"></a>HoloLens (1ª geração)

Para o HoloLens (1ª geração), a DIP é estimada e definida durante a [calibragem do dispositivo](/hololens/hololens-calibration). Para os novos usuários em um dispositivo já configurado, a calibragem precisa ser executada ou a DIP precisa ser definida manualmente. O DV depende totalmente do ajuste do dispositivo. Especificamente, para minimizar o DV, o dispositivo precisa estar apoiado na cabeça de um usuário, de modo que os capacetes estejam nivelados com o eixo dos olhos. 

#### <a name="hololens-2"></a>HoloLens 2

Para o HoloLens 2, a DIP é estimada e definida durante a [calibragem](/hololens/hololens-calibration) do olho/do dispositivo. Para os novos usuários em um dispositivo já configurado, a calibragem precisa ser executada para garantir que a DIP seja definida corretamente. O DV é levado em conta automaticamente no HoloLens 2. 

### <a name="guidance-for-immersive-devices"></a>Diretrizes para dispositivos imersivos

Os HMDs imersivos do Windows Mixed Reality não têm nenhuma calibragem automática para DIP ou DV. A DIP pode ser definida manualmente no software (nas configurações do Portal de Realidade Misturada, confira [calibragem](/hololens/hololens-calibration)) ou alguns HMDs têm um controle deslizante mecânico que permite ao usuário ajustar o espaçamento das lentes para uma posição confortável que corresponda aproximadamente à DIP. 

## <a name="rendering-rates"></a>Taxas de renderização

Os aplicativos de realidade misturada são únicos, porque os usuários podem se mover livremente no mundo e interagir com o conteúdo virtual como se fossem objetos reais. Para manter essa impressão, é essencial renderizar os hologramas de modo que pareçam estáveis no mundo e sejam animados perfeitamente. A renderização em um [mínimo de 60 FPS (quadros por segundo)](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) ajuda a atingir essa meta. Há alguns dispositivos de Realidade Misturada que dão suporte à renderização em taxas de quadros maiores que 60 FPS e, para esses dispositivos, é recomendável executar a renderização nas taxas de quadros mais altas, a fim de proporcionar uma experiência do usuário ideal.

**Aprofundamento**

Para desenhar hologramas e fazer com que pareçam [estáveis no mundo real ou virtual](../develop/platform-capabilities-and-apis/hologram-stability.md), os aplicativos precisam renderizar imagens partindo da posição do usuário. Como a renderização de imagem leva tempo, o HoloLens e outros dispositivos do Windows Mixed Reality preveem o local em que a cabeça de um usuário estará quando as imagens forem mostradas nos capacetes. Esse algoritmo de previsão é uma aproximação. Os algoritmos e o hardware do Windows Mixed Reality ajustam a imagem renderizada para considerar a discrepância entre a posição prevista e a posição real da cabeça. Esse processo faz com que a imagem vista pelo usuário pareça como se tivesse sido renderizada na localização correta e os hologramas pareçam estáveis. As atualizações funcionam melhor para pequenas alterações na posição da cabeça e não podem considerar por completo algumas diferenças de imagens renderizadas, como as causadas por movimento-paralaxe.

**Ao executar a renderização em uma taxa de quadros mínima de 60 FPS, você está fazendo duas coisas para ajudar a tornar os hologramas estáveis:**
1. Reduzir a aparência de trepidação, que é caracterizada pelo movimento irregular e por imagens duplas. Um movimento mais rápido do holograma e taxas de renderização mais baixas estão associados a uma trepidação mais acentuada. Portanto, a tentativa de sempre manter 60 FPS (ou a taxa máxima de renderização do dispositivo) ajudará a evitar a trepidação na movimentação dos hologramas.
2. Minimizar a latência geral. Em um mecanismo com um thread de jogo e um thread de renderização executados em sincronia, a execução em 30 FPS pode adicionar 33,3 ms de latência extra. Ao reduzir a latência, isso diminui o erro de previsão e aumenta a estabilidade do holograma.

**Análise de desempenho**

Há diferentes ferramentas que podem ser usadas para submeter a benchmark a taxa de quadros do aplicativo, como:
* GPUView
* Depurador de Gráficos do Visual Studio
* Criadores de perfil incorporados em mecanismos 3D, como o Depurador de Quadros no Unity

## <a name="self-motion-and-user-locomotion"></a>Automovimento e locomoção do usuário

A única limitação é o tamanho do espaço físico; caso você deseje permitir que os usuários se movimentem em uma distância maior no ambiente virtual do que é possível nas salas reais, uma forma de movimento puramente virtual precisará ser implementada. No entanto, um movimento virtual sustentado que não corresponde ao movimento físico e real do usuário pode, muitas vezes, induzir o enjoo de movimento. Esse resultado é devido às *indicações visuais* para o automovimento do *mundo virtual* em conflito com as [indicações vestibulares](https://en.wikipedia.org/wiki/Vestibular_system) para o automovimento proveniente do *mundo real*.

A boa notícia é que há dicas para implementar a locomoção do usuário que podem ajudar a evitar o problema:
* Sempre coloque o usuário no controle dos movimentos que ele faz; o automovimento inesperado gera problemas
* Os humanos são sensíveis à direção da gravidade. Portanto, especialmente, os movimentos verticais não iniciados pelo usuário devem ser evitados.

### <a name="guidance-for-holographic-devices"></a>Diretrizes para dispositivos holográficos

Um método para permitir que o usuário se mova para outra localização em um ambiente virtual grande é dar a impressão de que ele está movendo um objeto pequeno na cena. Esse efeito pode ser obtido da seguinte maneira:
   1. Forneça uma interface na qual o usuário possa selecionar um ponto no ambiente virtual para onde deseja se mover.
   2. Após a seleção, reduza a renderização da cena para um disco em torno do ponto desejado.
   3. Enquanto mantém o ponto selecionado, permita que o usuário o mova como se fosse um objeto pequeno. O usuário poderá então mover a seleção para perto dos pés.
   4. Depois de anular a seleção, retome a renderização da cena inteira.

### <a name="guidance-for-immersive-devices"></a>Diretrizes para dispositivos imersivos

A abordagem anterior do dispositivo holográfico não funciona tão bem em um dispositivo imersivo, porque exige que o aplicativo renderize um vazio preto grande ou outro ambiente padrão ao mover o “disco”. Esse tratamento desfaz a percepção de imersão de uma pessoa. Um truque para a locomoção do usuário em um headset imersivo é a abordagem de “intermitência”. Essa implementação fornece ao usuário o controle sobre o movimento que ele faz e oferece uma breve impressão do movimento, mas faz com que ele seja tão breve que há uma menor probabilidade de que o usuário se sinta desorientado pelo automovimento virtual:
   1. Forneça uma interface na qual o usuário possa selecionar um ponto no ambiente virtual para onde deseja se mover.
   2. Na seleção, comece um movimento simulado rápido (100 m/s) em direção a essa localização enquanto esmaece rapidamente a renderização.
   3. Aplique o fade in à renderização novamente depois de concluir a conversão.

## <a name="heads-up-displays"></a>Painéis transparentes

Em jogos de tiros em primeira pessoa, os HUDs (painéis transparentes) apresentam informações persistentemente presentes, como condição do jogador, minimapas e estoques diretamente na tela. Os HUDs funcionam bem para manter o jogador informado sem a intrusão na experiência de jogo. Em experiências de realidade misturada, os HUDs têm o potencial de causar um desconforto significativo e precisam ser adaptados para o contexto mais imersivo. Especificamente, os HUDs que são rigidamente bloqueados em relação à orientação da cabeça do usuário provavelmente produzirão desconforto. Se um aplicativo exigir um HUD, recomendaremos o bloqueio de *corpo* em vez do bloqueio de cabeça. Esse tratamento pode ser implementado como um conjunto de exibições que são convertidas imediatamente com o usuário, mas não giram com a cabeça dele até que um limite de rotação seja atingido. Depois que essa rotação é atingida, o HUD pode se reorientar para apresentar as informações dentro do campo de visão do usuário. Evite implementar a rotação de 1:1 do HUD e a conversão com base nos movimentos da cabeça do usuário.

## <a name="text-legibility"></a>Legibilidade do texto

Uma legibilidade ideal do texto pode ajudar a reduzir o cansaço visual e manter o conforto do usuário, especialmente em aplicativos ou cenários que exigem que os usuários façam leituras com um HMD. A legibilidade do texto depende de vários fatores, incluindo:
* Propriedades de vídeo, como densidade de pixels, brilho e contraste. 
* Propriedades de lente, como aberração cromática
* Propriedades de texto/fonte, como peso, espaçamento, serifas e cor da fonte/da tela de fundo.  

Em geral, recomendamos testar aplicativos específicos quanto à legibilidade e ampliar o máximo possível os tamanhos das fontes para uma experiência confortável. Encontre diretrizes mais detalhadas para dispositivos holográficos e imersivos nas páginas [Tipografia](typography.md) e [Texto no Unity](../develop/unity/text-in-unity.md).

## <a name="holographic-frame-considerations"></a>Considerações sobre quadros holográficos

Para experiências de Realidade Misturada com objetos grandes ou muitos objetos, é crucial considerar a quantidade de movimentos de cabeça e pescoço necessária para interagir com o conteúdo. As experiências podem ser divididas em três categorias em termos de movimento da cabeça: 
* **Horizontal** (para os lados)
* **Vertical** (para cima e para baixo)
* **Imersiva** (horizontal e vertical)
 
Quando possível, limite a maioria das interações a categorias horizontais ou verticais, de preferência, com a maioria das experiências ocorrendo no centro do quadro holográfico, enquanto a cabeça do usuário está em uma posição neutra. Evite interações que façam com que o usuário mova constantemente a visão para uma posição não natural da cabeça (por exemplo, sempre olhar para cima para acessar uma interação básica de menu).

![A região ideal para o conteúdo é de 0 a 35 graus abaixo do horizonte](images/optimal-field-of-view-2.png)<br>
*A região ideal para o conteúdo é de 0 a 35 graus abaixo do horizonte*

O movimento horizontal da cabeça é mais adequado para interações frequentes, enquanto os movimentos verticais devem ser reservados para eventos incomuns. Por exemplo, uma experiência que envolva uma longa linha de tempo horizontal deve limitar o movimento vertical da cabeça para interações (como olhar para baixo em um menu).

Considere a possibilidade de incentivar a movimentação de corpo completo, em vez de apenas a movimentação da cabeça, colocando objetos em torno do espaço do usuário. Ao projetar experiências com a movimentação de objetos ou objetos grandes, preste atenção especial ao movimento da cabeça, especialmente quando as experiências exigirem um movimento frequente ao longo dos eixos horizontal e vertical.

## <a name="gaze-direction"></a>Direção do foco

Para evitar o cansaço visual e cervical, o conteúdo deve ser projetado de modo a evitar o excesso de movimentos visuais e cervicais.
* **Evite** ângulos de foco superiores a 10 graus acima do horizonte (movimento vertical)
* **Evite** ângulos de foco superiores a 60 graus abaixo do horizonte (movimento vertical)
* **Evite** rotações de pescoço superiores a 45 graus fora do centro (movimento horizontal)

Consideramos que o ângulo de foco ideal (repouso) está entre 10 e 20 graus abaixo do horizonte, pois a cabeça tende a se inclinar um pouco para baixo, principalmente durante as atividades.

## <a name="arm-positions"></a>Posições do braço

A fadiga muscular pode se acumular quando é esperado que os usuários mantenham uma mão levantada durante toda uma experiência. Também pode ser cansativo exigir que o usuário faça gestos de fechar e abrir os dedos indicador e polegar repetidamente por longas durações. Portanto, recomendamos que as experiências evitem a exigência de uma entrada de gesto constante e repetida. Essa meta pode ser alcançada incorporando pequenos intervalos ou oferecendo uma combinação de entrada de gesto e fala para interagir com o aplicativo.

## <a name="see-also"></a>Veja também
* [Foco](gaze-and-commit.md)
* [Estabilidade do holograma](../develop/platform-capabilities-and-apis/hologram-stability.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Quadro holográfico](holographic-frame.md)
* [Calibragem](/hololens/hololens-calibration)
