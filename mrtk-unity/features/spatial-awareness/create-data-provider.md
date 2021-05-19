---
title: Criar Provedor de Dados de conscientização espacial
description: Descreve como criar provedores de dados personalizados no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 04a0cdbd18f666b6a99c120eb28966234cc8c92d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145157"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a><span data-ttu-id="a54b6-104">Criando um provedor de dados do sistema de conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="a54b6-104">Creating a spatial awareness system data provider</span></span>

<span data-ttu-id="a54b6-105">O sistema de conscientização espacial é um sistema extensível para fornecer aplicativos com dados sobre ambientes do mundo real.</span><span class="sxs-lookup"><span data-stu-id="a54b6-105">The Spatial Awareness system is an extensible system for providing applications with data about real world environments.</span></span> <span data-ttu-id="a54b6-106">Para adicionar suporte a uma nova plataforma de hardware ou a uma nova forma de dados de conscientização espacial, um provedor de dados personalizado pode ser necessário.</span><span class="sxs-lookup"><span data-stu-id="a54b6-106">To add support for a new hardware platform or a new form of Spatial Awareness data, a custom data provider may be required.</span></span>

<span data-ttu-id="a54b6-107">Este artigo descreve como criar [provedores de dados personalizados](../../architecture/systems-extensions-providers.md), também chamados de observadores espaciais, para o sistema de conscientização espacial.</span><span class="sxs-lookup"><span data-stu-id="a54b6-107">This article describes how to create [custom data providers](../../architecture/systems-extensions-providers.md), also called Spatial Observers, for the Spatial Awareness system.</span></span> <span data-ttu-id="a54b6-108">O código de exemplo mostrado aqui é da [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) implementação de classe que é [útil para carregar dados de malha 3D no editor](spatial-object-mesh-observer.md).</span><span class="sxs-lookup"><span data-stu-id="a54b6-108">The example code shown here is from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class implementation which is [useful for loading 3D mesh data in-editor](spatial-object-mesh-observer.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a54b6-109">O código-fonte completo usado neste exemplo pode ser encontrado na `Assets/MRTK/Providers/ObjectMeshObserver` pasta.</span><span class="sxs-lookup"><span data-stu-id="a54b6-109">The complete source code used in this example can be found in the `Assets/MRTK/Providers/ObjectMeshObserver` folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="a54b6-110">Namespace e estrutura de pastas</span><span class="sxs-lookup"><span data-stu-id="a54b6-110">Namespace and folder structure</span></span>

<span data-ttu-id="a54b6-111">Os provedores de dados podem ser distribuídos de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="a54b6-111">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="a54b6-112">Complementos de terceiros</span><span class="sxs-lookup"><span data-stu-id="a54b6-112">Third party add-ons</span></span>
1. <span data-ttu-id="a54b6-113">Parte do kit de ferramentas do Microsoft Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a54b6-113">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="a54b6-114">O processo de aprovação para envios de novos provedores de dados para o MRTK variará de acordo com o caso e será comunicado no momento da proposta inicial.</span><span class="sxs-lookup"><span data-stu-id="a54b6-114">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="a54b6-115">As propostas podem ser enviadas criando um novo [problema de tipo de *solicitação de recurso*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="a54b6-115">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-on"></a><span data-ttu-id="a54b6-116">Complemento de terceiros</span><span class="sxs-lookup"><span data-stu-id="a54b6-116">Third party add-on</span></span>

<span data-ttu-id="a54b6-117">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="a54b6-117">**Namespace**</span></span>

<span data-ttu-id="a54b6-118">Os provedores de dados precisam ter um namespace para atenuar colisões de nomes potenciais.</span><span class="sxs-lookup"><span data-stu-id="a54b6-118">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="a54b6-119">É recomendável que o namespace inclua os componentes a seguir.</span><span class="sxs-lookup"><span data-stu-id="a54b6-119">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="a54b6-120">Nome da empresa que produz o complemento</span><span class="sxs-lookup"><span data-stu-id="a54b6-120">Company name producing the add-on</span></span>
- <span data-ttu-id="a54b6-121">Área do recurso</span><span class="sxs-lookup"><span data-stu-id="a54b6-121">Feature area</span></span>

<span data-ttu-id="a54b6-122">Por exemplo, um provedor de dados de conscientização espacial criado e enviado pela empresa contoso pode ser *"contoso. MixedReality. Toolkit. SpatialAwareness"*.</span><span class="sxs-lookup"><span data-stu-id="a54b6-122">For example, a Spatial Awareness data provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.SpatialAwareness"*.</span></span>

<span data-ttu-id="a54b6-123">**Estrutura de pastas**</span><span class="sxs-lookup"><span data-stu-id="a54b6-123">**Folder structure**</span></span>

<span data-ttu-id="a54b6-124">É recomendável que o código-fonte para provedores de dados seja layeddo em uma hierarquia de pastas, conforme mostrado na imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="a54b6-124">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Estrutura de pasta de exemplo](../images/spatial-awareness/ExampleProviderFolderStructure.png)

