---
title: Guia de porta do HTK para o MRTK
description: Migração do HoloLens Toolkit (HTK) para o MRTK (Kit de Ferramentas de Realidade Misturada).
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, HTK,
ms.openlocfilehash: fbcb2863c894a4e4c1529e19112b33712f69e99f
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143766"
---
# <a name="porting-guide"></a>Guia de portabilidade

Um guia para ajudá-lo com a migração do HTK (Kit de Ferramentas do HoloLens) para o MRTK (Kit de Ferramentas de Realidade Misturada).

## <a name="controller-and-hand-input"></a>Controlador e entrada manual

### <a name="setup-and-configuration"></a>Instalação e configuração

|         Métodos                  | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Tipo                      | Eventos específicos para botões, com informações de tipo de entrada quando relevantes. | Entrada baseada em ação/gesto, passada por meio de eventos. |
| Instalação                     | Coloque o InputManager na cena. | Habilita o sistema de entrada no [Perfil de Configuração](../configuration/mixed-reality-configuration-guide.md) e especifique um tipo de sistema de entrada concreta. |
| Configuração             | Configurado no Inspetor, em cada script individual na cena. | Configurado por meio do Perfil do Sistema de Entrada de Realidade Misturada e seu perfil relacionado, listado abaixo. |

Perfis relacionados:

* Perfil de mapeamento do controlador de realidade misturada
* Perfil de visualização do Controlador de Realidade Misturada
* Perfil de Gestos de Realidade Misturada
* Perfil de ações de entrada de realidade misturada
* Perfil de regras de ação de entrada de realidade misturada
* Perfil de ponteiro de realidade misturada

As configurações do [provedor olhar](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider) são modificadas no objeto da câmera principal na cena.

Componentes de suporte de plataforma (por exemplo, o Windows Mixed Reality Gerenciador de Dispositivos) devem ser adicionados aos provedores de dados do serviço correspondente.

### <a name="interface-and-event-mappings"></a>Mapeamentos de interface e evento

Alguns eventos não têm mais eventos exclusivos e agora contêm um [MixedRealityInputAction](../features/input/input-actions.md). Essas ações são especificadas no perfil de ações de entrada e mapeadas para controladores e plataformas específicos no perfil de mapeamento do controlador. Eventos como `OnInputDown` deve agora verificar o tipo MixedRealityInputAction.

Sistemas de entrada relacionados:

* [Visão geral da entrada](../features/input/overview.md)
* [Eventos de entrada](../features/input/input-events.md)
* [Ponteiros de entrada](../features/input/pointers.md)

