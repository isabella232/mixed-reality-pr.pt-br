---
title: Recursos com suporte do plug-in OpenXR no Unity
description: Descubra os recursos que o OpenXR dá suporte para desenvolvimento de realidade misturada no Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realidade misturada, MRTK, Kit de Ferramentas de Realidade Misturada, realidade aumentada, realidade virtual, headsets de realidade misturada, learn, tutorial, introdução
ms.openlocfilehash: e622cd617ccf67c0877b9064efe791743e4c34b6
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333368"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Recursos com suporte do OpenXR de Realidade Misturada no Unity

O pacote de plug-in **OpenXR** de Realidade Misturada é uma extensão do **Plug-in OpenXR** do Unity e dá suporte a um conjunto de recursos para holoLens 2 e Windows Mixed Reality headsets. Antes de continuar, certifique-se de que seu projeto do Unity [está configurado para OpenXR.](openxr-getting-started.md)

## <a name="whats-supported"></a>O que tem suporte

No momento, há suporte para os seguintes recursos:

* Dá suporte a aplicativos UWP para HoloLens 2 e otimização para o modelo de aplicativo holoLens 2.
* Dá suporte a aplicativos Win32 VR para Windows Mixed Reality headset com perfis de controlador mais recentes e comunicação remoto de aplicativo holográfico.
* Acompanhamento de escala mundial usando âncoras e espaço não ressalvado.
* [Api de armazenamento de âncora para persistir âncoras](spatial-anchors-in-unity.md) no armazenamento local do HoloLens 2.
* [O controlador de movimento e as interações com a mão](#motion-controller-and-hand-interactions), incluindo o novo controlador HP Reverb G2.
* Acompanhamento de mão articulado usando 26 junções e entradas de raio conjunta.
* Interação com o olhar no HoloLens 2.
* Localizando a câmera de foto/vídeo (PV) no HoloLens 2.
* Captura de Realidade Misturada a renderização de 3º olho por meio da câmera PV.
* Dá [suporte a "Reproduzir" no HoloLens 2](unity-play-mode.md#holographic-remoting-in-unity-editor-play-mode)com o aplicativo holográfico remoting, permitindo que os desenvolvedores depurem scripts sem criar e implantar no dispositivo.
* Compatível com o MRTK Unity 2.5.3 e mais novo por meio do [MRTK OpenXR,](openxr-getting-started.md#using-mrtk-with-openxr-support)o provedor é compatível com .
* Compatível com o [Unity ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) ou posterior.
* (Adicionado em 0.1.3) Dá suporte ao aplicativo de área de trabalho [Holographic Remoting](holographic-remoting-desktop.md) de um aplicativo autônomo do Windows criado e implantado.
* (Adicionado em 0.1.4) Dá suporte ao [controle de código QR](#qr-codes) no HoloLens2 por meio de SpatialGraphNode
* (Adicionado em 0.2.0) Dá suporte à **âncora** na comunicação remota do Holographic
* (Adicionado em 0.2.0) Dá suporte a **junções de mão e acompanhamento de malha à mão**
* (Adicionado em 0.2.0) Dá suporte a **ARPlaneSubsystems** para detecção de plano e posicionar o holograma usando **ARRaycastManager**.
* (0.9.0) dá suporte a **XRMeshSubsystem** e **ARMeshManager** para mapeamento espacial.
* (Adicionado em 0.9.0) Dá suporte ao SDK de âncoras espaciais do Azure para o plug-in do Windows. Para obter mais informações, consulte o [projeto de exemplo das âncoras espaciais do Azure de realidade mista + OpenXR no GitHub](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample).
* (Adicionado em 0.9.1) Dá suporte à comunicação remota do aplicativo de desktop Holographic de um aplicativo UWP do Windows criado e implantado.
* (Adicionado em 0.9.4) Dá suporte à plataforma ARM, além do ARM64 para o aplicativo HoloLens 2.

## <a name="motion-controller-and-hand-interactions"></a>Controlador de movimento e interações de mão

Para aprender as noções básicas sobre interações de realidade misturada no Unity, visite o [manual do Unity para entrada do Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html). Esta documentação do Unity aborda os mapeamentos de entradas específicas do controlador para **InputFeatureUsage** s mais generalizadas, como as entradas de XR disponíveis podem ser identificadas e categorizadas, como ler dados dessas entradas e muito mais.

O plug-in Mixed Reality OpenXR fornece perfis de interação de entrada adicionais, mapeados para os **InputFeatureUsage** padrão, conforme detalhado abaixo:

| InputFeatureUsage | Controlador do HP reverbo G2 (OpenXR) | Mão do HoloLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Botões | |
| primary2DAxisClick | Joystick – clique em | |
| gatilho | Gatilho  | |
| Aperto | Aperto | Toque de ar ou pressão |
| primaryButton | [X/A] – Pressionar | Fechar e abrir dedos indicador e polegar |
| secondaryButton | [Y/B] – Pressionar | |
| gripButton | Segurar – Pressionar | |
| triggerButton | Gatilho – Pressionar | |
| menuButton | Menu | |

### <a name="aim-and-grip-poses"></a>Poses de ponta e de mão

Você tem acesso a dois conjuntos de poses por meio de interações de entrada do OpenXR:

* A mão representa para renderizar objetos na mão
* O objetivo é apontar para o mundo.

Mais informações sobre esse design e as diferenças entre as duas poses podem ser encontradas na Especificação [openXR – Subcaminhos de entrada.](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)

As poses fornecidas pela InputFeatureUsages **DevicePosition,** **DeviceRotation,** **DeviceVelocity** e **DeviceAngularVelocity** representam a pose de mão openXR.  InputFeatureUsages relacionados a poses de controle são definidos [em CommonUsages do](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)Unity.

Poses fornecidas pela InputFeatureUsages **PointerPosition,** **PointerRotation,** **PointerVelocity** e **PointerAngularVelocity** representam a **pose** de objetivo openXR. Esses InputFeatureUsages não são definidos em nenhum arquivo C# incluído, portanto, você precisará definir seu próprio InputFeatureUsages da seguinte maneira:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptics

Para obter informações sobre como usar o haptics no sistema de entrada XR da Unity, a documentação pode ser encontrada no [manual do Unity para o Unity XR Input-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).

## <a name="qr-codes"></a>Códigos QR

O HoloLens 2 pode detectar códigos QR no ambiente em torno do headset, estabelecendo um sistema de coordenadas na localização do mundo real de cada código. Você pode encontrar mais detalhes em nossa documentação de [controle de código QR](../platform-capabilities-and-apis/qr-code-tracking.md) .  Ao usar o plug-in OpenXR, pegue o [ `SpatialGraphNodeId` da API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) e use a `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API para localizar o código QR.

Para referência, temos um [projeto de exemplo de acompanhamento QR no GitHub](https://github.com/yl-msft/QRTracking) com mais uma explicação de uso detalhada para a [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="troubleshooting"></a>Solução de problemas

Quando você suspende e retoma um aplicativo do Unity no HoloLens 2, o aplicativo não pode retomar corretamente, o que leva a 4 pontos girando na exibição do HoloLens.

* Defina o **modo de envio de profundidade** como **nenhum** nas configurações do projeto OpenXR como uma solução alternativa
