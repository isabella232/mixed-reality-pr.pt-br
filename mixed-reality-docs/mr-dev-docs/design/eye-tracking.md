---
title: Acompanhamento ocular
description: Saiba mais sobre o acompanhamento ocular para HoloLens 2 e os novos níveis de compreensão humana se os recursos em experiências holográficas.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Acompanhamento ocular, realidade misturada, entrada, olhar com o olhar, calibragem, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Toolkit realidade misturada, intenção, ações
ms.openlocfilehash: ce8ffcb6b8b59b6b0484ba4b3db256a8df5810ea2719416bea9e3f4366ad6afe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214131"
---
# <a name="eye-tracking-on-hololens-2"></a>Acompanhamento ocular no HoloLens 2

![Demonstração de acompanhamento ocular no MRTK](images/mrtk_et_scenemenu.jpg)

HoloLens 2 permite um novo nível de contexto e compreensão humana dentro da experiência holográfica, fornecendo aos desenvolvedores a capacidade de usar informações sobre o que o usuário está vendo. Esta página explica como os desenvolvedores podem se beneficiar do acompanhamento ocular para vários casos de uso e o que procurar ao criar interações do usuário com base no olhar. 

A API de acompanhamento ocular foi projetada com a privacidade do usuário em mente, evitando passar informações identificáveis, especialmente qualquer biometria. Para aplicativos com capacidade para acompanhamento ocular, o usuário precisa conceder permissão ao aplicativo para usar informações de acompanhamento ocular.

### <a name="device-support"></a>Suporte a dispositivos

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
     <td>Olhar com o olhar</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

<br>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demonstração dos conceitos de design de rastreamento da cabeça e dos olhos

Se quiser ver os conceitos de design de rastreamento da cabeça e dos olhos em ação, confira abaixo nosso vídeo de demonstração do **Projetando hologramas - Rastreamento da cabeça e rastreamento dos olhos**. Depois de assistir ao vídeo, prossiga para saber mais sobre os tópicos específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo foi retirado do aplicativo "Projetando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*

## <a name="calibration"></a>Calibragem 

Para que o acompanhamento ocular funcione com precisão, [](/hololens/hololens-calibration) cada usuário precisa passar por uma calibragem de usuário de acompanhamento ocular para a qual o usuário precisa olhar para um conjunto de destinos holográficos. Isso permite que o dispositivo ajuste o sistema para uma experiência de exibição mais confortável e de maior qualidade para o usuário e para garantir o acompanhamento ocular preciso ao mesmo tempo. 

O acompanhamento ocular deve funcionar para a maioria dos usuários, mas há casos raros em que um usuário não pode calibrar com êxito. A calibragem pode falhar por vários motivos, incluindo, mas não se limitando a: 
* O usuário rejeitou o processo de calibragem anteriormente
* O usuário ficou confuso e não seguiu as metas de calibragem
* O usuário tem determinados tipos de lentes de contato e óculos, aos quais o sistema ainda não dá suporte 
* O usuário tem determinadas condições otais, de olho ou de olho, às quais o sistema ainda não dá suporte  
* Fatores externos que inibim o acompanhamento ocular confiável, como smudges no visor ou óculos do HoloLens, redução direta intensa e oclusão devido a pelos na frente dos olhos

Os desenvolvedores devem fornecer suporte adequado para usuários para os quais os dados de acompanhamento ocular podem não estar disponíveis (que não podem calibrar com êxito). Fornecemos recomendações para soluções de fallback na seção na parte inferior desta página. 

Para saber mais sobre a calibragem e sobre como garantir uma experiência suave, verifique nossa página [de calibragem do usuário de acompanhamento](/hololens/hololens-calibration) ocular.

<br>

## <a name="available-eye-tracking-data"></a>Dados de acompanhamento ocular disponíveis

