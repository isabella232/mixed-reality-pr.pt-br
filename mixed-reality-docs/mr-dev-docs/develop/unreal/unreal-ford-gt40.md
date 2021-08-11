---
title: Experiência Ford GT40
description: acompanhe à medida que exploramos a criação do aplicativo de realidade mista da Ford GT40 com MRTK para HoloLens 2 em inreal.
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: inreal, inreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, implantar em dispositivo, PC, documentação, headset de realidade misturada, headset de realidade mista do windows, headset da realidade virtual
appliesto:
- HoloLens 2
ms.openlocfilehash: 17314cca69148e73ee11fcd4cdc5359a5dbae4cf84b609bafb6cc75d477ec26f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200596"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>A criação da experiência Ford GT40
![Imagem do Ford GT40 Hero](images/ford-gt40-hero_1920.jpg)

*"MRTK, desenvolver para HoloLens 2 usando inreal era um pouco entediante porque todas as interações espaciais precisavam ser codificadas manualmente, em C++. O MRTK de forma não real fez muitas dessas mesmas tarefas triviais. Eu o estimava reduzindo o tempo necessário para o protótipo inicial pela metade. "* -José Rodriguez, desenvolvedor de software

*"a experiência da Ford GT40 é a prova de que um aplicativo HoloLens 2 de alta fidelidade pode ser concluído em apenas alguns meses, com um orçamento modesto, ainda assim fornecer resultados altamente impactados."*  -Daniel Cheetham, diretor de inovação, bom término

usando a Toolkit de realidade misturada (MRTK) para a empresa de produção criativa, a conclusão feliz é uma experiência de HoloLens 2 que fornece uma nova perspectiva no Ford GT40, o carro de corrida lendárias que lança Ferrari nas 24 horas da Le Mans!

Usando uma variedade de interações espaciais naturais e intuitivas, os usuários podem explorar a beleza, o desempenho e a engenharia do GT40's – tudo o que é fornecido de uma maneira que aproveita a alta fidelidade de Visual, fornecida pelo mecanismo inreal. O desenvolvimento de software para todo o projeto foi concluído por um único desenvolvedor em menos de três meses, possibilitado pelo MRTK para o ambiente de design e criação de scripts visuais inreais.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>baixar o aplicativo de Microsoft Store no HoloLens 2
se você tiver HoloLens 2 dispositivo, poderá baixar e instalar diretamente o aplicativo em seu dispositivo.

<a href='//www.microsoft.com/store/apps/9p4vllktfvfp?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="the-ask"></a>A pergunta

O bom término é uma das principais empresas de produção criativa do mundo, com uma base de clientes que inclui, Ford, Microsoft, Nike, Netflix, Vodafone e outros nomes domésticos. A empresa obteve seu início como uma agência de retoque de fotos de ponta, ramificação para o filme e o CGI antes de estender sua dedicação à excelência em narração de imersão com design e interação espaciais 3D.

em meados de 2020, a Microsoft abordou muito bem a fim de produzir um aplicativo de demonstração que pode ajudar a demonstrar as possibilidades habilitadas pela nova realidade misturada Toolkit (MRTK) para o inreal, que se baseia no suporte para HoloLens 2 no mecanismo inreal. neste ponto, a empresa já tinha dois projetos bem-sucedidos não reais de HoloLens 2 em sua correia. os dois eram para uma marca de consumidor reconhecida globalmente, que escolheva inreal em HoloLens 2 para uma ferramenta interna de vendas R&D/B2B para sua alta fidelidade de visual, conforme o necessário para demonstrar melhor os produtos de alto nível do cliente.

Embora a solução em si fosse deixada para o bom término, ela precisava atender a algumas diretrizes importantes. primeiro, ele precisava se concentrar em um cenário empresarial para ilustrar o utilitário de não real no HoloLens 2 fora do setor de jogos. Em segundo lugar, tinha que ser somente dispositivo, o que significa que ele poderia servir como uma demonstração autônoma, sem a necessidade de uma conexão de rede e poder de processamento externo para obter as taxas de quadros de destino e a qualidade visual. Em terceiro lugar, ele deve misturar a gama de interações intuitivas com suporte do MRTK em uma experiência perfeita e natural. Por fim, a solução proposta deve demonstrar a fidelidade visual inerente e outros benefícios do próprio mecanismo não real, como a eficiência do sombreador. 

Devido a essas diretrizes, o bom término começou a debater as possibilidades, contratando a ideia de uma experiência de realidade misturada que usou a interação espacial para comunicar o valor de um produto de nome de marca e de alto valores. Depois de considerar uma variedade de objetos que incluíam inspeções, câmeras, carros e Jets particulares, o bom término, por fim, foi decidido na Ford GT40, uma legenda automotivada que alcançou notoriedade em 1966 quando Ford superar Ferrari às 24 horas da Le Mans, como mostra o blockbuster de filmes 2019 e Ferrari. 

Ao obter a compra do Ford, um cliente feliz Finish existente, a empresa foi configurada para fornecer uma nova perspectiva sobre o ícone automotivo clássico.

## <a name="the-solution"></a>A solução

O trabalho começou em 7 de maio de 2020. Depois de obter os arquivos de modelo GT40, um artista 3D gastou três semanas otimizando modelos de polígono, mapeamento UV, redesenhando mapas de textura e condensando esses mapas no máximo de texturas possível. Um artista técnico trabalhou em paralelo para fazer o benchmark da saída do artista 3D, determinar os tamanhos de textura ideais fornecidos nas taxas de quadros de destino e descobrir a melhor maneira de aplicar sombreadores personalizados em tempo inreal. Todo esse trabalho de pré-produção foi feito para otimizar a experiência no dispositivo.

O diretor criativo Alex Lambert entrou na imagem após a conclusão do trabalho de pré-produção. Ele começou assistindo a Ford vs. Ferrari, pensando em como reunir uma narração em torno dos cenários e das interações. Ele também coletou referências visuais para o artista da interface do usuário, como imagens do painel GT40 e visuais do Le Mans Racetrack, e coletava gravações de áudio do GT40 em ação para o designer de som.

Com a narração definida e otimizada os ativos de pré-produção, o freelancer Software Developer José Rodriguez foi inscrito para juntar tudo isso. a Rodriguez tinha sido o desenvolvedor nos dois projetos anteriores que não são HoloLens 2, pois o término feliz tinha sido feito, antes que o MRTK para o inreal fosse lançado.

O valor fornecido pelo MRTK para inreal se tornou evidente no início, ajudando a Rodriguez a entregar um protótipo inicial em uma semana. Ele implementou três cenários exclusivos, um para cada um dos principais aspectos do GT40 que Lambert tinha identificado: sua beleza, seu desempenho e sua engenharia. Para cada cenário, Rodriguez usou o MRTK para integrar os ativos 3D otimizados da fase de pré-produção em um intervalo de interações espaciais. 

Com o MRTK para o inreal, Rodriguez criou cada cenário usando o designer de interface de usuário do UMG (Visual inreal Motion Graphics) em vez de ter que implementar tudo em C++. As [ferramentas de UX para não reais](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools), o plug-in que contém os componentes e os blocos de construção de UX dentro do MRTK, forneciam [plantas inreais](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) para a simulação de entrada, interações com o Visual scripting, botões prensais, manipulação de imagem 3D, Magnetism de superfície e muito mais – tudo em um ambiente de design de arrastar e soltar sem código.

"MRTK, desenvolver para HoloLens 2 usando inreal era um pouco entediante porque todas as interações espaciais precisavam ser codificadas manualmente, em C++", diz Rodriguez. "O MRTK de forma não real fez muitas dessas mesmas tarefas triviais. Eu o estimava reduzindo o tempo necessário para o protótipo inicial pela metade. "

