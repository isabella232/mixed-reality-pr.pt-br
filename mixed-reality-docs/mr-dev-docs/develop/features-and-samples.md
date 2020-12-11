---
title: Exemplos e aplicativos de recursos
description: Dê uma olhada nos exemplos de recursos disponíveis para o HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, learn, exemplos, MRTK, modo de pesquisa, HoloLens 2, códigos qr, WebRTC, captura de realidade misturada, comunicação remota holográfica, Ferramentas de Experiência de Usuário
ms.localizationpriority: high
ms.openlocfilehash: 2624949dd21b4c8e14ed45f152d41900b5f91faf
ms.sourcegitcommit: 924f8c1ceb93c378f800cf88d82944cf80f092bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96615532"
---
# <a name="samples-and-feature-apps"></a>Exemplos e aplicativos de recursos

![Imagem de um usuário usando um HoloLens e manipulando um holograma com movimentos de mão](unreal/images/unreal-developer.jpg)

Todo percurso de desenvolvimento começa com uma retrospectiva das criações de sucesso de outros desenvolvedores: a realidade misturada não é diferente. Atualmente, todos os tutoriais e aplicativos de exemplo são criados no Unity ou no Unreal. À medida que desenvolvermos conteúdo para outros mecanismos e outras plataformas, você os encontrará sob o título relevante no Sumário.

## <a name="sample-apps"></a>Aplicativos de exemplo

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a>Exemplos de recursos

Os exemplos de recursos listados abaixo correspondem a implementações específicas que são abordadas em nossa documentação e abrangem uma variedade de plataformas de desenvolvimento e dispositivos de hardware.

### <a name="research-mode"></a>Modo de pesquisa

O modo de pesquisa foi introduzido no HoloLens (1ª geração) para dar acesso aos principais sensores no dispositivo, especificamente para aplicativos de pesquisa não destinados à implantação. Os aplicativos abaixo são exemplos para acessar e gravar fluxos do modo de pesquisa e usar os [intrínsecos e os extrínsecos](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).

<br>

| Artigo de referência | Aplicativo de exemplo |
| --- | --- |
| [Modo de pesquisa](platform-capabilities-and-apis/research-mode.md) | [HoloLens (1ª geração)](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [Modo de pesquisa](platform-capabilities-and-apis/research-mode.md) | [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a>Códigos QR

O HoloLens 2 pode detectar códigos QR no ambiente em torno do headset, estabelecendo um sistema de coordenadas na localização do mundo real de cada código.

<br>

| Artigo de referência | Amostra |
| --- | --- |
| [Códigos QR](platform-capabilities-and-apis/qr-code-tracking.md) | [Controle de código QR no Unity](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a>WebRTC

O projeto MixedReality-WebRTC é uma coleção de componentes destinada a ajudar os desenvolvedores de aplicativos de realidade misturada a integrar áudio e vídeo ponto a ponto e comunicação em tempo real de dados aos aplicativos. Os componentes do WebRTC são baseados no protocolo WebRTC do RTC (Comunicação em Tempo Real), compatível com a maioria dos navegadores da Web modernos.

<br>

| Artigo de referência | Amostra |
| --- | --- |
| [WebRTC](https://microsoft.github.io/MixedReality-WebRTC) | [Aplicativos de exemplo do WebRTC](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a>Captura de Realidade Misturada holográfica

A MRC (Captura de Realidade Misturada) captura a experiência da primeira pessoa de misturar os mundos real e digital como uma foto ou um vídeo, compartilhando o que você vê com outras pessoas em tempo real.

<br>

| Artigo de referência | Amostra |
| --- | --- |
| [Captura de Realidade Misturada](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [Exemplos da Captura de Realidade Misturada](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a>Comunicação remota holográfica

O Holographic Remoting Player é um aplicativo complementar que se conecta a aplicativos do PC e jogos que dão suporte à comunicação remota holográfica. A comunicação remota holográfica transmite o conteúdo holográfico de um PC para o Microsoft HoloLens em tempo real usando uma conexão Wi-Fi e é compatível com o HoloLens (1ª geração) e o HoloLens 2.

<br>

| Artigo de referência | Amostra |
| --- | --- |
| [Comunicação remota holográfica](platform-capabilities-and-apis/holographic-remoting-player.md) | [Exemplos da comunicação remota holográfica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |