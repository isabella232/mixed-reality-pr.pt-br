---
title: Experiências compartilhadas em realidade misturada
description: Os aplicativos holográficos podem compartilhar âncoras espaciais de um HoloLens para outro, permitindo que os usuários renderizarem um holograma no mesmo local no mundo real, em vários dispositivos.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: experiência compartilhada, realidade misturada, holograma, âncora espacial, multiusuária, multiusuária
ms.openlocfilehash: 013d30bcbf3818e944eb637a792bdbc82d430f69
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184737"
---
# <a name="shared-experiences-in-mixed-reality"></a>Experiências compartilhadas em realidade misturada

Hologramas não precisa permanecer privado para apenas um usuário. Os [aplicativos holográficos](../../design/spatial-anchors.md) podem compartilhar âncoras espaciais de um dispositivo HoloLens, iOS ou Android para outro, permitindo que os usuários renderizarem um holograma no mesmo local no mundo real em vários dispositivos.

## <a name="six-questions-to-define-shared-scenarios"></a>Seis perguntas para definir cenários compartilhados

Antes de começar a criar experiências compartilhadas, é importante definir os cenários de destino. Esses cenários ajudam a esclarecer o que você está projetando e estabelecendo um vocabulário comum para ajudar a comparar e contrastar os recursos necessários em sua experiência. Entender o problema principal e os diferentes caminhos para soluções é fundamental para descobrir oportunidades inerentes a esse novo meio.

Por meio de protótipos internos e explorações de nossas HoloLens de parceiros, criamos seis perguntas para ajudá-lo a definir cenários compartilhados. Essas perguntas formam uma estrutura, não destinada a ser exaustiva, para ajudar a extração dos atributos importantes de seus cenários.

### <a name="1-how-are-they-sharing"></a>1. Como eles estão compartilhando?

Uma apresentação pode ser conduzida por um único usuário virtual, enquanto vários usuários podem colaborar ou um professor pode fornecer diretrizes para alunos virtuais que trabalham com materiais virtuais— a complexidade das experiências aumenta com base no nível de agência que um usuário tem ou pode ter em um cenário.

![Homem e mulheres com holograph na tabela](images/man-and-women-with-holograph-on-table-500px.png)

Há muitas maneiras de compartilhar, mas descobrimos que a maioria delas se enquadra em três categorias:

* **Apresentação**: quando o mesmo conteúdo está sendo mostrado a vários usuários. Por exemplo: um professor está dando uma palestra para vários alunos usando o mesmo material holográfico que está sendo apresentado a todos. No entanto, o professor pode ter suas próprias dicas e observações que podem não estar visíveis para outras pessoas.
* **Colaboração:** quando as pessoas estão trabalhando juntas para atingir algumas metas comuns. Por exemplo: o professor deu um projeto para saber mais sobre como fazer uma doença cardíaca. Os alunos emparelham e criam uma experiência de laboratório de habilidades compartilhadas, que permite que os alunos médicos colaborem no modelo de coração e aprendam.
* **Diretrizes:** quando uma pessoa está ajudando alguém a resolver um problema em uma interação de estilo mais um-para-um. Por exemplo: o professor que está dando diretrizes a um aluno quando está fazendo o laboratório de habilidades de saúde física na experiência compartilhada.

### <a name="2-what-is-the-group-size"></a>2. Qual é o tamanho do grupo?

