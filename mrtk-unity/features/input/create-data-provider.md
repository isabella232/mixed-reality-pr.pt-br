---
title: Criando provedores de dados de entrada
description: documentação para criar o sistema de entrada e o provedor de dados no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: c164fa406ae6822f4d889aff3bf615cf7fa76337
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144077"
---
# <a name="creating-an-input-system-data-provider"></a><span data-ttu-id="ad45c-104">Criando um provedor de dados do sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="ad45c-104">Creating an input system data provider</span></span>

<span data-ttu-id="ad45c-105">O sistema de entrada do Kit de Ferramentas de Realidade Misturada é um sistema extensível para habilenciar o suporte ao dispositivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="ad45c-105">The Mixed Reality Toolkit input system is an extensible system for enabling input device support.</span></span> <span data-ttu-id="ad45c-106">Para adicionar suporte para uma nova plataforma de hardware, um provedor de dados de entrada personalizado pode ser necessário.</span><span class="sxs-lookup"><span data-stu-id="ad45c-106">To add support for a new hardware platform, a custom input data provider may be required.</span></span>

<span data-ttu-id="ad45c-107">Este artigo descreve como criar provedores de dados personalizados, também chamados de gerenciadores de dispositivos, para o sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="ad45c-107">This article describes how to create custom data providers, also called device managers, for the input system.</span></span> <span data-ttu-id="ad45c-108">O código de exemplo mostrado aqui é do [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="ad45c-108">The example code shown here is from the [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager).</span></span>

> <span data-ttu-id="ad45c-109">O código completo usado neste exemplo pode ser encontrado na pasta MRTK/Providers/WindowsMixedReality.</span><span class="sxs-lookup"><span data-stu-id="ad45c-109">The complete code used in this example can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="ad45c-110">Estrutura de namespace e pasta</span><span class="sxs-lookup"><span data-stu-id="ad45c-110">Namespace and folder structure</span></span>

<span data-ttu-id="ad45c-111">Os provedores de dados podem ser distribuídos como um complemento de terceiros ou como parte do Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="ad45c-111">Data providers can be distributed as a third party add-on or as a part of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="ad45c-112">O processo de aprovação para envios de novos provedores de dados para o MRTK variará caso a caso e será comunicado no momento da proposta inicial.</span><span class="sxs-lookup"><span data-stu-id="ad45c-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span>

> [!Important]
> <span data-ttu-id="ad45c-113">Se um provedor de dados do sistema de entrada estiver sendo enviado para o repositório do Kit de Ferramentas de Realidade Misturada [,](https://github.com/Microsoft/MixedRealityToolkit-Unity)o **namespace** deverá começar com Microsoft.MixedReality.Toolkit (por exemplo: Microsoft.MixedReality.Toolkit.WindowsMixedReality) e o código deverá estar localizado em uma pasta abaixo de MRTK/Providers (por exemplo: MRTK/Providers/WindowsMixedReality).</span><span class="sxs-lookup"><span data-stu-id="ad45c-113">If an input system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: Microsoft.MixedReality.Toolkit.WindowsMixedReality) and the code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/WindowsMixedReality).</span></span>

### <a name="namespace"></a><span data-ttu-id="ad45c-114">Namespace</span><span class="sxs-lookup"><span data-stu-id="ad45c-114">Namespace</span></span>

<span data-ttu-id="ad45c-115">Os provedores de dados precisam ter um namespace para atenuar possíveis colisões de nomes.</span><span class="sxs-lookup"><span data-stu-id="ad45c-115">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="ad45c-116">É recomendável que o namespace inclua os componentes a seguir.</span><span class="sxs-lookup"><span data-stu-id="ad45c-116">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="ad45c-117">Nome da empresa</span><span class="sxs-lookup"><span data-stu-id="ad45c-117">Company name</span></span>
- <span data-ttu-id="ad45c-118">Área do recurso</span><span class="sxs-lookup"><span data-stu-id="ad45c-118">Feature area</span></span>

<span data-ttu-id="ad45c-119">Por exemplo, um provedor de dados de entrada criado pela empresa Contoso pode ser "Contoso.MixedReality.Toolkit.Input".</span><span class="sxs-lookup"><span data-stu-id="ad45c-119">For example, an input data provider created by the Contoso company may be "Contoso.MixedReality.Toolkit.Input".</span></span>

### <a name="recommended-folder-structure"></a><span data-ttu-id="ad45c-120">Estrutura de pastas recomendada</span><span class="sxs-lookup"><span data-stu-id="ad45c-120">Recommended folder structure</span></span>

<span data-ttu-id="ad45c-121">É recomendável que o código-fonte para provedores de dados seja organizado em uma hierarquia de pastas, conforme mostrado na imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="ad45c-121">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Estrutura de pasta de exemplo](../images/input/ExampleProviderFolderStructure.png)

<span data-ttu-id="ad45c-123">Onde ContosoInput contém a implementação do provedor de dados, a pasta Editor contém o inspetor (e qualquer outro código específico do editor do Unity), a pasta Texturas contém imagens dos controladores com suporte e Perfis contém um ou mais perfis pré-criados.</span><span class="sxs-lookup"><span data-stu-id="ad45c-123">Where ContosoInput contains the implementation of the data provider, the Editor folder contains the inspector (and any other Unity editor specific code), the Textures folder contains images of the supported controllers, and Profiles contains one or more pre-made profiles.</span></span>

> [!Note]
> <span data-ttu-id="ad45c-124">Algumas imagens comuns do controlador podem ser encontradas na pasta MixedRealityToolkit\StandardAssets\Textures</span><span class="sxs-lookup"><span data-stu-id="ad45c-124">Some common controller images can be found in the MixedRealityToolkit\StandardAssets\Textures folder.</span></span>

## <a name="implement-the-data-provider"></a><span data-ttu-id="ad45c-125">Implementar o provedor de dados</span><span class="sxs-lookup"><span data-stu-id="ad45c-125">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="ad45c-126">Especificar a interface e/ou a herança de classe base</span><span class="sxs-lookup"><span data-stu-id="ad45c-126">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="ad45c-127">Todos os provedores de dados do sistema de entrada devem implementar a [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface, que especifica a funcionalidade mínima exigida pelo sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="ad45c-127">All input system data providers must implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface, which specifies the minimum functionality required by the input system.</span></span> <span data-ttu-id="ad45c-128">O MRTK Foundation inclui a [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) classe que fornece uma implementação padrão dessa funcionalidade necessária.</span><span class="sxs-lookup"><span data-stu-id="ad45c-128">The MRTK foundation includes the [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) class which provides a default implementation of this required functionality.</span></span> <span data-ttu-id="ad45c-129">Para dispositivos que se baseiam na classe UInput do Unity, a [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) classe pode ser usada como uma classe base.</span><span class="sxs-lookup"><span data-stu-id="ad45c-129">For devices that build upon Unity's UInput class, the [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) class can be used as a base class.</span></span>

> [!Note]
> <span data-ttu-id="ad45c-130">As `BaseInputDeviceManager` `UnityJoystickManager` classes e fornecem a `IMixedRealityInputDeviceManager` implementação necessária.</span><span class="sxs-lookup"><span data-stu-id="ad45c-130">The `BaseInputDeviceManager` and `UnityJoystickManager` classes provide the required `IMixedRealityInputDeviceManager` implementation.</span></span>

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> <span data-ttu-id="ad45c-131">`IMixedRealityCapabilityCheck` é usado pelo `WindowsMixedRealityDeviceManager` para indicar que ele fornece suporte para um conjunto de recursos de entrada, especificamente; mãos articuladas, olhar-gestos de voz e controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="ad45c-131">`IMixedRealityCapabilityCheck` is used by the `WindowsMixedRealityDeviceManager` to indicate that it provides support for a set of input capabilities, specifically; articulated hands, gaze-gesture-voice hands and motion controllers.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="ad45c-132">Aplicar o atributo MixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="ad45c-132">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="ad45c-133">Uma etapa fundamental da criação de um provedor de dados do sistema de entrada é aplicar o [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) atributo à classe.</span><span class="sxs-lookup"><span data-stu-id="ad45c-133">A key step of creating an input system data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="ad45c-134">Esta etapa permite definir o perfil padrão e as plataformas para o provedor, quando selecionado no perfil do sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="ad45c-134">This step enables setting the default profile and platform(s) for the provider, when selected in the input system profile.</span></span>

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealityInputSystem),
    SupportedPlatforms.WindowsUniversal,
    "Windows Mixed Reality Device Manager")]
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="ad45c-135">Implementar os métodos IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="ad45c-135">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="ad45c-136">Depois que a classe tiver sido definida, a próxima etapa será fornecer a implementação da [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="ad45c-136">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!Note]
> <span data-ttu-id="ad45c-137">A `BaseInputDeviceManager` classe, por meio da `BaseService` classe, fornece apenas implementações vazias para `IMixedRealityDataProvider` métodos.</span><span class="sxs-lookup"><span data-stu-id="ad45c-137">The `BaseInputDeviceManager` class, via the `BaseService` class, provides only empty implementations for `IMixedRealityDataProvider` methods.</span></span> <span data-ttu-id="ad45c-138">Os detalhes desses métodos geralmente são específicos do provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="ad45c-138">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="ad45c-139">Os métodos que devem ser implementados pelo provedor de dados são:</span><span class="sxs-lookup"><span data-stu-id="ad45c-139">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="ad45c-140">Implementar a lógica do provedor de dados</span><span class="sxs-lookup"><span data-stu-id="ad45c-140">Implement the data provider logic</span></span>

