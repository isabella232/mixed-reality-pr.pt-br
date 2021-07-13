---
title: O que é um holograma?
description: HoloLens permite exibir e interagir com hologramas tridimensionais, objetos feitos de luz e som que aparecem no mundo ao seu redor.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, hologramas, design, interação, headset de realidade misturada, headset de realidade misturada do Windows, o que é realidade aumentada
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634327"
---
# <a name="what-is-a-hologram"></a>O que é um holograma?

HoloLens permite exibir **hologramas**, que são objetos feitos de luz e som que aparecem no mundo ao seu redor, como objetos reais. Hologramas pode responder ao seu [olhar,](../design/gaze-and-commit.md) [gestos](../design/gaze-and-commit.md#composite-gestures)e comandos [de voz.](../design/voice-input.md) Eles podem até mesmo interagir com [superfícies do mundo real](../design/spatial-mapping.md) ao seu redor. Hologramas são objetos digitais que fazem parte do seu mundo.

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

## <a name="a-hologram-is-made-of-light-and-sound"></a>Um holograma é feito de luz e som

### <a name="light"></a>Claro

Os hologramas que HoloLens [renderiza](../develop/platform-capabilities-and-apis/rendering.md) aparecem no quadro holográfico diretamente na frente dos olhos dos usuários. Hologramas adicione luz ao seu mundo, o que significa que você vê a luz da exibição e a luz do seu mundo ao redor. Como HoloLens usa uma exibição aditiva que adiciona luz, a cor preta será renderizada de forma transparente. 

Hologramas pode ter aparências e comportamentos muito diferentes. Alguns são realistas e sólidos e outros são desenhista e ethereal. Você pode usar hologramas para realçar recursos em seu ambiente ou usá-los como elementos na interface do usuário do aplicativo.

![Manipulação de mãos de um holograma](images/hologram-hands-940px.jpg)

### <a name="sound"></a>Som

Hologramas também pode produzir [sons](../design/spatial-sound.md), que parecem vir de um local específico em seu ambiente. No HoloLens, o som vem de dois alto-falantes localizados diretamente acima de seus olhos. Da mesma forma que as exibições holográficas, os alto-falantes são aditivos, introduzindo novos sons sem bloquear os sons do seu ambiente.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Um holograma pode ser colocado no mundo ou marcar com você

Quando você tem um local fixo para um holograma, pode [colocar](../design/coordinate-systems.md) exatamente nesse ponto do mundo. À medida que você anda, o holograma aparece estacionário com base no mundo ao seu redor, assim como um objeto físico. Se você usar uma [âncora espacial para](../design/coordinate-systems.md#spatial-anchors) fixar o objeto, o sistema poderá até mesmo se lembrar de onde você o deixou quando voltar mais tarde.

![Dois homens usando o Layout do Microsoft Dynamics 365 em um espaço de varejo](images/HLS19_retailLayoutHologram_001-940px.jpg)

Em vez disso, alguns hologramas seguem o usuário. Eles se posicionam com base no usuário. Você pode optar por trazer um holograma com você e, em seguida, coloque-o na parede quando chegar a outra sala.

**Práticas recomendadas**

* Alguns cenários exigem que os hologramas permaneçam facilmente descobertos ou visíveis durante toda a experiência. Há duas abordagens de alto nível para esse tipo de posicionamento. Vamos chamá-los **de bloqueados por exibição** **e bloqueados pelo corpo.**
   * **O conteúdo bloqueado para** exibição é bloqueado no dispositivo de exibição. Esse tipo de conteúdo é complicado por vários motivos, incluindo uma sensação anormal de "desariedade" que deixa muitos usuários frustrados e desejando "abalá-lo". Em geral, os designers descobriram melhor evitar o conteúdo de bloqueio de exibição.
   * **O conteúdo bloqueado pelo** corpo pode ser muito mais tolerante. O bloqueio do corpo é quando você insera um holograma no corpo ou vetor de olhar do usuário no espaço 3D. Muitas experiências adotaram um comportamento de bloqueio do corpo em que o holograma segue o olhar do usuário, o que permite que o usuário gire seu corpo e se mova pelo espaço sem perder o holograma. Incorporar um atraso ajuda os movimentos do holograma a se sentir mais natural. Por exemplo, algumas interfaces do usuário principais do sistema operacional holográfico do Windows usam uma variação no bloqueio de corpo que segue o olhar do usuário com um atraso elástico e elástico enquanto o usuário gira a cabeça.
* Coloque o holograma a uma distância de exibição confortável normalmente a cerca de 1 a 2 metros da cabeça.
* Permitir que os elementos se desmigam se eles devem estar continuamente no quadro holográfico ou considere mover o conteúdo para um lado da exibição quando o usuário altera seu ponto de vista. Para obter mais informações, consulte [a artilce de](../design/billboarding-and-tag-along.md) marcação e de marcação.

**Colocar hologramas na zona ideal – entre 1,25 m e 5 m**

Dois metros é a distância de exibição mais ideal. A experiência começará a ser degradada à medida que você se aproximar de 1 medidor. A distâncias menores que 1 medidor, hologramas que se movem regularmente em profundidade têm maior probabilidade de serem problemáticos do que hologramas estacionários. Considere cortar ou esvasar normalmente seu conteúdo quando ele ficar muito próximo, para que você não agrade o usuário em uma experiência de exibição desagrade.

![Distância ideal para colocar hologramas do usuário.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Um holograma interage com você e seu mundo

Hologramas não são apenas sobre luz e som; eles também são uma parte ativa do seu mundo. O olhar para um holograma e um gesto com a mão, e um holograma pode começar a seguir você. Dê um comando de voz e o holograma poderá responder.

![Grupo de funcionários públicos que usam Microsoft HoloLens 2 para colaborar em um projeto de desenvolvimento de parques eólicas](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

Hologramas habilitar interações pessoais que não são possíveis em outro lugar. Como o HoloLens sabe onde ele está no mundo, um caractere holográfico pode olhar para você diretamente nos olhos e iniciar uma conversa com você.

Um holograma também pode interagir com seu ambiente. Por exemplo, você pode colocar uma bola de salto holográfico acima de uma tabela. Em seguida, com um [toque de ar,](../design/gaze-and-commit.md#composite-gestures)observe a bola quicar e fazer som enquanto ela atinge a tabela.

Hologramas também podem ser ocluídos por objetos do mundo real. Por exemplo, um caractere holográfico pode passar por uma porta e atrás de uma parede, fora de sua vista.

**Dicas para integrar hologramas e o mundo real**

* Alinhar-se às regras de reação torna os hologramas mais fáceis de se relacionar e mais fáceis de se relacionar. Por exemplo: coloque um cachorro holográfico no chão & um cão na tabela em vez de fazer com que eles fluam no espaço.
* Muitos designers descobriram que podem integrar hologramas mais compreensíveis criando uma "sombra negativa" na superfície em que o holograma está. Eles fazem isso criando um brilho suave no chão ao redor do holograma e subtraindo a "sombra" do brilho. O brilho suave se integra à luz do mundo real. A sombra é usada para basear o holograma no ambiente.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a>Um holograma é o que <br>você pode se desemocar<br>
        Como desenvolvedor holográfico, você tem o poder de quebrar sua criatividade das telas 2D e do mundo ao seu redor.<br><br>
        O que *você criará?*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Mundo imaginário holográfico na sala de estar](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>Próximo ponto de verificação de descoberta

Você está no percurso [de descoberta](get-started-with-mr.md) que lançamos e explora os conceitos básicos da Realidade Misturada. Desse ponto, você poderá prosseguir para o próximo tópico básico: 

> [!div class="nextstepaction"]
> [Expanda seu processo de design](case-study-expanding-the-design-process-for-mixed-reality.md)