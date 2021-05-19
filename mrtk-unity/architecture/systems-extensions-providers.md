---
title: Provedor de extensões do sistema
description: Extensões de MRTK e provedores de dados
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, extensões do sistema,
ms.openlocfilehash: add1f443edb687edfc387a316d83443779e079f9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143507"
---
# <a name="systems-extension-services-and-data-providers"></a>Sistemas, serviços de extensão e provedores de dados

No kit de ferramentas de realidade misturada, muitos dos recursos são fornecidos na forma de serviços. Os serviços são agrupados em três categorias principais: sistemas, serviços de extensão e provedores de dados.

## <a name="systems"></a>Sistemas

Os sistemas são serviços que fornecem a funcionalidade básica do kit de ferramentas de realidade misturada. Todos os sistemas são implementações da [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.

- [BoundarySystem](../features/boundary/boundary-system-getting-started.md)
- [CameraSystem](../features/camera-system/camera-system-overview.md)
- [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md)
- [InputSystem](../features/input/overview.md)
- [SceneSystem](../features/scene-system/scene-system-getting-started.md)
- [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [TeleportSystem](../features/teleport-system/teleport-system.md)

Cada um dos sistemas listados está na superfície do [perfil](../features/profiles/profiles.md)de configuração do componente MixedRealityToolkit.

## <a name="extensions"></a>Extensões

Os serviços de extensão são componentes que estendem a funcionalidade do kit de ferramentas de realidade misturada. Todos os serviços de extensão devem especificar que eles implementam a [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.

Para obter informações sobre como criar serviços de extensão, consulte o artigo [serviços de extensão](../features/extensions/extension-services.md) .

Para ser acessível ao MRTK, os serviços de extensão são registrados e configurados usando a seção de extensões do perfil de configuração do componente MixedRealityToolkit.

![Configurando um serviço de extensão](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a>Provedores de dados

Os provedores de dados são componentes que, por nome, fornecem dados para um serviço kit de ferramentas de realidade misturada. Todos os provedores de dados devem especificar que implementam a [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface .

> [!NOTE]
> Nem todos os serviços exigirão provedores de dados. Dos sistemas do Kit de Ferramentas de Realidade Misturada, os sistemas de Entrada e Reconhecimento Espacial são os únicos serviços para utilizar provedores de dados.

Para ser acessível ao serviço específico do MRTK, os provedores de dados são registrados no perfil de configuração do serviço.

O código do aplicativo acessa provedores de dados por meio da [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface . Para simplificar o acesso, os provedores de dados também podem ser recuperados por meio `CoreServices` da classe auxiliar.

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> Embora `IMixedRealityDataProvider` herde de `IMixedRealityService` , os provedores de dados não estão registrados com o `MixedRealityServiceRegistry` . Para acessar provedores de dados, o código do aplicativo deve consultar a instância de serviço para a qual eles foram registrados (por exemplo: sistema de entrada).

### <a name="input"></a>Entrada

O sistema de entrada do MRTK utiliza apenas provedores de dados que implementam o [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) .

![Provedores de dados do sistema de entrada](../features/images/input/RegisteredServiceProviders.PNG)

O exemplo a seguir demonstra como acessar o provedor de simulação de entrada e alternar a propriedade SmoothEyeTracking.

```c#
IMixedRealityDataProviderAccess dataProviderAccess = CoreServices.InputSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IInputSimulationService inputSimulation =
        dataProviderAccess.GetDataProvider<IInputSimulationService>();

    if (inputSimulation != null)
    {
        inputSimulation.SmoothEyeTracking = !inputSimulation.SmoothEyeTracking;
    }
}
```

O acesso a um provedor de dados para o sistema de entrada principal também pode ser simplificado por meio do uso da `CoreServices` classe auxiliar.

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> O sistema de entrada retorna apenas provedores de dados com suporte para a plataforma na qual o aplicativo está em execução.

Para obter informações sobre como escrever um provedor de dados para o sistema de entrada do MRTK, consulte [criando um provedor de dados do sistema de entrada](../features/input/create-data-provider.md).

### <a name="spatial-awareness"></a>Reconhecimento espacial

O sistema de reconhecimento espacial do MRTK utiliza apenas provedores de dados que implementam a [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.

![Provedores de dados do sistema de reconhecimento espacial](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

O exemplo a seguir demonstra como acessar os provedores de dados de malha espacial registrados e alterar a visibilidade das malhas.

```c#
IMixedRealityDataProviderAccess dataProviderAccess =
    CoreServices.SpatialAwarenessSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IReadOnlyList<IMixedRealitySpatialAwarenessMeshObserver> observers =
        dataProviderAccess.GetDataProviders<IMixedRealitySpatialAwarenessMeshObserver>();

    foreach (IMixedRealitySpatialAwarenessMeshObserver observer in observers)
    {
        // Set the mesh to use the occlusion material
        observer.DisplayOption = SpatialMeshDisplayOptions.Occlusion;
    }
}
```

O acesso a um provedor de dados para o sistema de conscientização espacial principal também pode ser simplificado por meio do uso da `CoreServices` classe auxiliar.

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> O sistema de conscientização espacial retorna somente provedores de dados com suporte para a plataforma na qual o aplicativo está sendo executado.

Para obter informações sobre como escrever um provedor de dados para o sistema de conscientização espacial do MRTK, consulte [criando um provedor de dados do sistema de conscientização espacial](../features/spatial-awareness/create-data-provider.md).

## <a name="see-also"></a>Confira também

- [Serviços de extensão](../features/extensions/extension-services.md)
- [Criando um provedor de dados do sistema de entrada](../features/input/create-data-provider.md)
- [Criando um provedor de dados do sistema do sistema de reconhecimento espacial](../features/spatial-awareness/create-data-provider.md)
- [Interface IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [Interface IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [Interface IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
