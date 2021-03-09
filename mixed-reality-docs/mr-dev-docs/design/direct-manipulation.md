---
title: Manipulação direta com as mãos
description: Saiba mais sobre a manipulação direta, um modelo de entrada no qual os usuários tocam os hologramas diretamente com as mãos.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, Foco, direcionamento de foco, interação, design, mãos perto, HoloLens, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, MRTK, Kit de Ferramentas de Realidade Misturada, botão, colisores, caixa delimitadora, 2D, gestos instintivos
ms.openlocfilehash: 8316452b8308e159612a81d097c352cf1d935362
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759318"
---
# <a name="direct-manipulation-with-hands"></a>Manipulação direta com as mãos

![Botão](images/UX_Hero_Manipulation.jpg)

A manipulação direta é um modelo de entrada que envolve tocar hologramas diretamente com suas mãos. A ideia por trás desse conceito é que os objetos se comportem exatamente como no mundo real. Os botões podem ser ativados simplesmente pressionando-os, os objetos podem ser pegados e o conteúdo 2D se comporta como uma tela de toque virtual. A manipulação direta é baseada em funcionalidade, o que significa que é amigável ao usuário. Não há nenhum gesto simbólico para ensinar aos usuários. Todas as interações são criadas em torno de um elemento visual que você pode tocar ou pegar. Ela é considerada um modelo de entrada "próximo", ou seja, é mais adequado para interagir com o conteúdo que está no alcance dos braços.

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
     <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
     <td><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Headsets imersivos</strong></a></td>
</tr>
<tr>
     <td>Manipulação direta com as mãos</td>
     <td>❌ Sem suporte</td>
     <td>✔️ Recomendado</td>
     <td>➕ Com suporte.  Para a interface do usuário, recomendamos <a href="point-and-commit.md">apontar e confirmar com as mãos</a>.</td>
    
</tr>
</table>


A manipulação direta é um modelo de entrada primário no HoloLens 2, que usa o novo sistema articulado de acompanhamento com as mãos. O modelo de entrada também está disponível nos headsets imersivos com o uso de controladores de movimentos, mas não é recomendado como o principal meio de interação além da manipulação de objetos. A manipulação direta não está disponível no HoloLens (1ª geração).

<br>

---

## <a name="collidable-fingertip"></a>Ponta do dedo colidente

No HoloLens 2, as mãos do usuário são reconhecidas e interpretadas como modelos estruturais esquerdo e direito. Para implementar a ideia de tocar hologramas diretamente com mãos, idealmente, cinco colisores podem ser anexados às pontas dos cinco dedos de cada modelo estrutural de mão. No entanto, devido à falta de retorno tátil, dez pontas de dedo colidentes podem causar colisões inesperadas e imprevisíveis com os hologramas. 

Sugerimos colocar apenas um colisor em cada dedo indicador. As pontas de dedo indicador colidentes ainda podem servir como pontos de toque ativos para diversos gestos de toque que envolvam outros dedos. Os gestos de toque incluem pressionar com um dedo, tocar com um dedo, pressionar com dois dedos e pressionar com cinco dedos, conforme mostrado abaixo:

:::row:::
    :::column:::
       ![ponta do dedo colidente](images/Collidable-Fingertip.jpg)<br>
       **Ponta do dedo colidente**<br>
    :::column-end:::
    :::column:::
       ![Pressionar com um dedo](images/Collidable-Fingertip-1-finger-press.jpg)<br>
        **Pressionar com um dedo**<br>
    :::column-end:::
    :::column:::
       ![Tocar com um dedo](images/Collidable-Fingertip-1-finger-tap.jpg)<br>
       **Tocar com um dedo**<br>
    :::column-end:::
    :::column:::
       ![Pressionar com cinco dedos](images/Collidable-Fingertip-5-finger-press.jpg)<br>
       **Pressionar com cinco dedos**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a>Colisor esférico

Em vez de usar uma forma genérica aleatória, sugerimos que você use um colisor esférico. Em seguida, você pode renderizá-lo visualmente para fornecer indicações melhores para direcionamento próximo. O diâmetro da esfera deve corresponder à espessura do dedo indicador para aumentar a precisão do toque. É mais fácil recuperar a variável de espessura do dedo chamando a API da mão.

### <a name="fingertip-cursor"></a>Cursor de ponta do dedo

Além de renderizar uma esfera colidente na ponta do dedo indicador, criamos um cursor avançado de ponta do dedo para obter uma melhor experiência de direcionamento próximo. É um cursor em forma de rosca anexado à ponta do dedo indicador. De acordo com a proximidade, ele reage dinamicamente a um alvo em relação à orientação e ao tamanho, conforme detalhado abaixo:

