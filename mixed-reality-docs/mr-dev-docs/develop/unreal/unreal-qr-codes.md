---
title: Códigos QR no Unreal
description: Saiba como configurar, usar e controlar códigos QR em aplicativos de realidade misturada no Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, códigos qr, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: d9f23bacf31b310da6d49e74de2153b50e642c7d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98582663"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="cb88f-104">Códigos QR no Unreal</span><span class="sxs-lookup"><span data-stu-id="cb88f-104">QR codes in Unreal</span></span>

<span data-ttu-id="cb88f-105">O HoloLens 2 pode ver códigos QR no espaço de mundo usando a webcam, que os renderiza como hologramas na posição de cada código no mundo real.</span><span class="sxs-lookup"><span data-stu-id="cb88f-105">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms at each code's real-world position.</span></span> <span data-ttu-id="cb88f-106">O HoloLens 2 também pode renderizar os hologramas em vários dispositivos na mesma localização para criar uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="cb88f-106">HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="cb88f-107">Verifique se você está seguindo as melhores práticas para adicionar códigos QR aos aplicativos:</span><span class="sxs-lookup"><span data-stu-id="cb88f-107">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="cb88f-108">Zonas silenciosas</span><span class="sxs-lookup"><span data-stu-id="cb88f-108">Quiet zones</span></span>
- <span data-ttu-id="cb88f-109">Iluminação e pano de fundo</span><span class="sxs-lookup"><span data-stu-id="cb88f-109">Lighting and backdrop</span></span>
- <span data-ttu-id="cb88f-110">Tamanho, distância e posição angular</span><span class="sxs-lookup"><span data-stu-id="cb88f-110">Size, distance, and angular position</span></span>

<span data-ttu-id="cb88f-111">Preste atenção especial às [considerações sobre o ambiente](/hololens/hololens-environment-considerations) quando os códigos QR estiverem sendo posicionados em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cb88f-111">Pay special attention to the [environment considerations](/hololens/hololens-environment-considerations) when QR codes are being placed in your app.</span></span> <span data-ttu-id="cb88f-112">Você pode encontrar mais informações sobre cada um desses tópicos e instruções sobre como baixar o pacote NuGet necessário no documento principal [rastreamento de código QR](../platform-capabilities-and-apis/qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="cb88f-112">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

> [!CAUTION]
> <span data-ttu-id="cb88f-113">Os códigos QR são os únicos tipos de imagens que podem ser controlados pelo HoloLens para uso imediato. Não há suporte ao módulo **UARTrackedImage** do Unreal no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cb88f-113">QR codes are the only type of images that can be tracked by HoloLens out of the box - Unreal's **UARTrackedImage** module isn't supported on HoloLens.</span></span> <span data-ttu-id="cb88f-114">Se precisar controlar imagens personalizadas, acesse a [webcam](unreal-hololens-camera.md) do dispositivo e processe imagens usando uma biblioteca de reconhecimento de imagem de terceiros.</span><span class="sxs-lookup"><span data-stu-id="cb88f-114">If you need to track custom images, you can access the device's [webcam](unreal-hololens-camera.md) and process images using a third party image recognition library.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="cb88f-115">Como habilitar a detecção de QR</span><span class="sxs-lookup"><span data-stu-id="cb88f-115">Enabling QR detection</span></span>

<span data-ttu-id="cb88f-116">Como o HoloLens 2 precisa usar a webcam para ver os códigos QR, você precisará habilitá-la nas configurações do projeto:</span><span class="sxs-lookup"><span data-stu-id="cb88f-116">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="cb88f-117">Abra **Editar > Configurações de Projeto**, role o painel até a seção **Plataformas** e selecione **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="cb88f-117">Open **Edit > Project Settings**, scroll to the **Platforms** section, and select **HoloLens**.</span></span>
    + <span data-ttu-id="cb88f-118">Expanda a seção **Funcionalidades** e marque **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="cb88f-118">Expand the **Capabilities** section and check **Webcam**.</span></span>  
