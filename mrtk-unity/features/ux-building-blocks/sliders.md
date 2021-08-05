---
title: Controles deslizantes
description: Visão geral do MRTK dos controles deslizantes
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, controles deslizantes,
ms.openlocfilehash: de95201f381a148defe668ead03c16fac5b3ba4ff3674487057f9227cbe6efba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209526"
---
# <a name="sliders"></a>Controles deslizantes

![Exemplo de controle deslizante](../images/slider/MRTK_UX_Slider_Main.jpg)

Controles deslizantes são componentes da interface do usuário que permitem alterar continuamente um valor movendo um controle deslizante em uma faixa. Atualmente, o Controle Deslizante de Pinçar pode ser movido ao segurar diretamente o controle deslizante, diretamente ou à distância. Os controles deslizantes funcionam em AR e VR, usando controladores de movimento, mãos ou Gesto + Voz.

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar exemplos na cena **SliderExample** em `MRTK/Examples/Demos/UX/Slider/Scenes/` .

## <a name="how-to-use-sliders"></a>Como usar controles deslizantes

Arraste e solte o pré-fab **PinchSlider** na hierarquia de cena. Se você quiser modificar ou criar seu próprio controle deslizante, lembre-se de fazer o seguinte:

- Certifique-se de que seu objeto thumb tenha um colisor nele. No pré-fab PinchSlider, o colisor está em `SliderThumb/Button_AnimationContainer/Slider_Button`
- Certifique-se de que o objeto que contém o colisor também tenha um componente Grabbable de Interação Próxima, se você quiser ser capaz de segurar o controle deslizante próximo.

Também é recomendável usar a hierarquia a seguir

- PinchSlider – contém o controle deslizanteComponent
  - TouchCollider – Colisor que contém toda a área selecionável do controle deslizante. Habilita o comportamento de Ajustar à Posição.
  - SliderThumb – contém o thumb removível
  - TrackVisuals – contendo a faixa e quaisquer outros visuais
  - OtherVisuals – contendo outros visuais

## <a name="slider-events"></a>Eventos do controle deslizante

Os controles deslizantes expõem os seguintes eventos:

- OnValueUpdated – chamado sempre que o valor do controle deslizante for alterando
- OnInteractionStarted – chamado quando o usuário captura o controle deslizante
- OnInteractionEnded – chamado quando o usuário libera o controle deslizante
- OnHoverEntered – chamado quando a mão/controlador do usuário se sobrecarra sobre o controle deslizante, usando interação próxima ou distante.
- OnHoverExited – chamado quando a mão/controlador do usuário não está mais perto do controle deslizante.

## <a name="configuring-slider-bound-and-axis"></a>Configurando o eixo e o limite do controle deslizante

Você pode mover diretamente os pontos inicial e final do controle deslizante movendo as alças na cena:

![Configuração de controle deslizante](../images/sliders/MRTK_Sliders_Setup.png)

Você também pode especificar o eixo (no espaço local) do controle deslizante por meio do _campo Eixo do Controle_ Deslizante

Se você não puder usar os alças, poderá especificar os pontos  inicial e final do controle deslizante por meio dos campos Distância inicial do controle deslizante e Distância final do controle _deslizante._ Eles especificam a posição inicial/final do controle deslizante como uma distância do centro do controle deslizante, em coordenadas locais. Isso significa que, depois de definir as distâncias de início e término do controle deslizante conforme você quiser, você poderá dimensionar o controle deslizante para ser menor ou maior sem a necessidade de atualizar as distâncias inicial e final.

## <a name="inspector-properties"></a>Propriedades do inspetor

**Raiz do thumb** O gameobject que contém o controle deslizante.

**Ajustar à posição** Se esse controle deslizante se encaixa ou não na posição designada no controle deslizante

**É sensível ao toque** Se esse controle deslizante é ou não controlável por meio de eventos de toque

**Colisor de miniatura** O colisor que controla o controle deslizante

**Colisor sensível ao toque** A área do controle deslizante que pode ser tocada ou selecionada quando Ajustar à Posição é verdadeira.

**Valor do controle deslizante** O valor do controle deslizante.

**Usar divisões de etapa do controle deslizante** Controla se esse controle deslizante é incrementado em etapas ou continuamente.

**Divisões de etapa do controle deslizante** Número de subdivisões em que o controle deslizante é dividido quando Usar Divisões de Etapa do Controle Deslizante está habilitado.

**Acompanhar visuais** O gameobject que contém os visuais de faixa desejados que acompanham o controle deslizante.

**Marcas de escala** O gameobject que contém as marcas de escala desejadas que acompanham o controle deslizante.

**Visuais de miniatura** O gameobject que contém o visual de miniatura desejado que acompanha o controle deslizante.

**Eixo do controle deslizante** O eixo que o controle deslizante se move.

**Distância de início do controle deslizante** Onde a faixa do controle deslizante é iniciada, como distância do centro ao longo do eixo do controle deslizante, em unidades de espaço local.

**Distância final do controle deslizante** Onde a faixa do controle deslizante termina, como distância do centro ao longo do eixo do controle deslizante, em unidades de espaço local.

Quando o usuário atualiza o valor do eixo do controle deslizante no editor, se Os Visuais de Faixa ou Visuais de Escala são especificados, sua transformação é atualizada.
Especificamente, sua posição local é redefinida e sua rotação local é definida para corresponder à orientação do eixo deslizante.
Sua escala não é modificada.
Se As Marcas de Escala têm um componente coleção de objetos de grade, o Layout e CellWidth ou CellHeight são atualizados de acordo para corresponder ao eixo do controle deslizante.

## <a name="example-slider-configurations"></a>Exemplo de configurações do controle deslizante

Controles deslizantes contínuos com controles deslizantes contínuos de ![ ajustar à posição](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)

Controles deslizantes de etapa com ajustar à posição

![Controles deslizantes de etapa](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

Controles deslizantes de toque

![Controles deslizantes de toque](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)
