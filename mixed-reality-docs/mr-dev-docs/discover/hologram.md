---
title: O que é um holograma?
description: O HoloLens permite exibir e interagir com hologramas tridimensionais, objetos compostos de luz e som que aparecem no mundo todo.
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, hologramas, design, interação, headset de realidade misturada, headset da realidade mista do Windows, o que é a realidade aumentada
ms.openlocfilehash: b390910fcece8e6263d19f52c80b784efb2561f6
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757554"
---
# <a name="what-is-a-hologram"></a>O que é um holograma?

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


O HoloLens permite criar **hologramas**, que são objetos compostos de luz e som que aparecem no mundo inteiro, como objetos reais. Os hologramas respondem aos seus [olhar](../design/gaze-and-commit.md), [gestos](../design/gaze-and-commit.md#composite-gestures)e [comandos de voz](../design/voice-input.md). Eles podem até mesmo interagir com [superfícies reais](../design/spatial-mapping.md) em todo o mundo. Com os hologramas, você pode criar objetos digitais que fazem parte do seu mundo.

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
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
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

Os hologramas que o HoloLens [renderiza](../develop/platform-capabilities-and-apis/rendering.md) aparecem no quadro Holographic diretamente na frente dos olhos do usuário. Os hologramas adicionam luz ao seu mundo, o que significa que você vê a luz da tela e a luz de seus arredores. O HoloLens não remove a luz dos seus olhos, portanto, os hologramas não podem ser renderizados com a cor preta. Em vez disso, o conteúdo preto aparece como transparente.

Os hologramas podem ter várias aparências e comportamentos diferentes. Alguns são realísticos e sólidos, e outros são animados e o Ethereal. Você pode usar hologramas para realçar recursos em seus arredores ou usá-los como elementos na interface do usuário do aplicativo.

![Mãos manipulando um holograma](images/hologram-hands-940px.jpg)

Os hologramas também podem fazer [sons](../design/spatial-sound.md), que parecerão vir de um local específico em seus arredores. No HoloLens, o som vem de dois alto-falantes que estão localizados diretamente acima de seus ouvidos, sem cobri-los. Semelhante às telas, os alto-falantes são aditivos, apresentando novos sons sem bloquear os sons do seu ambiente.

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Um holograma pode ser colocado no mundo ou em uma marca junto com você

Quando você tem um local específico para um holograma, você pode [colocá](../design/coordinate-systems.md) -lo precisamente nesse ponto do mundo. À medida que você se movimenta, o holograma parece estável com base no mundo em relação a você. Se você usar uma [âncora espacial](../design/coordinate-systems.md#spatial-anchors) para fixar o objeto, o sistema poderá até mesmo se lembrar de onde você o deixou quando voltar mais tarde.

![Dois homens usando o layout do Microsoft Dynamics 365 em um espaço de varejo](images/HLS19_retailLayoutHologram_001-940px.jpg)

Em vez disso, alguns hologramas seguem o usuário, posicionando-se com base no usuário, independentemente de onde eles se movimentam. Você pode até mesmo optar por trazer um holograma com você por um tempo e colocá-lo na parede quando chegar a outra sala.

**Práticas recomendadas**
* Alguns cenários podem exigir que os hologramas permaneçam facilmente detectáveis ou visíveis em toda a experiência. Há duas abordagens de alto nível para esse tipo de posicionamento. Vamos chamá-los de **"display-Locked"** e **"Body-Locked"**.
   * O conteúdo bloqueado de exibição é posicionado "bloqueado" na tela do dispositivo. Esse tipo de conteúdo é complicado por vários motivos, incluindo uma sensação não natural de "clingyness" que torna muitos usuários frustrados e querendo "agite-los". Em geral, muitos designers acharam melhor evitar conteúdo de bloqueio de exibição.
   * A abordagem de corpo bloqueado é muito mais forgivable. O bloqueio de corpo é quando você faz o compartilhamento de um holograma para o corpo do usuário ou vetor olhar no espaço 3D. Muitas experiências adotaram um comportamento de bloqueio de corpo onde o holograma "segue" os usuários olhar, o que permite ao usuário girar seu corpo e percorrer o espaço sem perder o holograma. Incorporar um atraso ajuda o movimento do holograma a se sentir mais natural. Por exemplo, alguma interface do usuário principal do sistema operacional Windows Holographic usa uma variação no bloqueio de corpo que segue o olhar do usuário com um atraso de AdaBoost e elástico, enquanto o usuário transforma sua cabeça.
* Coloque o holograma em uma distância de exibição confortável, normalmente, cerca de 1-2 metros longe do início.
* Forneça uma quantidade de descompasso para os elementos que devem estar continuamente no quadro Holographic ou considere animar seu conteúdo para um lado da exibição quando o usuário alterar seu ponto de vista.

**Coloque os hologramas na zona ideal-entre 1,25 m e 5 m**

Dois medidores são os mais ideais, e a experiência diminuirá quanto mais perto você chegar do medidor 1. Às distâncias próximas de 1 medidor, os hologramas que se movem regularmente em profundidade têm maior probabilidade de serem problemáticos do que os hologramas fixos. Considere recortar ou desbotar seu conteúdo de forma elegante quando ele ficar muito próximo, de modo que você não o desconectará do usuário em uma experiência inesperada.

![Distância ideal para colocar os hologramas do usuário.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Um holograma interage com você e seu mundo

Os hologramas não são apenas sobre luz e som; Eles também são uma parte ativa do seu mundo. Olhar com um holograma e um gesto com sua mão, e um holograma pode começar a acompanhá-lo. Dê um comando de voz para um holograma e ele pode responder.

![Grupo de funcionários de utilitário do governo usando o Microsoft HoloLens 2 para colaborar em um projeto de desenvolvimento de farm de vento](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

Os hologramas permitem interações pessoais que não são possíveis em outro lugar. Como o HoloLens sabe onde ele está no mundo, um caractere Holographic pode examiná-lo diretamente nos olhos à medida que você percorre a sala.

Um holograma também pode interagir com seus arredores. Por exemplo, você pode inserir uma bola saltando Holographic acima de uma tabela. Em seguida, com um [toque de ar](../design/gaze-and-commit.md#composite-gestures), observe o salto de bola e faça o som quando ele atingir a tabela.

Os hologramas também podem ser obstruídodos por objetos do mundo real. Por exemplo, um caractere Holographic pode percorrer uma porta e atrás de uma parede, fora de sua visão.

**Dicas para integrar hologramas e o mundo real**
* Alinhar às regras do Gravitational torna os hologramas mais fáceis de se relacionar e mais verossímeis. por exemplo: Coloque um cachorro Holographic no chão & um vaso na tabela em vez de tê-los flutuantes no espaço.
* Muitos designers descobriram que podem integrar hologramas mais verossímeis criando uma "sombra negativa" na superfície em que o holograma está sentado. Eles fazem isso criando um brilho suave no chão ao lado do holograma e subtraindo a "sombra" do brilho. O brilho suave se integra com a luz do mundo real, que usa a sombra para aterrar o holograma no ambiente.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a>Um holograma é qualquer coisa <br>Você pode sonho<br>
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

Se estiver seguindo a [jornada de descoberta](get-started-with-mr.md) que apresentamos, você estará no meio da exploração dos fundamentos da Realidade Misturada. A partir daqui, você pode continuar para o próximo tópico básico: 

> [!div class="nextstepaction"]
> [Expanda seu processo de design](case-study-expanding-the-design-process-for-mixed-reality.md)