<span data-ttu-id="ad45c-141">A próxima etapa é adicionar a lógica para gerenciar os dispositivos de entrada, incluindo os controladores a serem suportados.</span><span class="sxs-lookup"><span data-stu-id="ad45c-141">The next step is to add the logic for managing the input devices, including any controllers to be supported.</span></span>

### <a name="implement-the-controller-classes"></a><span data-ttu-id="ad45c-142">Implementar as classes do controlador</span><span class="sxs-lookup"><span data-stu-id="ad45c-142">Implement the controller classes</span></span>

 <span data-ttu-id="ad45c-143">O exemplo de `WindowsMixedRealityDeviceManager` define e implementa as classes de controlador a seguir.</span><span class="sxs-lookup"><span data-stu-id="ad45c-143">The example of the `WindowsMixedRealityDeviceManager` defines and implements the following controller classes.</span></span>

> <span data-ttu-id="ad45c-144">O código-fonte para cada uma dessas classes pode ser encontrado na pasta MRTK/Providers/WindowsMixedReality.</span><span class="sxs-lookup"><span data-stu-id="ad45c-144">The source code for each of these classes can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

- <span data-ttu-id="ad45c-145">WindowsMixedRealityArticulatedHand. cs</span><span class="sxs-lookup"><span data-stu-id="ad45c-145">WindowsMixedRealityArticulatedHand.cs</span></span>
- <span data-ttu-id="ad45c-146">WindowsMixedRealityController. cs</span><span class="sxs-lookup"><span data-stu-id="ad45c-146">WindowsMixedRealityController.cs</span></span>
- <span data-ttu-id="ad45c-147">WindowsMixedRealityGGVHand. cs</span><span class="sxs-lookup"><span data-stu-id="ad45c-147">WindowsMixedRealityGGVHand.cs</span></span>

