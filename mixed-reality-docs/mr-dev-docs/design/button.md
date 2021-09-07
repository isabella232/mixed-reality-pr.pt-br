---
title: Botão
description: Saiba como disparar uma ação imediata com botões, que é um dos componentes fundamentais da realidade misturada.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: realidade misturada, controles, interação, interface do usuário, ux, headset de realidade misturada, headset da realidade mista do windows, headset da realidade virtual, HoloLens, MRTK, realidade misturada Toolkit, botão
ms.openlocfilehash: 4b3a9bda852c7a83ee603c3f2340d44f4be89f4d
ms.sourcegitcommit: 4f1697b11e5638db9bbd0bd7a671d846d54c6389
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2021
ms.locfileid: "122682958"
---
# <a name="button"></a>Botão

![Botão](images/UX_Hero_Button.jpg)

Um botão é um dos elementos mais fundamentais e cruciais da interface do usuário em realidade misturada. Permite que os usuários disparem ações imediatas. Como não há nenhum comentário físico em realidade misturada, é crucial fornecer comentários visuais e de áudio suficientes para aumentar a confiança da interação do usuário. 

no design de botão HoloLens 2, com base em muitas iterações de design, protótipos e estudos de pesquisa de usuário, integramos várias capacidades visuais e indicações de áudio que ajudam a percepção de profundidade e a interação do usuário em um espaço vazio. 

## <a name="visual-affordances"></a>Capacidades Visual

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWJHgW]


:::row:::
    :::column:::
       ![Botão com efeito de luz de proximidade mostrado](images/UX_Button_Affordance_ProximityLight.jpg)<br>
       **Luz de proximidade**<br>
    :::column-end:::
    :::column:::
       ![Botão selecionado com o efeito de realce de foco mostrado](images/UX_Button_Affordance_FocusHighlight.jpg)<br>
        **Realce de foco**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Botão sendo pressionado com o efeito de compartimento de compactação mostrado](images/UX_Button_Affordance_Compression.jpg)<br>
       **Compactando o compartimento**<br>
    :::column-end:::
    :::column:::
       ![Botão sendo pressionado com efeito de pulso de gatilho mostrado](images/UX_Button_Affordance_Pulse.jpg)<br>
        **Pulso no gatilho**<br>
    :::column-end:::
:::row-end:::

<br>

## <a name="audio-cues"></a>Indicações de áudio

Os comentários de áudio adequados podem melhorar drasticamente a experiência do usuário. HoloLens botão 2 fornece comentários de áudio para comunicar as seguintes indicações:
* **Contato começa**: reproduzir som quando o toque começar (próximo à interação)
* **Contatos termina**: reproduzir som no ponto de toque (próxima interação)
* **Começa a pinçar**: reproduzir som em pinçar seleção (interação extrema com olhar ou raios)
* **Extremidades de pinçagem**: reproduzir som na versão de pinçagem (interação extrema com olhar ou raios)

<br>

---

:::row:::
    :::column:::
        ## <a name="voice-commandingbr"></a>Comando de voz<br>
        Para qualquer botão em realidade misturada, é importante dar suporte a opções de interação alternativas. Por padrão, recomendamos que os comandos de voz tenham suporte para botões. no design de botão de HoloLens 2, fornecemos uma dica de ferramenta durante o estado de foco para melhorar a capacidade de descoberta.
    :::column-end:::
        :::column:::
       ![Entrada de voz](images/UX_Hero_VoiceCommand.jpg)<br>
        *Imagem: dica de ferramenta para o comando de voz*
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

## <a name="design-guidelines"></a>Diretrizes de design

### <a name="avoid-transparent-backplate"></a>Evitar placa traseira transparente
Ao criar a interface do usuário do menu com botões, é recomendável usar a chapa traseira opaca. As chapas de backtransparente não são recomendadas pelos seguintes motivos:
* Difícil de interagir, pois é difícil entender quanto profundidade o botão precisa ser pressionado para disparar o evento
* Problema de legibilidade em um ambiente físico complexo
* Hologramas exibidas por meio da chapa transparente podem mostrar um problema de efeito incompleto quando usado com a tecnologia de estabilização LSR de profundidade.

Consulte [Designing Content for Holographic display](designing-content-for-holographic-display.md) para obter mais detalhes sobre as opções e diretrizes de cores para a exibição do Holographic.

![Exemplos de interface do usuário transparente exemplos ](images/color_transparent_examples.jpg)
 *de placa traseira da interface do usuário transparente*

<br>

### <a name="use-shared-backplate"></a>Usar placa traseira compartilhada
Para vários botões, é recomendável usar a chapa traseira compartilhada em vez da placa traseira do botão individual.

* Reduzir o ruído e a complexidade do Visual
* Limpar agrupamento  

![Exemplos de placa traseira compartilhada ](images/Button_Design_SharedBackplate.png
)
 *exemplos de placa traseira da interface do usuário compartilhada*

<br>

---

## <a name="button-in-mrtk-mixed-reality-toolkit"></a>Botão em MRTK (realidade misturada Toolkit)
**[MRTK para Unity](/windows/mixed-reality/mrtk-unity/)** e **[MRTK para inreal](/windows/mixed-reality/develop/unreal/unreal-mrtk-introduction)** fornecem vários tipos de pré-fabricados de botão, incluindo botões de estilo HoloLens 2. o componente de botão HoloLens 2 contém todos os comentários visuais e detalhes de interação que foram introduzidos nesta página. Ao usá-lo, você pode aproveitar o resultado de várias iterações de design e pesquisa de usuário que nossos designers, desenvolvedores, pesquisadores realizaram.

Confira o [botão MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) para obter mais instruções e exemplos personalizados.

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