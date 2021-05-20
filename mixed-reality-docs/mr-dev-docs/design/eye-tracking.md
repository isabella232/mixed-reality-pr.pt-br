---
title: Acompanhamento ocular
description: Saiba mais sobre o acompanhamento de olho para o HoloLens 2 e os novos níveis de compreensão humana se estiverem em experiências holographics.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Acompanhamento de olho, realidade misturada, entrada, olho-olhar, calibragem, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade mista, intenção, ações
ms.openlocfilehash: b76fd2e05999e5807156714fcdf12ca2863501bc
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196501"
---
# <a name="eye-tracking-on-hololens-2"></a>Acompanhamento ocular no HoloLens 2

![Demonstração de controle de olho no MRTK](images/mrtk_et_scenemenu.jpg)

O HoloLens 2 permite um novo nível de contexto e compreensão humana dentro da experiência do Holographic, fornecendo aos desenvolvedores a capacidade de usar informações sobre o que o usuário está olhando. Esta página explica como os desenvolvedores podem se beneficiar do controle de olho para vários casos de uso e o que procurar ao projetar interações de usuário com base no olhar. 

A API de acompanhamento de olho foi projetada com a privacidade de um usuário em mente, evitando a aprovação de qualquer informação identificável, especialmente qualquer biometria. Para aplicativos compatíveis com acompanhamento de olho, o usuário precisa conceder permissão de aplicativo para usar informações de controle de olho.

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
     <td>Olho-olhar</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

<br>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demonstração dos conceitos de design de controle de cabeça e olho

Se você gostaria de ver os conceitos de design de controle de cabeça e olho em ação, Confira nossa demonstração de vídeo **de acompanhamento de holograma e** acompanhamento de cabeça abaixo. Quando tiver terminado, continue em para obter mais detalhes sobre tópicos específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo foi tirado do aplicativo "criando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*

## <a name="calibration"></a>Calibragem 

Para que o acompanhamento de olho funcione com precisão, cada usuário precisa passar por uma [calibragem do usuário com acompanhamento de olho](/hololens/hololens-calibration) para o qual o usuário precisa examinar um conjunto de destinos Holographic. Isso permite que o dispositivo ajuste o sistema para uma experiência de exibição de qualidade mais confortável e mais segura para o usuário e para garantir o acompanhamento preciso do controle de olho ao mesmo tempo. 

O controle de olho deve funcionar para a maioria dos usuários, mas há casos raros em que um usuário não pode calibrar com êxito. A calibragem pode falhar por vários motivos, incluindo, mas não se limitando a: 
* O usuário optou anteriormente pelo processo de calibragem
* O usuário ficou confuso e não seguiu as metas de calibragem
* O usuário tem determinados tipos de lentes de contato e óculos, aos quais o sistema ainda não dá suporte 
* O usuário tem determinadas condições otais, de olho ou de olho, às quais o sistema ainda não dá suporte  
* Fatores externos que inibim o acompanhamento ocular confiável, como smudges no visor ou óculos do HoloLens, redução direta intensa e oclusão devido a pelos na frente dos olhos

Os desenvolvedores devem fornecer suporte adequado para usuários para os quais os dados de acompanhamento ocular podem não estar disponíveis (que não podem calibrar com êxito). Fornecemos recomendações para soluções de fallback na seção na parte inferior desta página. 

Para saber mais sobre a calibragem e sobre como garantir uma experiência suave, verifique nossa página [de calibragem do usuário de acompanhamento](/hololens/hololens-calibration) ocular.

<br>

## <a name="available-eye-tracking-data"></a>Dados de acompanhamento ocular disponíveis

