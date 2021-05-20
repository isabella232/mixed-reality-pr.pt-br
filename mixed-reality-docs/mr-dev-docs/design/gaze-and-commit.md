---
title: Focar e confirmar
description: Saiba mais sobre o modelo de entrada de olhar e confirmação, incluindo dois tipos de olhar (com o olhar e com o olhar) e vários tipos de confirmação.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidade Misturada, olhar, direcionamento de olhar, interação, design, acompanhamento ocular, acompanhamento de cabeça, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada
ms.openlocfilehash: db394ab4aded7136550e8e88eb3d66e06f3eeb92
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196561"
---
# <a name="gaze-and-commit"></a>Focar e confirmar

_O olhar e_ a confirmação são um modelo de entrada fundamental que está intimamente relacionado à maneira como estamos interagindo com nossos computadores usando o mouse: aponte para & _clique em_. Nesta página, apresentamos dois tipos de entrada de olhar (com a cabeça e o olhar) e diferentes tipos de ações de commit. _O olhar e a commit_ são considerados um modelo de entrada distante com manipulação indireta. Ele é mais bem usado para interagir com o conteúdo holográfico que está fora de alcance.

Os headsets de realidade misturada podem usar a posição e a orientação da cabeça do usuário para determinar o vetor de direção da cabeça. Pense no foco como um raio apontando diretamente para frente diretamente entre os olhos do usuário. Essa é uma aproximação bastante grosseira da direção para a qual o usuário está olhando. Seu aplicativo pode intersecção desse raio com objetos virtuais ou do mundo real e desenhar um cursor nesse local para permitir que o usuário saiba o que ele está direcionando.

Além do olhar para a cabeça, alguns headsets de realidade misturada, como o HoloLens 2, incluem sistemas de acompanhamento ocular que produzem um vetor de olhar. Isso fornece uma medida refinada da direção para a qual o usuário está olhando. Em ambos os casos, o olhar representa um sinal importante para a intenção do usuário. Quanto melhor o sistema puder interpretar e prever as ações pretendíveis do usuário, mais satisfação e desempenho do usuário melhorarão.

Abaixo estão alguns exemplos de como você, como desenvolvedor de realidade misturada, pode se beneficiar do olhar ou da cabeça:
* Seu aplicativo pode interseção de olhar com os hologramas em sua cena para determinar onde está a atenção do usuário (mais preciso com o olhar).
* Seu aplicativo pode canalizar gestos e pressionas de controlador com base no olhar do usuário, o que permite que o usuário selecione, ative, segure, role ou interaja diretamente com seus hologramas.
* Seu aplicativo pode permitir que o usuário Coloque os hologramas em superfícies do mundo real interseccionando seu olhar Ray com a malha de mapeamento espacial.
* Seu aplicativo pode saber quando o usuário não está olhando para a direção de um objeto importante, o que pode fazer com que seu aplicativo dê indicações visuais e de áudio para virar esse objeto.

<br>

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Foco com a cabeça e confirmação</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</td>
        <td>➕ Opção alternativa</td>
    </tr>
         <tr>
        <td>Focar com o olhar e confirmar</td>
        <td>❌ Não disponível</td>
        <td>✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</td>
        <td>❌ Não disponível</td>
    </tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demonstração dos conceitos de design de controle de cabeça e olho

