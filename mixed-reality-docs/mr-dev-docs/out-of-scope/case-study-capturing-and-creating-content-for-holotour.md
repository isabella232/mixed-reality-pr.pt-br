---
title: Estudo de caso – HoloTour
description: Explore o estudo de caso do aplicativo HoloTour e veja o processo de captura e criação de seu conteúdo.
author: dannyaskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, Windows Mixed Reality
ms.openlocfilehash: 7e9bc2078e90b0f0cd98cf0612b583c06b2d51b400d682d3aff71e59eed620a4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202184"
---
# <a name="case-study---holotour"></a>Estudo de caso – HoloTour

O HoloTour para Microsoft HoloLens fornece viagens pessoais 3D imersivas de localizações em todo o mundo. Conforme os designers, os criadores, os produtores, os designers de áudio e os desenvolvedores que trabalham nesse projeto descobriram, a criação de uma renderização 3D real de um local conhecido leva uma mistura exclusiva de assistentes criativos e tecnológicos. Este estudo de caso explica o processo de captura e criação do conteúdo usado para o HoloTour.

## <a name="the-tech"></a>A tecnologia

Com o HoloTour, queríamos tornar possível que as pessoas visitam alguns dos destinos mais incríveis do mundo, como [asruelas](https://en.wikipedia.org/wiki/Machu_Picchu) de Charles Meio no Equador ou a moderna [DayLa Naspota](https://en.wikipedia.org/wiki/Piazza_Navona) na Itália, desde suas próprias salas de estar. Nossa equipe fez com que a meta do HoloTour fosse "fazer com que você se sinta realmente lá". A experiência precisava ser mais do que apenas imagens ou vídeos. Aproveitando a tecnologia exclusiva de exibição, acompanhamento e áudio HoloLens acreditamos que poderíamos praticamente transportá-lo para outro lugar. Precisaríamos capturar a visão, os sons e a geometria tridimensional de cada local visitado e, em seguida, recriar isso em nosso aplicativo.

Para fazer isso, precisamos de um equipamento de câmera de 360° com captura de áudio direcional. Ele precisava capturar em resolução extremamente alta, para que as imagens parecesse nítidos quando tocadas em um HoloLens e as câmeras precisariam ser posicionadas próximas para minimizar a inging artifacts. Queríamos cobertura esférica completa, não apenas ao longo do horizonte, mas acima e abaixo de você também. O equipamento também precisava ser portátil para que poderíamos adoá-lo em todo o mundo. Avaliamos as opções disponíveis e percebemos que elas simplesmente não eram boas o suficiente para perceber nossa visão, seja devido à resolução, ao custo ou ao tamanho. Se não conseguimos encontrar um equipamento de câmera que atendia às nossas necessidades, precisaríamos criar uma por conta própria.

### <a name="building-the-rig"></a>Criando o caminhão

A primeira versão, feita por meio de fitas Velcro, fita de fita e 14 câmeras GoPro, era algo do que MacGyver teria sido desapropriado. Depois de revisar tudo, desde soluções de baixo nível até equipamentos personalizados, as câmeras GoPro eram, em última análise, a melhor opção para nós, pois eram pequenas, acessíveis e tinham armazenamento de memória fácil de usar. O fator forma pequeno era especialmente importante porque nos permitia colocar câmeras bastante próximas – quanto menor a distância entre as câmeras, menor será o número de artefatos de ing. Nossa disposição exclusiva da câmera nos  permitiu obter cobertura de esfera completa, além de sobreposição suficiente para alinhar as câmeras de forma inteligente e suavizar alguns artefatos durante o processo de posição.

Aproveitar as [funcionalidades de som](../design/spatial-sound.md) espacial HoloLens é essencial para criar uma experiência de imersão muito real. Utilizamos uma matriz de quatro microfones embaixo das câmeras no tripod, que capturaria o som da localização da câmera em quatro direções, dando-nos informações suficientes para criar sons espaciais em nossas cenas.

![Nossa plataforma de câmera de 360° configurada para a partida fora do Pantheon.](images/camera-pantheon-200px.png)

Nossa plataforma de câmera de 360° configurada para a partida fora do Pantheon. 


Testamos nosso equipamento em casa, levando-o até Rattlesnake Ridge perto de Seattle, capturando os cenários na parte superior da escalada. O resultado, embora significativamente menos polido do que os locais que você vê no HoloTour hoje, nos deu confiança de que nosso design de equipamento era bom o suficiente para fazer você se sentir realmente lá.

Atualizamos nosso equipamento de Velcro para uma casa de câmera impressa em 3D e compramos pacotes de bateria externos para as câmeras GoPro para simplificar o gerenciamento de bateria. Em seguida, fizemos um teste mais extensivo, viajando até São Francisco para criar um tour pela costa da cidade e pela ponte golden gate. Esse equipamento de câmera é o que utilizamos para a maioria de nossas capturas dos locais que você visita no HoloTour.

![O equipamento de câmera de 360°, que está sendo ressaludo em Sua Casa.](images/camera-machu-pichu-500px.png)

O equipamento de câmera de 360°, que está sendo ressaludo em Sua Casa. 

## <a name="behind-the-scenes"></a>Nos bastidores

Antes da viagem, precisávamos descobrir quais locais queríamos incluir em nosso tour virtual. Rome foi o primeiro local que pretendemos enviar e queríamos fazer isso certo, portanto, decidimos fazer uma viagem de reconhecimento com antecedência. Enviamos uma equipe de seis pessoas, incluindo criadores, designers e produtores, para uma visita pessoalmente aos sites que estávamos considerando. A viagem levou cerca de 9 dias – 2,5 para viagem, o restante para viagem. (Para o Paulo ª, optamos por não fazer uma viagem de scout, pesquisando com antecedência e reservando alguns dias de buffer para o filme.)

Enquanto estava em Rome, a equipe fez fotos de cada área e anotou fatos interessantes, bem como considerações práticas, como como é difícil viajar para cada ponto e como seria difícil fazer o filme devido a público ou restrições. Isso pode parecer uma férias, mas é muito trabalho. Os dias começaram no início da manhã e continuariam sem parar até a noite. Todas as noite, as imagens foram carregadas para a equipe de volta em Seattle para revisão. 

![Nossa equipe de captura em Rome.](images/holotour-filming-crew-rome-500px.jpg) 

Nossa equipe de captura em Rome. 


Depois que a viagem de scout foi concluída, foi feito um plano final para a viagem real. Isso exigia uma lista detalhada de onde estávamos indo para o filme, em que dia e em que hora. Todos os dias é caro, portanto, essas viagens precisavam ser eficientes. Reservamos guias e manipuladores em Rome para nos ajudar e ser totalmente usados todos os dias, desde antes do sol até o fim do sol. Precisamos obter a melhor gravação possível para que você se sinta realmente lá.

### <a name="capturing-the-video"></a>Capturando o vídeo

Fazer algumas coisas simples durante a captura pode facilitar muito o pós-processamento. Por exemplo, sempre que você unir imagens de várias câmeras, acabará com artefatos visuais porque cada câmera tem uma exibição ligeiramente diferente. Quanto mais próximos os objetos são da câmera, maior será a diferença entre as exibições e maior será o tamanho dos artefatos de ing. Esta é uma maneira fácil de visualizar o problema: mantenha o dedo polegar para cima na frente do rosto e veja-o com apenas um olho. Agora, alternar os olhos. Você verá que o polegar parece mover-se em relação à plano de fundo. Se você manter o dedo polegar mais longe do rosto e repetir o experimento, o polegar parece será menor. Esse movimento aparente é semelhante ao problema de inging que encontramos: seus olhos, como nossas câmeras, não veem exatamente a mesma imagem porque estão separados por um pouco de distância.

Como é muito mais fácil evitar os piores artefatos durante a reação do que corrigi-los no pós-processamento, tentamos manter as pessoas e as coisas longe da câmera na expectativa de que poderíamos eliminar a necessidade de se fechar objetos. Manter uma limpeza grande em torno de nossa câmera provavelmente foi um dos maiores desafios que tínhamos durante a gravação e precisamos ser criativos para fazer isso funcionar. Trabalhar com guias locais foi uma grande ajuda no gerenciamento de público, mas também descobrimos que o uso de sinais e, às vezes, pequenos cones ou pacotes de bean, para marcar nosso espaço de vigilância foi razoavelmente eficaz, especialmente porque precisamos apenas obter uma pequena quantidade de imagens em cada local. Geralmente, a melhor maneira de obter uma boa captura era apenas chegar muito cedo pela manhã, antes da maioria das pessoas aparecer.

Algumas outras técnicas de captura úteis vêm diretamente de práticas de filmes tradicionais. Por exemplo, utilizamos um cartão de correção de cor em todas as nossas câmeras e capturamos fotos de referência de texturas e objetos que talvez precisemos mais tarde. 

![Um corte aproximado de Clara Nci mostrando o cartão de correção de cor.](images/rough-cut-machu-picchu-500px.png)

Um corte aproximado de imagens do Pantheon antes da cortagem.

### <a name="processing-the-video"></a>Processando o vídeo

A captura de conteúdo de 360° é apenas a primeira etapa— muitos processamentos são necessários para converter as imagens de câmera brutas que capturamos nos ativos finais que você vê no HoloTour. Quando voltarmos para casa, precisávamos pegar o vídeo de 14 feeds de câmera diferentes e transformá-lo em um único vídeo contínuo com artefatos mínimos. Nossa equipe de arte usou várias ferramentas para combinar e melhorar as imagens capturadas e desenvolvemos um pipeline para otimizar o processamento tanto quanto possível. As imagens tinham que ser reunidas, corrigidas por cores e, em seguida, compostas para remover elementos e artefatos de distração ou para adicionar uma saúde suplementar de vida e movimento, tudo isso com o objetivo de aprimorar essa sensação de realmente estar lá.

![Um corte aproximado de imagens do Pantheon antes da cortagem.](images/rough-cut-pantheon-500px.png)

Um corte aproximado de imagens do Pantheon antes da cortagem. 


Para unir os vídeos, utilizamos uma ferramenta chamada [PTGui](https://www.ptgui.com/) e a integramos ao nosso pipeline de processamento. Como parte do pós-processamento, extraímos quadros ainda de nossos vídeos e encontramos um padrão de inging que era bom para um desses quadros. Em seguida, aplicamos esse padrão a um plug-in personalizado que escrevemos que permitia aos nossos videoclipes ajustar e ajustar o padrão de inging diretamente durante a composição em Efeitos Após. 

![Captura de tela de PTGui mostrando as gravações do Pantheon.](images/stitching-tool-pantheon-500px.png)

Captura de tela de PTGui mostrando as gravações do Pantheon. 


### <a name="video-playback"></a>Reprodução de vídeo

Após a conclusão do processamento das imagens, temos um vídeo contínuo, mas ele é muito grande, em torno de 8K de resolução. A decodificação de vídeo é cara e há muito poucos computadores que podem lidar com um vídeo de 8K, portanto, o próximo desafio foi encontrar uma maneira de reproduzir esse vídeo novamente HoloLens. Desenvolvemos várias estratégias para evitar o custo de decodificação, fazendo com que o usuário se sinta como se estivesse exibindo todo o vídeo.

A otimização mais fácil é evitar a decodificação de partes do vídeo que não mudam muito. Escrevemos uma ferramenta para identificar áreas em cada cena que têm pouco ou nenhum movimento. Para essas regiões, mostramos uma imagem estática em vez de decodificar um vídeo para cada quadro. Para tornar isso possível, dividimos o vídeo maciço em partes muito menores.

Também fizemos com que cada pixel decodificado fosse usado com mais eficiência. Experimentamos técnicas de compactação para reduzir o tamanho do vídeo; dividimos as regiões de vídeo de acordo com os polígonos da geometria em que ela seria projetada; Ajustamos as UVs e reempacodemos os vídeos com base em quantos polígonos diferentes de detalhes foram incluídos. O resultado desse trabalho é que o que começou como um único vídeo de 8k se tornou em muitas partes que parecem quase ininteligíveis até que sejam projetadas corretamente na cena. Para um desenvolvedor de jogos que compreende o mapeamento de textura e o empacotamento de UV, isso provavelmente parece familiar. 

![Uma exibição completa do Pantheon antes das otimizações.](images/pantheon-before-optimization-500px.png) 

Uma exibição completa do Pantheon antes das otimizações. 


![A metade direita do Pantheon, processada para reprodução de vídeo.](images/pantheon-process-video-playback-500px.png) 

A metade direita do Pantheon, processada para reprodução de vídeo. 


![Exemplo de uma única região de vídeo após otimização e empacotamento.](images/single-video-region-after-optimization-500px.png) 

Exemplo de uma única região de vídeo após otimização e empacotamento. 


Outro truque usado foi evitar a decodificação de vídeo que você não está exibindo ativamente. No HoloTour, você só pode ver parte da cena completa em um determinado momento. Nós apenas decodificamos vídeos dentro ou logo fora do seu FOV (campo de exibição). À medida que você gira a cabeça, começamos a tocar as regiões do vídeo que agora estão em seu FOV e paramos de tocar aquelas que não estão mais dentro dele. A maioria das pessoas nem perceberá que isso está acontecendo, mas se você se voltar rapidamente, verá que o vídeo leva um segundo para começar. Enquanto isso, você verá uma imagem estática que, em seguida, esmaece de volta para o vídeo quando estiver pronto.

Para fazer essa estratégia funcionar, desenvolvemos um amplo sistema de reprodução de vídeo. Otimizamos o código de reprodução de baixo nível para tornar a alternação de vídeo extremamente eficiente. Além disso, precisamos codificar nossos vídeos de uma maneira especial para tornar possível alternar rapidamente para qualquer vídeo a qualquer momento. Esse pipeline de reprodução levou uma quantidade significativa de tempo de desenvolvimento para que o implementamos em estágios. Começamos com um sistema mais simples que era menos eficiente, mas permitia que designers e artista trabalhem na experiência e aprimoramos lentamente para um sistema de reprodução mais robusto que nos permitia enviar na barra de qualidade final. Esse sistema final tinha ferramentas personalizadas que criamos no Unity para configurar o vídeo dentro da cena e monitorar o mecanismo de reprodução.

### <a name="recreating-near-space-objects-in-3d"></a>Recriando objetos de espaço próximo em 3D

Os vídeos compõe a maior parte do que você vê no HoloTour, mas há vários objetos 3D que aparecem perto de você, como a pintura em Holograma, o balão fora do Pantheon ou o balão de ar quente em que você está para cenas aéreas. Esses objetos 3D são importantes porque a percepção de profundidade humana é muito boa de perto, mas não muito boa longe. Podemos sair com o vídeo à distância, mas para permitir que os usuários percoram seu espaço e sintam que estão realmente lá, os objetos próximos precisam de profundidade. Essa técnica é semelhante ao tipo de coisa que você pode ver em um acervo de histórico natural– imagine uma diorama que tem paisagem física, plantas e animais em primeiro plano, mas é recriada em uma pintura fosca mascarada inteligentemente em segundo plano.

Alguns objetos são simplesmente ativos 3D que criamos e adicionamos à cena para aprimorar a experiência. A pintura e o balão de ar quente se enquadram nessa categoria porque eles não estavam presentes quando filmemos. Semelhante aos ativos de jogos, eles foram criados por um artista 3D em nossa equipe e com textura adequada. Os colocaremos em nossas cenas perto de onde você está, e o mecanismo de jogo pode renderizar os dois HoloLens exibidos para que eles apareçam como um objeto 3D.

Outros ativos, como os que estão fora do Pantheon, são objetos reais que existem nos locais em que estamos gravando vídeo, mas para colocar esses objetos fora do vídeo e em 3D, precisamos fazer várias coisas.

Primeiro, precisamos de informações adicionais sobre cada objeto. Enquanto estava na localização para a captura, nossa equipe capturou muitas imagens de referência desses objetos, de modo que poderíamos ter imagens detalhadas suficientes para recriar com precisão as texturas. A equipe também realizou uma verificação [de fotogrametria,](https://en.wikipedia.org/wiki/Photogrammetry) que constrói um modelo 3D de dezenas de imagens 2D, nos dando um modelo aproximado do objeto em escala perfeita.

À medida que processam nossas imagens, os objetos que serão substituídos posteriormente por uma representação 3D são removidos do vídeo. O ativo 3D é baseado no modelo de fotogrametria, mas limpo e simplificado por nossos artista. Para alguns objetos, podemos usar partes do vídeo , como a textura da água na casa, mas a maioria dos corpos agora é um objeto 3D, que permite que os usuários percebam a profundidade e andem em torno dela em um espaço limitado na experiência. Ter objetos de espaço próximo como esse aumenta muito a noção de realismo e ajuda a basear os usuários no local virtual. 

![Imagens de pantheon com a remoção do painel. Ele será substituído por um ativo 3D.](images/object-removal-pantheon-500px.png)

Imagens de pantheon com a remoção do painel. Ele será substituído por um ativo 3D.


## <a name="final-thoughts"></a>Considerações finais

Obviamente, havia mais para criar esse conteúdo do que o que discutimos aqui. Há algumas cenas , que chamamos de "perspectivas impossíveis", incluindo a corrida de balão de ar quente e a bicicleta no Colosseum, que teve uma abordagem mais criativo. Abordaremos isso em um estudo de caso futuro.

Esperamos que o compartilhamento de soluções para alguns dos maiores desafios que apresentamos durante a produção seja útil para outros desenvolvedores e que você esteja inspirado a usar algumas dessas técnicas para criar suas próprias experiências imersivas para HoloLens. (E se você fizer isso, compartilhe-o conosco no fórum [HoloLens Desenvolvimento de Aplicativos](https://forums.hololens.com/)!)

## <a name="about-the-authors"></a>Sobre os autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Seniory é</b> um desenvolvedor sênior que aprendeu mais sobre os equipamentos de câmera e a reprodução de vídeo do que ele acha possível ao trabalhar no HoloTour.</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Mateus Askew é</b> um Video Artist que fez com que sua jornada por Rome fosse o mais incrível possível.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> é um Designer de Áudio que garante que você possa experimentar o soundscape de cada destino que visitar, mesmo quando voltar no tempo.</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Ele é</b> um Diretor de Design que pesquisou e pesquisou locais, criou planos de viagem e direcionou a replicação no site.</td>
</tr>
</table>



## <a name="see-also"></a>Confira também
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
