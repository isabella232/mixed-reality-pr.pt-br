---
title: Modo de reprodução do Unity
description: Saiba como usar o Modo de Reprodução no editor do Unity para visualizar as alterações do aplicativo em um dispositivo sem implantar um aplicativo.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, remoting, holographic remoting, holographic remoting player, HoloLens, mixed reality headset, windows mixed reality headset, virtual reality headset, unity play mode
ms.openlocfilehash: b998233fda34beee0c98795a1efa2c86a53541ba
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392283"
---
# <a name="unity-play-mode"></a><span data-ttu-id="0f752-104">Modo de reprodução do Unity</span><span class="sxs-lookup"><span data-stu-id="0f752-104">Unity Play Mode</span></span>

<span data-ttu-id="0f752-105">Uma maneira rápida de trabalhar em seu projeto do Unity é usar o "Modo de Reprodução", que executa seu aplicativo localmente no editor do Unity em seu computador.</span><span class="sxs-lookup"><span data-stu-id="0f752-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="0f752-106">O Unity usa a Holographic Remoting para fornecer uma maneira rápida de visualizar seu conteúdo em um dispositivo HoloLens real.</span><span class="sxs-lookup"><span data-stu-id="0f752-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="0f752-107">O Modo de Reprodução também pode ser usado com um Windows Mixed Reality headset anexado ao computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="0f752-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="0f752-108">Configuração de remoção holográfica</span><span class="sxs-lookup"><span data-stu-id="0f752-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="0f752-109">Primeiro, você precisa instalar [o aplicativo Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) do Microsoft Store em seu HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="0f752-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="0f752-110">Execute o aplicativo Holographic Remoting Player no HoloLens 2 e você verá o número de versão e o endereço IP ao que se conectar</span><span class="sxs-lookup"><span data-stu-id="0f752-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="0f752-111">Você precisará da v2.4 ou posterior para trabalhar com o plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="0f752-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Captura de tela do Holographic Remoting Player em execução no HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="0f752-113">Modo de reprodução do Unity com a Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="0f752-113">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="0f752-114">Com o Holographic Remoting, você pode experimentar seu aplicativo no HoloLens enquanto ele é executado no editor do Unity em seu computador.</span><span class="sxs-lookup"><span data-stu-id="0f752-114">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="0f752-115">O olhar, o gesto, a voz e a entrada de mapeamento espacial são enviados do HoloLens para o computador.</span><span class="sxs-lookup"><span data-stu-id="0f752-115">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="0f752-116">Os quadros renderizados são então enviados de volta para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0f752-116">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="0f752-117">Essa é uma ótima maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo.</span><span class="sxs-lookup"><span data-stu-id="0f752-117">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="0f752-118">A remoção holográfica requer um computador rápido e Wi-Fi conexão.</span><span class="sxs-lookup"><span data-stu-id="0f752-118">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="0f752-119">Você pode encontrar mais detalhes na [documentação do Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)</span><span class="sxs-lookup"><span data-stu-id="0f752-119">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="0f752-120">Para melhores resultados, certifique-se de que seu aplicativo define corretamente o [ponto de foco](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="0f752-120">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="0f752-121">Isso ajuda o Holographic Remoting a adaptar melhor sua cena à latência de sua conexão sem fio.</span><span class="sxs-lookup"><span data-stu-id="0f752-121">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f752-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0f752-122">See Also</span></span>

* [<span data-ttu-id="0f752-123">Player de Comunicação Remota Holográfica</span><span class="sxs-lookup"><span data-stu-id="0f752-123">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