Antes de entrar em detalhes sobre casos de uso específicos para entrada com o olhar, queremos apontar brevemente os recursos que a [API](/uwp/api/windows.perception.people.eyespose) de Acompanhamento Ocular do HoloLens 2 fornece. Os desenvolvedores têm acesso a um único raio de olhar (origem e direção do olhar) a aproximadamente _30 FPS (30 Hz)._
Para obter informações mais detalhadas sobre como acessar dados de acompanhamento ocular, consulte nossos guias de desenvolvedor para usar o olhar no [DirectX](../develop/native/gaze-in-directx.md) e o olhar [no Unity.](https://aka.ms/mrtk-eyes)

O olhar previsto está aproximadamente dentro de 1,5 graus no ângulo visual em torno do destino real (consulte a ilustração abaixo). Como pequenas imprecisões são esperadas, os desenvolvedores devem planejar alguma margem em torno desse valor de limite inferior (por exemplo, 2,0 a 3,0 graus pode resultar em uma experiência muito mais confortável). Discutiremos como abordar a seleção de destinos pequenos mais detalhadamente abaixo. Para que o acompanhamento ocular funcione com precisão, cada usuário deve passar por uma calibração de usuário de acompanhamento ocular. 

![Tamanho ideal do alvo em uma distância de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamanho de destino ideal a uma distância de 2 metros*

<br>

## <a name="use-cases"></a>Casos de uso

O acompanhamento ocular permite que os aplicativos acompanhem para que local o usuário está olhando em tempo real. Os casos de uso a seguir descrevem algumas interações possíveis com o acompanhamento ocular no HoloLens 2 na realidade misturada.
Esses casos de uso ainda não fazem parte da experiência de shell Holographic (ou seja, a interface que você vê quando inicia o seu HoloLens 2).
Você pode experimentar alguns deles no kit de [ferramentas de realidade misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html), que fornece vários exemplos interessantes e eficientes para usar o acompanhamento de olho, como seleções de destino com suporte rápido e sem esforço e rolagem automática pelo texto com base no que o usuário examina. 

### <a name="user-intent"></a>Intenção do usuário

As informações sobre onde e o que um usuário observa fornecem um **contexto poderoso para outras entradas**, como voz, mãos e controladores.
Isso pode ser usado para várias tarefas.
Por exemplo, isso pode variar de um **direcionamento** rápido e sem esforço em toda a cena, observando um holograma e dizendo *"Select"* (também Confira [olhar e commit](gaze-and-commit.md)) ou *"Put this..."* e, em seguida, procurando onde o usuário deseja colocar o holograma e dizer *"... lá "*. Exemplos para esse caso podem ser encontrados em [Kit de Ferramentas de Realidade Misturada – Seleção de alvo com suporte ocular](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) e [Kit de Ferramentas de Realidade Misturada – Posicionamento de alvo com suporte ocular](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html).

Além disso, um exemplo de intenção de usuário pode incluir o uso de informações sobre o que os usuários examinam para aprimorar o envolvimento com os agentes virtuais e os hologramas interativos. Por exemplo, os agentes virtuais podem adaptar as opções disponíveis e seu comportamento, com base no conteúdo exibido atualmente. 

### <a name="implicit-actions"></a>Ações implícitas

A categoria de ações implícitas está intimamente relacionada à intenção do usuário.
A ideia é que os hologramas ou os elementos da interface do usuário reagem de uma maneira instinctual que talvez nem pareça que o usuário esteja interagindo com o sistema, mas que o sistema e o usuário estejam em sincronia. Um exemplo é a **rolagem automática baseada em olhar de olho** em que o usuário pode ler um texto longo, o que inicia automaticamente a rolagem quando o usuário chega à parte inferior da caixa de texto para manter o usuário no fluxo de leitura, sem levantar um dedo.  
Um aspecto fundamental disso é que a velocidade da rolagem se adapta à velocidade de leitura do usuário.
Outro exemplo é o **zoom e a panorâmica com suporte,** em que o usuário pode se sentir como mergulhar exatamente em relação ao que ele está concentrado. Disparar e controlar a velocidade de zoom pode ser controlado pela entrada de voz ou mão, o que é importante para fornecer ao usuário a sensação de controle, evitando a sobrecarregamento. Vamos falar sobre essas considerações de design mais detalhadamente abaixo. Uma vez ampliado, o usuário pode seguir sem problemas, por exemplo, o curso de uma rua para explorar seu distrito usando o olhar.
Exemplos de demonstração para esses tipos de interações podem ser encontrados na amostra do [Kit de Ferramentas de Realidade Misturada – Navegação com suporte ocular](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html).

Outros casos de uso para _ações implícitas_ podem incluir:
- **Notificações inteligentes:** Já ficou com medo por notificações que aparecem exatamente onde você está procurando? Levando em conta o que um usuário está prestendo atenção, você pode melhorar essa experiência deslocando as notificações do local em que o usuário está olhando no momento. Isso limita as distração e as descarta automaticamente quando o usuário termina a leitura. 
- **Hologramas desamodos:** Hologramas que reagem de forma subtly ao se olharem. Isso pode variar de elementos de interface do usuário ligeiramente ativos, uma flor lentamente em um cachorro virtual começando a olhar para o usuário e abanando sua cauda. Essa interação pode fornecer uma noção interessante de conectividade e satisfação em seu aplicativo.

### <a name="attention-tracking"></a>Acompanhamento de atenção

Informações sobre onde ou o que os usuários estão olhando podem ser uma ferramenta extremamente poderosa. Ele pode ajudar a avaliar a usabilidade de designs e identificar problemas em fluxos de trabalho para torná-los mais eficientes.
A visualização e a análise de acompanhamento ocular são uma prática comum em várias áreas de aplicativo. Com o HoloLens 2, fornecemos uma nova dimensão para essa compreensão, pois os hologramas 3D podem ser colocados em contextos do mundo real e avaliados adequadamente. O [Kit de Ferramentas de Realidade Misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) fornece exemplos básicos para registro em log e carregamento de dados de acompanhamento ocular e como visualizá-los.
A Microsoft é dedicada a facilitar a inovação, garantindo que os usuários tenham uma experiência informada e transparente com como suas informações de acompanhamento ocular são usadas.  Trabalharemos com nossos desenvolvedores e equipes de experiência do usuário para fornecer diretrizes para terceiros a fim de garantir que as experiências sejam centralizadas em torno do usuário.  

Outros aplicativos nessa área podem incluir: 
-   **Visualização de olhar de olho remoto:** Visualizações de olhar de olho remoto: visualize o que os colaboradores remotos estão observando, para poder fornecer comentários imediatos e facilitar o processamento de informações mais precisos.
-   **Estudos de pesquisa do usuário:** O controle de atenção pode ajudar os pesquisadores a obter mais informações sobre como os usuários percebem e se envolvem com o ambiente natural, sem interferir, para projetar mais interações de computadores humanos instinctuals. O controle de olho pode fornecer informações que não são diretamente articuladas pelos participantes do estudo, que, de outra forma, podem ser facilmente perdidas pelo pesquisador. 
-   **Monitoramento de desempenho e treinamento:** Pratique e otimize a execução de tarefas identificando afunilamentos com mais eficiência no fluxo de execução. O controle de olho pode fornecer informações naturais, em tempo real e objetivas para ajudar a melhorar o treinamento, a produtividade e a segurança no local de trabalho. 
-   **Avaliações de design, marketing e pesquisa de consumidor:** O controle de olho permite que empresas comerciais executem estudos de marketing e de consumidor em ambientes reais ou analisem o que captura a atenção de um usuário para melhorar o design de produtos ou espaços. 

### <a name="other-use-cases"></a>Outros casos de uso

- **Jogos:** Já quis ter superpotências? Esta é a sua chance! Você pode levitater os hologramas por estrelas. Ressaltar as emissões de laser dos seus olhos-Experimente no [RoboRaid para o HoloLens 2](https://www.microsoft.com/p/roboraid/9nblggh5fv3j).
Transforme inimigos em pedra ou congele-os. Use sua visão de raios X para explorar prédios. O limite é sua imaginação.
Fique atento ao fato de não sobrecarregar o usuário – para saber mais, confira nossas [diretrizes de design de entrada com base no olhar](eye-gaze-interaction.md).

- **Avatars expressivos:** Controle de olho ajuda em avatars 3D mais expressivos usando dados de acompanhamento de olho ao vivo para animar os olhos do avatar que indicam o que o usuário está olhando. 

- **Entrada de texto:** O controle de olho pode ser usado como uma alternativa para a entrada de texto de baixo esforço, especialmente quando a fala ou as mãos são inconvenientes de usar. 

<br>

## <a name="using-eye-gaze-for-interaction"></a>Usando olho-olhar para interação

A criação de uma interação que aproveita o direcionamento de olho rápido pode ser desafiadora.
Por um lado, os olhos se movem tão rapidamente que você precisa ter cuidado sobre como usar a entrada de olhar com o olhar, pois caso contrário, os usuários podem achar a experiência desapressiva ou desadorante. Por outro lado, você também pode criar experiências verdadeiramente mágicas que vão excitar seus usuários! Para [ajudá-lo,](eye-gaze-interaction.md)confira nossa visão geral das principais vantagens, desafios e recomendações de design para o olhar para interação. 
 
## <a name="fallback-solutions-when-eye-tracking-isnt-available"></a>Soluções de fallback quando o acompanhamento ocular não está disponível

Em casos raros, os dados de acompanhamento ocular podem não estar disponíveis.
Isso pode ser devido a diferentes motivos dos quais os mais comuns estão listados abaixo:
* O sistema não conseguiu [calibrar o usuário.](/hololens/hololens-calibration)
* O usuário ignorava a [calibragem](/hololens/hololens-calibration).   
* O usuário está calibrado, mas decidiu não dar permissão ao seu aplicativo para usar seus dados de acompanhamento ocular.    
* O usuário tem óculos exclusivos ou alguma condição ocular que o sistema ainda não dá suporte. 
* Fatores externos que inibim o acompanhamento ocular confiável, como asudges no visor ou óculos do HoloLens, redução direta intensa e oclusão devido a pelos na frente dos olhos.

Os desenvolvedores devem garantir que haja suporte de fallback apropriado para esses usuários. Na página [Acompanhamento ocular no DirectX,](../develop/native/gaze-in-directx.md#fallback-when-eye-tracking-isnt-available) explicamos as APIs necessárias para detectar se os dados de acompanhamento ocular estão disponíveis. 

Embora alguns usuários possam ter decidido revogar com certeza, o acesso aos seus dados de acompanhamento ocular e estão de acordo com a troca de uma experiência inferior do usuário com a privacidade de não fornecer acesso aos dados de acompanhamento ocular, em alguns casos, isso pode não ser intencional. Se seu aplicativo usa acompanhamento ocular e essa é uma parte importante da experiência, recomendamos comunicar isso claramente ao usuário.   

Informe ao usuário por que o acompanhamento ocular é essencial para seu aplicativo (talvez até mesmo listar alguns recursos avançados) para experimentar todo o potencial do seu aplicativo, pode ajudar o usuário a entender melhor o que ele está desistindo. Ajude o usuário a identificar por que o acompanhamento de olhos pode não estar funcionando (com base nas verificações acima) e oferecer algumas sugestões para solucionar problemas em potencial rapidamente. 

Por exemplo, se você puder detectar que o sistema dá suporte ao controle de olho, o usuário será calibrado e terá, até mesmo, dada a sua permissão, mas nenhum dado de acompanhamento de olho será recebido, isso poderá apontar para alguns outros problemas, como manchas ou olhos obstruídodos. 

Há casos raros de usuários para os quais o acompanhamento de olho pode não funcionar. Portanto, seja obedientes disso, permitindo descartar ou até mesmo desabilitar lembretes para habilitar o acompanhamento de olho em seu aplicativo.

### <a name="fall-back-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>Retorne para aplicativos usando olhar de olho como um ponteiro de entrada primário

Se seu aplicativo usa olhar como uma entrada de ponteiro para selecionar rapidamente os hologramas em toda a cena, mas os dados de acompanhamento de olho não estão disponíveis, é recomendável fazer o fallback para Head-olhar e começar a mostrar o cursor Head-olhar. É recomendável usar um tempo limite (por exemplo, 500 – 1500 MS) para determinar se deseja ou não alternar. Essa ação impede que os cursores apareçam toda vez que o sistema pode perder o controle rapidamente devido a movimentos ou winks de olhos rápidos e cintilações. Se você for um desenvolvedor do Unity, o fallback automático para Head-olhar já será tratado no kit de ferramentas da realidade misturada. Se você for um desenvolvedor do DirectX, precisará lidar com esse comutador por conta própria.

### <a name="fall-back-for-other-eye-tracking-specific-applications"></a>Volte para outros aplicativos específicos de controle de olho

Seu aplicativo pode usar olhar de olho de forma exclusiva, adaptada especificamente aos olhos. Por exemplo, animar os olhos de um avatar ou atenção com base nos olhos calor depender de informações precisas sobre a atenção do Visual. Nesse caso, não há nenhum fallback claro. Se o acompanhamento de olho não estiver disponível, talvez seja necessário desabilitar esses recursos.
Novamente, é recomendável comunicar claramente isso com o usuário que talvez não esteja ciente de que a funcionalidade não está funcionando.

<br>

Essa página espero que você tenha uma boa visão geral para começar a entender a função de acompanhamento de olho e a entrada olhar para o HoloLens 2. Para começar a desenvolver, confira nossas informações sobre a função de olhar para interagir com [hologramas,](eye-gaze-interaction.md)com o olhar no [Unity](https://aka.ms/mrtk-eyes) e com o olhar [no DirectX.](../develop/native/gaze-in-directx.md)

## <a name="see-also"></a>Confira também

* [Calibragem](/hololens/hololens-calibration)
* [Conforto](comfort.md)
* [Interação com base no foco com o olhar](eye-gaze-interaction.md)
* [Olhar com o olhar no DirectX](../develop/native/gaze-in-directx.md)
* [Olhar com o olhar no Unity (Kit de Ferramentas de Realidade Misturada)](https://aka.ms/mrtk-eyes)
* [Focar e confirmar](gaze-and-commit.md)
* [Entrada de voz](../out-of-scope/voice-design.md)
