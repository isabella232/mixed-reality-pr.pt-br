---
title: Controle deslizante
description: Visão geral dos controles deslizantes MRTK
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, controles deslizantes,
ms.openlocfilehash: be19806e0202f6cb3ddcea1a80c2c40811aff4f2
ms.sourcegitcommit: e9661d3bab061f9499134226ef3b87751ec56277
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112426872"
---
# <a name="sliders"></a>Controles deslizantes

![Exemplo de Slider](../images/slider/MRTK_UX_Slider_Main.jpg)

Os controles deslizantes são componentes de interface do usuário que permitem que você altere continuamente um valor movendo um controle deslizante em uma faixa. Atualmente, o controle deslizante pinça pode ser movido por meio da captura direta do controle deslizante, seja diretamente ou em uma distância. Os controles deslizantes funcionam em AR e VR, usando controladores de movimento, mãos ou gesto + voz.

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar exemplos na cena **SliderExample** em `MRTK/Examples/Demos/UX/Slider/Scenes/` .

## <a name="how-to-use-sliders"></a>Como usar controles deslizantes

Arraste e solte o **PinchSlider** pré-fabricado na hierarquia de cena. Se você quiser modificar ou criar seu próprio controle deslizante, lembre-se de fazer o seguinte:

- Verifique se o seu objeto Thumb tem um colisor nele. No PinchSlider pré-fabricado, o colisor está ligado `SliderThumb/Button_AnimationContainer/Slider_Button`
- Certifique-se de que o objeto que contém o colisor também tenha um componente que pode ser captado pela interação, se você quiser conseguir obter o controle deslizante próximo.

Também é recomendável usar a seguinte hierarquia

- PinchSlider-contém o sliderComponent
  - TouchCollider-colisor que contém a área selecionável inteira do controle deslizante. Habilita o comportamento de ajustar à posição.
  - SliderThumb-contém o Thumb móvel
  - TrackVisuals-contendo a faixa e quaisquer outros visuais
  - OtherVisuals-contendo quaisquer outros visuais

## <a name="slider-events"></a>Eventos Slider

Os controles deslizantes expõem os seguintes eventos:

- OnValueUpdated – chamado sempre que o valor do controle deslizante é alterado
- OnInteractionStarted – chamado quando o usuário captura o controle deslizante
- OnInteractionEnded – chamado quando o usuário libera o controle deslizante
- OnHoverEntered – chamado quando a mão/controlador do usuário passa o mouse sobre o controle deslizante, usando interação próxima ou extrema.
- OnHoverExited – chamado quando a mão/controlador do usuário não está mais próximo do controle deslizante.

## <a name="configuring-slider-bound-and-axis"></a>Configurando eixo e limite do controle deslizante

Você pode mover diretamente os pontos inicial e final do controle deslizante movendo as alças na cena:

![Configuração de controles deslizantes](../images/sliders/MRTK_Sliders_Setup.png)

Você também pode especificar o eixo (no espaço local) do controle deslizante por meio do campo _eixo do controle deslizante_

Se você não puder usar as alças, poderá especificar os pontos inicial e final do controle deslizante por meio dos campos distância de _início_ do controle deslizante e _distância de término do controle_ deslizante. Elas especificam a posição inicial/final do controle deslizante como uma distância do centro do controle deslizante, em coordenadas locais. Isso significa que, depois de definir as distâncias de início e término do controle deslizante conforme desejado, você pode dimensionar o controle deslizante para ser menor ou maior sem a necessidade de atualizar as distâncias de início e término.

## <a name="inspector-properties"></a>Propriedades do Inspetor

**Raiz do polegar** O gameobject que contém a miniatura do slider.

**Ajustar à posição** Se este controle deslizante se ajusta à posição designada no controle deslizante

**É tocável** Se esse controle deslizante é controlável por meio de eventos de toque

**Colisor de polegar** O colisor que controla o controle deslizante Thumb

**Colisor tocável** A área do controle deslizante que pode ser tocada ou selecionado quando ajustar à posição for verdadeiro.

**Valor do controle deslizante** O valor do controle deslizante.

**Usar divisões de etapa do controle deslizante** Controla se esse controle deslizante é incrementado em etapas ou continuamente.

**Divisões da etapa do controle deslizante** Número de subdivisãos em que o controle deslizante é dividido quando o uso de divisões de etapa de controle deslizante está habilitado.

**Acompanhar visuais** O gameobject que contém os visuais de faixa desejados que acompanham o controle deslizante.

**Marcas de escala** O gameobject que contém as marcas de escala desejadas que vão ao longo do controle deslizante.

**Visuais Thumb** O gameobject que contém o Visual de miniatura desejado que acompanha o controle deslizante.

**Eixo do controle deslizante** O eixo no qual o controle deslizante se move.

**Distância de início do controle deslizante** Em que a faixa do controle deslizante começa, como distância do centro do slider ao longo do eixo, em unidades de espaço local.

**Distância de extremidade do controle deslizante** Em que a faixa do controle deslizante termina, como distância do centro do controle deslizante, em unidades de espaço local.

Quando o usuário atualizar o valor do eixo do controle deslizante no editor, então, se rastrear visuais ou visuais de tique forem especificados, a transformação será atualizada.
Especificamente, sua posição local é redefinida e sua rotação local é definida para corresponder à orientação do eixo do controle deslizante.
Sua escala não é modificada.
Se as marcas de escala tiverem um componente de coleção de objetos de grade, o layout e o CellWidth ou CellHeight serão atualizados adequadamente para corresponder ao eixo do controle deslizante.

## <a name="example-slider-configurations"></a>Configurações de controle deslizante de exemplo

Controles deslizantes contínuos com snap para posicionar ![ controles deslizantes contínuos](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)

Deslizantes de etapa com ajustar à posição

![Deslizantes de etapa](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

Controles deslizantes de toque

![Controles deslizantes de toque](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)