---
title: Visão geral da entrada
description: Visão geral do sistema de entrada no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: b175b16e2004fb00cef430335751c3aabc8c59fdd4ae78a2fc78c959a92240fb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219742"
---
# <a name="input-overview"></a>Visão geral da entrada

O sistema de entrada no MRTK permite que você:

- Consumir entradas de uma variedade de fontes de entrada, como 6 controladores DOF, mãos articuladas ou fala, por meio de eventos de entrada.
- Defina ações abstratas, *como Selecionar* *ou Menu,* e associá-las a entradas diferentes.
- Ponteiros de instalação anexados aos controladores para conduzir componentes da interface do usuário por meio de eventos de foco e ponteiro.

<img src="../images/input/MRTK_InputSystem.png" alt="Input System" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Visão geral do sistema de entrada do MRTK</sup>

As entradas são produzidas por provedores de [**dados de entrada (Gerenciador de Dispositivos)**](input-providers.md). Cada provedor corresponde a uma fonte específica de entrada: OPEN VR, Windows Mixed Reality (WMR), Unity Windows Speech etc. Os provedores são **adicionados** ao projeto por  meio do Perfil de Provedores de Serviços Registrados no componente Toolkit de Realidade Misturada e produzirão Eventos de Entrada automaticamente quando as fontes de entrada correspondentes estão disponíveis (por exemplo, quando um controlador WMR é detectado ou um gamepad conectado). [](input-events.md)

[**As Ações de**](input-actions.md) Entrada são abstrações sobre entradas brutas destinadas a ajudar a isolar a lógica do aplicativo das fontes de entrada específicas que produzem uma entrada. Pode ser útil, por exemplo,  definir uma ação Selecionar e mapeá-la para o botão esquerdo do mouse, um botão em um gamepad e um gatilho em um controlador de 6 DOF. Em seguida, você pode fazer com que a lógica do aplicativo escute *selecionar* eventos de ação de entrada em vez de ter que estar ciente de todas as diferentes entradas que podem produzi-los. As ações de entrada são definidas no **Perfil de Ações de Entrada**, encontrado no Perfil *do* Sistema de Entrada no componente *Toolkit* Realidade Misturada.

[**Os controladores**](controllers.md) são criados por *provedores de* entrada quando os dispositivos de entrada são detectados e destruídos quando eles são perdidos ou desconectados. O provedor de entrada WMR, por exemplo, criará controladores WMR para 6 *dispositivos* DOF e controladores de mão articulados *wmR* para mãos articuladas. As entradas do controlador podem ser mapeadas para ações de entrada por meio do Perfil de Mapeamento **do Controlador**, dentro do Perfil do Sistema *de Entrada*. Os eventos de entrada gerados pelos controladores incluirão a ação de entrada associada, se for o caso.

Os controladores podem ter [**ponteiros**](pointers.md) anexados a eles que consultam a cena para determinar o objeto do jogo com foco e aufocar Eventos [**de**](pointers.md#pointer-event-interfaces) Ponteiro nele. Por exemplo, nosso *ponteiro de* linha executa um raycast na cena usando a pose do controlador para calcular a origem e a direção do raio. Os ponteiros criados para cada controlador são definidos no Perfil **de Ponteiro,** no Perfil *do Sistema de Entrada*.

<img src="../images/input/MRTK_Input_EventFlow.png" width="200px" alt="Event Flow" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Fluxo de eventos.</sup>

Embora você possa manipular eventos de entrada diretamente nos [componentes](input-events.md)da interface do usuário, é recomendável usar eventos de ponteiro [para](pointers.md#pointer-event-interfaces) manter a implementação independente do dispositivo.

O MRTK também fornece vários métodos de conveniência para consultar o estado de entrada diretamente de uma maneira independente do dispositivo. Consulte [Acessando o estado de entrada no MRTK](input-state.md) para obter mais detalhes.
