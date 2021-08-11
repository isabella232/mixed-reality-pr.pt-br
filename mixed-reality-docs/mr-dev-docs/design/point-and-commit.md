---
title: Apontar e confirmar com as mãos
description: Conheça as noções básicas do modelo de entrada de apontar e confirmar para obter suporte a gestos em aplicativos de realidade misturada.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, interação, design, HoloLens, mãos, longe, apontar e confirmar, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, HoloLens, raios de mão, manipulação de objeto, MRTK, Kit de Ferramentas de Realidade Misturada, DoF
ms.openlocfilehash: 7cf3aa3dd77776fce00d45b0ec086bf1d2e8c06241fd4525276783c2abfd51d9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115194506"
---
# <a name="point-and-commit-with-hands"></a>Apontar e confirmar com as mãos

![Cursores](images/UX_Hero_HandRay.jpg)

Apontar e confirmar com as mãos é um modelo de entrada que permite aos usuários direcionar, selecionar e manipular o conteúdo 2D e 3D fora de alcance. Essa técnica de interação "à distância" é exclusiva da Realidade Misturada, porque não é uma forma natural de interação humana com o mundo real. Por exemplo, no filme de super-heróis, *X-Men*, o personagem [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) pode manipular objetos distantes com as mãos. Isso não é algo que os humanos podem fazer na realidade. No RA (HoloLens) e na MR (Realidade Misturada), equipamos os usuários com esse poder mágico para eliminar a restrição física do mundo real. É uma experiência holográfica divertida e torna as interações do usuário mais eficientes e eficazes.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>Modelo de entrada</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></td>
     <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
</tr>
<tr>
     <td>Apontar e confirmar com as mãos</td>
     <td>❌ Sem suporte</td>
     <td>✔️ Recomendado</td>
     <td>✔️ Recomendado</td>
</tr>
</table>


_"Apontar e confirmar com as mãos"_ é um dos novos recursos que usa o novo sistema articulado de acompanhamento com as mãos. Esse modelo de entrada também é o modelo de entrada primário em headsets imersivos com o uso de controladores de movimentos.

<br>

---

## <a name="hand-rays"></a>Raios de mão

No HoloLens 2, criamos um raio de mão que é disparado do centro da palma da mão do usuário. Este raio é tratado como uma extensão da mão. Um cursor em forma de rosca é anexado ao final do raio para indicar o local onde o raio cruza com um objeto-alvo. O objeto sobre o cursor pode receber comandos gestuais da mão.

Esse comando gestual básico é disparado com o polegar e o dedo indicador para executar uma ação de fechar e abrir os dedos indicador e polegar. Usando o raio de mão para apontar e a ação de fechar e abrir os dedos indicador e polegar para confirmar, os usuários podem ativar um botão ou um hiperlink. Com gestos compostos mais complexos, os usuários podem navegar pelo conteúdo da Web e manipular objetos 3D à distância. O design visual do raio de mão também deve reagir com esses estados de apontar e confirmar, conforme descrito e mostrado abaixo: 

:::row:::
    :::column:::
        ![apontar com raios de mão](images/hand-rays-pointing.jpg)<br>
        **Estado de apontar**<br>
        Ao *apontar*, o raio é mostrado como uma linha tracejada e o cursor assume a forma de uma rosca.
    :::column-end:::
    :::column:::
        ![confirmar com raios de mão](images/hand-rays-commit.jpg)<br>
        **Estado de confirmação**<br>
        Ao *confirmar*, o raio se transforma em uma linha sólida e o cursor se reduz a um ponto.
    :::column-end:::
:::row-end:::

<br>

---

## <a name="transition-between-near-and-far"></a>Transição entre próximo e distante

Em vez de usar gestos específicos como "apontar com o dedo indicador" para direcionar o raio, projetamos o raio de modo que ele saia da palma da mão dos usuários. Dessa forma, lançamos e reservamos os cinco dedos para gestos mais manipulativos, como apertar e segurar. Com esse design, criamos um só modelo mental – o mesmo conjunto de gestos de mão é usado para uma interação próxima e distante. Você pode usar o mesmo gesto de captura para manipular objetos em distâncias diferentes. A invocação dos raios é automática e baseada na proximidade, conforme demonstrado a seguir:

