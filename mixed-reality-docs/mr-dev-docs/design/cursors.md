---
title: Cursores
description: um cursor ou indicador de seu vetor de direcionamento, fornece comentários contínuos para o usuário entender o que HoloLens entende sobre suas intenções.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1ª gen), HoloLens 2, realidade misturada, cursores, direcionamento, olhar, gestos, headset de realidade misturada, headset de realidade mista do windows, headset de realidade virtual, HoloLens, MRTK, realidade misturada Toolkit, raios, entrada
ms.openlocfilehash: 46e570328451078586109448bce28a7074bc9c2f791c15a284c85b845441fabe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187036"
---
# <a name="cursors"></a>Cursores

![Cursores](images/UX_Hero_Cursor.jpg)

Um cursor fornece comentários contínuos com base em onde o headset acredita que o foco de um usuário atual está em um determinado momento. Os comentários do cursor incluem qual área, holograma ou ponto no ambiente virtual responde à entrada. Embora o cursor seja uma representação digital de onde o dispositivo entende a atenção do usuário, isso não é o mesmo que determinar as intenções do usuário. Os comentários do cursor também permitem que os usuários saibam quais respostas do sistema esperam. Você pode usar os comentários para comunicar sua intenção ao dispositivo, o que aumenta a confiança do usuário.

Há três tipos de cursores: **Finger, Ray** e **Head-olhar**. esses cursores de apontação funcionam com modalidades de entrada diferentes nos headsets HoloLens, HoloLens 2 e de imersão. Abaixo está a orientação sobre qual tipo de cursor usar para cada tipo de headset e modelo de interação. na realidade misturada Toolkit (MRTK), criamos módulos de cursores do tipo "arrastar e soltar" para ajudá-lo a criar a experiência correta.

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
        <td>Cursor do dedo</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Cursor Ray</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Cursor de olhar de cabeçalho</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>Cursor do dedo

o cursor do dedo só está disponível no HoloLens 2 para aprimorar o modo de interação "[manipulação direta com mãos](direct-manipulation.md)". Anexamos anéis às dicas de ambos os dedos para entender melhor onde o dedo está apontando. O tamanho do anel é baseado na proximidade do dedo com a superfície da interface do usuário, que se reduz a um ponto pequeno quando o dedo toca na interface do usuário. Quanto mais próximo do dedo, menor o anel. <br>

![cursor do dedo](images/finger-cursor.png)<br>
**Estados de comentários visuais do cursor 1 do dedo** : o anel é reduzido para um ponto. 2: o anel se alinha com a superfície. 3: o anel é perpendicular ao vetor de dedo. 4: nenhum anel.

## <a name="ray-cursor"></a>Cursor Ray

Os cursores de raio são anexados ao fim dos raios distantes para permitir a manipulação de objetos que estão fora de mãos. Em headsets de imersão, os raios saem dos controladores de movimento e dos cursores de fim em ponto. no HoloLens 2, aplicamos o modelo mental desses raios do controlador de movimento e raios de mão projetadas que se originam de palms e terminam com cursores em forma de anel que são consistentes com cursores de dedo usados na manipulação direta. <br>
:::row:::
    :::column:::
        ![Ray cursor Controller](images/ray-cursor-controller.png)<br>
        **Ray cursores de controladores de movimento**<br>
    :::column-end:::
    :::column:::
        ![Raio do cursor](images/ray-cursor-hand.png)<br>
        **Raios cursores de mãos**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a>Cursor de olhar de cabeçalho

O cursor Head-olhar é um ponto que é anexado ao final de um vetor Head-olhar invisível que usa a posição e a rotação do ponto de partida. Para executar ações, esse cursor apontando é emparelhado com várias entradas de confirmação, como toque de ar, comandos de voz, duração e pressionamento de botão. no HoloLens 2, o head-olhar é melhor emparelhado com qualquer entrada de confirmação que não seja o toque de ar, pois haverá um conflito de interação entre o toque de ar e raios de distância. <br>
:::row:::
    :::column:::
        ![Olhar do cursor de cabeçalho](images/head-gaze-cursor-hand.png)<br>
        **Cursor de cabeçalho olhar com gesto de mão**<br>
    :::column-end:::
    :::column:::
        ![Voz do cursor olhar de cabeçalho](images/head-gaze-cursor-voice.png)<br>
        **Cursor de cabeçalho olhar com comando de voz**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a>Recomendações de personalização do cursor

Se você quiser personalizar os comportamentos e as aparências dos comentários do cursor, veja algumas recomendações de design:

### <a name="cursor-scale"></a>Escala do cursor

* O cursor não deve ser maior do que os destinos disponíveis, permitindo que os usuários interajam com facilidade e exibam o conteúdo.
* Dependendo da experiência que você criar, dimensionar o cursor à medida que o usuário procura também é uma consideração importante. Por exemplo, à medida que o usuário fica mais distante em sua experiência, o cursor não deve se tornar muito pequeno, de modo que ele é perdido.
* Ao dimensionar o cursor, considere aplicar uma animação suave a ele, pois ele é dimensionado para dar a ele uma sensação orgânica.
* Evite obstruir o conteúdo. Hologramas são o que torna a experiência fácil de memorizar e o cursor não deve ser retirado delas.

