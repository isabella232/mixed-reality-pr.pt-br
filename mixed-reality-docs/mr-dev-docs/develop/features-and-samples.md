---
title: Exemplos e aplicativos de recursos
description: Mantenha-se atualizado com todos os aplicativos de exemplos e de recursos de realidade misturada da Microsoft para HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 6/7/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, learn, exemplos, MRTK, modo de pesquisa, HoloLens 2, códigos qr, WebRTC, captura de realidade misturada, comunicação remota holográfica, Ferramentas de Experiência de Usuário
ms.localizationpriority: high
ms.openlocfilehash: 78a9e343fde4a6cbc23268f0be353577498d67b6
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906892"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="93b42-104">Exemplos e aplicativos de recursos</span><span class="sxs-lookup"><span data-stu-id="93b42-104">Samples and feature apps</span></span>

![Imagem de um usuário usando um HoloLens e manipulando um holograma com movimentos de mão](unreal/images/unreal-developer.jpg)

<span data-ttu-id="93b42-106">Todo percurso de desenvolvimento começa com uma retrospectiva das criações de sucesso de outros desenvolvedores: a realidade misturada não é diferente.</span><span class="sxs-lookup"><span data-stu-id="93b42-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="93b42-107">Atualmente, todos os tutoriais e aplicativos de exemplo são criados no Unity ou no Unreal.</span><span class="sxs-lookup"><span data-stu-id="93b42-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="93b42-108">À medida que desenvolvermos conteúdo para outros mecanismos e outras plataformas, você os encontrará sob o título relevante no Sumário.</span><span class="sxs-lookup"><span data-stu-id="93b42-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="93b42-109">Aplicativos de exemplo</span><span class="sxs-lookup"><span data-stu-id="93b42-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="93b42-110">Exemplos de recursos</span><span class="sxs-lookup"><span data-stu-id="93b42-110">Feature samples</span></span>

<span data-ttu-id="93b42-111">Os exemplos de recursos listados abaixo correspondem a implementações específicas que são abordadas em nossa documentação e abrangem uma variedade de plataformas de desenvolvimento e dispositivos de hardware.</span><span class="sxs-lookup"><span data-stu-id="93b42-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="openxr"></a><span data-ttu-id="93b42-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="93b42-112">OpenXR</span></span>

<span data-ttu-id="93b42-113">Para desenvolvedores que direcionam o Unity 2020 para criar aplicativos HoloLens 2 ou de Realidade Misturada, o plug-in OpenXR pode ser usado em vez do plug-in WindowsXR para uma melhor compatibilidade entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="93b42-113">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span> <span data-ttu-id="93b42-114">O plug-in OpenXR de Realidade Misturada também funciona bem com a versão mais recente do Kit de ferramentas de Realidade Misturada 2.7.</span><span class="sxs-lookup"><span data-stu-id="93b42-114">The Mixed Reality OpenXR Plugin also works well with latest Mixed Reality Toolkit 2.7.</span></span>

<br>

