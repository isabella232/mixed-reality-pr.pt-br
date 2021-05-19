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
# <a name="creating-a-camera-settings-provider"></a><span data-ttu-id="6400d-104">Criando um provedor de configurações de câmera</span><span class="sxs-lookup"><span data-stu-id="6400d-104">Creating a camera settings provider</span></span>

<span data-ttu-id="6400d-105">O sistema câmera é um sistema extensível para dar suporte a configurações de câmera específicas da plataforma.</span><span class="sxs-lookup"><span data-stu-id="6400d-105">The Camera system is an extensible system for providing support for platform specific camera configurations.</span></span> <span data-ttu-id="6400d-106">Para adicionar suporte para uma nova configuração de câmera, um provedor de configurações personalizadas pode ser necessário.</span><span class="sxs-lookup"><span data-stu-id="6400d-106">To add support for a new camera configuration, a custom settings provider may be required.</span></span>

> [!NOTE]
> <span data-ttu-id="6400d-107">O código-fonte completo usado neste exemplo pode ser encontrado na pasta **MRTK/Providers/UnityAR.**</span><span class="sxs-lookup"><span data-stu-id="6400d-107">The complete source code used in this example can be found in the **MRTK/Providers/UnityAR** folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="6400d-108">Estrutura de namespace e pasta</span><span class="sxs-lookup"><span data-stu-id="6400d-108">Namespace and folder structure</span></span>

<span data-ttu-id="6400d-109">Os provedores de dados podem ser distribuídos de uma das duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="6400d-109">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="6400d-110">Complementos de terceiros</span><span class="sxs-lookup"><span data-stu-id="6400d-110">Third party add-ons</span></span>
1. <span data-ttu-id="6400d-111">Parte do Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="6400d-111">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="6400d-112">O processo de aprovação para envios de novos provedores de dados para o MRTK variará caso a caso e será comunicado no momento da proposta inicial.</span><span class="sxs-lookup"><span data-stu-id="6400d-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="6400d-113">As propostas podem ser enviadas criando um novo problema de tipo [ *de Solicitação* de Recurso](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="6400d-113">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-ons"></a><span data-ttu-id="6400d-114">Complementos de terceiros</span><span class="sxs-lookup"><span data-stu-id="6400d-114">Third party add-ons</span></span>

<span data-ttu-id="6400d-115">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="6400d-115">**Namespace**</span></span>

<span data-ttu-id="6400d-116">Os provedores de dados precisam ter um namespace para atenuar possíveis colisões de nomes.</span><span class="sxs-lookup"><span data-stu-id="6400d-116">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="6400d-117">É recomendável que o namespace inclua os componentes a seguir.</span><span class="sxs-lookup"><span data-stu-id="6400d-117">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="6400d-118">Nome da empresa que produz o complemento</span><span class="sxs-lookup"><span data-stu-id="6400d-118">Company name producing the add-on</span></span>
- <span data-ttu-id="6400d-119">Área do recurso</span><span class="sxs-lookup"><span data-stu-id="6400d-119">Feature area</span></span>

<span data-ttu-id="6400d-120">Por exemplo, um provedor de configurações de câmera criado e enviado pela empresa Contoso pode ser *"Contoso.MixedReality.Toolkit.Camera".*</span><span class="sxs-lookup"><span data-stu-id="6400d-120">For example, a camera settings provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.Camera"*.</span></span>

<span data-ttu-id="6400d-121">**Estrutura de pastas**</span><span class="sxs-lookup"><span data-stu-id="6400d-121">**Folder structure**</span></span>

<span data-ttu-id="6400d-122">É recomendável que o código-fonte para provedores de dados seja organizado em uma hierarquia de pastas, conforme mostrado na imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="6400d-122">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Estrutura de pasta de exemplo](../images/camera-system/ExampleProviderFolderStructure.png)

<span data-ttu-id="6400d-124">Onde a *pasta ContosoCamera* contém a implementação do provedor de dados, a pasta *Editor*  contém o inspetor (e qualquer outro código específico do editor do Unity) e a pasta Perfis contém um ou mais objetos de script de perfil pré-criados.</span><span class="sxs-lookup"><span data-stu-id="6400d-124">Where the *ContosoCamera* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="6400d-125">Envio do MRTK</span><span class="sxs-lookup"><span data-stu-id="6400d-125">MRTK submission</span></span>

