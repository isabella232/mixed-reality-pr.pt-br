---
title: Como criar hologramas
description: Saiba mais sobre a realidade misturada por meio do novo aplicativo de hologramas de design da Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, kit de ferramentas de realidade misturada, hologramas, criação de hologramas, aprendizado, aplicativo de exemplo, headset de realidade misturada, headset de realidade virtual, o que é realidade virtual
ms.openlocfilehash: 2480b5e0b4dca502c746dad6f070226ffa8cd1f9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757754"
---
# <a name="the-making-of-designing-holograms"></a>A criação de hologramas de design

> [!NOTE]
> Aguarde uma pequena janela de carregamento para considerar todos os GIFs e vídeos incorporados nesta página.

Aprender a criar uma realidade misturada pode ser difícil porque a média nem sempre se traduz bem em processos de design 2D. Aqui na Microsoft, criamos um aplicativo gratuito para o HoloLens 2 para ajudá-lo a aprender os conceitos básicos do design de UX da realidade misturada em primeira mão. A abordagem exclusiva do aplicativo de criação de hologramas se aprofunda em comportamentos, dicas e recomendações de realidade misturada para ajudá-lo a criar aplicativos de HoloLens atraentes e incríveis. Baixe o aplicativo gratuitamente na Microsoft Store e aprenda com a equipe de design da realidade misturada da Microsoft!

> [!div class="nextstepaction"]
> [Baixar o aplicativo de criação de hologramas](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animado da cena de acompanhamento de cabeçalho na sala de demonstração de criação de holograma](images/designing-holograms/demo-room.gif)

*Projetando a sala de demonstração do holograma (também conhecida como a casa Doll)*

## <a name="designing-for-mixed-reality"></a>Projetando para realidade misturada

Como muitos de vocês, usei para criar aplicativos móveis. Vindo de um mundo de design 2D, que entra em total na computação espacial, onde tudo está agora no mundo, foi uma mudança significativa. Em realidade misturada, os aplicativos não são mais confinados para uma tela 2D; na verdade, eles são quase gratuitos, colocados no mundo real e interagindo com objetos reais.

Para mim, conectar experiências 3D a processos de design de 2D convencionais é o aspecto mais desafiador do desenvolvimento de realidade misturada. Em conversas com clientes, eu ouviria coisas como "sei quais recursos incluir e como colocá-los em funcionamento. É código, posso seguir os documentos e tutoriais, mas a experiência do usuário? Tantos recursos, diferentes opções de entrada, cenários diferentes e ambientes físicos, é muito difícil ".

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
- E o pior de todo um ambiente virtual altamente restrito por um campo de exibição.

Quando tentamos uma escala de 1:10, o resultado era uma visão fantástica de uma sala realista. Você poderia ver tudo o que estava acontecendo de qualquer ângulo ao mesmo tempo. O que era mais surpreendente é que a maioria dos testadores o achava muito mais imersiva para ver uma versão pequena, então eles nunca mudaram de volta para a escala 1:1. Então, decidimos realmente refazer a versão 1:1 e evitar o trabalho extra necessário para adaptar a interface do usuário e outros aspectos do aplicativo.

![Campo de exibição com 1:1 escala ](images/designing-holograms/1-1-scale.png)
 *do campo de exibição com escala de 1:1*

![Campo de exibição com 1:10 escala ](images/designing-holograms/1-10-scale.png)
 *do campo de exibição com escala de 1:10*

## <a name="using-mixed-reality-capture"></a>Usando a captura de realidade misturada

Um dos recursos mais característicos desse aplicativo é o uso da captura de realidade misturada para ensinar e demonstrar conceitos de design de realidade misturada.