**Experiências de compartilhamento um-para-um** podem fornecer uma linha de base forte e, idealmente, suas provas de conceito podem ser criadas nesse nível. Mas esteja ciente de que o compartilhamento com grupos grandes (além de seis pessoas) pode levar a dificuldades técnicas (dados e rede) e sociais (o impacto de estar em uma sala com vários [avatares).](https://vimeo.com/160704056) A complexidade aumenta exponencialmente conforme você vai de **grupos pequenos** **para grandes.**

Descobrimos que as necessidades de grupos podem se enquadrar em três categorias de tamanho:
* 1:1
* Pequeno < 7
* Grandes >= 7

O tamanho do grupo faz uma pergunta importante porque influencia:

* Representações de pessoas no espaço holográfico
* Escala de objetos
* Escala do ambiente

### <a name="3-where-is-everyone"></a>3. Onde estão todos?

A força da realidade misturada entra em jogo quando uma experiência compartilhada pode ocorrer no mesmo local. Chamamos isso **de colocal.** Por outro lado, quando o grupo é distribuído e pelo menos um participante não está no mesmo espaço físico (como geralmente é o caso com VR), chamamos isso de experiência **remota**. Geralmente, é o caso de  seu grupo ter participantes colocal e remotos (por exemplo, dois grupos em salas de conferência).

![Três pessoas com holograph na tabela](images/three-people-with-holograph-on-table-500px.png)

As seguintes categorias ajudam a transmitir onde os usuários estão localizados:

* **Colocated:** todos os usuários estarão no mesmo espaço físico.
* **Remoto:** todos os usuários estarão em espaços físicos separados.
* **Ambos:** seus usuários serão uma combinação de espaços colocated e remotos.

Essa pergunta é crucial porque influencia:

* Como as pessoas se comunicam?
    * Por exemplo: se eles devem ter avatares?
* Quais objetos eles veem. Todos os objetos são compartilhados?
* Se precisamos nos adaptar ao ambiente deles?

### <a name="4-when-are-they-sharing"></a>4. Quando eles estão compartilhando?

Normalmente, acreditamos em experiências **síncronas** quando as experiências compartilhadas vêm à mente: estamos fazendo isso juntos. Mas se incluímos um único elemento virtual que foi adicionado por outra pessoa, temos um **cenário assíncrono.** Imagine uma nota ou um memorando de voz, deixado em um ambiente virtual. Como você lida com 100 memorandos virtuais deixados em seu design? E se eles são de dezenas de pessoas com níveis diferentes de privacidade?

Considere suas experiências como uma destas categorias de tempo:

* **De forma síncrona:** compartilhando a experiência holográfica ao mesmo tempo. Por exemplo: dois alunos fazendo o laboratório de habilidades ao mesmo tempo.
* **De forma assíncrona:** compartilhando a experiência holográfica em momentos diferentes. Por exemplo: dois alunos fazendo o laboratório de habilidades, mas trabalhando em seções separadas em momentos diferentes.
* **Ambos:** às vezes, os usuários serão compartilhados de forma síncrona, mas outras vezes de forma assíncrona. Por exemplo: um professor fazendo a classificação da atribuição feita pelos alunos posteriormente e deixando anotações para os alunos no dia seguinte.

Essa pergunta é importante porque influencia:

* Persistência de objeto e ambiente. Por exemplo: armazenar os estados para que eles possam ser recuperados.
* Perspectiva do usuário. Por exemplo: talvez lembrar o que o usuário estava vendo ao deixar anotações.

### <a name="5-how-similar-are-their-physical-environments"></a>5. Quão semelhantes são seus ambientes físicos?

A probabilidade de dois ambientes idênticos da vida real, fora das experiências colocadas, é pequena, a menos que esses ambientes tenham sido projetados para serem idênticos. É mais provável que você tenha ambientes **semelhantes.** Por exemplo, as salas de conferência são semelhantes– elas normalmente têm uma tabela localizada centralmente entre si. As salas de estar, por outro lado, são diferentes** e podem incluir qualquer quantidade de móveis em uma matriz infinita de layouts.

![Holograph na tabela](images/holograph-on-table-500px.png)

Considere suas experiências de compartilhamento se ajustando a uma destas duas categorias:

* **Semelhante:** ambientes que tendem a ter móveis semelhantes, luz ambiente e som, tamanho físico da sala. Por exemplo: o professor está na sala de aula A e os alunos estão no sala de aula B. O sala de aula A pode ter menos alunos do que B, mas ambos podem ter uma mesa física para colocar hologramas.
* **Diferente de : ambientes** diferentes em configurações de móveis, tamanhos de sala, leve e considerações de som. Por exemplo: um professor está em uma sala de foco, mas os alunos estão em uma grande sala de aula, preenchida com alunos e professores.

É importante pensar [no ambiente](/hololens/hololens-environment-considerations), pois ele influenciará:

* Como as pessoas experimentarão esses objetos. Por exemplo: se sua experiência funcionar melhor em uma tabela e o usuário não tiver nenhuma tabela? Ou em uma superfície de piso simples, mas o usuário tem um espaço cheio.
* Escala dos objetos. Por exemplo: Colocar um modelo humano de seis pés em uma tabela pode ser um desafio, mas um modelo de coração funcionaria muito bem.

### <a name="6-what-devices-are-they-using"></a>6. Quais dispositivos eles estão usando?

Hoje, é provável que você veja experiências compartilhadas entre dois dispositivos imersivos (esses dispositivos podem diferir ligeiramente Para botões e capacidade relativa, mas não muito) ou dois [**dispositivos holográficos,**](../../discover/immersive-headset-hardware-details.md) considerando as soluções que estão sendo direcionadas a esses dispositivos.  Mas considere se dispositivos **2D** (um participante da área de trabalho ou observador móvel) serão uma consideração necessária, especialmente em situações de dispositivos **2D e 3D mistos.** Entender os tipos de dispositivos que seus participantes usarão é importante, não apenas porque eles vêm com diferentes fidelidade e restrições de dados e oportunidades, mas porque os usuários têm expectativas exclusivas para cada plataforma.

## <a name="exploring-the-potential-of-shared-experiences"></a>Explorando o potencial de experiências compartilhadas

As respostas às perguntas acima podem ser combinadas para entender melhor seu cenário compartilhado, melhorando os desafios conforme você expande a experiência. Para a equipe da Microsoft, isso ajudou a estabelecer um roteiro para melhorar as experiências que usamos hoje, compreendendo a nuance desses problemas complexos e como aproveitar as experiências compartilhadas na realidade misturada.

Por exemplo, considere um dos Skype do HoloLens: um usuário trabalhou em [](https://www.youtube.com/watch?v=iBfzs3G8BEA) como corrigir um comutadores de luz quebrados com a ajuda de um especialista localizado remotamente.

![Corrigindo um comáforo de luz com assistência Skype para HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

*Um especialista fornece **diretrizes 1:1** de seu **computador 2D,** desktop para um usuário de um dispositivo **3D de realidade** misturada. As **diretrizes** são **síncronas** e os ambientes físicos **são diferentes.***

Uma experiência como essa é uma mudança de etapa da nossa experiência atual, aplicando o paradigma de vídeo e voz a uma nova mídia. Mas, ao olharmos para o futuro, devemos definir melhor a oportunidade de nossos cenários e criar experiências que reflitam a força da realidade misturada.

Considere a [ferramenta de colaboração OnSight](https://www.youtube.com/watch?v=XtUyUJAVQ6w), desenvolvida pelo Laboratório jet-in da NASA. Os cientistas que trabalham nos dados das missões de sonda de Mars podem colaborar com colegas em tempo real dentro dos dados da paisagem do País.

![Colaboração entre colegas separados remotamente para planejar o trabalho para o Mars Rover](images/onsight-nasa-jpl.gif)

*Um cientista explora um ambiente usando um dispositivo de  realidade **misturada 3D** com um pequeno grupo de colegas remotos usando dispositivos **3D e 2D.**  A **colaboração** **é síncrona** (mas pode ser revisitada de forma assíncrona) e os ambientes físicos são (virtualmente) **semelhantes.***

Experiências como o OnSight apresentam novas oportunidades para colaborar. Desde apontar fisicamente elementos no ambiente virtual para ficar ao lado de um colega e compartilhar sua perspectiva enquanto explicam suas descobertas. O OnSight usa a lente de imersão e presença para reavaliar experiências de compartilhamento na realidade misturada.

A colaboração intuitiva é a base da conversa, trabalhar em conjunto e entender como podemos aplicar essa inserção à complexidade da realidade misturada é crucial. Se não apenas recriarmos experiências de compartilhamento na realidade misturada, mas sobrecarregá-las, será uma mudança de paradigma para o futuro do trabalho. A criação de experiências compartilhadas na realidade misturada é um espaço novo e empolgante– e estamos apenas no início.

## <a name="get-started-building-shared-experiences"></a>Começar a criar experiências compartilhadas

Dependendo do aplicativo e do cenário, haverá vários requisitos para obter sua experiência desejada. Entre eles estão:

* **Criação de união:** capacidade de criar sessões, anunciar sessões, descobrir e convidar pessoas específicas, local e remotamente para ingressar em sua sessão.
* **Compartilhamento de** âncora: capacidade de alinhar coordenadas em vários dispositivos em um espaço local comum, de modo que os hologramas apareçam no mesmo local para todas as pessoas.
* **Rede:** capacidade de ter posições, interações e movimentos de pessoas e hologramas sincronizados em tempo real em todos os participantes.
* **Armazenamento de estado:** capacidade de armazenar características e locais do holograma no espaço para junção de sessão média, recall em um momento posterior e robustez em relação a problemas de rede.

A chave para experiências compartilhadas é fazer com que vários usuários vejam os mesmos hologramas no mundo em seu próprio dispositivo, frequentemente feito compartilhando âncoras para alinhar coordenadas entre dispositivos.

Para compartilhar âncoras, use as Âncoras Espaciais do [Azure:](/azure/spatial-anchors)

* Primeiro, o usuário coloca o holograma.
* O aplicativo cria [uma âncora espacial](../../design/spatial-anchors.md)para fixar esse holograma precisamente no mundo.
* As âncoras podem ser compartilhadas com HoloLens, iOS e Android por meio das Âncoras Espaciais [do Azure.](/azure/spatial-anchors/)

Com uma âncora espacial compartilhada, o aplicativo em cada dispositivo agora tem um sistema de [coordenadas](../../design/coordinate-systems.md) comum no qual eles podem colocar conteúdo. Agora, o aplicativo pode garantir a posição e orientar o holograma no mesmo local.

Em HoloLens dispositivos, você também pode compartilhar âncoras offline de um dispositivo para outro.  Use os links abaixo para decidir o que é melhor para seu aplicativo.

## <a name="evaluating-tech-options"></a>Avaliando opções de tecnologia

Há várias opções de serviço e tecnologia disponíveis para ajudar a criar experiências de realidade misturada de vários usuários.  Pode ser complicado escolher um caminho, portanto, tendo uma perspectiva voltada para o cenário, algumas opções são detalhadas abaixo.

## <a name="shared-static-holograms-no-interactions"></a>Hologramas estáticos compartilhados (sem interações)

Aproveite [as Âncoras Espaciais do Azure](/azure/spatial-anchors/) em seu aplicativo.  A habilitação e o compartilhamento de âncoras espaciais entre dispositivos permitem que você crie um aplicativo em que os usuários vejam hologramas no mesmo local ao mesmo tempo.  A sincronização adicional entre dispositivos é necessária para permitir que os usuários interajam com hologramas e vejam movimentações ou atualizações de estado de hologramas.

## <a name="share-first-person-perspective"></a>Compartilhar perspectiva da primeira pessoa

Aproveite o suporte interno Miracast, para usuários locais quando você tiver um receptor de Miracast com suporte, como um PC ou TV – nenhum código de aplicativo adicional é necessário.

Aproveite [MixedReality-WebRTC](https://github.com/microsoft/mixedreality-webrtc) em seu aplicativo, para usuários remotos ou quando você tiver Miracast dispositivos que você gostaria de compartilhar.  Habilitar uma conexão WebRTC permite fluxos de áudio/vídeo 1:1 entre usuários, com um canal de dados para mensagens entre dispositivos também.  A implementação de realidade misturada otimiza para HoloLens, fornecendo fluxo de vídeo de captura de realidade misturada da exibição do HoloLens usuário para outras pessoas.  Se você quiser escalar o streaming de vídeo para vários clientes remotos, um provedor de serviços [MCU](https://webrtcglossary.com/mcu/) (Unidade de Conferência multipoint) normalmente será usado, como [SignalWire.](https://signalwire.com/)  Uma implantação do SignalWire com um clique no Azure está disponível por meio [do Freeswitch.](https://github.com/andywolk/azure-freeswitch-gpu-windows)

> [!NOTE]
> Observe que SignalWire é um serviço pago e não pertence/é afiliado à Microsoft.

## <a name="presenter-spectator-applications-and-demos"></a>Presenter-Spectator aplicativos e demonstrações

Aproveite [MixedReality-View para](https://github.com/microsoft/MixedReality-SpectatorView) trazer a [funcionalidade de exibição de espectador](spectator-view.md) para seu aplicativo.  Habilita outros dispositivos (HL, Android, iOS e câmeras de vídeo) para ver o que o HoloLens vê de uma perspectiva diferente no mesmo local e receber atualizações sobre as interações do host HoloLens usuário interagindo com os hologramas.  Assista, tire fotos e grave um vídeo do que o host faz com os hologramas no aplicativo de sua própria perspectiva espacial com o colega espectador do mesmo aplicativo.

**Observação:** As imagens são feitas por meio de captura de tela em dispositivos iOS/Android.

## <a name="multi-user-collaborative-experience"></a>Experiência colaborativa de vários usuários
<!--Unity Note-->
Comece com nosso [tutorial de](../unity/tutorials/mr-learning-sharing-02.md)aprendizado de vários usuários, que aproveita as Âncoras Espaciais do [Azure](/azure/spatial-anchors/) para usuários locais e o [SDK](https://www.photonengine.com/PUN) do Photon para sincronizar o conteúdo/estado na cena. Crie aplicativos colaborativos localmente em que cada usuário tenha sua própria perspectiva sobre os hologramas na cena e possa interagir totalmente com os hologramas.  As atualizações são fornecidas em todos os dispositivos e o gerenciamento de conflitos de interação é tratado pelo Photon.

> [!NOTE]
> Observe que [o Photon](https://www.photonengine.com/) é um produto que não é da Microsoft, portanto, uma relação de cobrança com o Photon pode ser necessária para o productize e a escala para um uso mais alto.

## <a name="future-work"></a>Trabalho futuro

As funcionalidades e interfaces de componente ajudarão a fornecer consistência comum e suporte robusto em vários cenários e tecnologias subjacentes.  Até lá, escolha o melhor caminho que se alinha ao cenário que você está tentando alcançar em seu aplicativo.

Cenário diferente ou desejo de usar uma tecnologia/serviço diferente? Forneça comentários como GitHub problemas no repo correspondente, na parte inferior desta página ou entre em contato com [o HoloDevelopers slack](https://holodevelopers.slack.com/).

## <a name="see-also"></a>Veja também

* [Âncoras Espaciais do Azure](/azure/spatial-anchors)
* [Âncoras espaciais compartilhadas no DirectX](shared-spatial-anchors-in-directx.md)
* [Experiências compartilhadas no Unity](../unity/shared-experiences-in-unity.md)
* [Modo de exibição Espectador](spectator-view.md)