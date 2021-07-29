---
title: Experiência Ford GT40
description: Acompanhe enquanto exploramos a complicação do aplicativo Dev Gt40 de realidade misturada com o MRTK para HoloLens 2 no Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, implantação no dispositivo, PC, documentação, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
appliesto:
- HoloLens 2
ms.openlocfilehash: e634d75af92509372209d8e7c0cde2833127c128
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757188"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>A marcação da experiência Det. Gt40
![Imagem hero de Gt40 de Gt40](images/ford-gt40-hero_1920.jpg)

*"O pré-MRTK, desenvolver para o HoloLens 2 usando o Unreal era um pouco entediante porque todas as interações espaciais tinham que ser codificadas manualmente, em C++. O MRTK para Unreal tornou muitas dessas mesmas tarefas triviais. Eu estimava que ele recortou o tempo necessário para o protótipo inicial pela metade."* – Jose Ltda, Desenvolvedor de Software

*"A Experiência Det. Gt40 é uma prova de que um aplicativo de alta fidelidade HoloLens 2 pode ser concluído em apenas alguns meses, com um orçamento baixo, mas ainda fornece resultados altamente impactante."*  - Daniel Cheetham, Diretor de Inovação, Happy Finish

Usando o MRTK (Mixed Reality Toolkit) para Unreal, a empresa de produção criativo Happy Finish forneceu uma experiência de HoloLens 2 que fornece uma nova perspectiva sobre o Gt40, o carro de corrida confuso que venciam o 24 Horas de Le Mans!

Usando uma variedade de interações espaciais naturais e intuitivas, os usuários podem explorar a natureza, o desempenho e a engenharia do GT40– tudo entregue de uma maneira que aproveita a alta fidelidade visual fornecida pelo Unreal Engine. O desenvolvimento de software para todo o projeto foi concluído por um único desenvolvedor em menos de três meses, possibilitado pelo MRTK para o ambiente de design e script visual do Unreal.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Baixar o aplicativo Microsoft Store no HoloLens 2
Se você tiver HoloLens 2, poderá baixar e instalar diretamente o aplicativo em seu dispositivo.

<a href='//www.microsoft.com/store/apps/9p4vllktfvfp?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="the-ask"></a>A solicitação

A Happy Finish é uma das principais empresas de produção criativo do mundo, com uma base de clientes que inclui, Entre outras, a Microsoft, a Microsoft, a Netflix, a Vodafone e outros nomes domésticos. A empresa começou como uma agência de toque de fotos de alto nível, ramificando-se em filmes e CGI antes de estender sua excelência à excelência em narrativas imersivas com design espacial 3D e interação.

Em meados de 2020, a Microsoft abordou o Happy Finish para produzir um aplicativo de demonstração que poderia ajudar a demonstrar as possibilidades habilitadas pelo novo MRTK (Mixed Reality Toolkit) para Unreal, que se baseia no suporte para HoloLens 2 no Unreal Engine. Neste ponto, a empresa já tinha dois projetos bem-sucedidos do Unreal-on-HoloLens 2 sob seu controle. Ambos foram para uma marca de consumidor reconhecida globalmente, que escolheu o Unreal no HoloLens 2 para uma ferramenta de vendas de R&D/B2B interna para sua alta fidelidade visual, conforme necessário para melhor demonstrar os próprios produtos de alto nível do cliente.

Embora a solução em si seja deixada até Feliz Concluir, ela precisava atender a algumas diretrizes principais. Primeiro, ele precisava se concentrar em um cenário empresarial para ilustrar o utilitário do Unreal HoloLens 2 fora do setor de jogos. Em segundo lugar, ele tinha que ser somente dispositivo, o que significa que ele poderia servir como uma demonstração autônoma , sem exigir uma conexão de rede e potência de processamento externo para obter as taxas de quadros de destino e a qualidade visual. Em terceiro lugar, ele deve combinar o intervalo de interações intuitivas com suporte do MRTK em uma experiência perfeita e natural. Por fim, a solução proposta deve demonstrar a fidelidade visual inerente e outros benefícios do próprio Unreal Engine, como eficiências do sombreador. 

Considerando essas diretrizes, a Happy Finish começou a pensar sobre as possibilidades, com a ideia de uma experiência de realidade misturada que usava a interação espacial para comunicar o valor de um produto de nome de marca e alto valor. Depois de considerar uma variedade de objetos que incluíam relógios, câmeras, carros e jets particulares, a Happy Finish acabou decidindo sobre o Gt40 Det. Gt40, uma legenda automotiva que atingiu a notorção em 1966 quando Ela morou Em 24 Horas de Le Mans, conforme mostrado no filme de blockbuster de 2019, Alex vs. 

