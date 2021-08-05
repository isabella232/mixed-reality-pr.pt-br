---
title: criar Provedor de Dados de conscientização espacial
description: Descreve como criar provedores de dados personalizados no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 05186c418a7b0b7b143abc58be6a6afb64cb69f5a1c90c73ed516d51c2a5d8ea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188840"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a>Criando um provedor de dados do sistema de conscientização espacial

O sistema de conscientização espacial é um sistema extensível para fornecer aplicativos com dados sobre ambientes do mundo real. Para adicionar suporte a uma nova plataforma de hardware ou a uma nova forma de dados de conscientização espacial, um provedor de dados personalizado pode ser necessário.

Este artigo descreve como criar [provedores de dados personalizados](../../architecture/systems-extensions-providers.md), também chamados de observadores espaciais, para o sistema de conscientização espacial. O código de exemplo mostrado aqui é da [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) implementação de classe que é [útil para carregar dados de malha 3D no editor](spatial-object-mesh-observer.md).

> [!NOTE]
> O código-fonte completo usado neste exemplo pode ser encontrado na `Assets/MRTK/Providers/ObjectMeshObserver` pasta.

## <a name="namespace-and-folder-structure"></a>Namespace e estrutura de pastas

Os provedores de dados podem ser distribuídos de duas maneiras:

1. Complementos de terceiros
1. Parte da realidade misturada da Microsoft Toolkit

