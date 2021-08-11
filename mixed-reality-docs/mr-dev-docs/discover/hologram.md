---
title: O que é um holograma?
description: HoloLens permite exibir e interagir com hologramas tridimensionais, objetos compostos de luz e som que aparecem no mundo todo.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, hologramas, design, interação, headset de realidade misturada, headset de realidade mista do Windows, o que é a realidade aumentada
ms.openlocfilehash: e028fe6180bded26263fa47feb5acefc94570222e43f10fe85db5adf90307844
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202094"
---
# <a name="what-is-a-hologram"></a>O que é um holograma?

HoloLens permite exibir **hologramas**, que são objetos compostos de luz e som que aparecem no mundo inteiro, como objetos reais. Hologramas pode responder aos seus [olhar](../design/gaze-and-commit.md), [gestos](../design/gaze-and-commit.md#composite-gestures)e [comandos de voz](../design/voice-input.md). Eles podem até mesmo interagir com [superfícies reais](../design/spatial-mapping.md) em todo o mundo. Hologramas são objetos digitais que fazem parte do seu mundo.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
        <td><strong>Recurso</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Hologramas</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a>Um holograma é formado de luz e som

### <a name="light"></a>Claro

os hologramas que HoloLens [renderizações](../develop/platform-capabilities-and-apis/rendering.md) aparecem no quadro holographic diretamente na frente dos olhos dos usuários. Hologramas adicionar luz ao seu mundo, o que significa que você vê a luz da tela e a luz do seu mundo ao redor. como HoloLens usa uma exibição aditiva que adiciona light, a cor preta será transparent. 

Hologramas pode ter comportamentos e aparências muito diferentes. Alguns são realísticos e sólidos, e outros são animados e o Ethereal. Você pode usar hologramas para realçar recursos em seu ambiente ou usá-los como elementos na interface do usuário do aplicativo.

![Mãos manipulando um holograma](images/hologram-hands-940px.jpg)

### <a name="sound"></a>Som

Hologramas também pode produzir [sons](../design/spatial-sound.md), que parecem vir de um local específico em seu ambiente. no HoloLens, o som vem de dois alto-falantes que estão localizados diretamente acima de seus ouvidos. O mesmo que o Holographic é exibido, os alto-falantes são aditivos, apresentando novos sons sem bloquear os sons do seu ambiente.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Um holograma pode ser colocado no mundo ou em uma marca junto com você

Quando você tem um local fixo para um holograma, você pode [colocá](../design/coordinate-systems.md) -lo precisamente nesse ponto do mundo. À medida que você percorre, o holograma aparece de forma estática com base no mundo, assim como um objeto físico. Se você usar uma [âncora espacial](../design/coordinate-systems.md#spatial-anchors) para fixar o objeto, o sistema poderá até mesmo se lembrar de onde você o deixou quando voltar mais tarde.

![Dois homens usando o layout do Microsoft Dynamics 365 em um espaço de varejo](images/HLS19_retailLayoutHologram_001-940px.jpg)

Em vez disso, alguns hologramas seguem o usuário. Elas se posicionam com base no usuário. Você pode optar por trazer um holograma para você e colocá-lo na parede quando chegar a outra sala.

**Práticas recomendadas**

* Alguns cenários exigem que os hologramas permaneçam facilmente detectáveis ou visíveis em toda a experiência. Há duas abordagens de alto nível para esse tipo de posicionamento. Vamos chamá-los **de exibição, bloqueados** e de **corpo bloqueado**.
   * **Exibição-** o conteúdo bloqueado está bloqueado para o dispositivo de vídeo. Esse tipo de conteúdo é complicado por vários motivos, incluindo uma sensação não natural de "clingyness" que torna muitos usuários frustrados e querendo "agite-los". Em geral, os designers acharam melhor evitar conteúdo de bloqueio de exibição.
   * O conteúdo **bloqueado pelo corpo** pode ser muito mais tolerante. O bloqueio de corpo é quando você faz o compartilhamento de um holograma para o corpo do usuário ou vetor olhar no espaço 3D. Muitas experiências adotaram um comportamento de bloqueio de corpo em que o holograma segue o olhar do usuário, o que permite ao usuário girar seu corpo e percorrer o espaço sem perder o holograma. Incorporar um atraso ajuda os movimentos do holograma a se sentirem mais naturais. por exemplo, alguma interface do usuário principal do Windows sistema operacional Holographic usa uma variação no bloqueio de corpo que segue o olhar do usuário com um atraso de adaboost e elástico, enquanto o usuário transforma sua cabeça.
* Coloque o holograma em uma distância de exibição confortável, normalmente, cerca de 1-2 metros longe do início.
* Permita que os elementos sejam descompassos se eles precisarem ser continuamente no quadro Holographic, ou considere mover o conteúdo para um lado da exibição quando o usuário alterar seu ponto de vista. Para obter mais informações, consulte a [mensagem e a marca](../design/billboarding-and-tag-along.md) Artilce.

**Coloque os hologramas na zona ideal-entre 1,25 m e 5 m**

Dois medidores é a distância de exibição mais ideal. A experiência começará a diminuir à medida que você ficar mais próximo que 1 medidor. Em distâncias menores que 1 medidor, os hologramas que se movem regularmente em profundidade têm maior probabilidade de serem problemáticos do que os hologramas fixos. Considere recortar ou desbotar seu conteúdo quando ele ficar muito próximo e, portanto, você não desconectará o usuário em uma experiência de exibição desagradável.

![Distância ideal para colocar os hologramas do usuário.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Um holograma interage com você e seu mundo

Hologramas não são apenas sobre luz e som; Eles também são uma parte ativa do seu mundo. Olhar com um holograma e um gesto com sua mão, e um holograma pode começar a acompanhá-lo. Dê um comando de voz e o holograma pode responder.

![grupo de funcionários de utilitário do governo usando o Microsoft HoloLens 2 para colaborar em um projeto de desenvolvimento de farm de ventos](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

Hologramas habilitar interações pessoais que não são possíveis em outro lugar. como o HoloLens sabe onde está no mundo, um caractere holographic pode olhar diretamente nos olhos e iniciar uma conversa com você.

Um holograma também pode interagir com seus arredores. Por exemplo, você pode inserir uma bola saltando Holographic acima de uma tabela. Em seguida, com um [toque de ar](../design/gaze-and-commit.md#composite-gestures), observe o salto de bola e faça o som à medida que ele atinge a tabela.

Hologramas também pode ser obstruído por objetos do mundo real. Por exemplo, um caractere Holographic pode percorrer uma porta e atrás de uma parede, fora de sua visão.

**Dicas para integrar hologramas e o mundo real**

* Alinhar às regras do Gravitational torna os hologramas mais fáceis de se relacionar e mais verossímeis. Por exemplo: Coloque um cachorro Holographic no chão & um vaso na tabela em vez de tê-los flutuantes no espaço.
* Muitos designers descobriram que podem integrar hologramas mais verossímeis criando uma "sombra negativa" na superfície em que o holograma está sentado. Eles fazem isso criando um brilho suave no chão ao lado do holograma e subtraindo a "sombra" do brilho. O brilho suave se integra com a luz do mundo real. A sombra é usada para aterrar o holograma no ambiente.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a>Um holograma é o que <br>Você pode sonho<br>
        Como desenvolvedor de Holographic, você tem a capacidade de dividir sua criatividade em telas 2D e em seu mundo.<br><br>
        O que *você* vai criar?
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Holographic imaginário mundial na sala de vida](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>Próximo ponto de verificação de descoberta

Você está na [jornada de descoberta](get-started-with-mr.md) que apresentamos e explorando as noções básicas da realidade misturada. Desse ponto, você poderá prosseguir para o próximo tópico básico: 

> [!div class="nextstepaction"]
> [Expanda seu processo de design](case-study-expanding-the-design-process-for-mixed-reality.md)