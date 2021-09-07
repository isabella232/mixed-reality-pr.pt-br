---
title: Objeto interativo
description: Saiba como disparar eventos, fornecer indicações visuais e interagir com objetos em seus aplicativos de realidade misturada.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/06/2019
ms.topic: article
keywords: realidade misturada, controles, interação, indicações, interface do usuário, ux, headset de realidade misturada, headset de realidade mista do windows, headset de realidade virtual, HoloLens, MRTK, realidade misturada Toolkit, áudio
ms.openlocfilehash: f1fe68c7f35fecb9fbee888893fb15a83a8595ec
ms.sourcegitcommit: 4f1697b11e5638db9bbd0bd7a671d846d54c6389
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2021
ms.locfileid: "122682992"
---
# <a name="interactable-object"></a>Objeto interativo

![Objetos Interactible](images/UX_Hero_Interactable.jpg)

Um botão tem muito tempo uma metáfora usada para disparar um evento no mundo abstrato de 2D. No mundo de realidade misturada tridimensional, não precisamos mais ser confinado para esse mundo de abstração. Qualquer coisa pode ser um objeto que possa ser **interagindo** que dispara um evento. Um objeto de interação pode ser qualquer coisa, desde uma xícara de café em uma tabela até um balão no midair. Ainda fazemos uso de botões tradicionais em determinadas situações, como na interface do usuário da caixa de diálogo. A representação visual do botão depende do contexto.

<br>

---

## <a name="important-properties-of-the-interactable-object"></a>Propriedades importantes do objeto que interage

### <a name="visual-cues"></a>Indicações visuais

As indicações visuais são indicações de sensor de luz, recebidas pelo olho e processadas pelo sistema visual durante a percepção visual. Como o sistema visual é dominante em muitas espécies, especialmente nas pessoas, as indicações visuais são uma grande fonte de informações sobre como o mundo é percebido.

Como os objetos Holographic são mesclados com o ambiente do mundo real em realidade misturada, pode ser difícil entender de quais objetos você pode interagir. Para qualquer objeto interagindo em sua experiência, é importante fornecer indicações visuais diferenciadas para cada Estado de entrada. Isso ajuda o usuário a entender qual parte da sua experiência é interagir e torna o usuário confiante usando um método de interação consistente.

<br>

---

### <a name="far-interactions"></a>Interações distantes

Para todos os objetos que o usuário pode interagir com o olhar, o conjunto de raio e o raio do controlador de movimento, é recomendável ter uma indicação visual diferente para esses três Estados de entrada:

:::row:::
    :::column:::
       ![Objeto que interage com o estado padrão](images/interactibleobject-states-default.jpg)<br>
       **Estado padrão (observação)**<br>
        Estado ocioso padrão do objeto.
    O cursor não está no objeto. A mão não é detectada.
    :::column-end:::
    :::column:::
       ![Objeto de interação com o estado de destino e de foco](images/interactibleobject-states-targeted.jpg)<br>
        **Estado de destino (focalizar)**<br>
        Quando o objeto é direcionado com o cursor olhar, a proximidade do dedo ou o ponteiro do controlador de movimento.
    O cursor está no objeto. A mão foi detectada, pronto.
    :::column-end:::
    :::column:::
       ![Objeto interagir com estado pressionado](images/interactibleobject-states-pressed.jpg)<br>
       **Estado pressionado**<br>
        Quando o objeto for pressionado com um gesto de toque de ar, pressione o botão de seleção de dedo ou controlador de movimento.
    O cursor está no objeto. A mão é detectada, o ar está tocado.
    :::column-end:::
:::row-end:::

<br>

---

Você pode usar técnicas como realce ou dimensionamento para fornecer indicações visuais para o estado de entrada do usuário. em realidade misturada, você pode encontrar exemplos de visualização de diferentes estados de entrada no menu Iniciar e com botões da barra de aplicativos. 

Veja como esses Estados se parecem em um **botão de Holographic**:

:::row:::
    :::column:::
       ![Botão Holographic no estado padrão](images/MRTK_InteractableState-default.jpg)<br>
       **Estado padrão (observação)**<br>
    :::column-end:::
    :::column:::
       ![Botão Holographic no estado de destino e de foco](images/MRTK_InteractableState-targeted.jpg)<br>
        **Estado de destino (focalizar)**<br>
    :::column-end:::
    :::column:::
       ![Botão Holographic no estado pressionado](images/MRTK_InteractableState-pressed.jpg)<br>
       **Estado pressionado**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>Interações próximas (diretas) 

o HoloLens 2 dá suporte à entrada de acompanhamento de mão articulada, que permite que você interaja com objetos. Sem comentários haptics e percepção de profundidade perfeita, pode ser difícil dizer por quanto longe sua mão é de um objeto ou se você está tocando. É importante fornecer indicações visuais suficientes para comunicar o estado do objeto, em particular, o estado de suas mãos com base nesse objeto.

Use comentários visuais para comunicar os seguintes Estados:
* **Padrão (observação)**: estado ocioso padrão do objeto.
* **Focalizar**: quando uma mão está perto de um holograma, alterar elementos visuais para se comunicar que essa mão está direcionando o holograma. 
* **Distância e ponto de interação**: à medida que a mão se aproxima de um holograma, o design de comentários para comunicar o ponto de interação projetado e a distância do objeto que o dedo é
* **Contato começa**: alterar visuais (claro, cor) para comunicar que um toque ocorreu
* **Segure**: alterar visuais (Light, Color) quando o objeto for Segure
* **Contatos termina**: alterar visuais (claro, cor) quando o toque terminar

<br>

---

