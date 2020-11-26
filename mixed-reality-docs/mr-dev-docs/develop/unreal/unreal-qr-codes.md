---
title: Códigos QR no Unreal
description: Um guia para usar códigos QR no Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, códigos qr, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 68edfdd0dd77b1d00ceeb9c50202abd5d94b95f3
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678885"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="b36bc-104">Códigos QR no Unreal</span><span class="sxs-lookup"><span data-stu-id="b36bc-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="b36bc-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="b36bc-105">Overview</span></span>

<span data-ttu-id="b36bc-106">O HoloLens 2 pode ver códigos QR no espaço de mundo usando a webcam, que os renderiza como hologramas usando um sistema de coordenadas na posição de cada código no mundo real.</span><span class="sxs-lookup"><span data-stu-id="b36bc-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="b36bc-107">Além de códigos QR individuais, o HoloLens 2 também pode renderizar hologramas em vários dispositivos no mesmo local para criar uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="b36bc-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="b36bc-108">Verifique se você está seguindo as melhores práticas para adicionar códigos QR aos aplicativos:</span><span class="sxs-lookup"><span data-stu-id="b36bc-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="b36bc-109">Zonas silenciosas</span><span class="sxs-lookup"><span data-stu-id="b36bc-109">Quiet zones</span></span>
- <span data-ttu-id="b36bc-110">Iluminação e pano de fundo</span><span class="sxs-lookup"><span data-stu-id="b36bc-110">Lighting and backdrop</span></span>
- <span data-ttu-id="b36bc-111">Tamanho, distância e posição angular</span><span class="sxs-lookup"><span data-stu-id="b36bc-111">Size, distance, and angular position</span></span>

<span data-ttu-id="b36bc-112">Preste atenção especial às [considerações sobre o ambiente](../../environment-considerations-for-hololens.md) quando os códigos QR estiverem sendo posicionados em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b36bc-112">Pay special attention to the [environment considerations](../../environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="b36bc-113">Você pode encontrar mais informações sobre cada um desses tópicos e instruções sobre como baixar o pacote NuGet necessário no documento principal [rastreamento de código QR](../platform-capabilities-and-apis/qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="b36bc-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

## <a name="enabling-qr-detection"></a><span data-ttu-id="b36bc-114">Como habilitar a detecção de QR</span><span class="sxs-lookup"><span data-stu-id="b36bc-114">Enabling QR detection</span></span>
<span data-ttu-id="b36bc-115">Como o HoloLens 2 precisa usar a webcam para ver os códigos QR, você precisará habilitá-la nas configurações do projeto:</span><span class="sxs-lookup"><span data-stu-id="b36bc-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="b36bc-116">Abra **Editar > Configurações do Projeto**, role até a seção **Plataformas** e clique em **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="b36bc-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="b36bc-117">Expanda a seção **Funcionalidades** e marque **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="b36bc-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="b36bc-118">Você também precisará aceitar o controle de código QR [adicionando um ativo ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="b36bc-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

<span data-ttu-id="b36bc-119">Logo antes do uso, habilite manualmente o rastreamento chamando `UHoloLensARFunctionLibrary::StartCameraCapture()`.</span><span class="sxs-lookup"><span data-stu-id="b36bc-119">Right before the usage, you should manually enable the tracking by calling `UHoloLensARFunctionLibrary::StartCameraCapture()`.</span></span> <span data-ttu-id="b36bc-120">Depois de encerrar o rastreamento do código QR, desabilite-o com `UHoloLensARFunctionLibrary::StopCameraCapture()` para salvar os recursos do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b36bc-120">After ending the QR code tracking, you should disable it by `UHoloLensARFunctionLibrary::StopCameraCapture()` to save the device resources.</span></span>

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="b36bc-121">Configurar uma imagem rastreada</span><span class="sxs-lookup"><span data-stu-id="b36bc-121">Setting up a tracked image</span></span>