Com um protótipo em mãos, a equipe começou iterações semanais para refinar a experiência. "isso ocorre quando o recurso de captura de realidade misturada e o Windows Portal de dispositivo se tornaram muito úteis," recupera Lambert. "Eu as usei para capturar minhas revisões de design, transmitir meus comentários para outras pessoas e colaborar em alterações. Trabalhar em isolamento como esse seria impossível fazer sem essas ferramentas. "

![Editor inreal Ford GT40 app em execução com componentes de roda dispostos em sequência](images/ford-gt40-img-04.JPG)

Como Lambert as alterações solicitadas, como reposicionar elementos da interface do usuário ou alterar o comportamento de um botão, o Rodriguez os implementou. Embora algumas das alterações exigissem pequenos ajustes de código, a maioria deles era tratada no designer visual inreal. "Fiquei surpreso com a rapidez com que eu poderia iterar", diz Rodriguez. "Nenhum tempo foi desperdiçado; Eu farei uma alteração no designer e, em seguida, pressionaria reproduzir para exibi-lo imediatamente no dispositivo. O MRTK realmente simplificou o meu trabalho. "

Rodriguez também está impressionado com a forma como todas as ferramentas de desenvolvimento estão prontas para a produção. "Progredimos suavemente do protótipo inicial por meio da produção final, sem precisar voltar e reimplementar ou otimizar as coisas no código", ele diz.  

## <a name="the-final-build"></a>A compilação final

o bom término concluiu a produção da experiência Ford GT40 para o HoloLens 2 em 28 de julho de 2020, fornecendo uma nova perspectiva sobre o carro de corrida lendárias. A experiência começa com uma tela de boas-vindas e, em seguida, orienta o usuário a configurar uma âncora ao captar o logotipo Ford e colocá-lo em uma superfície plana como uma tabela ou área de trabalho. 

### <a name="beauty"></a>Grande

O segmento de **beleza** leva o usuário a um configurador GT40, que EXIBE o GT40 em um pedestal rotativo, semelhante a como um carro físico pode ser exibido em um automotivo. O usuário pode aplicar opções de roda diferentes, escolher entre esquemas de cores diferentes e abrir e fechar as portas e o tronco (ou inicialização, conforme eles o chamam no Reino Unido). Durante toda a experiência de beleza, o usuário pode pegar o carro e manipulá-lo livremente para uma análise mais detalhada.

![GIF animado do Configurador GT40 em execução em um dispositivo](images/ford-gt40-img-05.gif)

### <a name="performance"></a>Desempenho

O segmento de **desempenho** demonstra a velocidade e a durabilidade do GT40's. A VoiceOver começa descrevendo como o carro foi desenvolvido e atravessando seus ritmos na Ford Recife, o Arizona comprova o aterramento, com visuais 3D mostrando o GT40 em movimento na faixa de teste. À medida que a introdução ao segmento de desempenho é concluída, o VoiceOver solicita que o usuário "Pressione o botão Le Mans para atingir o Racetrack".

![GIF animado do aplicativo de velocidade e durabilidade de GT40 em execução em um dispositivo](images/ford-gt40-img-06.gif)

A segunda parte do segmento de desempenho demonstra o GT40 sob o intervalo de condições que os drivers podem experimentar nas 24 horas de Le Mans, que é mantido anualmente no circuito de La Sarthe próximo a Le Mans, França. Uma exibição 3D mostra o carro em movimento na faixa Le Mans, com botões fornecidos para fazer com que o carro fique mais rápido ou mais lento. Imagens do GT40's analógico velocímetro e do tacômetro flutuam acima da exibição Racetrack, com mais telemetria de corrida exibida em segundo plano. O usuário pode alternar entre as exibições dia e noite e entre as condições de condução seca e úmida, fornecendo uma perspectiva realista e realista sobre o que Ken milhas e os outros drivers GT40s experimentaram na corrida real.

