---
title: Câmera de foto/vídeo do HoloLens no Unreal
description: Guia para usar a câmera de foto/vídeo do HoloLens no Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, câmera, câmera PV, MRC, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: ef557bc6492ced6bb9b3c47a8cccc897e33b76c1
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354555"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="10f2e-104">Câmera de foto/vídeo do HoloLens no Unreal</span><span class="sxs-lookup"><span data-stu-id="10f2e-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="10f2e-105">O HoloLens traz uma câmera PV (foto/vídeo) no visor que pode ser usada para a MRC (Captura de Realidade Misturada) e por um aplicativo para localizar objetos no espaço de mundo do Unreal por meio de coordenadas de pixel no quadro da câmera.</span><span class="sxs-lookup"><span data-stu-id="10f2e-105">The HoloLens has a Photo/Video (PV) Camera on the visor that can be used for both Mixed Reality Capture (MRC) and by an app to locate objects in Unreal world space from pixel coordinates in the camera frame.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10f2e-106">A câmera PV não é compatível com a Comunicação Remota Holográfica, mas é possível usar uma webcam anexada ao seu PC para simular a funcionalidade da câmera PV do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="10f2e-106">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

[!INCLUDE[](includes/tabs-pv-camera.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="10f2e-107">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="10f2e-107">Next Development Checkpoint</span></span>

<span data-ttu-id="10f2e-108">Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unreal que apresentamos, você está no meio da exploração de funcionalidades e APIs da plataforma de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="10f2e-108">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="10f2e-109">Daí, você pode prosseguir para o próximo tópico:</span><span class="sxs-lookup"><span data-stu-id="10f2e-109">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="10f2e-110">Códigos QR</span><span class="sxs-lookup"><span data-stu-id="10f2e-110">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="10f2e-111">Ou vá diretamente para a implantação de seu aplicativo em um dispositivo ou emulador:</span><span class="sxs-lookup"><span data-stu-id="10f2e-111">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="10f2e-112">Como fazer a implantação no dispositivo</span><span class="sxs-lookup"><span data-stu-id="10f2e-112">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="10f2e-113">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="10f2e-113">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="10f2e-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="10f2e-114">See also</span></span>
* [<span data-ttu-id="10f2e-115">Câmera localizável</span><span class="sxs-lookup"><span data-stu-id="10f2e-115">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="10f2e-116">Captura de realidade misturada para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="10f2e-116">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
