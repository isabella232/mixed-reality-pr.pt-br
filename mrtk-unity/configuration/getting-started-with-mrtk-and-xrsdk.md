---
title: Introdução ao SDK do MRTK e do XR
description: Página de aterrissagem do MRTK com o XR SDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, XRSDK, XR SDK
ms.openlocfilehash: d3ff4306205cc6548bc5617d727f32a780855439
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647208"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Introdução ao SDK do MRTK e do XR

O XR SDK é o [novo pipeline XR do Unity no Unity 2019,3 e posterior](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). No Unity 2019, ele fornece uma alternativa ao pipeline XR existente. No Unity 2020, ele se tornará o único pipeline XR no Unity.

## <a name="prerequisites"></a>Pré-requisitos

Para começar a usar o kit de ferramentas de realidade misturada, siga [as etapas fornecidas](../install-the-tools.md#importing-the-mixed-reality-toolkit) para adicionar o MRTK a um projeto.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Configurando o Unity para o pipeline do SDK do XR

Atualmente, o pipeline do XR SDK dá suporte a três plataformas: Windows Mixed Reality, Oculus e OpenXR. As seções a seguir abordarão as etapas necessárias para configurar o XR SDK para cada plataforma.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Acesse o **Gerenciador de pacotes do Unity** e instale o pacote de plug-in do Windows XR, que adiciona suporte para a realidade mista do Windows no XR SDK. Isso também obterá alguns pacotes de dependência. 

1. Verifique se todos os itens a seguir foram instalados com êxito:
   * Gerenciamento de plugin XR
   * Plug-in do Windows XR
   * Auxiliares de entrada do XR Legacy

2. Acesse **Editar > Configurações do Projeto**.
3. Clique na guia gerenciamento de plug-ins do XR na janela Configurações do projeto.
4. Vá para as configurações de Plataforma Universal do Windows e verifique se a realidade mista do Windows está marcada em provedores de plug-in.
5. Verifique se inicializar XR na inicialização está marcado.
6. (**_Necessário para comunicação remota do HoloLens no editor, caso contrário, opcional_**) Vá para as configurações autônomas e verifique se a realidade mista do Windows está marcada em provedores de plug-in. Verifique também se inicializar XR na inicialização está marcado.

![Gerenciamento de plugin XR com guia autônoma selecionada](images/xr-management-img-02.png)

7. (**_Opcional_**) Clique na guia realidade misturada do Windows em gerenciamento de plug-in do XR e crie um perfil de configurações personalizadas para alterar os padrões. Se a lista de configurações já estiver lá, nenhum perfil precisará ser criado.

![Gerenciamento de plugin XR com a guia Windows selecionada](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. Siga a guia [como configurar o Oculus Quest no MRTK usando o pipeline do XR SDK](../supported-devices/oculus-quest-mrtk.md) para o final. O guia descreve as etapas necessárias para configurar o Unity e o MRTK para usar o pipeline do SDK do XR para o Oculus Quest.

### <a name="openxr-preview"></a>OpenXR (visualização)

> [!IMPORTANT]
> O OpenXR no Unity só tem suporte no Unity 2020,2 e superior.
>
> Atualmente, ele também dá suporte apenas a compilações de x64 e ARM64.

1. Siga o guia [usando o plug-in Mixed Reality OpenXR plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) , incluindo as etapas para configurar a otimização e o gerenciamento de plug-in do XR para instalar o plug-in do OpenXR em seu projeto. Verifique se os itens a seguir foram instalados com êxito:
   1. Gerenciamento de plugin XR
   1. Plug-in OpenXR
   1. Plug-in OpenXR de realidade misturada
1. Vá para editar configurações de projeto >.
1. Clique na guia gerenciamento de plug-ins do XR na janela Configurações do projeto.
1. Verifique se inicializar XR na inicialização está marcado.
1. (**_Opcional_**) Se estiver direcionando para o HoloLens 2, verifique se você está na plataforma UWP e selecione conjunto de recursos do Microsoft HoloLens

![Gerenciamento de plugin aberto XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Se você tiver um projeto pré-existente que esteja usando MRTK do UPM, verifique se a linha a seguir está no arquivo **link.xml** localizado na pasta MixedRealityToolkit. Generated.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> Para a versão inicial do MRTK e do OpenXR, somente as mãos do HoloLens 2 e os controladores de movimento de realidade do Windows Mixed Realm têm suporte nativo. O suporte para hardware adicional será adicionado em versões futuras.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Configurando o MRTK para o pipeline do SDK do XR
::: moniker range=">= mrtkunity-2021-05" 
Se estiver usando OpenXR, escolha "DefaultOpenXRConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.

Se estiver usando outros tempos de execução do XR na configuração de gerenciamento de plug-in do XR, como o Windows Mixed Reality ou oculus, escolha "DefaultXRSDKConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.

Esses perfis são configurados com os sistemas e provedores corretos, quando necessário. Consulte [os documentos de perfis](../features/profiles/profiles.md#xr-sdk) para obter mais informações sobre o suporte a perfis e amostras com o XR SDK.

Para migrar um perfil existente para o XR SDK, os serviços e provedores de dados a seguir devem ser adicionados. Você poderá ver os novos provedores de dados na guia do SDK do XR

![A guia do SDK do XR](../features/images/xrsdk/XrsdkTabView.png)

### <a name="camera"></a>Câmera

Adicionar os seguintes provedores de dados 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**e**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![Configurações da câmera do XR SDK](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Entrada

Adicionar os seguintes provedores de dados 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR__:

![Configurações de entrada do OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

__Realidade mista do Windows__:

![Configurações de entrada do SDK do XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Limite

Adicionar os seguintes provedores de dados 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Configurações de limite do SDK do XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Conscientização espacial

Adicionar os seguintes provedores de dados 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| Em Andamento | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Configurações de reconhecimento espacial do SDK do XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Mapeamentos de controlador

Se você estiver usando perfis de mapeamento de controlador personalizado, abra um deles e execute o item de menu Mixed Reality Toolkit-> Utilities-> Update-> controlador de mapeamento de perfis para garantir que os novos tipos de controlador do SDK do XR sejam definidos.

## <a name="see-also"></a>Confira também

* [Introdução ao desenvolvimento do AR no Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Introdução ao desenvolvimento VR no Unity](https://docs.unity3d.com/Manual/VROverview.html)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Se estiver usando OpenXR, escolha "DefaultOpenXRConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.

Se estiver usando outros tempos de execução do XR na configuração de gerenciamento de plug-in do XR, como o Windows Mixed Reality ou oculus, escolha "DefaultXRSDKConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.

Esses perfis são configurados com os sistemas e provedores corretos, quando necessário. Consulte [os documentos de perfis](../features/profiles/profiles.md#xr-sdk) para obter mais informações sobre o suporte a perfis e amostras com o XR SDK.

Para migrar um perfil existente para o XR SDK, os seguintes serviços e provedores de dados devem ser atualizados:

### <a name="camera"></a>Câmera

De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Configurações de câmera herdadas](../features/images/xrsdk/CameraSystemLegacy.png)

como

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**e**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![Configurações da câmera do XR SDK](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Entrada

De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Configurações de entrada herddas](../features/images/xrsdk/InputSystemWMRLegacy.png)

como

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR:__

![Configurações de entrada do OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![Configurações de entrada do SDK do XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Limite

De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Configurações de limite herdou](../features/images/xrsdk/BoundarySystemLegacy.png)

como

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Configurações de limite do SDK do XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Reconhecimento espacial

De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Configurações de reconhecimento espacial herddas](../features/images/xrsdk/SpatialAwarenessLegacy.png)

como

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| Em Andamento | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Configurações de reconhecimento espacial do SDK do XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Mapeamentos de controlador

Se estiver usando perfis de mapeamento de controlador personalizado, abra um deles e execute o item de menu Utilitários do Kit de Ferramentas de Realidade Misturada -> -> Atualizar -> Perfis de Mapeamento do Controlador para garantir que os novos tipos de controlador do SDK do XR sejam definidos.

## <a name="see-also"></a>Confira também

* [Começar a trabalhar com o desenvolvimento de RA no Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Começar a trabalhar com o desenvolvimento de VR no Unity](https://docs.unity3d.com/Manual/VROverview.html)
::: moniker-end