- <span data-ttu-id="cb88f-119">Você também precisará aceitar o controle de código QR [adicionando um ativo ARSessionConfig](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="cb88f-119">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a><span data-ttu-id="cb88f-120">Como configurar um código QR controlado</span><span class="sxs-lookup"><span data-stu-id="cb88f-120">Setting up a tracked QR code</span></span>

<span data-ttu-id="cb88f-121">Os códigos QR são exibidos por meio do sistema de geometria controlado pelo RA do Unreal como uma imagem rastreada.</span><span class="sxs-lookup"><span data-stu-id="cb88f-121">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="cb88f-122">Para fazer isso funcionar, você precisará:</span><span class="sxs-lookup"><span data-stu-id="cb88f-122">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="cb88f-123">Criar um Blueprint Actor e adicionar um componente **ARTrackableNotify**:</span><span class="sxs-lookup"><span data-stu-id="cb88f-123">Create an Actor Blueprint and add an **ARTrackableNotify** component:</span></span>

![AR Trackable Notify de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="cb88f-125">Selecionar **ARTrackableNotify** e expandir a seção **Eventos** no painel **Detalhes**:</span><span class="sxs-lookup"><span data-stu-id="cb88f-125">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel:</span></span>

![Eventos de QR](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="cb88f-127">Clique em **+** ao lado de **Ao Adicionar Geometria Rastreada** para adicionar o nó ao Grafo de Eventos.</span><span class="sxs-lookup"><span data-stu-id="cb88f-127">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="cb88f-128">Você pode encontrar a lista completa de eventos na API do componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="cb88f-128">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![Adicionar nó a Ao Adicionar Geometria Rastreada](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a><span data-ttu-id="cb88f-130">Como usar um código QR controlado</span><span class="sxs-lookup"><span data-stu-id="cb88f-130">Using a tracked QR code</span></span>

<span data-ttu-id="cb88f-131">O Grafo de Eventos na imagem a seguir mostra o evento **OnUpdateTrackedImage** que está sendo usado para processar um ponto no centro de um código QR e imprimir os dados desse código.</span><span class="sxs-lookup"><span data-stu-id="cb88f-131">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

<span data-ttu-id="cb88f-132">Isto é o que está acontecendo:</span><span class="sxs-lookup"><span data-stu-id="cb88f-132">Here's what's going on:</span></span>
1. <span data-ttu-id="cb88f-133">Primeiro, a imagem rastreada é convertida em um **ARTrackedQRCode** para verificar se a imagem atualizada atual é um código QR.</span><span class="sxs-lookup"><span data-stu-id="cb88f-133">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="cb88f-134">Os dados codificados são recuperados da variável **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="cb88f-134">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="cb88f-135">Com o local de **GetLocalToWorldTransform**, é possível obter as coordenadas do canto superior esquerdo do código QR; já com **GetEstimateSize**, é possível obter as dimensões desse código.</span><span class="sxs-lookup"><span data-stu-id="cb88f-135">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="cb88f-136">Você também pode [obter o sistema de coordenadas de um código QR](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) no código.</span><span class="sxs-lookup"><span data-stu-id="cb88f-136">You can also [get the coordinate system for a QR code](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="cb88f-137">Como localizar a ID exclusiva</span><span class="sxs-lookup"><span data-stu-id="cb88f-137">Finding the unique ID</span></span>

<span data-ttu-id="cb88f-138">Todo código QR tem uma ID GUID exclusiva, que pode ser encontrada:</span><span class="sxs-lookup"><span data-stu-id="cb88f-138">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="cb88f-139">Arrastando e soltando o marcador **Como QRCode ARTracked** e pesquisando por **Obter ID Exclusiva**.</span><span class="sxs-lookup"><span data-stu-id="cb88f-139">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID de QR](images/unreal-qr-guid.PNG)

<span data-ttu-id="cb88f-141">Há muita coisa acontecendo nos bastidores envolvendo os códigos QR. Portanto, esse não é o final da estrada.</span><span class="sxs-lookup"><span data-stu-id="cb88f-141">There's a lot going on behind the scenes with QR codes, so you're not at the end of the road.</span></span> <span data-ttu-id="cb88f-142">Não deixe de conferir os links a seguir para obter mais detalhes sobre o que está acontecendo nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="cb88f-142">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="cb88f-143">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="cb88f-143">Next Development Checkpoint</span></span>

<span data-ttu-id="cb88f-144">Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unreal que apresentamos, você está no meio da exploração de funcionalidades e APIs da plataforma de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="cb88f-144">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="cb88f-145">Daí, você pode prosseguir para o próximo tópico:</span><span class="sxs-lookup"><span data-stu-id="cb88f-145">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cb88f-146">WinRT</span><span class="sxs-lookup"><span data-stu-id="cb88f-146">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="cb88f-147">Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:</span><span class="sxs-lookup"><span data-stu-id="cb88f-147">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cb88f-148">Como fazer a implantação no dispositivo</span><span class="sxs-lookup"><span data-stu-id="cb88f-148">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="cb88f-149">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#3-advanced-features) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="cb88f-149">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb88f-150">Veja também</span><span class="sxs-lookup"><span data-stu-id="cb88f-150">See also</span></span>
* [<span data-ttu-id="cb88f-151">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="cb88f-151">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="cb88f-152">Hologramas</span><span class="sxs-lookup"><span data-stu-id="cb88f-152">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="cb88f-153">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="cb88f-153">Coordinate systems</span></span>](../../design/coordinate-systems.md)