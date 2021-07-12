---
title: Introdução ao SDK do MRTK e do XR
description: Página de aterrissagem do MRTK com o XR SDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, XRSDK, XR SDK
ms.openlocfilehash: bc2924f8e080b0c202f7c3e394a5382cf306431c
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603687"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Introdução ao SDK do MRTK e do XR

O XR SDK é o [novo pipeline XR do Unity no Unity 2019,3 e posterior](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). No Unity 2019, ele fornece uma alternativa ao pipeline XR existente. No Unity 2020, é o único pipeline XR no Unity.

## <a name="prerequisites"></a>Pré-requisitos

para começar com a realidade misturada Toolkit, siga [as etapas fornecidas](../install-the-tools.md#importing-the-mixed-reality-toolkit) para adicionar o MRTK a um projeto.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Configurando o Unity para o pipeline do SDK do XR

o pipeline do XR SDK atualmente dá suporte a três plataformas: Windows Mixed Reality, Oculus e OpenXR. As seções a seguir abordarão as etapas necessárias para configurar o XR SDK para cada plataforma.

### <a name="windows-mixed-reality"></a>Realidade Misturada do Windows

acesse o **Gerenciador de Pacotes do Unity** e instale o pacote de plug-in Windows xr, que adiciona suporte para Windows Mixed Reality no XR SDK. Isso também obterá alguns pacotes de dependência.

1. Verifique se todos os itens a seguir foram instalados com êxito:
   * Gerenciamento de plugin XR
   * Windows Plug-in XR
   * Auxiliares de entrada do XR Legacy

2. Acesse **Editar > Configurações do Projeto**.
3. clique na guia gerenciamento de Plug-ins do XR na janela Project Configurações.
4. vá para as configurações de Plataforma Universal do Windows e verifique se Windows Mixed Reality está marcado em provedores de Plug-in.
5. Verifique se inicializar XR na inicialização está marcado.
6. (**_necessário para comunicação remota HoloLens no editor, caso contrário, opcional_**) vá para as configurações autônomas e verifique se Windows Mixed Reality está marcado em provedores de Plug-in. Verifique também se inicializar XR na inicialização está marcado.

    ![Gerenciamento de plugin XR com guia autônoma selecionada](images/xr-management-img-02.png)

7. (**_Opcional_**) clique na guia Windows Mixed Reality em gerenciamento de Plug-in de XR e crie um perfil de configurações personalizadas para alterar os padrões. Se a lista de configurações já estiver lá, nenhum perfil precisará ser criado.

    ![gerenciamento de Plugin XR com guia Windows selecionada](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. Siga a guia [como configurar o Oculus Quest no MRTK usando o pipeline do XR SDK](../supported-devices/oculus-quest-mrtk.md) para o final. O guia descreve as etapas necessárias para configurar o Unity e o MRTK para usar o pipeline do SDK do XR para o Oculus Quest.

### <a name="openxr"></a>OpenXR

> [!IMPORTANT]
> O OpenXR no Unity só tem suporte no Unity 2020,2 e superior.
> Ele também dá suporte apenas a compilações de x64, ARM e ARM64.

1. Siga o guia [usando o plug-in Mixed Reality OpenXR plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) , incluindo as etapas para configurar a otimização e o gerenciamento de plug-in do XR para instalar o plug-in do OpenXR em seu projeto. Verifique se os itens a seguir foram instalados com êxito:
   1. Gerenciamento de plugin XR
   1. Plug-in OpenXR
   1. Plug-in OpenXR de realidade misturada
1. vá para editar > Project Configurações.
1. clique na guia gerenciamento de Plug-ins do XR na janela Project Configurações.
1. Verifique se inicializar XR na inicialização está marcado.
1. (**_Opcional_**) se estiver direcionando HoloLens 2, verifique se você está na plataforma UWP e selecione Microsoft HoloLens conjunto de recursos

![OpenXR de gerenciamento de plugin](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Se você tiver um projeto pré-existente que esteja usando MRTK do UPM, verifique se a linha a seguir está no arquivo **link.xml** localizado na pasta MixedRealityToolkit. Generated.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> para a versão inicial do MRTK e do OpenXR, somente os HoloLens 2 hands e os controladores de movimento de Windows Mixed Reality são suportados nativamente. O suporte para hardware adicional será adicionado em versões futuras.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Configurando o MRTK para o pipeline do SDK do XR

::: moniker range=">= mrtkunity-2021-05"
Use qualquer um dos perfis de MRTK padrão, que são todos configurados nos pipelines XR do Unity. Os "DefaultOpenXRConfigurationProfile" e "DefaultXRSDKConfigurationProfile" anteriores agora estão rotulados como obsoletos.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Se estiver usando OpenXR, escolha "DefaultOpenXRConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.

se estiver usando outros tempos de execução do xr na configuração de gerenciamento de Plug-in do xr, como Windows Mixed Reality ou Oculus, escolha "DefaultXRSDKConfigurationProfile" como o perfil ativo ou clone-o para fazer personalizações.

Esses perfis são configurados com os sistemas e provedores corretos, quando necessário. Consulte [os documentos de perfis](../features/profiles/profiles.md#xr-sdk) para obter mais informações sobre o suporte a perfis e amostras com o XR SDK.
::: moniker-end

Para migrar um perfil existente para o XR SDK, os serviços e provedores de dados a seguir devem ser atualizados.
::: moniker range=">= mrtkunity-2021-05"
Você poderá ver os novos provedores de dados na guia do SDK do XR no Unity 2019 ou na exibição principal/somente no Unity 2020 +, em que o XR herdado não existe.

![A guia do SDK do XR](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a>Câmera

::: moniker range=">= mrtkunity-2021-05"
Adicionar os seguintes provedores de dados
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Configurações de câmera herdadas](../features/images/xrsdk/CameraSystemLegacy.png)

como
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![Configurações da câmera do XR SDK](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Entrada

::: moniker range=">= mrtkunity-2021-05"
Adicionar os seguintes provedores de dados
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Configurações de entrada herdadas](../features/images/xrsdk/InputSystemWMRLegacy.png)

como
::: moniker-end

| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR__:

![Configurações de entrada do OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![Configurações de entrada do SDK do XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Limite

::: moniker range=">= mrtkunity-2021-05"
Adicionar os seguintes provedores de dados
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Configurações de limite herdadas](../features/images/xrsdk/BoundarySystemLegacy.png)

como
::: moniker-end

| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Configurações de limite do SDK do XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Conscientização espacial

::: moniker range=">= mrtkunity-2021-05"
Adicionar os seguintes provedores de dados
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Configurações de conscientização espacial herdadas](../features/images/xrsdk/SpatialAwarenessLegacy.png)

como
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (para UWP) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (para UWP) |
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (para não UWP) | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![Configurações de reconhecimento espacial do SDK do XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Mapeamentos de controlador

Se estiver usando perfis de mapeamento de controlador personalizado, abra um deles e execute o item de menu Utilitários de Toolkit -> -> Update -> Controller Mapping Profiles para garantir que os novos tipos de controlador do SDK do XR sejam definidos.

## <a name="see-also"></a>Confira também

* [Começar a trabalhar com o desenvolvimento de RA no Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Começar a trabalhar com o desenvolvimento de VR no Unity](https://docs.unity3d.com/Manual/VROverview.html)