:::row:::
    :::column:::
        ![Focalizar (longe)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **Focalizar (longe)**<br>
        Realce com base na proximidade da mão.
    :::column-end:::
    :::column:::
        ![Focalizar (próximo)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **Focalizar (próximo)**<br>
        Realçar alterações de tamanho com base na distância para a mão.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Toque/pressione](images/640px-interactibleobject-states-near-press.jpg)<br>
        **Toque/pressione**<br>
        Comentários sobre áudio visual Plus.
    :::column-end:::
    :::column:::
        ![Compreendi](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **Compreendi**<br>
        Comentários sobre áudio visual Plus.
    :::column-end:::
:::row-end:::

<br>

<br>

---

um [botão no HoloLens 2](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) é um exemplo de como os diferentes estados de interação de entrada são visualizados:

:::row:::
    :::column:::
        ![Default](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **Padrão**<br>
    :::column-end:::
    :::column:::
        ![Passar o mouse](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **Passar o mouse**<br>
        Revelar um efeito de iluminação baseada em proximidade.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Tocar](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **Tocar**<br>
        Mostrar efeito de ondulação.
    :::column-end:::
    :::column:::
        ![Pressione](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **Pressione**<br>
        Mova a placa frontal.
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>a indicação visual "anel" no HoloLens 2<br>
        no HoloLens 2, há uma indicação visual extra, que pode ajudar a percepção de profundidade do usuário. Um anel próximo a ele é exibido e escala verticalmente conforme o alcance fica mais próximo do objeto. O anel, eventualmente, convergi em um ponto quando o estado pressionado é atingido. Essa unificação Visual ajuda o usuário a entender a distância deles do objeto.<br>
        <br>
        *Loop de vídeo: exemplo de comentários visuais com base na proximidade a uma caixa delimitadora*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Comentário visual sobre a proximidade](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>Indicações de áudio

Para interações diretas, os comentários de áudio adequados podem melhorar drasticamente a experiência do usuário. Use comentários de áudio para comunicar as seguintes indicações:
* **Contato começa**: Tocar som quando o toque começar
* **Contatos termina**: Tocar som no ponto de toque
* **Captura começa**: reproduzir som quando a captura começar
* **Captações de captura**: Tocar som quando a captura terminar

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>Comando de voz<br>
        Para qualquer objeto que interaja, é importante dar suporte a opções de interação alternativas. Por padrão, recomendamos que os [comandos de voz](../out-of-scope/voice-design.md) tenham suporte para todos os objetos que estiverem interagindo. Para melhorar a descoberta, você também pode fornecer uma dica de ferramenta durante o estado de foco.<br>
        <br>
        *Imagem: dica de ferramenta para o comando de voz*
    :::column-end:::
        :::column:::
       ![comando de voz](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a>Recomendações de dimensionamento

Para garantir que todos os objetos interajantes possam ser facilmente tocados, é recomendável garantir que o interaja com um tamanho mínimo com base na distância em que ele é colocado do usuário. O ângulo visual geralmente é medido em graus de arco visual. O ângulo visual é baseado na distância entre os olhos do usuário e o objeto e permanece constante, enquanto o tamanho físico do destino pode mudar conforme a distância do usuário muda. Para determinar o tamanho físico necessário de um objeto com base na distância do usuário, tente usar uma calculadora de ângulo visual como [esta.](https://elvers.us/perception/visualAngle/)

Abaixo estão as recomendações para tamanhos mínimos de conteúdo interagido.

### <a name="target-size-for-direct-hand-interaction"></a>Tamanho de destino para interação direta com a mão

| Distância | Ângulo de exibição | Tamanho |
|---------|---------|---------|
| 45 cm  | não menor que 2° | 1,6 x 1,6 cm |

![Tamanho de destino para interação direta com a mão](images/TargetSizingNear.jpg)<br>
*Tamanho de destino para interação direta com a mão*


<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Tamanho de destino para interação de raio de mão ou de olhar
| Distância | Ângulo de exibição | Tamanho |
|---------|---------|---------|
| 2 m  | não menor que 1° | 3,5 x 3,5 cm |

![Tamanho de destino para interação de raio de mão ou de olhar](images/TargetSizingFar.jpg)<br>
*Tamanho de destino para interação de raio de mão ou de olhar*

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a>Objeto interajante no MRTK (Mixed Reality Toolkit) para Unity

No **[MRTK,](https://github.com/Microsoft/MixedRealityToolkit-Unity)** você pode usar o script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) para fazer com que os objetos respondam a vários tipos de estados de interação de entrada. Ele dá suporte a vários tipos de temas que permitem definir estados visuais controlando as propriedades do objeto, como cor, tamanho, material e sombreador.

* [Interativo](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [Botão](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [Cena de exemplos de interação com a mão](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

O sombreador Standard do MixedRealityToolkit  fornece várias opções, como luz de proximidade que ajuda você a criar dicas visuais e de áudio.

* [Sombreador Padrão do MRTK](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a>Confira também

* [Cursores](cursors.md)
* [Raio de mão](point-and-commit.md)
* [Botão](button.md)
* [Objeto interativo](interactable-object.md)
* [Caixa delimitadora e barra de aplicativos](app-bar-and-bounding-box.md)
* [Manipulação](direct-manipulation.md)
* [Menu lateral](hand-menu.md)
* [Menu próximo](near-menu.md)
* [Coleção de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Dica de ferramenta](tooltip.md)
* [Slate](slate.md)
* [Controle deslizante](slider.md)
* [Sombreador](shader.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
* [Exibindo o progresso](progress.md)
* [Magnetismo de superfície](surface-magnetism.md)