| <span data-ttu-id="93b42-115">Artigo de referência</span><span class="sxs-lookup"><span data-stu-id="93b42-115">Reference article</span></span> | <span data-ttu-id="93b42-116">Amostra</span><span class="sxs-lookup"><span data-stu-id="93b42-116">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="93b42-117">Como usar o plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="93b42-117">Using the OpenXR plugin</span></span>](./unity/xr-project-setup.md) | [<span data-ttu-id="93b42-118">OpenXR de Realidade Misturada com exemplos do Unity</span><span class="sxs-lookup"><span data-stu-id="93b42-118">Mixed Reality OpenXR with Unity samples</span></span>](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) |
| <span data-ttu-id="93b42-119">N/D</span><span class="sxs-lookup"><span data-stu-id="93b42-119">N/A</span></span> | [<span data-ttu-id="93b42-120">Projeto do Unity com base no OpenXR do MRTK</span><span class="sxs-lookup"><span data-stu-id="93b42-120">OpenXR MRTK Base Unity project</span></span>](https://github.com/microsoft/UnityOpenXRMRTKBase) |

### <a name="research-mode"></a><span data-ttu-id="93b42-121">Modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="93b42-121">Research Mode</span></span>

<span data-ttu-id="93b42-122">O modo de pesquisa foi introduzido no HoloLens (1ª geração) para dar acesso aos principais sensores no dispositivo, especificamente para aplicativos de pesquisa não destinados à implantação.</span><span class="sxs-lookup"><span data-stu-id="93b42-122">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="93b42-123">Os aplicativos abaixo são exemplos para acessar e gravar fluxos do modo de pesquisa e usar os [intrínsecos e os extrínsecos](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span><span class="sxs-lookup"><span data-stu-id="93b42-123">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="93b42-124">Artigo de referência</span><span class="sxs-lookup"><span data-stu-id="93b42-124">Reference article</span></span> | <span data-ttu-id="93b42-125">Aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="93b42-125">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="93b42-126">Modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="93b42-126">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="93b42-127">HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="93b42-127">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="93b42-128">Modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="93b42-128">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="93b42-129">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="93b42-129">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="93b42-130">Códigos QR</span><span class="sxs-lookup"><span data-stu-id="93b42-130">QR codes</span></span>

<span data-ttu-id="93b42-131">O HoloLens 2 pode detectar códigos QR no ambiente em torno do headset, estabelecendo um sistema de coordenadas na localização do mundo real de cada código.</span><span class="sxs-lookup"><span data-stu-id="93b42-131">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="93b42-132">Artigo de referência</span><span class="sxs-lookup"><span data-stu-id="93b42-132">Reference article</span></span> | <span data-ttu-id="93b42-133">Amostra</span><span class="sxs-lookup"><span data-stu-id="93b42-133">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="93b42-134">Códigos QR</span><span class="sxs-lookup"><span data-stu-id="93b42-134">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="93b42-135">Controle de código QR no Unity</span><span class="sxs-lookup"><span data-stu-id="93b42-135">QR code tracking in Unity</span></span>](https://github.com/microsoft/MixedReality-QRCode-Sample) |

### <a name="scene-understanding"></a><span data-ttu-id="93b42-136">Reconhecimento de cena</span><span class="sxs-lookup"><span data-stu-id="93b42-136">Scene understanding</span></span>

<span data-ttu-id="93b42-137">O reconhecimento de cena fornece aos desenvolvedores de Realidade Misturada uma representação de ambiente estruturada e de alto nível, projetada para tornar intuitivo o desenvolvimento de aplicativos ecologicamente corretos.</span><span class="sxs-lookup"><span data-stu-id="93b42-137">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="93b42-138">O reconhecimento de cena faz isso combinando o poder dos runtimes de realidade misturada existentes, como o mapeamento espacial altamente preciso porém pouco estruturado, e os novos runtimes orientados por IA.</span><span class="sxs-lookup"><span data-stu-id="93b42-138">Scene understanding does this by combining the power of existing mixed reality runtimes, like the highly accurate but less structured spatial mapping and new AI driven runtimes.</span></span>

<br>

| <span data-ttu-id="93b42-139">Artigo de referência</span><span class="sxs-lookup"><span data-stu-id="93b42-139">Reference article</span></span> | <span data-ttu-id="93b42-140">Amostra</span><span class="sxs-lookup"><span data-stu-id="93b42-140">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="93b42-141">Reconhecimento de cena</span><span class="sxs-lookup"><span data-stu-id="93b42-141">Scene understanding</span></span>](../design/scene-understanding.md) | [<span data-ttu-id="93b42-142">Exemplos de reconhecimento de cena de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="93b42-142">Mixed Reality Scene Understanding samples</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) |

### <a name="webrtc"></a><span data-ttu-id="93b42-143">WebRTC</span><span class="sxs-lookup"><span data-stu-id="93b42-143">WebRTC</span></span>

<span data-ttu-id="93b42-144">O projeto MixedReality-WebRTC é uma coleção de componentes destinada a ajudar os desenvolvedores de aplicativos de realidade misturada a integrar áudio e vídeo ponto a ponto e comunicação em tempo real de dados aos aplicativos. Os componentes do WebRTC são baseados no protocolo WebRTC do RTC (Comunicação em Tempo Real), compatível com a maioria dos navegadores da Web modernos.</span><span class="sxs-lookup"><span data-stu-id="93b42-144">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="93b42-145">Artigo de referência</span><span class="sxs-lookup"><span data-stu-id="93b42-145">Reference article</span></span> | <span data-ttu-id="93b42-146">Amostra</span><span class="sxs-lookup"><span data-stu-id="93b42-146">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="93b42-147">WebRTC</span><span class="sxs-lookup"><span data-stu-id="93b42-147">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="93b42-148">Aplicativos de exemplo do WebRTC</span><span class="sxs-lookup"><span data-stu-id="93b42-148">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="93b42-149">Captura de Realidade Misturada holográfica</span><span class="sxs-lookup"><span data-stu-id="93b42-149">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="93b42-150">A MRC (Captura de Realidade Misturada) captura a experiência da primeira pessoa de misturar os mundos real e digital como uma foto ou um vídeo, compartilhando o que você vê com outras pessoas em tempo real.</span><span class="sxs-lookup"><span data-stu-id="93b42-150">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="93b42-151">Artigo de referência</span><span class="sxs-lookup"><span data-stu-id="93b42-151">Reference article</span></span> | <span data-ttu-id="93b42-152">Amostra</span><span class="sxs-lookup"><span data-stu-id="93b42-152">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="93b42-153">Captura de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="93b42-153">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="93b42-154">Exemplos da Captura de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="93b42-154">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="93b42-155">Comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="93b42-155">Holographic Remoting</span></span>

<span data-ttu-id="93b42-156">O Holographic Remoting Player é um aplicativo complementar que se conecta a aplicativos do PC e jogos que dão suporte à comunicação remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="93b42-156">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="93b42-157">A comunicação remota holográfica transmite o conteúdo holográfico de um PC para o Microsoft HoloLens em tempo real usando uma conexão Wi-Fi e é compatível com o HoloLens (1ª geração) e o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="93b42-157">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="93b42-158">Artigo de referência</span><span class="sxs-lookup"><span data-stu-id="93b42-158">Reference article</span></span> | <span data-ttu-id="93b42-159">Amostra</span><span class="sxs-lookup"><span data-stu-id="93b42-159">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="93b42-160">Comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="93b42-160">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="93b42-161">Exemplos da comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="93b42-161">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |