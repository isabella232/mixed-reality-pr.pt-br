---
title: Entrada olhar em não real
description: Tutorial sobre como configurar a entrada de olhar para o HoloLens e o mecanismo inreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realidade mista do Windows, hologramas, HoloLens 2, controle de olho, entrada de olhar, exibição montada de cabeçalho, mecanismo inreal, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 2ea55e3c53275f6150ca7f2def10d71634119e2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679045"
---
# <a name="gaze-input"></a><span data-ttu-id="9be39-104">Entrada olhar</span><span class="sxs-lookup"><span data-stu-id="9be39-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="9be39-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="9be39-105">Overview</span></span>

<span data-ttu-id="9be39-106">O [plug-in do Windows Mixed Reality](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) não fornece funções internas para entrada olhar, mas o HoloLens 2 dá suporte ao acompanhamento de olho.</span><span class="sxs-lookup"><span data-stu-id="9be39-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="9be39-107">Os recursos de acompanhamento reais são fornecidos por APIs de exibição e acompanhamento de cabeça e de **controle de olhos** **desmontadas** e incluem:</span><span class="sxs-lookup"><span data-stu-id="9be39-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="9be39-108">Informações do dispositivo</span><span class="sxs-lookup"><span data-stu-id="9be39-108">Device information</span></span>
- <span data-ttu-id="9be39-109">Sensores de acompanhamento</span><span class="sxs-lookup"><span data-stu-id="9be39-109">Tracking sensors</span></span>
- <span data-ttu-id="9be39-110">Orientação e posição</span><span class="sxs-lookup"><span data-stu-id="9be39-110">Orientation and position</span></span>
- <span data-ttu-id="9be39-111">Painéis de recorte</span><span class="sxs-lookup"><span data-stu-id="9be39-111">Clipping panes</span></span>
- <span data-ttu-id="9be39-112">Informações de rastreamento e dados do olhar</span><span class="sxs-lookup"><span data-stu-id="9be39-112">Gaze data and tracking information</span></span>

<span data-ttu-id="9be39-113">Você pode encontrar a lista completa de recursos na documentação de exibição e [controle de olho](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) do [rumo](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) .</span><span class="sxs-lookup"><span data-stu-id="9be39-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="9be39-114">Além das APIs inreais, confira a documentação sobre a [interação baseada em olhar](../../design/eye-gaze-interaction.md) para o hololens 2 e leia como o [controle de olhos no hololens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) funciona.</span><span class="sxs-lookup"><span data-stu-id="9be39-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](../../design/eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9be39-115">Só há suporte para acompanhamento de olho no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9be39-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="9be39-116">Habilitando o acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="9be39-116">Enabling eye tracking</span></span>
<span data-ttu-id="9be39-117">A entrada olhar precisa ser habilitada nas configurações do projeto do HoloLens antes que você possa usar qualquer uma das APIs inreais.</span><span class="sxs-lookup"><span data-stu-id="9be39-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="9be39-118">Quando o aplicativo for iniciado, você verá um prompt de consentimento mostrado na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="9be39-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="9be39-119">Selecione **Sim** para definir a permissão e obter acesso à entrada olhar.</span><span class="sxs-lookup"><span data-stu-id="9be39-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="9be39-120">Se você precisar alterar essa configuração a qualquer momento, ela poderá ser encontrada no aplicativo **configurações** .</span><span class="sxs-lookup"><span data-stu-id="9be39-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![Permissões de entrada de olho](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="9be39-122">O controle de olhos do HoloLens em tempo inreal tem apenas um único olhar Ray para ambos os olhos, em vez dos dois raios necessários para o acompanhamento do estereoscópico, o que não é suportado.</span><span class="sxs-lookup"><span data-stu-id="9be39-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="9be39-123">Essa é a configuração que você precisará para começar a adicionar a entrada olhar aos seus aplicativos do HoloLens 2 em um não real.</span><span class="sxs-lookup"><span data-stu-id="9be39-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="9be39-124">Mais informações sobre a entrada do olhar e como isso afeta os usuários em realidade misturada podem ser encontradas nos links abaixo.</span><span class="sxs-lookup"><span data-stu-id="9be39-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="9be39-125">Lembre-se de pensar nisso ao criar suas experiências interativas.</span><span class="sxs-lookup"><span data-stu-id="9be39-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="9be39-126">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="9be39-126">Next Development Checkpoint</span></span>

<span data-ttu-id="9be39-127">Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unreal, você está no meio da exploração dos principais blocos de construção do MRTK.</span><span class="sxs-lookup"><span data-stu-id="9be39-127">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="9be39-128">De lá, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="9be39-128">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="9be39-129">Acompanhamento da mão</span><span class="sxs-lookup"><span data-stu-id="9be39-129">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="9be39-130">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="9be39-130">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9be39-131">Câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="9be39-131">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="9be39-132">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="9be39-132">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="9be39-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="9be39-133">See also</span></span>
* [<span data-ttu-id="9be39-134">Calibragem</span><span class="sxs-lookup"><span data-stu-id="9be39-134">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="9be39-135">Conforto</span><span class="sxs-lookup"><span data-stu-id="9be39-135">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="9be39-136">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="9be39-136">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="9be39-137">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="9be39-137">Voice input</span></span>](../../out-of-scope/voice-design.md)
