---
title: Recursos com suporte do plug-in OpenXR no Unity
description: Descubra os recursos que o OpenXR dá suporte para desenvolvimento de realidade misturada no Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realidade misturada, MRTK, Kit de Ferramentas de Realidade Misturada, realidade aumentada, realidade virtual, headsets de realidade misturada, learn, tutorial, introdução
ms.openlocfilehash: e622cd617ccf67c0877b9064efe791743e4c34b6
ms.sourcegitcommit: c9d52f9529cabeaf912fffa6efc6599a9041a929
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112398049"
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
* (Adicionado na 0.1.4) Dá [suporte ao acompanhamento de código QR](#qr-codes) no HoloLens2 por meio de SpatialGraphNode
* (Adicionado em 0.2.0) Dá **suporte à âncora** na remoção holográfica
* (Adicionado em 0.2.0) Dá suporte a **junções de mão e acompanhamento de malha manual**
* (Adicionado em 0.2.0) Dá **suporte a ARPlaneSubsystems para** detecção de plano e colocação de holograma usando **ARRaycastManager**.
* (0.9.0) Dá suporte **a XRMeshSubsystem** e **ARMeshManager** para mapeamento espacial.
* (Adicionado em 0.9.0) Dá suporte ao plug-in do SDK de Âncoras Espaciais do Azure para Windows. Para obter mais informações, consulte o projeto de exemplo [Realidade Misturada + Âncoras Espaciais do Azure OpenXR no GitHub.](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)
* (Adicionado em 0.9.1) Dá suporte ao aplicativo de área de trabalho Holographic Remoting de um aplicativo UWP do Windows criado e implantado.
* (Adicionado na 0.9.4) Dá suporte à plataforma ARM além do aplicativo ARM64 para HoloLens 2.

## <a name="motion-controller-and-hand-interactions"></a>Controlador de movimento e interações com a mão

Para saber as noções básicas sobre interações de realidade misturada no Unity, visite o Manual do [Unity para Entrada XR do Unity.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html) Esta documentação do Unity aborda os mapeamentos de entradas específicas do controlador para entradas mais generalizáveis **InputFeatureUsage** s, como as entradas XR disponíveis podem ser identificadas e categorizadas, como ler dados dessas entradas e muito mais.

O Plug-in OpenXR de Realidade Misturada fornece perfis de interação de entrada adicionais, mapeados para **InputFeatureUsage** s padrão, conforme detalhado abaixo:

| InputFeatureUsage | Controlador HP Reverb G2 (OpenXR) | Mão do HoloLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Mouse – Click | |
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

### <a name="haptics"></a>Nárticos

Para obter informações sobre como usar o tics no sistema de Entrada XR do Unity, a documentação pode ser encontrada no Manual do Unity para Entrada XR do [Unity – Tics.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)

## <a name="qr-codes"></a>Códigos QR

O HoloLens 2 pode detectar códigos QR no ambiente em torno do headset, estabelecendo um sistema de coordenadas na localização do mundo real de cada código. Você pode encontrar mais detalhes em nossa [documentação de acompanhamento de código QR.](../platform-capabilities-and-apis/qr-code-tracking.md)  Ao usar o plug-in OpenXR, pegue o da [ `SpatialGraphNodeId` API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) e use a `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API para localizar o código QR.

Para referência, temos um projeto de exemplo de acompanhamento de [QR no GitHub](https://github.com/yl-msft/QRTracking) com uma explicação de uso mais detalhada para a [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="troubleshooting"></a>Solução de problemas

Quando você suspende e retoma um aplicativo unity no HoloLens 2, o aplicativo não pode ser retomado corretamente, o que leva a quatro pontos de rotação na exibição do HoloLens.

* Definir **Modo de envio de** profundidade como **Nenhum** nas configurações do projeto OpenXR como uma solução alternativa
