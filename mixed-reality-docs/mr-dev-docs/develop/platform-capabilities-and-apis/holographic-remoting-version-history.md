---
title: Histórico de versões de comunicação remota do Holographic
description: mantenha-se atualizado sobre o histórico de versões do recurso de comunicação remota do Holographic para o HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 07/20/2021
ms.topic: article
keywords: HoloLens, comunicação remota, Holographic de comunicação remota, histórico de versão, headset de realidade misturada, headset de realidade mista do windows, headset da realidade virtual
ms.openlocfilehash: 21ba89e477872f5dfa41468f1a7f2d7507affd681556d79843c195d7d5839e7b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223546"
---
# <a name="holographic-remoting-version-history"></a>Histórico de versões de comunicação remota do Holographic

> [!IMPORTANT]
> estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.

## <a name="version-261-july-20-2021"></a>Versão 2.6.1 (20 de julho de 2021) <a name="v2.6.1"></a>
* A extensão XR_MSFT_holographic_remoting_speech agora permite a reinicialização do reconhecedor de fala com novos parâmetros durante uma sessão em execução.
* Corrigido um problema em que a confiabilidade do reconhecimento de fala diminuiu em várias conexões.
* Várias correções de bugs e aprimoramentos de estabilidade.

## <a name="version-260-june-10-2021"></a>Versão 2.6.0 (10 de junho de 2021) <a name="v2.6.0"></a>
* A Holographic remota usando a API OpenXR agora dá suporte a:
  * A nova extensão de XR_MSFT_holographic_remoting_speech, que permite que os aplicativos escutem os comandos de fala personalizados em vários idiomas.
  * A extensão XR_MSFT_scene_understanding, que fornece aos aplicativos uma representação estruturada e de alto nível dos planos, das malhas e dos objetos no ambiente do usuário, permitindo o desenvolvimento de aplicativos com reconhecimento espacial. No entanto, com a limitação de que XR_SCENE_COMPUTE_CONSISTENCY_OCCLUSION_OPTIMIZED_MSFT é a única consistência com suporte do xrComputeNewSceneMSFT.
  * a extensão XR_MSFT_spatial_graph_bridge, que permite que os aplicativos criem identificadores XrSpace para rastrear os nós espaciais Graph de outras bibliotecas de plataforma de dispositivo Windows Mixed Reality ou APIs. No entanto, com a limitação de que XR_SPATIAL_GRAPH_NODE_TYPE_STATIC_MSFT é o único tipo de nó com suporte do xrCreateSpatialGraphNodeSpaceMSFT. 
* A comunicação remota Holographic usando a API de realidade misturada agora dá suporte a:
  * as sobrecargas SpatialGraphInteropPreview. CreateCoordinateSystemForNode, que permitem que os aplicativos acompanhem nós Graph espaciais estáticos para que os usuários possam ter um motivo sobre locais e coisas em seu ambiente.
* A comunicação remota Holographic usando as APIs OpenXR e de realidade misturada agora dá suporte a:
  * O SDK do Microsoft. MixedReality. SceneUnderstanding, que permite que os aplicativos computam uma descrição da cena em torno do usuário (como paredes, andares e superfícies), fornecendo quádruplas, malhas e indicações de posicionamento de conteúdo.
  * O SDK Microsoft. MixedReality. QR, que permite que os aplicativos acompanhem o local, o tamanho e o conteúdo dos códigos QR detectados.
* O exemplo remoto OpenXR foi atualizado para incluir: 
  * Um exemplo de como usar a extensão XR_MSFT_holographic_remoting_speech.
* A amostra remota de realidade misturada foi atualizada para incluir:  
  * Um exemplo de como usar o SDK Microsoft. MixedReality. SceneUnderstanding.
  * Um exemplo de como usar o SDK Microsoft. MixedReality. QR (que substitui o mecanismo de detecção de código QR anterior).
* O player de comunicação remota do Holographic agora mostra uma animação de carregamento enquanto a conexão está sendo estabelecida.
* Correção de problemas com a compatibilidade de RenderDoc no tempo de execução de API OpenXR e no exemplo de API de realidade misturada.
* Várias correções de bugs e aprimoramentos de estabilidade.

## <a name="version-250-february-12-2021"></a>Versão 2.5.0 (12 de fevereiro de 2021) <a name="v2.5.0"></a>
* A Holographic remota usando a [API OpenXR](../native/openxr.md) agora dá suporte a:
  * Extensão de XR_MSFT_spatial_anchor. Essa extensão permite que um aplicativo crie âncoras espaciais, que são pontos de espaço livre arbitrários no ambiente físico do usuário que serão rastreados pelo tempo de execução.
  * Extensão de XR_MSFT_controller_model. Essa extensão fornece um mecanismo para carregar modelos GLTF para controladores.
  * Canais de dados personalizados como parte da extensão de XR_MSFT_holographic_remoting. Um exemplo para isso é mostrado no [exemplo remoto OpenXR](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).
