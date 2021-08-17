---
title: Histórico de versão de remoção holográfica
description: Mantenha-se atualizado sobre o histórico de versão do recurso de Remoção Holográfica para HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 07/20/2021
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, histórico de versão, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: c474583aacf3872095eaf151f5ab47b617fe0252
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184747"
---
# <a name="holographic-remoting-version-history"></a>Histórico de versão de remoção holográfica

> [!IMPORTANT]
> Essas diretrizes são específicas para a Holographic Remoting no HoloLens 2.

## <a name="version-261-july-20-2021"></a>Versão 2.6.1 (20 de julho de 2021) <a name="v2.6.1"></a>
* A XR_MSFT_holographic_remoting_speech agora permite a inicialização do reconhecedor de fala com novos parâmetros durante uma sessão em execução.
* Corrigido um problema em que a confiabilidade do reconhecimento de fala diminuía em várias conexões.
* Várias correções de bugs e melhorias de estabilidade.

## <a name="version-260-june-10-2021"></a>Versão 2.6.0 (10 de junho de 2021) <a name="v2.6.0"></a>
* O Holographic Remoting usando a API openXR agora dá suporte a:
  * A nova XR_MSFT_holographic_remoting_speech, que permite aos aplicativos escutar comandos de fala personalizados em vários idiomas.
  * A extensão XR_MSFT_scene_understanding, que fornece aos aplicativos uma representação estruturada e de alto nível dos planos, malhas e objetos no ambiente do usuário, permitindo o desenvolvimento de aplicativos com conhecimento espacial. No entanto, com a ressalva XR_SCENE_COMPUTE_CONSISTENCY_OCCLUSION_OPTIMIZED_MSFT é a única consistência com suporte de xrComputeNewSceneMSFT.
  * A extensão XR_MSFT_spatial_graph_bridge, que permite que os aplicativos criem alças XrSpace para acompanhar os nós de Graph espaciais de outras bibliotecas ou APIs de plataforma de Windows Mixed Reality dispositivo. No entanto, com a ressalva XR_SPATIAL_GRAPH_NODE_TYPE_STATIC_MSFT é o único tipo de nó com suporte de xrCreateSpatialGraphNodeSpaceMSFT. 
* O Holographic Remoting usando a API de Realidade Misturada agora dá suporte a:
  * As sobrecargas SpatialGraphInteropPreview.CreateCoordinateSystemForNode, que permitem que os aplicativos acompanhem nós de Graph espaciais estáticos para que os usuários possam pensar sobre locais e coisas em seu ambiente.
* O Holographic Remoting usando as APIs OpenXR e Mixed Reality agora dá suporte a:
  * O SDK Microsoft.MixedReality.SceneUnderstanding, que permite que os aplicativos computem uma descrição da cena em torno do usuário (como paredes, pisos e superfícies), fornecendo quads, malhas e dicas de posicionamento de conteúdo.
  * O SDK Microsoft.MixedReality.QR, que permite que os aplicativos acompanhem o local, o tamanho e o conteúdo dos códigos QR detectados.
* O exemplo remoto do OpenXR foi atualizado para incluir: 
  * Um exemplo de como usar a extensão XR_MSFT_holographic_remoting_speech aplicativo.
* O exemplo remoto de Realidade Misturada foi atualizado para incluir:  
  * Um exemplo de como usar o SDK Microsoft.MixedReality.SceneUnderstanding.
  * Um exemplo de como usar o SDK Microsoft.MixedReality.QR (que substitui o mecanismo de detecção de código QR anterior).
* O player de remoção holográfica agora mostra uma animação de carregamento enquanto a conexão está sendo estabelecida.
* Corrigidos problemas com a compatibilidade do RenderDoc no runtime da API do OpenXR e no exemplo de API de Realidade Misturada.
* Várias correções de bugs e melhorias de estabilidade.

