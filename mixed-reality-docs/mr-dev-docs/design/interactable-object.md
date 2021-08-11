---
title: Objeto interativo
description: Saiba como disparar eventos, fornecer dicas visuais e interagir com objetos em seus aplicativos de realidade misturada.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Realidade Misturada, Controles, interação, versões de interface do usuário, experiência do usuário, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Toolkit realidade misturada, áudio
ms.openlocfilehash: 9ce682de7e400eba6ffbaccbca34065a1f09966f842cffd6853f3a064f146904
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190690"
---
# <a name="interactable-object"></a>Objeto interativo

![Objetos interacionáveis](images/UX_Hero_Interactable.jpg)

Há muito tempo, um botão é uma metáfora usada para disparar um evento no mundo abstrato 2D. No mundo da realidade misturada tridimensional, não precisamos mais estar restritos a esse mundo de abstração. Qualquer coisa pode ser **um objeto interacionável** que dispara um evento. Um objeto interagente pode ser qualquer coisa, desde uma cafeteira em uma tabela até um balão no ar médio. Ainda usamos botões tradicionais em determinada situação, como na interface do usuário do diálogo. A representação visual do botão depende do contexto.

<br>

---

## <a name="important-properties-of-the-interactable-object"></a>Propriedades importantes do objeto interajante

### <a name="visual-cues"></a>Dicas visuais

As responsabilidades visuais são responsabilidades sensoriais da luz, recebidas pelo olho e processadas pelo sistema visual durante a percepção visual. Como o sistema visual é dominante em muitas espécies, especialmente em humanos, as dicas visuais são uma grande fonte de informações sobre como o mundo é percebido.

Como os objetos holográficos são mesclados com o ambiente do mundo real na realidade misturada, pode ser difícil entender com quais objetos você pode interagir. Para qualquer objeto interajante em sua experiência, é importante fornecer responsabilidades visuais diferenciadas para cada estado de entrada. Isso ajuda o usuário a entender qual parte da sua experiência é interativa e torna o usuário confiante usando um método de interação consistente.

<br>

---

### <a name="far-interactions"></a>Interações distantes

Para qualquer objeto que o usuário possa interagir com o olhar, o raio de mão e o raio do controlador de movimento, recomendamos ter uma indicação visual diferente para esses três estados de entrada:

:::row:::
    :::column:::
       ![Objeto interajante com o estado padrão](images/interactibleobject-states-default.jpg)<br>
       **Estado padrão (Observação)**<br>
        Estado ocioso padrão do objeto.
    O cursor não está no objeto . A mão não é detectada.
    :::column-end:::
    :::column:::
       ![Objeto interajante com o estado de destino e foco](images/interactibleobject-states-targeted.jpg)<br>
        **Estado direcionado (foco)**<br>
        Quando o objeto é direcionado com cursor de olhar, proximidade do dedo ou ponteiro do controlador de movimento.
    O cursor está no objeto . A mão é detectada, pronta.
    :::column-end:::
    :::column:::
       ![Objeto interagido com estado pressionado](images/interactibleobject-states-pressed.jpg)<br>
       **Estado pressionado**<br>
        Quando o objeto é pressionado com um gesto de toque de ar, pressione o dedo ou o botão de seleção do controlador de movimento.
    O cursor está no objeto . A mão é detectada, com o ar tapped.
    :::column-end:::
:::row-end:::

<br>

---

Você pode usar técnicas como realçamento ou dimensionamento para fornecer dicas visuais para o estado de entrada do usuário. Na realidade misturada, você pode encontrar exemplos de visualização de diferentes estados de entrada no menu Iniciar e com botões da barra de aplicativos. 

Veja a aparência desses estados em um **botão holográfico:**

:::row:::
    :::column:::
       ![Botão holográfico no estado padrão](images/MRTK_InteractableState-default.jpg)<br>
       **Estado padrão (Observação)**<br>
    :::column-end:::
    :::column:::
       ![Botão holográfico no estado de destino e foco](images/MRTK_InteractableState-targeted.jpg)<br>
        **Estado direcionado (foco)**<br>
    :::column-end:::
    :::column:::
       ![Botão holográfico no estado pressionado](images/MRTK_InteractableState-pressed.jpg)<br>
       **Estado pressionado**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>Interações próximas (diretas) 

HoloLens 2 dá suporte à entrada de acompanhamento de mão articulada, que permite interagir com objetos. Sem comentários acráticos e percepção de profundidade perfeita, pode ser difícil dizer o quão distante sua mão está de um objeto ou se você está tocando nele. É importante fornecer dicas visuais suficientes para comunicar o estado do objeto, em particular o estado de suas mãos com base nesse objeto.

Use comentários visuais para comunicar os seguintes estados:
* **Padrão (Observação)**: estado ocioso padrão do objeto.
* **Passar** o mouse: quando uma mão estiver perto de um holograma, altere os visuais para comunicar que a mão está direcionando o holograma. 
* **Distância e ponto de interação:** à medida que a mão se aproxima de um holograma, projete comentários para comunicar o ponto de interação projetado e a distância do objeto em que o dedo está
* **Início do contato:** alterar visuais (claro, cor) para comunicar que ocorreu um toque
* **Compreendido:** alterar visuais (claro, cor) quando o objeto é compreendido
* **Extremidades de** contato: alterar visuais (claro, cor) quando o toque terminar

