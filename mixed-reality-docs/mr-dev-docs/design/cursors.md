---
title: Cursores
description: Um cursor ou indicador do vetor de direcionamento fornece comentários contínuos para o usuário entender o que o HoloLens entende sobre suas intenções.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1ª geração), HoloLens 2, Realidade Misturada, cursores, direcionamento, olhar, gestos, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada, raios, entrada
ms.openlocfilehash: 829d7b3f766f848228946ee0a623f9f3013adca3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600375"
---
# <a name="cursors"></a>Cursores

![Cursores](images/UX_Hero_Cursor.jpg)

Um cursor fornece comentários contínuos com base em onde o headset acredita que um foco atual dos usuários está em um determinado momento. Os comentários do cursor incluem qual área, holograma ou ponto no ambiente virtual responde à entrada. Embora o cursor seja uma representação digital de onde o dispositivo entende a atenção do usuário, isso não é o mesmo que determinar as intenções do usuário. Os comentários do cursor também permitem que os usuários saibam quais respostas do sistema esperar. Você pode usar os comentários para comunicar sua intenção ao dispositivo, o que aumenta a confiança do usuário.

Há três tipos de cursores: **dedo, raio** e **olhar para a cabeça.** Esses cursores que apontam funcionam com diferentes modais de entrada no HoloLens, no HoloLens 2 e em headsets imersivos. Abaixo estão as diretrizes sobre qual tipo de cursor usar para cada tipo de headset e modelo de interação. No MRTK (Kit de Ferramentas de Realidade Misturada), criamos módulos de cursores do "arrastar e soltar" para ajudá-lo a criar a experiência de apontar para a direita.

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
        <td>Cursor de dedo</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Cursor de raio</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Cursor de olhar para a cabeça</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>Cursor de dedo

O cursor de dedo só está disponível no HoloLens 2 para aprimorar o[modo](direct-manipulation.md)de interação " manipulação direta com as mãos ". Anexamos anéis às dicas de ambos os dedos indicadores para entender melhor para onde o dedo está apontando. O tamanho do anel é baseado na proximidade do dedo com a superfície da interface do usuário, que é reduzido a um ponto pequeno quando o dedo toca a interface do usuário. Quanto mais próximo o dedo, menor será o anel. <br>

![cursor de dedo](images/finger-cursor.png)<br>
**Estados de comentários visuais do cursor** de dedo 1: o anel diminui para um ponto. 2: o anel se alinha com a superfície. 3: o anel é um vetor de dedo para o dedo. 4: Sem anel.

## <a name="ray-cursor"></a>Cursor de raio

Cursores de raio são anexados ao final de raios que apontam muito para permitir a manipulação de objetos que estão fora do alcance das mãos. Em headsets imersivos, os raios se disparam dos controladores de movimento e terminam em cursores de ponto. No HoloLens 2, aplicamos o modelo mental desses raios do controlador de movimento e os raios de mão projetados que se originam das mãos e terminam em cursores em forma de anel consistentes com cursores de dedo usados na manipulação direta. <br>
:::row:::
    :::column:::
        ![Controlador de cursor de raio](images/ray-cursor-controller.png)<br>
        **Cursores de raio de controladores de movimento**<br>
    :::column-end:::
    :::column:::
        ![Mão do cursor de raio](images/ray-cursor-hand.png)<br>
        **Cursores de raio de mãos**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a>Cursor de olhar para a cabeça

O cursor de olhar para a cabeça é um ponto anexado ao final de um vetor invisível de olhar para a cabeça que usa a posição e a rotação da cabeça para apontar. Para executar ações, esse cursor apontador é emparelhado com várias entradas de commit, como toque de ar, comandos de voz, pausar e pressionar botão. No HoloLens 2, o olhar com a cabeça é melhor emparelhado com qualquer entrada de commit que não seja toque de ar, pois haverá conflito de interação entre o toque do ar e os raios de mão distantes. <br>
:::row:::
    :::column:::
        ![Mão do cursor de cursor de curso](images/head-gaze-cursor-hand.png)<br>
        **Cursor de olhar para a cabeça com gesto de mão**<br>
    :::column-end:::
    :::column:::
        ![Voz do cursor de cursor de olhar para a cabeça](images/head-gaze-cursor-voice.png)<br>
        **Cursor de olhar para a cabeça com comando de voz**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a>Recomendações de personalização do cursor

Se você quiser personalizar os comportamentos e as aparências dos comentários do cursor, aqui estão algumas recomendações de design:

### <a name="cursor-scale"></a>Escala de cursor

* O cursor não deve ser maior do que os destinos disponíveis, permitindo que os usuários interajam facilmente e exibiam o conteúdo.
* Dependendo da experiência que você cria, dimensionar o cursor conforme o usuário procura também é uma consideração importante. Por exemplo, à medida que o usuário fica mais distante em sua experiência, o cursor não deve se tornar muito pequeno, de forma que seja perdido.
* Ao dimensionar o cursor, considere aplicar uma animação suave a ele à medida que ele é dimensionamento para dar a ele uma sensação química.
* Evite obstruir o conteúdo. Os hologramas são o que fazem com que a experiência seja uma memória e o cursor não deve estar sendo desacordo deles.

### <a name="directionless-cursor-shape"></a>Forma do cursor sem direção