* Sincronização aprimorada entre o Player e o lado remoto. Isso permite alterar dinamicamente a pose e o buffer de quadros, o que garante que o conteúdo renderizado remotamente alcance os monitores na taxa de quadros de destino esperada.
* Desempenho aprimorado do Holographic Remoting Player disponível por meio do Microsoft Store. no HoloLens 2, o jogador agora é executado em 60 quadros por segundo.
* Transmissão otimizada de malhas de superfície espacial que podem ser consultadas por meio de [SpatialSurfaceObserver](/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) por um aplicativo remoto.
* Corrigido um problema no qual a chamada de métodos SpatialAnchorManager ou a liberação de âncoras causaram exceções na desconexão.
* Correção do problema de Threading que leva a falhas ao fechar instâncias de PlayerContext ou RemoteContext.
* Player de comunicação remota do Holographic na área de trabalho: exibe uma mensagem de erro quando Windows Mixed Reality não é instalado em vez de fechar silenciosamente.
* Muitas outras correções de bugs e aprimoramentos de estabilidade.

## <a name="version-241-january-22-2021"></a>Versão 2.4.1 (22 de janeiro de 2021) <a name="v2.4.1"></a>

* Problema corrigido com SpatialAnchorManager:: RequestStoreAsync não funciona de maneira confiável quando chamado durante a conexão.
* Correção do problema com SpatialAnchorManager:: TrySave não salvar corretamente uma âncora se a âncora em questão não for localizável.

## <a name="version-240-december-1-2020"></a>Versão 2.4.0 (1º de dezembro de 2020) <a name="v2.4.0"></a>

* A comunicação remota do Holographic agora dá suporte à gravação de aplicativos remotos usando a [API do OpenXR](../native/openxr.md). Confira [escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs do OpenXR](holographic-remoting-create-remote-openxr.md) para começar.
* Correções de bugs e melhorias de estabilidade.

## <a name="version-231-october-10-2020"></a>Versão 2.3.1 (10 de outubro de 2020) <a name="v2.3.1"></a>

* Regressão fixa com previsão de pose remota, que causou a tremulação Visual.
* Implementado o PerceptionDeviceSetCreateFactoryOverride, que garante que o PerceptionDevice.dll fornecido com o Holographic Remoting não interfira na versão fornecida com Windows 10.

## <a name="version-230-october-2-2020"></a>Versão 2.3.0 (2 de outubro de 2020) <a name="v2.3.0"></a>

* Correção de falhas, o que pode acontecer quando o Holographic Remoting Player é suspenso.
* Aprimoramentos de estabilidade.

## <a name="version-223-august-28-2020"></a>Versão 2.2.3 (28 de agosto de 2020) <a name="v2.2.3"></a>

* Correções de bugs e melhorias de estabilidade.

## <a name="version-222-july-10-2020"></a>Versão 2.2.2 (10 de julho de 2020) <a name="v2.2.2"></a>

* corrigido o problema com [HolographicCamera. LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) e [HolographicCamera. RightViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) não retornando nenhum vértice de malha da área oculta ao transmitir de um Windows Mixed Reality headset.
* Correção de falha, o que pode acontecer com uma conexão de rede ruim.

## <a name="version-221-july-6-2020"></a>Versão 2.2.1 (6 de julho de 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> [Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) validação do Kit de certificação de aplicativo com a versão [2.2.0](holographic-remoting-version-history.md#v2.2.0) falhará. Caso você esteja na versão [2.2.0](holographic-remoting-version-history.md#v2.2.0) e queira enviar seu aplicativo para a concessão p da Microsoft Store atualizada para pelo menos a versão 2.2.1.
* correção de problemas de conformidade do [Kit de certificação de aplicativo Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) .

## <a name="version-220-july-1-2020"></a>Versão 2.2.0 (1º de julho de 2020) <a name="v2.2.0"></a>

