---
title: Sistema principal
description: Sistema de entrada, gerenciadores de dispositivos e provedores de dados no MRTK
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Eventos
ms.openlocfilehash: ff4c23b796374940de1a1de6b72e08702d6fd24f79234e8ef80dc1210d13d103
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190170"
---
# <a name="core-system"></a>Sistema principal

No centro do sistema de entrada está o [InputSystem,](../features/input/overview.md)que é um serviço responsável por inicializar e operar toda a funcionalidade relacionada à entrada associada ao MRTK.

> [!NOTE]
> Supõe-se que os leitores já tenham lido e tenham uma compreensão básica da [seção de terminologia.](terminology.md)

Esse serviço é responsável por:

- Lendo o perfil [do sistema de entrada](../configuration/mixed-reality-configuration-guide.md#input-system-settings)
- Iniciando os provedores [de dados configurados](../features/input/input-providers.md) (por exemplo, `Windows Mixed Reality Device Manager` e `OpenVR Device Manager` ).
- Instalização do [GazeProvider,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider)que é um componente responsável por fornecer informações de olhar com o olhar com estilo HoloLens (1ª geração), além de informações de HoloLens de olhar com estilo 2.
- Instação do [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider), que é um componente responsável por determinar objetos que têm foco. Isso é descrito mais detalhadamente na seção [ponteiros e foco](controllers-pointers-and-focus.md#pointers-and-focus) da documentação.
- Fornecendo pontos de registro para todos os eventos de entrada (como [ouvintes globais).](#global-listeners)
- Fornecendo recursos de expedição de eventos para esses eventos de entrada.

## <a name="input-events"></a>Eventos de entrada

Eventos de entrada geralmente são acionados em dois canais diferentes:

### <a name="objects-in-focus"></a>Objetos em foco

Os eventos podem ser enviados diretamente para um GameObject que tem foco. Por exemplo, um objeto pode ter um script que implementa [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) .
Esse objeto obteria eventos de toque quando focalizado por uma mão próxima a ele. Esses tipos de eventos vão "para cima" na hierarquia GameObject até encontrar um GameObject capaz de manipular o evento.

Isso é feito usando [ExecuteHierarchy](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) de dentro da implementação padrão do sistema de entrada.

### <a name="global-listeners"></a>Ouvintes globais

Os eventos podem ser enviados para ouvintes globais. É possível registrar todos os eventos de entrada usando a interface do sistema de [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) entrada. É recomendável usar o método [RegisterHandler](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler%2A) para registrar eventos globais – a função preterida fará com que os ouvintes recebam notificados de TODOS os eventos de entrada, em vez de apenas eventos de entrada de um tipo específico (em que o tipo é definido pela interface de `Register` evento).

Observe que [os ouvintes de fallback](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler%2A) são outro tipo de ouvintes globais que também não são desencorajados porque receberão todos os eventos de entrada que não foram tratados em outro lugar na cena.

### <a name="order-of-event-dispatch"></a>Ordem de expedição de eventos

Em geral, os eventos são enviados aos ouvintes da seguinte maneira. Observe que, se qualquer uma das etapas abaixo marcar o evento como [manipulado,](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html)o processo de expedição de eventos será interrompido.

1. O evento é enviado para ouvintes globais.
2. O evento é enviado para caixas de diálogo modais do objeto focalizado.
3. O evento é enviado para o objeto focalizado.
4. O evento é enviado para ouvintes de fallback.

## <a name="device-managers-and-data-providers"></a>Gerenciadores de dispositivos e provedores de dados

Essas entidades são responsáveis por intercalar com APIs de nível inferior (como APIs do Windows Mixed Reality ou APIs OpenVR) e traduzir dados desses sistemas em aqueles que se ajustam às abstrações de entrada de nível superior do MRTK. Eles são responsáveis por detectar, criar e gerenciar o tempo de vida [dos controladores](controllers-pointers-and-focus.md#controllers).

O fluxo básico de um gerenciador de dispositivos envolve:

1. O gerenciador de dispositivos é instanciado pelo serviço de sistema de entrada.
2. O gerenciador de dispositivos registra-se com seu sistema subjacente (por [](../features/input/input-events.md) exemplo, Windows Mixed Reality gerenciador de dispositivos registrará eventos de entrada [e](../features/input/gestures.md#gesture-events) gesto.
3. Ele cria controladores que descobre do sistema subjacente (por exemplo, o provedor pode detectar a presença de mãos articuladas)
4. Em seu loop Update(), chame UpdateController() para sondar o novo estado do sistema subjacente e atualizar sua representação do controlador.
