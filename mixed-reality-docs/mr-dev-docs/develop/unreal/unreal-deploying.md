---
title: Implantar no dispositivo no Unreal
description: Um guia para a implantação no dispositivo de não real para o HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: Inreal, inreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, implantar em dispositivo, PC, documentação, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
appliesto:
- HoloLens 2
ms.openlocfilehash: 390bd1a9f1bc643efb1a342421e8c96574e74334
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925907"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="b960a-104">Implantar no dispositivo no Unreal</span><span class="sxs-lookup"><span data-stu-id="b960a-104">Deploy to device in Unreal</span></span>

<span data-ttu-id="b960a-105">Há duas maneiras de implantar um aplicativo inreal no HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="b960a-105">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="b960a-106">Diretamente do editor inreal</span><span class="sxs-lookup"><span data-stu-id="b960a-106">Directly from the Unreal editor</span></span>
* <span data-ttu-id="b960a-107">Como um pacote carregado por meio do portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="b960a-107">As a package uploaded via the device portal</span></span>

<span data-ttu-id="b960a-108">As duas opções exigem que você configure seu HoloLens para usar o [portal do dispositivo](../platform-capabilities-and-apis/using-the-windows-device-portal.md) para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="b960a-108">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="b960a-109">Implantando no dispositivo do editor inreal</span><span class="sxs-lookup"><span data-stu-id="b960a-109">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="b960a-110">Selecione a seta suspensa ao lado do botão **Iniciar** .</span><span class="sxs-lookup"><span data-stu-id="b960a-110">Select the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="b960a-111">Inicialmente, a opção do dispositivo HoloLens ficará esmaecida.</span><span class="sxs-lookup"><span data-stu-id="b960a-111">Initially, the HoloLens device option will be grayed out.</span></span>

![Opções de menu suspenso de inicialização](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="b960a-113">Abra o **Device Manager** e observe que o seu HoloLens não aparecerá automaticamente na lista de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b960a-113">Open the **Device Manager** and note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="b960a-114">Expanda a seção **Adicionar um dispositivo não listado** .</span><span class="sxs-lookup"><span data-stu-id="b960a-114">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="b960a-115">Selecione **HoloLens** como sua **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="b960a-115">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="b960a-116">Insira o endereço IP e as informações de porta dos dispositivos separados por dois-pontos como o identificador do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b960a-116">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="b960a-117">Por exemplo, "127.0.0.1:10080" (quando conectado via USB).</span><span class="sxs-lookup"><span data-stu-id="b960a-117">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="b960a-118">Use as credenciais de nome de usuário e senha do portal do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b960a-118">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="b960a-119">Clique em **Adicionar** e feche o Gerenciador de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b960a-119">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="b960a-120">Se houver um erro, como um endereço incorreto ou credenciais de usuário, uma mensagem será impressa no log de saída.</span><span class="sxs-lookup"><span data-stu-id="b960a-120">If there's an error, such as wrong address or user credentials, a message will print to the Output Log.</span></span>

![Adicionando um dispositivo não listado](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="b960a-122">Selecione a seta suspensa ao lado do botão **Iniciar** novamente. desta vez, você verá o dispositivo HoloLens que você acabou de adicionar.</span><span class="sxs-lookup"><span data-stu-id="b960a-122">Select the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="b960a-123">Selecione o dispositivo HoloLens para compilar e implantar em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b960a-123">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="b960a-124">A criação para o dispositivo pode envolver a recompilação de sombreadores (especialmente na primeira execução) – isso pode levar algum tempo.</span><span class="sxs-lookup"><span data-stu-id="b960a-124">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="b960a-125">Não deixe que o dispositivo vá para o estado de suspensão até que o aplicativo esteja em execução (talvez você precise fazê-lo).</span><span class="sxs-lookup"><span data-stu-id="b960a-125">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="b960a-126">Caso contrário, haverá falha na compilação do sombreador!</span><span class="sxs-lookup"><span data-stu-id="b960a-126">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="b960a-127">Implantando no dispositivo por meio do portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="b960a-127">Deploying to device via device portal</span></span>

<span data-ttu-id="b960a-128">Você pode encontrar instruções detalhadas sobre como empacotar e implantar um aplicativo na [série de tutoriais não reais](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span><span class="sxs-lookup"><span data-stu-id="b960a-128">You can find detailed instructions on packaging and deploying an app in the [Unreal tutorial series](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b960a-129">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="b960a-129">Next Development Checkpoint</span></span>

<span data-ttu-id="b960a-130">Se você estiver seguindo a jornada de desenvolvimento inreal que apresentamos, você está no meio do estágio de implantação.</span><span class="sxs-lookup"><span data-stu-id="b960a-130">If you're following the Unreal development journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="b960a-131">A partir daqui, você pode continuar a adicionar serviços avançados:</span><span class="sxs-lookup"><span data-stu-id="b960a-131">From here, you can continue to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b960a-132">Serviços avançados</span><span class="sxs-lookup"><span data-stu-id="b960a-132">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="b960a-133">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="b960a-133">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) at any time.</span></span>