:::row:::
    :::column:::
        ![Manipulação próxima](images/transition-near-manipulation.jpg)<br>
        **Manipulação próxima**<br>
        Quando um objeto está dentro da distância de alcance do braço (aproximadamente 50 cm), os raios são desativados automaticamente, incentivando a interação próxima.
    :::column-end:::
    :::column:::
        ![Manipulação distante](images/transition-far-manipulation.jpg)<br>
        **Manipulação distante**<br>
        Quando o objeto está mais distante do que 50 cm, os raios são ativados. A transição deve ser simples e direta.
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>Interação do slate 2D

Um slate 2D é um contêiner holográfico que hospeda o conteúdo do aplicativo 2D, assim como um navegador da Web. O conceito de design da interação distante com um slate 2D é usar os raios de mão para focalizar e fechar e abrir os dedos indicador e polegar para selecionar. Após focalizar com um raio de mão, os usuários podem fechar e abrir os dedos indicador e polegar para disparar um hiperlink ou um botão. Eles podem usar uma mão para "fechar e abrir os dedos indicador e polegar" para rolar o conteúdo de um slate para cima e para baixo. O movimento relativo do uso das duas mãos para fechar e abrir os dedos indicador e polegar e arrastar pode aumentar e diminuir o zoom do conteúdo do slate.

Focalizar o raio de mão nos cantos e bordas revela a funcionalidade de manipulação mais próxima. Por meio das funcionalidades de manipulação do tipo "segurar e arrastar", os usuários podem realizar o dimensionamento uniforme utilizando as funcionalidades de canto e refluir o slate por meio das funcionalidades de borda. Ao segurar e arrastar a barra holográfica na parte superior do slate 2D, os usuários podem mover todo o slate.

:::row:::
    :::column:::
       ![Clique de interação do slate 2D](images/2d-slate-interaction-click.jpg)<br>
       **Clicar**<br>
    :::column-end:::
    :::column:::
       ![Rolagem de interação do slate 2D](images/2d-slate-interaction-scroll.jpg)<br>
        **Rolar**<br>
    :::column-end:::
    :::column:::
       ![Zoom de interação do slate 2D](images/2d-slate-interaction-zoom.jpg)<br>
       **Aplicar zoom**<br>
    :::column-end:::
:::row-end:::

<br>

**Para manipular o slate 2D**<br>

* Os usuários apontam o raio de mão para os cantos ou bordas para revelar a funcionalidade de manipulação mais próxima. 
* Aplicando um gesto de manipulação na funcionalidade, os usuários podem realizar o dimensionamento uniforme usando a funcionalidade de canto e refluir o slate por meio da funcionalidade de borda. 
* Aplicando um gesto de manipulação na barra holográfica na parte superior do slate 2D, os usuários podem mover todo o slate.<br>

<br>

---

## <a name="3d-object-manipulation"></a>Manipulação de objetos 3D

Na manipulação direta, há duas maneiras de os usuários manipularem objetos 3D: a manipulação baseada em funcionalidade e a manipulação não baseada em funcionalidade. No modelo de apontar e confirmar, os usuários podem realizar exatamente as mesmas tarefas por meio dos raios de mão. Nenhum aprendizado extra é necessário.<br>

### <a name="affordance-based-manipulation"></a>Manipulação baseada em funcionalidade

Os usuários podem usar os raios de mão para apontar e revelar a caixa delimitadora e as funcionalidades de manipulação. Os usuários podem aplicar o gesto de manipulação na caixa delimitadora para mover todo o objeto, nas funcionalidades de borda para girá-lo e nas funcionalidades de canto para dimensioná-lo de maneira uniforme. <br>