<span data-ttu-id="b36bc-122">Os códigos QR são exibidos por meio do sistema de geometria controlado pelo RA do Unreal como uma imagem rastreada.</span><span class="sxs-lookup"><span data-stu-id="b36bc-122">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="b36bc-123">Para fazer isso funcionar, você precisará:</span><span class="sxs-lookup"><span data-stu-id="b36bc-123">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="b36bc-124">Criar um Blueprint e adicionar um componente **ARTrackableNotify** a ele.</span><span class="sxs-lookup"><span data-stu-id="b36bc-124">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![AR Trackable Notify de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="b36bc-126">Selecione **ARTrackableNotify** e expanda a seção **Eventos** no painel **Detalhes**.</span><span class="sxs-lookup"><span data-stu-id="b36bc-126">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span>

![Eventos de QR](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="b36bc-128">Clique em **+** ao lado de **Ao Adicionar Geometria Rastreada** para adicionar o nó ao Grafo de Eventos.</span><span class="sxs-lookup"><span data-stu-id="b36bc-128">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="b36bc-129">Você pode encontrar a lista completa de eventos na API do componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="b36bc-129">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![Adicionar nó a Ao Adicionar Geometria Rastreada](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="b36bc-131">Como usar uma imagem rastreada</span><span class="sxs-lookup"><span data-stu-id="b36bc-131">Using a tracked image</span></span>
<span data-ttu-id="b36bc-132">O Grafo de Eventos na imagem a seguir mostra o evento **OnUpdateTrackedImage** que está sendo usado para processar um ponto no centro de um código QR e imprimir os dados desse código.</span><span class="sxs-lookup"><span data-stu-id="b36bc-132">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

![Exemplo de renderização de QR](images/unreal-qr-render.PNG)

<span data-ttu-id="b36bc-134">Isto é o que está acontecendo:</span><span class="sxs-lookup"><span data-stu-id="b36bc-134">Here's what's going on:</span></span>
1. <span data-ttu-id="b36bc-135">Primeiro, a imagem rastreada é convertida em um **ARTrackedQRCode** para verificar se a imagem atualizada atual é um código QR.</span><span class="sxs-lookup"><span data-stu-id="b36bc-135">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="b36bc-136">Os dados codificados são recuperados da variável **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="b36bc-136">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="b36bc-137">Com o local de **GetLocalToWorldTransform**, é possível obter as coordenadas do canto superior esquerdo do código QR; já com **GetEstimateSize**, é possível obter as dimensões desse código.</span><span class="sxs-lookup"><span data-stu-id="b36bc-137">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="b36bc-138">Você também pode [obter o sistema de coordenadas de um código QR](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) no código.</span><span class="sxs-lookup"><span data-stu-id="b36bc-138">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="b36bc-139">Como localizar a ID exclusiva</span><span class="sxs-lookup"><span data-stu-id="b36bc-139">Finding the unique ID</span></span>
<span data-ttu-id="b36bc-140">Todo código QR tem uma ID GUID exclusiva, que pode ser encontrada:</span><span class="sxs-lookup"><span data-stu-id="b36bc-140">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="b36bc-141">Arrastando e soltando o marcador **Como QRCode ARTracked** e pesquisando por **Obter ID Exclusiva**.</span><span class="sxs-lookup"><span data-stu-id="b36bc-141">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID de QR](images/unreal-qr-guid.PNG)

<span data-ttu-id="b36bc-143">Há muita coisa acontecendo nos bastidores envolvendo códigos QR, portanto, esse não é o fim da linha.</span><span class="sxs-lookup"><span data-stu-id="b36bc-143">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="b36bc-144">Não deixe de conferir os links a seguir para obter mais detalhes sobre o que está acontecendo nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="b36bc-144">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b36bc-145">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="b36bc-145">Next Development Checkpoint</span></span>

<span data-ttu-id="b36bc-146">Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unreal que apresentamos, você está no meio da exploração de funcionalidades e APIs da plataforma de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="b36bc-146">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="b36bc-147">Daí, você pode prosseguir para o próximo tópico:</span><span class="sxs-lookup"><span data-stu-id="b36bc-147">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b36bc-148">WinRT</span><span class="sxs-lookup"><span data-stu-id="b36bc-148">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="b36bc-149">Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:</span><span class="sxs-lookup"><span data-stu-id="b36bc-149">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b36bc-150">Como fazer a implantação no dispositivo</span><span class="sxs-lookup"><span data-stu-id="b36bc-150">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="b36bc-151">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="b36bc-151">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b36bc-152">Veja também</span><span class="sxs-lookup"><span data-stu-id="b36bc-152">See also</span></span>
* [<span data-ttu-id="b36bc-153">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="b36bc-153">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="b36bc-154">Hologramas</span><span class="sxs-lookup"><span data-stu-id="b36bc-154">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="b36bc-155">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="b36bc-155">Coordinate systems</span></span>](../../design/coordinate-systems.md)