* Quando um dedo indicador se move em direção a um holograma, o cursor sempre fica paralelo à superfície do holograma e diminui gradualmente o tamanho.
* Assim que o dedo toca a superfície, o cursor é reduzido a um ponto e emite um evento de toque.

Com o retorno interativo, os usuários podem realizar tarefas de direcionamento próximo com alta precisão, como disparar um hiperlink ou pressionar um botão, conforme mostrado abaixo. 

:::row:::
    :::column:::
       ![Cursor de ponta do dedo distante](images/Fingertip-cursor-far.jpg)<br>
       **Cursor de ponta do dedo distante**<br>
    :::column-end:::
    :::column:::
       ![Cursor de ponta do dedo próximo](images/Fingertip-cursor-near.jpg)<br>
        **Cursor de ponta do dedo próximo**<br>
    :::column-end:::
    :::column:::
       ![Cursor de ponta do dedo com contato](images/Fingertip-cursor-contact.jpg)<br>
       **Cursor de ponta do dedo com contato**<br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a>Caixa delimitadora com o sombreador de proximidade

O holograma em si também requer a capacidade de fornecer retorno visual e sonoro para compensar a falta do retorno tátil. Para isso, criamos o conceito de uma caixa delimitadora com um sombreador de proximidade. Uma caixa delimitadora é uma área volumétrica mínima que inclui um objeto 3D. A caixa delimitadora tem um mecanismo de renderização interativo chamado de sombreador de proximidade. O sombreador de proximidade se comporta da seguinte maneira:

:::row:::
    :::column:::
       ![Focalizar (distante) com comentários visuais](images/bounding-box-with-proximity-shader-hover-far.jpg)<br>
       **Focalizar (distante)**<br>
       Quando o dedo indicador está em um intervalo, um destaque da ponta do dedo é mostrado na superfície da caixa delimitadora.
    :::column-end:::
    :::column:::
       ![Focalizar (próximo) com comentários visuais](images/bounding-box-with-proximity-shader-hover-near.jpg)<br>
        **Focalizar (próximo)**<br>
        Quando a ponta do dedo se aproxima da superfície, o destaque é reduzido.
    :::column-end:::
    :::column:::
       ![O contato começa](images/bounding-box-with-proximity-shader-begin-contact.jpg)<br>
       **O contato começa**<br>
       Quando a ponta do dedo toca a superfície, toda a caixa delimitadora tem sua cor alterada ou gera efeitos visuais para refletir o estado de toque.
    :::column-end:::
    :::column:::
       ![O contato termina](images/bounding-box-with-proximity-shader-end-contact.jpg)<br>
       **O contato termina**<br>
       Um efeito sonoro pode ser ativado para aprimorar o retorno visual do toque.
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a>Botão de pressão

Com uma ponta do dedo colidente, os usuários podem interagir com um componente holográfico da interface do usuário fundamental, como o botão de pressionar. Um botão de pressão é um botão holográfico adaptado para o pressionar direto do dedo. Novamente, devido à falta de retorno tátil, um botão de pressão ativa alguns mecanismos para lidar com os problemas relacionados ao retorno tátil.

* O primeiro mecanismo é uma caixa delimitadora com um sombreador de proximidade, o qual é detalhado na seção anterior. Ele fornece aos usuários uma melhor sensação de proximidade quando eles se aproximam e fazem contato com um botão.
* O segundo mecanismo é o de liberação. A liberação cria uma ideia de pressionar para baixo depois da ponta de um dedo entrar em contato com um botão. O mecanismo verifica se o botão se move intimamente com a ponta do dedo ao longo do eixo de profundidade. O botão pode ser disparado quando atinge uma profundidade escolhida (ao ser pressionado) ou deixa a profundidade (ao ser liberado) depois de passar por ela.
* O efeito sonoro deve ser adicionado para melhorar o retorno quando o botão é disparado.

:::row:::
    :::column:::
       ![botão de pressionar a distância](images/pressable-button-far.jpg)<br>
       **O dedo está longe**<br>
    :::column-end:::
    :::column:::
       ![botão de pressionar próximo](images/pressable-button-approach.jpg)<br>
        **O dedo se aproxima**<br>
    :::column-end:::
    :::column:::
       ![o contato com o botão de pressionar começa](images/pressable-button-contact.jpg)<br>
       **O contato começa**<br>
    :::column-end:::
    :::column:::
       ![pressionar o botão de pressionar](images/pressable-button-press.jpg)<br>
       **Pressione**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>Interação do slate 2D

Um [slate](slate.md) 2D é um contêiner holográfico usado para hospedar o conteúdo do aplicativo 2D, assim como um navegador da Web. O conceito de design para interagir com um slate 2D por meio da manipulação direta é o mesmo que interagir com uma tela touch física.

