---
title: Manipulador de manipulação
description: Documentação sobre manipulador de manipulação no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Manipulação,
ms.openlocfilehash: 24034c43bf8ce1f1ef463e894e9ca5293c2b0d2a146284535b161f8b4277dfa9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190190"
---
# <a name="manipulation-handler"></a>Manipulador de manipulação

![Manipulador de manipulação](../images/manipulation-handler/MRTK_Manipulation_Main.png)

O script *ManipulationHandler* permite que um objeto se deixe móvel, escalonável e rotatável usando uma ou duas mãos. A manipulação pode ser restrita para permitir apenas determinados tipos de transformação. O script funciona com vários tipos de entradas, incluindo HoloLens entrada de mão articulada 2, raios de mão, entrada de gesto HoloLens (1ª geração) e entrada do controlador de movimento do headset imersivo.

## <a name="how-to-use-the-manipulation-handler"></a>Como usar o manipulador de manipulação

Adicione o `ManipulationHandler` componente de script a um GameObject. Certifique-se também de adicionar um colisor ao objeto, correspondendo aos seus limites que podem ser capturados.

Para fazer com que o objeto responda à entrada de mão quase articulada, adicione `NearInteractionGrabbable` o script também.

![Usando o manipulador de manipulação no editor do Unity](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a>Propriedades do inspetor

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

**Transformação host** Transformação que será arrastada. Assume como padrão o objeto do componente.

**Tipo de manipulação** Especifica se o objeto pode ser manipulado usando uma mão, duas mãos ou ambas.

* *Somente uma mão*
* *Somente duas mãos*
* *Uma e duas mãos*

**Tipo de manipulação de duas mãos**

* *Escala:* somente o dimensionamento é permitido.
* *Girar:* somente a rotação é permitida.
* *Escala de movimentação:* a movimentação e o dimensionamento são permitidos.
* *Mover Girar:* mover e girar é permitido.
* *Girar Escala:* rotação e dimensionamento são permitidos.
* *Mover Escala de Rotação:* é permitido mover, girar e dimensionar.

![Manipulador de manipulação](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

**Permitir manipulação distante** Especifica se a manipulação pode ser feita usando interação distante com ponteiros.

**Modo de rotação de uma mão próximo** Especifica como o objeto se comportará quando estiver sendo capturado com uma mão/controlador próximo.

**Modo de rotação de uma mão distante** Especifica como o objeto se comportará quando estiver sendo capturado com uma mão/controlador à distância.

**Opções de modo de rotação de uma mão** Especifica como o objeto girará quando estiver sendo capturado com uma mão.

* *Manter a rotação original:* não gira o objeto conforme ele está sendo movido
* *Manter a rotação para* o usuário: mantém a rotação original do objeto para o eixo X/Y para o usuário
* *A gravidade alinhada mantém a rotação para o* usuário: mantém a rotação original do objeto para o usuário, mas torna o objeto vertical. Útil para objetos com um controle de limites.
* *Usuário de face:* garante que o objeto sempre enfrenta o usuário. Útil para slates/painéis.
* *Face para fora do usuário:* garante que o objeto sempre se desdonte do usuário. Útil para slates/painéis configurados para trás.
* *Girar sobre o centro de objetos:* funciona apenas para mãos/controladores articulados. Girar o objeto usando a rotação da mão/controlador, mas sobre o ponto central do objeto. Útil para inspecionar à distância.
* *Girar sobre o ponto de captura:* funciona apenas para mãos/controladores articulados. Gire o objeto como se estivesse sendo mantido pela mão/controlador. Útil para inspeção.

**Comportamento da versão** Quando um objeto é liberado, especifique seu comportamento de movimento físico. Requer um componente rigidbody para estar nesse objeto.

* *Nothing*
* *Tudo*
* *Manter a velocidade*
* *Manter Angular velocidade*

**Restrições na rotação** Especifica em qual eixo o objeto girará quando interagido.

* *Nenhuma*
* *Somente eixo X*
* *Somente eixo Y*
* *Somente eixo Z*

**Usar espaço local para restrição** Uma alternância para alternar entre a aplicação de restrições em relação ao eixo de espaço do mundo ou eixo de espaço local.

**Restrições de movimentação**

* *Nenhuma*
* *Corrigir a distância da cabeça*

**Suavização ativa** Especifica se a suavização está ativa.

**Suavizando a quantidade uma mão** Quantidade de suavização a ser aplicada à movimentação, escala, rotação. Suavização de 0 significa nenhuma suavização. Valor máximo significa nenhuma alteração no valor.

## <a name="events"></a>Eventos

O manipulador de manipulação fornece os seguintes eventos:

* *OnManipulationStarted:* acionado quando a manipulação é iniciada.
* *OnManipulationEnded:* é a incêndio quando a manipulação termina.
* *OnHoverStarted:* é a incêndio quando uma mão/controlador passar o mouse no manipulador, próximo ou distante.
* *OnHoverEnded:* é a incêndio quando uma mão/controlador destoca o manipulador, próximo ou distante.
