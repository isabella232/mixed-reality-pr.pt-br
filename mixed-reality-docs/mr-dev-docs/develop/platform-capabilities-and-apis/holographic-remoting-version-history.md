---
title: Histórico de versões de comunicação remota do Holographic
description: Mantenha-se atualizado sobre o histórico de versões do recurso de comunicação remota do Holographic para o HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicação remota, Holographic de comunicação remota, histórico de versões, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 84caf761af15645410c7439660747fa2f369c6c7
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009516"
---
# <a name="holographic-remoting-version-history"></a>Histórico de versões de comunicação remota do Holographic

> [!IMPORTANT]
> Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.

## <a name="version-240-december-1-2020"></a>Versão 2.4.0 (1º de dezembro de 2020) <a name="v2.4.0"></a>

* A comunicação remota do Holographic agora dá suporte à gravação de aplicativos remotos usando a [API do OpenXR](../native/openxr.md). Confira [escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs do OpenXR](holographic-remoting-create-remote-openxr.md) para começar.
* Correções de bugs e melhorias de estabilidade.

## <a name="version-231-october-10-2020"></a>Versão 2.3.1 (10 de outubro de 2020) <a name="v2.3.1"></a>

* Regressão fixa com previsão de pose remota, que causou a tremulação Visual.
* Implementado o PerceptionDeviceSetCreateFactoryOverride, que garante que o PerceptionDevice.dll fornecido com o Holographic Remoting não interfira na versão fornecida com o Windows 10.

## <a name="version-230-october-2-2020"></a>Versão 2.3.0 (2 de outubro de 2020) <a name="v2.3.0"></a>

* Correção de falhas, o que pode acontecer quando o Holographic Remoting Player é suspenso.
* Aprimoramentos de estabilidade.

## <a name="version-223-august-28-2020"></a>Versão 2.2.3 (28 de agosto de 2020) <a name="v2.2.3"></a>

* Correções de bugs e melhorias de estabilidade.

## <a name="version-222-july-10-2020"></a>Versão 2.2.2 (10 de julho de 2020) <a name="v2.2.2"></a>

* Corrigido o problema com [HolographicCamera. LeftViewportParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) e [HolographicCamera. RightViewportParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) não retornando nenhum vértice de malha da área oculta ao transmitir de um headset de realidade mista do Windows.
* Correção de falha, o que pode acontecer com uma conexão de rede ruim.

## <a name="version-221-july-6-2020"></a>Versão 2.2.1 (6 de julho de 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> A validação do [Kit de certificação de aplicativos para Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) com a versão [2.2.0](holographic-remoting-version-history.md#v2.2.0) falhará. Caso você esteja na versão [2.2.0](holographic-remoting-version-history.md#v2.2.0) e queira enviar seu aplicativo para a concessão p da Microsoft Store atualizada para pelo menos a versão 2.2.1.
* Correção dos problemas de conformidade do [Kit de certificação de aplicativos do Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) .

## <a name="version-220-july-1-2020"></a>Versão 2.2.0 (1º de julho de 2020) <a name="v2.2.0"></a>

* O Holographic Remoting Player agora pode ser instalado em computadores que executam a [realidade mista do Windows](../../discover/navigating-the-windows-mixed-reality-home.md), tornando possível transmitir para headsets de imersão.
* Os [controladores de movimento](../../design/motion-controllers.md) agora têm suporte da comunicação remota Holographic e os dados específicos do controlador podem ser recuperados por meio de [SpatialInteractionSource. Controller](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller).
* Agora há suporte para [SpatialStageFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference) e o estágio atual pode ser recuperado por meio de [SpatialStageFrameOfReference. Current](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current). Além disso, um novo estágio pode ser solicitado por meio de [SpatialStageFrameOfReference. RequestNewStageAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync).
* Em versões anteriores, a previsão de pose foi tratada no lado do jogador pelo Player de comunicação remota do Holographic. A partir da versão 2.2.0, a comunicação remota do Holographic tem sincronização de tempo e a previsão é totalmente feita pelo aplicativo remoto. Os usuários também devem esperar uma melhoria na estabilidade do holograma em situações de rede difíceis.

## <a name="version-213-may-25-2020"></a>Versão 2.1.3 (25 de maio de 2020) <a name="v2.1.3"></a>

* Comportamento alterado do evento [HolographicSpace. CameraAdded](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) . Em versões anteriores, **não** era garantido que um [HolographicCamera](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera) adicional também tenha um [HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose) válido ao criar o próximo quadro via [HolographicSpace. CreateNextFrame](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createnextframe). A partir da versão 2.1.3, o [HolographicSpace. CameraAdded](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) é sincronizado com dados de pose provenientes do player de comunicação remota do Holographic. Os usuários podem esperar que, quando uma câmera é adicionada, também haja uma [HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose) válida disponível para essa câmera no próximo quadro.
* Adicionado **desabilitado** a DepthBufferStreamResolution, que pode ser usado para desabilitar o streaming de buffer de profundidade por meio de RemoteContext.ConfigureDepthVideoStream. Observe que, se for usado, [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) falhará com *E_ILLEGAL_METHOD_CALL*.
* A tela de inicialização do Holographic Remoting Player foi reformulada e agora não bloqueia a exibição dos usuários.
* Melhorias de estabilidade e correções de bugs.