### <a name="directionless-cursor-shape"></a>Forma de cursor de direção

* Embora não haja uma forma de cursor à direita, recomendamos que você use uma forma sem direção como uma Torus. Um cursor que aponta em alguma direção (por exemplo, um cursor de seta tradicional) pode confundir o usuário para sempre verificar dessa forma.
* Uma exceção a isso é quando se usa o cursor para comunicar a instrução de interação ao usuário. Por exemplo, ao dimensionar hologramas no sistema operacional de realidade misturada, o cursor inclui temporariamente setas que instruem o usuário sobre como mover sua mão para dimensionar o holograma.

### <a name="look-and-feel"></a>Aparência

* Um cursor com formato de rosca ou Torus funciona para muitos aplicativos.
* Escolha uma cor e forma que melhor represente a experiência que você está criando.
* Os cursores estão especialmente sujeitos à [separação de cores](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).
* Um cursor pequeno com opacidade equilibrada mantém-o informativo sem a predominante da hierarquia visual.
* Seja Cognizant de usar sombras ou destaques por trás do cursor, pois eles podem obstruir o conteúdo e distrair a tarefa em questão.
* Os cursores devem alinhar e Hug as superfícies em seu aplicativo. Os usuários terão a sensação de que o sistema pode ver onde estão olhando, mas também que o sistema está ciente de seus arredores. Por exemplo, o cursor no sistema operacional misto da realidade se alinha às superfícies do mundo do usuário, criando uma sensação de conscientização do mundo, mesmo quando o usuário não está olhando diretamente para um holograma.
* Bloquear magneticamente o cursor para um elemento interativo quando ele está próximo do usuário pode ajudar a melhorar a confiança que o usuário irá interagir com esse elemento quando usar uma ação de seleção.

### <a name="visual-cues"></a>Indicações visuais

* Se sua experiência estiver concentrada em um único holograma, o cursor deverá alinhar e hugr apenas esse holograma e alterar a forma quando você olhar para fora desse holograma. Isso pode transmitir ao usuário que o holograma é acionável e pode interagir com ele.
* Se seu aplicativo usar o mapeamento espacial, o cursor poderá ser alinhado e Hug cada superfície que vê. isso fornece comentários aos usuários que HoloLens e seu aplicativo pode ver seu espaço. Isso reforça o fato de que os hologramas são reais e em nosso mundo e ajudam a preencher a lacuna entre o real e o virtual.
* Tenha uma ideia do que o cursor deve fazer quando não há hologramas ou superfícies na exibição. Colocá-lo em uma distância predeterminada na frente do usuário é uma opção.

### <a name="possible-actions"></a>Ações possíveis

* O cursor pode ser representado por ícones diferentes para transmitir possíveis ações que um holograma pode fazer, como dimensionamento ou rotação.
* Somente adicione informações extras sobre o cursor se isso significa algo para o usuário. Caso contrário, os usuários talvez não percebam as alterações de estado ou ficam confusos com o cursor.

### <a name="input-state"></a>Estado de entrada

* Poderíamos usar o cursor para exibir o estado ou a intenção de entrada do usuário. Por exemplo, podemos exibir um ícone informando ao usuário que o sistema vê seu estado de mão e que o aplicativo sabe que está pronto para agir.
* Também poderíamos usar o cursor para mostrar aos usuários que comandos de voz foram ouvidos pelo sistema por meio de uma alteração de cor momentânea

* Os seguintes Estados de cursor podem ser implementados de maneiras diferentes. Você pode implementar esses Estados diferentes modelando o cursor como um computador de estado. Por exemplo:
    * Estado ocioso é onde você mostra o cursor padrão.
    * Estado pronto é quando você detecta a mão do usuário na posição pronta.
    * O estado de interação é quando o usuário está fazendo uma interação específica.
    * O estado de ações possíveis ou o estado de foco é quando você transmite possíveis ações que podem ser executadas em um holograma.

Você também pode implementar esses estados de maneira capaz de exibir diferentes ativos de arte ao detectar estados diferentes.

<br>

---

## <a name="going-cursor-free"></a>Ir para "sem cursor"

O design sem um cursor é recomendado quando a sensação de imersão é um componente fundamental de uma experiência e ao apontar interações (por meio de olhar e gesto) não exigem grande precisão. O sistema ainda precisa atender aos requisitos normais de um cursor: fornecer aos usuários comentários contínuos sobre a compreensão do sistema de seus apontamentos e ajudá-los a comunicar suas intenções ao sistema. Isso pode ser possível por meio de outras alterações de estado perceptíveis.

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>Cursor no MRTK (Mixed Reality Toolkit) para Unity

Por padrão, [o MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece um cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) que tem o mesmo estado visual que o cursor do sistema do shell. Ele é atribuído no perfil de Entrada do MRTK, em Ponteiros. Você pode substituir/personalizar esse cursor para sua experiência. Para a experiência com a entrada de acompanhamento ocular, o MRTK também fornece EyeGazeCursor, que tem um visual sutil para minimizar a distração.

* [MRTK – Perfil de ponteiro](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [MRTK – Sistema de entrada](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [MRTK – Ponteiros](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a>Consulte também

* [Gestos](gaze-and-commit.md#composite-gestures)
* [Focar com a cabeça e confirmar](gaze-and-commit.md)