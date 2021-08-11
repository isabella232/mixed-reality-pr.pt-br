---
title: Solução de problemas e limitações de comunicação remota do Holographic
description: encontre recursos de solução de problemas e instruções para o recurso de comunicação remota do Holographic em dispositivos HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, comunicação remota holographic, renderização remota, renderização de rede, HoloLens, hologramas remotos, solução de problemas, ajuda, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: fa984e89fb6eb770917d9a1d62ce7c1007d45fab7fbcb2723f9642ac81814054
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223566"
---
# <a name="holographic-remoting-troubleshooting"></a>Solução de problemas de comunicação remota do Holographic

> [!IMPORTANT]
> estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>Bibliotecas atenuadas do Spectre não encontradas.

Os aplicativos de exemplo de comunicação remota Holographic têm/Qspectre (mitigação de Spectre) habilitada na configuração de versão.

se você receber a *vccorlib. lib, o erro fatal não poderá ser aberto* , certifique-se de que sua carga de trabalho de Visual Studio inclui as [bibliotecas atenuadas do Spectre](/cpp/build/reference/qspectre)

## <a name="speech"></a>Fala

O player de comunicação remota Holographic dá suporte a uma sobreposição de diagnóstico, que pode ser habilitada dizendo ```Enable Diagnostics``` e desabilitada dizendo ```Disable Diagnostics``` . Se você tiver problemas com esses comandos de voz, também poderá iniciar o player de comunicação remota do Holographic por meio de um navegador da Web usando ```ms-holographic-remoting:?stats``` como uma URL.

## <a name="h265-video-codec-not-available"></a>Codec de vídeo H265 não disponível

instale o [Extensões de Vídeo HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) ao usar o codec de vídeo H265 em seu aplicativo remoto. Se você encontrar problemas em que o codec está instalado, mas não pode ser usado, consulte o guia de [solução de problemas](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) .

## <a name="limitations"></a>Limitações

atualmente, **não** há suporte para as seguintes APIs ao usar a comunicação remota Holographic para o HoloLens 2 e gerará um ```ERROR_NOT_SUPPORTED``` erro, a menos que indicado de outra forma:

[Windows.Graphics.Holographic](/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - Com suporte a partir da versão [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - Em versões anteriores sempre geram um erro.
* [HolographicCamera.IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - Com suporte a partir da versão [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - As versões anteriores não falham, mas o tamanho do destino de renderização não será alterado.
* [HolographicCameraPose.OverrideProjectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - Com suporte a partir da versão [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Silva.
  - Com suporte a partir da versão [2.1.0](holographic-remoting-version-history.md#v2.1.0)
* [HolographicDisplay.TryGetViewConfiguration](/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - Consultar HolographicViewConfigurationKind. PhotoVideoCamera sempre retornará um ```nullptr``` .
  - Com suporte a partir da versão [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - Em versões anteriores sempre geram um erro.
* [HolographicSpace.CreateFramePresentationMonitor](/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay. GetDefault](/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - Relatará um erro se chamado antes de uma conexão ser estabelecida.


[Windows.Perception.Spatial](/uwp/api/windows.perception.spatial)

* [SpatialLocation. AbsoluteAngularAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. AbsoluteAngularVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. AbsoluteLinearAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. AbsoluteLinearVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference. Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - Com suporte a partir da versão [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - Nas versões anteriores, sempre retornam ```nullptr``` .
* [SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - Com suporte a partir da versão [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [SpatialAnchor.RemovedByUser](/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - Com suporte a partir da versão [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - Nas versões anteriores, sempre retornam ```nullptr``` . 
* [SpatialAnchorExporter.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - Com suporte a partir da versão [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - Em versões anteriores, a operação assíncrona sempre foi concluída com ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [SpatialAnchorTransferManager.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - A operação assíncrona sempre é concluída com ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - A operação assíncrona sempre é concluída com ```false``` .
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - A operação assíncrona sempre é concluída com ```nullptr``` .

[Windows.UI.Input.Spatial](/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource. Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - Com suporte a partir da versão [2.2.0](holographic-remoting-version-history.md#v2.2.0)

[Windows.Perception.Spatial.Preview](/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>Consulte Também
* [Histórico de versões de comunicação remota do Holographic](holographic-remoting-version-history.md)
* [escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs de Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs do OpenXR](holographic-remoting-create-remote-openxr.md)
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Termos de licença de software de comunicação remota holográfica](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)