> [!Note]
> <span data-ttu-id="ad45c-148">Nem todos os gerenciadores de dispositivos terão suporte para vários tipos de controlador.</span><span class="sxs-lookup"><span data-stu-id="ad45c-148">Not all device managers will support multiple controller types.</span></span>

#### <a name="apply-the-mixedrealitycontroller-attribute"></a><span data-ttu-id="ad45c-149">Aplicar o atributo MixedRealityController</span><span class="sxs-lookup"><span data-stu-id="ad45c-149">Apply the MixedRealityController attribute</span></span>

<span data-ttu-id="ad45c-150">Em seguida, aplique o [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) atributo à classe.</span><span class="sxs-lookup"><span data-stu-id="ad45c-150">Next, apply the [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) attribute to the class.</span></span> <span data-ttu-id="ad45c-151">Esse atributo especifica o tipo de controlador (por exemplo, a mão articulada), a destro/canhoto (ex: esquerda ou direita) e uma imagem de controlador opcional.</span><span class="sxs-lookup"><span data-stu-id="ad45c-151">This attribute specifies the type of controller (ex: articulated hand), the handedness (ex: left or right) and an optional controller image.</span></span>

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a><span data-ttu-id="ad45c-152">Configurar os mapeamentos de interação</span><span class="sxs-lookup"><span data-stu-id="ad45c-152">Configure the interaction mappings</span></span>

