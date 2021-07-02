---
title: Ações de entrada
description: Documentação para criar ações de entrada no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, InputActions,
ms.openlocfilehash: cf6ce2af304ee1cd706d0111d66a97018113fb09
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176816"
---
# <a name="input-actions"></a>Ações de entrada

As [**ações de entrada**](input-actions.md) são abstrações sobre entradas brutas destinadas a ajudar a isolar a lógica do aplicativo das fontes de entrada específicas que produzem uma entrada. Pode ser útil, por exemplo, definir uma ação *Select* e mapeá-la para o botão esquerdo do mouse, um botão em um gamepad e um gatilho em um controlador 6 DOF. Em seguida, você pode fazer com que a lógica do aplicativo Ouça os *eventos de ação de entrada em* vez de ter que estar ciente de todas as diferentes entradas que podem produzir.

## <a name="creating-an-input-action"></a>Criando uma ação de entrada

as ações de entrada são configuradas no **perfil de ações de entrada**, dentro do perfil do sistema de *entrada* na realidade misturada Toolkit componente, especificando um nome para a ação e o tipo de entradas (*restrição de eixo*) para a qual ela pode ser mapeada:

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

Esses são os valores mais comumente usados para a **restrição de eixo**:

Restrição de eixo | Descrição
--- | ---
Digital | Entrada/saída como um botão binário em um gamepad ou mouse.
Eixo único | Entrada de análogo de eixo único como um gatilho analógico em um gamepad.
Eixo duplo | Entrada de análogo de eixo duplo como um Thumbstick.
Seis DOF | pose 3D com conversão e rotação como a produzida por 6 controladores DOF.

Você pode encontrar a lista completa no [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .

## <a name="mapping-input-to-actions"></a>Mapeando entrada para ações

A maneira como você mapeia uma entrada e uma ação depende do tipo da fonte de entrada:

### <a name="controller-input"></a>Entrada do controlador

Vá para o **perfil de mapeamento de entrada do controlador**, no *perfil do sistema de entrada*. Lá, você encontrará uma lista de todos os controladores com suporte:

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

Selecione aquele que você deseja configurar e uma janela de diálogo aparecerá com todas as entradas do controlador, permitindo que você defina uma ação para cada uma delas:

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a>Entrada de fala

No **perfil de comando de fala**, no *perfil do sistema de entrada*, você encontrará a lista de comandos de fala definidos no momento. Para mapear um deles para uma ação, basta selecioná-lo na lista suspensa *ação* .

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a>Entrada de gesto

O **perfil de gestos**, no *perfil do sistema de entrada*, contém todos os gestos definidos. Você pode mapear cada um deles para uma ação selecionando-o na lista suspensa *ação* .

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a>Manipulando ações de entrada

> [!WARNING]
> No momento, somente as ações de entrada do tipo *digital* podem ser tratadas usando os métodos descritos nesta seção. Para outros tipos de ação, você terá que manipular diretamente os eventos para as entradas correspondentes. Por exemplo, para manipular uma ação de 6 DOF mapeada para entradas de controlador, você precisará usar [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) with T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

A maneira mais fácil de lidar com as ações de entrada é usar o [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script. Isso permite que você defina a ação que deseja escutar e reaja a ações iniciadas e eventos encerrados usando eventos do Unity.

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

Se você quiser mais controle, poderá implementar a [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface diretamente no seu script. Consulte a seção [**eventos de entrada**](input-events.md) para obter mais detalhes sobre a manipulação de eventos por meio de interfaces de manipulador.

## <a name="examples"></a>Exemplos

Consulte `MRTK/Examples/Demos/Input/Scenes/InputActions` para ver uma cena de exemplo mostrando como criar uma ação, mapeá-la para entradas de controlador, fala e gesto e usá-la para girar um objeto no comando.

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
