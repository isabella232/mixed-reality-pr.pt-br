---
title: UsingGuide
description: Descreve os principais mecanismos e APIs para configurar programaticamente o sistema de conscientização espacial
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 3a4b6ce17b87dba6155a9e020e41c800fd8ab86bc1b507e77e680fe9ec9a6687
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204118"
---
# <a name="configuring-mesh-observers-via-code"></a>Configurando os observadores de malha por meio do código

Este artigo discutirá alguns dos principais mecanismos e APIs para configurar programaticamente o [sistema de conscientização espacial](spatial-awareness-getting-started.md) e os provedores de dados de *observadores de malha* relacionados.

## <a name="accessing-mesh-observers"></a>Acessando observadores de malha

As classes de observadores de malha que implementam a [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) interface fornecem dados de malha específicos da plataforma para o sistema de conscientização espacial. Vários observadores podem ser configurados no perfil de conscientização espacial.

o acesso aos provedores de dados do sistema de conscientização espacial é, na maioria das vezes, o mesmo para qualquer outra realidade misturada Toolkit serviço. O serviço de conscientização espacial deve ser convertido na [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface para acessar por meio das `GetDataProvider<T>` APIs, que podem ser utilizadas para acessar os objetos observadores de malha diretamente no tempo de execução.

```c#
// Use CoreServices to quickly get access to the IMixedRealitySpatialAwarenessSystem
var spatialAwarenessService = CoreServices.SpatialAwarenessSystem;

// Cast to the IMixedRealityDataProviderAccess to get access to the data providers
var dataProviderAccess = spatialAwarenessService as IMixedRealityDataProviderAccess;

var meshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
```

O `CoreServices.GetSpatialAwarenessSystemDataProvider<T>()` auxiliar simplifica esse padrão de acesso, conforme demonstrado abaixo.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var meshObserver = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Get the SpatialObjectMeshObserver specifically
var meshObserverName = "Spatial Object Mesh Observer";
var spatialObjectMeshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

## <a name="starting-and-stopping-mesh-observation"></a>Como iniciar e parar a observação de malha

Uma das tarefas mais comuns ao lidar com o sistema de conscientização espacial é desativar o recurso dinamicamente em tempo de execução. Isso é feito por meio do observador por meio das [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) APIs e.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Suspends observation of spatial mesh data
observer.Suspend();

// Resumes observation of spatial mesh data
observer.Resume();
```

Essa funcionalidade de código também pode ser simplificada por meio do acesso diretamente por meio do sistema de conscientização espacial.

```c#
var meshObserverName = "Spatial Object Mesh Observer";
CoreServices.SpatialAwarenessSystem.ResumeObserver<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

### <a name="starting-and-stopping-all-mesh-observation"></a>Iniciando e parando toda a observação de malha

Geralmente é conveniente iniciar/parar toda a observação de malha no aplicativo. Isso pode ser feito por meio das APIs úteis do sistema de conscientização espacial [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) e [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers) .

```c#
// Resume Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.ResumeObservers();

// Suspend Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.SuspendObservers();
```

## <a name="enumerating-and-accessing-the-meshes"></a>Enumerando e acessando as malhas

O acesso às malhas pode ser feito por meio do observador e, em seguida, a enumeração pelas malhas conhecidas pelo observador de malha por meio da [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) API.

Se estiver executando no editor, será possível usar o [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) para salvar o `Mesh` objeto em um arquivo de ativo.

Se estiver em execução no dispositivo, há muitos plug-ins da Comunidade e da loja disponíveis para serializar os `MeshFilter` dados em um tipo de arquivo de modelo ([exemplo de obj](http://wiki.unity3d.com/index.php/ObjExporter)).

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Loop through all known Meshes
foreach (SpatialAwarenessMeshObject meshObject in observer.Meshes.Values)
{
    Mesh mesh = meshObject.Filter.mesh;
    // Do something with the Mesh object
}
```

## <a name="showing-and-hiding-the-spatial-mesh"></a>Mostrando e ocultando a malha espacial

É possível ocultar/mostrar malhas programaticamente usando o código de exemplo abaixo:

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Set to not visible
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.None;

// Set to visible and the Occlusion material
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.Occlusion;
```

## <a name="registering-for-mesh-observation-events"></a>Registrando para eventos de observação de malha

Os componentes podem implementar `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` e, em seguida, registrar-se com o sistema de conscientização espacial para receber eventos de observação de malha.

O `DemoSpatialMeshHandler` script (ativos/MRTK/exemplos/demos/SpatialAwareness/scripts) é um exemplo útil e um ponto de partida para a escuta de eventos de observador de malha.

Este é um exemplo simplificado de escuta de evento de observação de *DemoSpatialMeshHandler* e script de malha.

```c#
// Simplify type
using SpatialAwarenessHandler = IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>;

public class MyMeshObservationExample : MonoBehaviour, SpatialAwarenessHandler
{
    private void OnEnable()
    {
        // Register component to listen for Mesh Observation events, typically done in OnEnable()
        CoreServices.SpatialAwarenessSystem.RegisterHandler<SpatialAwarenessHandler>(this);
    }

    private void OnDisable()
    {
        // Unregister component from Mesh Observation events, typically done in OnDisable()
        CoreServices.SpatialAwarenessSystem.UnregisterHandler<SpatialAwarenessHandler>(this);
    }

    public virtual void OnObservationAdded(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationUpdated(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationRemoved(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }
}
```

## <a name="see-also"></a>Confira também

- [Introdução de conscientização espacial](spatial-awareness-getting-started.md)
- [Configurando o observador de malha de conscientização espacial](configuring-spatial-awareness-mesh-observer.md)
- [Documentação da API de conscientização espacial](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