## <a name="version-250-february-12-2021"></a>Versão 2.5.0 (12 de fevereiro de 2021) <a name="v2.5.0"></a>
* O Holographic Remoting usando a [API openXR agora](../native/openxr.md) dá suporte a:
  * XR_MSFT_spatial_anchor extensão. Essa extensão permite que um aplicativo crie âncoras espaciais, que são pontos arbitrários de espaço livre no ambiente físico do usuário que serão rastreados pelo runtime.
  * XR_MSFT_controller_model extensão. Essa extensão fornece um mecanismo para carregar modelos GLTF para controladores.
  * Canais de dados personalizados como parte da extensão XR_MSFT_holographic_remoting dados. Um exemplo para isso é mostrado no exemplo [remoto openXR](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).
* Sincronização aprimorada entre o player e o lado remoto. Isso permite alterar dinamicamente a pose e o buffer de quadro, o que garante que o conteúdo renderizado remoto atinja suavemente as exibições na taxa de quadros de destino esperada.
* Desempenho aprimorado do player de Remoção Holográfica disponível por meio do Microsoft Store. No HoloLens 2, o player agora é executado em 60 quadros por segundo.
* Transmissão otimizada de malhas de superfície espacial que podem ser consultadas por [meio de SpatialSurfaceObserver](/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) por um aplicativo remoto.
* Corrigido um problema em que chamar métodos SpatialAnchorManager ou liberar âncoras causava exceções na desconexão.
* Corrigido o problema de threading que leva a falhas ao fechar instâncias PlayerContext ou RemoteContext.
* Holographic Remoting Player on Desktop: exibe uma mensagem de erro Windows Mixed Reality não está instalado em vez de fechar silenciosamente.
* Muitas outras correções de bug e melhorias de estabilidade.

## <a name="version-241-january-22-2021"></a>Versão 2.4.1 (22 de janeiro de 2021) <a name="v2.4.1"></a>

* Corrigido um problema com SpatialAnchorManager::RequestStoreAsync não funcionando de forma confiável quando chamado durante a conexão.
* Correção do problema com SpatialAnchorManager::TrySave não salvando corretamente uma âncora se a âncora em questão não for localizado.

## <a name="version-240-december-1-2020"></a>Versão 2.4.0 (1º de dezembro de 2020) <a name="v2.4.0"></a>

* O Holographic Remoting agora é suporte à escrita de aplicativos remotos usando a [API openXR](../native/openxr.md). Confira Escrevendo [um aplicativo remoto de remoção holográfica usando APIs OpenXR](holographic-remoting-create-remote-openxr.md) para começar.
* Correções de bugs e melhorias de estabilidade.

## <a name="version-231-october-10-2020"></a>Versão 2.3.1 (10 de outubro de 2020) <a name="v2.3.1"></a>

* Corrigida a regressão com previsão de pose remota, o que causava tremução visual.
* Implementado PerceptionDeviceSetCreateFactoryOverride, o que garante que o PerceptionDevice.dll fornecido com a Holographic Remoting não interfira na versão enviada com Windows 10.

## <a name="version-230-october-2-2020"></a>Versão 2.3.0 (2 de outubro de 2020) <a name="v2.3.0"></a>

* Corrigidas falhas, o que pode acontecer quando o Holographic Remoting Player é suspenso.
* Aprimoramentos de estabilidade.

## <a name="version-223-august-28-2020"></a>Versão 2.2.3 (28 de agosto de 2020) <a name="v2.2.3"></a>

* Correções de bugs e melhorias de estabilidade.

## <a name="version-222-july-10-2020"></a>Versão 2.2.2 (10 de julho de 2020) <a name="v2.2.2"></a>

* Corrigido o problema com [HolographicCamera.LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) e [HolographicCamera.RightViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) não retornando nenhum vértice de malha de área oculta ao transmitir de um headset Windows Mixed Reality.
* Falha corrigida, o que pode acontecer com uma conexão de rede ruim.