Depois de obter a entrada de Meio, um cliente Happy Finish existente, a empresa se des conjuntou para fornecer uma nova perspectiva sobre o ícone automotivo clássico.

## <a name="the-solution"></a>A solução

O trabalho começou em 7 de maio de 2020. Depois de obter os arquivos de modelo GT40, um artista 3D passou três semanas otimizando modelos de polígono, mapeamento UV, reainting de mapas de textura e condensando esses mapas no máximo de texturas possível. Um artista técnico trabalhou em paralelo para avaliar a saída do artista 3D, determinar tamanhos de textura ideais considerando as taxas de quadros de destino e descobrir a melhor maneira de aplicar sombreadores personalizados no Unreal. Todo esse trabalho de pré-produção foi feito para otimizar a experiência no dispositivo.

O diretor criativo Alex Lambert entrou na imagem depois que o trabalho de pré-produção foi concluído. Ele começou assistindo a Ela versus Clara, pensando em como unir uma narrativa em torno dos cenários e das interações. Ele também coletou referências visuais para o artista da interface do usuário, como imagens do painel GT40 e visuais do hiptrack le Mans e coletou gravações de áudio do GT40 em ação para o designer de som.

Com os ativos de pré-produção definidos e otimizados da narrativa em mãos, o desenvolvedor de software Também foi inscrito Em todos eles. Ela era a desenvolvedora dos dois projetos anteriores do Unreal-on-HoloLens 2 que o Happy Finish tinha feito, antes do MRTK para Unreal ter sido lançado.

O valor fornecido pelo MRTK para Unreal ficou evidente no início, ajudando o Paulo a entregar um protótipo inicial em uma semana. Ele implementou três cenários exclusivos, um para cada um dos principais aspectos do GT40 que Lambert identificou: sua sorte, seu desempenho e sua engenharia. Para cada cenário, Ela usou o MRTK para integrar os ativos 3D otimizados da fase de pré-produção em uma variedade de interações espaciais. 

Com o MRTK para Unreal, Ela criou cada cenário usando o Visual Unreal Motion Graphics (UMG) UI Designer em vez de ter que implementar tudo em C++. Ferramentas de experiência do usuário para [Unreal](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools), o plug-in que contém blocos de construção e componentes de experiência do usuário dentro do MRTK, deu a ele [blueprints](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) do Unreal para simulação de entrada, criando scripts visuais de interações com a mão, botões pressionáveis, manipulação de imagem 3D, superfície e muito mais– tudo dentro de um ambiente de design sem código, do tipo "arrastar e soltar".

"O pré-MRTK, desenvolver para o HoloLens 2 usando o Unreal foi um pouco entediante porque todas as interações espaciais tinham que ser codificadas manualmente, em C++", diz Ela. "O MRTK para Unreal tornou muitas dessas mesmas tarefas triviais. Eu estimava que ele recortou o tempo necessário para o protótipo inicial pela metade."

Com um protótipo em mãos, a equipe começou ierações semanais para refinar a experiência. "É quando o recurso Captura de Realidade Misturada e o Windows Portal de Dispositivos se tornaram realmente úteis", lembra Lambert. "Eu os usei para capturar minhas revisões de design, transmitir meus comentários para outras pessoas e colaborar com as alterações. Trabalhar em isolamento como isso teria sido impossível de fazer sem essas ferramentas."

![Aplicativo Unreal Editor– Gt40 em execução com componentes de roda colocados em sequência](images/ford-gt40-img-04.JPG)

Conforme Lambert solicitou alterações, como reposicionar elementos da interface do usuário ou alterar o comportamento de um botão, Ele os implementou. Embora algumas das alterações exigiam pequenos ajustes de código, a maioria delas foi tratada no designer visual do Unreal. "Eu estava surpresa com a rapidez com que eu poderia iterar", diz Ela. "Nenhum tempo foi perdido; Eu faria uma alteração no designer e pressione Play para exibi-la imediatamente no dispositivo. O MRTK realmente simplificou meu trabalho."

Ela também se lembra de ter se lembrado de como todas as ferramentas de desenvolvimento estavam prontas para produção. "Progredimos sem problemas desde o protótipo inicial até a produção final, sem precisar voltar e reimplementar ou otimizar as coisas no código", diz ele.  

## <a name="the-final-build"></a>O build final

A Happy Finish concluiu a produção da Experiência Gt40 da HoloLens 2 em 28 de julho de 2020, fornecendo uma nova perspectiva sobre o carro de corrida. A experiência começa com uma tela de boas-vindas e, em seguida, orienta o usuário a configurar uma âncora, segurando o logotipo do Jogador e colocando-o em uma superfície plana, como uma tabela ou área de trabalho. 

### <a name="beauty"></a>Beleza

O **segmento** de saúde leva o usuário para um configurador GT40, que exibe o GT40 em um carro giratório, semelhante a como um carro físico pode ser exibido em um show automotivo. O usuário pode aplicar diferentes opções de roda, escolher entre diferentes esquemas de cores e abrir e fechar as portas e o tronco (ou inicialização, como ele o chama no Reino Unido). Em toda a experiência de mulher, o usuário pode pegar o carro e manipulá-lo livremente para uma aparência mais próxima.

![GIF animado do configurador GT40 em execução em um dispositivo](images/ford-gt40-img-05.gif)

### <a name="performance"></a>Desempenho

O **segmento** de desempenho demonstra a velocidade e a durabilidade do GT40. O voiceover começa descrevendo como o carro foi desenvolvido e colocado em seus ritmos em Kingman, Arizona, provando a experiência, com visuais 3D mostrando o GT40 em movimento na faixa de teste. À medida que a introdução ao segmento de desempenho é concluída, o voiceover solicita que o usuário "Pressione o botão Le Mans para atingir a faixa de corrida".

![GIF animado do aplicativo de velocidade e durabilidade GT40 em execução em um dispositivo](images/ford-gt40-img-06.gif)

A segunda parte do segmento de desempenho demonstra o GT40 sob o intervalo de condições que os drivers podem experimentar nas 24 Horas de Le Mans, que é realizada anualmente no Circuito de la Sarthe, perto de Le Mans, França. Uma exibição 3D mostra o carro em movimento na faixa le mans, com botões fornecidos para fazer com que o carro seja mais rápido ou mais lento. Imagens do velocômetro e do tachômetro análogo do GT40 flutuam acima do modo de exibição de corrida, com mais telemetria de corrida exibida em segundo plano. O usuário pode alternar entre as exibições de dia e noite e entre condições de condução simulada e de umidade, fornecendo uma perspectiva realista e realista do que Ken Miles e os outros drivers GT40 experimentaram na corrida real.

### <a name="engineering"></a>Engenharia

O  segmento de engenharia da Experiência Gt40 de Gt40 apresenta uma das inovações de engenharia que ajudou o Paulo a ganhar a corrida: a capacidade de alterar os motores de motor e os pads em menos de um minuto, em comparação com os 20 a 30 minutos necessários para todas as outras equipes. Usando gestos intuitivos, o usuário pode manipular um modelo 3D detalhado da roda GT40 e do assembly de trava. Para expandir o assembly, o usuário escolhe uma chave de fenda, alinha-a ao bloqueio central na roda, gira-o no sentido anti-horário e, em seguida, o retira da roda. Outros gestos são usados para remover os cadeados e os pads do motor, substituí-los por novos, removê-los do assembly e ressecionar o bloqueio central. Em segundo plano, um temporizador exibe o tempo decorrido, deixando o usuário ver se ele pode concluir o processo tão rapidamente quanto a equipe de pit em Le Mans.

![GIF animado da experiência de engenharia GT40 em execução em um dispositivo](images/ford-gt40-img-07.gif)

A Experiência Com o Gt40 da Microsoft pode ser baixada da [Microsoft Store,](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab)permitindo que qualquer pessoa com um HoloLens 2 explore como o Happy Finish traz uma nova perspectiva para um carro de corrida descarado.

### <a name="getting-impressive-visual-fidelity"></a>Obter fidelidade visual impressionante

Embora o intervalo de interações espaciais com suporte da Experiência Gt40 de Gt40 seja impressionante por conta própria, a criatividade e a fidelidade visual que a experiência oferece é o que realmente a torna brilhante. Por meio de sua otimização de modelos 3D e do uso de sombreadores personalizados do Unreal, a Happy Finish atingiu seu destino de 60 quadros por segundo, mesmo com o segmento de desempenho do aplicativo se aproximando de 315.000 polígonos de tamanho. 

"Estou muito feliz com como conseguimos reunir um conjunto de interações intuitivas e fluidas em uma narrativa coerente e envolvente", diz Lambert. "Claramente, o poder do Unreal Engine no HoloLens 2 abre um novo mundo de oportunidade para experiências de realidade misturada mais surpreendentes e empolgantes. A fidelidade visual nãocompromada nem sempre é a meta final para aplicativos empresariais no HoloLens 2, mas quando é, o suporte para Unreal no HoloLens 2 se torna invasível."

### <a name="rapid-solution-delivery"></a>Entrega rápida de solução

