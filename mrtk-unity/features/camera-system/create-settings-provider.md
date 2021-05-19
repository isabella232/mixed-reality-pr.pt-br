---
title: Criar provedor de configuração
description: provedor de dados para configurações de câmera no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 6ec3fc1c88c1a32334cb2869ad1994863e55bf9a
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144897"
---
# <a name="creating-a-camera-settings-provider"></a>Criando um provedor de configurações de câmera

O sistema câmera é um sistema extensível para dar suporte a configurações de câmera específicas da plataforma. Para adicionar suporte para uma nova configuração de câmera, um provedor de configurações personalizadas pode ser necessário.

> [!NOTE]
> O código-fonte completo usado neste exemplo pode ser encontrado na pasta **MRTK/Providers/UnityAR.**

## <a name="namespace-and-folder-structure"></a>Estrutura de namespace e pasta

Os provedores de dados podem ser distribuídos de uma das duas maneiras:

1. Complementos de terceiros
1. Parte do Microsoft Mixed Reality Toolkit

O processo de aprovação para envios de novos provedores de dados para o MRTK variará caso a caso e será comunicado no momento da proposta inicial. As propostas podem ser enviadas criando um novo problema de tipo [ *de Solicitação* de Recurso](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

### <a name="third-party-add-ons"></a>Complementos de terceiros

**Namespace**

Os provedores de dados precisam ter um namespace para atenuar possíveis colisões de nomes. É recomendável que o namespace inclua os componentes a seguir.

- Nome da empresa que produz o complemento
- Área do recurso

Por exemplo, um provedor de configurações de câmera criado e enviado pela empresa Contoso pode ser *"Contoso.MixedReality.Toolkit.Camera".*

**Estrutura de pastas**

É recomendável que o código-fonte para provedores de dados seja organizado em uma hierarquia de pastas, conforme mostrado na imagem a seguir.

![Estrutura de pasta de exemplo](../images/camera-system/ExampleProviderFolderStructure.png)

Onde a *pasta ContosoCamera* contém a implementação do provedor de dados, a pasta *Editor*  contém o inspetor (e qualquer outro código específico do editor do Unity) e a pasta Perfis contém um ou mais objetos de script de perfil pré-criados.

### <a name="mrtk-submission"></a>Envio do MRTK

**Namespace**

Se um provedor de configurações de câmera estiver sendo enviado para o [repositório Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity), o namespace **deverá** começar com Microsoft. MixedReality. Toolkit (por exemplo: *Microsoft. MixedReality. Toolkit. CameraSystem*).

**Estrutura de pastas**

Todo o código deve estar localizado em uma pasta abaixo de MRTK/Providers (por exemplo: MRTK/Providers/UnityAR).

## <a name="define-the-camera-settings-object"></a>Definir o objeto de configurações da câmera

A primeira etapa na criação de um provedor de configurações de câmera é determinar o tipo de dados (por exemplo, malhas ou aviões) que ele fornecerá aos aplicativos.

Todos os objetos de dados espaciais devem implementar a [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface.

## <a name="implement-the-settings-provider"></a>Implementar o provedor de configurações

### <a name="specify-interface-andor-base-class-inheritance"></a>Especificar a interface e/ou a herança de classe base

Todos os provedores de configurações de câmera devem implementar a [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface, que especifica a funcionalidade mínima exigida pelo sistema de câmera. O MRTK Foundation inclui a [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) classe que fornece uma implementação padrão da funcionalidade necessária.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Aplicar o atributo MixedRealityDataProvider

Uma etapa fundamental na criação de um provedor de configurações de câmera é aplicar o [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) atributo à classe. Esta etapa permite definir o perfil padrão e as plataformas para o provedor de dados, quando selecionado no perfil de sistema da câmera, bem como nome, caminho da pasta e muito mais.

```c#
    [MixedRealityDataProvider(
        typeof(IMixedRealityCameraSystem),
        SupportedPlatforms.Android | SupportedPlatforms.IOS,
        "Unity AR Foundation Camera Settings",
        "UnityAR/Profiles/DefaultUnityARCameraSettingsProfile.asset",
        "MixedRealityToolkit.Providers")]
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implementar os métodos IMixedRealityDataProvider

Depois que a classe tiver sido definida, a próxima etapa será fornecer a implementação da [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.

> [!NOTE]
> A [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) classe, por meio da [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) classe, fornece implementações vazias para [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) métodos. Os detalhes desses métodos geralmente são específicos do provedor de dados.

Os métodos que devem ser implementados pelo provedor de dados são:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> Nem todos os provedores de configurações precisarão de implementações para todos esses métodos. É altamente recomendável que `Destroy()` e `Initialize()` seja implementado no mínimo.

### <a name="implement-the-data-provider-logic"></a>Implementar a lógica do provedor de dados

A próxima etapa é adicionar a lógica do provedor de configurações implementando [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) . Essa parte do provedor de dados normalmente será específica da configuração da câmera.

## <a name="create-the-profile-and-inspector"></a>Criar o perfil e o inspetor

No Kit de Ferramentas de Realidade Misturada, os provedores de dados são configurados usando [perfis](../profiles/profiles.md).

### <a name="define-the-profile"></a>Definir o perfil

O conteúdo do perfil deve espelhar as opções de configuração selecionáveis pelo desenvolvedor. Todas as propriedades configuráveis pelo usuário definidas em cada interface também devem estar contidas com o perfil.

```c#
using UnityEngine.SpatialTracking;

namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CreateAssetMenu(
        menuName = "Mixed Reality Toolkit/Profiles/Unity AR Camera Settings Profile",
        fileName = "UnityARCameraSettingsProfile",
        order = 100)]
    public class UnityARCameraSettingsProfile : BaseCameraSettingsProfile
    {
        [SerializeField]
        [Tooltip("The portion of the device (ex: color camera) from which to read the pose.")]
        private ArTrackedPose poseSource = TrackedPoseDriver.TrackedPose.ColorCamera;

        /// <summary>
        /// The portion of the device (ex: color camera) from which to read the pose.
        /// </summary>
        public ArTrackedPose PoseSource => poseSource;

        [SerializeField]
        [Tooltip("The type of tracking (position and/or rotation) to apply.")]
        private ArTrackingType trackingType = TrackedPoseDriver.TrackingType.RotationAndPosition;

        /// <summary>
        /// The type of tracking (position and/or rotation) to apply.
        /// </summary>
        public ArTrackingType TrackingType => trackingType;

        [SerializeField]
        [Tooltip("Specifies when (during Update and/or just before rendering) to update the tracking of the pose.")]
        private ArUpdateType updateType = TrackedPoseDriver.UpdateType.UpdateAndBeforeRender;

        /// <summary>
        /// Specifies when (during Update and/or just before rendering) to update the tracking of the pose.
        /// </summary>
        public ArUpdateType UpdateType => updateType;
    }
}
```

O atributo pode ser aplicado à classe de perfil para permitir que os clientes criem uma instância de perfil usando o menu Criar Perfis do Kit de Ferramentas de Realidade `CreateAssetMenu`   >    >    >   Misturada de Ativos.

### <a name="implement-the-inspector"></a>Implementar o inspetor

Inspetores de perfil são a interface do usuário para configurar e exibir o conteúdo do perfil. Cada inspetor de perfil deve estender a [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe.

O `CustomEditor` atributo informa ao Unity o tipo de ativo ao qual o inspetor se aplica.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a>Criar definições de assembly

O Kit de Ferramentas de Realidade Misturada usa arquivos de definição de assembly ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) para especificar dependências entre componentes, bem como para ajudar o Unity a reduzir o tempo de compilação.

É recomendável que os arquivos de definição de assembly sejam criados para todos os provedores de dados e seus componentes do editor.

Usando a [estrutura de](#namespace-and-folder-structure) pastas no exemplo anterior, haveria dois arquivos .asmdef para o provedor de dados ContosoCamera.

A primeira definição de assembly é para o provedor de dados. Neste exemplo, ele será chamado contosoCamera e estará localizado na pasta *ContosoCamera do* exemplo. Essa definição de assembly deve especificar uma dependência no Microsoft.MixedReality.Toolkit e em todos os outros assemblies dos quais ela depende.

A definição de assembly ContosoCameraEditor especificará o inspetor de perfil e qualquer código específico do editor. Esse arquivo deve estar localizado na pasta raiz do código do editor. Neste exemplo, o arquivo estará localizado na pasta *ContosoCamera\Editor* . Essa definição de assembly conterá uma referência ao assembly ContosoCamera, bem como:

- Microsoft. MixedReality. Toolkit
- Microsoft. MixedReality. Toolkit. editor. Inspectors
- Microsoft. MixedReality. Toolkit. editor. Utilities

## <a name="register-the-data-provider"></a>Registrar o provedor de dados

Depois de criado, o provedor de dados pode ser registrado com o sistema de câmera a ser usado no aplicativo.

![Selecionando o provedor de configurações da câmera](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a>Empacotamento e distribuição

Os provedores de dados que são distribuídos como componentes de terceiros têm os detalhes específicos de empacotamento e distribuição deixados para a preferência do desenvolvedor. Provavelmente, a solução mais comum será gerar um. unitypackage e distribuir por meio do repositório de ativos do Unity.

Se um provedor de dados for enviado e aceito como parte do pacote do Microsoft Mixed Reality Toolkit, a equipe do Microsoft MRTK irá empacotá-lo e distribuí-lo como parte das ofertas do MRTK.

## <a name="see-also"></a>Confira também

- [Visão geral do sistema de câmera](camera-system-overview.md)
- [`BaseCameraSettingsProvider` classe](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [`IMixedRealityCameraSettingsProvider` interface](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [`IMixedRealityDataProvider` interface](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
