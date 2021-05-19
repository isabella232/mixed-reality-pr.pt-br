---
title: Registro do Serviço de Realidade Misturada e IMixedRealityServiceRegistrar
description: Documentação sobre MixedRealityServiceRegistry e IMixedRealityServiceRegistrar
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 09b20537824af42d241b6c33496cedcb4f530bc7
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145231"
---
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a>O que são MixedRealityServiceRegistry e IMixedRealityServiceRegistrar?

O Kit de Ferramentas de Realidade Misturada tem dois componentes nomeados de forma muito semelhante que executam tarefas relacionadas: MixedRealityServiceRegistry e IMixedRealityServiceRegistrar.

## <a name="mixedrealityserviceregistry"></a>MixedRealityServiceRegistry

O [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) é o componente que contém instâncias de cada serviço registrado (sistemas principais e serviços de extensão).

> [!NOTE]
> O MixedRealityServiceRegistry contém instâncias de objetos que implementam a interface [IMixedRealityService,](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) incluindo [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).
>
>Os objetos que implementam [o IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (uma subclasse de IMixedRealityService) não são explicitamente registrados no MixedRealityServiceRegistry. Esses objetos são gerenciados pelos serviços individuais (por ex. Reconhecimento Espacial).

O MixedRealityServiceRegistry é implementado como uma classe C# estática e é o padrão recomendado a ser usado para adquirir instâncias de serviço no código do aplicativo.

O snippet a seguir demonstra a aquisição de uma instância IMixedRealityInputSystem.

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a>IMixedRealityServiceRegistrar

O [IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) é a interface que define a funcionalidade implementada pelos componentes que gerenciam o registro de um ou mais serviços. Os componentes que implementam IMixedRealityServiceRegistrar são responsáveis por adicionar e remover os dados no MixedRealityServiceRegistry. O [objeto MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) é um desses componentes.

Outros registradores podem ser encontrados na pasta MRTK/SDK/Experimental/Features. Esses componentes podem ser usados para adicionar suporte de serviço único (por exemplo: Reconhecimento Espacial) a um aplicativo. Esses gerenciadores de serviços individuais estão listados abaixo.

- [BoundarySystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [CameraSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [DiagnosticsSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [InputSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [SpatialAwarenessSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [TeleportSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

Cada um dos componentes acima, com exceção do InputSystemManager, é responsável por gerenciar o registro e o status de um único tipo de serviço. O InputSystem requer alguns serviços de suporte adicionais (ex: Focusprovider) que também são gerenciados pelo InputSystemManager.

Em geral, os métodos definidos por IMixedRealityServiceRegistrar são chamados internamente pelos componentes de gerenciamento de serviços ou chamados por serviços que exigem componentes de serviço adicionais para funcionar corretamente. O código do aplicativo deve, em geral, não chamar esses métodos, pois isso pode fazer com que o aplicativo se comporte de modo não previsível (por exemplo: uma instância de serviço em cache pode se tornar inválida).

## <a name="see-also"></a>Confira também

- [Documentação da API do IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [Documentação da API do MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
