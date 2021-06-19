---
title: Recursos com suporte do plug-in OpenXR no Unity
description: Descubra os recursos que o OpenXR dá suporte para desenvolvimento de realidade misturada no Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução
ms.openlocfilehash: 371815d6410a7add8ee9c62f72d746d74ad397b0
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392664"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Recursos com suporte da realidade misturada OpenXR no Unity

O pacote de **plug-in OpenXR da realidade mista** é uma extensão do **plug-in OpenXR** do Unity e dá suporte a um conjunto de recursos para headsets do HoloLens 2 e do Windows Mixed Reality. Antes de continuar, verifique se o seu projeto do Unity está [configurado para OpenXR](openxr-getting-started.md).

## <a name="whats-supported"></a>O que tem suporte

Atualmente, há suporte para os seguintes recursos:

* Dá suporte a aplicativos UWP para o HoloLens 2 e otimizar para o modelo de aplicativo do HoloLens 2.
* Dá suporte a aplicativos Win32 VR para o headset de realidade mista do Windows com perfis de controlador mais recentes e comunicação remota de aplicativo Holographic.
* Controle de escala mundial usando âncoras e espaço não associado.
* [API de armazenamento de ancoragem para persistir âncoras](spatial-anchors-in-unity.md) no armazenamento local do HoloLens 2.
* [Controlador de movimento e interações de mão](#motion-controller-and-hand-interactions), incluindo o novo controlador do HP reverberate G2.
* Controle de mão articulado usando 26 junções e entradas de raio conjuntas.
* Observe a interação olhar no HoloLens 2.
* Localizando a câmera de foto/vídeo (PV) no HoloLens 2.
* A realidade misturada é a captura usando o processamento de 3ª vista por meio da câmera VP.
* Dá suporte à ["reprodução" para o HoloLens 2 com o aplicativo de comunicação remota do Holographic](unity-play-mode.md#unity-play-mode-with-holographic-remoting), permitindo que os desenvolvedores depurem scripts sem compilar e implantar no dispositivo.
* Compatível com o MRTK Unity 2.5.3 e mais recente por meio do [suporte do provedor MRTK OpenXR](openxr-getting-started.md#using-mrtk-with-openxr-support).
* Compatível com o Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) ou posterior.
* (Adicionado em 0.1.3) Dá suporte à [comunicação remota do aplicativo de desktop Holographic](holographic-remoting-desktop.md) de um aplicativo autônomo do Windows e compilado.
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
| Dimensiona | Dimensiona | Toque ou aperte o ar |
| primaryButton | [X/A]-Pressione | Fechar e abrir dedos indicador e polegar |
| secondaryButton | [S/B]-Pressione | |
| gripButton | Segure a tecla | |
| triggerButton | Gatilho-Pressione | |
| menuButton | Menu | |

### <a name="aim-and-grip-poses"></a>As poses AIM e segure

Você tem acesso a dois conjuntos de poses por meio de interações de entrada OpenXR:

* A alça representa a renderização de objetos à mão
* O objetivo se destaca no mundo.

Mais informações sobre esse design e as diferenças entre as duas poses podem ser encontradas na [especificação OpenXR-subcaminhos de entrada](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).

As poses fornecidas pelo InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** e **DeviceAngularVelocity** representam a pose de **alça** de OpenXR. Os InputFeatureUsages relacionados a pose são definidos no [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)do Unity.

As poses fornecidas pelo InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** e **PointerAngularVelocity** representam a pose de **AIM** de OpenXR. Esses InputFeatureUsages não são definidos em nenhum arquivo C# incluído, portanto, você precisará definir seu próprio InputFeatureUsages da seguinte maneira:

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