<span data-ttu-id="6400d-126">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="6400d-126">**Namespace**</span></span>

<span data-ttu-id="6400d-127">Se um provedor de configurações de câmera estiver sendo enviado para o [repositório Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity), o namespace **deverá** começar com Microsoft. MixedReality. Toolkit (por exemplo: *Microsoft. MixedReality. Toolkit. CameraSystem*).</span><span class="sxs-lookup"><span data-stu-id="6400d-127">If a camera settings provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.CameraSystem*).</span></span>

<span data-ttu-id="6400d-128">**Estrutura de pastas**</span><span class="sxs-lookup"><span data-stu-id="6400d-128">**Folder structure**</span></span>

<span data-ttu-id="6400d-129">Todo o código deve estar localizado em uma pasta abaixo de MRTK/Providers (por exemplo: MRTK/Providers/UnityAR).</span><span class="sxs-lookup"><span data-stu-id="6400d-129">All code must be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/UnityAR).</span></span>

## <a name="define-the-camera-settings-object"></a><span data-ttu-id="6400d-130">Definir o objeto de configurações da câmera</span><span class="sxs-lookup"><span data-stu-id="6400d-130">Define the camera settings object</span></span>

<span data-ttu-id="6400d-131">A primeira etapa na criação de um provedor de configurações de câmera é determinar o tipo de dados (por exemplo, malhas ou aviões) que ele fornecerá aos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="6400d-131">The first step in creating a camera settings provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="6400d-132">Todos os objetos de dados espaciais devem implementar a [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="6400d-132">All spatial data objects must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface.</span></span>

## <a name="implement-the-settings-provider"></a><span data-ttu-id="6400d-133">Implementar o provedor de configurações</span><span class="sxs-lookup"><span data-stu-id="6400d-133">Implement the settings provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="6400d-134">Especificar a interface e/ou a herança de classe base</span><span class="sxs-lookup"><span data-stu-id="6400d-134">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="6400d-135">Todos os provedores de configurações de câmera devem implementar a [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface, que especifica a funcionalidade mínima exigida pelo sistema de câmera.</span><span class="sxs-lookup"><span data-stu-id="6400d-135">All camera settings providers must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface, which specifies the minimum functionality required by the camera system.</span></span> <span data-ttu-id="6400d-136">O MRTK Foundation inclui a [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) classe que fornece uma implementação padrão da funcionalidade necessária.</span><span class="sxs-lookup"><span data-stu-id="6400d-136">The MRTK foundation includes the [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) class which provides a default implementation of the required functionality.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="6400d-137">Aplicar o atributo MixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="6400d-137">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="6400d-138">Uma etapa fundamental na criação de um provedor de configurações de câmera é aplicar o [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) atributo à classe.</span><span class="sxs-lookup"><span data-stu-id="6400d-138">A key step in creating a camera settings provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="6400d-139">Esta etapa permite definir o perfil padrão e as plataformas para o provedor de dados, quando selecionado no perfil de sistema da câmera, bem como nome, caminho da pasta e muito mais.</span><span class="sxs-lookup"><span data-stu-id="6400d-139">This step enables setting the default profile and platform(s) for the data provider, when selected in the Camera System profile as well as name, folder path, and more.</span></span>

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="6400d-140">Implementar os métodos IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="6400d-140">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="6400d-141">Depois que a classe tiver sido definida, a próxima etapa será fornecer a implementação da [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="6400d-141">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="6400d-142">A [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) classe, por meio da [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) classe, fornece implementações vazias para [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) métodos.</span><span class="sxs-lookup"><span data-stu-id="6400d-142">The [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="6400d-143">Os detalhes desses métodos geralmente são específicos do provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="6400d-143">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="6400d-144">Os métodos que devem ser implementados pelo provedor de dados são:</span><span class="sxs-lookup"><span data-stu-id="6400d-144">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> <span data-ttu-id="6400d-145">Nem todos os provedores de configurações precisarão de implementações para todos esses métodos.</span><span class="sxs-lookup"><span data-stu-id="6400d-145">Not all settings providers will require implementations for all of these methods.</span></span> <span data-ttu-id="6400d-146">É altamente recomendável que `Destroy()` e `Initialize()` seja implementado no mínimo.</span><span class="sxs-lookup"><span data-stu-id="6400d-146">It is highly recommended that `Destroy()` and `Initialize()` be implemented at a minimum.</span></span>

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="6400d-147">Implementar a lógica do provedor de dados</span><span class="sxs-lookup"><span data-stu-id="6400d-147">Implement the data provider logic</span></span>

<span data-ttu-id="6400d-148">A próxima etapa é adicionar a lógica do provedor de configurações implementando [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) .</span><span class="sxs-lookup"><span data-stu-id="6400d-148">The next step is to add the logic of the settings provider by implementing [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider).</span></span> <span data-ttu-id="6400d-149">Essa parte do provedor de dados normalmente será específica da configuração da câmera.</span><span class="sxs-lookup"><span data-stu-id="6400d-149">This portion of the data provider will typically be camera configuration specific.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="6400d-150">Criar o perfil e o inspetor</span><span class="sxs-lookup"><span data-stu-id="6400d-150">Create the profile and inspector</span></span>

<span data-ttu-id="6400d-151">No Kit de Ferramentas de Realidade Misturada, os provedores de dados são configurados usando [perfis](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6400d-151">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="6400d-152">Definir o perfil</span><span class="sxs-lookup"><span data-stu-id="6400d-152">Define the profile</span></span>

<span data-ttu-id="6400d-153">O conteúdo do perfil deve espelhar as opções de configuração selecionáveis pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="6400d-153">Profile contents should mirror the developer selectable configuration options.</span></span> <span data-ttu-id="6400d-154">Todas as propriedades configuráveis pelo usuário definidas em cada interface também devem estar contidas com o perfil.</span><span class="sxs-lookup"><span data-stu-id="6400d-154">Any user configurable properties defined in each interface should also be contained with the profile.</span></span>

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

<span data-ttu-id="6400d-155">O atributo pode ser aplicado à classe de perfil para permitir que os clientes criem uma instância de perfil usando o menu Criar Perfis do Kit de Ferramentas de Realidade `CreateAssetMenu`   >    >    >   Misturada de Ativos.</span><span class="sxs-lookup"><span data-stu-id="6400d-155">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="6400d-156">Implementar o inspetor</span><span class="sxs-lookup"><span data-stu-id="6400d-156">Implement the inspector</span></span>

<span data-ttu-id="6400d-157">Inspetores de perfil são a interface do usuário para configurar e exibir o conteúdo do perfil.</span><span class="sxs-lookup"><span data-stu-id="6400d-157">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="6400d-158">Cada inspetor de perfil deve estender a [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe.</span><span class="sxs-lookup"><span data-stu-id="6400d-158">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="6400d-159">O `CustomEditor` atributo informa ao Unity o tipo de ativo ao qual o inspetor se aplica.</span><span class="sxs-lookup"><span data-stu-id="6400d-159">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="6400d-160">Criar definições de assembly</span><span class="sxs-lookup"><span data-stu-id="6400d-160">Create assembly definition(s)</span></span>

<span data-ttu-id="6400d-161">O Kit de Ferramentas de Realidade Misturada usa arquivos de definição de assembly ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) para especificar dependências entre componentes, bem como para ajudar o Unity a reduzir o tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="6400d-161">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="6400d-162">É recomendável que os arquivos de definição de assembly sejam criados para todos os provedores de dados e seus componentes do editor.</span><span class="sxs-lookup"><span data-stu-id="6400d-162">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="6400d-163">Usando a [estrutura de](#namespace-and-folder-structure) pastas no exemplo anterior, haveria dois arquivos .asmdef para o provedor de dados ContosoCamera.</span><span class="sxs-lookup"><span data-stu-id="6400d-163">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoCamera data provider.</span></span>

<span data-ttu-id="6400d-164">A primeira definição de assembly é para o provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="6400d-164">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="6400d-165">Neste exemplo, ele será chamado contosoCamera e estará localizado na pasta *ContosoCamera do* exemplo.</span><span class="sxs-lookup"><span data-stu-id="6400d-165">For this example, it will be called ContosoCamera and will be located in the example's *ContosoCamera* folder.</span></span> <span data-ttu-id="6400d-166">Essa definição de assembly deve especificar uma dependência no Microsoft.MixedReality.Toolkit e em todos os outros assemblies dos quais ela depende.</span><span class="sxs-lookup"><span data-stu-id="6400d-166">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="6400d-167">A definição de assembly ContosoCameraEditor especificará o inspetor de perfil e qualquer código específico do editor.</span><span class="sxs-lookup"><span data-stu-id="6400d-167">The ContosoCameraEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="6400d-168">Esse arquivo deve estar localizado na pasta raiz do código do editor.</span><span class="sxs-lookup"><span data-stu-id="6400d-168">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="6400d-169">Neste exemplo, o arquivo estará localizado na pasta *ContosoCamera\Editor* .</span><span class="sxs-lookup"><span data-stu-id="6400d-169">In this example, the file will be located in the *ContosoCamera\Editor* folder.</span></span> <span data-ttu-id="6400d-170">Essa definição de assembly conterá uma referência ao assembly ContosoCamera, bem como:</span><span class="sxs-lookup"><span data-stu-id="6400d-170">This assembly definition will contain a reference to the ContosoCamera assembly as well as:</span></span>

- <span data-ttu-id="6400d-171">Microsoft. MixedReality. Toolkit</span><span class="sxs-lookup"><span data-stu-id="6400d-171">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="6400d-172">Microsoft. MixedReality. Toolkit. editor. Inspectors</span><span class="sxs-lookup"><span data-stu-id="6400d-172">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="6400d-173">Microsoft. MixedReality. Toolkit. editor. Utilities</span><span class="sxs-lookup"><span data-stu-id="6400d-173">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="6400d-174">Registrar o provedor de dados</span><span class="sxs-lookup"><span data-stu-id="6400d-174">Register the data provider</span></span>

<span data-ttu-id="6400d-175">Depois de criado, o provedor de dados pode ser registrado com o sistema de câmera a ser usado no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6400d-175">Once created, the data provider can be registered with the Camera system to be used in the application.</span></span>

![Selecionando o provedor de configurações da câmera](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="6400d-177">Empacotamento e distribuição</span><span class="sxs-lookup"><span data-stu-id="6400d-177">Packaging and distribution</span></span>

<span data-ttu-id="6400d-178">Os provedores de dados que são distribuídos como componentes de terceiros têm os detalhes específicos de empacotamento e distribuição deixados para a preferência do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="6400d-178">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="6400d-179">Provavelmente, a solução mais comum será gerar um. unitypackage e distribuir por meio do repositório de ativos do Unity.</span><span class="sxs-lookup"><span data-stu-id="6400d-179">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="6400d-180">Se um provedor de dados for enviado e aceito como parte do pacote do Microsoft Mixed Reality Toolkit, a equipe do Microsoft MRTK irá empacotá-lo e distribuí-lo como parte das ofertas do MRTK.</span><span class="sxs-lookup"><span data-stu-id="6400d-180">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="6400d-181">Confira também</span><span class="sxs-lookup"><span data-stu-id="6400d-181">See also</span></span>

- [<span data-ttu-id="6400d-182">Visão geral do sistema de câmera</span><span class="sxs-lookup"><span data-stu-id="6400d-182">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="6400d-183">`BaseCameraSettingsProvider` classe</span><span class="sxs-lookup"><span data-stu-id="6400d-183">`BaseCameraSettingsProvider` class</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [<span data-ttu-id="6400d-184">`IMixedRealityCameraSettingsProvider` interface</span><span class="sxs-lookup"><span data-stu-id="6400d-184">`IMixedRealityCameraSettingsProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [<span data-ttu-id="6400d-185">`IMixedRealityDataProvider` interface</span><span class="sxs-lookup"><span data-stu-id="6400d-185">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
