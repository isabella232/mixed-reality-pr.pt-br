---
title: Implantar no dispositivo no Unreal
description: Um guia para a implantação no dispositivo de não real para o HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Inreal, inreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, implantar em dispositivo, PC, documentação, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
appliesto:
- HoloLens 2
ms.openlocfilehash: 9d32dff121899d40175af813fac4f7be1acc66c3
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679115"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="e269f-104">Implantar no dispositivo no Unreal</span><span class="sxs-lookup"><span data-stu-id="e269f-104">Deploy to device in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="e269f-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e269f-105">Overview</span></span>
<span data-ttu-id="e269f-106">Há duas maneiras de implantar um aplicativo inreal no HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="e269f-106">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="e269f-107">Diretamente do editor inreal</span><span class="sxs-lookup"><span data-stu-id="e269f-107">Directly from the Unreal editor</span></span>
* <span data-ttu-id="e269f-108">Como um pacote carregado por meio do portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="e269f-108">As a package uploaded via the device portal</span></span>

<span data-ttu-id="e269f-109">As duas opções exigem que você configure seu HoloLens para usar o [portal do dispositivo](../platform-capabilities-and-apis/using-the-windows-device-portal.md) para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="e269f-109">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="e269f-110">Implantando no dispositivo do editor inreal</span><span class="sxs-lookup"><span data-stu-id="e269f-110">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="e269f-111">Clique na seta suspensa ao lado do botão **Iniciar** .</span><span class="sxs-lookup"><span data-stu-id="e269f-111">Click the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="e269f-112">Inicialmente, a opção do dispositivo HoloLens ficará esmaecida.</span><span class="sxs-lookup"><span data-stu-id="e269f-112">Initially, the HoloLens device option will be grayed out.</span></span>

![Opções de menu suspenso de inicialização](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="e269f-114">Abra o **Device Manager**.</span><span class="sxs-lookup"><span data-stu-id="e269f-114">Open the **Device Manager**.</span></span> <span data-ttu-id="e269f-115">Observe que seu HoloLens não aparecerá automaticamente na lista de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="e269f-115">Note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="e269f-116">Expanda a seção **Adicionar um dispositivo não listado** .</span><span class="sxs-lookup"><span data-stu-id="e269f-116">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="e269f-117">Selecione **HoloLens** como sua **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="e269f-117">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="e269f-118">Insira o endereço IP e as informações de porta dos dispositivos separados por dois-pontos como o identificador do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e269f-118">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="e269f-119">Por exemplo, "127.0.0.1:10080" (quando conectado via USB).</span><span class="sxs-lookup"><span data-stu-id="e269f-119">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="e269f-120">Use as credenciais de nome de usuário e senha do portal do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e269f-120">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="e269f-121">Clique em **Adicionar** e feche o Gerenciador de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="e269f-121">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="e269f-122">No caso de um erro (como endereço incorreto, nome de usuário ou senha), uma mensagem será impressa no log de saída.</span><span class="sxs-lookup"><span data-stu-id="e269f-122">In the case of an error (such as wrong address, user name or password), a message will be printed to the Output Log.</span></span>

![Adicionando um dispositivo não listado](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="e269f-124">Clique na seta suspensa ao lado do botão **Iniciar** novamente. desta vez, você verá o dispositivo HoloLens que você acabou de adicionar.</span><span class="sxs-lookup"><span data-stu-id="e269f-124">Click the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="e269f-125">Selecione o dispositivo HoloLens para compilar e implantar em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e269f-125">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="e269f-126">A criação para o dispositivo pode envolver a recompilação de sombreadores (especialmente na primeira execução) – isso pode levar algum tempo.</span><span class="sxs-lookup"><span data-stu-id="e269f-126">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="e269f-127">Não deixe que o dispositivo vá para o estado de suspensão até que o aplicativo esteja em execução (talvez você precise fazê-lo).</span><span class="sxs-lookup"><span data-stu-id="e269f-127">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="e269f-128">Caso contrário, haverá falha na compilação do sombreador!</span><span class="sxs-lookup"><span data-stu-id="e269f-128">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="e269f-129">Implantando no dispositivo por meio do portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="e269f-129">Deploying to device via device portal</span></span>

<span data-ttu-id="e269f-130">Você pode encontrar instruções detalhadas sobre como [empacotar e implantar um aplicativo](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) na última seção do introdução com séries de tutoriais não reais.</span><span class="sxs-lookup"><span data-stu-id="e269f-130">You can find detailed instructions on [packaging and deploying an app](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="e269f-131">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="e269f-131">Next Development Checkpoint</span></span>

<span data-ttu-id="e269f-132">Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento inreal, você estará no meio do estágio de implantação.</span><span class="sxs-lookup"><span data-stu-id="e269f-132">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="e269f-133">A partir daqui, você pode continuar a adicionar serviços avançados:</span><span class="sxs-lookup"><span data-stu-id="e269f-133">From here, you can proceed to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e269f-134">Serviços avançados</span><span class="sxs-lookup"><span data-stu-id="e269f-134">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="e269f-135">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#4-deploying-to-a-device) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="e269f-135">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-deploying-to-a-device) at any time.</span></span>
