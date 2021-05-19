---
title: Como criar hologramas
description: Saiba mais sobre a Realidade Misturada por meio do novo aplicativo Designing Holograms da Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Kit de Ferramentas de Realidade Misturada, hologramas, Criação de Hologramas, aprendizado, aplicativo de exemplo, headset de realidade misturada, headset de realidade virtual, o que é realidade virtual
ms.openlocfilehash: 6e37c3f1ba98f202addb9c323632bca8bffae3b6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143630"
---
# <a name="the-making-of-designing-holograms"></a>A criação de hologramas de criação

> [!NOTE]
> Permita que uma pequena janela de carregamento dê conta de todos os GIFs e vídeos inseridos e interessantes nesta página.

Aprender a projetar para realidade misturada pode ser difícil porque a mídia nem sempre se traduz bem em processos de design 2D. Aqui na Microsoft, criamos um aplicativo gratuito para o HoloLens 2 para ajudá-lo a aprender os conceitos básicos do Design de UX de realidade misturada em primeira mão. A abordagem exclusiva do aplicativo Designing Holograms se envolve em comportamentos de realidade misturada, dicas e recomendações para ajudá-lo a criar aplicativos holoLens envolvente e incríveis por conta própria. Baixe o aplicativo gratuitamente no Microsoft Store e aprenda com a Equipe de Design de Realidade Misturada da Microsoft!

> [!div class="nextstepaction"]
> [Baixar o aplicativo Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animado da cena de acompanhamento de cabeça na sala de demonstração do Holograma de Criação](images/designing-holograms/demo-room.gif)

*Projetando a sala de demonstração do holograma (também conhecida como a casa da casa da casa)*

## <a name="designing-for-mixed-reality"></a>Projetando para realidade misturada

Como muitos de vocês, eu costumava criar aplicativos móveis. Proveniente de um mundo de design 2D, saltar para o mundo completo da computação espacial, em que tudo agora está no mundo, foi uma mudança significativa. Na realidade misturada, os aplicativos não são mais restritos a uma tela 2D; na verdade, eles são quase livres, colocados no mundo real e interagindo com objetos reais.

Para mim, conectar experiências 3D a processos convencionais de design 2D é o aspecto mais desafiador do desenvolvimento de realidade misturada. Em conversas com clientes, eu escutava coisas como "Eu sei quais recursos incluir e como au-los em funcionamento. É código, posso seguir os documentos e tutoriais, mas a experiência do usuário? Muitos recursos, diferentes opções de entrada, cenários diferentes e ambientes físicos, é muito difícil".

![Imagem do workshop de design do HoloLens 2 na ](images/designing-holograms/workshop.jpeg)
 *imagem de São Francisco do workshop de design do hololens 2 em San Francisco*

## <a name="an-opportunity-to-teach"></a>Uma oportunidade de ensinar

Não era óbvio a princípio, mas foi apresentada uma excelente oportunidade de usar realidade misturada como uma mídia para ensiná-la.

A criação de hologramas é uma experiência visual que explica conceitos e recomendações de design de realidade misturada. É apenas você e um professor virtual que demonstra conceitos de design de realidade misturada. Tudo é da perspectiva de uma terceira pessoa com a experiência firmemente em seu próprio espaço.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*Vídeo do trailer de design de hologramas*

## <a name="exploring-the-doll-house"></a>Explorando a casa Doll

A Doll House é o ambiente virtual que usamos em todo o aplicativo. O ambiente é uma sala em miniatura de 80 x 60 x 40 cm que contém os elementos básicos que a maioria das salas tem em comum, como paredes, lâmpadas, mobília, uma tabela e uma TV. A Doll House é a principal protagonist da experiência do aplicativo, portanto, precisávamos garantir que ela funcionasse muito bem em qualquer ambiente. Imagine-o como um pequeno espaço de demonstração para Visualizar todos os tipos de conceitos de realidade misturada.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Vídeo do comportamento de ajuste de Dollhouse*

### <a name="11-vs-110-prototypes"></a>protótipos de 1:1 x 1:10

Nossa suposição inicial era que 1:1 demonstrações seriam incríveis, quase como examinar um professor de vida real. O usuário veria tudo o que o professor vê em uma escala de vida real. No entanto, percebemos imediatamente que haveria alguns problemas:

- A maioria dos desenvolvedores executará seus aplicativos em escritórios ou salas menores do que a sala de demonstração e, portanto, não se ajustaria.
- As exibições são aditivas, o que significa que todo o ambiente virtual será sobreposto ao espaço de um usuário. Isso pode ficar confuso com duas tabelas, talvez duas vezes em sofás e as paredes que não se alinham.
- E o pior de tudo é um ambiente virtual muito restrito por um campo de exibição.