* Embora não haja uma forma de cursor à direita, recomendamos que você use uma forma sem direção como um torus. Um cursor que aponta em alguma direção (por exemplo, um cursor de seta tradicional) pode confundir o usuário para sempre ter essa aparência.
* Uma exceção a isso é ao usar o cursor para comunicar a instrução de interação com o usuário. Por exemplo, ao dimensionar hologramas no sistema operacional de Realidade Misturada, o cursor inclui temporariamente setas que instruim o usuário sobre como mover a mão para dimensionar o holograma.

### <a name="look-and-feel"></a>Aparência

* Um cursor em forma de rosca ou torus funciona para muitos aplicativos.
* Escolha uma cor e uma forma que melhor represente a experiência que você está criando.
* Cursores são especialmente propensos à [separação de cores.](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* Um cursor pequeno com opacidade equilibrada o mantém informativo sem dominar a hierarquia visual.
* Seja ciente do uso de sombras ou realçadas por trás do cursor, pois eles podem obstruir o conteúdo e desviar a tarefa em mãos.
* Os cursores devem se alinhar e se alinhar às superfícies em seu aplicativo. Os usuários terão a impressão de que o sistema pode ver onde estão procurando, mas também que o sistema está ciente de seus ambientes. Por exemplo, o cursor no sistema operacional de Realidade Misturada se alinha às superfícies do mundo do usuário, criando uma sensação de reconhecimento do mundo mesmo quando o usuário não está olhando diretamente para um holograma.
* O bloqueio magnético do cursor em um elemento interativo quando ele está próximo ao usuário pode ajudar a melhorar a confiança de que o usuário interagirá com esse elemento quando usar uma ação de seleção.

### <a name="visual-cues"></a>Dicas visuais

* Se sua experiência estiver focada em um único holograma, o cursor deverá alinhar e se alinhar somente a esse holograma e alterar a forma quando você olhar para fora desse holograma. Isso pode transmitir ao usuário que o holograma pode ser a ação e pode interagir com ele.
* Se o aplicativo usar o mapeamento espacial, o cursor poderá alinhar e se alinhar a todas as superfícies que ele vir. Isso fornece comentários aos usuários de que o HoloLens e seu aplicativo podem ver seu espaço. Isso reforça o fato de que os hologramas são reais e em nosso mundo e ajudam a fazer a ponte entre o real e o virtual.
* Tenha uma ideia do que o cursor deve fazer quando não houver hologramas ou superfícies em exibição. Colocá-lo a uma distância predeterminada na frente do usuário é uma opção.

### <a name="possible-actions"></a>Ações possíveis

* O cursor pode ser representado por ícones diferentes para transmitir possíveis ações que um holograma pode fazer, como dimensionamento ou rotação.
* Adicione apenas informações extras no cursor se ele significa algo para o usuário. Caso contrário, os usuários podem não notar as alterações de estado ou se confundirem com o cursor.

### <a name="input-state"></a>Estado de entrada

* Poderíamos usar o cursor para exibir o estado de entrada ou a intenção do usuário. Por exemplo, podemos exibir um ícone dizendo ao usuário que o sistema vê seu estado de mão e que o aplicativo sabe que está pronto para tomar medidas.
* Também podemos usar o cursor para mostrar aos usuários que os comandos de voz foram ouvido pelo sistema por meio de uma alteração de cor momentânea

* Os seguintes estados de cursor podem ser implementados de maneiras diferentes. Você pode implementar esses estados diferentes modelando o cursor como um computador de estado. Por exemplo:
    * O estado ocioso é onde você mostra o cursor padrão.
    * O estado pronto é quando você detecta a mão do usuário na posição pronta.
    * O estado de interação é quando o usuário está fazendo uma interação específica.
    * O estado de ações possíveis ou o estado de foco é quando você transmite possíveis ações que podem ser executadas em um holograma.

Você também pode implementar esses estados de maneira capaz de exibir diferentes ativos de arte ao detectar estados diferentes.

<br>

---

## <a name="going-cursor-free"></a>Ir para "sem cursor"

O design sem um cursor é recomendado quando a sensação de imersão é um componente fundamental de uma experiência e ao apontar interações (por meio de olhar e gesto) não exigem grande precisão. O sistema ainda precisa atender aos requisitos normais de um cursor: fornecer aos usuários comentários contínuos sobre a compreensão do sistema de seus apontamentos e ajudá-los a comunicar suas intenções ao sistema. Isso pode ser possível por meio de outras alterações de estado perceptíveis.

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>Cursor no MRTK (Kit de Ferramentas de Realidade Misturada) para Unity

Por padrão, [o MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece um cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) que tem o mesmo estado visual que o cursor do sistema do shell. Ele é atribuído no perfil de Entrada do MRTK, em Ponteiros. Você pode substituir/personalizar esse cursor para sua experiência. Para a experiência com a entrada de acompanhamento ocular, o MRTK também fornece EyeGazeCursor, que tem um visual sutil para minimizar a distração.

* [MRTK – Perfil de ponteiro](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [MRTK – Sistema de entrada](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [MRTK – Ponteiros](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a>Consulte também

* [Gestos](gaze-and-commit.md#composite-gestures)
* [Focar com a cabeça e confirmar](gaze-and-commit.md)