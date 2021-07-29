---
title: The Making of Galaxy Explorer for HoloLens 2
description: Saiba mais sobre como nossa equipe está atualizando o projeto de código aberto do Galaxy Explorer para HoloLens 2 no GitHub.
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: galaxy explorer, estudo de caso, projeto, exemplo, MRTK, Toolkit de Realidade Misturada, Unity, aplicativos de exemplo, aplicativos de exemplo, open-source, Microsoft Store, HoloLens, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 1e19f63f493eba2559cf60ef7c1224b7323ec825
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757064"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>A comação do Galaxy Explorer para HoloLens 2

![Logotipo do Novo Galaxy Explorer](../images/GalaxyExplorer2.jpg)


Bem-vindo ao aplicativo Atualizado do Galaxy Explorer HoloLens 2! [O Galaxy Explorer](/windows/mixed-reality/galaxy-explorer "Gerenciador do Galaxy") foi desenvolvido originalmente como um aplicativo de código aberto para HoloLens (primeira geração) por meio do programa Compartilhar sua ideia e é uma das primeiras experiências de realidade misturada que muitas pessoas tiveram. Agora estamos atualizando-o para as funcionalidades novas e interessantes [do HoloLens 2.](https://www.microsoft.com/hololens/hardware)

Como um dos [Estúdios de Realidade](galaxy-explorer-update.md#mixed-reality-studios)Misturada da Microsoft, geralmente desenvolvemos soluções de nível comercial e estamos desenvolvendo & testes em plataformas de destino em todo o processo de criação e desenvolvimento. Estamos nos preparando para este projeto usando as estruturas e ferramentas (como o [MRTK)](mrtk-getting-started.md)à medida que elas se tornam disponíveis para nós e para a comunidade, e queremos levar você para a corrida.

Assim como o Galaxy Explorer [original,](galaxy-explorer-update.md#meet-the-team) nossa equipe estará aberta para receber o projeto no GitHub para garantir que a comunidade tenha acesso completo. [](https://github.com/Microsoft/GalaxyExplorer) Também documentaremos nosso percurso aqui com transparência completa sobre como portamos do MRTK v1 para o MRTK v2, aprimoramos a experiência com novos recursos disponíveis no HoloLens 2 e garantimos que o Galaxy Explorer permanecesse uma experiência de várias plataformas. Se você estiver exibindo o Galaxy Explorer no HoloLens (primeira geração), HoloLens 2, um headset Windows Mixed Reality ou na área de trabalho do Windows 10, queremos garantir que você esteja aproveitando o percurso tanto quanto estamos!

Esta página será expandida conforme avançamos pelo projeto com links para artigos mais detalhados, código, artefatos de design e documentação adicional do MRTK para fornecer uma análise interna do projeto.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Baixar o aplicativo Microsoft Store no HoloLens 2
Se você tiver HoloLens 2, poderá baixar e instalar diretamente o aplicativo em seu dispositivo.

<a href='//www.microsoft.com/store/apps/9nblggh4q4jg?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="thinking-about-interactions"></a>Pensando em interações

Como um estúdio criativo, estávamos empolgados com o privilégio de portuar o Galaxy Explorer para HoloLens 2. Sabemos desde o início que queríamos que a experiência fosse um desafio do novo dispositivo e demonstrar que a realidade misturada é limitada apenas pela criatividade.

HoloLens 2 permite que os usuários toquem, compreendam e movam hologramas de maneiras que parecem naturais – eles respondem muito como objetos reais. Modelos de mão totalmente articulados são incríveis, pois permitem aos usuários fazer o que parece natural. Por exemplo, todos escolhem uma xícara um pouco diferente – e, em vez de impor uma maneira específica de fazer isso, HoloLens 2 permite que você faça isso da sua maneira.

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

Essa é uma alteração significativa das interfaces baseadas em Toque de Ar em dispositivos HoloLens primeira geração. Em vez de interagir com hologramas à distância, os usuários agora podem ficar "mais próximos e pessoais". Ao portar experiências existentes para HoloLens 2 ou planejar novas experiências, é importante se familiarizar com a manipulação direta de hologramas.

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>Manipulação direta versus as grandes distâncias no espaço

É uma experiência mágica entrar em contato, pegar um planeta e mantê-lo em suas mãos. O desafio com essa abordagem é o tamanho do sistema solar– ele é enorme! O usuário precisaria dar uma volta em seu quarto para se aproximar de cada planeta para interagir com ele.

Para permitir que os usuários interajam com objetos mais distantes, o MRTK oferece raios de mão que disparam do centro da mão do usuário, atuando como uma extensão da mão. Um cursor em forma de rosca é anexado ao final do raio para indicar onde o raio intersecções com um objeto de destino. O objeto sobre o cursor pode receber comandos gestuais da mão. 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

Na versão original do Galaxy Explorer, o usuário direcionaria um planeta com o cursor de olhar e, em seguida, tocaria no ar para chamá-lo mais próximo. A maneira mais fácil de portuar a experiência para HoloLens 2 é usar esse comportamento e usar raios de mão para selecionar planetas. Embora isso fosse funcional, isso nos deixou esperando mais.

### <a name="back-to-the-drawing-board"></a>De volta à estaca zero

Fizemos uma ideia do que poderia ser criado com base nas interações existentes. O raciocínio era: embora HoloLens 2 permita que os usuários interajam com hologramas de maneiras naturais e realistas, os hologramas são, por definição, não reais. Portanto, desde que uma interação seja abrangente para o usuário, não importa se essa interação seria possível com um objeto real ou não– podemos torná-la possível.

Um conceito que exploramos foi baseado na telekinesis – o poder de manipular objetos com a mente. Geralmente visto em filmes super-hero, uma pessoa alcançaria com a mente e chamaria um objeto em sua mão aberta. Começamos com a ideia um pouco mais e fizemos um esboço rápido de como o conceito poderia funcionar.

![Conceito para a interação de captura de força](images/ge-update-interactions-concept-force-grab.png)

O usuário apontaria o raio de mão em um planeta, o que forneceria comentários de destino. À medida que o usuário estende a mão aberta, o planeta seria esvasado para o usuário por uma força mágica até que ele fosse próximo o suficiente para agarrá-lo. Portanto, nosso nome para a interação: forçar a captura. Como o usuário esvaria o planeta com a mão aberta, ele retornaria novamente à sua lua.

### <a name="force-grab-prototyping"></a>Forçar a criação de protótipos de captura

Em seguida, criamos vários protótipos para testar o conceito: Como a interação se parece em geral? O objeto chamado deve parar na frente do usuário ou manter as mãos até ser colocado? O objeto chamado deve alterar o tamanho ou a escala ao ser chamado?

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>Implementando a captura de força no aplicativo

Quando tentamos a captura de força em planetas, percebemos que precisamos alterar a escala do sistema solar. Acabou que uma representação precisa e de tamanho médio do sistema solar é difícil para os usuários entenderem e navegarem– eles não sabem onde procurar. No entanto, uma representação de tamanho pequeno tornou alguns planetas muito pequenos para serem facilmente selecionados. Como resultado, o tamanho dos planetas e o espaçamento entre objetos solares foram projetados para se sentir confortável em uma sala de tamanho médio, mantendo a precisão relativa.

Durante os estágios posteriores do nosso sprint de desenvolvimento, tínhamos sorte o suficiente para ter colegas especialistas em Realidade Misturada do MSFT em casa, portanto, começamos a trabalhar para obter sua entrada como testadores especialistas e fazer iterações rápidas na interação de captura de força.

![Kam Kam testando um build de versão prévia do Galaxy Explorer](images/ge-update-user-testing.png)

Na imagem: Kam Kam, líder sênior de design, testando um trabalho em andamento do Galaxy Explorer.

### <a name="adding-affordances-for-targeting"></a>Adicionando recursos para direcionamento

Como experimentamos no HoloLens 2, descobrimos que, embora as novas interações sejam naturais e intuitivas, os hologramas permanecem os mesmos: sem peso ou reações de tactile. Como os hologramas não fornecem comentários naturais que os humanos estão acostumados a receber quando interagem com objetos, precisamos crie-los.

Falamos sobre os comentários visuais e de áudio que os usuários seriam fornecidos para os vários estágios de suas interações e, como o mecanismo de captura de força é fundamental para interagir com o Galaxy Explorer, fizemos muitas iterações. O objetivo era encontrar o equilíbrio certo de comentários visuais e de áudio para cada estágio da interação: concentrar-se no objeto pretendido, chamá-lo para o usuário e, em seguida, liberá-lo. O que aprendemos é que mais comentários visuais e de áudio foram necessários para reforçar a interação do que estávamos acostumados para HoloLens (primeira geração).

![Recursos visuais em planetas](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>Adicionando recursos para a captura à força
 
Depois de termos o mecanismo básico de captura de força com recursos visuais e de áudio, vimos como tornar a seleção de planetas mais amigável. Havia duas coisas principais a resolver: como o sistema solar é uma interface móvel 3D, há complexidade adicionada para os usuários aprenderem a direcionar objetos de forma consistente. Isso foi composto pelo fato de que o raio de mão é rápido na seleção de um objeto, fazendo com que os planetas se movam para o usuário incrivelmente rapidamente.

Abordamos isso com uma solução de três pronged. A primeira foi bastante intuitiva: reduza o processo de seleção para que os planetas se aproximarem do usuário em um ritmo mais natural. Depois que a velocidade foi ajustada, precisamos revisitar as responsabilidades visuais e de áudio, adicionando comentários de áudio à medida que o planeta acompanhava em direção ao usuário.

A segunda parte da solução era tornar a visualização de toda a interação de captura de força tangível. Visualizamos uma linha espesso que se move para o objeto de alvo quando o raio de mão se conecta a ele e, em seguida, traz o objeto de volta para o usuário , como um laço. 

![Recursos visuais de "laço" para a captura de força](images/ge-update-lasso-affordances.png)

Por fim, otimizamos a escala do sistema solar para que os planetas fossem grandes o suficiente para que o olhar do usuário e o raio de mão os direcionasse. 

Esses três aprimoramentos permitiram que os usuários façam seleções precisas, chamando planetas para eles de maneira intuitiva. Em geral, o efeito da captura de força final é uma experiência mais imersiva e interativa no sistema solar.

## <a name="spotlight-on-jupiter"></a>Destaque no Spotlight on Spotlight

A criação dos corpos solares da Via Leitena foi uma experiência incrível. Em particular, as características exclusivas de Sempre fazem com que seja uma visão à toa. É o maior e mais colorido do gas gas e contém mais massa do que todos os outros planetas combinados. Seu tamanho completo e as faixas mesmerizadoras de movimentos e dinâmicas de nuvem são perfeitos para atenção especial.

### <a name="geometry-and-meshes"></a>Geometria e malhas

Como um robô gasoso, os shells externos de Gaseous são formados por camadas gasosas. A combinação de sua velocidade de rotação rápida, troca de calor interna e força Coriolis cria camadas coloridas e fluxos que se formam em faixas de nuvem e vortices. Capturar essa complexidade era fundamental na criação de nosso sistema solar.

Ficou imediatamente claro que o uso de técnicas de visualização, como simulações fluidas e texturas animadas com fluxos pré-computados, estava fora de questão. O poder de computação necessário para simular isso em combinação com todo o resto acontecendo simultaneamente teria impactos prejudiciais significativos no desempenho. 

![Visão geral do objeto Det.](images/ge-update-jupiter-shells-complete.jpg)

A próxima abordagem era uma solução "smoke-and-mirror", que consiste na sobreposição de camadas de textura transparente, cada uma abordando um aspecto específico do movimento atômico, compilado em uma composição de malhas giratórias.

Na imagem abaixo, você pode ver o shell interno à esquerda. Essa camada de mat forneceu um plano de fundo para a composição para se proteger contra quaisquer pequenas lacunas entre as várias camadas que comiam as nuvens. Devido à rotação lenta da camada, ela também servia como um buffer visual entre as faixas móveis mais rápidas para ajudar a criar o Visual Unity em todas as camadas.

Depois de definir essa âncora para o modelo, as camadas de nuvem móveis foram projetadas nas malhas intermediária e direita vistas abaixo.

![Visão geral do objeto Demão com shells separados](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>Texturização

A textura existente foi separada em um atlas de textura de três partes: a terceira parte superior hospeda uma camada sem movimento de nuvens com lacunas para fornecer um efeito paralax, a seção intermediária contém os fluxos externos móveis rápidos e o terceiro inferior contém uma camada base interna giratória lenta.

A característica Great Red Spot também foi separada em suas várias partes móveis e, em seguida, inserida em uma área invisível da textura. Esses componentes podem ser vistos como as culalhes em vermelho na seção intermediária da imagem abaixo.

Como cada faixa tem uma direção e velocidade específicas, a textura foi aplicada a cada malha individualmente. Em seguida, as malhas tinham um ponto central e um ponto pivô comuns, o que possibilita animar de forma conccentricamente toda a superfície.

![Visão geral das texturas de texturas de textura](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>Comportamento de rotação e textura

Depois que a composição visual de Orbital foi definida, precisamos garantir que as velocidades de rotação e de órbita foram calculadas corretamente e aplicadas adequadamente. Leva cerca de 9 horas para Queliano conclua uma rotação completa. Isso é uma questão de definição devido à rotação diferencial. Portanto, o fluxo ltda foi definido como um "fluxo mestre", levando 3600 quadros para uma rotação completa. Todas as outras camadas precisavam ter uma velocidade de rotação como um fator de 3600 para corresponder à sua posição inicial, permitindo, por exemplo, 600, 900, 1200, 1800 etc.

![Texturas de shell de casca de](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>O Grande Ponto Vermelho

Os fluxos que giram individualmente proporcionam uma boa impressão visual, mas não têm detalhes quando observados a um intervalo próximo.

A parte mais atraente era o Excelente Ponto Vermelho de Sempre, portanto, criamos um conjunto de malhas e texturas especificamente para demonstrar isso.
 
Utilizamos um mecanismo semelhante ao das bandas de Sempre: um conjunto de partes giratórias era composto umas sobre as outras, enquanto também era agrupado sob sua "camada mestra" para garantir que elas permaneçam na posição, independentemente da velocidade com que o restante se move.

Quando as malhas foram configuradas e no local, diferentes camadas do stormy foram aplicadas e cada disco foi animado individualmente, as partes do centro se movem mais rápido, com o restante diminuindo progressivamente conforme ele se move para fora.

![Malha do Great Red Spot](images/ge-update-great-red-spot-mesh.jpg)

A composição também tinha o mesmo pivô de todas as outras malhas, mantendo também sua inclinação do eixo y original (!) para permitir a liberdade na animação da rotação. 3600 quadros é a taxa base, com cada camada tendo um fator disso como um período de rotação.

![Textura do Great Red Spot](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>Como fazer isso no Unity

Há algumas coisas importantes a ter em mente ao implementar isso no Unity.

O Unity é facilmente confundido ao lidar com grandes conjuntos de camadas transparentes. A solução era duplicar o material de textura para cada malha e aplicar valores crescentes de Renderizar Fila progressivamente do interno para o externo em 5 para cada material.

O resultado foi que o shell interno tinha um valor de Fila de Renderização de 3000 (padrão), o externo com sinal vermelho estático mais tarde tinha um valor de 3005, as nuvens externas brancas rápidas tinham 3010. O Grande Ponto Vermelho (que progride de camada interna para externa), concluído com um valor de 3025 nesse modelo.

![Objeto final Det.](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>Toques finais

As camadas deInferiores texturizou foram configuradas no início, o que se mostrou insuficiente para implementação.

O sombreador Padrão do Planeta original e todas as suas variações recebem suas informações de iluminação por meio de um script, o SunLightReceiver, que não é suportado pelo sombreador padrão do MRTK.

Simplesmente trocar os sombreadores não era uma solução porque o sombreador Planet Standard não dá suporte a mapas de textura com transparências. Editamos esse sombreador para fazer com que o build Doliano funcione conforme o esperado.

Por fim, os Blends Alfa precisavam ser definidos definindo o Source Blend como 10 e o Destination Blend como 5.

![Propriedades do Unity do Unity](images/ge-update-jupiter-unity-render-queue.jpg)

Você pode ver a renderização final do Galaxy Explorer!

## <a name="meet-the-team"></a>Conheça a equipe 

Nossa equipe do Estúdio de Realidade Misturada é feita de designers, artista 3D, especialistas de UX, desenvolvedores, um gerente de programa e um diretor de estúdio. Nós nos vemos em todo o mundo: Canadá, Canadá, Alemanha, Canadá, Japão, Reino Unido e Estados Unidos. Nós somos uma equipe multidisciplinar que vem de uma forma diversificada: jogos – tradicional e profissional, marketing digital, serviços de saúde e ciência.

Estamos felizes em criar o Galaxy Explorer para o HoloLens 2 e atualizar as versões de HoloLens (primeira geração), VR e área de trabalho. 

![A equipe do Galaxy Explorer](images/ge-update-team-image.png)

Na parte superior da esquerda para a direita: Artemis Tsouflidou (Desenvolvedor), Artemis Teickner (Designer Visual), David Janer (Designer de UX), Laura Delivery & Production Lead), Shishi Zonno (Creative Lead), Eline Ledent (Developer) e Ben Ltd (Desenvolvedor Sênior).
De baixo da esquerda para a direita: Amit Rojtblat (Technical Artist), Martin Wettig (3D Artist) e Kam Filho (Studio Head).
Não em destaque: Tim Gerken (Tech Lead) e Ash Salandin (Visual Designer).

## <a name="additional-information"></a>Informações adicionais

### <a name="mixed-reality-studios"></a>Estúdios de Realidade Misturada

As equipes do Microsoft Mixed Reality Studio – localizadas nas Américas, Na Europa e Asia-Pacific – são especialistas em design de experiência do usuário, computação holográfica, tecnologias ar/VR e desenvolvimento 3D; incluindo a criação de ativos 3D, DirectX, Unity e Unreal. Ajudamos a prever futuros desejados, projetar, criar e fornecer soluções, permitindo que os clientes criem um impacto mensurável em sua organização. Os estúdios trabalham em estreita proximidade com mais de 22.000 profissionais dos Serviços da Microsoft para integração, adoção, operações e suporte de aplicativos empresariais.