* o player de comunicação remota do Holographic agora pode ser instalado em computadores que executam [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md), tornando possível transmitir para headsets de imersão.
* Os [controladores de movimento](../../design/motion-controllers.md) agora têm suporte da comunicação remota Holographic e os dados específicos do controlador podem ser recuperados por meio de [SpatialInteractionSource. Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller).
* Agora há suporte para [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) e o estágio atual pode ser recuperado por meio de [SpatialStageFrameOfReference. Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current). Além disso, um novo estágio pode ser solicitado por meio de [SpatialStageFrameOfReference. RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync).
* Em versões anteriores, a previsão de pose foi tratada no lado do jogador pelo Player de comunicação remota do Holographic. A partir da versão 2.2.0, a comunicação remota do Holographic tem sincronização de tempo e a previsão é totalmente feita pelo aplicativo remoto. Os usuários também devem esperar uma melhoria na estabilidade do holograma em situações de rede difíceis.

## <a name="version-213-may-25-2020"></a>Versão 2.1.3 (25 de maio de 2020) <a name="v2.1.3"></a>

* Comportamento alterado do evento [HolographicSpace. CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) . Em versões anteriores, **não** era garantido que um [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera) adicional também tenha um [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) válido ao criar o próximo quadro via [HolographicSpace. CreateNextFrame](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe). A partir da versão 2.1.3, o [HolographicSpace. CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) é sincronizado com dados de pose provenientes do player de comunicação remota do Holographic. Os usuários podem esperar que, quando uma câmera é adicionada, também haja uma [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) válida disponível para essa câmera no próximo quadro.
* Adicionado **desabilitado** a DepthBufferStreamResolution, que pode ser usado para desabilitar o streaming de buffer de profundidade por meio de RemoteContext.ConfigureDepthVideoStream. Observe que, se for usado, [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) falhará com *E_ILLEGAL_METHOD_CALL*.
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
* Adicionado suporte para [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## <a name="version-2020-february-2-2020"></a>Versão 2.0.20 (2 de fevereiro de 2020) <a name="v2.0.20"></a>

* Correção de vários bugs que levam a falhas.

## <a name="version-2018-december-17-2019"></a>Versão 2.0.18 (17 de dezembro de 2019) <a name="v2.0.18"></a>

* Adicionado suporte para [HolographicViewConfiguration](/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Correção de vários bugs que levam a falhas.
* Corrigido o bug em que um retorno de chamada HolographicSpace. CameraAdded era necessário para um HolographicCamera ser aceito e exibido como uma câmera adicionada no HolographicFrame.

## <a name="version-2016-november-11-2019"></a>Versão 2.0.16 (11 de novembro de 2019) <a name="2.0.16"></a>

* Correção de deadlock no controle de código QR.
* Correção da exceção unhandeled devido a uma espera de bloqueio no thread principal.

## <a name="version-2014-october-26-2019"></a>Versão 2.0.14 (26 de outubro de 2019) <a name="v2.0.14"></a>

* suporte para novas APIs PerceptionDevice (Windows 10 atualização de novembro de 2019).
* Correção do problema, que impede que eventos de gesto de suspensão sejam disparados por SpatialGestureRecognizer.
* Corrigido o problema de Threading ao usar SpatialSurfaceObserver. SetBoundingVolume.

## <a name="version-2012-october-18-2019"></a>Versão 2.0.12 (18 de outubro de 2019) <a name="v2.0.12"></a>

* Correção de falha em SpatialGestureRecognizer ao usar NavigationRail (X/Y/Z).

## <a name="version-2010-october-10-2019"></a>Versão 2.0.10 (10 de outubro de 2019) <a name="v2.0.10"></a>

* Correção de falha ao usar o botão de gatilho de controladores VR. a comunicação remota do Holographic não dá suporte total a controladores, somente o botão de gatilho e o botão de Windows estão funcionando se emparelhados com HoloLens 2.

## <a name="version-209-september-19-2019"></a>Versão 2.0.9 (19 de setembro de 2019) <a name="v2.0.9"></a>

* Adicionado suporte para [SpatialAnchorExporter](/uwp/api/windows.perception.spatial.spatialanchorexporter)
* Adicionada nova interface ```IPlayerContext2``` (implementada por ```PlayerContext``` ) fornecendo os seguintes membros:
  - Propriedade [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .
* ```Failed_RemoteFrameTooOld```Valor adicionado a```BlitResult```
* Aprimoramentos de estabilidade e confiabilidade

## <a name="version-208-august-20-2019"></a>Versão 2.0.8 (20 de agosto de 2019) <a name="v2.0.8"></a>

* Correção de falha ao chamar [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) com um [IDXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) como parâmetro.
* Aprimoramentos de estabilidade e confiabilidade

## <a name="version-207-july-26-2019"></a>Versão 2.0.7 (26 de julho de 2019) <a name="v2.0.7"></a>

* primeira versão pública da comunicação remota do Holographic para o HoloLens 2.

## <a name="see-also"></a>Consulte Também

* [escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs de Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs do OpenXR](holographic-remoting-create-remote-openxr.md)
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)