Antes de entrar em detalhes sobre casos de uso específicos para entrada com o olhar, queremos apontar brevemente os recursos que a [API](/uwp/api/windows.perception.people.eyespose) de Acompanhamento Ocular HoloLens 2 fornece. Os desenvolvedores têm acesso a um único raio de olhar (origem e direção do olhar) a aproximadamente _30 FPS (30 Hz)._
Para obter informações mais detalhadas sobre como acessar dados de acompanhamento ocular, consulte nossos guias de desenvolvedor para usar o olhar no [DirectX](../develop/native/gaze-in-directx.md) e o olhar [no Unity.](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

O olhar previsto está aproximadamente dentro de 1,5 graus no ângulo visual em torno do destino real (consulte a ilustração abaixo). Como pequenas imprecisões são esperadas, os desenvolvedores devem planejar alguma margem em torno desse valor de limite inferior (por exemplo, 2,0 a 3,0 graus pode resultar em uma experiência muito mais confortável). Discutiremos como abordar a seleção de destinos pequenos mais detalhadamente abaixo. Para que o acompanhamento ocular funcione com precisão, cada usuário deve passar por uma calibração de usuário de acompanhamento ocular. 

![Tamanho ideal do alvo em uma distância de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamanho de destino ideal a uma distância de 2 metros*

<br>

## <a name="use-cases"></a>Casos de uso

O acompanhamento ocular permite que os aplicativos acompanhem para que local o usuário está olhando em tempo real. Os casos de uso a seguir descrevem algumas interações possíveis com o acompanhamento ocular HoloLens 2 na realidade misturada.
Esses casos de uso ainda não fazem parte da experiência do Shell Holographic (ou seja, a interface que você vê ao iniciar seu HoloLens 2).
Você pode experimentar alguns [](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)deles no Toolkit de Realidade Misturada, que fornece vários exemplos interessantes e poderosos para usar o acompanhamento ocular, como seleções de destino rápidas e sem esforço com suporte ocular e rolagem automática pelo texto com base na aparência do usuário. 

### <a name="user-intent"></a>Intenção do usuário

Informações sobre onde e o que um usuário analisa fornece um **contexto** poderoso para outras entradas, como voz, mãos e controladores.
Isso pode ser usado para várias tarefas.
Por exemplo, isso pode variar de  direcionamento rápido e fácil em toda a cena, observando um holograma e dizendo *"selecionar"* (também ver foco e confirmação [)](gaze-and-commit.md)ou *"colocar isso..."*, em seguida, observando onde o usuário deseja colocar o holograma e dizer *"... there"*. Exemplos para esse caso podem ser encontrados em [Kit de Ferramentas de Realidade Misturada – Seleção de alvo com suporte ocular](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) e [Kit de Ferramentas de Realidade Misturada – Posicionamento de alvo com suporte ocular](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-positioning).

Além disso, um exemplo de intenção do usuário pode incluir o uso de informações sobre o que os usuários estão procurando para aprimorar o envolvimento com agentes virtuais e hologramas interativos. Por exemplo, os agentes virtuais podem adaptar as opções disponíveis e seu comportamento, com base no conteúdo exibido no momento. 

### <a name="implicit-actions"></a>Ações implícitas

A categoria de ações implícitas está intimamente relacionada à intenção do usuário.
A ideia é que os hologramas ou elementos de interface do usuário reajam de uma maneira instintiva que pode até mesmo parecer que o usuário está interagindo com o sistema, mas, em vez disso, que o sistema e o usuário estão em sincronia. Um exemplo  é a rolagem automática baseada no foco com o olhar, em que o usuário pode ler um texto longo, que começa a rolar automaticamente quando o usuário chega à parte inferior da caixa de texto para manter o usuário no fluxo de leitura, sem a necessidade de deslizar o dedo.  
Um aspecto importante disso é que a velocidade de rolagem se adapta à velocidade de leitura do usuário.
Outro exemplo é **o** zoom com suporte com o olhar e a panoragem em que o usuário pode se sentir exatamente voltado para o que ele se concentra. Disparar e controlar a velocidade de zoom pode ser controlado pela entrada de voz ou mão, o que é importante para fornecer ao usuário a sensação de controle, evitando a sobrecarregamento. Vamos falar sobre essas considerações de design mais detalhadamente abaixo. Uma vez ampliado, o usuário pode seguir sem problemas, por exemplo, o curso de uma rua para explorar seu distrito usando o olhar.
Exemplos de demonstração para esses tipos de interações podem ser encontrados na amostra do [Kit de Ferramentas de Realidade Misturada – Navegação com suporte ocular](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation).

Outros casos de uso para _ações implícitas_ podem incluir:
- **Notificações inteligentes:** Já ficou com medo por notificações que aparecem exatamente onde você está procurando? Levando em conta o que um usuário está prestendo atenção, você pode melhorar essa experiência deslocando as notificações do local em que o usuário está olhando no momento. Isso limita as distração e as descarta automaticamente quando o usuário termina a leitura. 
- **Hologramas desalojados:** Hologramas que reagem de maneira subtenta ao serem acarrados. Isso pode variar de elementos de interface do usuário ligeiramente ativos, uma flor lentamente em um cachorro virtual começando a olhar para o usuário e abanando sua cauda. Essa interação pode fornecer uma noção interessante de conectividade e satisfação em seu aplicativo.

### <a name="attention-tracking"></a>Acompanhamento de atenção

Informações sobre onde ou o que os usuários estão olhando podem ser uma ferramenta extremamente poderosa. Ele pode ajudar a avaliar a usabilidade de designs e identificar problemas em fluxos de trabalho para torná-los mais eficientes.
A visualização e a análise de acompanhamento ocular são uma prática comum em várias áreas de aplicativo. Com HoloLens 2, fornecemos uma nova dimensão para essa compreensão, pois os hologramas 3D podem ser colocados em contextos do mundo real e avaliados adequadamente. O [Toolkit realidade misturada](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main) fornece exemplos básicos para registro em log e carregamento de dados de acompanhamento ocular e como visualizá-los.
A Microsoft é dedicada a facilitar a inovação, garantindo que os usuários tenham uma experiência informada e transparente com como suas informações de acompanhamento ocular são usadas.  Trabalharemos com nossos desenvolvedores e equipes de experiência do usuário para fornecer diretrizes para terceiros a fim de garantir que as experiências sejam centralizadas em torno do usuário.  

Outros aplicativos nessa área podem incluir: 
-   **Visualização de olhar remoto:** Visualizações de olhar remoto: visualize o que os colaboradores remotos estão vendo, para poder fornecer comentários imediatos e facilitar o processamento de informações mais preciso.
-   **Estudos de pesquisa de usuário:** O acompanhamento de atenção pode ajudar os pesquisadores a obter mais informações sobre como os usuários agem e se envolvem com o ambiente natural, sem interferir, a criar interações mais instintivas entre humanos e computadores. O acompanhamento ocular pode fornecer informações que não são articuladas diretamente pelos participantes do estudo, que, caso contrário, podem ser facilmente perdidas pelo pesquisador. 
-   **Treinamento e monitoramento de desempenho:** Pratique e otimize a execução de tarefas identificando gargalos com mais eficiência no fluxo de execução. O acompanhamento ocular pode fornecer informações naturais, em tempo real e objetivos para ajudar a melhorar o treinamento, a produtividade e a segurança no local de trabalho. 
-   **Avaliações de design, marketing e pesquisa de consumidor:** O acompanhamento ocular permite que as empresas comerciais realizem estudos de marketing e consumidores em ambientes do mundo real ou analisem o que captura a atenção de um usuário para melhorar o design de produto ou espaço. 

### <a name="other-use-cases"></a>Outros casos de uso

- **Jogos:** Alguma vez você queria ter pessoas de bem-estar? Esta é a sua chance! Você pode fazer hologramas se olharem para eles. Dispare raios de raios de seus olhos – experimente no [RoboRaid para HoloLens 2](https://www.microsoft.com/p/roboraid/9nblggh5fv3j).
Transforme os cérebros em rochas ou congele-os. Use sua visão de raios X para explorar prédios. O limite é sua imaginação.
Tenha cuidado para não sobrecarregar o usuário – para saber mais, confira nossas diretrizes de [design](eye-gaze-interaction.md)de entrada com base no olhar.

- **Avatares expressivas:** O acompanhamento ocular ajuda em avatars 3D mais expressivas usando dados de acompanhamento ocular ao vivo para animar os olhos do avatar que indicam o que o usuário está olhando. 

- **Entrada de texto:** O acompanhamento ocular pode ser usado como uma alternativa para entrada de texto de baixo esforço, especialmente quando fala ou mãos são inconvenientes de usar. 

<br>

## <a name="using-eye-gaze-for-interaction"></a>Usando o olhar com o olhar para interação

Criar uma interação que aproveita o direcionamento de olho em movimento rápido pode ser um desafio.
Por um lado, os olhos se movem tão rapidamente que você precisa ter cuidado sobre como usar a entrada de olhar com o olhar, pois caso contrário, os usuários podem achar a experiência desapressiva ou desadorante. Por outro lado, você também pode criar experiências verdadeiramente mágicas que vão excitar seus usuários! Para [ajudá-lo,](eye-gaze-interaction.md)confira nossa visão geral das principais vantagens, desafios e recomendações de design para o olhar para interação. 
 
## <a name="fallback-solutions-when-eye-tracking-isnt-available"></a>Soluções de fallback quando o acompanhamento ocular não está disponível

Em casos raros, os dados de acompanhamento ocular podem não estar disponíveis.
Isso pode ser devido a diferentes motivos dos quais os mais comuns estão listados abaixo:
* O sistema não conseguiu [calibrar o usuário.](/hololens/hololens-calibration)
* O usuário ignorava a [calibragem](/hololens/hololens-calibration).   
* O usuário está calibrado, mas decidiu não dar permissão ao seu aplicativo para usar seus dados de acompanhamento ocular.    
* O usuário tem óculos exclusivos ou alguma condição ocular que o sistema ainda não dá suporte. 
* Fatores externos que inibim o acompanhamento ocular confiável, como asudges no visor do HoloLens ou óculos, redução direta intensa e oclusão devido a pelos na frente dos olhos.

Os desenvolvedores devem garantir que haja suporte de fallback apropriado para esses usuários. Na página [Acompanhamento ocular no DirectX,](../develop/native/gaze-in-directx.md#fallback-when-eye-tracking-isnt-available) explicamos as APIs necessárias para detectar se os dados de acompanhamento ocular estão disponíveis. 

Embora alguns usuários possam ter decidido revogar com certeza, o acesso aos seus dados de acompanhamento ocular e estão de acordo com a troca de uma experiência inferior do usuário com a privacidade de não fornecer acesso aos dados de acompanhamento ocular, em alguns casos, isso pode não ser intencional. Se seu aplicativo usa acompanhamento ocular e essa é uma parte importante da experiência, recomendamos comunicar isso claramente ao usuário.   

Informe ao usuário por que o acompanhamento ocular é essencial para seu aplicativo (talvez até mesmo listar alguns recursos avançados) para experimentar todo o potencial do seu aplicativo, pode ajudar o usuário a entender melhor o que ele está desistindo. Ajude o usuário a identificar por que o acompanhamento ocular pode não estar funcionando (com base nas verificações acima) e ofereça algumas sugestões para solucionar rapidamente possíveis problemas. 

Por exemplo, se você puder detectar que o sistema dá suporte ao acompanhamento ocular, o usuário será calibrado e até mesmo terá dado sua permissão, mas nenhum dado de acompanhamento ocular será recebido, então isso poderá apontar para alguns outros problemas, como asudges ou os olhos que estão sendo ocluídos. 

Há casos raros de usuários para os quais o acompanhamento ocular pode não funcionar. Portanto, não deixe de respeitar isso, permitindo descartar ou até mesmo desabilitar lembretes para habilenciar o acompanhamento ocular em seu aplicativo.

### <a name="fall-back-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>Fall back para aplicativos que usam o foco com o olhar como um ponteiro de entrada primário

Se seu aplicativo usa o foco com o olhar como uma entrada de ponteiro para selecionar rapidamente hologramas em toda a cena, mas os dados de acompanhamento ocular não estão disponíveis, recomendamos voltar ao foco com a cabeça e começar a mostrar o cursor de foco com a cabeça. É recomendável usar um tempo final (por exemplo, 500 a 1500 ms) para determinar se é preciso alternar ou não. Essa ação impede que os cursores apareçam sempre que o sistema pode perder rapidamente o controle devido a movimento ocular rápido ou pisca e pisca. Se você for um desenvolvedor do Unity, o fallback automático para o olhar com a cabeça já será tratado no Toolkit. Se você for um desenvolvedor do DirectX, precisará lidar com essa opção por conta própria.

### <a name="fall-back-for-other-eye-tracking-specific-applications"></a>Fall back para outros aplicativos específicos do acompanhamento ocular

Seu aplicativo pode usar o olhar com o olhar de uma maneira exclusiva, adaptada especificamente aos olhos. Por exemplo, animar os olhos de um avatar ou para mapas de calor de atenção com base nos olhos que dependem de informações precisas sobre a atenção visual. Nesse caso, não há nenhum fallback claro. Se o acompanhamento ocular não estiver disponível, talvez esses recursos precisem ser desabilitados.
Novamente, recomendamos comunicar claramente isso ao usuário que pode não estar ciente de que a funcionalidade não está funcionando.

<br>

Espera-se que esta página tenha fornecido uma boa visão geral para você começar a entender a função de acompanhamento ocular e a entrada de olhar para HoloLens 2. Para começar a desenvolver, confira nossas informações sobre a função de olhar para interagir com [hologramas,](eye-gaze-interaction.md)com o olhar no [Unity](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main) e com o olhar [no DirectX.](../develop/native/gaze-in-directx.md)

## <a name="see-also"></a>Confira também

* [Calibragem](/hololens/hololens-calibration)
* [Conforto](comfort.md)
* [Interação com base no foco com o olhar](eye-gaze-interaction.md)
* [Olhar com o olhar no DirectX](../develop/native/gaze-in-directx.md)
* [Olhar com o olhar no Unity (realidade misturada Toolkit)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)
* [Focar e confirmar](gaze-and-commit.md)
* [Entrada de voz](../out-of-scope/voice-design.md)