---
title: Câmera de foto/vídeo do HoloLens no Unreal
description: Guia para usar a câmera de foto/vídeo do HoloLens no Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, camera, PV camera, MRC
ms.openlocfilehash: 6302a64fcde2a16b6ae1cb570215629a3e6ea9e5
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573230"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="11736-104">Câmera de foto/vídeo do HoloLens no Unreal</span><span class="sxs-lookup"><span data-stu-id="11736-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="11736-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="11736-105">Overview</span></span>

<span data-ttu-id="11736-106">O HoloLens tem uma câmera de foto/vídeo (PV) que é usada para a MRC (captura de realidade misturada) e pode também ser usada por um aplicativo para acessar elementos visuais do mundo real.</span><span class="sxs-lookup"><span data-stu-id="11736-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="11736-107">A câmera PV não é compatível com a Comunicação Remota Holográfica, mas é possível usar uma webcam anexada ao seu PC para simular a funcionalidade da câmera PV do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="11736-107">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="11736-108">Renderizar da câmera de PV para MRC</span><span class="sxs-lookup"><span data-stu-id="11736-108">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="11736-109">Isso requer o **Unreal Engine 4.25** ou posterior.</span><span class="sxs-lookup"><span data-stu-id="11736-109">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="11736-110">O sistema e os gravadores personalizados de MRC criam capturas de realidade misturada combinando a câmera de PV com hologramas renderizados pelo aplicativo de imersão.</span><span class="sxs-lookup"><span data-stu-id="11736-110">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="11736-111">Por padrão, a captura de realidade misturada usa a saída holográfica do olho direito.</span><span class="sxs-lookup"><span data-stu-id="11736-111">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="11736-112">Se um aplicativo de imersão optar por [renderizar da câmera de PV](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), isso será usado em vez do padrão citado acima.</span><span class="sxs-lookup"><span data-stu-id="11736-112">If an immersive app chooses to [render from the PV Camera](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="11736-113">Isso melhora o mapeamento entre o mundo real e os hologramas no vídeo do MRC.</span><span class="sxs-lookup"><span data-stu-id="11736-113">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="11736-114">Para aceitar a renderização da câmera de PV:</span><span class="sxs-lookup"><span data-stu-id="11736-114">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="11736-115">Chamar **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="11736-115">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="11736-116">Use os valores de **Tamanho X** e **Tamanho Y** para definir as dimensões do vídeo.</span><span class="sxs-lookup"><span data-stu-id="11736-116">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Terceira câmera](../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="11736-118">Em seguida, o Unreal lidará com as solicitações da MRC para renderizar da perspectiva da câmera de PV.</span><span class="sxs-lookup"><span data-stu-id="11736-118">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="11736-119">Somente quando a [Captura de Realidade Misturada](../../mixed-reality-capture.md) for disparada, o aplicativo será solicitado a renderizar partindo da perspectiva da câmera de foto/vídeo.</span><span class="sxs-lookup"><span data-stu-id="11736-119">Only when [Mixed Reality Capture](../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="11736-120">Usando a câmera de PV</span><span class="sxs-lookup"><span data-stu-id="11736-120">Using the PV Camera</span></span>

<span data-ttu-id="11736-121">A textura de webcam pode ser recuperada no jogo em runtime, mas precisa ser habilitada no menu **Editar > Configurações de Projeto** do editor:</span><span class="sxs-lookup"><span data-stu-id="11736-121">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="11736-122">Acesse **Plataformas > HoloLens > Funcionalidades** e marque **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="11736-122">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="11736-123">Use a função **StartCameraCapture** para usar a webcam em runtime e a função **StopCameraCapture** para interromper a gravação.</span><span class="sxs-lookup"><span data-stu-id="11736-123">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Iniciar/interromper câmera](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="11736-125">Renderização de uma imagem</span><span class="sxs-lookup"><span data-stu-id="11736-125">Rendering an image</span></span>
<span data-ttu-id="11736-126">Para renderizar a imagem da câmera:</span><span class="sxs-lookup"><span data-stu-id="11736-126">To render the camera image:</span></span>
1. <span data-ttu-id="11736-127">Crie uma instância de material dinâmico com base em um material no projeto, nomeado **PVCamMat** na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="11736-127">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="11736-128">Defina a instância de material dinâmico para uma variável de **Referência de Objeto Dinâmico da Instância de Material**.</span><span class="sxs-lookup"><span data-stu-id="11736-128">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="11736-129">Defina o material do objeto na cena que renderizará o feed da câmera para essa nova instância de material dinâmico.</span><span class="sxs-lookup"><span data-stu-id="11736-129">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="11736-130">Inicie um temporizador que será usado para associar a imagem da câmera ao material.</span><span class="sxs-lookup"><span data-stu-id="11736-130">Start a timer that will be used to bind the camera image to the material.</span></span>

![Renderização da câmera](images/unreal-camera-render.PNG)

4. <span data-ttu-id="11736-132">Crie uma função para esse temporizador (neste caso, **MaterialTimer**) e chame **GetARCameraImage** para obter a textura da webcam.</span><span class="sxs-lookup"><span data-stu-id="11736-132">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="11736-133">Se a textura for válida, defina um parâmetro de textura no sombreador para a imagem.</span><span class="sxs-lookup"><span data-stu-id="11736-133">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="11736-134">Caso contrário, inicie o temporizador de material novamente.</span><span class="sxs-lookup"><span data-stu-id="11736-134">Otherwise, start the material timer again.</span></span>

![Textura da câmera da webcam](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="11736-136">Verifique se o material tem um parâmetro correspondente ao nome em **SetTextureParameterValue** que esteja associado a uma entrada de cor.</span><span class="sxs-lookup"><span data-stu-id="11736-136">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="11736-137">Sem isso, a imagem da câmera não pode ser exibida corretamente.</span><span class="sxs-lookup"><span data-stu-id="11736-137">Without this, the camera image can't be properly displayed.</span></span>

![Textura da câmera](images/unreal-camera-material.PNG)

## <a name="next-development-checkpoint"></a><span data-ttu-id="11736-139">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="11736-139">Next Development Checkpoint</span></span>

<span data-ttu-id="11736-140">Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unreal que apresentamos, você está no meio da exploração de funcionalidades e APIs da plataforma de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="11736-140">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="11736-141">Daí, você pode prosseguir para o próximo tópico:</span><span class="sxs-lookup"><span data-stu-id="11736-141">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="11736-142">Códigos QR</span><span class="sxs-lookup"><span data-stu-id="11736-142">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="11736-143">Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:</span><span class="sxs-lookup"><span data-stu-id="11736-143">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="11736-144">Como fazer a implantação no dispositivo</span><span class="sxs-lookup"><span data-stu-id="11736-144">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="11736-145">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="11736-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="11736-146">Veja também</span><span class="sxs-lookup"><span data-stu-id="11736-146">See also</span></span>
* [<span data-ttu-id="11736-147">Câmera localizável</span><span class="sxs-lookup"><span data-stu-id="11736-147">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="11736-148">Captura de realidade misturada para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="11736-148">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