<br>

---

:::row:::
    :::column:::
        ![Passar o mouse (distante)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **Passar o mouse (distante)**<br>
        Realçamento com base na proximidade da mão.
    :::column-end:::
    :::column:::
        ![Passar o mouse (próximo)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **Passar o mouse (próximo)**<br>
        Realça as alterações de tamanho com base na distância até a mão.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Toque/pressione](images/640px-interactibleobject-states-near-press.jpg)<br>
        **Toque/pressione**<br>
        Visual mais comentários de áudio.
    :::column-end:::
    :::column:::
        ![Agarrar](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **Agarrar**<br>
        Visual mais comentários de áudio.
    :::column-end:::
:::row-end:::

<br>

<br>

---

Um [botão no HoloLens 2](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) é um exemplo de como os diferentes estados de interação de entrada são visualizados:

:::row:::
    :::column:::
        ![Default](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **Padrão**<br>
    :::column-end:::
    :::column:::
        ![Passar o mouse](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **Passar o mouse**<br>
        Revelar um efeito de iluminação baseado em proximidade.
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
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>A indicação visual "anel" HoloLens 2<br>
        No HoloLens 2, há uma indicação visual extra, que pode ajudar a percepção de profundidade do usuário. Um anel próximo à ponta do dedo aparece e é escalado para baixo à medida que a ponta do dedo se aproxima do objeto. O anel eventualmente convergirá para um ponto quando o estado pressionado for atingido. Essa governança visual ajuda o usuário a entender a distância do objeto.<br>
        <br>
        *Loop de vídeo: exemplo de comentários visuais com base na proximidade de uma caixa delimitada*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Comentários visuais sobre proximidade da mão](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>Sinais de áudio

Para interações diretas com as mãos, os comentários de áudio adequados podem melhorar drasticamente a experiência do usuário. Use comentários de áudio para comunicar as seguintes dicas:
* **O contato começa:** reproduzir som quando o toque começa
* **Términos de contato:** reproduzir som no toque final
* **Início da captura:** reproduzir som quando a captura é iniciada
* **Extremidades de captura:** reproduzir som quando a captura termina

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>Comando de voz<br>
        Para qualquer objeto interajante, é importante dar suporte a opções de interação alternativas. Por padrão, recomendamos que os [comandos de](../out-of-scope/voice-design.md) voz sejam suportados para todos os objetos que são interajantes. Para melhorar a descoberta, você também pode fornecer uma dica de ferramenta durante o estado de foco.<br>
        <br>
        *Imagem: dica de ferramenta para o comando de voz*
    :::column-end:::
        :::column:::
       ![comandos de voz](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a>Recomendações de dimensionamento

Para garantir que todos os objetos que podem interagir possam ser facilmente tocadas, é recomendável garantir que os interajam com um tamanho mínimo com base na distância em que são colocados do usuário. O ângulo visual é geralmente medido em graus de arco Visual. O ângulo visual se baseia na distância entre os olhos do usuário e o objeto e permanece constante, enquanto o tamanho físico do destino pode mudar à medida que a distância do usuário é alterada. Para determinar o tamanho físico necessário de um objeto com base na distância do usuário, tente usar uma calculadora de ângulo visual como [esta](https://elvers.us/perception/visualAngle/).

Abaixo estão as recomendações para tamanhos mínimos de conteúdo de interação.

### <a name="target-size-for-direct-hand-interaction"></a>Tamanho de destino para interação direta

| Distância | Ângulo de exibição | Tamanho |
|---------|---------|---------|
| 45 cm  | Não é menor que 2 ° | 1,6 x 1,6 cm |

![Tamanho de destino para interação direta](images/TargetSizingNear.jpg)<br>
*Tamanho de destino para interação direta*

<br>

### <a name="target-size-for-buttons"></a>Tamanho de destino para botões

Ao criar botões para interação direta, recomendamos um tamanho mínimo maior de 3,2 x 3,2 cm para garantir que haja espaço suficiente para conter um ícone e potencialmente algum texto.

| Distância | Tamanho mínimo |
|---------|---------|
| 45 cm  | 3,2 x 3,2 cm |

![Tamanho do destino dos botões](images/TargetSizingButtons.png)<br>
*Tamanho do destino dos botões*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Tamanho de destino para interação de olhar
| Distância | Ângulo de exibição | Tamanho |
|---------|---------|---------|
| 2 m  | Não é menor que 1 ° | 3,5 x 3,5 cm |

![Tamanho de destino para interação de olhar](images/TargetSizingFar.jpg)<br>
*Tamanho de destino para interação de olhar*

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a>objeto de interação em MRTK (realidade misturada Toolkit) para o Unity

No **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, você pode usar o script de forma a [**interagir**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) para fazer com que os objetos respondam a vários tipos de Estados de interação de entrada. Ele dá suporte a vários tipos de temas que permitem definir estados visuais controlando Propriedades de objeto, como cor, tamanho, material e sombreador.

* [Interativo](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [Botão](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [Exemplos de interação de mão cena](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

O sombreador padrão de MixedRealityToolkit fornece várias opções, como a **luz de proximidade** que ajuda você a criar indicações visuais e de áudio.

* [Sombreador padrão MRTK](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

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