<span data-ttu-id="a54b6-126">Onde a *pasta ContosoSpatialAwareness* contém a implementação do provedor de dados, a pasta *Editor* contém o inspetor (e qualquer outro código específico do editor do Unity) e a pasta *Perfis* contém um ou mais objetos de script de perfil pré-criados.</span><span class="sxs-lookup"><span data-stu-id="a54b6-126">Where the *ContosoSpatialAwareness* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="a54b6-127">Envio do MRTK</span><span class="sxs-lookup"><span data-stu-id="a54b6-127">MRTK submission</span></span>

<span data-ttu-id="a54b6-128">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="a54b6-128">**Namespace**</span></span>

<span data-ttu-id="a54b6-129">Se um provedor de dados do sistema de reconhecimento espacial estiver sendo enviado para o repositório do Kit de Ferramentas de Realidade Misturada [,](https://github.com/Microsoft/MixedRealityToolkit-Unity)o **namespace** deverá começar com Microsoft.MixedReality.Toolkit (por ex. *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver*)</span><span class="sxs-lookup"><span data-stu-id="a54b6-129">If a spatial awareness system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver*)</span></span>

 <span data-ttu-id="a54b6-130">e o código deve estar localizado em uma pasta abaixo do MRTK/Provedores (por ex. *MRTK/Providers/ObjectMeshObserver*).</span><span class="sxs-lookup"><span data-stu-id="a54b6-130">and the code should be located in a folder beneath MRTK/Providers (ex: *MRTK/Providers/ObjectMeshObserver*).</span></span>

<span data-ttu-id="a54b6-131">**Estrutura de pastas**</span><span class="sxs-lookup"><span data-stu-id="a54b6-131">**Folder structure**</span></span>

<span data-ttu-id="a54b6-132">Todo o código deve estar localizado em uma pasta abaixo do MRTK/Provedores (por ex. MRTK/Providers/ObjectMeshObserver).</span><span class="sxs-lookup"><span data-stu-id="a54b6-132">All code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/ObjectMeshObserver).</span></span>

## <a name="define-the-spatial-data-object"></a><span data-ttu-id="a54b6-133">Definir o objeto de dados espaciais</span><span class="sxs-lookup"><span data-stu-id="a54b6-133">Define the spatial data object</span></span>