| HTK 2017 |  MRTK v2  | Mapeamento de ação |
|----------|-----------|----------------|
| `IControllerInputHandler` | [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mapeado para o touchpad ou Thumbstick |
| `IControllerTouchpadHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Mapeado para o touchpad |
| `IFocusable` | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) | |
| `IGamePadHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IHoldHandler` | [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Mapeado para manter no perfil de gestos |
| `IInputClickHandler` | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) |
| `IInputHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Mapeado para os botões do controlador ou toque à mão |
| `IManipulationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Mapeado para manipulação no perfil de gestos |
| `INavigationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Mapeado para navegação no perfil de gestos |
| `IPointerSpecificFocusable` | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) | |
| `ISelectHandler` | [`IMixedRealityInputHandler<float>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mapeado para a posição do gatilho |
| `ISourcePositionHandler` | [`IMixedRealityInputHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) ou [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mapeado para posição do ponteiro ou posição de alça |
| `ISourceRotationHandler` | [`IMixedRealityInputHandler<Quaternion>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) ou [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mapeado para posição do ponteiro ou posição de alça |
| `ISourceStateHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IXboxControllerHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) E [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mapeado para os vários botões e thumbsticks do controlador |

## <a name="camera"></a>Câmera

|        Métodos                    | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalação                     | Exclua MainCamera, adicione o pré-fab MixedRealityCameraParent/MixedRealityCamera/HoloLensCamera à cena ou **use** o item de menu Kit de Ferramentas de Realidade Misturada > Configurar > Aplicar Configurações de Cena de Realidade Misturada. | MainCamera pai em MixedRealityPlayspace por meio do Kit de Ferramentas de Realidade Misturada > Adicionar à Cena e Configurar... |
| Configuração             | Configuração de configurações de câmera executadas na instância de pré-fab. | Configurações de câmera configuradas no [Câmera de Realidade Misturada Profile](xref:Microsoft.MixedReality.Toolkit.MixedRealityCameraProfile). |

## <a name="speech"></a>Fala

### <a name="keyword-recognition"></a>Reconhecimento de palavra-chave

|         Métodos                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalação                     | Adicione um SpeechInputSource à sua cena. | O serviço de palavra-chave (por exemplo, Gerenciador de Entrada de Fala do Windows) deve ser adicionado aos provedores de dados do sistema de entrada. |
| Configuração             | As palavras-chave reconhecidas são configuradas no inspetor de SpeechInputSource. | As palavras-chave são configuradas no Perfil de Comandos [de Fala de Realidade Misturada](../features/input/speech.md). |
| Manipuladores de eventos            | `ISpeechHandler` | [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

### <a name="dictation"></a>Ditado

|         Métodos                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalação                     | Adicione um DictationInputManager à sua cena. | O suporte a ditado requer que o serviço (por exemplo, Gerenciador de Entrada de Ditado do Windows) seja adicionado aos provedores de dados do Sistema de Entrada. |
| Manipuladores de eventos            | `IDictationHandler` | `IMixedRealityDictationHandler`[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

## <a name="spatial-awareness--mapping"></a>Reconhecimento espacial/mapeamento

### <a name="mesh"></a>Malha

|         Métodos                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalação                     | Adicione o pré-fab SpatialMapping à cena. | Habilita o Sistema de Reconhecimento Espacial no Perfil de Configuração e adicione um observador espacial (por exemplo, Windows Mixed Reality Observador de Malha Espacial) aos provedores de dados do Sistema de Reconhecimento Espacial. |
| Configuração             | Configure a instância da cena no inspetor. | Definir as configurações no perfil de cada observador espacial. |

### <a name="planes"></a>Aviões

|         Métodos                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalação                     | Use o `SurfaceMeshesToPlanes` script. | Ainda não implementado. |

### <a name="spatial-understanding"></a>Compreensão espacial

|       Métodos                      | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalação                     | Adicione o pré-fab SpatialUnderstanding à cena. | Ainda não implementado. |
| Configuração             | Configure a instância da cena no inspetor. | Ainda não implementado. |

## <a name="boundary"></a>Limite

|         Métodos                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalação                     | Adicione o `BoundaryManager` script à cena. | Habilita o Sistema de Limites no Perfil de Configuração. |
| Configuração             | Configure a instância da cena no inspetor. | De configurar as configurações no perfil visualização de limite. |

## <a name="sharing"></a>Compartilhamento

|             Métodos               | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalação                     | Compartilhamento de serviço: Adicionar pré-fabricado de compartilhamento à cena. UNet: Use o exemplo SharingWithUNET. | Em andamento |
| Configuração             | Configure as instâncias de cena no Inspetor. | Em andamento |

## <a name="ux"></a>UX

|         Métodos                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Botão                     | [Objetos que interagem](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Botão](../features/ux-building-blocks/Button.md) |
| Interativo                     | [Objetos que interagem](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Interativo](../features/ux-building-blocks/Interactable.md) |
| Caixa delimitadora             | [Caixa delimitadora](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Caixa delimitadora](../features/ux-building-blocks/bounding-box.md) |
| Barra de aplicativos             | [Barra de aplicativos](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Barra de aplicativos](../features/ux-building-blocks/app-bar.md) |
| Manipulação de uma mão (GRB e mover)   | [HandDraggable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/HandDraggable.cs) | [Manipulador de manipulação](../features/ux-building-blocks/manipulation-handler.md) |
| Manipulação de duas mãos (pegar/mover/girar/dimensionar)             | [TwoHandManipulatable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/TwoHandManipulatable.cs) | [Manipulador de manipulação](../features/ux-building-blocks/manipulation-handler.md) |
| Teclado             | [Pré-fabricado de teclado]() | [Teclado do sistema](../features/ux-building-blocks/system-keyboard.md) |
| Dica de ferramenta             | [Dica de ferramenta](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_TooltipExample.md) | [Dica de ferramenta](../features/ux-building-blocks/tooltip.md) |
| Coleção de objetos             | [Coleção de objetos](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md) | [Coleção de objetos](../features/ux-building-blocks/object-collection.md) |
| Solver             | [Solver](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Readme/README_SolverSystem.md) | [Solver](../features/ux-building-blocks/solvers/solver.md) |

## <a name="utilities"></a>Utilitários

Alguns utilitários foram reconciliados como duplicatas com o sistema de solução de problemas. Registre um problema se algum dos scripts necessários estiver ausente.

| HTK 2017 |  MRTK v2  |
|----------|-----------|
| Mensagem | [`Billboard`](xref:Microsoft.MixedReality.Toolkit.UI.Billboard) |
| Que | [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) ou [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) [resolvedor](../features/ux-building-blocks/solvers/Solver.md) |
| FixedAngularSize | [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)[Resolvedor](../features/ux-building-blocks/solvers/solver.md) |
| FpsDisplay | [Sistema de diagnóstico](../features/diagnostics/diagnostics-system-getting-started.md) (no perfil de configuração) |
| NearFade | [Sombreador padrão misto de kit de ferramentas de realidade misturada](../features/rendering/mrtk-standard-shader.md) |
