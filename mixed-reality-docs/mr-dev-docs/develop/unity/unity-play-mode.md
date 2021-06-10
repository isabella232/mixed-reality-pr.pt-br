---
title: Modo de reprodução do Unity
description: Saiba como usar o Modo de Reprodução no editor do Unity para visualizar as alterações do aplicativo em um dispositivo sem implantar um aplicativo.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, remoting, holographic remoting, holographic remoting player, HoloLens, mixed reality headset, windows mixed reality headset, virtual reality headset, unity play mode
ms.openlocfilehash: caa9d7bf11104ee168fda24fc369de490feb7817
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547096"
---
# <a name="unity-play-mode"></a><span data-ttu-id="86a79-104">Modo de reprodução do Unity</span><span class="sxs-lookup"><span data-stu-id="86a79-104">Unity Play Mode</span></span>

<span data-ttu-id="86a79-105">Uma maneira rápida de trabalhar em seu projeto do Unity é usar o "Modo de Reprodução", que executa seu aplicativo localmente no editor do Unity em seu computador.</span><span class="sxs-lookup"><span data-stu-id="86a79-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="86a79-106">O Unity usa a Holographic Remoting para fornecer uma maneira rápida de visualizar seu conteúdo em um dispositivo HoloLens real.</span><span class="sxs-lookup"><span data-stu-id="86a79-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="86a79-107">O Modo de Reprodução também pode ser usado com um Windows Mixed Reality headset anexado ao computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="86a79-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="86a79-108">Configuração de remoção holográfica</span><span class="sxs-lookup"><span data-stu-id="86a79-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="86a79-109">Primeiro, você precisa instalar [o aplicativo Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) do Microsoft Store em seu HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="86a79-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="86a79-110">Execute o aplicativo Holographic Remoting Player no HoloLens 2 e você verá o número de versão e o endereço IP ao que se conectar</span><span class="sxs-lookup"><span data-stu-id="86a79-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="86a79-111">Você precisará da v2.4 ou posterior para trabalhar com o plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="86a79-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Captura de tela do Holographic Remoting Player em execução no HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="86a79-113">Holographic Remoting no modo de reprodução do Editor do Unity</span><span class="sxs-lookup"><span data-stu-id="86a79-113">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="86a79-114">A criação de um projeto UWP Unity Visual Studio projeto e, em seguida, empacotá-lo e implantá-lo em um dispositivo HoloLens 2 pode levar algum tempo.</span><span class="sxs-lookup"><span data-stu-id="86a79-114">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="86a79-115">Uma solução é habilitar o recurso comunicação de comunicação remo do Editor Holográfico, que permite depurar o script C# usando o modo "Reproduzir" diretamente para um dispositivo HoloLens 2 em sua rede.</span><span class="sxs-lookup"><span data-stu-id="86a79-115">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="86a79-116">Esse cenário evita a sobrecarga de criação e implantação de um pacote UWP no dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="86a79-116">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="86a79-117">Siga as etapas em [Configuração de Remoção Holográfica](#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="86a79-117">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="86a79-118">Abra **a > do Windows XR > De remoção do Editor do OpenXR:**</span><span class="sxs-lookup"><span data-stu-id="86a79-118">Open **Windows > XR > OpenXR Editor Remoting**:</span></span>

    ![Captura de tela do painel de configurações do projeto aberto no Editor do Unity com o gerenciamento de plug-in XR realçada](images/openxr-features-img-02.png)

3. <span data-ttu-id="86a79-120">Input the IP address you get from the Holographic Remoting app e select **Enable Editor Remoting**</span><span class="sxs-lookup"><span data-stu-id="86a79-120">Input the IP address you get from the Holographic Remoting app, and select **Enable Editor Remoting**</span></span>

    ![Captura de tela do painel de configurações do projeto aberto no Editor do Unity com recursos realçadas](images/openxr-features-img-03.png)

<span data-ttu-id="86a79-122">Agora você pode clicar no botão "Reproduzir" para reproduzir seu aplicativo Unity no aplicativo de Remoção Holográfica em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="86a79-122">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="86a79-123">Você também pode [anexar Visual Studio ao Unity para](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) depurar scripts C# no modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="86a79-123">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="86a79-124">A partir da versão 0.1.0, o runtime de Comunicação Remográfica Holográfica não dá suporte a Âncoras, e as funcionalidades ARAnchorManager não funcionarão por meio da comunicação remot.</span><span class="sxs-lookup"><span data-stu-id="86a79-124">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="86a79-125">Esse recurso será lançado em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="86a79-125">This feature is coming in future releases.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="86a79-126">Modo de reprodução do Unity com a Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="86a79-126">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="86a79-127">Com o Holographic Remoting, você pode experimentar seu aplicativo no HoloLens enquanto ele é executado no editor do Unity em seu computador.</span><span class="sxs-lookup"><span data-stu-id="86a79-127">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="86a79-128">O olhar, o gesto, a voz e a entrada de mapeamento espacial são enviados do HoloLens para o computador.</span><span class="sxs-lookup"><span data-stu-id="86a79-128">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="86a79-129">Os quadros renderizados são então enviados de volta para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="86a79-129">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="86a79-130">Essa é uma ótima maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo.</span><span class="sxs-lookup"><span data-stu-id="86a79-130">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="86a79-131">A remoção holográfica requer um computador rápido e Wi-Fi conexão.</span><span class="sxs-lookup"><span data-stu-id="86a79-131">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="86a79-132">Você pode encontrar mais detalhes na [documentação do Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)</span><span class="sxs-lookup"><span data-stu-id="86a79-132">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="86a79-133">Para melhores resultados, certifique-se de que seu aplicativo define corretamente o [ponto de foco](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="86a79-133">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="86a79-134">Isso ajuda o Holographic Remoting a adaptar melhor sua cena à latência de sua conexão sem fio.</span><span class="sxs-lookup"><span data-stu-id="86a79-134">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="86a79-135">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="86a79-135">See Also</span></span>

* [<span data-ttu-id="86a79-136">Player de Comunicação Remota Holográfica</span><span class="sxs-lookup"><span data-stu-id="86a79-136">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