### <a name="engineering"></a>Engenharia

O segmento de **engenharia** da experiência da Ford GT40 apresenta uma das inovações de engenharia que ajudou a Ford ganhar a corrida: a capacidade de alterar os rotores e pads de freio em menos de um minuto, em comparação com os 20-30 minutos necessários para todas as outras equipes. Usando gestos intuitivos, o usuário pode manipular um modelo 3D detalhado da roda do GT40 e do conjunto de freios. Para expandir o assembly, o usuário pega uma chave inglesa carregar, alinha-a ao bloqueio central na roda, transforma-a no sentido anti-horário e a retira da roda. Outros gestos são usados para remover os rotores de freio e Pads, substituí-los por novos, recolher o assembly e proteger novamente o bloqueio do centro. Em segundo plano, um temporizador exibe o tempo decorrido, permitindo que o usuário veja se ele pode concluir o processo tão rapidamente quanto a equipe de pit em Le Mans.

![GIF animado da experiência de engenharia do GT40 em execução em um dispositivo](images/ford-gt40-img-07.gif)

a experiência do Ford GT40 pode ser [baixada da Microsoft store](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab), permitindo que qualquer pessoa com um HoloLens 2 explore o quão feliz terminar foi uma nova perspectiva para o carro de corrida lendárias.

### <a name="getting-impressive-visual-fidelity"></a>Obtendo uma fidelidade visual impressionante

Embora o intervalo de interações espaciais com suporte da experiência Ford GT40 seja impressionante por conta própria, a criatividade e a fidelidade visual que a experiência fornece é o que realmente faz se brilhar. Por meio da otimização dos modelos 3D e do uso de sombreadores personalizados não reais, o bom término atingiu seu destino de 60 quadros por segundo, mesmo com o segmento de desempenho do aplicativo que está abordando 315.000 polígonos de tamanho. 

"Estou realmente satisfeito com a forma como pudemos reunir um conjunto de interações fluidas e intuitivas em uma narrativa coerente e envolvente", diz Lambert. "claramente, o poder do mecanismo inreal no HoloLens 2 abre um novo mundo de oportunidade para experiências de realidade misturadas mais surpreendentes e empolgantes. a fidelidade visual descomprometida nem sempre é a meta final para aplicativos empresariais no HoloLens 2, mas quando é, o suporte para inreal em HoloLens 2 se torna inestimável. "

### <a name="rapid-solution-delivery"></a>Entrega rápida de solução

Tão impressionante quanto a experiência de GT40 do usuário final Ford é a rapidez com que o término do seu fornecimento é rápido, com todo o projeto — desde a pré-produção até a entrega final – concluído em apenas menos de 12 semanas. Em suma, o projeto consumiu 1088 horas de esforço, dividido da seguinte maneira: Creative Director (80 horas), UX Designer (56 horas), designer de interface do usuário (40 horas), designer de som (40 horas), 3D/artista técnico (328 horas), desenvolvedor de software (408 horas), diretor técnico (40 horas), produtor (56 horas) e garantia de qualidade (40 horas).

"Em geral, chegamos muito perto de nossas estimativas de projeto originais", diz Daniel Cheetham, diretor de inovação em boas-vidas, que anuncia a divisão interativa da empresa. "a experiência da Ford GT40 é a prova de que um aplicativo HoloLens 2 de alta fidelidade pode ser concluído em apenas alguns meses, com um orçamento modesto, ainda assim fornecer resultados altamente impactados." 

do ponto de vista do desenvolvimento, com base em sua experiência anterior com inreal no HoloLens 2, o Rodriguez estima que a MRTK para reduzir inreal o tempo total e o esforço necessário em sua parte pela metade. ele também observa como o MRTK pode ajudar os desenvolvedores que nunca trabalharam com HoloLens 2 começar. "quando outros desenvolvedores dizem que estão interessados em realidade misturada, recomendo que eles apenas pulem, instalem a pilha de desenvolvimento do HoloLens 2 e o MRTK, e vamos para ele. o MRTK torna a criação de um aplicativo rápido e fácil, e o editor visual inreal funciona tão bem que você nem precisa de um dispositivo HoloLens 2 para começar. Não é complicado, tudo simplesmente funciona. "