Se você gostaria de ver os conceitos de design de controle de cabeça e olho em ação, Confira nossa demonstração de vídeo **de acompanhamento de holograma e** acompanhamento de cabeça abaixo. Quando tiver terminado, continue em para obter mais detalhes sobre tópicos específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo foi tirado do aplicativo "criando hologramas" do HoloLens 2. Baixe e aproveite a experiência completa [aqui](https://aka.ms/dhapp).*

## <a name="gaze"></a>Focar

### <a name="eye--or-head-gaze"></a>Olho ou cabeça-olhar?
Há várias considerações ao enfrentar a pergunta se você deve usar o modelo de entrada "olho-olhar e confirmar" ou "Head-olhar e Commit". Se você estiver desenvolvendo para um headset de imersão ou para o HoloLens (1º gen), a escolha será simples: Head-olhar e Commit. Se você estiver desenvolvendo para o HoloLens 2, a escolha se tornará um pouco mais difícil. É importante entender as vantagens e os desafios que acompanham cada um deles.
Compilamos alguns dos nossos profissionais e contratados na tabela abaixo para contrastars em contraste com a olhar de direcionamento. Isso está longe de ser concluído e sugerimos saber mais sobre o direcionamento olhar para a realidade misturada aqui:
* [Acompanhamento de olho no hololens 2](eye-tracking.md): introdução geral do nosso novo recurso de acompanhamento de olho no hololens 2, incluindo algumas diretrizes para desenvolvedores. 
* [Olhar interação](eye-gaze-interaction.md)entre os olhos: considerações de design e recomendações ao planejar o uso de acompanhamento de olho como uma entrada.

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>Direcionamento de olhar de olho</strong></td>
        <td><strong>Direcionamento de foco com a cabeça</strong></td>
    </tr>
    <tr>
        <td>Rápida!</td>
        <td>Mais lento</td>
    </tr>
    <tr>
        <td>Baixo esforço (praticamente todos os movimentos de corpo necessários)</td>
        <td>Pode ser fatiguing – Possível estresse (por exemplo, tensão de cabeça)</td>
    </tr>
    <tr>
        <td>Não requer um cursor, mas comentários sutis são recomendados</td>
        <td>Requer para mostrar um cursor</td>
    </tr>
    <tr>
        <td>Sem movimentos de olho suaves – por exemplo, não é bom para desenho</td>
        <td>Mais controlado e explícito</td>
    </tr>
    <tr>
        <td>Difícil para destinos pequenos (por exemplo, botões pequenos ou weblinks)</td>
        <td>Confiável! Excelente fallback!</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

Se você usar o olhar com a cabeça ou com o olhar para seu modelo de entrada de olhar e de commit, cada um deles vem com diferentes conjuntos de restrições de design. Eles são abordados separadamente nos artigos [de](gaze-and-commit-eyes.md) confirmação e de olhar com o olhar e [com a cabeça e commit.](gaze-and-commit-head.md)

<br>

---

### <a name="cursor"></a>Cursor

:::row:::
    :::column:::
        Para o olhar para a cabeça, a maioria dos aplicativos deve usar um [cursor](cursors.md) ou outra indicação auditiva/visual para dar ao usuário confiança sobre com o que eles estão prestes a interagir. Normalmente, você posiciona esse cursor no mundo em que o raio de olhar de cabeça primeiro intersecciona um objeto, que pode ser um holograma ou uma superfície do mundo real.<br>
        <br>
        Para o foco com  o olhar, geralmente recomendamos não mostrar um cursor, pois isso pode se tornar rapidamente uma distração e uma distração para o usuário. Em vez disso, realça subtly os destinos visuais ou use um cursor de olho para dar confiança sobre com o que o usuário está prestes a interagir. Para obter mais informações, confira nossas [diretrizes de design para](eye-tracking.md) entrada com base nos olhos no HoloLens 2.
    :::column-end:::
        :::column:::
       ![Um cursor visual de exemplo para mostrar o olhar](images/cursor.jpg)<br>
       *Imagem: um cursor visual de exemplo para mostrar o olhar*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>Commit
Depois de falar sobre diferentes maneiras _de_ olhar para um destino, vamos falar um pouco mais sobre a parte _de confirmação_ no olhar e fazer _commit do_.
Depois de direcionar um objeto ou elemento de interface do usuário, o usuário pode interagir ou clicar nele usando uma entrada secundária. Isso é conhecido como a etapa de confirmação do modelo de entrada. 

Os seguintes métodos de confirmação são compatíveis:
- Gesto de toque do ar à mão (ou seja, eleve sua mão na frente e reúna o dedo e o polegar)
- Diga _"Select"_ ou um dos comandos de voz de destino
- Pressione um único botão em um [clicador de HoloLens](/hololens/hololens1-clicker)
- Pressione o botão ' A ' em um gamepad do Xbox
- Pressione o botão ' A ' em um controlador adaptável do Xbox

### <a name="gaze-and-air-tap-gesture"></a>Gesto de toque olhar e Air
Fechar e abrir dedos indicador e polegar é um gesto de tocar feito com a mão levantada. Para usar um toque de ar, aumente o seu indicador para a posição pronta, aperte o polegar e aumente o seu dedo de índice de volta para o lançamento. No HoloLens (1ª gen), o Air Tap é a entrada secundária mais comum.


:::row:::
    :::column:::
       ![Dedo na posição pronta](images/readyandpress-ready.jpg)<br>
       **Dedo na posição pronta**<br>
    :::column-end:::
    :::column:::
       ![Pressione dedo para baixo para tocar ou clique](images/readyandpress-press.jpg)<br>
        **Pressione dedo para baixo para tocar ou clique**<br>
    :::column-end:::
:::row-end:::


O toque de ar também está disponível no HoloLens 2. Ele foi relaxado da versão original. Quase todos os tipos de pinçações agora têm suporte, contanto que a mão esteja na vertical e mantendo ainda. Isso torna muito mais fácil para os usuários aprender e usar o gesto. Esse novo toque de ar substitui o antigo por meio da mesma API, de modo que os aplicativos existentes terão o novo comportamento automaticamente após a recompilação para o HoloLens 2.

<br>

---

### <a name="gaze-and-select-voice-command&quot;></a>Olhar e comando de voz &quot;Select&quot;
A linha de comando de voz é um dos principais métodos de interação na realidade misturada. Ele fornece um poderoso mecanismo prático para controlar o sistema. Há diferentes tipos de modelos de interação de voz:

- O comando genérico &quot;Selecionar&quot; que usa uma acionamento de clique ou confirmação como uma entrada secundária.
- Comandos de objeto (por exemplo, &quot;Fechar&quot; ou &quot;Aumentar") executam e se comprometem com uma ação como uma entrada secundária.
- Comandos globais (por exemplo, "Ir para iniciar") não exigem um destino.
- Interfaces de usuário de conversa ou entidades como a Cortana têm uma funcionalidade de linguagem natural de IA.
- Comandos de voz personalizados

Para saber mais sobre detalhes e uma lista abrangente de comandos de voz disponíveis e como usá-los, confira nossas [diretrizes de comandos de](../out-of-scope/voice-design.md) voz.

<br>

---


### <a name="gaze-and-hololens-clicker"></a>Gaze e HoloLens Clicker

:::row:::
    :::column:::
        O HoloLens Clicker é o primeiro dispositivo periférico criado especificamente para o HoloLens. Ele está incluído no HoloLens (1ª geração) Development Edition. O HoloLens Clicker permite que um usuário clique com movimento mínimo de mão e faça commit como uma entrada secundária. O HoloLens Clicker se conecta ao HoloLens (1ª geração) ou ao HoloLens 2 usando Bluetooth de Baixa Energia (BTLE).<br>
        <br>
        [Mais informações e instruções para emparelhar o dispositivo](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Imagem: HoloLens Clicker*
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>Gaze e controlador sem fio Xbox

:::row:::
    :::column:::
        O Controlador Sem Fio Xbox executa uma audição de clique como uma entrada secundária usando o botão "A". O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar e controlar o sistema. Se você quiser personalizar o controlador, use o aplicativo Acessórios Xbox para configurar o controlador sem fio Xbox.<br>
        <br>
        [Como emparelhar um controlador Xbox com seu computador](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Imagem: Controlador Sem Fio Xbox*
    :::column-end:::
        :::column:::
       ![Controle sem Fio Xbox](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>Controlador adaptável olhar e Xbox
Projetado principalmente para atender às necessidades de jogos com mobilidade limitada, o controlador adaptável do Xbox é um hub unificado para dispositivos que ajuda a tornar a realidade misturada mais acessível.

O controlador adaptável do Xbox executa um clique actuation como uma entrada secundária usando o botão ' A '. O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar e controlar o sistema. Se você quiser personalizar o controlador, use o aplicativo de acessórios do Xbox para configurar o controlador adaptável do Xbox.

![Controle Adaptável Xbox](images/xbox-adaptive-controller-devices.jpg)<br>
*Controle Adaptável Xbox*

Conecte dispositivos externos, como comutadores, botões, montagens e joysticks, para criar uma experiência de controlador personalizada que seja exclusivamente sua. As entradas de botão, Thumbstick e gatilho são controladas com dispositivos assistenciais conectados por meio de portas USB e conectores de 3,5-mm.

![Portas do Controle Adaptável Xbox](images/xbox-adaptive-controller-ports.jpg)<br>
*Portas do Controle Adaptável Xbox*

[Instruções para emparelhar o dispositivo](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Mais informações disponíveis no site do Xbox</a>

<br>

---

## <a name="composite-gestures"></a>Gestos compostos

### <a name="air-tap"></a>Fechar e abrir dedos indicador e polegar
O gesto de toque do ar (e os outros gestos abaixo) reage apenas a um toque específico. Para detectar outros toques, como menu ou compreender, seu aplicativo deve usar diretamente as interações de nível inferior descritas na seção dois principais gestos de componente acima.

### <a name="tap-and-hold"></a>Fechar e abrir dedos indicador e polegar e manter
Manter é simplesmente manter a posição do dedo para baixo no gesto de fechar e abrir dedos indicador e polegar. A combinação de toque e suspensão do ar permite várias interações mais complexas de "clicar e arrastar" quando combinadas com a movimentação do ARM, como a seleção de um objeto, em vez de ativá-lo ou interações secundárias de MouseDown, como mostrar um menu de contexto.
Deve-se ter cuidado ao criar esse gesto, pois os usuários podem estar propensos a relaxar suas posturas de mão durante qualquer gesto estendido.

### <a name="manipulation"></a>manipulação
Os gestos de manipulação podem ser usados para mover, redimensionar ou girar um holograma quando você quiser que o holograma reaja 1:1 aos movimentos da mão do usuário. Um uso para essas movimentações de 1:1 é permitir que o usuário desenhe ou pinte no mundo.
O direcionamento inicial de um gesto de manipulação deve ser feito pelo foco ou apontando. Quando o toque e a suspensão são iniciados, qualquer manipulação de objeto é tratada por movimentos de mão, o que libera o usuário para examinar enquanto manipula.

### <a name="navigation"></a>Navegação
Os gestos de navegação funcionam como um joystick virtual e podem ser usados para navegar por widgets de interface do usuário, como menus radiais. Feche e abra os dedos indicador e polegar e mantenha para iniciar o gesto e, em seguida, mova a mão dentro de um cubo 3D normalizado, centralizado em torno do pressionamento inicial. Você pode mover sua mão ao longo do eixo X, Y ou Z de um valor de-1 para 1, sendo que 0 é o ponto de partida.
A navegação pode ser usada para criar gestos de rolagem ou zoom contínuo baseados em velocidade, semelhante à rolagem de uma interface do usuário 2D com um clique no botão do meio do mouse e, em seguida, a movimentação do mouse para cima e para baixo.

A navegação com Rails refere-se à capacidade de reconhecer movimentos em determinado eixo até que um determinado limite seja atingido nesse eixo. Isso só é útil quando a movimentação em mais de um eixo é habilitada em um aplicativo pelo desenvolvedor, como se um aplicativo estiver configurado para reconhecer gestos de navegação no eixo X, Y, mas também especificado eixo X com trilhos. Nesse caso, o sistema reconhecerá os movimentos de mão no eixo X, desde que permaneçam dentro de um trilho imaginário (guia) no eixo X, se o movimento da mão também ocorrer no eixo Y.

Em aplicativos 2D, os usuários podem usar gestos de navegação vertical para rolagem, zoom ou operações de arrastar dentro do aplicativo. Isso injeta toques de dedo virtuais no aplicativo para simular gestos de toque do mesmo tipo. Os usuários podem selecionar quais dessas ações ocorrem ao fazer a agregação entre as ferramentas na barra acima do aplicativo, selecionando o botão ou dizendo "<Ferramenta de Rolagem/Arrastar/Ampliar>".

[Mais informações sobre gestos compostos](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>Reconhecedores de gestos

Um benefício de usar o reconhecimento de gestos é que você pode configurar um reconhecedor de gestos somente para os gestos que o holograma atualmente direcionado pode aceitar. A plataforma só faz a desambiguidade conforme necessário para distinguir esses gestos com suporte específicos. Dessa forma, um holograma que dá suporte apenas ao toque de ar pode aceitar qualquer período de tempo entre a pressão e a liberação, enquanto um holograma que dá suporte ao toque e à espera pode promover o toque para uma espera após o limite de tempo de espera.

## <a name="hand-recognition"></a>Reconhecimento de mão
O HoloLens reconhece gestos de mão acompanhando a posição de uma ou das duas mãos visíveis para o dispositivo. O HoloLens vê as mãos quando elas estão no estado pronto (parte posterior da mão voltada para você com o dedo indicador para cima) ou no estado pressionado (parte posterior da mão voltada para você com o dedo indicador para baixo). Quando as mãos estão em outras poses, o HoloLens as ignora.
Para cada mão detectada pelo HoloLens, você pode acessar sua posição sem orientação e seu estado pressionado. Conforme a mão se aproxima da borda do quadro de gesto, você também recebe um vetor de direção, que você pode mostrar ao usuário para que ele saiba como mover a mão para retorná-la ao local em que o HoloLens possa vê-la.

## <a name="gesture-frame"></a>Quadro de gesto
Para gestos no HoloLens, a mão deve estar dentro de um quadro de gesto, em um intervalo que as câmeras de gestos possam ver adequadamente, desde o nariz até a cabeça e entre os olhos. Os usuários precisam ser treinados nessa área de reconhecimento para o sucesso da ação e para seu próprio conforto. Inicialmente, muitos usuários pressupom que o quadro de gestos deve estar dentro de sua exibição por meio do HoloLens e manterão seus braços incomparáveis para interagir. Ao usar o HoloLens Clicker, não é necessário que as mãos sejam dentro do quadro de gestos.

Para gestos contínuos em particular, há algum risco de os usuários moverem as mãos para fora do quadro de gestos durante o gesto ao mover um objeto holográfico, por exemplo, e perderem o resultado pretendido.

Há três coisas que você deve considerar:

- Educação do usuário na existência do quadro gesto e limites aproximados. Isso é ensinado durante a configuração do HoloLens.

- Notificar os usuários quando seus gestos estiverem se aproximando ou dividindo os limites de quadro de gesto dentro de um aplicativo no grau de um gesto perdido levar a resultados indesejados. A pesquisa mostrou as principais qualidades desse sistema de notificação. O Shell do HoloLens fornece um bom exemplo desse tipo de notificação – Visual, no cursor central, indicando a direção na qual o cruzamento de limites está ocorrendo.

- As consequências de sair dos limites do quadro do gesto deverão ser minimizadas. Em geral, isso significa que o resultado de um gesto deve ser interrompido no limite e não revertido. Por exemplo, se um usuário estiver movendo algum objeto Holographic em uma sala, a movimentação deverá parar quando o quadro do gesto for violado e não retornar ao ponto de partida. O usuário pode enfrentar alguma frustração, mas pode entender mais rapidamente os limites e não precisa reiniciar suas ações pretendidas todas as vezes.



## <a name="see-also"></a>Confira também
* [Interação ocular](eye-gaze-interaction.md)
* [Acompanhamento ocular no HoloLens 2](eye-tracking.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Mãos – Manipulação direta](direct-manipulation.md)
* [Mãos – Gestos](gaze-and-commit.md#composite-gestures)
* [Mãos – Apontar e confirmar](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)