## <a name="version-212-april-5-2020"></a>Versão 2.1.2 (5 de abril de 2020) <a name="v2.1.2"></a>

* Correção do problema de compatibilidade com versões anteriores de áudio entre o player de comunicação remota Holographic mais recente e os aplicativos remotos usando a versão menor que 2.1.0.
* Problema fixo de âncora espacial, que fechou inesperadamente o player de comunicação remota do Holographic. Esse problema também afeta os players personalizados.

## <a name="version-211-march-20-2020"></a>Versão 2.1.1 (20 de março de 2020) <a name="v2.1.1"></a>

* Correção do problema de codificação de vídeo com aplicativos remotos ao usar GPUs AMD.
* Melhorias de desempenho do Holographic Remoting Player.

## <a name="version-210-march-11-2020"></a>Versão 2.1.0 (11 de março de 2020) <a name="v2.1.0"></a>

* Transporte de rede alternado para usar [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP. As conexões seguras usam o [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) agora. Observe que o [player de comunicação remota do Holographic](holographic-remoting-player.md) ainda é compatível com todas as versões de comunicação remota do Holographic de versão anterior. Para se beneficiar do novo transporte de rede, o Holographic Remoting Player e o aplicativo remoto em questão precisam usar a versão 2.1.0.
* Adicionado suporte para [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## <a name="version-2020-february-2-2020"></a>Versão 2.0.20 (2 de fevereiro de 2020) <a name="v2.0.20"></a>

* Correção de vários bugs que levam a falhas.

## <a name="version-2018-december-17-2019"></a>Versão 2.0.18 (17 de dezembro de 2019) <a name="v2.0.18"></a>

* Adicionado suporte para [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Correção de vários bugs que levam a falhas.
* Corrigido o bug em que um retorno de chamada HolographicSpace. CameraAdded era necessário para um HolographicCamera ser aceito e exibido como uma câmera adicionada no HolographicFrame.

## <a name="version-2016-november-11-2019"></a>Versão 2.0.16 (11 de novembro de 2019) <a name="2.0.16"></a>

* Correção de deadlock no controle de código QR.
* Correção da exceção unhandeled devido a uma espera de bloqueio no thread principal.

## <a name="version-2014-october-26-2019"></a>Versão 2.0.14 (26 de outubro de 2019) <a name="v2.0.14"></a>

* Suporte para novas APIs PerceptionDevice (atualização de novembro de 2019 do Windows 10).
* Correção do problema, que impede que eventos de gesto de suspensão sejam disparados por SpatialGestureRecognizer.
* Corrigido o problema de Threading ao usar SpatialSurfaceObserver. SetBoundingVolume.

## <a name="version-2012-october-18-2019"></a>Versão 2.0.12 (18 de outubro de 2019) <a name="v2.0.12"></a>

* Correção de falha em SpatialGestureRecognizer ao usar NavigationRail (X/Y/Z).

## <a name="version-2010-october-10-2019"></a>Versão 2.0.10 (10 de outubro de 2019) <a name="v2.0.10"></a>

* Correção de falha ao usar o botão de gatilho de controladores VR. A comunicação remota do Holographic não dá suporte total a controladores, apenas o botão de gatilho e o botão do Windows estão funcionando se emparelhados com o HoloLens 2.

## <a name="version-209-september-19-2019"></a>Versão 2.0.9 (19 de setembro de 2019) <a name="v2.0.9"></a>

* Adicionado suporte para [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)
* Adicionada nova interface ```IPlayerContext2``` (implementada por ```PlayerContext``` ) fornecendo os seguintes membros:
  - Propriedade [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .
* ```Failed_RemoteFrameTooOld```Valor adicionado a```BlitResult```
* Aprimoramentos de estabilidade e confiabilidade

## <a name="version-208-august-20-2019"></a>Versão 2.0.8 (20 de agosto de 2019) <a name="v2.0.8"></a>

* Correção de falha ao chamar [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) com um [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) como parâmetro.
* Aprimoramentos de estabilidade e confiabilidade

## <a name="version-207-july-26-2019"></a>Versão 2.0.7 (26 de julho de 2019) <a name="v2.0.7"></a>

* Primeira versão pública da comunicação remota do Holographic para o HoloLens 2.

## <a name="see-also"></a>Consulte Também

* [Escrevendo um aplicativo remoto de comunicação remota do Holographic usando as APIs de realidade mista do Windows](holographic-remoting-create-remote-wmr.md)
* [Escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs do OpenXR](holographic-remoting-create-remote-openxr.md)
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
