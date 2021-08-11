---
title: a criação do Galaxy Explorer para HoloLens 2
description: saiba mais sobre como nossa equipe está atualizando o projeto de código-fonte aberto do Galaxy Explorer para HoloLens 2 em GitHub.
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: gerenciador do galaxy, estudo de caso, projeto, exemplo, MRTK, realidade misturada Toolkit, Unity, aplicativos de exemplo, aplicativos de amostra, software livre, Microsoft Store, HoloLens, headset de realidade misturada, headset de realidade mista do windows, headset de realidade virtual
ms.openlocfilehash: c3d9c6da13446816f3fd75f83e5a9088661c9604ef4d86ea805202f538d395b5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200444"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>a criação do Galaxy Explorer para HoloLens 2

![Novo logotipo do Galaxy Explorer](../images/GalaxyExplorer2.jpg)


bem-vindo ao aplicativo do Galaxy Explorer atualizado para HoloLens 2! o [Galaxy Explorer](/windows/mixed-reality/galaxy-explorer "Gerenciador do Galaxy") foi originalmente desenvolvido como um aplicativo de software livre para HoloLens (primeira gen) por meio do programa compartilhar sua ideia e é uma das primeiras experiências misturadas de realidade que muitas pessoas tinham. agora estamos atualizando-o para os [recursos novos e empolgantes do HoloLens 2](https://www.microsoft.com/hololens/hardware).

Como uma das [estúdios de realidade misturada da Microsoft](galaxy-explorer-update.md#mixed-reality-studios), normalmente desenvolvemos soluções comerciais e estamos desenvolvendo & testes em plataformas de destino em todo o processo criativo e de desenvolvimento. Estamos embarcando neste projeto usando as estruturas e ferramentas (como [MRTK](mrtk-getting-started.md)) à medida que se tornam disponíveis para nós e para a Comunidade, e queremos levá-lo para a jornada.

assim como o Galaxy Explorer original, [nossa equipe](galaxy-explorer-update.md#meet-the-team) estará [aberta no fornecimento do projeto em GitHub](https://github.com/Microsoft/GalaxyExplorer) para garantir que a comunidade tenha acesso completo. também documentaremos nossa jornada aqui em transparência completa sobre a forma como transportamos do MRTK v1 para o MRTK v2, aprimoramos a experiência com os novos recursos disponíveis no HoloLens 2 e garantimos que o Galaxy Explorer permanecesse em uma experiência de várias plataformas. independentemente de você estar exibindo o Galaxy Explorer em HoloLens (primeira gen), HoloLens 2, um Windows Mixed Reality headset ou em sua área de trabalho Windows 10, queremos ter certeza de que você está aproveitando a jornada tanto quanto estamos!

Esta página será expandida à medida que progredirmos por meio do projeto com links para artigos mais detalhados, código, artefatos de design e documentação adicional do MRTK para fornecer uma visão do Insider do projeto.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>baixar o aplicativo de Microsoft Store no HoloLens 2
se você tiver HoloLens 2 dispositivo, poderá baixar e instalar diretamente o aplicativo em seu dispositivo.

<a href='//www.microsoft.com/store/apps/9nblggh4q4jg?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="thinking-about-interactions"></a>Pensando sobre interações

como um creative studio, estávamos maravilhadas sobre o privilégio de portar o Galaxy Explorer para HoloLens 2. Sabíamos desde o início que queríamos que a experiência fosse uma comemoração do novo dispositivo e que demonstrasse que a capacitação da realidade misturada é limitada apenas pela imaginação.

o HoloLens 2 permite que os usuários toquem, segurem e movam os hologramas de formas que se sentem naturais – eles respondem muito como objetos reais. Modelos de mão totalmente articulados são impressionantes, pois permitem que os usuários façam o que se sente natural. por exemplo, todo mundo escolhe uma xícara um pouco diferente – e em vez de impor uma maneira específica de fazê-lo, HoloLens 2 permite que você faça o seu caminho.

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

essa é uma alteração significativa das interfaces baseadas em toque de ar em dispositivos HoloLens de primeira geração. Em vez de interagir com hologramas de uma distância, os usuários agora podem obter "de perto e pessoal". ao portar experiências existentes no HoloLens 2 ou planejar novas, é importante se familiarizar com a manipulação direta de hologramas.

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>Manipulação direta versus grandes distâncias no espaço

É uma experiência mágico de entrar em contato, pegar um planeta e mantê-lo em sua mão. O desafio dessa abordagem é o tamanho do sistema solar – é enorme! O usuário precisaria examinar sua sala para se tornar um perto de cada planeta para interagir com ele.

Para permitir que os usuários interajam com objetos que estão mais distantes, o MRTK oferece raios de mão que saem do centro da palma do usuário, agindo como uma extensão da mão. Um cursor em forma de rosca é anexado ao final do raio para indicar onde o raio intersecciona com um objeto de destino. O objeto sobre o cursor pode receber comandos gestuais da mão. 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

Na versão original do Galaxy Explorer, o usuário visaria um planeta com o cursor olhar e, em seguida, tocaria em volta para chamá-lo mais próximo. a maneira mais fácil de portar a experiência para HoloLens 2 é pegar esse comportamento e usar raios de mão para selecionar planetas. Embora isso fosse funcional, ele nos deixou mais.

### <a name="back-to-the-drawing-board"></a>Voltar para o quadro de desenho

Nós reunimos para ideate o que poderia ser criado sobre as interações existentes. o pensamento foi: embora HoloLens 2 permita que os usuários interajam com hologramas de maneiras naturais e realistas, os hologramas são por definição não reais. Portanto, desde que uma interação seja plausível para o usuário, não importa se essa interação seria possível com um objeto real ou não – podemos torná-la possível.

Um conceito que exploramos foi baseado em Telekinesis – a capacidade de manipular objetos com uma ideia. Geralmente visto em filmes de Superheroes, uma pessoa deve entrar em contato com sua ideia e chamar um objeto em sua mão aberta. Nós jogamos com mais idéias e surgiu um esboço rápido de como o conceito poderia funcionar.

![Conceito para a interação de captura forçada](images/ge-update-interactions-concept-force-grab.png)

O usuário apontaria o lado raio de um planeta, que forneceria comentários de destino. À medida que o usuário estende sua mão aberta, o planeta seria puxado para o usuário por uma força mágico até que esteja perto o suficiente para conseguir. Portanto, nosso nome para a interação: forçar captura. À medida que o usuário retirar o planeta da mão aberta, ele retornaria novamente à sua órbita.

### <a name="force-grab-prototyping"></a>Forçar captura de protótipos

Depois, criamos vários protótipos para testar o conceito: como a interação se sente geral? O objeto chamado deve parar na frente do usuário ou aderir até suas mãos até que seja colocado? O tamanho ou a escala da alteração do objeto chamado deve ser chamado?

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>Implementando força de coleta no aplicativo

Quando tentamos a captura forçada em planetas, percebemos que tivemos que alterar a escala do sistema solar. Foi claro que uma representação precisa e de tamanho médio do sistema solar é difícil para os usuários entenderem e navegarem, mas não soubessem onde procurar. No entanto, uma representação de tamanho pequeno tornou alguns planetas muito pequenos para serem facilmente selecionados. Como resultado, o tamanho dos planetas e o espaçamento entre os objetos solares foi projetado para se sentir confortável em uma sala de tamanho médio, mantendo a precisão relativa.

Durante os estágios posteriores de nosso Sprint de desenvolvimento, estávamos à frente de ter o colega de realidade misturada da MSFT, portanto, temos que trabalhar obtendo sua entrada como testadores especialistas e fazer iterações rápidas na interação de captura forçada.

![Maria Kam testando uma versão prévia do Galaxy Explorer](images/ge-update-user-testing.png)

Em figura: Maria Kam, Lead de design sênior, testando um trabalho em andamento do Galaxy Explorer.

### <a name="adding-affordances-for-targeting"></a>Adicionando capacidades para direcionamento

à medida que experimentamos o HoloLens 2, descobrimos que, embora as novas interações sejam naturais e intuitivas, os hologramas permanecem os mesmos: sem peso ou tactile sensations. Como os hologramas não fornecem comentários naturais que os humanos são usados para receber quando interagem com objetos, precisávamos criá-los.

Pensamos nos comentários visuais e de áudio que os usuários seriam fornecidos para os vários estágios de suas interações, e como o mecanismo de captura forçada é fundamental para interagir com o Gerenciador do Galaxy, fizemos muitas iterações. O objetivo era encontrar o equilíbrio certo entre áudio e comentários visuais para cada estágio da interação: concentrando-se no objeto pretendido, chamando-o ao usuário e, em seguida, liberando-o. o que aprendemos é que mais comentários visuais e de áudio eram necessários para reforçar a interação do que eram usados para a HoloLens (primeira gen).

![Visual capacidades no planetas](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>Adicionando capacidades para forçar captura
 
Quando tínhamos o mecanismo básico de captura forçada com áudio e Visual capacidades, examinamos como tornar a seleção de planetas mais amigável. Havia dois aspectos principais a serem abordados: como o sistema solar é uma interface de movimentação 3D, há uma complexidade adicional para que os usuários aprendam a direcionar os objetos de forma consistente. Isso foi composto pelo fato de que o raio da mão é rápido na seleção de um objeto, fazendo com que os planetas se movam para o usuário incrivelmente rapidamente.

Abordamos isso com uma solução em três pinos. A primeira era bastante intuitiva: retardar o processo de seleção para que os planetas abordem o usuário em um ritmo mais natural. Depois que a velocidade foi ajustada, tivemos que revisitar o áudio e o Visual capacidades, adicionando comentários de áudio como o planeta rastreado para o usuário.

A segunda parte da solução era tornar a visualização de toda a interação de captura de força tangível. Nós visualizamos uma linha espessa que se move para o objeto de destino depois que o raio de alcance se conecta a ele e, em seguida, coloca o objeto de volta para o usuário como um laço. 

![Capacidades do Visual "laço" para a captura forçada](images/ge-update-lasso-affordances.png)

Por fim, otimizamos a escala do sistema solar para que os planetas fossem grandes o suficiente para a olhar e a mão Ray do usuário a fim de direcioná-los. 

Esses três aprimoramentos permitiam que os usuários tomassem seleções precisas, chamando os planetas a eles de forma intuitiva. De modo geral, o efeito da captura de força final é uma experiência mais envolvente e interativa no sistema solar.

## <a name="spotlight-on-jupiter"></a>Destaque em Júpiter

Criar os corpos solares da forma de leite era uma experiência humbling. Em particular, as características exclusivas do Júpiter o tornam uma visão surpreendentemente. É o maior e mais colorido do gigantes de gás e contém mais massa do que todos os outros planetas combinados. Suas bandas de tamanho e mesmerizing de turbulência e Cloud Dynamics são Prefect para uma atenção de artístico especial.

### <a name="geometry-and-meshes"></a>Geometria e malhas

Como um Giant gigante, os shells externos do Júpiter consistem em camadas de gaseous. A combinação de sua velocidade rápida de rotação, troca interna de calor e Coriolis força cria camadas coloridas e transmite a forma de espiraar as correias de nuvem e vortices. Capturar essa beleza complexa foi fundamental para a criação de nosso sistema solar.

Ficou imediatamente claro que o uso de técnicas de visualização como simulações fluidas e texturas animadas com fluxos computacionais estavam fora de questão. O poder de computação necessário para simular isso em combinação com tudo o mais acontecendo simultaneamente teria impacto negativo significativo sobre o desempenho. 

![Visão geral do objeto Júpiter](images/ge-update-jupiter-shells-complete.jpg)

A próxima abordagem era uma solução de "fumaça e espelho", consistindo na sobreposição de camadas de textura transparente, cada uma delas resolveva um aspecto específico da movimentação de atmosférica, compilada em uma composição de malhas giratórias.

Na imagem abaixo, você pode ver o Shell interno à esquerda. Essa camada de passe-partout forneceu um plano de fundo para a composição a fim de se proteger contra qualquer pequena lacuna entre as várias camadas que compõem as nuvens. Por causa da rotação lenta da camada, ela também é servida como um buffer visual entre as faixas de movimentação mais rápidas para ajudar a criar o Visual Unity em todas as camadas.

Depois de definir essa âncora para o modelo, as camadas de nuvem em movimento foram projetadas nas malhas intermediária e direita, vistas abaixo.

![Visão geral do objeto Júpiter com shells separados](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>Texturing

A textura existente foi separada em um Atlas de textura de três partes: a terceira parte superior hospeda uma camada sem movimento de nuvens com intervalos para fornecer um efeito da Parallax, a seção intermediária contém os fluxos externos de movimentação rápida e o terceiro inferior contém uma camada de base interna de rotação lenta.

A característica incrível de Red Spot também foi separada em suas várias partes móveis e, em seguida, inserida em uma área invisível do tipo de textura. Esses componentes podem ser vistos como manchas de toned vermelha na seção intermediária da imagem abaixo.

Como cada banda tem uma direção e velocidade específicas, a textura foi aplicada a cada malha individualmente. Em seguida, as malhas tinham um centro comum e um ponto dinâmico, o que torna possível animar de forma concêntrica toda a superfície.

![Visão geral das texturas de Júpiter](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>Comportamento de rotação e textura

Uma vez que a composição visual de Júpiter foi definida, precisávamos garantir que as velocidades de rotação e de órbita fossem calculadas e aplicadas adequadamente. Leva aproximadamente 9 horas para Júpiter concluir uma rotação completa. Essa é uma questão de definição devido à sua rotação diferencial. Portanto, o fluxo Equatorial foi definido como um ' fluxo mestre ', levando 3600 quadros para uma rotação completa. Todas as outras camadas precisavam ter uma velocidade rotacional como um fator de 3600 para corresponder à sua posição inicial, permitindo, por exemplo, 600, 900, 1200, 1800 etc.

![Texturas do Shell Júpiter](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>O grande ponto vermelho

Os fluxos de rotação individualmente forneciam uma boa impressão Visual, mas não têm mais detalhes quando observados no intervalo de fechamento.

A parte mais atraente foi o grande ponto vermelho da Júpiter, portanto, criamos um conjunto de malhas e texturas especificamente para mostrá-la.
 
Usamos um mecanismo semelhante ao da faixa de Júpiter: um conjunto de partes de rotação foi composto sobre um do outro, enquanto também está sendo agrupado em sua ' camada mestra ' para garantir que eles permaneçam em posição, não importa a velocidade com que o REST se move.

Quando as malhas foram configuradas e, em vigor, camadas diferentes do Storm Vortex foram aplicadas e cada disco era então animado individualmente, as partes centrais se movimentam mais rapidamente, com o REST progressivamente diminuindo à medida que se movem para cima.

![Grande malha de pontos vermelhos de Júpiter](images/ge-update-great-red-spot-mesh.jpg)

A composição também tinha a mesma tabela dinâmica que todas as outras malhas, enquanto também mantém sua inclinação do eixo y original (!) para permitir a liberdade de animar a rotação. 3600 quadros é a taxa base, sendo que cada camada tem um fator como um período de rotação.

![Boa textura de pontos vermelhos de Júpiter](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>Fazendo isso diretamente no Unity

Há algumas coisas importantes para se ter em mente ao implementar isso no Unity.

O Unity é facilmente confundido ao lidar com grandes conjuntos de camadas transparentes. A solução era duplicar o material de textura para cada malha e aplicar valores crescentes da fila de renderização progressivamente, do interior ao exterior, em 5 a cada material.

O resultado era que o Shell interno tinha um valor de fila de renderização de 3000 (padrão), o externo vermelho-toned externa mais tarde tinha um valor de 3005, as nuvens externas brancas rápidas tinham 3010. O grande ponto vermelho (progredindo da camada interna para a externa), terminou com um valor de 3025 neste modelo.

![Objeto final Júpiter](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>Toques finais

As camadas de Júpiter texturizadas foram configuradas primeiro, o que provou ser insuficiente para a implementação.

O sombreador padrão do planeta original e todas as suas variações, recebem suas informações de iluminação por meio de um script, o SunLightReceiver, que não tem suporte do sombreador padrão do MRTK.

Simplesmente trocar os sombreadores não era uma solução porque o sombreador padrão do planeta não dá suporte a mapas de textura com transparências. Editamos este sombreador para fazer com que o Build Júpiter funcione conforme o esperado.

Por fim, as misturas alfa precisavam ser configuradas definindo o Blend de origem como 10 e a mistura de destino como 5.

![Propriedades do Unity do Júpiter](images/ge-update-jupiter-unity-render-queue.jpg)

Você pode ver a renderização final de Júpiter no Galaxy Explorer!

## <a name="meet-the-team"></a>Conheça a equipe 

Nossa equipe mista do reality Studio é composta por designers, artistas de 3D, especialistas de UX, desenvolvedores, gerente de programa e diretor de estúdio. Nós Hail em todo o mundo: Bélgica, Canadá, Alemanha, Israel, Japão, Reino Unido e o Estados Unidos. Somos uma equipe multidisciplinar que vem de um plano de fundo diversificado: jogos – tradicional e indie, marketing digital, assistência médica e ciência.

estamos empolgados para criar o Galaxy Explorer para HoloLens 2 e para atualizar a HoloLens (primeira gen), o VR e as versões da área de trabalho. 

![A equipe do Galaxy Explorer](images/ge-update-team-image.png)

Na parte superior da esquerda para a direita: Artemis Tsouflidou (desenvolvedor), Angie Teickner (Visual Designer), David Janer (Designer de UX), Laura Garrett (entrega & líder de produção), Yasushi Zonno (líder criativo), Eline Ledent (desenvolvedor) e Ben Turner (Sr. Developer).
Inferior da esquerda para a direita: Amit Rojtblat (artista técnico), Martin Wettig (artista 3D) e Dirk Songuer (estúdio Head).
Não em destaque: Tim Gerken (Tech Lead) e Oscar Salandin (Visual Designer).

## <a name="additional-information"></a>Informações adicionais

### <a name="mixed-reality-studios"></a>Realidade misturada ESTÚDIOS

As equipes do Microsoft Mixed Reality Studio – localizadas nas Américas, na Europa e no Asia-Pacific-são especialistas em design de experiência do usuário, computação Holographic, tecnologias de AR/VR e desenvolvimento 3D; incluindo a criação de ativos 3D, DirectX, Unity e inreal. Ajudamos a prever futuros, projetar, criar e fornecer soluções, permitindo que os clientes criem um impacto mensurável em toda a organização. O estúdios trabalha em conjunto com mais de 22.000 profissionais de serviços da Microsoft para integração de aplicativos empresariais, adoção, operações e suporte.