A Microsoft tem um estúdio de captura de realidade misturada em San Francisco. A Microsoft também licencia essa tecnologia para outros estúdios, que incluem a dimensão de avatar em Washington D.C., metastage em Los Angeles, Dimension estúdios em Londres, SK Telecom in Seul e Volucap em Berlim. Você pode encontrar mais informações sobre nossa [estúdios de captura de realidade misturada aqui](https://www.microsoft.com/mixed-reality/capture-studios).

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*A seqüência bruta de Daniel Escudero de uma das câmeras 106 no estúdio de captura de realidade misturada em San Francisco.*

O processo de captura gera uma malha, Normals e texturas em quadros-chave, que podem ser entregues como arquivos OBJ/PNG para posterior produção ou pronto para reprodução como um arquivo MP4 compactado H. 264. Esses arquivos podem ser importados para projetos do Unity, inreal, nativo e WebXR. Os arquivos podem ser executados no Windows, iOS, Mac, Android, Magic Leap e PlayStation VR.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*O player de captura fornecido para analisar MP4s que contêm vídeo com malhas de áudio e incorporadas.*

## <a name="manipulating-captures-and-virtual-objects"></a>Manipulando capturas e objetos virtuais

As capturas de realidade misturadas produzem representações virtuais de pessoas ou animais, mas às vezes você pode precisar desses caracteres para interagir com outros objetos virtuais. Os dois exemplos a seguir mostram diferentes maneiras de manipularmos as cenas para alcançar esse efeito.

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

Quando começamos o design da interface do usuário, queríamos mostrar algumas das mágicas e possibilidades que os hologramas têm a oferecer. Simplesmente Mostrar janelas 2D estáticas e caixas de texto não se sente bem no mundo 3D. Muitas das possibilidades à mão simplesmente não aparecem, logo desde o início, decidimos sair dessa parte e fazer uso completo do espaço 3D Holographic.

Inicialmente, começamos com a adição de uma espessura aos painéis, ícones e informações de texto. Ainda assim, como um usuário, o que vejo é uma caixa de texto. Caixas de texto com imagens, mas não estamos lá. Além disso, usamos os sombreadores do MRTK (Kit de ferramentas de realidade misturada). Os sombreadores MRTK se tornaram uma ferramenta poderosa e usamos seus recursos de estêncil para adicionar profundidade negativa aos painéis. Isso significa que, em vez de adicionar elementos na frente de uma caixa de texto, os ícones agora aparecem atrás de um painel transparente. O que vejo agora como um usuário é algo que simplesmente não posso replicar no mundo real, e é aí que começou a Holographic mágica. Também como um usuário que eu não gosto muito de ler, eu já tenho muito no mundo físico.

Obviamente, os ícones funcionam muito melhor do que o texto simples, para fornecer uma orientação ainda mais poderosa, comecei a criar um conjunto de objetos animados e avatars, cada um deles dizendo uma pequena história sobre o que está sendo feito no respectivo cenário e como ele está sendo usado.

![GIF animado de um sistema de menus Holographic interativo](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a>Conceitos fundamentais

**Quadro holográfico**

![GIF animado de um usuário olhando o Dollhouse com o quadro Holographic realçado](images/designing-holograms/FOVandFOI.gif)

**Sistemas de coordenadas**

![GIF animado de um usuário que procura o Dollhouse com os sistemas de coordenadas realçados](images/designing-holograms/CoordinateSystems.gif)

**Acompanhamento ocular**

![GIF animado de um usuário olhando para hologramas fixos com o olho olhar Ray realçado](images/designing-holograms/EyeTracking.gif)

**Visualização da verificação de sala e mapeamento espacial**

![GIF animado de todas as superfícies dentro do Dollhouse que está sendo mapeado](images/designing-holograms/SpatialMapping.gif)

**Reconhecimento de cena**

![GIF animado de objetos no Dollhouse que está sendo reconhecido](images/designing-holograms/SceneUnderstanding.gif)

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

Um enorme agradecimento à equipe de design da realidade misturada por compartilhar tanto conhecimento e para o pessoal incrível da [teoria do objeto](https://objecttheory.com/) para ser um colega de equipe essencial em cada etapa do projeto. Obrigado por todos os talentos incríveis, pelo entusiasmo e pelo olho excepcional para o design.

> [!div class="nextstepaction"]
> [Baixar o aplicativo de criação de hologramas](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)