### <a name="to-interact-with-the-slate-contact"></a>Para interagir com o contato do slate

:::row:::
    :::column:::
       ![Tocar](images/2d-slate-interaction-touch.jpg)<br>
       **Tocar**<br>
       Use o dedo indicador para pressionar um botão ou hiperlink.
    :::column-end:::
    :::column:::
       ![Rolar](images/2d-slate-interaction-scroll2.jpg)<br>
        **Rolar**<br>
        Use o dedo indicador para rolar um slate de conteúdo para cima e para baixo.
    :::column-end:::
    :::column:::
       ![Aplicar zoom](images/2d-slate-interaction-zoom2.jpg)<br>
       **Aplicar zoom**<br>
       O usuário usa os dois dedos indicadores para aumentar e diminuir o zoom no conteúdo do slate, de acordo com o movimento relativo dos dedos.
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a>Para manipular o slate 2D em si

:::row:::
    :::column:::
       ![Gráfico mostrando o recurso segurar e arrastar](images/manipulate-2d-slate-move.jpg)<br>
       **Mover**<br>
       Movimente suas mãos para os cantos e bordas para revelar as funcionalidades de manipulação mais próximas. Segure a barra holográfica na parte superior do slate 2D, o que permite mover todo o slate.
    :::column-end:::
    :::column:::
       ![Gráfico mostrando o recurso de escala](images/manipulate-2d-slate-scale.jpg)<br>
        **Dimensionar**<br>
        Segure as funcionalidades de manipulação e faça um dimensionamento uniforme utilizando as funcionalidades de canto.
    :::column-end:::
    :::column:::
       ![Refluxo](images/manipulate-2d-slate-reflow.jpg)<br>
       **Refluxo**<br>
       Segure as funcionalidades de manipulação e faça um refluxo por meio das funcionalidades de borda.
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a>Manipulação de objetos 3D

O HoloLens 2 permite que os usuários habilitem suas mãos para orientar e manipular objetos holográficos 3D, aplicando uma caixa delimitadora a cada objeto 3D. A caixa delimitadora fornece uma melhor percepção da profundidade por meio do sombreador de proximidade. Com a caixa delimitadora, há duas abordagens de design para a manipulação de objetos 3D.

### <a name="affordance-based-manipulation"></a>Manipulação baseada em funcionalidade

A manipulação com base em funcionalidade permite manipular o objeto 3D por meio de uma caixa delimitadora, junto com as funcionalidades de manipulação em torno dela. 

:::row:::
    :::column:::
       ![Gráfico mostrando uma caixa delimitadora de objetos e o recurso mover](images/3d-object-manipulation-move.jpg)<br>
       **Mover**<br>
       Quando a mão de um usuário está próxima a um objeto 3D, a caixa delimitadora e a funcionalidade mais próxima são reveladas. Os usuários podem segurar a caixa delimitadora para mover todo o objeto.
    :::column-end:::
    :::column:::
       ![Gráfico mostrando o usuário segurando a borda de um objeto para girá-lo](images/3d-object-manipulation-rotate.jpg)<br>
        **Girar**<br>
        Os usuários podem segurar as funcionalidades de borda para girar.
    :::column-end:::
    :::column:::
       ![Gráfico mostrando o usuário segurando o canto de um objeto para dimensioná-lo](images/3d-object-manipulation-scale.jpg)<br>
       **Dimensionar**<br>
       Os usuários podem segurar as funcionalidades de borda para dimensionar uniformemente.
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a>Manipulação não baseada em funcionalidade

A manipulação que não é baseada em funcionalidade não anexa a funcionalidade à caixa delimitadora. Os usuários podem revelar apenas a caixa delimitadora e interagir diretamente com ela. Se a caixa delimitadora for pega com uma mão, a translação e rotação do objeto estarão associadas ao movimento e à orientação da mão. Quando o objeto é pego com as duas mãos, os usuários podem transladá-lo, dimensioná-lo e girá-lo de acordo com os movimentos relativos das duas mãos.

A manipulação específica requer precisão. Recomendamos usar a **manipulação baseada em funcionalidade**, pois ela fornece um alto nível de granularidade. Para a manipulação flexível, recomendamos usar a **manipulação não baseada em funcionalidade**, pois ela permite experiências instantâneas e divertidas.

<br>

---


## <a name="instinctual-gestures"></a>Gestos instintuais

