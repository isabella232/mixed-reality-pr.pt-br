---
title: Criando um provedor de dados do sistema de entrada
description: documentação para criar o sistema de entrada e o provedor de dados no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 0b6012871a4d4988fdb70336a3c33455f479bcac
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281928"
---
# <a name="creating-an-input-system-data-provider"></a>Criando um provedor de dados do sistema de entrada

O sistema de entrada de Toolkit Mixed Reality é um sistema extensível para habilenciar o suporte ao dispositivo de entrada. Para adicionar suporte para uma nova plataforma de hardware, um provedor de dados de entrada personalizado pode ser necessário.

Este artigo descreve como criar provedores de dados personalizados, também chamados de gerenciadores de dispositivos, para o sistema de entrada. O código de exemplo mostrado aqui é do [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .

> O código completo usado neste exemplo pode ser encontrado na pasta MRTK/Providers/WindowsMixedReality.

## <a name="namespace-and-folder-structure"></a>Estrutura de namespace e pasta

Os provedores de dados podem ser distribuídos como um complemento de terceiros ou como parte do microsoft mixed reality Toolkit. O processo de aprovação para envios de novos provedores de dados para o MRTK variará caso a caso e será comunicado no momento da proposta inicial.

> [!Important]
> Se um provedor de dados do sistema de entrada estiver sendo enviado para o repositório Toolkit Mixed [Reality](https://github.com/Microsoft/MixedRealityToolkit-Unity), o **namespace** deverá começar com Microsoft.MixedReality. Toolkit (por ex. Microsoft.MixedReality.Toolkit. WindowsMixedReality) e o código devem estar localizados em uma pasta abaixo de MRTK/Providers (por ex. MRTK/Providers/WindowsMixedReality).

### <a name="namespace"></a>Namespace

Os provedores de dados precisam ter um namespace para atenuar possíveis colisões de nomes. É recomendável que o namespace inclua os componentes a seguir.

- Nome da empresa
- Área do recurso

Por exemplo, um provedor de dados de entrada criado pela empresa Contoso pode ser "Contoso.MixedReality. Toolkit. Entrada".

### <a name="recommended-folder-structure"></a>Estrutura de pastas recomendada

É recomendável que o código-fonte para provedores de dados seja organizado em uma hierarquia de pastas, conforme mostrado na imagem a seguir.

![Estrutura de pasta de exemplo](../images/input/ExampleProviderFolderStructure.png)

Onde ContosoInput contém a implementação do provedor de dados, a pasta Editor contém o inspetor (e qualquer outro código específico do editor do Unity), a pasta Texturas contém imagens dos controladores com suporte e Perfis contém um ou mais perfis pré-criados.

> [!Note]
> Algumas imagens comuns do controlador podem ser encontradas na pasta MixedRealityToolkit\StandardAssets\Textures.

## <a name="implement-the-data-provider"></a>Implementar o provedor de dados

### <a name="specify-interface-andor-base-class-inheritance"></a>Especificar a herança da interface e/ou da classe base

Todos os provedores de dados do sistema de entrada devem implementar a interface , que especifica a funcionalidade [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) mínima exigida pelo sistema de entrada. A base do MRTK inclui [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) a classe que fornece uma implementação padrão dessa funcionalidade necessária. Para dispositivos que se baseam na classe UInput do Unity, [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) a classe pode ser usada como uma classe base.

> [!Note]
> As `BaseInputDeviceManager` classes e fornecem a implementação `UnityJoystickManager` `IMixedRealityInputDeviceManager` necessária.

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> `IMixedRealityCapabilityCheck` é usado pelo para indicar que ele dá suporte a um conjunto de funcionalidades de entrada, especificamente; mãos articuladas, mãos com gesto de olhar e `WindowsMixedRealityDeviceManager` controladores de movimento.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Aplicar o atributo MixedRealityDataProvider

Uma etapa fundamental da criação de um provedor de dados do sistema de entrada é aplicar [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) o atributo à classe . Esta etapa permite definir o perfil padrão e as plataformas para o provedor, quando selecionado no perfil do sistema de entrada.

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implementar os métodos IMixedRealityDataProvider

Depois que a classe tiver sido definida, a próxima etapa será fornecer a implementação da [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface .

> [!Note]
> A `BaseInputDeviceManager` classe , por meio da classe , fornece apenas `BaseService` implementações vazias para `IMixedRealityDataProvider` métodos. Os detalhes desses métodos geralmente são específicos do provedor de dados.

Os métodos que devem ser implementados pelo provedor de dados são:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Implementar a lógica do provedor de dados

A próxima etapa é adicionar a lógica para gerenciar os dispositivos de entrada, incluindo todos os controladores com suporte.

### <a name="implement-the-controller-classes"></a>Implementar as classes do controlador

 O exemplo do `WindowsMixedRealityDeviceManager` define e implementa as classes de controlador a seguir.

> O código-fonte para cada uma dessas classes pode ser encontrado na pasta MRTK/Providers/WindowsMixedReality.

- WindowsMixedRealityArticulatedHand.cs
- WindowsMixedRealityController.cs
- WindowsMixedRealityGGVHand.cs

> [!Note]
> Nem todos os gerenciadores de dispositivos darão suporte a vários tipos de controlador.

#### <a name="apply-the-mixedrealitycontroller-attribute"></a>Aplicar o atributo MixedRealityController

Em seguida, aplique [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) o atributo à classe . Esse atributo especifica o tipo de controlador (por exemplo: mão articulada), a mão (por exemplo: esquerda ou direita) e uma imagem de controlador opcional.

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a>Configurar os mapeamentos de interação

A próxima etapa é definir o conjunto de mapeamentos de interação com suporte pelo controlador. Para dispositivos que recebem seus dados por [](../tools/controller-mapping-tool.md) meio da classe Entrada do Unity, a ferramenta de mapeamento do controlador é um recurso útil para confirmar os mapeamentos de eixo e botão corretos para atribuir a interações.

O exemplo a seguir é abreviado da classe , localizada na `GenericOpenVRController` pasta MRTK/Providers/OpenVR.

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
>A [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) classe fornece constantes simbólicas para as definições de botão e eixo de entrada do Unity.

### <a name="raise-notification-events"></a>Ative eventos de notificação

Para permitir que os aplicativos respondam à entrada do usuário, o provedor de dados gera eventos de notificação correspondentes às alterações de estado do controlador, conforme definido nas [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces e .

Para controles de tipo digital (botão), aumente os eventos OnInputDown e OnInputUp.

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

Para controles análogos (por exemplo: posição do touchpad), o evento InputChanged deve ser gerado.

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a>Adicionar instrumentação do Unity Profiler

O desempenho é essencial em aplicativos de realidade misturada. Cada componente adiciona alguma sobrecarga para a qual os aplicativos devem levar em conta. Para esse fim, é importante que todos os provedores de dados de entrada contenham instrumentação do Unity Profiler em loop interno e caminhos de código frequentemente utilizados.

É recomendável implementar o padrão utilizado pelo MRTK ao instrumentar provedores personalizados.

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
> O nome usado para identificar o marcador do profiler é arbitrário. O MRTK usa o padrão a seguir.
>
> "[product] className.methodName – observação opcional"
>
> É recomendável que os provedores de dados personalizados sigam um padrão semelhante para ajudar a simplificar a identificação de componentes e métodos específicos ao analisar rastreamentos.

## <a name="create-the-profile-and-inspector"></a>Criar o perfil e o inspetor

No Toolkit realidade misturada, os provedores de dados são configurados usando [perfis](../profiles/profiles.md).

Provedores de dados com opções de configuração adicionais (por exemplo: [InputSimulationService](../input-simulation/input-simulation-service.md)) devem criar um perfil e um inspetor para permitir que os clientes modifiquem o comportamento para atender melhor às necessidades do aplicativo.

> O código completo para o exemplo nesta seção pode ser encontrado no MRTK. Pasta Services/InputSimulation.

### <a name="define-the-profile"></a>Definir o perfil

O conteúdo do perfil deve espelhar as propriedades acessíveis do observador (por ex. intervalo de atualização). Todas as propriedades configuráveis pelo usuário definidas em cada interface devem estar contidas com o perfil.

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

O atributo pode ser aplicado à classe de perfil para permitir que os clientes criem uma instância de perfil usando o menu Criar > Ativos > Realidade `CreateAssetMenu` **Misturada Toolkit > Perfis.**

### <a name="implement-the-inspector"></a>Implementar o inspetor

Inspetores de perfil são a interface do usuário para configurar e exibir o conteúdo do perfil. Cada inspetor de perfil deve estender [a classe 'BaseMixedRealityToolkitConfigurationProfileInspector.](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector)

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

O `CustomEditor` atributo informa ao Unity o tipo de ativo ao qual o inspetor se aplica.

## <a name="create-assembly-definitions"></a>Criar definições de assembly

A Toolkit de realidade misturada usa arquivos de definição de assembly ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) para especificar dependências entre componentes, bem como para ajudar o Unity a reduzir o tempo de compilação.

É recomendável que os arquivos de definição de assembly sejam criados para todos os provedores de dados e seus componentes do editor.

Usando a [estrutura de](#recommended-folder-structure) pastas no exemplo anterior, haverá dois arquivos .asmdef para o provedor de dados ContosoInput.

A primeira definição de assembly é para o provedor de dados. Neste exemplo, ele será chamado contosoInput e estará localizado na pasta ContosoInput do exemplo.
Essa definição de assembly deve especificar uma dependência em Microsoft.MixedReality. Toolkit e quaisquer outros assemblies dos quais ele depende.

A definição de assembly ContosoInputEditor especificará o inspetor de perfil e qualquer código específico do editor. Esse arquivo deve estar localizado na pasta raiz do código do editor. Neste exemplo, o arquivo estará localizado na pasta ContosoInput\Editor. Essa definição de assembly conterá uma referência ao assembly ContosoInput, bem como:

- Microsoft.MixedReality. Toolkit
- Microsoft.MixedReality. Toolkit. Editor.Inspectors
- Microsoft.MixedReality. Toolkit. Editor.Utilities

## <a name="register-the-data-provider"></a>Registrar o provedor de dados

Depois de criado, o provedor de dados pode ser registrado com o sistema de entrada e ser usado no aplicativo.

![Provedores de dados do sistema de entrada registrados](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a>Empacotamento e distribuição

Provedores de dados distribuídos como componentes de terceiros têm os detalhes específicos de empacotamento e distribuição deixados à preferência do desenvolvedor. Provavelmente, a solução mais comum será gerar um .unitypackage e distribuir por meio do Asset Store do Unity.

Se um provedor de dados for enviado e aceito como parte do pacote microsoft mixed reality Toolkit, a equipe do Microsoft MRTK o empacota e distribui como parte das ofertas do MRTK.

## <a name="see-also"></a>Confira também

- [Sistema de entrada](overview.md)
- [`BaseInputDeviceManager` classe](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [`IMixedRealityInputDeviceManager` Interface](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [`IMixedRealityInputHandler` Interface](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [`IMixedRealityInputHandler<T>` Interface](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [`IMixedRealityDataProvider` Interface](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` Interface](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [Ferramenta de mapeamento de controlador](../tools/controller-mapping-tool.md)