### <a name="potential-azure-service-enhancements"></a>Possíveis aprimoramentos de serviço do Azure

Lambert vê várias maneiras pelas quais os serviços mistos de realidade do Azure poderiam ser usados para aprimorar a experiência de Ford GT40, como usar âncoras espaciais do Azure para fornecer uma experiência multiusuário ancorada no mundo real. "Do ponto de vista criativo, as Âncoras Espaciais do Azure abrem uma gama totalmente nova de possibilidades por meio da capacidade que elas fornecem para mapear, persistir e restaurar conteúdo 3D ou pontos de interesse em nosso mundo físico", diz ele.

Lambert também prevê como o Azure Remote Rendering ou streaming do aplicativo do Azure pode ser usado para obter as taxas de quadros desejadas enquanto trabalha com modelos 3D mais detalhados e complexos. "Precisamos implementar alguns sombreadores personalizados altamente otimizados no Unreal para atingir nosso destino no dispositivo de 60 quadros por segundo", explica. "Com Azure Remote Rendering, poderíamos fazer muito mais e fazer isso muito mais facilmente, sem tanto trabalho necessário para otimizar modelos de polígono, repintar mapas de textura e assim por diante."

### <a name="endless-new-possibilities"></a>Novas possibilidades infinitas

Então, o que vem a seguir para o Final Feliz? Os comentários de Ela sobre a experiência de Gt40 de Ltda foram muito positivos, levando a mais discussões entre Happy Finish e Ela sobre projetos HoloLens 2 futuros. Fora de sua relação com o Gates, o Happy Finish já está iniciando um novo projeto no HoloLens 2, em que o MRTK para Unreal será um bloco de construção fundamental para a maioria da experiência do usuário. 

"Sempre mantemos uma abordagem independente de tecnologia para cada novo projeto, propondo qualquer conjunto de ferramentas mais adequado para ajudar o cliente a obter os resultados desejados", diz Cheetham. "Dito isso, o HoloLens 2 surgiu como o padrão ouro de fato para realidade misturada, especialmente na empresa, com a cabeça e a cabeça sobre todas as outras opções em termos de funcionalidades de dispositivo e da persistência do ecossistema de suporte."

De acordo com Cheetham, a pandêmia global acarretou um novo interesse enorme na realidade misturada imersiva entre clientes potenciais. "Estamos mais movimentados do que nunca, com cerca de 50% dos clientes potenciais abertos para discutir uma opção de realidade misturada", diz ele. "A chave é fazer com que as pessoas o experimentem. Você pode contar a eles sobre a realidade misturada o dia todo, mas quando você entrega a eles um HoloLens 2 para experimentar por si só, eles imediatamente conseguem como ele pode ser um alterador de jogos. O suporte para o Unreal Engine no HoloLens 2 só aumenta o valor que podemos oferecer, permitindo que ofereçamos experiências visualmente incríveis que certamente atenderão até mesmo aos clientes mais exigentes."

## <a name="try-it-out"></a>Experimente!

> [!div class="nextstepaction"]
> [Baixar o aplicativo Gt40 Det.](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

Confira nossa introdução [ao desenvolvimento de Realidade Misturada no HoloLens 2](../development.md) ou [MRTK para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) GitHub.

<!-- ## About the team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Lead Game Designer</i><br>Jack currently works on Mixed Reality experiences for Microsoft, including HoloLens 2 projects and AltspaceVR, and was previously a designer on the HoloLens platform team.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Summer Wu</b><br><i>Producer</i><br>Summer works on the mixed reality developer platform and heads the team’s Unreal Engine related efforts.</td>
</tr>
</table> -->