Com o HoloLens (1ª geração), ensinamos aos usuários alguns gestos predefinidos, como abrir a mão e fechar e abrir dedos indicador e polegar. Para o HoloLens 2, não pedimos para os usuários memorizarem gestos simbólicos. Todos os gestos exigidos do usuário, em que os usuários precisam interagir com os hologramas e o conteúdo, são instintivos. A forma de atingir gestos instintuais é ajudar os usuários a realizar os gestos por meio do design de funcionalidades da interface do usuário.

Por exemplo, se nós incentivarmos o usuário a segurar um objeto ou um ponto de controle com uma pinçagem de dois dedos, o objeto ou o ponto de controle deverá ser pequeno. Se quisermos que o usuário o segure com cinco dedos, o objeto ou o ponto de controle deverá ser relativamente grande. Como acontece com os botões, um botão pequeno limitará os usuários a pressioná-lo com um dedo. Um botão grande encorajará os usuários a pressioná-lo com a palma da mão.


:::row:::
    :::column:::
       ![Gráfico mostrando o usuário segurando um objeto pequeno para movê-lo](images/instinctual-gestures-smallobject.jpg)<br>
       **Objeto pequeno**<br>
    :::column-end:::
    :::column:::
       ![Gráfico mostrando o usuário segurando um objeto médio para movê-lo](images/instinctual-gestures-mediumobject.jpg)<br>
        **Objeto médio**<br>
    :::column-end:::
    :::column:::
       ![Gráfico mostrando o usuário segurando um objeto grande para movê-lo](images/instinctual-gestures-largeobject.jpg)<br>
       **Objeto grande**<br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Design simétrico entre os controladores de mão e DoF 6

Talvez você tenha observado que há interações paralelas que podemos utilizar entre as mãos em controladores de RA e de movimento na VR. Ambas as entradas podem ser usadas para disparar manipulações diretas em seus respectivos ambientes. No HoloLens 2, os movimentos de segurar e arrastar com mãos em distância próxima funcionam da mesma maneira que o botão para segurar nos controladores de movimentos do WMR. Isso proporciona aos usuários uma familiaridade de interação entre as duas plataformas, o que poderá ser útil se você decidir portar seu aplicativo entre plataformas.

<br>

---

## <a name="optimize-with-eye-tracking"></a>Otimizar com acompanhamento ocular

A manipulação direta poderá proporcionar uma sensação mágica se funcionar conforme o esperado. No entanto, ela também poderá se tornar frustrante se você não puder mover sua mão para algum lugar sem disparar inadvertidamente um holograma. O acompanhamento ocular ajuda potencialmente a identificar melhor qual é a intenção do usuário.

* **Quando**: reduzir o disparo involuntário de uma resposta de manipulação. O acompanhamento ocular permite entender melhor o que um usuário realmente deseja fazer.
Por exemplo, imagine que você esteja lendo um texto (instrutivo) holográfico e se aproxime para pegar uma ferramenta de trabalho do mundo real.

Ao fazer isso, você move acidentalmente sua mão sobre alguns botões holográficos interativos que não tinha observado antes. Por exemplo, ela pode estar fora do FoV (campo de visão) do usuário.

Se o usuário não olhar um holograma por um tempo, mas um evento de toque ou aperto tiver sido detectado para ele, provavelmente, a interação não será intencional.

* **Qual deles**:  além de lidar com ativações falso-positivas, outro exemplo inclui a melhor identificação dos hologramas a serem segurados ou tocados, já que o ponto de interseção preciso pode não ser claro da sua perspectiva, especialmente se vários hologramas estão posicionados próximos uns dos outros.

  Embora o acompanhamento ocular no HoloLens 2 tenha limitações com base na precisão com a que ele pode determinar seu foco com o olhar, isso ainda pode ser muito útil para interações próximas devido à disparidade de profundidade ao interagir com a entrada de mão. Isso significa que, às vezes, é difícil determinar se a sua mão está atrás ou na frente de um holograma para segurar precisamente um widget de manipulação, por exemplo.

* **Onde**: usar informações sobre o que um usuário está vendo com gestos de lançamento rápido. Segure um holograma e lance-o para seu destino pretendido.  

    Embora isso geralmente funcione bem, gestos de mão muito rápidos podem resultar em destinos altamente imprecisos. No entanto, o acompanhamento ocular poderia melhorar a precisão do gesto.

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a>Manipulação no MRTK (Kit de Ferramentas de Realidade Misturada) para o Unity
Com o **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , você pode alcançar facilmente o comportamento de manipulação comum usando o script **ObjectManipulator**. Com o ObjectManipulator, você pode pegar e mover objetos diretamente com mãos ou com o raio de mão. Ele também dá suporte à manipulação com as duas mãos para dimensionar e girar um objeto.

* [MRTK – Manipulação](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-manipulator.md)

---

## <a name="see-also"></a>Veja também

* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Apontar e confirmar com as mãos](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)