:::row:::
    :::column:::
       ![Movimento a distância da manipulação de objetos 3D](images/3d-object-manipulation-far-move.jpg)<br>
       **Mover**<br>
    :::column-end:::
    :::column:::
       ![Rotação a distância da manipulação de objetos 3D](images/3d-object-manipulation-far-rotate.jpg)<br>
        **Girar**<br>
    :::column-end:::
    :::column:::
       ![Escala a distância da manipulação de objetos 3D](images/3d-object-manipulation-far-scale.jpg)<br>
       **Escala**<br>
    :::column-end:::
:::row-end:::

### <a name="non-affordance-based-manipulation"></a>Manipulação não baseada em funcionalidade

Os usuários apontam com os raios de mão para revelar a caixa delimitadora e aplicam gestos de manipulação diretamente nela. Com uma mão, a translação e a rotação do objeto estão associadas ao movimento e à orientação da mão. Com as duas mãos, os usuários podem transladar, dimensionar e girar o objeto de acordo com os movimentos relativos das duas mãos.<br>

<br>

---

## <a name="instinctual-gestures"></a>Gestos instintuais

O conceito de gestos instintuais para apontar e confirmar é semelhante ao da [manipulação direta com as mãos](direct-manipulation.md). Os gestos feitos pelos usuários em um objeto 3D são orientados pelo design das funcionalidades da interface do usuário. Por exemplo, um ponto de controle pequeno pode motivar os usuários a apertar com o polegar e o dedo indicador, ao passo que, para segurar um objeto maior, os usuários podem preferir usar os cinco dedos.

:::row:::
    :::column:::
       ![gestos instintivos para objeto pequeno](images/instinctual-gestures-far-smallobject.jpg)<br>
       **Objeto pequeno**<br>
    :::column-end:::
    :::column:::
       ![gestos instintivos para objeto médio](images/instinctual-gestures-far-mediumobject.jpg)<br>
        **Objeto médio**<br>
    :::column-end:::
    :::column:::
       ![gestos instintivos para objeto grande](images/instinctual-gestures-far-largeobject.jpg)<br>
       **Objeto grande**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Design simétrico entre os controladores de mão e DoF 6 

O conceito de apontar e confirmar para interação à distância foi criado e definido para o MRP (Portal de Realidade Misturada). Nesse cenário, um usuário usa um headset imersivo e interage com objetos 3D por meio de controladores de movimentos. Os controladores de movimento disparam raios para apontar e manipular objetos distantes. Existem botões nos controladores para confirmar diferentes ações. Aplicamos o modelo de interação de raios e os anexamos às duas mãos. Com esse design simétrico, os usuários que estão familiarizados com o MRP não precisarão aprender a usar outro modelo de interação para apontar e manipular objetos à distância quando usarem o HoloLens 2 e vice-versa.    

:::row:::
    :::column:::
        ![design simétrico para raios com controladores](images/symmetric-design-for-rays-controllers.jpg)<br>
        **Raios do controlador**<br>
    :::column-end:::
    :::column:::
        ![design simétrico para raios com as mãos](images/symmetric-design-for-rays-hands.jpg)<br>
        **Raios de mão**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a>Raio de mão no MRTK (Kit de Ferramentas de Realidade Misturada) para o Unity

Por padrão, o MRTK fornece um prefab de raio de mão ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) que tem o mesmo estado visual que o raio de mão do sistema do shell. Ele é atribuído no perfil de Entrada do MRTK, em Ponteiros. Em um headset imersivo, os mesmos raios são usados para os controladores de movimento.

* [MRTK – Perfil de ponteiro](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [MRTK – Sistema de entrada](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [MRTK – Ponteiros](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a>Consulte também

* [Manipulação direta com as mãos](direct-manipulation.md)
* [Focar e confirmar](gaze-and-commit.md)
* [Mãos – Manipulação direta](direct-manipulation.md)
* [Mãos – Gestos](gaze-and-commit.md#composite-gestures)
* [Interações instinctuais](interaction-fundamentals.md)