Quando tentamos uma escala mini 1:10, o resultado foi uma exibição de olho de pássaros incrível de uma sala realista. Você pode ver tudo o que estava acontecendo de qualquer ângulo ao mesmo tempo. O que foi mais surpreendente é que a maioria dos testadores acha muito mais imersivo ver uma versão pequena e, em seguida, eles nunca alternam de volta para a escala 1:1. Portanto, decidimos, na verdade, desmancar a versão 1:1 e evitar o trabalho extra necessário para adaptar a interface do usuário e outros aspectos do aplicativo.

![Campo de exibição com escala de 1:1 ](images/designing-holograms/1-1-scale.png)
 *Campo de exibição com escala de 1:1*

![Campo de exibição com escala de 1:10 ](images/designing-holograms/1-10-scale.png)
 *Campo de exibição com escala de 1:10*

## <a name="using-mixed-reality-capture"></a>Usando Captura de Realidade Misturada

Um dos recursos mais características desse aplicativo é o uso de Captura de Realidade Misturada ensinar e demonstrar conceitos de design de realidade misturada.

A Microsoft tem um Captura de Realidade Misturada studio em São Francisco. A Microsoft também licencia essa tecnologia para outros estúdios, que incluem Dimensão Avatar em Washington D.C., Metastage em Los Angeles, Dimension Studios em Londres, SK Telecom em Seul e Volucap em Beque. Você pode encontrar mais informações sobre nosso [Captura de Realidade Misturada Estúdios aqui.](https://www.microsoft.com/mixed-reality/capture-studios)

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*Imagens brutas de Daniel Escudero de uma das 106 câmeras no Captura de Realidade Misturada Studio em São Francisco.*

O processo de captura gera uma malha, normais e textura com keyframe, que podem ser entregues como arquivos OBJ/PNG para posterior pós-produção ou prontos para reprodução como um arquivo MP4 compactado H.264. Esses arquivos podem ser importados para projetos Unity, Unreal, Native e WebXR. Os arquivos podem ser executados no Windows, iOS, Mac, Android, Magic Leap e Vr Vr.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*O Player de Captura fornecido para analisar mp4s que contêm vídeo com áudio e malhas inseridas.*

## <a name="manipulating-captures-and-virtual-objects"></a>Manipulando capturas e objetos virtuais

As Capturas de Realidade Misturada produzem representações virtuais de pessoas ou animais, mas às vezes você pode precisar desses caracteres para interagir com outros objetos virtuais. Os dois exemplos a seguir mostram diferentes maneiras de manipularmos as cenas para alcançar esse efeito.

### <a name="head-gaze-adjustment"></a>Ajuste de olhar de cabeçalho

O ajuste Headgaze permite mover o cabeçalho de uma pessoa capturada em tempo de execução, o que significa que você pode ter uma face de captura para um usuário. Em nosso caso, nós o usamos para mostrar o campo de exibição e campo de interesse. O que você vê abaixo é um gameobject em movimento agindo como um destino para o olhar de cabeçalho examinar. À medida que movemos o destino do lado a lado, o início da captura é mostrado a seguir.

Usamos esse truque para garantir que a captura ociosa sempre se deparasse com os hologramas colocados em diferentes partes da casa Doll. 

![A cabeça da captura está sendo movida no tempo de execução após um gameobject de destino no Unity](images/designing-holograms/head-adjustment.gif)

*A cabeça da captura está sendo movida no tempo de execução após um gameobject de destino no Unity.*

### <a name="syncing-animated-objects"></a>Sincronizando objetos animados

A segunda, estava animando objetos para sincronizar com o movimento de uma captura. Em diferentes partes do aplicativo, importamos objs tivessem sequenciais de uma captura específica a cada cinco quadros. Os objs tivessem foram então animados na cena para garantir que correspondam ao quadro correspondente da captura. É um processo entediante de animação e enquadramento, mas o resultado é ótimo. Agora você pode ver uma interação de captura de realidade misturada com objetos não capturados.

![Animação sincronizada entre uma captura de realidade misturada e o painel da interface do usuário](images/designing-holograms/synced-objects.gif)

*Animação sincronizada entre uma captura de realidade misturada e o painel da interface do usuário*

### <a name="ui-creative-process"></a>Processo criativo da interface do usuário

Quando começamos o design da interface do usuário, queríamos mostrar algumas das mágicas e possibilidades que os hologramas têm a oferecer. Simplesmente Mostrar janelas 2D estáticas e caixas de texto não se sente bem no mundo 3D. Muitas das possibilidades em mãos simplesmente não aparecem, portanto, desde o início, decidimos sair dessa e fazer uso completo do espaço 3D holográfico.

Primeiro, começamos a adicionar alguma espessura aos painéis, ícones e informações de texto. Ainda assim, como usuário, o que vejo é uma caixa de texto. Caixas de texto com imagens, mas não estamos lá. Fizemos mais uso dos sombreadores do MRTK (Kit de Ferramentas de Realidade Misturada). Os sombreadores do MRTK se tornaram uma ferramenta poderosa e usamos seus recursos de estêncil para adicionar profundidade negativa aos painéis. Isso significa que, em vez de adicionar elementos na frente de uma caixa de texto, os ícones agora aparecem atrás de um painel transparente. O que vejo agora como um usuário é algo que não consigo mais replicar no mundo real e é aí que a mágica holográfica começou a acontecer. Além disso, como um usuário que realmente não gosto de ler, eu já faço muita coisa no mundo físico.

Obviamente, os ícones funcionam muito melhor do que o texto simples, para fornecer uma orientação ainda mais poderosa, então, eu começamos a criar um conjunto de objetos animados e avatars, cada um deles contando uma pequena história sobre o que está sendo feito no respectivo cenário e como ele está sendo usado.

![GIF animado de um sistema de menu holográfico interativo](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a>Conceitos fundamentais

**Acompanhamento de cabeça e acompanhamento ocular**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

**Acompanhamento de mão**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

**Reconhecimento espacial**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

**Quadro holográfico**

![GIF animado de um usuário que está observando a casa com o quadro holográfico realçada](images/designing-holograms/FOVandFOI.gif)

**Sistemas de coordenadas**

![GIF animado de um usuário que está observando a casa com os sistemas de coordenadas realçadas](images/designing-holograms/CoordinateSystems.gif)

**Acompanhamento ocular**

![GIF animado de um usuário observando hologramas estacionários com o raio de olhar realçada](images/designing-holograms/EyeTracking.gif)

**Visualização de varredura de sala e mapeamento espacial**

![GIF animado de todas as superfícies dentro da casa que está sendo mapeada](images/designing-holograms/SpatialMapping.gif)

**Reconhecimento de cena**

![GIF animado de objetos na casa que está sendo reconhecida](images/designing-holograms/SceneUnderstanding.gif)

**Apontar e confirmar com raios de mão**

![GIF animado de um usuário levantando sua mão com um raio de mão realçado](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a>Tempo "Experimente"

A criação de hologramas ensina conceitos de realidade misturada, mas também permite testá-los em sua sala. Depois de algumas dessas explicações, vamos pausar e levá-lo da casa Doll e em um momento interativo. Aqui estão alguns exemplos desses momentos interativos:

![GIF animado do quadro de acompanhamento à mão mostrando quando as mãos são detectadas e quando elas inserem o campo de exibição](images/designing-holograms/try-out-1.gif)

*O quadro de acompanhamento à mão mostrando quando as mãos são detectadas e quando elas inserem o campo de exibição.*

![GIF animado de interagir com a colisão de Crystals por meio de interação distante](images/designing-holograms/try-out-2.gif)

*Interagindo com a colisão de Crystals por meio de interação distante*

![GIF animado de explorar o capacidades de interação próxima](images/designing-holograms/try-out-3.gif)

*Explorando capacidades de interação próxima*

## <a name="about-the-team"></a>Sobre a equipe

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Escudero</b><br><i>Designer técnico líder</i><br>Dan é o diretor criativo da criação de hologramas e atualmente funciona como líder de design para a Academia de realidade misturada da Microsoft em São Francisco, e era um designer de uma das estúdios de realidade misturada da Microsoft em Londres.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>Martin Wettig</b><br><i>Artista 3D sênior</i><br>Martin lidera a arte 3D e o design da interface do usuário na criação de hologramas e era anteriormente um artista 3D sênior em um dos estúdios de realidade misturada da Microsoft em Berlim.</td>
</tr>
</table>

Um enorme agradecimento à equipe de design da realidade misturada por compartilhar tanto conhecimento e para o pessoal incrível da [teoria do objeto](https://objecttheory.com/) para ser um colega de equipe essencial em cada etapa do projeto. Agradecemos a todos por seu incrível talento, por sua paixão e pelo olhar excepcional pelo design.

> [!div class="nextstepaction"]
> [Baixar o aplicativo Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)