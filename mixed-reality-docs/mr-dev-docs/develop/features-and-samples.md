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
# <a name="samples-and-feature-apps"></a><span data-ttu-id="7475d-104">Exemplos e aplicativos de recursos</span><span class="sxs-lookup"><span data-stu-id="7475d-104">Samples and feature apps</span></span>

![Imagem de um usuário usando um HoloLens e manipulando um holograma com movimentos de mão](unreal/images/unreal-developer.jpg)

<span data-ttu-id="7475d-106">Todo percurso de desenvolvimento começa com uma retrospectiva das criações de sucesso de outros desenvolvedores: a realidade misturada não é diferente.</span><span class="sxs-lookup"><span data-stu-id="7475d-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="7475d-107">Atualmente, todos os tutoriais e aplicativos de exemplo são criados no Unity ou no Unreal.</span><span class="sxs-lookup"><span data-stu-id="7475d-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="7475d-108">À medida que desenvolvermos conteúdo para outros mecanismos e outras plataformas, você os encontrará sob o título relevante no Sumário.</span><span class="sxs-lookup"><span data-stu-id="7475d-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="7475d-109">Aplicativos de exemplo</span><span class="sxs-lookup"><span data-stu-id="7475d-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="7475d-110">Exemplos de recursos</span><span class="sxs-lookup"><span data-stu-id="7475d-110">Feature samples</span></span>

<span data-ttu-id="7475d-111">Os exemplos de recursos listados abaixo correspondem a implementações específicas que são abordadas em nossa documentação e abrangem uma variedade de plataformas de desenvolvimento e dispositivos de hardware.</span><span class="sxs-lookup"><span data-stu-id="7475d-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="research-mode"></a><span data-ttu-id="7475d-112">Modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="7475d-112">Research Mode</span></span>

<span data-ttu-id="7475d-113">O modo de pesquisa foi introduzido no HoloLens (1ª geração) para dar acesso aos principais sensores no dispositivo, especificamente para aplicativos de pesquisa não destinados à implantação.</span><span class="sxs-lookup"><span data-stu-id="7475d-113">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="7475d-114">Os aplicativos abaixo são exemplos para acessar e gravar fluxos do modo de pesquisa e usar os [intrínsecos e os extrínsecos](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span><span class="sxs-lookup"><span data-stu-id="7475d-114">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="7475d-115">Artigo de referência</span><span class="sxs-lookup"><span data-stu-id="7475d-115">Reference article</span></span> | <span data-ttu-id="7475d-116">Aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="7475d-116">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="7475d-117">Modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="7475d-117">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="7475d-118">HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="7475d-118">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="7475d-119">Modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="7475d-119">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="7475d-120">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7475d-120">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="7475d-121">Códigos QR</span><span class="sxs-lookup"><span data-stu-id="7475d-121">QR codes</span></span>

<span data-ttu-id="7475d-122">O HoloLens 2 pode detectar códigos QR no ambiente em torno do headset, estabelecendo um sistema de coordenadas na localização do mundo real de cada código.</span><span class="sxs-lookup"><span data-stu-id="7475d-122">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="7475d-123">Artigo de referência</span><span class="sxs-lookup"><span data-stu-id="7475d-123">Reference article</span></span> | <span data-ttu-id="7475d-124">Amostra</span><span class="sxs-lookup"><span data-stu-id="7475d-124">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="7475d-125">Códigos QR</span><span class="sxs-lookup"><span data-stu-id="7475d-125">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="7475d-126">Controle de código QR no Unity</span><span class="sxs-lookup"><span data-stu-id="7475d-126">QR code tracking in Unity</span></span>](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a><span data-ttu-id="7475d-127">WebRTC</span><span class="sxs-lookup"><span data-stu-id="7475d-127">WebRTC</span></span>

<span data-ttu-id="7475d-128">O projeto MixedReality-WebRTC é uma coleção de componentes destinada a ajudar os desenvolvedores de aplicativos de realidade misturada a integrar áudio e vídeo ponto a ponto e comunicação em tempo real de dados aos aplicativos. Os componentes do WebRTC são baseados no protocolo WebRTC do RTC (Comunicação em Tempo Real), compatível com a maioria dos navegadores da Web modernos.</span><span class="sxs-lookup"><span data-stu-id="7475d-128">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="7475d-129">Artigo de referência</span><span class="sxs-lookup"><span data-stu-id="7475d-129">Reference article</span></span> | <span data-ttu-id="7475d-130">Amostra</span><span class="sxs-lookup"><span data-stu-id="7475d-130">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="7475d-131">WebRTC</span><span class="sxs-lookup"><span data-stu-id="7475d-131">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="7475d-132">Aplicativos de exemplo do WebRTC</span><span class="sxs-lookup"><span data-stu-id="7475d-132">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="7475d-133">Captura de Realidade Misturada holográfica</span><span class="sxs-lookup"><span data-stu-id="7475d-133">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="7475d-134">A MRC (Captura de Realidade Misturada) captura a experiência da primeira pessoa de misturar os mundos real e digital como uma foto ou um vídeo, compartilhando o que você vê com outras pessoas em tempo real.</span><span class="sxs-lookup"><span data-stu-id="7475d-134">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="7475d-135">Artigo de referência</span><span class="sxs-lookup"><span data-stu-id="7475d-135">Reference article</span></span> | <span data-ttu-id="7475d-136">Amostra</span><span class="sxs-lookup"><span data-stu-id="7475d-136">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="7475d-137">Captura de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="7475d-137">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="7475d-138">Exemplos da Captura de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="7475d-138">Mixed Reality Capture samples</span></span>](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="7475d-139">Comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="7475d-139">Holographic Remoting</span></span>

<span data-ttu-id="7475d-140">O Holographic Remoting Player é um aplicativo complementar que se conecta a aplicativos do PC e jogos que dão suporte à comunicação remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="7475d-140">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="7475d-141">A comunicação remota holográfica transmite o conteúdo holográfico de um PC para o Microsoft HoloLens em tempo real usando uma conexão Wi-Fi e é compatível com o HoloLens (1ª geração) e o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7475d-141">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="7475d-142">Artigo de referência</span><span class="sxs-lookup"><span data-stu-id="7475d-142">Reference article</span></span> | <span data-ttu-id="7475d-143">Amostra</span><span class="sxs-lookup"><span data-stu-id="7475d-143">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="7475d-144">Comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="7475d-144">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="7475d-145">Exemplos da comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="7475d-145">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |