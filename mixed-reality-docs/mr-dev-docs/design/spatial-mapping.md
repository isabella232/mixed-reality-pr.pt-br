---
title: mapeamento espacial
description: O mapeamento espacial fornece uma representação detalhada das superfícies do mundo real no ambiente em volta do HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: mapeamento espacial, HoloLens, realidade mista, reconstrução de superfície, malha, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada, compreensão da cena, malha mundial, oclusão, física, navegação, observador de superfície, renderização, processamento de malha
ms.openlocfilehash: 3268f25f86cdfea3aa1ae0b77c4fbeb9aa0ce1b9
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196421"
---
# <a name="spatial-mapping"></a>mapeamento espacial

O mapeamento espacial fornece uma representação detalhada das superfícies do mundo real no ambiente em todo o HoloLens, permitindo que os desenvolvedores criem uma experiência de realidade misturada convincente. Ao mesclar o mundo real com o mundo virtual, um aplicativo pode fazer com que os hologramas pareçam reais. Os aplicativos também podem se alinhar naturalmente com as expectativas do usuário, fornecendo comportamentos e interações do mundo real.

<br>

>[!VIDEO https://www.youtube.com/embed/zff2aQ1RaVo]

## <a name="device-supports"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>mapeamento espacial</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>


## <a name="why-is-spatial-mapping-important"></a>Por que o mapeamento espacial é importante?

O mapeamento espacial torna possível posicionar objetos em superfícies reais. Isso ajuda a ancorar objetos no mundo do usuário e aproveita as indicações de profundidade do mundo real. Occluding seus hologramas com base em outros hologramas e objetos do mundo real ajudam a convencer o usuário de que esses hologramas estão na verdade em seu espaço. Os hologramas flutuam no espaço ou quando se movem com o usuário não se sentirão reais. Quando possível, coloque os itens em conforto.

Visualize superfícies ao colocar ou mover hologramas (use uma grade projetada). Isso ajuda os usuários a saber onde eles podem posicionar melhor seus hologramas e mostra se o ponto em que eles estão tentando posicionar o holograma não está mapeado. Você pode "itens do mural" em direção ao usuário se eles acabarem em muito um ângulo.

## <a name="conceptual-overview"></a>Visão geral conceitual

![Superfícies de malha que abrangem uma sala](images/SurfaceReconstruction.jpg)<br>
*Um exemplo de uma malha de mapeamento espacial que abrange uma sala*

Os dois tipos de objeto primários usados para o mapeamento espacial são o ' observador de superfície espacial ' e a ' superfície espacial '.

O aplicativo fornece o observador de superfície espacial com um ou mais volumes delimitadores para definir as regiões de espaço em que o aplicativo deseja receber dados de mapeamento espacial. Para cada um desses volumes, o mapeamento espacial fornecerá ao aplicativo um conjunto de Superfícies Espaciais.

Esses volumes podem ser estacionários (em um local fixo baseado no mundo real) ou podem ser anexados ao HoloLens (eles se movem, mas não giram, com o HoloLens conforme ele se move pelo ambiente). Cada superfície espacial descreve superfícies do mundo real em um pequeno volume de espaço, representado como uma malha de triângulo anexada a um sistema de coordenadas [espaciais bloqueado pelo mundo.](coordinate-systems.md)

À medida que o HoloLens coleta novos dados sobre o ambiente e conforme ocorrem alterações no ambiente, as superfícies espaciais aparecerão, desaparecerão e mudarão.

## <a name="spatial-awareness-design-concepts-demo"></a>Demonstração de conceitos de design de Reconhecimento Espacial

Se você quiser ver os conceitos de design de Reconhecimento Espacial em ação, confira nossa demonstração de vídeo **Designing Holograms – Spatial Awareness** abaixo. Quando terminar, continue para obter uma análise mais detalhada de tópicos específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Este vídeo foi tirado do aplicativo "Projetando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui.](https://aka.ms/dhapp)*

## <a name="spatial-mapping-vs-scene-understanding-worldmesh"></a>Mapeamento espacial vs. Noções básicas sobre a cena WorldMesh

Para o HoloLens 2, é possível consultar uma versão estática dos dados de mapeamento espacial usando o [SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) de Compreensão de cena (configuração EnableWorldMesh). Aqui estão as diferenças entre duas maneiras de acessar os dados de mapeamento espacial:
* API de Mapeamento Espacial:
   * Intervalo limitado: os dados de mapeamento espacial disponíveis para aplicativos em um tamanho limitado armazenado em cache "bolha" em torno do usuário.
   * Fornece atualizações de baixa latência de regiões de malha alteradas por meio de eventos SurfacesChanged.
   * Nível variável de detalhes controlado pelo parâmetro Triângulos por Medidor Cúbico.
* SDK de compreensão de cena:
   * Intervalo ilimitado – fornece todos os dados de mapeamento espacial digitalizados dentro do raio de consulta.
   * Fornece um instantâneo estático dos dados de mapeamento espacial. Obter os dados atualizados de mapeamento espacial requer a execução de uma nova consulta para toda a malha.
   * Nível consistente de detalhes controlado pela configuração RequestedMeshLevelOfDetail.

## <a name="what-influences-spatial-mapping-quality"></a>O que influencia a qualidade do mapeamento espacial?

Vários fatores, detalhados [aqui](/hololens/hololens-environment-considerations), podem afetar a frequência e a severidade desses erros.  No entanto, você deve projetar seu aplicativo para que o usuário possa atingir suas metas mesmo na presença de erros nos dados de mapeamento espacial.

## <a name="common-usage-scenarios"></a>Cenários de uso comuns

![Ilustrações de cenários de uso de mapeamento espacial comum: posicionamento, oclusão, física e navegação](images/sm-concepts-1000px.png)

### <a name="placement"></a>Posicionamento

O mapeamento espacial fornece aos aplicativos a oportunidade de apresentar formas naturais e familiares de interação para o usuário; o que poderia ser mais natural do que colocar seu telefone na mesa?

Restringir o posicionamento de hologramas (ou mais geralmente, qualquer seleção de locais espaciais) para se situar em superfícies fornece um mapeamento natural de 3D (ponto no espaço) para 2D (ponto na superfície). Isso reduz a quantidade de informações que o usuário precisa fornecer ao aplicativo e torna as interações do usuário mais rápidas, fáceis e mais precisas. Isso é verdade porque a "distância" não é algo que estamos acostumados a se comunicar fisicamente com outras pessoas ou computadores. Quando apontamos para o dedo, estamos especificando uma direção, mas não uma distância.

Uma limitação importante aqui é que, quando um aplicativo infere distância da direção (por exemplo, fazendo uma Raycast ao longo da direção do olhar do usuário para encontrar a superfície espacial mais próxima), isso deve produzir resultados que o usuário pode prever de forma confiável. Caso contrário, o usuário perderá sua noção de controle e isso pode rapidamente se tornar frustrante. Um método que ajuda com isso é fazer várias raycasts em vez de apenas uma. Os resultados agregados devem ser mais suaves e mais previsíveis, menos suscetíveis a influenciar de resultados transitórios "de exceção" (como pode ser causado por raios que passam por pequenos orifícios ou atingindo pequenos bits de geometria que o usuário não está ciente). A agregação ou a suavização também pode ser executada ao longo do tempo; por exemplo, você pode limitar a velocidade máxima na qual um holograma pode variar em distância do usuário. Simplesmente limitar o valor de distância mínima e máxima também pode ajudar, para que o holograma que está sendo movido não de repente vá para a distância ou volte para o rosto do usuário.

Os aplicativos também podem usar a forma e a direção das superfícies para orientar o posicionamento do holograma. Uma mesa holográfica não deve entrar pelas paredes e deve ficar em liberação com o chão, mesmo que seja um pouco desigual. Esse tipo de funcionalidade provavelmente dependeria do uso de colisões físicas em vez de raycasts, no entanto, preocupações semelhantes se aplicarão. Se o holograma que está sendo colocado tiver muitos polígonos pequenos que se destacam, como os pés em uma mesa, pode fazer sentido expandir a representação física desses polígonos para algo mais amplo e mais suave para que eles possam deslizar sobre superfícies espaciais sem a necessidade de se descontinuar.

Em seu extremo, a entrada do usuário pode ser simplificada inteiramente e superfícies espaciais podem ser usadas para fazer o posicionamento totalmente automático do holograma. Por exemplo, o aplicativo pode colocar uma opção de luz holográfica em algum lugar na parede para o usuário pressionar. A mesma ressalva sobre a previsibilidade se aplica duplamente aqui; se o usuário espera controle sobre o posicionamento do holograma, mas o aplicativo nem sempre coloca os hologramas onde ele espera (se a opção de luz aparecer em algum lugar que o usuário não possa alcançar), essa será uma experiência frustrante. Na verdade, pode ser pior fazer o posicionamento automático que exige a correção do usuário algumas vezes, do que apenas exigir que o usuário sempre faça o posicionamento por conta própria; como o posicionamento automático bem-sucedido *é esperado,* a correção manual parece uma carga!

Observe também que a capacidade de um aplicativo usar superfícies espaciais para posicionamento depende muito da experiência de [verificação do aplicativo.](spatial-mapping.md#the-environment-scanning-experience) Se uma superfície não tiver sido digitalizada, ela não poderá ser usada para posicionamento. É responsabilidade do aplicativo deixar isso claro para o usuário, para que ele possa ajudar a verificar novas superfícies ou selecionar um novo local.

Os comentários visuais para o usuário são de extrema importância durante o posicionamento. O usuário precisa saber onde o holograma é baseado na superfície mais próxima com efeitos de [aterramento](spatial-mapping.md#visualization). Eles devem entender por que a movimentação de seu holograma está sendo restrita (por exemplo, devido a colisões com outra superfície próxima). Se eles não conseguirem colocar um holograma no local atual, os comentários visuais devem deixá-lo claro por que não. Por exemplo, se o usuário estiver tentando posicionar um Holographic sofá preso na parede, as partes do sofá que estão atrás da parede devem pulsater em uma cor irritado. Ou inversamente, se o aplicativo não conseguir encontrar uma superfície espacial em um local onde o usuário possa ver uma superfície do mundo real, o aplicativo deverá tornar isso claro. A ausência óbvia de um efeito de aterramento nessa área pode atingir essa finalidade.

### <a name="occlusion"></a>Oclusão

Um dos principais usos das superfícies de mapeamento espacial é simplesmente para os hologramas occlude. Esse comportamento simples tem um grande impacto sobre o realm de hologramas percebido, ajudando a criar um sensor de visceral que realmente inempolga o mesmo espaço físico que o usuário.

O oclusão também fornece informações para o usuário; Quando um holograma parece ser obstruídodo por uma superfície do mundo real, isso fornece comentários visuais adicionais sobre o local espacial desse holograma no mundo. Por outro lado, o oclusão também pode *ocultar* informações de forma útil do usuário; os hologramas occluding por trás das paredes podem reduzir a desordem Visual de uma maneira intuitiva. Para ocultar ou revelar um holograma, o usuário precisa apenas mover sua cabeça.

O oclusão também pode ser usado para obter as principais expectativas de uma interface do usuário natural com base em interações físicas familiares; se um holograma for obstruídodo por uma superfície, isso ocorre porque essa superfície é sólida e, portanto, o usuário deve esperar que o holograma *colidirá* com essa superfície e não passará por ela.

Às vezes, oclusão de hologramas é indesejável. Se um usuário precisar interagir com um holograma, ele precisará vê-lo, mesmo se ele estiver atrás de uma superfície do mundo real. Nesses casos, geralmente faz sentido renderizar esse holograma de maneira diferente quando ele é ocluído (por exemplo, reduzindo seu brilho). Dessa forma, o usuário pode localizar visualmente o holograma, mas ele ainda vai saber que está por trás de algo.

### <a name="physics"></a>Física

O uso da simulação de física é outra maneira  na qual o mapeamento espacial pode ser usado para reforçar a presença de hologramas no espaço físico do usuário. Quando minha bola de borracha holográfica rola de forma realista para fora da minha mesa, salta pelo chão e desaparece sob o diviso, pode ser difícil para mim acreditar que ela não está lá.

A simulação de física também fornece a oportunidade para um aplicativo usar interações naturais e familiares baseadas em física. Mover uma peça de móveis holográficos no chão provavelmente será mais fácil para o usuário se o móvel responder como se estivesse deslizando pelo chão com a inércia e o atrito apropriados.

Para gerar comportamentos físicos realistas, você [](spatial-mapping.md#mesh-processing) provavelmente precisará fazer algum processamento de malha, como preencher os orifícios, remover desilusão flutuante e suavizar superfícies aproximadas.

Você também precisará considerar como a experiência de verificação do aplicativo influencia [sua](spatial-mapping.md#the-environment-scanning-experience) simulação de física. Em primeiro lugar, as superfícies ausentes não colidem com nada; o que acontece quando a bola de borracha rola para baixo e para fora do final do mundo conhecido? Em segundo lugar, você precisa decidir se continuará respondendo às alterações no ambiente ao longo do tempo. Em alguns casos, você vai querer responder o mais rápido possível; digamos que o usuário está usando portas e móveis como móveis móveis em defesa contra uma tempestade de setas de entrada de Roman. No entanto, em outros casos, talvez você queira ignorar novas atualizações; conduzir seu carro desportivo holográfico ao redor da pista de corrida no chão pode, de repente, não ser tão divertido se o cachorro decidir ficar no meio da faixa.

### <a name="navigation"></a>Navegação

Os aplicativos podem usar dados de mapeamento espacial para conceder aos Holographic caracteres (ou agentes) a capacidade de navegar pelo mundo real da mesma maneira que uma pessoa real. Isso pode ajudar a reforçar a presença de caracteres Holographic restringindo-os ao mesmo conjunto de comportamentos naturais e conhecidos que os do usuário e seus amigos.

Os recursos de navegação também podem ser úteis para os usuários. Depois que um mapa de navegação tiver sido criado em uma determinada área, ele poderá ser compartilhado para fornecer instruções de Holographic para novos usuários que não conhecem esse local. Esse mapa poderia ser criado para ajudar a manter o tráfego do básicos em trânsito sem problemas, ou para evitar acidentes em locais perigosos, como sites de construção.

Os principais desafios técnicos envolvidos na implementação da funcionalidade de navegação serão a detecção confiável de superfícies que poderão ser perfeitas (as pessoas não se movimentam nas tabelas!) e a adaptação normal às alterações no ambiente (as pessoas não percorrem as portas fechadas!). A malha pode exigir algum [processamento](spatial-mapping.md#mesh-processing) antes de ser utilizável para o planejamento e a navegação de caminho por um caractere virtual. Suavizar a malha e remover hallucinations pode ajudar a evitar que os caracteres se tornem presos. Você também pode desejar simplificar drasticamente a malha para acelerar os cálculos de navegação e de planejamento de caminho do caractere. Esses desafios receberam muita atenção no desenvolvimento da tecnologia de jogos de vídeo, e há uma infinidade de literatura de pesquisa disponível sobre esses tópicos.

A funcionalidade interna NavMesh no Unity não pode ser usada com superfícies de mapeamento espacial. Isso ocorre porque as superfícies de mapeamento espacial não são conhecidas até que o aplicativo seja iniciado, mas os arquivos de dados de NavMesh precisam ser gerados a partir dos ativos de origem antes do tempo. Observe também que, o sistema de mapeamento espacial não fornecerá [informações sobre superfícies longe](spatial-mapping.md#the-environment-scanning-experience) da localização atual do usuário. Portanto, o aplicativo deve "se lembrar" dessas superfícies se for criar um mapa de uma área grande.

### <a name="visualization"></a>Visualização

Na maioria das vezes, é apropriado que as superfícies espaciais sejam invisíveis; para minimizar a desorganização visual e permitir que o mundo real fale por si mesmo. No entanto, às vezes é útil visualizar as superfícies de mapeamento espacial diretamente, apesar de suas contrapartes do mundo real estarem visíveis.

Por exemplo, quando o usuário está tentando colocar um holograma em uma superfície (colocando um gabinete holográfico na parede, digamos) pode ser útil 'terra' no holograma, lançando uma sombra na superfície. Isso dá ao usuário uma noção muito mais clara da proximidade física exata entre o holograma e a superfície. Este também é um exemplo da prática mais geral de "visualizar" visualmente uma alteração antes de o usuário se comprometer com ela.

Ao visualizar superfícies, o aplicativo pode compartilhar com o usuário sua compreensão do ambiente. Por exemplo, um jogo de tabuleiro holográfico pode visualizar as superfícies horizontais identificadas como 'tabelas', para que o usuário saiba onde deve ir para interagir.

Visualizar superfícies pode ser uma maneira útil de mostrar ao usuário espaços próximos que estão ocultos da exibição. Isso pode fornecer uma maneira de dar ao usuário acesso à sua cozinha (e a todos os seus hologramas contidos) de sua sala de estar.

As malhas de superfície fornecidas pelo mapeamento espacial podem não ser particularmente 'limpas'. É importante visualizá-los adequadamente. Cálculos de iluminação tradicionais podem realçar erros em normais da superfície de maneira visualmente distração, enquanto texturas 'limpas' projetadas na superfície podem ajudar a dar a ela uma aparência de tidier. Também é possível fazer o processamento de malha [para](spatial-mapping.md#mesh-processing) melhorar as propriedades da malha, antes que as superfícies sejam renderizadas.

> [!NOTE]
> O HoloLens 2 implementa um novo [Runtime](scene-understanding.md)de Compreensão de Cena, que fornece aos desenvolvedores de Realidade Misturada uma representação de ambiente estruturada e de alto nível projetada para simplificar a implementação de posicionamento, oclusão, física e navegação.

## <a name="using-the-surface-observer"></a>Usando o Observador da Superfície

O ponto de partida para o mapeamento espacial é o observador da superfície. O fluxo do programa é o seguinte:
* Criar um objeto de observador de superfície
   * Forneça um ou mais volumes espaciais para definir as regiões de interesse em que o aplicativo deseja receber dados de mapeamento espacial. Um volume espacial é simplesmente uma forma que define uma região de espaço, como uma esfera ou uma caixa.
   * Use um volume espacial com um sistema de coordenadas espaciais bloqueados pelo mundo para identificar uma região fixa do mundo físico.
   * Use um volume espacial, atualizado cada quadro com um sistema de coordenadas espaciais bloqueadas pelo corpo, para identificar uma região de espaço que se move (mas não gira) com o usuário.
   * Esses volumes espaciais podem ser alterados posteriormente a qualquer momento, à medida que o status do aplicativo ou do usuário é alterado.
* Usar sondagem ou notificação para recuperar informações sobre superfícies espaciais
   * Você pode ' sondar ' o observador de superfície para o status da superfície espacial a qualquer momento. Em vez disso, você pode se registrar para o evento ' superfícies alteradas ' do observador de superfície, que notificará o aplicativo quando as superfícies espaciais forem alteradas.
   * Para um volume espacial dinâmico, como o modo de exibição frustum ou um volume bloqueado por corpo, os aplicativos precisarão sondar as alterações em cada quadro definindo a região de interesse e, em seguida, obtendo o conjunto atual de superfícies espaciais.
   * Para um volume estático, como um cubo protegido por mundo que cobre uma única sala, os aplicativos podem se registrar para que o evento ' superfícies alteradas ' seja notificado quando as superfícies espaciais dentro desse volume podem ter sido alteradas.
* Alterações de superfícies de processo
   * Itere o conjunto de superfícies espaciais fornecido.
   * Classifique as superfícies espaciais como adicionadas, alteradas ou removidas.
   * Para cada superfície espacial adicionada ou alterada, se apropriado, envie uma solicitação assíncrona para receber a malha atualizada que representa o estado atual da superfície no nível de detalhe desejado.
* Processe a solicitação de malha assíncrona (mais detalhes nas seções a seguir).

## <a name="mesh-caching"></a>Cache de malha

As superfícies espaciais são representadas por malhas de triângulo densas. Armazenar, renderizar e processar essas malhas pode consumir recursos de computação e armazenamento significativos. Assim, cada aplicativo deve adotar um esquema de cache de malha apropriado para suas necessidades, a fim de minimizar os recursos usados para processamento e armazenamento de malha. Esse esquema deve determinar quais malhas manter e quais descartar e quando atualizar a malha para cada superfície espacial.

Muitas das considerações discutidas informarão diretamente como seu aplicativo deve abordar o cache de malha. Você deve considerar como o usuário se move pelo ambiente, quais superfícies são necessárias, quando diferentes superfícies serão observadas e quando as alterações no ambiente devem ser capturadas.

Ao interpretar o evento 'superfícies alteradas' fornecido pelo observador de superfície, a lógica básica de cache de malha é a seguinte:
* Se o aplicativo vir uma ID de superfície espacial que não tenha visto antes, ele deverá tratá-la como uma nova superfície espacial.
* Se o aplicativo vir uma superfície espacial com uma ID conhecida, mas com um novo tempo de atualização, ele deverá tratá-la como uma superfície espacial atualizada.
* Se o aplicativo não vir mais uma superfície espacial com uma ID conhecida, ele deverá tratá-la como uma superfície espacial removida.

Em seguida, é decisão de cada aplicativo fazer as seguintes escolhas:
* Para novas superfícies espaciais, a malha deve ser solicitada?
   * Geralmente, a malha deve ser solicitada imediatamente para novas superfícies espaciais, o que pode fornecer novas informações úteis para o usuário.
   * No entanto, novas superfícies espaciais próximas e na frente do usuário devem receber prioridade e sua malha deve ser solicitada primeiro.
   * Se a nova malha não for necessária, se, por exemplo, o aplicativo tiver 'congelado' permanente ou temporariamente seu modelo do ambiente, ele não deverá ser solicitado.
* Para superfícies espaciais atualizadas, a malha deve ser solicitada?
   * Superfícies espaciais atualizadas próximas e na frente do usuário devem receber prioridade e sua malha deve ser solicitada primeiro.
   * Também pode ser apropriado dar maior prioridade a novas superfícies do que às superfícies atualizadas, especialmente durante a experiência de verificação.
   * Para limitar os custos de processamento, os aplicativos podem querer limitar a taxa na qual eles processam atualizações em superfícies espaciais.
   * Pode ser possível inferir que as alterações em uma superfície espacial sejam secundárias, por exemplo, se os limites da superfície forem pequenos, caso em que a atualização pode não ser importante para ser processada.
   * As atualizações para superfícies espaciais fora da região atual de interesse do usuário podem ser ignoradas inteiramente, embora, nesse caso, seja mais eficiente modificar os volumes delimitadores espaciais em uso pelo observador de superfície.
* Para superfícies espaciais removidas, a malha deve ser descartada?
   * Em geral, a malha deve ser descartada imediatamente para superfícies espaciais removidas, de forma que o holograma oclusão permaneça correto.
   * No entanto, se o aplicativo tiver motivo para acreditar que uma superfície espacial reaparecerá em breve (com base no design da experiência do usuário), poderá ser mais eficiente mantê-la do que descartar sua malha e recriá-la mais tarde.
   * Se o aplicativo estiver criando um modelo de grande escala do ambiente do usuário, talvez não queira descartar todas as malhas. No entanto, ele ainda precisará limitar o uso de recursos, possivelmente colocando em spool as malhas em disco, pois as superfícies espaciais desaparecem.
   * Alguns eventos relativamente raros durante a geração de superfície espacial podem fazer com que superfícies espaciais sejam substituídas por novas superfícies espaciais em um local semelhante, mas com IDs diferentes. Assim, os aplicativos que optam por não descartar uma superfície removida devem ter cuidado para não terminar com várias malhas de superfícies espaciais altamente sobrepostas que abrangem o mesmo local.
* A malha deve ser descartada para outras superfícies espaciais?
   * Mesmo que exista uma superfície espacial, se ela não for mais útil para a experiência do usuário, ela deverá ser descartada. Por exemplo, se o aplicativo "substituir" a sala do outro lado de um porta com um espaço virtual alternativo, as superfícies espaciais nessa sala não serão mais importantes.

Aqui está um exemplo de estratégia de cache de malha, usando histerese espacial e temporal:
* Considere um aplicativo que deseja usar um volume espacial em forma de frustum de interesse que segue o olhar do usuário à medida que ele olhar ao redor e dar uma volta.
* Uma superfície espacial pode desaparecer temporariamente desse volume simplesmente porque o usuário se parece com a superfície ou fica mais distante dela... apenas para olhar para trás ou se aproximar novamente um momento depois. Nesse caso, descartar e re-criar a malha para essa superfície representa muitos processamentos redundantes.
* Para reduzir o número de alterações processadas, o aplicativo usa dois observadores de superfície espacial, um contido dentro do outro. O volume maior é esférico e segue o usuário 'lazily'; ele só se move quando necessário para garantir que seu centro está a 2,0 metros do usuário.
* Malhas de superfície espacial novas e atualizadas são sempre processadas do observador de superfície interna menor, mas as malhas são armazenadas em cache até desaparecerem do observador de superfície externa maior. Isso permite que o aplicativo evite processar muitas alterações redundantes devido à movimentação do usuário local.
* Como uma superfície espacial também pode desaparecer temporariamente devido à perda de acompanhamento, o aplicativo também adia o descarte de superfícies espaciais removidas durante a perda de acompanhamento.
* Em geral, um aplicativo deve avaliar a diferença entre o processamento reduzido de atualizações e o aumento do uso de memória para determinar sua estratégia ideal de cache.

## <a name="rendering"></a>Renderização

Há três maneiras principais pelas quais malhas de mapeamento espacial tendem a ser usadas para renderização:
* Para visualização da superfície
   * Geralmente, é útil visualizar superfícies espaciais diretamente. Por exemplo, a transmissão de "sombras" de objetos em superfícies espaciais pode fornecer comentários visuais úteis para o usuário enquanto eles estão colocando hologramas em superfícies.
   * Uma coisa a ter em mente é que malhas espaciais são diferentes do tipo de malha que um artista 3D pode criar. A topologia do triângulo não será tão "limpa" quanto a topologia criada por humanos e a malha sofrerá vários [erros.](spatial-mapping.md#what-influences-spatial-mapping-quality)
   * Para criar uma estética visual agradável, talvez você queira fazer algum [processamento de malha](spatial-mapping.md#mesh-processing), por exemplo, para preencher buracos ou Normals de superfície suave. Você também pode querer usar um sombreador para projetar texturas criadas pelo artista em sua malha, em vez de Visualizar diretamente a topologia de malha e os normais.
* Para os hologramas occluding por trás das superfícies do mundo real
   * As superfícies espaciais podem ser renderizadas em uma passagem somente de profundidade, o que afeta apenas o [buffer de profundidade](/windows/win32/direct3d9/depth-buffers) e não afeta os destinos de renderização de cor.
   * Isso força o buffer de profundidade a occlude subsequentemente processará os hologramas por trás das superfícies espaciais. A oclusão precisa dos hologramas melhora o sentido de que os hologramas realmente existem dentro do espaço físico do usuário.
   * Para habilitar a renderização de profundidade, atualize seu estado de mesclagem para definir o [RenderTargetWriteMask](/windows/win32/api/d3d11_1/ns-d3d11_1-d3d11_render_target_blend_desc1) como zero para todos os destinos de renderização de cor.
* Para modificar a aparência de hologramas obstruído por superfícies do mundo real
   * Normalmente, a geometria renderizada fica oculta quando é obstruído. Isso é feito definindo a função Depth em seu [estado de estêncil de profundidade](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc) como "menor ou igual a", o que faz com que a geometria fique visível apenas onde está **mais perto** da câmera do que toda a geometria renderizada anteriormente.
   * No entanto, pode ser útil manter determinada geometria visível mesmo quando é obstruído e modificar sua aparência quando obstruído como uma forma de fornecer comentários visuais ao usuário. Por exemplo, isso permite que o aplicativo mostre ao usuário o local de um objeto, tornando-o claro que está por trás de uma superfície do mundo real.
   * Para conseguir isso, renderize a geometria uma segunda vez com um sombreador diferente que cria a aparência desejada de ' obstruído '. Antes de renderizar a geometria pela segunda vez, faça duas alterações em seu [estado de estêncil de profundidade](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc). Primeiro, defina a função Depth como "maior que ou igual a" para que a geometria seja visível somente quando ela estiver **além** da câmera do que toda a geometria renderizada anteriormente. Em segundo lugar, de acordo com DepthWriteMask como zero, para que o buffer de profundidade  não seja modificado (o buffer de profundidade deve continuar representando a profundidade da geometria mais próxima da câmera).

[O](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) desempenho é uma preocupação importante ao renderizar malhas de mapeamento espacial. Aqui estão algumas técnicas de desempenho de renderização específicas para renderizar malhas de mapeamento espacial:
* Ajustar a densidade do triângulo
   * Ao solicitar malhas de superfície espacial do observador de superfície, solicite a densidade mais baixa de malhas de triângulo que serão suficientes para suas necessidades.
   * Pode fazer sentido variar a densidade do triângulo em uma superfície por superfície, dependendo da distância da superfície do usuário e sua relevância para a experiência do usuário.
   * A redução das contagens de triângulo reduzirá o uso de memória e os custos de processamento de vértice na GPU, embora isso não afete os custos de processamento de pixel.
* Usar o descarte de frustum
   * O descarte de Frustum ignora objetos de desenho que não podem ser vistos porque estão fora do frustum de exibição atual. Isso reduz os custos de processamento de CPU e GPU.
   * Como a redução é executada por malha e as superfícies espaciais podem ser grandes, a quebra de cada malha de superfície espacial em partes menores pode resultar em redução mais eficiente (no caso de menos triângulos fora da tela serem renderizados). No entanto, há uma troca; quanto mais malhas você tiver, mais chamadas de desenho você deverá fazer, o que pode aumentar os custos de CPU. Em um caso extremo, os próprios cálculos de redução de frustum podem até mesmo ter um custo de CPU mensurável.
* Ajustar a ordem de renderização
   * Superfícies espaciais tendem a ser grandes, pois representam todo o ambiente do usuário ao redor delas. Os custos de processamento de pixel na GPU podem ser altos, especialmente em casos em que há mais de uma camada de geometria visível (incluindo superfícies espaciais e outros hologramas). Nesse caso, a camada mais próxima do usuário será oclusão de camadas mais distantes, portanto, qualquer tempo de GPU gasto renderizando essas camadas mais distantes será perdido.
   * Para reduzir esse trabalho redundante na GPU, ele ajuda a renderizar superfícies opacas na ordem de frente para trás (mais próximas primeiro, mais distantes). Por ' opaco ', queremos dizer superfícies para as quais o DepthWriteMask está definido como um em seu [estado de estêncil de profundidade](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc). Quando as superfícies mais próximas são renderizadas, elas primem o buffer de profundidade para que as superfícies mais distantes sejam ignoradas com eficiência pelo processador de pixel na GPU.

## <a name="mesh-processing"></a>Processamento de malha

Um aplicativo pode querer realizar [várias operações](spatial-mapping.md#mesh-processing) em malhas de superfície espacial para atender às suas necessidades. Os dados de índice e vértice fornecidos com cada malha de superfície espacial usam o mesmo layout familiar que os [buffers de vértice e de índice](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) usados para renderizar malhas de triângulo em todas as APIs de renderização modernas. No entanto, um fator importante a ser considerado é que os triângulos de mapeamento espacial têm uma **ordem de vento no sentido anti-horário**. Cada triângulo é representado por três índices de vértice no buffer de índice da malha e esses índices identificarão os vértices do triângulo em um pedido no **sentido horário** , quando o triângulo for exibido do lado **frontal** . O lado frontal (ou externo) de malhas de superfície espacial corresponde à medida que você esperaria para o lado frontal (visível) das superfícies do mundo real.

Os aplicativos só devem realizar a simplificação de malha se a densidade de triângulo mais grosseira fornecida pelo observador de superfície ainda for muito grande: esse trabalho é computacionalmente caro e já está sendo executado pelo tempo de execução para gerar os vários níveis de detalhes fornecidos.

Como cada observador de superfície pode fornecer várias superfícies espaciais desconectadas, alguns aplicativos talvez queiram recortar essas malhas de superfície espacial entre si e, em seguida, zipper-las em conjunto. Em geral, a etapa de recorte é necessária, pois as malhas de superfície espacial próximas geralmente se sobrepõem ligeiramente.

## <a name="raycasting-and-collision"></a>Raycasting e colisão

Para que uma API de física (como [Havok](https://www.havok.com/)) forneça um aplicativo com a funcionalidade de raycasting e colisão para superfícies espaciais, o aplicativo deve fornecer malhas de superfície espacial para a API de física. Malhas usadas para física geralmente têm as seguintes propriedades:
* Eles contêm apenas pequenos números de triângulos. As operações de física são mais computacionalmente intensivas do que as operações de renderização.
* Eles são 'water-tight'. Superfícies destinadas a serem sólidas não devem ter pequenos orifícios; até mesmo os orifícios muito pequenos para serem visíveis podem causar problemas.
* Eles são convertidos em cascas convexas. As cascas convexas têm poucos polígonos e são livres de orifícios e são muito mais eficientes de processar do que malhas de triângulo bruto.

Ao fazer raycasts em superfícies espaciais, tenha em mente que essas superfícies geralmente são formas complexas e desorganizado, cheia de pequenos detalhes confusos, assim como sua mesa! Isso significa que um único raycast geralmente é insuficiente para lhe dar informações suficientes sobre a forma da superfície e a forma do espaço vazio perto dela. Geralmente, é uma boa ideia fazer muitos raycasts em uma pequena área e usar os resultados agregados para derivar uma compreensão mais confiável da superfície. Por exemplo, usar a média de 10 raycasts para orientar o posicionamento do holograma em uma superfície produzirá um resultado muito mais suave e menos "tremeado" que usa apenas um único raycast.

No entanto, tenha em mente que cada raycast pode ter um alto custo computacional. Dependendo do seu cenário de uso, você deve trocar o custo computacional de raycasts [](spatial-mapping.md#mesh-processing) extras (feitos em cada quadro) em relação ao custo computacional do processamento de malha para suavizar e remover os orifícios em superfícies espaciais (feitas quando malhas espaciais são atualizadas).

## <a name="the-environment-scanning-experience"></a>A experiência de verificação de ambiente

Cada aplicativo que usa mapeamento espacial deve considerar fornecer uma "experiência de verificação"; o processo por meio do qual o aplicativo orienta o usuário a examinar superfícies necessárias para que o aplicativo funcione corretamente.

![Exemplo de verificação](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Exemplo de verificação*

A natureza dessa experiência de verificação pode variar muito dependendo das necessidades de cada aplicativo, mas dois princípios principais devem guiar seu design.

Em primeiro lugar, **a comunicação clara com o usuário é a principal preocupação**. O usuário deve estar sempre atento se os requisitos do aplicativo estão sendo atendidos. Quando eles não estão sendo atendidos, deve ser imediatamente claro para o usuário por que isso é feito, e eles devem ser rapidamente acionados para executar a ação apropriada.

Em segundo lugar, **os aplicativos devem tentar um equilíbrio entre a eficiência e a confiabilidade**. Quando é possível fazer isso de forma **confiável**, os aplicativos devem analisar automaticamente os dados de mapeamento espacial para salvar a hora do usuário. Quando não é possível fazer isso de forma confiável, os aplicativos devem permitir que o usuário forneça rapidamente o aplicativo com as informações adicionais necessárias.

Para ajudar a criar a experiência de verificação correta, considere quais das seguintes possibilidades são aplicáveis ao seu aplicativo:

* **Nenhuma experiência de verificação**
   * Um aplicativo pode funcionar perfeitamente sem nenhuma experiência de verificação guiada; Ele aprenderá sobre as superfícies observadas no decorrer do movimento de usuário natural.
   * Por exemplo, um aplicativo que permite que o usuário desenhe superfícies com tinta de irrigação Holographic requer conhecimento apenas das superfícies visíveis no momento para o usuário.
   * O ambiente pode ser verificado, já que é aquele em que o usuário já gastou muito tempo usando o HoloLens.
   * No entanto, lembre-se de que a câmera usada pelo mapeamento espacial só pode ver 3,1 m na frente do usuário, portanto, o mapeamento espacial não saberá sobre nenhuma superfície mais distante, a menos que o usuário as tenha observado de uma distância mais próxima no passado.
   * Portanto, o usuário entende quais superfícies foram verificadas, o aplicativo deve fornecer comentários visuais para esse efeito, por exemplo, converter sombras virtuais em superfícies digitalizadas pode ajudar o usuário a posicionar os hologramas nessas superfícies.
   * Nesse caso, os volumes delimitados do observador da superfície espacial devem ser atualizados em cada quadro para um sistema de coordenadas espaciais bloqueado pelo [corpo,](coordinate-systems.md)para que eles sigam o usuário.

* **Localizar um local adequado**
   * Um aplicativo pode ser projetado para uso em um local com requisitos específicos.
   * Por exemplo, o aplicativo pode exigir uma área vazia em torno do usuário para que ele possa praticar com segurança o holográfico-fu.
   * Os aplicativos devem comunicar todos os requisitos específicos para o usuário e reforce-os com comentários visuais claros.
   * Neste exemplo, o aplicativo deve visualizar a extensão da área vazia necessária e realça visualmente a presença de objetos indesejáveis nessa zona.
   * Nesse caso, os volumes delimitados do observador da superfície espacial devem usar um sistema de coordenadas espaciais bloqueado [pelo](coordinate-systems.md) mundo no local escolhido.

* **Encontrar uma configuração adequada de superfícies**
   * Um aplicativo pode exigir uma configuração específica de superfícies, por exemplo, duas paredes grandes, planas e opostas para criar um hall holográfico de espelhos.
   * Nesses casos, o aplicativo precisará analisar as superfícies fornecidas pelo mapeamento espacial para detectar superfícies adequadas e direcionar o usuário para elas.
   * O usuário deverá ter uma opção de fallback se a análise de superfície do aplicativo não for confiável. Por exemplo, se o aplicativo identificar incorretamente uma porta como uma parede plana, o usuário precisará de uma maneira simples de corrigir esse erro.

* **Examinar parte do ambiente**
   * Um aplicativo pode querer capturar apenas parte do ambiente, conforme direcionado pelo usuário.
   * Por exemplo, o aplicativo examina parte de uma sala para que o usuário possa postar um ad holográfico classificado para móveis que deseja vender.
   * Nesse caso, o aplicativo deve capturar dados de mapeamento espacial dentro das regiões observadas pelo usuário durante a verificação.

* **Examinar a sala inteira**
   * Um aplicativo pode exigir uma verificação de todas as superfícies na sala atual, incluindo aquelas por trás do usuário.
   * Por exemplo, um jogo pode colocar o usuário na função de Gulliver, sob o Siege de centenas de pequenas Lilliputians abordagens de todas as direções.
   * Nesses casos, o aplicativo precisará determinar quantas superfícies na sala atual já foram verificadas e direcionar o olhar do usuário para preencher lacunas significativas.
   * A chave para esse processo é fornecer comentários visuais que o tornam claro para o usuário quais superfícies ainda não foram verificadas. O aplicativo poderia, por exemplo, usar a [neblina baseada em distância](/windows/win32/direct3d9/fog-formulas) para realçar visualmente regiões que não são cobertas por superfícies de mapeamento espacial.

* **Tirar um instantâneo inicial do ambiente**
   * Um aplicativo pode desejar ignorar todas as alterações no ambiente depois de usar um ' instantâneo ' inicial.
   * Isso pode ser apropriado para evitar a interrupção de dados criados pelo usuário que estejam rigidamente acoplados ao estado inicial do ambiente.
   * Nesse caso, o aplicativo deve fazer uma cópia dos dados de mapeamento espacial em seu estado inicial quando a verificação for concluída.
   * Os aplicativos devem continuar recebendo atualizações para dados de mapeamento espacial se os hologramas ainda estiverem obstruídodos corretamente pelo ambiente.
   * Atualizações continuadas para dados de mapeamento espacial também permitem visualizar todas as alterações que ocorreram, esclarecendo ao usuário as diferenças entre os Estados anterior e o presente do ambiente.

* **Fazer instantâneos iniciados pelo usuário do ambiente**
   * Um aplicativo pode querer responder apenas a alterações ambientais quando instruído pelo usuário.
   * Por exemplo, o usuário poderia criar várias ' Statues ' 3D de um amigo capturando suas poses em momentos diferentes.

* **Permitir que o usuário altere o ambiente**
   * Um aplicativo pode ser projetado para responder em tempo real a quaisquer alterações feitas no ambiente do usuário.
   * Por exemplo, o usuário que desenha um Curtain poderia disparar a "mudança de cena" para uma reprodução de Holographic em andamento no outro lado.

* **Orientar o usuário para evitar erros nos dados de mapeamento espacial**
   * Um aplicativo pode querer fornecer diretrizes para o usuário enquanto ele estiver digitalizando seu ambiente.
   * Isso pode ajudar o usuário a evitar [determinados](spatial-mapping.md#what-influences-spatial-mapping-quality)tipos de erros nos dados de mapeamento espacial, por exemplo, mantendo-se longe de janelas ou espelhos com luz solar.

Um detalhe extra a ser ciente é que o 'intervalo' de dados de mapeamento espacial não é ilimitado. Embora o mapeamento espacial crie um banco de dados permanente de espaços grandes, ele só disponibiliza esses dados para aplicativos em uma "bolha" de tamanho limitado ao redor do usuário. Se você começar no início de uma longa viagem e sair o suficiente do início, eventualmente as superfícies espaciais de volta no início desaparecerão. Você pode atenuar isso armazenando essas superfícies em cache em seu aplicativo depois que elas desaparecerem dos dados de mapeamento espacial disponíveis.

## <a name="mesh-processing"></a>Processamento de malha

Pode ajudar a detectar tipos comuns de erros em superfícies e filtrar, remover ou modificar os dados de mapeamento espacial conforme apropriado.

Tenha em mente que os dados de mapeamento espacial devem ser o mais atentos possível às superfícies do mundo real, portanto, qualquer processamento que você aplicar corre o risco de mudar suas superfícies para além da "verdade".

Aqui estão alguns exemplos de diferentes tipos de processamento de malha que podem ser úteis:

* **Preenchimento de orifício**
   * Se um pequeno objeto feito de um material escuro não for digital, ele deixará um orifício na superfície ao redor.
   * Os orifícios afetam a oclusão: os hologramas podem ser vistos 'por meio' de um orifício em uma superfície opaca do mundo real.
   * Os orifícios afetam raios: se você estiver usando raycasts para ajudar os usuários a interagir com superfícies, pode ser indesejável que esses raios passem pelos orifícios. Uma mitigação é usar um pacote de vários raycasts que abrangem uma região de tamanho apropriado. Isso permitirá filtrar os resultados de "outlier", de modo que, mesmo que um raycast passe por um pequeno orifício, o resultado agregado ainda será válido. No entanto, essa abordagem vem a um custo computacional.
   * Os buracos afetam as colisões de física: um objeto controlado pela simulação física pode derrubar um orifício no chão e se tornar perdido.
   * É possível forma algorítmica o preenchimento desses buracos na malha da superfície. No entanto, você precisará ajustar seu algoritmo para que "buracos reais", como Windows e doorways, não sejam preenchidos. Pode ser difícil diferenciar de forma confiável ' buracos reais ' de ' buracos imaginários ', portanto, você precisará experimentar uma heurística diferente, como ' tamanho ' e ' forma de limite '.

* **Remoção de hallucination**
   * Reflexos, luzes brilhantes e movimentação de objetos podem deixar o ' hallucinations ' remanescente pequeno no ar médio.
   * Hallucinations afeta oclusão: hallucinations pode se tornar visível como formas escuras se movendo na frente e occluding outros hologramas.
   * Hallucinations afeta raycasts: se você estiver usando o raycasts para ajudar os usuários a interagir com superfícies, esses raios poderão atingir um hallucination em vez da superfície por trás dele. Assim como acontece com os buracos, uma mitigação é usar muitas raycasts em vez de um único Raycast, mas novamente isso será fornecido a um custo computacional.
   * Hallucinations afetam as colisões de física: um objeto controlado pela simulação física pode ficar preso contra um hallucination e não pode passar por uma área de espaço aparentemente nítida.
   * É possível filtrar esses hallucinations da malha de superfície. No entanto, assim como com os buracos, você precisará ajustar seu algoritmo para que os objetos reais pequenos, como a lâmpada e os identificadores de porta, não sejam removidos.

* **Suavização**
   * O mapeamento espacial pode retornar superfícies que parecem ser aproximadas ou "ruidosas" em comparação com suas contrapartes do mundo real.
   * A suavidade afeta as colisões de física: se o piso for aproximado, uma bola de golfe fisicamente simulada poderá não ser organizada sem problemas em uma linha reta.
   * A suavidade afeta a renderização: se uma superfície for visualizada diretamente, os Normals da superfície aproximada poderão afetar sua aparência e interromper uma aparência "limpa". É possível mitigar isso usando a iluminação e texturas apropriadas no sombreador que é usado para renderizar a superfície.
   * É possível suavizar a assada em uma malha de superfície. No entanto, isso pode levar a superfície para mais longe da superfície do mundo real correspondente. Manter uma correspondência próxima é importante para produzir a oclusão precisa do holograma e permitir que os usuários alcancem interações precisas e previsíveis com superfícies holográficas.
   * Se apenas uma alteração superficial for necessária, poderá ser suficiente suavizar os normais de vértice sem alterar as posições do vértice.

* **Descoberta de plano**
   * Há muitas formas de análise que um aplicativo pode querer executar nas superfícies fornecidas pelo mapeamento espacial.
   * Um exemplo simples é a 'descoberta de plano'; identificando regiões limitadas, principalmente planar de superfícies.
   * As regiões planar podem ser usadas como superfícies de trabalho holográficas, regiões em que o conteúdo holográfico pode ser colocado automaticamente pelo aplicativo.
   * As regiões planares podem restringir a interface do usuário para orientar os usuários a interagir com as superfícies que melhor se adequam às suas necessidades.
   * As regiões planares podem ser usadas como no mundo real, para equivalentes holográficos a objetos funcionais, como telas DE LCD, tabelas ou quadros de branco.
   * As regiões planares podem definir áreas de jogo, formando a base dos níveis de jogos de vídeo.
   * As regiões planares podem ajudar os agentes virtuais a navegar pelo mundo real, identificando as áreas de piso nas quais as pessoas reais provavelmente devem se orientar.

## <a name="prototyping-and-debugging"></a>Criação de protótipos e depuração

### <a name="useful-tools"></a>Ferramentas úteis

* O [emulador do HoloLens](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) pode ser usado para desenvolver aplicativos usando o mapeamento espacial sem acesso a um HoloLens físico. Ele permite simular uma sessão ao vivo em um HoloLens em um ambiente realista, com todos os dados que seu aplicativo normalmente consumiria, incluindo movimento do HoloLens, sistemas de coordenadas espaciais e malhas de mapeamento espacial. Isso pode ser usado para fornecer entrada confiável e repetida, o que pode ser útil para depurar problemas e avaliar alterações em seu código.
* Para reproduzir um cenário, capture dados de mapeamento espacial pela rede de um HoloLens ao vivo, salve-os em disco e reutilizar-os em sessões de depuração posteriores.
* O [modo de exibição 3D do portal de dispositivo do Windows](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#3d-view) fornece uma maneira de ver todas as superfícies espaciais disponíveis atualmente por meio do sistema de mapeamento espacial. Isso fornece uma base de comparação para as superfícies espaciais dentro de seu aplicativo; por exemplo, você pode identificar facilmente se alguma superfície espacial está ausente ou sendo exibida no local errado.

### <a name="general-prototyping-guidance"></a>Diretrizes gerais de protótipo

* Como os [erros](spatial-mapping.md#what-influences-spatial-mapping-quality) nos dados de mapeamento espacial podem afetar seriamente a experiência do usuário, recomendamos que você teste seu aplicativo em uma ampla variedade de ambientes.
* Não se preocupe com o hábito de testar sempre no mesmo local, por exemplo, em sua mesa. Certifique-se de testar várias superfícies de diferentes posições, formas, tamanhos e materiais.
* Da mesma forma, embora os dados sintéticos ou registrados possam ser úteis para depuração, não se tornem muito dependentes dos mesmos casos de teste. Isso pode atrasar a localização de problemas importantes que os testes mais variados teriam detectados anteriormente.
* É uma boa ideia executar testes com usuários reais (e, teoricamente, iniguals), porque eles não podem usar o HoloLens ou seu aplicativo exatamente da mesma maneira que você. Na verdade, ele pode surpreender você como o comportamento, o conhecimento e as suposições das pessoas podem ser divergentes!

## <a name="troubleshooting"></a>Solução de problemas

* Para que as malhas de superfície sejam orientadosdas corretamente, cada gameobject precisa estar ativo antes de ser enviado para o SurfaceObserver para que sua malha seja construída. Caso contrário, as malhas serão exibidas no seu espaço, mas giradas em ângulos estranhos.
* O gameobject que executa o script que se comunica com o SurfaceObserver precisa ser definido para a origem. Caso contrário, todos os GameObjects que você criar e enviar para o SurfaceObserver ter suas malhas construídas terão um deslocamento igual ao deslocamento do objeto do jogo pai. Isso pode fazer com que suas malhas mostrem vários medidores de distância, o que dificulta a depuração do que está acontecendo.

## <a name="see-also"></a>Confira também

* [Sistemas de coordenadas](coordinate-systems.md)
* [Mapeamento espacial no DirectX](../develop/native/spatial-mapping-in-directx.md)
* [Mapeamento espacial no Unity](../develop/unity/spatial-mapping-in-unity.md)
* [Compreensão da cena](scene-understanding.md)
* [Visualização de varredura do ambiente](room-scan-visualization.md)
* [Projeto de som espacial](spatial-sound-design.md)
* [Estudo de caso - Como olhar através dos buracos na sua realidade](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)