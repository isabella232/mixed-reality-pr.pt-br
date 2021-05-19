---
title: Ponto de Partida com MRTK e XRSDK
description: Página de aterrissagem do MRTK com XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, XRSDK,
ms.openlocfilehash: ef6d8c9205a9d801e8cb0ec2690d77b74c72b5fb
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143525"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Como começar a trabalhar com o MRTK e o SDK do XR

O SDK do XR é o novo pipeline XR do [Unity no Unity 2019.3 e além de](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). No Unity 2019, ele fornece uma alternativa ao pipeline XR existente. No Unity 2020, ele se tornará o único pipeline XR no Unity.

## <a name="prerequisites"></a>Pré-requisitos

Para começar a trabalhar com o Kit de Ferramentas de Realidade Misturada, siga [as etapas fornecidas](../install-the-tools.md#importing-the-mixed-reality-toolkit) para adicionar o MRTK a um projeto.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Configurando o Unity para o pipeline do SDK do XR

Atualmente, o pipeline do SDK do XR dá suporte a três plataformas: Windows Mixed Reality, Oculus e OpenXR. As seções a seguir abrangem as etapas necessárias para configurar o SDK do XR para cada plataforma.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Acesse o **pacote de Gerenciador de Pacotes** do Unity e instale o pacote do Plug-in do Windows XR, que adiciona suporte para Windows Mixed Reality no SDK do XR. Isso também efetuará pull de alguns pacotes de dependência. 

1. Certifique-se de que todos os seguintes foram instalados com êxito:
   * Gerenciamento de plug-in XR
   * Plug-in do Windows XR
   * Auxiliares de entrada herddos do XR

2. Acesse **Editar > Configurações do Projeto**.
3. Clique na guia Gerenciamento de Plug-in XR na janela Configurações do Projeto.
4. Vá para as Plataforma Universal do Windows configurações e verifique se Windows Mixed Reality está marcada em Provedores de Plug-in.
5. Verifique se Inicializar XR na Inicialização está marcada.
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
1. (**_Opcional_**) Se estiver direcionando o HoloLens 2, certifique-se de que você está na plataforma UWP e selecione Microsoft HoloLens conjunto de recursos

![Gerenciamento de plug-ins Open XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Se você tiver um projeto pré-existente que está usando o MRTK do UPM, certifique-se de que a linha a seguir está no arquivo **link.xml** localizado na pasta MixedRealityToolkit.Generated.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> Para a versão inicial do MRTK e do OpenXR, somente as mãos articuladas do HoloLens 2 e Windows Mixed Reality de movimento têm suporte nativo. O suporte para hardware adicional será adicionado em versões futuras.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Configurando o MRTK para o pipeline do SDK do XR

Se estiver usando o OpenXR, escolha "DefaultOpenXRConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.

Se estiver usando outros runtimes XR na configuração de Gerenciamento de Plug-in XR, como Windows Mixed Reality ou Oculus, escolha "DefaultXRSDKConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.

Esses perfis são definidos com os sistemas e provedores corretos, quando necessário. Consulte [os documentos de perfis](../features/profiles/profiles.md#xr-sdk) para obter mais informações sobre o perfil e o suporte de exemplo com o SDK do XR.

Para migrar um perfil existente para o SDK do XR, os seguintes serviços e provedores de dados devem ser atualizados:

### <a name="camera"></a>Câmera

De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Configurações de câmera herddas](../features/images/xrsdk/CameraSystemLegacy.png)

para

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**e**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![Configurações de câmera do SDK do XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Entrada

De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Configurações de entrada herddas](../features/images/xrsdk/InputSystemWMRLegacy.png)

para

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR:__

![Configurações de entrada do OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![Configurações de entrada do SDK do XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Limite

De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Configurações de limite herdadas](../features/images/xrsdk/BoundarySystemLegacy.png)

para

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Configurações de limite do SDK do XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Conscientização espacial

De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Configurações de conscientização espacial herdadas](../features/images/xrsdk/SpatialAwarenessLegacy.png)

para

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| Em Andamento | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Configurações de reconhecimento espacial do SDK do XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Mapeamentos de controlador

Se você estiver usando perfis de mapeamento de controlador personalizado, abra um deles e execute o item de menu Mixed Reality Toolkit-> Utilities-> Update-> controlador de mapeamento de perfis para garantir que os novos tipos de controlador do SDK do XR sejam definidos.

## <a name="see-also"></a>Confira também

* [Introdução ao desenvolvimento do AR no Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Introdução ao desenvolvimento VR no Unity](https://docs.unity3d.com/Manual/VROverview.html)