## <a name="version-221-july-6-2020"></a>Versão 2.2.1 (6 de julho de 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> [Windows validação do Kit](https://developer.microsoft.com/windows/downloads/app-certification-kit/) de Certificação de Aplicativos com a versão [2.2.0](holographic-remoting-version-history.md#v2.2.0) falhará. Caso você esteja na versão [2.2.0](holographic-remoting-version-history.md#v2.2.0) e queira enviar seu aplicativo para a concessão p da Microsoft Store atualizada para pelo menos a versão 2.2.1.
* Corrigidos [Windows de conformidade do Kit de Certificação de Aplicativos.](https://developer.microsoft.com/windows/downloads/app-certification-kit/)

## <a name="version-220-july-1-2020"></a>Versão 2.2.0 (1º de julho de 2020) <a name="v2.2.0"></a>

* O player de remoção holográfica agora pode ser instalado em PCs que executam Windows Mixed Reality [,](../../discover/navigating-the-windows-mixed-reality-home.md)possibilitando transmitir para headsets imersivos.
* [Os controladores de](../../design/motion-controllers.md) movimento agora são suportados pelo Holographic Remoting e os dados específicos do controlador podem ser recuperados por [meio de SpatialInteractionSource.Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller).
* Agora há suporte para [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) e o estágio atual pode ser recuperado por [meio de SpatialStageFrameOfReference.Current.](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) Além disso, um novo estágio pode ser solicitado por meio [de SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync).
* Nas versões anteriores, a previsão de pose era manipulada no lado do jogador pelo jogador holográfico de remoting. A partir da versão 2.2.0, a Holographic Remoting tem sincronização de tempo e a previsão é totalmente feita pelo aplicativo remoto. Os usuários também devem esperar uma estabilidade aprimorada do holograma em situações de rede difíceis.

## <a name="version-213-may-25-2020"></a>Versão 2.1.3 (25 de maio de 2020) <a name="v2.1.3"></a>

* Comportamento alterado do [evento HolographicSpace.CameraAdded.](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) Nas versões anteriores, não havia garantia de que um [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera) adicionado também tem um [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) válido ao criar o próximo quadro por meio de [HolographicSpace.CreateNextFrame](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe).  A partir da versão 2.1.3, [HolographicSpace.CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) é sincronizado com os dados de pose provenientes do Holographic Remoting Player. Os usuários podem esperar que, quando uma câmera é adicionada, também haja um [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) válido disponível para essa câmera no próximo quadro.
* Adicionado **Desabilitado** a DepthBufferStreamResolution, que pode ser usado para desabilitar o streaming de buffer de profundidade por meio RemoteContext.ConfigureDepthVideoStream. Observe que, se [usado HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) *falhará* com E_ILLEGAL_METHOD_CALL .
* A tela de inicialização do Holographic Remoting Player foi reprojetada e agora não bloqueia a exibição dos usuários.
* Melhorias de estabilidade e correções de bugs.

## <a name="version-212-april-5-2020"></a>Versão 2.1.2 (5 de abril de 2020) <a name="v2.1.2"></a>

* Correção do problema de compatibilidade com versões regressivas de áudio entre o player de remota holográfica mais recente e os aplicativos remotos usando a versão menor que 2.1.0.
* Corrigido o problema de âncora espacial, que fechou inesperadamente o player de remo holográfica. Esse problema também afeta os jogadores personalizados.

## <a name="version-211-march-20-2020"></a>Versão 2.1.1 (20 de março de 2020) <a name="v2.1.1"></a>

* Corrigido o problema de codificação de vídeo com aplicativos remotos ao usar GPUs AMD.
* Melhorias de desempenho do Player de Remoção Holográfica.

## <a name="version-210-march-11-2020"></a>Versão 2.1.0 (11 de março de 2020) <a name="v2.1.0"></a>

* Transporte de rede alternado para [usar RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP. As conexões seguras [usam SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) agora. Observe que o [Holographic Remoting Player](holographic-remoting-player.md) ainda é compatível com todas as versões anteriormente de Holographic Remoting. Para se beneficiar do novo transporte de rede, o Holographic Remoting Player e o aplicativo remoto em questão têm que usar a versão 2.1.0.
* Adicionado suporte [para HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## <a name="version-2020-february-2-2020"></a>Versão 2.0.20 (2 de fevereiro de 2020) <a name="v2.0.20"></a>

* Corrigidos vários bugs que levam a falhas.

## <a name="version-2018-december-17-2019"></a>Versão 2.0.18 (17 de dezembro de 2019) <a name="v2.0.18"></a>

* Adicionado suporte para [HolographicViewConfiguration](/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Corrigidos vários bugs que levam a falhas.
* Correção de bug em que um retorno de chamada HolographicSpace.CameraAdded era necessário para um HolographicCamera ser aceito e aparecer como uma câmera adicionada no HolographicFrame.

## <a name="version-2016-november-11-2019"></a>Versão 2.0.16 (11 de novembro de 2019) <a name="2.0.16"></a>

* Corrigido o deadlock no acompanhamento de código QR.
* Corrigida a exceção com bloqueio devido a uma espera de bloqueio no thread principal.

## <a name="version-2014-october-26-2019"></a>Versão 2.0.14 (26 de outubro de 2019) <a name="v2.0.14"></a>

* Suporte para novas APIs perceptionDevice (Windows 10 de novembro de 2019).
* Corrigido o problema, que impede que eventos de gesto de espera são disparados por SpatialGestureRecognizer.
* Corrigido o problema de threading ao usar SpatialSurfaceObserver.SetBoundingVolume.

## <a name="version-2012-october-18-2019"></a>Versão 2.0.12 (18 de outubro de 2019) <a name="v2.0.12"></a>

* Falha corrigida em SpatialGestureRecognizer ao usar NavigationRail(X/Y/Z).

## <a name="version-2010-october-10-2019"></a>Versão 2.0.10 (10 de outubro de 2019) <a name="v2.0.10"></a>

* Falha corrigida ao usar o botão de gatilho dos controladores de VR. O Holographic Remoting não dá suporte total a controladores, apenas o botão de gatilho e o botão Windows estão funcionando se emparelhados com HoloLens 2.

## <a name="version-209-september-19-2019"></a>Versão 2.0.9 (19 de setembro de 2019) <a name="v2.0.9"></a>

* Adicionado suporte para [SpatialAnchorExporter](/uwp/api/windows.perception.spatial.spatialanchorexporter)
* Adicionada nova interface ```IPlayerContext2``` (implementada ```PlayerContext``` por ) fornecendo os seguintes membros:
  - [Propriedade BlitRemoteFrameTimeout.](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)
* Valor ```Failed_RemoteFrameTooOld``` adicionado a ```BlitResult```
* Melhorias de estabilidade e confiabilidade

## <a name="version-208-august-20-2019"></a>Versão 2.0.8 (20 de agosto de 2019) <a name="v2.0.8"></a>

* Falha corrigida ao chamar [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) com [um IDXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) como parâmetro.
* Melhorias de estabilidade e confiabilidade

## <a name="version-207-july-26-2019"></a>Versão 2.0.7 (26 de julho de 2019) <a name="v2.0.7"></a>

* Primeira versão pública da Holographic Remoting para HoloLens 2.

## <a name="see-also"></a>Consulte Também
* [Visão geral de remoção holográfica](holographic-remoting-overview.md)
* [Escrevendo um aplicativo remoto de remoção holográfica usando APIs Windows Mixed Reality holográficas](holographic-remoting-create-remote-wmr.md)
* [Escrevendo um aplicativo remoto de remoção holográfica usando APIs OpenXR](holographic-remoting-create-remote-openxr.md)
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Solução de problemas e limitações de remoção holográfica](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)