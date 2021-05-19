---
title: Ações de entrada
description: Documentação para criar ações de entrada no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, InputActions,
ms.openlocfilehash: 071d4bc8bb4193a3d60cb53852c192ae975d79df
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144152"
---
# <a name="input-actions"></a>Ações de entrada

[**As Ações de**](input-actions.md) Entrada são abstrações sobre entradas brutas destinadas a ajudar a isolar a lógica do aplicativo das fontes de entrada específicas que produzem uma entrada. Pode ser útil, por exemplo,  definir uma ação Selecionar e mapeá-la para o botão esquerdo do mouse, um botão em um gamepad e um gatilho em um controlador de 6 DOF. Em seguida, você pode fazer com que a lógica do aplicativo escute *selecionar* eventos de ação de entrada em vez de ter que estar ciente de todas as diferentes entradas que podem produzi-los.

## <a name="creating-an-input-action"></a>Criando uma ação de entrada

As ações de entrada são configuradas  no Perfil de Ações de Entrada **,** dentro do Perfil do Sistema de Entrada no componente Kit de Ferramentas de Realidade Misturada, especificando um nome para a ação e o tipo de entradas *(* Restrição do Eixo ) para o qual ele pode ser mapeado:

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

Estes são os valores mais comumente usados para **Restrição de Eixo:**

Restrição de eixo | Descrição
--- | ---
Digital | Entrada ligar/desligar como um botão binário em um gamepad ou mouse.
Eixo único | Entrada de eixo único como um gatilho análogo em um gamepad.
Eixo duplo | Entrada de eixo duplo, como um thumbstick.
Seis Dof | Pose 3D com conversão e rotação como aquela produzida por 6 controladores DOF.

Você pode encontrar a lista completa em [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .

## <a name="mapping-input-to-actions"></a>Mapeando a entrada para ações

A maneira como você mapeia uma entrada para a ação e depende do tipo da fonte de entrada:

### <a name="controller-input"></a>Entrada do controlador

Vá para o Perfil **de Mapeamento de Entrada do Controlador,** no Perfil do Sistema de *Entrada*. Lá, você encontrará uma lista de todos os controladores com suporte:

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

Selecione aquela que você deseja configurar e uma janela de diálogo será exibida com todas as entradas do controlador, permitindo que você de definir uma ação para cada uma delas:

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a>Entrada de fala

No Perfil **de Comando de Fala**, no Perfil do Sistema de *Entrada*, você encontrará a lista de comandos de fala definidos no momento. Para mapear um deles para uma ação, basta selecioná-lo *na* lista lista de ações.

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a>Entrada de gesto

O **Perfil de Gestos**, no Perfil *do Sistema de Entrada*, contém todos os gestos definidos. Você pode mapear cada um deles para uma ação selecionando-a *na* lista de lista de ações.

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a>Manipulando ações de entrada

> [!WARNING]
> Atualmente, somente as ações de entrada *do tipo Digital* podem ser tratadas usando os métodos descritos nesta seção. Para outros tipos de ação, você terá que manipular diretamente os eventos para as entradas correspondentes. Por exemplo, para lidar com uma ação de 6 DOF mapeada para entradas do controlador, você terá que usar [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) com T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

A maneira mais fácil de lidar com ações de entrada é usar o [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script. Isso permite que você defina a ação que deseja escutar e reagir a eventos iniciados e encerrados usando eventos do Unity.

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

Se você quiser mais controle, poderá implementar a [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface diretamente em seu script. Consulte a [**seção Eventos de Entrada**](input-events.md) para obter mais detalhes sobre a manipulação de eventos por meio de interfaces de manipulador.

## <a name="examples"></a>Exemplos

Consulte para ver uma cena de exemplo mostrando como criar uma ação, mapeá-la para entradas de controlador, fala e gesto e usá-la para girar um `MRTK/Examples/Demos/Input/Scenes/InputActions` objeto no comando .

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