<span data-ttu-id="a54b6-134">A primeira etapa na criação de um provedor de dados de Reconhecimento Espacial é determinar o tipo de dados (por ex. malhas ou planos) que ele fornecerá aos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="a54b6-134">The first step in creating a Spatial Awareness data provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="a54b6-135">Todos os objetos de dados espaciais devem implementar a [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interface .</span><span class="sxs-lookup"><span data-stu-id="a54b6-135">All spatial data objects must implement the [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interface.</span></span>

<span data-ttu-id="a54b6-136">A base do Kit de Ferramentas de Realidade Misturada fornece os seguintes objetos espaciais que podem ser usados ou estendidos em novos provedores de dados.</span><span class="sxs-lookup"><span data-stu-id="a54b6-136">The Mixed Reality Toolkit foundation provides the following spatial objects that can be used or extended in new data providers.</span></span>

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a><span data-ttu-id="a54b6-137">Implementar o provedor de dados</span><span class="sxs-lookup"><span data-stu-id="a54b6-137">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="a54b6-138">Especificar a herança da interface e/ou da classe base</span><span class="sxs-lookup"><span data-stu-id="a54b6-138">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="a54b6-139">Todos os provedores de dados de Reconhecimento Espacial devem implementar a interface , que especifica a funcionalidade mínima [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) exigida pelo sistema de Reconhecimento Espacial.</span><span class="sxs-lookup"><span data-stu-id="a54b6-139">All Spatial Awareness data providers must implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface, which specifies the minimum functionality required by the Spatial Awareness system.</span></span> <span data-ttu-id="a54b6-140">A base do MRTK inclui [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) a classe que fornece uma implementação padrão dessa funcionalidade necessária.</span><span class="sxs-lookup"><span data-stu-id="a54b6-140">The MRTK foundation includes the [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class which provides a default implementation of this required functionality.</span></span>

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> <span data-ttu-id="a54b6-141">A interface é usada pela classe para indicar que ela dá suporte à funcionalidade [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) SpatialAwarenessMesh.</span><span class="sxs-lookup"><span data-stu-id="a54b6-141">The [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interface is used by the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class to indicate that it provides support for the SpatialAwarenessMesh capability.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="a54b6-142">Aplicar o atributo MixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="a54b6-142">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="a54b6-143">Uma etapa importante na criação de um provedor de dados de Reconhecimento Espacial é aplicar [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) o atributo à classe .</span><span class="sxs-lookup"><span data-stu-id="a54b6-143">A key step in creating a Spatial Awareness data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="a54b6-144">Esta etapa permite definir o perfil padrão e as plataformas para o provedor de dados, quando selecionado no perfil de Reconhecimento Espacial, bem como Nome, caminho da pasta e muito mais.</span><span class="sxs-lookup"><span data-stu-id="a54b6-144">This step enables setting the default profile and platform(s) for the data provider, when selected in the Spatial Awareness profile as well as Name, folder path, and more.</span></span>

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="a54b6-145">Implementar os métodos IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="a54b6-145">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="a54b6-146">Depois que a classe tiver sido definida, a próxima etapa será fornecer a implementação da [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="a54b6-146">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="a54b6-147">A [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) classe, por meio da [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) classe, fornece apenas uma implementação vazia para [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) métodos.</span><span class="sxs-lookup"><span data-stu-id="a54b6-147">The [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides only an empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="a54b6-148">Os detalhes desses métodos geralmente são específicos do provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="a54b6-148">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="a54b6-149">Os métodos que devem ser implementados pelo provedor de dados são:</span><span class="sxs-lookup"><span data-stu-id="a54b6-149">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="a54b6-150">Implementar a lógica do provedor de dados</span><span class="sxs-lookup"><span data-stu-id="a54b6-150">Implement the data provider logic</span></span>

<span data-ttu-id="a54b6-151">A próxima etapa é adicionar a lógica do provedor de dados implementando a interface de provedor de dados específica, por exemplo [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) .</span><span class="sxs-lookup"><span data-stu-id="a54b6-151">The next step is to add the logic of the data provider by implementing the specific data provider interface, for example [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver).</span></span> <span data-ttu-id="a54b6-152">Essa parte do provedor de dados normalmente será específica da plataforma.</span><span class="sxs-lookup"><span data-stu-id="a54b6-152">This portion of the data provider will typically be platform specific.</span></span>

### <a name="observation-change-notifications"></a><span data-ttu-id="a54b6-153">Notificações de alteração de observação</span><span class="sxs-lookup"><span data-stu-id="a54b6-153">Observation change notifications</span></span>

<span data-ttu-id="a54b6-154">Para permitir que os aplicativos respondam às alterações na compreensão do dispositivo do ambiente, o provedor de dados gera eventos de notificação, conforme definido na [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interface.</span><span class="sxs-lookup"><span data-stu-id="a54b6-154">To allow applications to respond to changes in the device's understanding of the environment, the data provider raises notification events as defined in the [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interface.</span></span>

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 <span data-ttu-id="a54b6-155">O código a seguir dos [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) exemplos demonstra o lançamento e evento quando os dados de malha são adicionados.</span><span class="sxs-lookup"><span data-stu-id="a54b6-155">The following code from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) examples demonstrates raising and event when mesh data is added.</span></span>

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> <span data-ttu-id="a54b6-156">A [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe não gera `OnObservationUpdated` eventos, pois o modelo 3D só é carregado uma vez.</span><span class="sxs-lookup"><span data-stu-id="a54b6-156">The [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class does not raise `OnObservationUpdated` events since the 3D model is only loaded once.</span></span> <span data-ttu-id="a54b6-157">A implementação na [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe fornece um exemplo de como gerar um `OnObservationUpdated` evento para uma malha observada.</span><span class="sxs-lookup"><span data-stu-id="a54b6-157">The implementation in the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class provides an example of raising an `OnObservationUpdated` event for an observed mesh.</span></span>

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="a54b6-158">Adicionar instrumentação do criador de perfil do Unity</span><span class="sxs-lookup"><span data-stu-id="a54b6-158">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="a54b6-159">O desempenho é essencial em aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="a54b6-159">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="a54b6-160">Cada componente adiciona alguma quantidade de sobrecarga para os aplicativos que devem ser contados.</span><span class="sxs-lookup"><span data-stu-id="a54b6-160">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="a54b6-161">Para esse fim, é importante que todos os provedores de dados de reconhecimento espacial contenham instrumentação do Unity Profiler no loop interno e caminhos de código frequentemente utilizados.</span><span class="sxs-lookup"><span data-stu-id="a54b6-161">To this end, it is important that all spatial awareness data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="a54b6-162">É recomendável implementar o padrão utilizado pelo MRTK ao instrumentar provedores personalizados.</span><span class="sxs-lookup"><span data-stu-id="a54b6-162">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> <span data-ttu-id="a54b6-163">O nome usado para identificar o marcador do criador de perfil é arbitrário.</span><span class="sxs-lookup"><span data-stu-id="a54b6-163">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="a54b6-164">O MRTK usa o seguinte padrão.</span><span class="sxs-lookup"><span data-stu-id="a54b6-164">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="a54b6-165">"[Product] className. methodName-observação opcional"</span><span class="sxs-lookup"><span data-stu-id="a54b6-165">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="a54b6-166">É recomendável que os provedores de dados personalizados sigam um padrão semelhante para ajudar a simplificar a identificação de componentes e métodos específicos ao analisar os rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="a54b6-166">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="a54b6-167">Criar o perfil e o Inspetor</span><span class="sxs-lookup"><span data-stu-id="a54b6-167">Create the profile and inspector</span></span>

<span data-ttu-id="a54b6-168">No kit de ferramentas de realidade misturada, os provedores de dados são configurados usando [perfis](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a54b6-168">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="a54b6-169">Definir o perfil</span><span class="sxs-lookup"><span data-stu-id="a54b6-169">Define the profile</span></span>

<span data-ttu-id="a54b6-170">O conteúdo do perfil deve espelhar as propriedades acessíveis do provedor de dados (ex: intervalo de atualização).</span><span class="sxs-lookup"><span data-stu-id="a54b6-170">Profile contents should mirror the accessible properties of the data provider (ex: update interval).</span></span> <span data-ttu-id="a54b6-171">Todas as propriedades configuráveis pelo usuário definidas em cada interface devem estar contidas no perfil.</span><span class="sxs-lookup"><span data-stu-id="a54b6-171">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

<span data-ttu-id="a54b6-172">As classes base serão incentivadas se um novo provedor de dados estender um provedor existente.</span><span class="sxs-lookup"><span data-stu-id="a54b6-172">Base classes are encouraged if a new data provider extends an existing provider.</span></span> <span data-ttu-id="a54b6-173">Por exemplo, o [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) estende o [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) para permitir que os clientes forneçam um modelo 3D a ser usado como os dados do ambiente.</span><span class="sxs-lookup"><span data-stu-id="a54b6-173">For example, the [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) extends the [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) to enable customers to provide a 3D model to be used as the environment data.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

<span data-ttu-id="a54b6-174">O `CreateAssetMenu` atributo pode ser aplicado à classe de perfil para permitir que os clientes criem uma instância de perfil usando o menu **Create**  >  **assets**  >  **Mixed Realm**  >  **Profiles** do kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="a54b6-174">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="a54b6-175">Implementar o Inspetor</span><span class="sxs-lookup"><span data-stu-id="a54b6-175">Implement the inspector</span></span>

<span data-ttu-id="a54b6-176">Os inspetores de perfil são a interface do usuário para configurar e exibir o conteúdo do perfil.</span><span class="sxs-lookup"><span data-stu-id="a54b6-176">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="a54b6-177">Cada Inspetor de perfil deve estender a [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe.</span><span class="sxs-lookup"><span data-stu-id="a54b6-177">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="a54b6-178">O `CustomEditor` atributo informa ao Unity o tipo de ativo ao qual o Inspetor se aplica.</span><span class="sxs-lookup"><span data-stu-id="a54b6-178">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="a54b6-179">Criar definição (ões) de assembly</span><span class="sxs-lookup"><span data-stu-id="a54b6-179">Create assembly definition(s)</span></span>

<span data-ttu-id="a54b6-180">O kit de ferramentas de realidade misturada usa arquivos de definição de assembly ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) para especificar dependências entre componentes, bem como para auxiliar o Unity na redução do tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="a54b6-180">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="a54b6-181">É recomendável que os arquivos de definição de assembly sejam criados para todos os provedores de dados e seus componentes do editor.</span><span class="sxs-lookup"><span data-stu-id="a54b6-181">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="a54b6-182">Usando a [estrutura de pastas](#namespace-and-folder-structure) no exemplo anterior, haveria dois arquivos. asmdef para o provedor de dados ContosoSpatialAwareness.</span><span class="sxs-lookup"><span data-stu-id="a54b6-182">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoSpatialAwareness data provider.</span></span>

<span data-ttu-id="a54b6-183">A primeira definição do assembly é para o provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="a54b6-183">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="a54b6-184">Para este exemplo, ele será chamado de ContosoSpatialAwareness e estará localizado na pasta *ContosoSpatialAwareness* do exemplo.</span><span class="sxs-lookup"><span data-stu-id="a54b6-184">For this example, it will be called ContosoSpatialAwareness and will be located in the example's *ContosoSpatialAwareness* folder.</span></span> <span data-ttu-id="a54b6-185">Essa definição de assembly deve especificar uma dependência no Microsoft.MixedReality.Toolkit e em todos os outros assemblies dos quais ela depende.</span><span class="sxs-lookup"><span data-stu-id="a54b6-185">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="a54b6-186">A definição de assembly ContosoInputEditor especificará o inspetor de perfil e qualquer código específico do editor.</span><span class="sxs-lookup"><span data-stu-id="a54b6-186">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="a54b6-187">Esse arquivo deve estar localizado na pasta raiz do código do editor.</span><span class="sxs-lookup"><span data-stu-id="a54b6-187">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="a54b6-188">Neste exemplo, o arquivo estará localizado na *pasta ContosoSpatialAwareness\Editor.*</span><span class="sxs-lookup"><span data-stu-id="a54b6-188">In this example, the file will be located in the *ContosoSpatialAwareness\Editor* folder.</span></span> <span data-ttu-id="a54b6-189">Essa definição de assembly conterá uma referência ao assembly ContosoSpatialAwareness, bem como:</span><span class="sxs-lookup"><span data-stu-id="a54b6-189">This assembly definition will contain a reference to the ContosoSpatialAwareness assembly as well as:</span></span>

- <span data-ttu-id="a54b6-190">Microsoft.MixedReality.Toolkit</span><span class="sxs-lookup"><span data-stu-id="a54b6-190">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="a54b6-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span><span class="sxs-lookup"><span data-stu-id="a54b6-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="a54b6-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span><span class="sxs-lookup"><span data-stu-id="a54b6-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="a54b6-193">Registrar o provedor de dados</span><span class="sxs-lookup"><span data-stu-id="a54b6-193">Register the data provider</span></span>

<span data-ttu-id="a54b6-194">Depois de criado, o provedor de dados pode ser registrado com o sistema de Reconhecimento Espacial a ser usado no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a54b6-194">Once created, the data provider can be registered with the Spatial Awareness system to be used in the application.</span></span>

![Selecionando o observador de malha de objeto espacial](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="a54b6-196">Empacotamento e distribuição</span><span class="sxs-lookup"><span data-stu-id="a54b6-196">Packaging and distribution</span></span>

<span data-ttu-id="a54b6-197">Provedores de dados distribuídos como componentes de terceiros têm os detalhes específicos de empacotamento e distribuição deixados à preferência do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="a54b6-197">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="a54b6-198">Provavelmente, a solução mais comum será gerar um .unitypackage e distribuir por meio do Asset Store do Unity.</span><span class="sxs-lookup"><span data-stu-id="a54b6-198">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="a54b6-199">Se um provedor de dados for enviado e aceito como parte do pacote do Microsoft Mixed Reality Toolkit, a equipe do Microsoft MRTK o empacota e distribui como parte das ofertas do MRTK.</span><span class="sxs-lookup"><span data-stu-id="a54b6-199">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="a54b6-200">Confira também</span><span class="sxs-lookup"><span data-stu-id="a54b6-200">See also</span></span>

- [<span data-ttu-id="a54b6-201">Sistema de conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="a54b6-201">Spatial awareness system</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="a54b6-202">`IMixedRealitySpatialAwarenessObject` Interface</span><span class="sxs-lookup"><span data-stu-id="a54b6-202">`IMixedRealitySpatialAwarenessObject` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [<span data-ttu-id="a54b6-203">`BaseSpatialAwarenessObject` classe</span><span class="sxs-lookup"><span data-stu-id="a54b6-203">`BaseSpatialAwarenessObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [<span data-ttu-id="a54b6-204">`SpatialAwarenessMeshObject` classe</span><span class="sxs-lookup"><span data-stu-id="a54b6-204">`SpatialAwarenessMeshObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [<span data-ttu-id="a54b6-205">`SpatialAwarenessPlanarObject` classe</span><span class="sxs-lookup"><span data-stu-id="a54b6-205">`SpatialAwarenessPlanarObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [<span data-ttu-id="a54b6-206">`IMixedRealitySpatialAwarenessObserver` Interface</span><span class="sxs-lookup"><span data-stu-id="a54b6-206">`IMixedRealitySpatialAwarenessObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [<span data-ttu-id="a54b6-207">`BaseSpatialObserver` classe</span><span class="sxs-lookup"><span data-stu-id="a54b6-207">`BaseSpatialObserver` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [<span data-ttu-id="a54b6-208">`IMixedRealitySpatialAwarenessMeshObserver` Interface</span><span class="sxs-lookup"><span data-stu-id="a54b6-208">`IMixedRealitySpatialAwarenessMeshObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [<span data-ttu-id="a54b6-209">`IMixedRealityDataProvider` Interface</span><span class="sxs-lookup"><span data-stu-id="a54b6-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="a54b6-210">`IMixedRealityCapabilityCheck` Interface</span><span class="sxs-lookup"><span data-stu-id="a54b6-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