Tão impressionante quanto a Experiência gt40 do usuário final é a rapidez com que o Happy Finish a entrega, com todo o projeto, da pré-produção à entrega final, foi concluída em pouco menos de 12 semanas. Em resumo, o projeto consumiu 1088 horas de esforço, dividido da seguinte maneira: diretor criativo (80 horas), designer de UX (56 horas), designer de interface do usuário (40 horas), designer de som (40 horas), 3D/técnico (328 horas), desenvolvedor de software (408 horas), diretor técnico (40 horas), produtor (56 horas) e garantia de qualidade (40 horas).

"Em geral, estamos muito próximos de nossas estimativas de projeto originais", diz Daniel Cheetham, Diretor de Inovação da Happy Finish, que é responsável pela divisão interativa da empresa. "A Experiência Det. Gt40 é uma prova de que um aplicativo de alta fidelidade HoloLens 2 pode ser concluído em apenas alguns meses, com um orçamento baixo, mas ainda fornece resultados altamente impactante." 

De uma perspectiva de desenvolvimento, com base em sua experiência anterior com o Unreal no HoloLens 2, Ele estima que o MRTK para Unreal recortou o tempo total e o esforço necessários de sua parte pela metade. Ele também observa como o MRTK pode ajudar os desenvolvedores que nunca trabalharam com HoloLens 2. "Quando outros desenvolvedores dizem que estão interessados em realidade misturada, encorato-os a simplesmente entrar, instalar a pilha de desenvolvimento do HoloLens 2 e o MRTK e ir em frente. O MRTK torna a criação de um aplicativo rápida e fácil, e o editor visual do Unreal funciona tão bem que você nem precisa de um HoloLens 2 para começar. Não é complicado, tudo simplesmente funciona."

### <a name="potential-azure-service-enhancements"></a>Aprimoramentos potenciais do serviço do Azure

Lambert vê várias maneiras pelas quais os serviços de realidade misturada do Azure podem ser usados para aprimorar a experiência de Gt40 do Azure, como o uso de Âncoras Espaciais do Azure para fornecer uma experiência de vários usuários ancorada no mundo real. "De uma perspectiva criativa, as âncoras espaciais do Azure abrem uma variedade totalmente nova de possibilidades por meio da capacidade que eles fornecem para mapear, persistir e restaurar o conteúdo 3D ou pontos de interesse em nosso mundo físico," ele diz.

O Lambert também prevê como a renderização remota do Azure ou o streaming do aplicativo do Azure pode ser usado para atingir as taxas de quadros desejadas ao trabalhar com modelos 3D mais detalhados e complexos. "Tivemos que implementar alguns sombreadores personalizados altamente otimizados em inreal para atingir nosso destino no dispositivo de 60 quadros por segundo", ele explica. "Com a renderização remota do Azure, poderíamos fazer muito mais – e fazer isso muito mais facilmente, sem o trabalho necessário para otimizar os modelos de polígono, redesenhar mapas de textura e assim por diante".

### <a name="endless-new-possibilities"></a>Novas possibilidades infinitas

Então, o que vem a seguir para um bom término? os comentários da ford sobre a experiência da ford GT40 foram intensamente positivos, levando a discussões adicionais entre o feliz término e a Ford em projetos futuros HoloLens 2. fora de sua relação com o Ford, o bom término já está começando a iniciar um novo projeto no HoloLens 2, em que o MRTK for inreal será um bloco de construção básico para a maior parte da experiência do usuário. 

"Sempre mantivemos uma abordagem independente de tecnologia para cada novo projeto, propondo o que o conjunto de ferramentas é mais adequado para ajudar o cliente a obter os resultados desejados", diz Cheetham. "dito isso, HoloLens 2 surgiu como o padrão ouro de verdade para realidade misturada, especialmente na empresa, a ombros de ponta e a outra acima de todas as outras opções em termos de recursos de dispositivo e da abrangência do ecossistema de suporte".

De acordo com o Cheetham, o pandemia global impulsionava grandes interesse na realidade misturada de imersão entre clientes em potencial. "Estamos mais ocupados do que nunca, com cerca de 50% dos clientes potenciais sendo abertos para discutir uma opção de realidade misturada", ele diz. "A chave é fazer com que as pessoas experimentem. você pode informá-los sobre realidade misturada o dia todo, mas quando você entrega um HoloLens 2 para experimentar, eles imediatamente obtêm como ele pode ser um alterador de jogo. o suporte para o mecanismo inreal no HoloLens 2 aumenta apenas o valor que podemos oferecer, permitindo que possamos fornecer experiências visualmente impressionantes que têm a certeza de satisfazer até os clientes mais exigentes. "

## <a name="try-it-out"></a>Experimente!

> [!div class="nextstepaction"]
> [Baixe o aplicativo Ford GT40](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

confira nossa [introdução ao desenvolvimento de realidade misturada no HoloLens 2](../development.md) ou [MRTK para o inreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) em GitHub.

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