<span data-ttu-id="ad45c-153">A próxima etapa é definir o conjunto de mapeamentos de interação com suporte pelo controlador.</span><span class="sxs-lookup"><span data-stu-id="ad45c-153">The next step is to define the set of interaction mappings supported by the controller.</span></span> <span data-ttu-id="ad45c-154">Para dispositivos que recebem seus dados por meio da classe de entrada do Unity, a [ferramenta de mapeamento de controlador](../tools/controller-mapping-tool.md) é um recurso útil para confirmar o eixo correto e os mapeamentos de botão a serem atribuídos às interações.</span><span class="sxs-lookup"><span data-stu-id="ad45c-154">For devices that receive their data via Unity's Input class, the [controller mapping tool](../tools/controller-mapping-tool.md) is a helpful resource to confirm the correct axis and button mappings to assign to interactions.</span></span>

<span data-ttu-id="ad45c-155">O exemplo a seguir é abreviado da `GenericOpenVRController` classe, localizada na pasta MRTK/Providers/OpenVR.</span><span class="sxs-lookup"><span data-stu-id="ad45c-155">The following example is abbreviated from the `GenericOpenVRController` class, located in the MRTK/Providers/OpenVR folder.</span></span>

```c#
public override MixedRealityInteractionMapping[] DefaultLeftHandedInteractions => new[]
{
    // Controller Pose
    new MixedRealityInteractionMapping(0, "Spatial Pointer", AxisType.SixDof, DeviceInputType.SpatialPointer, MixedRealityInputAction.None),
    // Left Trigger Squeeze
    new MixedRealityInteractionMapping(1, "Trigger Position", AxisType.SingleAxis, DeviceInputType.Trigger, ControllerMappingLibrary.AXIS_9),
    // Left Trigger Press (Select)
    new MixedRealityInteractionMapping(2, "Trigger Press (Select)", AxisType.Digital, DeviceInputType.TriggerPress, KeyCode.JoystickButton14),
};
```

>[!Note]
><span data-ttu-id="ad45c-156">A [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) classe fornece constantes simbólicas para o eixo de entrada do Unity e definições de botão.</span><span class="sxs-lookup"><span data-stu-id="ad45c-156">The [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) class provides symbolic constants for the Unity input axis and button definitions.</span></span>

### <a name="raise-notification-events"></a><span data-ttu-id="ad45c-157">Gerar eventos de notificação</span><span class="sxs-lookup"><span data-stu-id="ad45c-157">Raise notification events</span></span>

