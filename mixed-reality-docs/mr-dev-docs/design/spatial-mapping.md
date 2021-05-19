---
title: mapeamento espacial
description: O mapeamento espacial fornece uma representação detalhada das superfícies do mundo real no ambiente em torno do HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: mapeamento espacial, HoloLens, realidade misturada, reconstrução de superfície, malha, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada, compreensão de cena, malha do mundo, oclusão, física, navegação, observador de superfície, renderização, processamento de malha
ms.openlocfilehash: 941e72b441771849e48e8ebc4924605750804831
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143721"
---
# <a name="spatial-mapping"></a>mapeamento espacial

O mapeamento espacial fornece uma representação detalhada das superfícies do mundo real no ambiente em torno do HoloLens, permitindo que os desenvolvedores criem uma experiência de realidade misturada confusa. Mesclando o mundo real com o mundo virtual, um aplicativo pode fazer com que os hologramas pareçam reais. Os aplicativos também podem alinhar-se naturalmente com as expectativas do usuário fornecendo comportamentos e interações conhecidos do mundo real.

<br>

>[!VIDEO https://www.youtube.com/embed/zff2aQ1RaVo]

## <a name="device-supports"></a>Suporte ao dispositivo

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

O mapeamento espacial torna possível posicionar objetos em superfícies reais. Isso ajuda a ancorar objetos no mundo do usuário e aproveita as responsabilidades de profundidade do mundo real. A conclusão de seus hologramas com base em outros hologramas e objetos do mundo real ajuda a convencer o usuário de que esses hologramas estão realmente em seu espaço. Os hologramas que flutuam no espaço ou se movem com o usuário não se sentirão tão reais. Quando possível, coloque itens para conforto.

Visualize superfícies ao colocar ou mover hologramas (use uma grade projetada). Isso ajuda os usuários a saber onde eles podem colocar melhor seus hologramas e mostra se o ponto em que eles estão tentando colocar o holograma não está mapeado. Você poderá "itens de 1000000000" para o usuário se eles acabarem em um ângulo muito grande.

## <a name="conceptual-overview"></a>Visão geral conceitual

![Superfícies de malha que abrangem uma sala](images/SurfaceReconstruction.jpg)<br>
*Um exemplo de uma malha de mapeamento espacial que abrange uma sala*

Os dois tipos de objeto primários usados para mapeamento espacial são o 'Observador da Superfície Espacial' e a 'Superfície Espacial'.

O aplicativo fornece ao Observador da Superfície Espacial um ou mais volumes delimitados para definir as regiões do espaço em que o aplicativo deseja receber dados de mapeamento espacial. Para cada um desses volumes, o mapeamento espacial fornecerá ao aplicativo um conjunto de superfícies espaciais.

Esses volumes podem ser fixos (em um local fixo com base no mundo real) ou podem ser anexados ao HoloLens (eles se movem, mas não giram, com o HoloLens à medida que se movem pelo ambiente). Cada superfície espacial descreve as superfícies do mundo real em um pequeno volume de espaço, representado como uma malha de triângulo anexada a um [sistema de coordenadas espaciais](coordinate-systems.md)bloqueados pelo mundo.

Como o HoloLens reúne novos dados sobre o ambiente e, à medida que ocorrem alterações no ambiente, as superfícies espaciais aparecerão, desaparecerão e serão alteradas.

## <a name="spatial-awareness-design-concepts-demo"></a>Demonstração dos conceitos de design de conscientização espacial

Se você quiser ver os conceitos de design de conscientização espacial em ação, Confira nossa demonstração de vídeo [de conscientização espacial a]() seguir. Quando tiver terminado, continue em para obter mais detalhes sobre tópicos específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

## <a name="spatial-mapping-vs-scene-understanding-worldmesh"></a>Mapeamento espacial versus WorldMesh de compreensão da cena

Para o HoloLens 2, é possível consultar uma versão estática dos dados de mapeamento espacial usando o [SDK de compreensão da cena](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) (configuração EnableWorldMesh). Aqui estão as diferenças entre duas maneiras de acessar os dados de mapeamento espacial:
* API de mapeamento espacial:
   * Intervalo limitado: os dados de mapeamento espacial disponíveis para aplicativos em um tamanho limitado em cache ' bolha ' em todo o usuário.
   * Fornece atualizações de baixa latência de regiões de malha alteradas por meio de eventos de Superfícieschanged.
   * Nível variável de detalhes controlado por triângulos por parâmetro de medidor cúbico.
* SDK de compreensão da cena:
   * Intervalo ilimitado – fornece todos os dados de mapeamento espacial verificados dentro do raio de consulta.
   * Fornece um instantâneo estático dos dados de mapeamento espacial. Obter os dados de mapeamento espacial atualizados requer a execução de uma nova consulta para toda a malha.
   * Nível consistente de detalhes controlado pela configuração de RequestedMeshLevelOfDetail.

## <a name="what-influences-spatial-mapping-quality"></a>O que influencia a qualidade do mapeamento espacial?

Vários fatores, [detalhados aqui,](/hololens/hololens-environment-considerations)podem afetar a frequência e a gravidade desses erros.  No entanto, você deve criar seu aplicativo para que o usuário possa atingir suas metas mesmo na presença de erros nos dados de mapeamento espacial.

## <a name="common-usage-scenarios"></a>Cenários de uso comuns

![Ilustrações de cenários comuns de uso do Mapeamento Espacial: Posicionamento, Oclusão, Física e Navegação](images/sm-concepts-1000px.png)

### <a name="placement"></a>Posicionamento

O mapeamento espacial fornece aos aplicativos a oportunidade de apresentar formas naturais e familiares de interação com o usuário; o que poderia ser mais natural do que colocar seu telefone na mesa?

Restringir o posicionamento de hologramas (ou, em geral, qualquer seleção de locais espaciais) para ficar em superfícies fornece um mapeamento natural de 3D (ponto no espaço) para 2D (ponto na superfície). Isso reduz a quantidade de informações que o usuário precisa fornecer ao aplicativo e torna as interações do usuário mais rápidas, fáceis e precisas. Isso é verdadeiro porque 'distância' não é algo que estamos acostumados a nos comunicar fisicamente com outras pessoas ou com computadores. Quando apontamos com o dedo, estamos especificando uma direção, mas não uma distância.

Uma ressalva importante aqui é que, quando um aplicativo infere a distância da direção (por exemplo, fazendo um raycast ao longo da direção do olhar do usuário para encontrar a superfície espacial mais próxima), isso deve gerar resultados que o usuário possa prever de forma confiável. Caso contrário, o usuário perderá a noção de controle e isso poderá se tornar frustrante rapidamente. Um método que ajuda com isso é fazer vários raycasts em vez de apenas um. Os resultados agregados devem ser mais suaves e mais previsíveis, menos suscetíveis a influenciar de resultados transitórios de "outlier" (como pode ser causado por raios passando por pequenos orifícios ou atingindo pequenos bits de geometria que o usuário não está ciente). A agregação ou suavização também podem ser executadas ao longo do tempo; por exemplo, você pode limitar a velocidade máxima na qual um holograma pode variar em distância do usuário. Simplesmente limitar o valor de distância mínimo e máximo também pode ajudar, de modo que o holograma que está sendo movido não acabe repentinamente na distância ou venha a falhar novamente na face do usuário.

Os aplicativos também podem usar a forma e a direção das superfícies para orientar o posicionamento do holograma. Uma cadeira Holographic não deve penetrar através de paredes e deve ficar com o chão, mesmo que seja ligeiramente desigual. Esse tipo de funcionalidade provavelmente dependeria do uso de colisões de física em vez de raycasts, mas questões semelhantes serão aplicadas. Se o holograma que está sendo posicionado tiver muitos polígonos pequenos que se desdobram, como os lados de uma cadeira, pode fazer sentido expandir a representação física desses polígonos para algo mais largo e suave, de forma que seja mais capaz de deslizar por superfícies espaciais sem realce em captura.

Em seu extremo, a entrada do usuário pode ser simplificada de maneira totalmente e as superfícies espaciais podem ser usadas para realizar o posicionamento totalmente automático do holograma. Por exemplo, o aplicativo poderia fazer um interruptor de Holographic em algum lugar na parede para que o usuário pressione. A mesma limitação sobre previsibilidade se aplica duplamente; Se o usuário espera o controle sobre o posicionamento do holograma, mas o aplicativo nem sempre coloca os hologramas onde eles esperam (se a opção de luz aparecer em algum lugar que o usuário não consegue alcançar), essa será uma experiência frustrante. Na verdade, pode ser pior fazer o posicionamento automático que exige a correção do usuário, em vez de exigir que o usuário sempre faça o mesmo posicionamento; como *espera*-se um posicionamento automático bem-sucedido, a correção manual parece ser um fardo!

Observe também que a capacidade de um aplicativo de usar superfícies espaciais para posicionamento depende muito da experiência de [verificação](spatial-mapping.md#the-environment-scanning-experience)do aplicativo. Se uma superfície não tiver sido verificada, ela não poderá ser usada para posicionamento. Cabe ao aplicativo ficar claro para o usuário, para que eles possam ajudar a examinar novas superfícies ou selecionar um novo local.

Os comentários visuais para o usuário são de importância fundamental durante o posicionamento. O usuário precisa saber onde o holograma é baseado na superfície mais próxima com [efeitos de terra.](spatial-mapping.md#visualization) Eles devem entender por que o movimento do holograma está sendo restrito (por exemplo, devido a colisões com outra superfície próxima). Se eles não puderem colocar um holograma no local atual, os comentários visuais deverão deixar claro por que não. Por exemplo, se o usuário estiver tentando colocar um diviso holográfico preso na parede, as partes do diviso que estão atrás da parede deverão pulsar em uma cor vermelha. Ou, por outro lado, se o aplicativo não puder encontrar uma superfície espacial em um local em que o usuário possa ver uma superfície do mundo real, o aplicativo deverá deixar isso claro. A ausência óbvia de um efeito de base nessa área pode atingir essa finalidade.

### <a name="occlusion"></a>Oclusão

Um dos principais usos de superfícies de mapeamento espacial é simplesmente ocluir hologramas. Esse comportamento simples tem um grande impacto sobre o realismo percebido dos hologramas, ajudando a criar uma noção de que realmente tem o mesmo espaço físico que o usuário.

A oclusão também fornece informações para o usuário; quando um holograma parece estar ocluído por uma superfície do mundo real, isso fornece comentários visuais adicionais sobre a localização espacial desse holograma no mundo. Por outro lado, a oclusão também pode *ocultar* informações do usuário de maneira útil; A oclusão de hologramas atrás de paredes pode reduzir a desorganização visual de maneira intuitiva. Para ocultar ou revelar um holograma, o usuário simplesmente precisa mover a cabeça.

A oclusão também pode ser usada para a expectativa de uma interface do usuário natural com base em interações físicas familiares; se um holograma é ocluído por uma superfície, é porque essa superfície  é sólida, portanto, o usuário deve esperar que o holograma colida com essa superfície e não passe por ela.

Às vezes, a oclusão de hologramas é indesejável. Se um usuário precisar interagir com um holograma, ele precisará vê-lo-mesmo que esteja por trás de uma superfície do mundo real. Nesses casos, geralmente faz sentido renderizar esse holograma de forma diferente quando é obstruído (por exemplo, reduzindo seu brilho). Dessa forma, o usuário pode visualmente localizar o holograma, mas ainda saberá que está por trás de algo.

### <a name="physics"></a>Física

O uso da simulação de física é outra maneira na qual o mapeamento espacial pode ser usado para reforçar a *presença* de hologramas no espaço físico do usuário. Quando minha bola de borracha Holographic se acumula Realistamente na minha mesa, passa pelo andar e desaparece sob o sofá, pode ser difícil acreditar que não está lá.

A simulação de física também oferece a oportunidade de um aplicativo usar interações baseadas em física e natural. Mover uma peça de mobília de Holographic no chão provavelmente será mais fácil para o usuário se as mobília responderem como se estivessem deslizando em todo o andar com a inércia e a fricção apropriadas.

Para gerar comportamentos físicos reais, você provavelmente precisará fazer algum [processamento de malha](spatial-mapping.md#mesh-processing) , como o preenchimento de buracos, a remoção de hallucinations flutuantes e a suavização de superfícies de ásperos.

Você também precisará considerar como a [experiência de verificação](spatial-mapping.md#the-environment-scanning-experience) do seu aplicativo influencia sua simulação física. Em primeiro lugar, as superfícies ausentes não colidirão nada; o que acontece quando a bola de borracha faz o corredor e o final do mundo conhecido? Em segundo lugar, você precisa decidir se continuará a responder às alterações no ambiente ao longo do tempo. Em alguns casos, você desejará responder o mais rápido possível; Digamos que se o usuário estiver usando portas e móveis como Barricades móveis em defesa contra uma Tempest de setas romanos de entrada. Em outros casos, no entanto, talvez você queira ignorar novas atualizações; dirigir seu carro Holographic em volta ao Racetrack em seu andar pode repentinamente não ser tão divertido se seu cão decidir ficar no meio do controle.

### <a name="navigation"></a>Navegação

Os aplicativos podem usar dados de mapeamento espacial para conceder aos caracteres holográficos (ou agentes) a capacidade de navegar pelo mundo real da mesma maneira que uma pessoa real. Isso pode ajudar a reforçar a presença de caracteres holográficos restringindo-os ao mesmo conjunto de comportamentos naturais e familiares que aqueles do usuário e seus amigos.

As funcionalidades de navegação também podem ser úteis para os usuários. Depois que um mapa de navegação tiver sido criado em uma determinada área, ele poderá ser compartilhado para fornecer instruções holográficas para novos usuários não familiarizados com esse local. Esse mapa pode ser projetado para ajudar a manter o fluxo contínuo do 'tráfego' ou evitar acidentes em locais perigosos, como locais de construção.

Os principais desafios técnicos envolvidos na implementação da funcionalidade de navegação serão a detecção confiável de superfícies walkable (os humanos não andam em tabelas!) e a adaptação elegante às alterações no ambiente (os humanos não passam por portas fechadas!). A malha pode exigir algum [processamento antes](spatial-mapping.md#mesh-processing) de ser acessível para planejamento de caminho e navegação por um caractere virtual. Suavizar a malha e remover desilusão pode ajudar a evitar que os caracteres fique preso. Talvez você também queira simplificar drasticamente a malha para acelerar os cálculos de navegação e planejamento de caminho do seu caractere. Esses desafios receberam muita atenção no desenvolvimento da tecnologia de jogos de vídeo e há uma grande quantidade de pesquisas disponíveis sobre esses tópicos.

A funcionalidade interna na NavMesh no Unity não pode ser usada com superfícies de mapeamento espacial. Isso acontece porque as superfícies de mapeamento espacial não são conhecidas até que o aplicativo seja iniciado, mas os arquivos de dados NavMesh precisam ser gerados a partir de ativos de origem com antecedência. Observe também que o sistema de mapeamento espacial não fornecerá informações sobre [superfícies distantes](spatial-mapping.md#the-environment-scanning-experience) do local atual do usuário. Portanto, o aplicativo deve 'lembrar' aparecer se for para criar um mapa de uma área grande.

### <a name="visualization"></a>Visualização

Na maioria das vezes, é apropriado que as superfícies espaciais sejam invisíveis; para minimizar a desordem Visual e deixar o mundo real se falar de si mesmo. No entanto, às vezes é útil visualizar as superfícies de mapeamento espacial diretamente, apesar de suas contrapartes reais estarem visíveis.

Por exemplo, quando o usuário está tentando colocar um holograma em uma superfície (colocando um gabinete Holographic na parede, digamos), pode ser útil "aterrar" o holograma ao converter uma sombra na superfície. Isso dá ao usuário um sentido muito mais claro da proximidade física exata entre o holograma e a superfície. Este também é um exemplo da prática mais geral de ' Visualizar visualmente ' uma alteração antes de o usuário confirmá-la.

Ao visualizar as superfícies, o aplicativo pode compartilhar com o usuário sua compreensão do ambiente. Por exemplo, um jogo de tabuleiro de Holographic poderia visualizar as superfícies horizontais identificadas como "tabelas", de modo que o usuário saiba onde elas devem ir para interagir.

A visualização de superfícies pode ser uma maneira útil de mostrar os espaços próximos do usuário que estão ocultos na exibição. Isso pode fornecer uma maneira de fornecer ao usuário acesso à sua cozinha (e a todos os seus hologramas contidos) a partir de sua sala de vida.

As malhas de superfície fornecidas pelo mapeamento espacial podem não ser particularmente ' limpas '. É importante visualizá-los adequadamente. Os cálculos de iluminação tradicionais podem realçar erros em normalidades de superfície de maneira Visual, enquanto as texturas "limpas" projetadas na superfície podem ajudar a dar uma aparência mais organizada. Também é possível fazer o [processamento de malha](spatial-mapping.md#mesh-processing) para melhorar as propriedades de malha, antes que as superfícies sejam renderizadas.

> [!NOTE]
> O HoloLens 2 implementa uma nova [cena que entende o tempo de execução](scene-understanding.md), que fornece aos desenvolvedores de realidade misturada uma representação de ambiente estruturada e de alto nível projetada para simplificar a implementação do posicionamento, oclusão, física e de navegação.

## <a name="using-the-surface-observer"></a>Usando o observador de superfície

O ponto de partida para o mapeamento espacial é o observador de superfície. O fluxo do programa é o seguinte:
* Criar um objeto de observador de superfície
   * Forneça um ou mais volumes espaciais para definir as regiões de interesse nas quais o aplicativo deseja receber dados de mapeamento espacial. Um volume espacial é simplesmente uma forma que define uma região do espaço, como uma esfera ou uma caixa.
   * Use um volume espacial com um sistema de coordenadas espaciais bloqueado pelo mundo para identificar uma região fixa do mundo físico.
   * Use um volume espacial, atualizou cada quadro com um sistema de coordenadas espaciais bloqueado pelo corpo para identificar uma região de espaço que se move (mas não gira) com o usuário.
   * Esses volumes espaciais podem ser alterados posteriormente a qualquer momento, conforme o status do aplicativo ou do usuário muda.
* Usar sondagem ou notificação para recuperar informações sobre superfícies espaciais
   * Você pode 'sondar' o observador da superfície quanto ao status da superfície espacial a qualquer momento. Em vez disso, você pode se registrar para o evento 'superfícies alteradas' do observador de superfície, que notificará o aplicativo quando as superfícies espaciais foram alteradas.
   * Para um volume espacial dinâmico, como a exibição frustum ou um volume bloqueado pelo corpo, os aplicativos precisarão sondar alterações em cada quadro definindo a região de interesse e, em seguida, obtendo o conjunto atual de superfícies espaciais.
   * Para um volume estático, como um cubo mundialmente bloqueado que abrange uma única sala, os aplicativos podem se registrar para o evento 'superfícies alteradas' serem notificados quando superfícies espaciais dentro desse volume podem ter sido alteradas.
* Alterações nas superfícies de processo
   * Iterar o conjunto fornecido de superfícies espaciais.
   * Classificar superfícies espaciais como adicionadas, alteradas ou removidas.
   * Para cada superfície espacial adicionada ou alterada, se apropriado, envie uma solicitação assíncrona para receber a malha atualizada que representa o estado atual da superfície no nível desejado de detalhes.
* Processe a solicitação de malha assíncrona (mais detalhes nas seções a seguir).

## <a name="mesh-caching"></a>Cache de malha

As superfícies espaciais são representadas por malhas de triângulo denso. Armazenar, renderizar e processar essas malhas pode consumir recursos computacionais e de armazenamento significativos. Assim, cada aplicativo deve adotar um esquema de cache de malha apropriado às suas necessidades, para minimizar os recursos usados para processamento e armazenamento de malha. Esse esquema deve determinar quais malhas manter e quais descartar e quando atualizar a malha para cada superfície espacial.

Muitas das considerações discutidas aqui informarão diretamente como seu aplicativo deve abordar o cache de malha. Você deve considerar como o usuário passa pelo ambiente, quais superfícies são necessárias, quando superfícies diferentes serão observadas e quando as alterações no ambiente devem ser capturadas.

Ao interpretar o evento "superfícies alteradas" fornecido pelo observador de superfície, a lógica de cache de malha básica é a seguinte:
* Se o aplicativo vir uma ID de superfície espacial que ele não viu antes, ele deve tratá-lo como uma nova superfície espacial.
* Se o aplicativo vir uma superfície espacial com uma ID conhecida, mas com uma nova hora de atualização, ela deverá tratá-la como uma superfície espacial atualizada.
* Se o aplicativo não vir mais uma superfície espacial com uma ID conhecida, ele deverá tratá-lo como uma superfície espacial removida.

Cabe a cada aplicativo, então, fazer as seguintes escolhas:
* Para novas superfícies espaciais, a malha deve ser solicitada?
   * Geralmente, a malha deve ser solicitada imediatamente para novas superfícies espaciais, o que pode fornecer novas informações úteis ao usuário.
   * No entanto, novas superfícies espaciais perto e na frente do usuário devem receber prioridade e sua malha deve ser solicitada primeiro.
   * Se a nova malha não for necessária, se, por exemplo, o aplicativo tiver ' congelado ' permanentemente ou temporariamente seu modelo do ambiente, ele não deverá ser solicitado.
* Para superfícies espaciais atualizadas, a malha deve ser solicitada?
   * As superfícies espaciais atualizadas perto e na frente do usuário devem receber prioridade e sua malha deve ser solicitada primeiro.
   * Também pode ser apropriado fornecer prioridade mais alta para novas superfícies do que para superfícies atualizadas, especialmente durante a experiência de verificação.
   * Para limitar os custos de processamento, os aplicativos podem querer limitar a taxa na qual eles processam atualizações para superfícies espaciais.
   * Pode ser possível inferir que as alterações em uma superfície espacial sejam secundárias, por exemplo, se os limites da superfície são pequenos, caso em que a atualização pode não ser importante o suficiente para processar.
   * As atualizações em superfícies espaciais fora da região atual de interesse do usuário podem ser totalmente ignoradas, embora, nesse caso, possa ser mais eficiente modificar os volumes delimitadores espaciais em uso pelo observador da superfície.
* Para superfícies espaciais removidas, a malha deve ser descartada?
   * Geralmente, a malha deve ser descartada imediatamente para superfícies espaciais removidas, para que a oclusão do holograma permaneça correta.
   * No entanto, se o aplicativo tiver motivos para acreditar que uma superfície espacial reaparecerá em breve (com base no design da experiência do usuário), poderá ser mais eficiente mantê-la do que descartar sua malha e recriá-la mais tarde.
   * Se o aplicativo estiver criando um modelo em grande escala do ambiente do usuário, talvez ele não queira descartar malhas. No entanto, ele ainda precisará limitar o uso de recursos, possivelmente por meio do spool de malhas no disco à medida que as superfícies espaciais desaparecerem.
   * Alguns eventos relativamente raros durante a geração de superfície espacial podem fazer com que superfícies espaciais sejam substituídas por novas superfícies espaciais em um local semelhante, mas com IDs diferentes. Portanto, os aplicativos que optam por não descartar uma superfície removida devem ter cuidado para não acabar com várias malhas de superfícies espaciais altamente sobrecargadas que abrangem o mesmo local.
* A malha deve ser descartada para qualquer outra superfície espacial?
   * Mesmo que exista uma superfície espacial, se ela não for mais útil para a experiência do usuário, ela deverá ser descartada. Por exemplo, se o aplicativo 'substituir' a sala do outro lado de uma porta por um espaço virtual alternativo, as superfícies espaciais nessa sala não serão mais importantes.

Aqui está um exemplo de estratégia de cache de malha, usando a histeresia espacial e temporal:
* Considere um aplicativo que deseja usar um volume de interesse espacial em forma de frustum que segue o olhar do usuário à medida que eles buscam e percorrem.
* Uma superfície espacial pode desaparecer temporariamente desse volume simplesmente porque o usuário fica longe da superfície ou das etapas mais distantes dela... apenas para olhar de volta ou se aproximar mais de um momento mais tarde. Nesse caso, descartar e recriar a malha para essa superfície representa muitos processos redundantes.
* Para reduzir o número de alterações processadas, o aplicativo usa dois observadores de superfície espacial, um contido dentro do outro. O volume maior é esférico e segue o usuário ' lentamente '; Ele só se move quando necessário para garantir que seu centro esteja dentro de 2,0 metros do usuário.
* As malhas de superfície espacial novas e atualizadas são sempre processadas do observador de superfície interna menor, mas as malhas são armazenadas em cache até que desapareçam do observador de superfície externa maior. Isso permite que o aplicativo Evite processar muitas alterações redundantes devido à movimentação de usuário local.
* Como uma superfície espacial também pode desaparecer temporariamente devido à perda de rastreamento, o aplicativo também adia a descartação de superfícies espaciais removidas durante a perda de rastreamento.
* Em geral, um aplicativo deve avaliar a compensação entre o processamento de atualização reduzido e o maior uso de memória para determinar sua estratégia de cache ideal.

## <a name="rendering"></a>Renderização

Há três maneiras principais pelas quais as malhas de mapeamento espacial tendem a ser usadas para renderização:
* Para visualização de superfície
   * Geralmente, é útil Visualizar superfícies espaciais diretamente. Por exemplo, a conversão de ' Shadows ' de objetos em superfícies espaciais pode fornecer comentários visuais úteis ao usuário enquanto eles estão colocando hologramas em superfícies.
   * Uma coisa a ser lembrada é que as malhas espaciais são diferentes para o tipo de malha que um artista 3D pode criar. A topologia de triângulo não será tão "limpa" quanto a topologia criada por humanos, e a malha será afetada de [vários erros](spatial-mapping.md#what-influences-spatial-mapping-quality).
   * Para criar uma insinteição visual, talvez você queira fazer algum processamento de [malha,](spatial-mapping.md#mesh-processing)por exemplo, para preencher os orifícios ou os normais de superfície suave. Você também pode querer usar um sombreador para projetar texturas projetadas por um artista em sua malha, em vez de visualizar diretamente a topologia e os normais da malha.
* Para oclusão de hologramas por trás de superfícies do mundo real
   * Superfícies espaciais podem ser renderizadas em uma passagem somente de profundidade, o que afeta apenas o [buffer](/windows/win32/direct3d9/depth-buffers) de profundidade e não afeta os destinos de renderização de cores.
   * Isso impede que o buffer de profundidade oclua os hologramas renderizados posteriormente por trás de superfícies espaciais. A oclusão precisa de hologramas melhora a noção de que os hologramas realmente existem dentro do espaço físico do usuário.
   * Para habilitar a renderização somente de profundidade, atualize o estado do blend para definir [RenderTargetWriteMask](/windows/win32/api/d3d11_1/ns-d3d11_1-d3d11_render_target_blend_desc1) como zero para todos os destinos de renderização de cor.
* Para modificar a aparência de hologramas ocluídos por superfícies do mundo real
   * Normalmente, a geometria renderizada fica oculta quando está oclusa. Isso é feito definindo a função de profundidade em seu estado de estêncil de profundidade como "menor  ou igual", o que faz com que a geometria seja visível apenas quando está mais próxima da câmera do que toda a geometria renderizada anteriormente. [](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc)
   * No entanto, pode ser útil manter determinada geometria visível mesmo quando ela está oclusa e modificar sua aparência quando ocluído como uma maneira de fornecer comentários visuais ao usuário. Por exemplo, isso permite que o aplicativo mostre ao usuário o local de um objeto, deixando claro que está atrás de uma superfície do mundo real.
   * Para fazer isso, renderize a geometria uma segunda vez com um sombreador diferente que cria a aparência 'oclusiva' desejada. Antes de renderizar a geometria pela segunda vez, faça duas alterações no estado [de estêncil de profundidade.](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc) Primeiro, de definir a função de profundidade como "maior ou igual" para  que a geometria seja visível somente onde ela está mais distante da câmera do que toda a geometria renderizada anteriormente. Em segundo lugar, defina DepthWriteMask como zero, para que o buffer de profundidade não seja modificado (o buffer de profundidade deve continuar a representar a profundidade da geometria **mais próxima** da câmera).

O [desempenho](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) é uma preocupação importante ao renderizar malhas de mapeamento espacial. Aqui estão algumas técnicas de desempenho de renderização específicas para renderizar malhas de mapeamento espacial:
* Ajustar densidade do triângulo
   * Ao solicitar malhas de superfície espacial do seu observador de superfície, solicite a menor densidade de malhas de triângulo que será suficiente para suas necessidades.
   * Pode fazer sentido variar a densidade do triângulo em uma superfície por superfície, dependendo da distância da superfície do usuário e de sua relevância para a experiência do usuário.
   * Reduzir as contagens de triângulos reduzirá o uso de memória e os custos de processamento de vértice na GPU, embora não afete os custos de processamento de pixel.
* Usar a remoção de frustum
   * A remoção de frustum ignora objetos de desenho que não podem ser vistos porque estão fora do frustum de exibição atual. Isso reduz os custos de processamento de CPU e GPU.
   * Como a remoção é realizada em uma base por malha e as superfícies espaciais podem ser grandes, dividir cada malha de superfície espacial em partes menores pode resultar em uma remoção mais eficiente (na medida em que menos triângulos de fora da tela são renderizados). No entanto, há uma compensação; Quanto mais malhas você tiver, mais chamadas de desenho deverão ser feitas, o que pode aumentar os custos de CPU. Em um caso extremo, os próprios cálculos de remoção de frustum podem até mesmo ter um custo de CPU mensurável.
* Ajustar a ordem de renderização
   * As superfícies espaciais tendem a ser grandes, pois representam o ambiente inteiro do usuário em torno delas. Os custos de processamento de pixel na GPU podem ser altos, especialmente em casos em que há mais de uma camada de geometria visível (incluindo superfícies espaciais e outros hologramas). Nesse caso, a camada mais próxima do usuário será occluding as camadas mais distantes, portanto, qualquer tempo de GPU gasto renderizando essas camadas mais distantes é desperdiçado.
   * Para reduzir esse trabalho redundante na GPU, ele ajuda a renderizar superfícies opacas na ordem de frente para trás (aquelas mais próximas primeiro, mais distantes por último). Por 'opaco', queremos dizer superfícies para as quais DepthWriteMask é definido como um em seu estado [de estêncil de profundidade.](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc) Quando as superfícies mais próximas são renderizadas, elas a primem o buffer de profundidade para que superfícies mais distantes sejam ignoradas com eficiência pelo processador de pixel na GPU.

## <a name="mesh-processing"></a>Processamento de malha

Um aplicativo pode querer fazer várias [operações em](spatial-mapping.md#mesh-processing) malhas de superfície espacial para atender às suas necessidades. Os dados de índice e vértice fornecidos com cada malha de superfície espacial usam o mesmo layout familiar que os buffers de [vértice](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) e índice usados para renderizar malhas de triângulo em todas as APIs de renderização modernas. No entanto, um fato importante a ser ciente é que os triângulos de mapeamento espacial têm uma ordem de vento no sentido horário **frontal.** Cada triângulo é representado por três índices de vértice no buffer de índice da malha e  esses índices identificarão os vértices do triângulo em uma ordem horário, quando o triângulo for exibido do lado frontal.  O lado frontal (ou fora) das malhas da superfície espacial corresponde à esperada do lado frontal (visível) das superfícies do mundo real.

Os aplicativos só deverão fazer a simplificação de malha se a densidade de triângulo mais alta fornecida pelo observador de superfície ainda for insuficientemente grosseira – esse trabalho é computacionalmente caro e já está sendo executado pelo runtime para gerar os vários níveis de detalhes fornecidos.

Como cada observador de superfície pode fornecer várias superfícies espaciais não conectadas, alguns aplicativos podem querer cortar essas malhas de superfície espacial entre si e, em seguida, reenconectá-las. Em geral, a etapa de recorte é necessária, pois malhas de superfície espacial próximas geralmente se sobrepõem ligeiramente.

## <a name="raycasting-and-collision"></a>Raycasting e Colisão

Para que uma API física (como [Havok](https://www.havok.com/)) forneça um aplicativo com raycasting e funcionalidade de colisão para superfícies espaciais, o aplicativo deve fornecer malhas de superfície espacial para a API física. As malhas usadas para a física geralmente têm as seguintes propriedades:
* Eles contêm apenas pequenos números de triângulos. As operações de física são mais intensivas em computação do que as operações de renderização.
* Eles são ' d' água. As superfícies destinadas a serem sólidas não devem ter pequenos buracos; até mesmo os orifícios muito pequenos para serem visíveis podem causar problemas.
* Eles são convertidos em convexa hulls. Convexa hulls têm poucos polígonos e são livres de buracos, e são muito mais eficientes em termos de computação do que as malhas de triângulo brutos.

Ao fazer raycasts em relação a superfícies espaciais, tenha em mente que essas superfícies são muitas vezes complexas, formas desorganizadas com detalhes de pouco confusos, assim como sua mesa! Isso significa que uma única Raycast geralmente é insuficiente para fornecer a você informações suficientes sobre a forma da superfície e a forma do espaço vazio perto dela. Geralmente, é uma boa ideia fazer muitas raycasts em uma pequena área e usar os resultados agregados para obter uma compreensão mais confiável da superfície. Por exemplo, usar a média de 10 raycasts para orientar o posicionamento do holograma em uma superfície produzirá um resultado muito mais suave e menos "tremulação" que usa apenas um único Raycast.

No entanto, tenha em mente que cada Raycast pode ter um alto custo computacional. Dependendo do seu cenário de uso, você deve compensar o custo computacional de raycasts extra (feito a cada quadro) em relação ao custo computacional do [processamento de malha](spatial-mapping.md#mesh-processing) para suavizar e remover buracos em superfícies espaciais (feitas quando as malhas espaciais são atualizadas).

## <a name="the-environment-scanning-experience"></a>A experiência de verificação do ambiente

Cada aplicativo que usa o mapeamento espacial deve considerar a possibilidade de fornecer uma "experiência de verificação"; o processo pelo qual o aplicativo orienta o usuário a verificar as superfícies necessárias para que o aplicativo funcione corretamente.

![Exemplo de verificação](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Exemplo de verificação*

A natureza dessa experiência de verificação pode variar muito dependendo das necessidades de cada aplicativo, mas dois princípios principais devem orientar seu design.

Em primeiro lugar, **a comunicação clara com o usuário é a principal preocupação.** O usuário sempre deve estar ciente de se os requisitos do aplicativo estão sendo atendidos. Quando eles não estão sendo atendidos, deve ser imediatamente claro para o usuário por que isso é assim e eles devem ser rapidamente levados a tomar a ação apropriada.

Em segundo lugar, **os aplicativos devem tentar atingir um equilíbrio entre eficiência e confiabilidade.** Quando for possível fazer isso de forma **confiável,** os aplicativos deverão analisar automaticamente os dados de mapeamento espacial para economizar o tempo do usuário. Quando não é possível fazer isso de forma confiável, os aplicativos devem permitir que o usuário forneça rapidamente ao aplicativo as informações adicionais necessárias.

Para ajudar a projetar a experiência de verificação correta, considere quais das seguintes possibilidades são aplicáveis ao seu aplicativo:

* **Nenhuma experiência de verificação**
   * Um aplicativo pode funcionar perfeitamente sem qualquer experiência de verificação guiada; ele aprenderá sobre as superfícies que são observadas durante a movimentação natural do usuário.
   * Por exemplo, um aplicativo que permite ao usuário desenhar em superfícies com pintura de pulverização holográfica requer conhecimento apenas das superfícies visíveis no momento para o usuário.
   * O ambiente já poderá ser verificado se ele for aquele em que o usuário já passou muito tempo usando o HoloLens.
   * Tenha em mente, no entanto, que a câmera usada pelo mapeamento espacial só pode ver 3,1 m na frente do usuário, portanto, o mapeamento espacial não conhecerá superfícies mais distantes, a menos que o usuário as tenha observado de uma distância mais próxima no passado.
   * Portanto, o usuário entende quais superfícies foram examinadas, o aplicativo deve fornecer comentários visuais para esse efeito, por exemplo, a transmissão de sombras virtuais em superfícies examinadas pode ajudar o usuário a colocar hologramas nessas superfícies.
   * Nesse caso, os volumes delimitados do observador de superfície espacial devem ser atualizados cada quadro para um [sistema de coordenadas espaciais](coordinate-systems.md)bloqueadas pelo corpo, para que eles sigam o usuário.

* **Encontrar um local adequado**
   * Um aplicativo pode ser projetado para uso em um local com requisitos específicos.
   * Por exemplo, o aplicativo pode exigir uma área vazia em todo o usuário para que possa praticar com segurança Holographic Kung-Fu.
   * Os aplicativos devem comunicar quaisquer requisitos específicos para o usuário antes e reforce-los com comentários visuais claros.
   * Neste exemplo, o aplicativo deve Visualizar a extensão da área vazia necessária e realçar visualmente a presença de qualquer objeto indesejado nessa zona.
   * Para esse caso, os volumes delimitados do observador de superfície espacial devem usar um [sistema de coordenadas espaciais](coordinate-systems.md) bloqueados pelo mundo no local escolhido.

* **Encontre uma configuração adequada de superfícies**
   * Um aplicativo pode exigir uma configuração específica de superfícies, por exemplo, duas paredes grandes e simples e opostas para criar um Holographic Hall de espelhos.
   * Nesses casos, o aplicativo precisará analisar as superfícies fornecidas pelo mapeamento espacial para detectar superfícies adequadas e direcionar o usuário para eles.
   * O usuário deverá ter uma opção de fallback se a análise da superfície do aplicativo não for confiável. Por exemplo, se o aplicativo identificar incorretamente um porta como uma parede simples, o usuário precisará de uma maneira simples de corrigir esse erro.

* **Examinar parte do ambiente**
   * Um aplicativo pode desejar capturar apenas parte do ambiente, conforme indicado pelo usuário.
   * Por exemplo, o aplicativo examina parte de uma sala para que o usuário possa postar um anúncio Holographic classificado para móveis que desejam vender.
   * Nesse caso, o aplicativo deve capturar dados de mapeamento espacial dentro das regiões observadas pelo usuário durante a verificação.

* **Verificar a sala inteira**
   * Um aplicativo pode exigir uma verificação de todas as superfícies no espaço atual, incluindo aquelas por trás do usuário.
   * Por exemplo, um jogo pode colocar o usuário na função de Sempre, sob pressão de centenas de lilliputianos minúsculos se aproximando de todas as direções.
   * Nesses casos, o aplicativo precisará determinar quantas superfícies na sala atual já foram examinadas e direcionar o olhar do usuário para preencher lacunas significativas.
   * A chave para esse processo é fornecer comentários visuais que deixa claro para o usuário quais superfícies ainda não foram examinadas. O aplicativo pode, por exemplo, usar a base de distância [para](/windows/win32/direct3d9/fog-formulas) realçar visualmente as regiões que não são cobertas por superfícies de mapeamento espacial.

* **Tirar um instantâneo inicial do ambiente**
   * Um aplicativo pode querer ignorar todas as alterações no ambiente depois de tirar um 'instantâneo' inicial.
   * Isso pode ser apropriado para evitar a interrupção de dados criados pelo usuário que estão firmemente a coupleados ao estado inicial do ambiente.
   * Nesse caso, o aplicativo deve fazer uma cópia dos dados de mapeamento espacial em seu estado inicial depois que a verificação for concluída.
   * Os aplicativos devem continuar recebendo atualizações para dados de mapeamento espacial se os hologramas ainda devem ser corretamente ocluídos pelo ambiente.
   * As atualizações contínuas nos dados de mapeamento espacial também permitem visualizar todas as alterações ocorridas, esclarecendo ao usuário as diferenças entre estados anteriores e atuais do ambiente.

* **Tirar instantâneos iniciados pelo usuário do ambiente**
   * Um aplicativo só pode querer responder a alterações ambientais quando instruído pelo usuário.
   * Por exemplo, o usuário pode criar várias '3D' de um amigo capturando suas poses em momentos diferentes.

* **Permitir que o usuário altere o ambiente**
   * Um aplicativo pode ser projetado para responder em tempo real a quaisquer alterações feitas no ambiente do usuário.
   * Por exemplo, o usuário desenhando uma cena pode disparar a 'alteração de cena' para uma peça holográfica que ocorre no outro lado.

* **Orientar o usuário para evitar erros nos dados de mapeamento espacial**
   * Um aplicativo pode desejar fornecer orientações ao usuário enquanto eles estão verificando seu ambiente.
   * Isso pode ajudar o usuário a evitar determinados tipos de [erros nos dados de mapeamento espacial](spatial-mapping.md#what-influences-spatial-mapping-quality), por exemplo, mantendo-se afastados das janelas sunlit ou dos espelhos.

Um detalhe extra a ser considerado é que o ' intervalo ' de dados de mapeamento espacial não é ilimitado. Embora o mapeamento espacial crie um banco de dados permanente com espaços grandes, ele torna os dados disponíveis apenas para os aplicativos em uma "bolha" de tamanho limitado em relação ao usuário. Se você começar no início de um longo corredor e ir longe o suficiente do início, eventualmente as superfícies espaciais no início desaparecerão. Você pode mitigar isso armazenando em cache essas superfícies em seu aplicativo depois que elas desaparecerem dos dados de mapeamento espacial disponíveis.

## <a name="mesh-processing"></a>Processamento de malha

Pode ajudar a detectar tipos comuns de erros em superfícies e filtrar, remover ou modificar os dados de mapeamento espacial conforme apropriado.

Tenha em mente que os dados de mapeamento espacial devem ser tão fiels quanto possível para superfícies reais, de modo que qualquer processamento que você aplique riscos mudará suas superfícies além da ' verdade '.

Aqui estão alguns exemplos de diferentes tipos de processamento de malha que podem ser úteis:

* **Preenchimento de orifício**
   * Se um pequeno objeto formado por um material escuro falhar ao digitalizar, ele deixará um orifício na superfície ao redor.
   * Os buracos afetam o oclusão: os hologramas podem ser vistos "por meio de um buraco em uma superfície do mundo real opaca supostamente.
   * Os buracos afetam o raycasts: se você estiver usando o raycasts para ajudar os usuários a interagir com as superfícies, pode ser indesejável que esses raios passem por buracos. Uma mitigação é usar um pacote de vários raycasts cobrindo uma região de tamanho adequado. Isso permitirá que você filtre os resultados de "exceção", de modo que, mesmo que um Raycast passe por uma pequena brecha, o resultado da agregação ainda será válido. No entanto, essa abordagem vem com um custo computacional.
   * Os orifícios afetam colisões físicas: um objeto controlado pela simulação de física pode cair por um orifício no chão e se perder.
   * É possível preencher de forma algorítmicamente esses orifícios na malha da superfície. No entanto, você precisará ajustar seu algoritmo para que "orifícios reais", como janelas e portas, não seja preenchido. Pode ser difícil diferenciar de forma confiável 'orifícios reais' de 'orifícios imaginários', portanto, você precisará experimentar heurísticas diferentes, como 'tamanho' e 'forma de limite'.

* **Remoção de remoção de resíduos**
   * As reflexões, as luzes brilhante e os objetos móveis podem deixar pequenas 'desilusão' persistentes flutuando no ar médio.
   * As figuras afetam a oclusão: as desilusão podem se tornar visíveis à medida que as formas escuras se movem na frente e ocluem outros hologramas.
   * As rotinas afetam os raios: se você estiver usando raycasts para ajudar os usuários a interagir com superfícies, esses raios poderão atingir uma desastagem em vez da superfície por trás dela. Assim como com os orifícios, uma mitigação é usar muitos raycasts em vez de um único raycast, mas novamente isso ocorrerá a um custo computacional.
   * As simulações afetam colisões físicas: um objeto controlado pela simulação de física pode ficar preso em uma desilusão e não conseguir se mover por uma área aparentemente clara do espaço.
   * É possível filtrar essas reações da malha da superfície. No entanto, assim como ocorre com os orifícios, você precisará ajustar seu algoritmo para que objetos pequenos reais, como arquibancadas de lâmpada e alças de porta, não seja removido.

* **Suavização**
   * O mapeamento espacial pode retornar superfícies que parecem ser aproximadas ou 'barulhentos' em comparação com suas contrapartes do mundo real.
   * A suavidade afeta colisões físicas: se o chão for aproximado, uma bola de futebol fisicamente simulada poderá não rolar suavemente em uma linha reta.
   * A suavidade afeta a renderização: se uma superfície for visualizada diretamente, os normais de superfície aproximada poderão afetar sua aparência e interromper uma aparência "limpa". É possível atenuar isso usando iluminação e texturas apropriadas no sombreador usado para renderizar a superfície.
   * É possível suavizar a áspero em uma malha de superfície. No entanto, isso pode empurrar a superfície para longe da superfície real correspondente. Manter uma correspondência próxima é importante para produzir oclusão de holograma precisos e para permitir que os usuários obtenham interações precisas e previsíveis com superfícies holographics.
   * Se apenas uma alteração superficial for necessária, pode ser suficiente para suavizar Normals de vértice sem alterar as posições de vértice.

* **Localização do plano**
   * Há muitas formas de análise que um aplicativo pode desejar executar nas superfícies fornecidas pelo mapeamento espacial.
   * Um exemplo simples é ' Localizar plano '; identificação das regiões de superfícies limitadas, em grande parte.
   * As regiões planar podem ser usadas como superfícies de trabalho Holographic, regiões em que o conteúdo Holographic pode ser colocado automaticamente pelo aplicativo.
   * As regiões planar podem restringir a interface do usuário, para orientar os usuários a interagir com as superfícies que melhor atendam às suas necessidades.
   * As regiões planar podem ser usadas como no mundo real, para contrapartes Holographic a objetos funcionais, como telas de LCD, tabelas ou quadros de comunicações.
   * As regiões planar podem definir áreas de reprodução, formando a base dos níveis de jogos de vídeo.
   * As regiões planar podem ajudar os agentes virtuais a navegar pelo mundo real, identificando as áreas de piso que as pessoas realmente têm a probabilidade de acompanhar.

## <a name="prototyping-and-debugging"></a>Protótipo e depuração

### <a name="useful-tools"></a>Ferramentas úteis

* O [emulador do HoloLens](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) pode ser usado para desenvolver aplicativos usando o mapeamento espacial sem acesso a um HoloLens físico. Ele permite simular uma sessão ao vivo em um HoloLens em um ambiente realista, com todos os dados que seu aplicativo normalmente consumiria, incluindo movimento de HoloLens, sistemas de coordenadas espaciais e malhas de mapeamento espacial. Isso pode ser usado para fornecer entradas confiáveis e reproduzíveis, que podem ser úteis para depurar problemas e avaliar alterações em seu código.
* Para reproduzir um cenário, Capture dados de mapeamento espacial pela rede de um HoloLens ao vivo e, em seguida, salve-os no disco e reutilize-os em sessões de depuração posteriores.
* A [exibição 3D](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#3d-view) do portal de dispositivos windows fornece uma maneira de ver todas as superfícies espaciais disponíveis atualmente por meio do sistema de mapeamento espacial. Isso fornece uma base de comparação para as superfícies espaciais dentro de seu aplicativo; por exemplo, você pode facilmente saber se alguma superfície espacial está ausente ou está sendo exibida no local errado.

### <a name="general-prototyping-guidance"></a>Diretrizes gerais de criação de protótipos

* Como [os erros nos](spatial-mapping.md#what-influences-spatial-mapping-quality) dados de mapeamento espacial podem afetar fortemente a experiência do usuário, recomendamos que você teste seu aplicativo em uma ampla variedade de ambientes.
* Não fique preso no hábito de sempre testar no mesmo local, por exemplo, em sua mesa. Certifique-se de testar em várias superfícies de diferentes posições, formas, tamanhos e materiais.
* Da mesma forma, embora os dados sintéticos ou gravados possam ser úteis para depuração, não se tornem muito dependentes dos mesmos poucos casos de teste. Isso pode atrasar a descoberta de problemas importantes que testes mais variados teriam capturado anteriormente.
* É uma boa ideia executar testes com usuários reais (e idealmente sem acesso), pois eles podem não usar o HoloLens ou seu aplicativo exatamente da mesma maneira que você. Na verdade, pode ser surpreendente como o comportamento, o conhecimento e as suposições das pessoas divergentes podem ser!

## <a name="troubleshooting"></a>Solução de problemas

* Para que as malhas de superfície sejam orientadas corretamente, cada GameObject precisa estar ativo antes de ser enviado ao SurfaceObserver para que sua malha seja construída. Caso contrário, as malhas aparecerão em seu espaço, mas giradas em ângulos estranho.
* O GameObject que executa o script que se comunica com o SurfaceObserver precisa ser definido como a origem. Caso contrário, todos os GameObjects que você criar e enviar ao SurfaceObserver para construir suas malhas terão um deslocamento igual ao deslocamento do Objeto de Jogo Pai. Isso pode fazer com que suas malhas mostrem vários metros de distância, o que dificulta a depuração do que está acontecendo.

## <a name="see-also"></a>Confira também

* [Sistemas de coordenadas](coordinate-systems.md)
* [Mapeamento espacial no DirectX](../develop/native/spatial-mapping-in-directx.md)
* [Mapeamento espacial no Unity](../develop/unity/spatial-mapping-in-unity.md)
* [Noções básicas sobre a cena](scene-understanding.md)
* [Visualização de varredura do ambiente](room-scan-visualization.md)
* [Projeto de som espacial](spatial-sound-design.md)
* [Estudo de caso - Como olhar através dos buracos na sua realidade](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)