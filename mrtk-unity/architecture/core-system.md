---
title: Sistema principal
description: Sistema de entrada, gerenciadores de dispositivos e provedores de dados no MRTK
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, eventos
ms.openlocfilehash: 79ebd3855cd991db168233f00058ab5d42f87d83
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121594"
---
# <a name="core-system"></a>Sistema principal

No coração do sistema de entrada está o [InputSystem](../features/input/overview.md), que é um serviço que é responsável por inicializar e operar toda a funcionalidade relacionada à entrada associada ao MRTK.

> [!NOTE]
> Supõe-se que os leitores já tenham lido e tenham uma compreensão básica da seção [terminologia](terminology.md) .

Este serviço é responsável por:

- Lendo o [perfil do sistema de entrada](../configuration/mixed-reality-configuration-guide.md#input-system-settings)
- Iniciando os [provedores de dados](../features/input/input-providers.md) configurados (por exemplo, `Windows Mixed Reality Device Manager` e `OpenVR Device Manager` ).
- Instanciação do [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider), que é um componente que é responsável por fornecer informações de olhar de cabeçalho do hololens (1ª geração), além de informações de olhar de olho no estilo do hololens 2.
- Instanciação do [focusprovider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider), que é um componente que é responsável pela determinação de objetos que têm foco. Isso é descrito mais detalhadamente na seção [ponteiros e foco](controllers-pointers-and-focus.md#pointers-and-focus) da documentação.
- Fornecer pontos de registro para todos os eventos de entrada (como [ouvintes globais](#global-listeners)).
- Fornecendo recursos de expedição de eventos para esses eventos de entrada.

## <a name="input-events"></a>Eventos de entrada

Eventos de entrada geralmente são acionados em dois canais diferentes:

### <a name="objects-in-focus"></a>Objetos em foco

Os eventos podem ser enviados diretamente a um gameobject que tenha foco. Por exemplo, um objeto pode ter um script que implementa [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) .
Esse objeto receberá eventos de toque quando estiver concentrado em uma mão que está perto dele. Esses tipos de eventos passam "para cima" a hierarquia gameobject até encontrar um gameobject capaz de lidar com o evento.

Isso é feito usando [ExecuteHierarchy](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) de dentro da implementação do sistema de entrada padrão.

### <a name="global-listeners"></a>Ouvintes globais

Os eventos podem ser enviados para ouvintes globais. É possível registrar-se para todos os eventos de entrada usando a interface do sistema de entrada [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) . É recomendável usar o método [RegisterHandler](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler%2A) para o registro de eventos globais – a função preterida fará com que os `Register` ouvintes sejam notificados de todos os eventos de entrada, em vez de apenas eventos de entrada de um tipo específico (em que Type é definido pela interface de evento).

Observe que os [ouvintes de fallback](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler%2A) são outro tipo de ouvintes globais que também são desencorajados, pois eles receberão todos os eventos de entrada únicos que não foram tratados em outro lugar na cena.

### <a name="order-of-event-dispatch"></a>Ordem de expedição do evento

Em geral, os eventos são enviados aos ouvintes da seguinte maneira. Observe que, se qualquer uma das etapas abaixo marcar o evento como [manipulado](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html), o processo de expedição do evento será interrompido.

1. O evento é enviado para ouvintes globais.
2. O evento é enviado para caixas de diálogo modais do objeto focalizado.
3. O evento é enviado para o objeto focalizado.
4. O evento é enviado aos ouvintes de fallback.

## <a name="device-managers-and-data-providers"></a>Gerenciadores de dispositivos e provedores de dados

Essas entidades são responsáveis pela interface com APIs de nível inferior (como APIs de realidade mista do Windows ou APIs OpenVR) e pela conversão de dados desses sistemas em aquelas que se ajustam às abstrações de entrada de nível superior do MRTK. Eles são responsáveis por detectar, criar e gerenciar o tempo de vida dos [controladores](controllers-pointers-and-focus.md#controllers).

O fluxo básico de um Gerenciador de dispositivos envolve:

1. O Gerenciador de dispositivos é instanciado pelo serviço do sistema de entrada.
2. O Gerenciador de dispositivos se registra com seu sistema subjacente (por exemplo, o Gerenciador de dispositivos do Windows Mixed Reality será registrado para eventos de [entrada](../features/input/input-events.md) e de [gesto](../features/input/gestures.md#gesture-events) .
3. Ele cria controladores que ele descobre do sistema subjacente (por exemplo, o provedor pode detectar a presença de mãos articuladas)
4. Em seu loop Update (), chame UpdateController () para sondar o novo estado do sistema subjacente e atualizar sua representação do controlador.