<span data-ttu-id="ad45c-158">Para permitir que os aplicativos respondam à entrada do usuário, o provedor de dados gera eventos de notificação correspondentes às alterações de estado do controlador, conforme definido nas [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces e.</span><span class="sxs-lookup"><span data-stu-id="ad45c-158">To enable applications to respond to input from the user, the data provider raises notification events corresponding to controller state changes as defined in the [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) and [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces.</span></span>

<span data-ttu-id="ad45c-159">Para controles de tipo digital (Button), gere os eventos OnInputDown e OnInputUp.</span><span class="sxs-lookup"><span data-stu-id="ad45c-159">For digital (button) type controls, raise the OnInputDown and OnInputUp events.</span></span>

```c#
// inputAction is the input event that is to be raised.
if (interactionSourceState.touchpadPressed)
{
    InputSystem?.RaiseOnInputDown(InputSource, ControllerHandedness, inputAction);
}
else
{
    InputSystem?.RaiseOnInputUp(InputSource, ControllerHandedness, inputAction);
}
```

<span data-ttu-id="ad45c-160">Para controles analógicos (por exemplo, posição do Touchpad), o evento de Entradachanged deve ser gerado.</span><span class="sxs-lookup"><span data-stu-id="ad45c-160">For analog controls (ex: touchpad position) the InputChanged event should be raised.</span></span>

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="ad45c-161">Adicionar instrumentação do criador de perfil do Unity</span><span class="sxs-lookup"><span data-stu-id="ad45c-161">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="ad45c-162">O desempenho é essencial em aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="ad45c-162">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="ad45c-163">Cada componente adiciona alguma quantidade de sobrecarga para os aplicativos que devem ser contados.</span><span class="sxs-lookup"><span data-stu-id="ad45c-163">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="ad45c-164">Para esse fim, é importante que todos os provedores de dados de entrada contenham instrumentação do Unity Profiler em loop interno e caminhos de código frequentemente utilizados.</span><span class="sxs-lookup"><span data-stu-id="ad45c-164">To this end, it is important that all input data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="ad45c-165">É recomendável implementar o padrão utilizado pelo MRTK ao instrumentar provedores personalizados.</span><span class="sxs-lookup"><span data-stu-id="ad45c-165">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

```c#
        private static readonly ProfilerMarker GetOrAddControllerPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealityDeviceManager.GetOrAddController");

        private async void GetOrAddController(InteractionSourceState interactionSourceState)
        {
            using (GetOrAddControllerPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> <span data-ttu-id="ad45c-166">O nome usado para identificar o marcador do profiler é arbitrário.</span><span class="sxs-lookup"><span data-stu-id="ad45c-166">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="ad45c-167">O MRTK usa o padrão a seguir.</span><span class="sxs-lookup"><span data-stu-id="ad45c-167">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="ad45c-168">"[product] className.methodName – observação opcional"</span><span class="sxs-lookup"><span data-stu-id="ad45c-168">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="ad45c-169">É recomendável que os provedores de dados personalizados sigam um padrão semelhante para ajudar a simplificar a identificação de componentes e métodos específicos ao analisar rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="ad45c-169">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="ad45c-170">Criar o perfil e o inspetor</span><span class="sxs-lookup"><span data-stu-id="ad45c-170">Create the profile and inspector</span></span>

<span data-ttu-id="ad45c-171">No Kit de Ferramentas de Realidade Misturada, os provedores de dados são configurados usando [perfis](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ad45c-171">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

<span data-ttu-id="ad45c-172">Provedores de dados com opções de configuração adicionais (por exemplo: [InputSimulationService](../input-simulation/input-simulation-service.md)) devem criar um perfil e um inspetor para permitir que os clientes modifiquem o comportamento para atender melhor às necessidades do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad45c-172">Data providers with additional configuration options (ex: [InputSimulationService](../input-simulation/input-simulation-service.md)) should create a profile and inspector to allow customers to modify the behavior to best suit the needs of the application.</span></span>

> <span data-ttu-id="ad45c-173">O código completo para o exemplo nesta seção pode ser encontrado no MRTK. Pasta Services/InputSimulation.</span><span class="sxs-lookup"><span data-stu-id="ad45c-173">The complete code for the example in this section can be found in the MRTK.Services/InputSimulation folder.</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="ad45c-174">Definir o perfil</span><span class="sxs-lookup"><span data-stu-id="ad45c-174">Define the profile</span></span>

<span data-ttu-id="ad45c-175">O conteúdo do perfil deve espelhar as propriedades acessíveis do observador (por ex. intervalo de atualização).</span><span class="sxs-lookup"><span data-stu-id="ad45c-175">Profile contents should mirror the accessible properties of the observer (ex: update interval).</span></span> <span data-ttu-id="ad45c-176">Todas as propriedades configuráveis pelo usuário definidas em cada interface devem estar contidas com o perfil.</span><span class="sxs-lookup"><span data-stu-id="ad45c-176">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

<span data-ttu-id="ad45c-177">O atributo pode ser aplicado à classe de perfil para permitir que os clientes criem uma instância de perfil usando o menu Criar > Ativos > Mixed `CreateAssetMenu` **Reality Toolkit > Profiles.**</span><span class="sxs-lookup"><span data-stu-id="ad45c-177">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create > Assets > Mixed Reality Toolkit > Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="ad45c-178">Implementar o inspetor</span><span class="sxs-lookup"><span data-stu-id="ad45c-178">Implement the inspector</span></span>

<span data-ttu-id="ad45c-179">Inspetores de perfil são a interface do usuário para configurar e exibir o conteúdo do perfil.</span><span class="sxs-lookup"><span data-stu-id="ad45c-179">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="ad45c-180">Cada inspetor de perfil deve estender [a classe 'BaseMixedRealityToolkitConfigurationProfileInspector.](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector)</span><span class="sxs-lookup"><span data-stu-id="ad45c-180">Each profile inspector should extend the [\`BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

<span data-ttu-id="ad45c-181">O `CustomEditor` atributo informa ao Unity o tipo de ativo ao qual o inspetor se aplica.</span><span class="sxs-lookup"><span data-stu-id="ad45c-181">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

## <a name="create-assembly-definitions"></a><span data-ttu-id="ad45c-182">Criar definições de assembly</span><span class="sxs-lookup"><span data-stu-id="ad45c-182">Create assembly definition(s)</span></span>

<span data-ttu-id="ad45c-183">O Kit de Ferramentas de Realidade Misturada usa arquivos de definição de assembly ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) para especificar dependências entre componentes, bem como para ajudar o Unity a reduzir o tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ad45c-183">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="ad45c-184">É recomendável que os arquivos de definição de assembly sejam criados para todos os provedores de dados e seus componentes do editor.</span><span class="sxs-lookup"><span data-stu-id="ad45c-184">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="ad45c-185">Usando a [estrutura de pastas](#recommended-folder-structure) no exemplo anterior, haveria dois arquivos. asmdef para o provedor de dados ContosoInput.</span><span class="sxs-lookup"><span data-stu-id="ad45c-185">Using the [folder structure](#recommended-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoInput data provider.</span></span>

<span data-ttu-id="ad45c-186">A primeira definição do assembly é para o provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="ad45c-186">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="ad45c-187">Para este exemplo, ele será chamado de ContosoInput e estará localizado na pasta ContosoInput do exemplo.</span><span class="sxs-lookup"><span data-stu-id="ad45c-187">For this example, it will be called ContosoInput and will be located in the example's ContosoInput folder.</span></span>
<span data-ttu-id="ad45c-188">Essa definição de assembly deve especificar uma dependência em Microsoft. MixedReality. Toolkit e quaisquer outros assemblies sobre os quais ela depende.</span><span class="sxs-lookup"><span data-stu-id="ad45c-188">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="ad45c-189">A definição do assembly ContosoInputEditor especificará o Inspetor de perfil e qualquer código específico do editor.</span><span class="sxs-lookup"><span data-stu-id="ad45c-189">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="ad45c-190">Esse arquivo deve estar localizado na pasta raiz do código do editor.</span><span class="sxs-lookup"><span data-stu-id="ad45c-190">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="ad45c-191">Neste exemplo, o arquivo estará localizado na pasta ContosoInput\Editor.</span><span class="sxs-lookup"><span data-stu-id="ad45c-191">In this example, the file will be located in the ContosoInput\Editor folder.</span></span> <span data-ttu-id="ad45c-192">Essa definição de assembly conterá uma referência ao assembly ContosoInput, bem como:</span><span class="sxs-lookup"><span data-stu-id="ad45c-192">This assembly definition will contain a reference to the ContosoInput assembly as well as:</span></span>

- <span data-ttu-id="ad45c-193">Microsoft. MixedReality. Toolkit</span><span class="sxs-lookup"><span data-stu-id="ad45c-193">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="ad45c-194">Microsoft. MixedReality. Toolkit. editor. Inspectors</span><span class="sxs-lookup"><span data-stu-id="ad45c-194">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="ad45c-195">Microsoft. MixedReality. Toolkit. editor. Utilities</span><span class="sxs-lookup"><span data-stu-id="ad45c-195">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="ad45c-196">Registrar o provedor de dados</span><span class="sxs-lookup"><span data-stu-id="ad45c-196">Register the data provider</span></span>

<span data-ttu-id="ad45c-197">Depois de criado, o provedor de dados pode ser registrado com o sistema de entrada e ser usado no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad45c-197">Once created, the data provider can be registered with the input system and be used in the application.</span></span>

![Provedores de dados do sistema de entrada registrados](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a><span data-ttu-id="ad45c-199">Empacotamento e distribuição</span><span class="sxs-lookup"><span data-stu-id="ad45c-199">Packaging and distribution</span></span>

<span data-ttu-id="ad45c-200">Os provedores de dados que são distribuídos como componentes de terceiros têm os detalhes específicos de empacotamento e distribuição deixados para a preferência do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="ad45c-200">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="ad45c-201">Provavelmente, a solução mais comum será gerar um. unitypackage e distribuir por meio do repositório de ativos do Unity.</span><span class="sxs-lookup"><span data-stu-id="ad45c-201">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="ad45c-202">Se um provedor de dados for enviado e aceito como parte do pacote do Microsoft Mixed Reality Toolkit, a equipe do Microsoft MRTK irá empacotá-lo e distribuí-lo como parte das ofertas do MRTK.</span><span class="sxs-lookup"><span data-stu-id="ad45c-202">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad45c-203">Confira também</span><span class="sxs-lookup"><span data-stu-id="ad45c-203">See also</span></span>

- [<span data-ttu-id="ad45c-204">Sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="ad45c-204">Input system</span></span>](overview.md)
- [<span data-ttu-id="ad45c-205">`BaseInputDeviceManager` classe</span><span class="sxs-lookup"><span data-stu-id="ad45c-205">`BaseInputDeviceManager` class</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [<span data-ttu-id="ad45c-206">`IMixedRealityInputDeviceManager` Interface</span><span class="sxs-lookup"><span data-stu-id="ad45c-206">`IMixedRealityInputDeviceManager` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [<span data-ttu-id="ad45c-207">`IMixedRealityInputHandler` Interface</span><span class="sxs-lookup"><span data-stu-id="ad45c-207">`IMixedRealityInputHandler` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [<span data-ttu-id="ad45c-208">`IMixedRealityInputHandler<T>` Interface</span><span class="sxs-lookup"><span data-stu-id="ad45c-208">`IMixedRealityInputHandler<T>` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [<span data-ttu-id="ad45c-209">`IMixedRealityDataProvider` Interface</span><span class="sxs-lookup"><span data-stu-id="ad45c-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="ad45c-210">`IMixedRealityCapabilityCheck` Interface</span><span class="sxs-lookup"><span data-stu-id="ad45c-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="ad45c-211">Ferramenta de mapeamento de controlador</span><span class="sxs-lookup"><span data-stu-id="ad45c-211">Controller Mapping Tool</span></span>](../tools/controller-mapping-tool.md)