O processo de aprovação para envios de novos provedores de dados para o MRTK variará de acordo com o caso e será comunicado no momento da proposta inicial. As propostas podem ser enviadas criando um novo [problema de tipo de *solicitação de recurso*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

### <a name="third-party-add-on"></a>Complemento de terceiros

**Namespace**

Os provedores de dados precisam ter um namespace para atenuar colisões de nomes potenciais. É recomendável que o namespace inclua os componentes a seguir.

- Nome da empresa que produz o complemento
- Área do recurso

Por exemplo, um provedor de dados de conscientização espacial criado e enviado pela empresa contoso pode ser *"contoso. MixedReality. Toolkit. SpatialAwareness "*.

**Estrutura de pastas**

É recomendável que o código-fonte para provedores de dados seja layeddo em uma hierarquia de pastas, conforme mostrado na imagem a seguir.

![Estrutura de pasta de exemplo](../images/spatial-awareness/ExampleProviderFolderStructure.png)

Onde a pasta *ContosoSpatialAwareness* contém a implementação do provedor de dados, a pasta do *Editor* contém o Inspetor (e qualquer outro código específico do editor do Unity) e a pasta *perfis* contém um ou mais objetos programáveis por script predefinidos.

### <a name="mrtk-submission"></a>Envio de MRTK

**Namespace**

se um provedor de dados do sistema de conscientização espacial estiver sendo enviado para a [realidade misturada Toolkit repositório](https://github.com/Microsoft/MixedRealityToolkit-Unity), o namespace **deverá** começar com Microsoft. MixedReality. Toolkit (ex: *Microsoft. MixedReality. Toolkit. SpatialObjectMeshObserver*)

 e o código deve estar localizado em uma pasta sob MRTK/Providers (por exemplo: *MRTK/Providers/ObjectMeshObserver*).

**Estrutura de pastas**

Todo o código deve estar localizado em uma pasta abaixo de MRTK/Providers (por exemplo: MRTK/Providers/ObjectMeshObserver).

## <a name="define-the-spatial-data-object"></a>Definir o objeto de dados espaciais

A primeira etapa na criação de um provedor de dados de conscientização espacial é determinar o tipo de dados (por exemplo, malhas ou aviões) que ele fornecerá aos aplicativos.

Todos os objetos de dados espaciais devem implementar a [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interface.

a realidade misturada Toolkit foundation fornece os seguintes objetos espaciais que podem ser usados ou estendidos em novos provedores de dados.

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a>Implementar o provedor de dados

### <a name="specify-interface-andor-base-class-inheritance"></a>Especificar a interface e/ou a herança de classe base

Todos os provedores de dados de reconhecimento espacial devem implementar a [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface, que especifica a funcionalidade mínima exigida pelo sistema de conscientização espacial. O MRTK Foundation inclui a [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) classe que fornece uma implementação padrão dessa funcionalidade necessária.

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> A [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interface é usada pela [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe para indicar que ela fornece suporte para o recurso SpatialAwarenessMesh.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Aplicar o atributo MixedRealityDataProvider

Uma etapa fundamental na criação de um provedor de dados de conscientização espacial é aplicar o [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) atributo à classe. Esta etapa permite definir o perfil padrão e as plataformas para o provedor de dados, quando selecionado no perfil de conscientização espacial, bem como nome, caminho da pasta e muito mais.

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implementar os métodos IMixedRealityDataProvider

Depois que a classe tiver sido definida, a próxima etapa será fornecer a implementação da [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.

> [!NOTE]
> A [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) classe, por meio da [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) classe, fornece apenas uma implementação vazia para [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) métodos. Os detalhes desses métodos geralmente são específicos do provedor de dados.

Os métodos que devem ser implementados pelo provedor de dados são:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Implementar a lógica do provedor de dados

A próxima etapa é adicionar a lógica do provedor de dados implementando a interface de provedor de dados específica, por exemplo [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) . Essa parte do provedor de dados normalmente será específica da plataforma.

### <a name="observation-change-notifications"></a>Notificações de alteração de observação

Para permitir que os aplicativos respondam às alterações na compreensão do dispositivo do ambiente, o provedor de dados gera eventos de notificação, conforme definido na [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interface.

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 O código a seguir dos [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) exemplos demonstra o lançamento e evento quando os dados de malha são adicionados.

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
> A [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe não gera `OnObservationUpdated` eventos, pois o modelo 3D só é carregado uma vez. A implementação na [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe fornece um exemplo de como gerar um `OnObservationUpdated` evento para uma malha observada.

### <a name="add-unity-profiler-instrumentation"></a>Adicionar instrumentação do criador de perfil do Unity

O desempenho é essencial em aplicativos de realidade misturada. Cada componente adiciona alguma quantidade de sobrecarga para os aplicativos que devem ser contados. Para esse fim, é importante que todos os provedores de dados de reconhecimento espacial contenham instrumentação do Unity Profiler no loop interno e caminhos de código frequentemente utilizados.

É recomendável implementar o padrão utilizado pelo MRTK ao instrumentar provedores personalizados.

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
> O nome usado para identificar o marcador do criador de perfil é arbitrário. O MRTK usa o seguinte padrão.
>
> "[Product] className. methodName-observação opcional"
>
> É recomendável que os provedores de dados personalizados sigam um padrão semelhante para ajudar a simplificar a identificação de componentes e métodos específicos ao analisar os rastreamentos.

## <a name="create-the-profile-and-inspector"></a>Criar o perfil e o Inspetor

na realidade misturada Toolkit, os provedores de dados são configurados usando [perfis](../profiles/profiles.md).

### <a name="define-the-profile"></a>Definir o perfil

O conteúdo do perfil deve espelhar as propriedades acessíveis do provedor de dados (ex: intervalo de atualização). Todas as propriedades configuráveis pelo usuário definidas em cada interface devem estar contidas no perfil.

As classes base serão incentivadas se um novo provedor de dados estender um provedor existente. Por exemplo, o [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) estende o [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) para permitir que os clientes forneçam um modelo 3D a ser usado como os dados do ambiente.

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

o `CreateAssetMenu` atributo pode ser aplicado à classe de perfil para permitir que os clientes criem uma instância de perfil usando o menu **create**  >  **assets**  >  **Mixed reality Toolkit**  >  **profiles** .

### <a name="implement-the-inspector"></a>Implementar o Inspetor

Os inspetores de perfil são a interface do usuário para configurar e exibir o conteúdo do perfil. Cada Inspetor de perfil deve estender a [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe.

O `CustomEditor` atributo informa ao Unity o tipo de ativo ao qual o Inspetor se aplica.

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a>Criar definição (ões) de assembly

a realidade misturada Toolkit usa arquivos de definição de assembly ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) para especificar dependências entre componentes, bem como para auxiliar o Unity na redução do tempo de compilação.

É recomendável que os arquivos de definição de assembly sejam criados para todos os provedores de dados e seus componentes do editor.

Usando a [estrutura de pastas](#namespace-and-folder-structure) no exemplo anterior, haveria dois arquivos. asmdef para o provedor de dados ContosoSpatialAwareness.

A primeira definição do assembly é para o provedor de dados. Para este exemplo, ele será chamado de ContosoSpatialAwareness e estará localizado na pasta *ContosoSpatialAwareness* do exemplo. Esta definição de assembly deve especificar uma dependência em Microsoft. MixedReality. Toolkit e quaisquer outros assemblies sobre os quais depende.

A definição do assembly ContosoInputEditor especificará o Inspetor de perfil e qualquer código específico do editor. Esse arquivo deve estar localizado na pasta raiz do código do editor. Neste exemplo, o arquivo estará localizado na pasta *ContosoSpatialAwareness\Editor* . Essa definição de assembly conterá uma referência ao assembly ContosoSpatialAwareness, bem como:

- Microsoft. MixedReality. Toolkit
- Microsoft. MixedReality. Toolkit. Editor. inspetores
- Microsoft. MixedReality. Toolkit. Editor. Utilities

## <a name="register-the-data-provider"></a>Registrar o provedor de dados

Depois de criado, o provedor de dados pode ser registrado com o sistema de reconhecimento espacial a ser usado no aplicativo.

![Selecionando o observador de malha de objetos espaciais](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a>Empacotamento e distribuição

Os provedores de dados que são distribuídos como componentes de terceiros têm os detalhes específicos de empacotamento e distribuição deixados para a preferência do desenvolvedor. Provavelmente, a solução mais comum será gerar um. unitypackage e distribuir por meio do repositório de ativos do Unity.

se um provedor de dados for enviado e aceito como parte do pacote de Toolkit da realidade misturada da microsoft, a equipe do microsoft MRTK irá empacotá-lo e distribuí-lo como parte das ofertas do MRTK.

## <a name="see-also"></a>Consulte também

- [Sistema de conscientização espacial](spatial-awareness-getting-started.md)
- [`IMixedRealitySpatialAwarenessObject` Interface](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [`BaseSpatialAwarenessObject` classe](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject` classe](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject` classe](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [`IMixedRealitySpatialAwarenessObserver` Interface](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [`BaseSpatialObserver` classe](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [`IMixedRealitySpatialAwarenessMeshObserver` Interface](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [`IMixedRealityDataProvider` Interface](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` Interface](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
