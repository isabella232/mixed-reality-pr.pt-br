---
title: Streaming no Unreal
description: Saiba como transmitir seus aplicativos Unreal para o HoloLens 2, incluindo opções de linha de comando e limitações de streaming.
author: sw5813
ms.author: suwu
ms.date: 12/7/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, streaming, PC, comunicação remota do aplicativo holográfico, player de comunicação remota holográfica, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: bbae1170850ec4bbb41bc9274223d19102adddae
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580330"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="e097a-104">Streaming no Unreal</span><span class="sxs-lookup"><span data-stu-id="e097a-104">Streaming in Unreal</span></span>

<span data-ttu-id="e097a-105">O streaming de um computador para o HoloLens fornece duas vantagens principais:</span><span class="sxs-lookup"><span data-stu-id="e097a-105">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="e097a-106">Ele permite que o aplicativo de realidade misturada aproveite a capacidade computacional dos seus computadores.</span><span class="sxs-lookup"><span data-stu-id="e097a-106">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="e097a-107">Ele ajuda a acelerar o tempo de iteração do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="e097a-107">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="e097a-108">Para começar, baixe o [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) no seu dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e097a-108">To get started, you'll need to download the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="e097a-109">O Holographic Remoting Player permite o streaming direto do seu aplicativo para o player de comunicação remota no HoloLens por meio das seguintes fontes:</span><span class="sxs-lookup"><span data-stu-id="e097a-109">The Holographic Remoting Player lets your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="e097a-110">O editor do Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="e097a-110">The Unreal Engine editor</span></span>
* <span data-ttu-id="e097a-111">Um executável empacotado do Windows</span><span class="sxs-lookup"><span data-stu-id="e097a-111">A packaged Windows executable</span></span> 

<span data-ttu-id="e097a-112">Durante o streaming, você tem acesso a quase todas as mesmas funcionalidades do HoloLens que teria ao executar um aplicativo em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e097a-112">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="e097a-113">Isso inclui o [acompanhamento da articulação da mão](unreal-hand-tracking.md), se você está usando um HoloLens 2, o [mapeamento espacial](unreal-spatial-mapping.md) e as [âncoras espaciais](unreal-spatial-anchors.md), mas exclui os recursos desta [lista](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="e097a-113">This includes [hand joint tracking](unreal-hand-tracking.md) if you're on a HoloLens 2, [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="e097a-114">A qualidade de streaming é altamente dependente da força da rede Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="e097a-114">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="e097a-115">Todos os recursos são habilitados automaticamente para o player de comunicação remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="e097a-115">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="e097a-116">Se você encontrar uma funcionalidade que exija permissão de usuário (por exemplo, acompanhamento de olho) para funcionar por streaming, mas não durante a execução no dispositivo, verifique se você habilitou os recursos adequados nas configurações do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="e097a-116">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

### <a name="streaming-limitations"></a><span data-ttu-id="e097a-117">Limitações de streaming</span><span class="sxs-lookup"><span data-stu-id="e097a-117">Streaming limitations</span></span>

<span data-ttu-id="e097a-118">As malhas de mão, a câmera do HoloLens e o teclado do sistema não estão disponíveis por streaming.</span><span class="sxs-lookup"><span data-stu-id="e097a-118">Hand meshes, the HoloLens camera, and the system keyboard are unavailable over streaming.</span></span> <span data-ttu-id="e097a-119">Observe que a entrada de fala para aplicativos transmitidos por streaming pode ser adquirida por meio do microfone do computador em que você está fazendo streaming.</span><span class="sxs-lookup"><span data-stu-id="e097a-119">Note that speech input for streamed apps can be acquired via the microphone of the PC you are streaming from.</span></span>

#### <a name="openxr"></a><span data-ttu-id="e097a-120">OpenXR</span><span class="sxs-lookup"><span data-stu-id="e097a-120">OpenXR</span></span>

<span data-ttu-id="e097a-121">O Unreal 4.26 em execução no OpenXR é compatível com streaming para as versões 2.4.0 e posteriores do Player de Comunicação Remota Holográfica.</span><span class="sxs-lookup"><span data-stu-id="e097a-121">Unreal 4.26 running on OpenXR supports streaming to versions 2.4.0+ of the Holographic Remoting Player.</span></span> <span data-ttu-id="e097a-122">O streaming do OpenXR na versão 2.4.0 não é compatível com o mapeamento espacial e âncoras espaciais.</span><span class="sxs-lookup"><span data-stu-id="e097a-122">OpenXR streaming in 2.4.0 is missing support for spatial mapping and spatial anchors.</span></span> 

## <a name="device-support"></a><span data-ttu-id="e097a-123">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="e097a-123">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e097a-124"><strong>Origem</strong></span><span class="sxs-lookup"><span data-stu-id="e097a-124"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="e097a-125"><a href="/hololens/hololens1-hardware"><strong>HoloLens 1ª geração</strong></a></span><span class="sxs-lookup"><span data-stu-id="e097a-125"><a href="/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="e097a-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="e097a-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="e097a-127"><strong>Headsets imersivos</strong></span><span class="sxs-lookup"><span data-stu-id="e097a-127"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e097a-128">Editor do Unreal</span><span class="sxs-lookup"><span data-stu-id="e097a-128">Unreal editor</span></span></td>
        <td><span data-ttu-id="e097a-129">✔️</span><span class="sxs-lookup"><span data-stu-id="e097a-129">✔️</span></span></td>
        <td><span data-ttu-id="e097a-130">✔️</span><span class="sxs-lookup"><span data-stu-id="e097a-130">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="e097a-131">Pacote do Windows</span><span class="sxs-lookup"><span data-stu-id="e097a-131">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="e097a-132">✔️</span><span class="sxs-lookup"><span data-stu-id="e097a-132">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="e097a-133">Streaming do editor do Unreal</span><span class="sxs-lookup"><span data-stu-id="e097a-133">Streaming from the Unreal editor</span></span>

<span data-ttu-id="e097a-134">Como desenvolvedor, você descobrirá que o streaming por meio do editor do Unreal para o dispositivo HoloLens oferece benefícios significativos durante o teste. Ou seja, você não precisa mais esperar que o aplicativo seja compilado e implantado para experimentar as atualizações.</span><span class="sxs-lookup"><span data-stu-id="e097a-134">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides significant benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="e097a-135">Encontre instruções detalhadas do [streaming por meio do editor do Unreal](tutorials/unreal-uxt-ch6.md#device-only-streaming) em nossa série de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="e097a-135">You can find detailed instructions for [streaming from the Unreal editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) in our tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="e097a-136">Streaming de um executável empacotado do Windows</span><span class="sxs-lookup"><span data-stu-id="e097a-136">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="e097a-137">No Unreal 4.25.1 em diante, você pode transmitir seu aplicativo para um dispositivo HoloLens 2 por meio de um executável empacotado do Windows:</span><span class="sxs-lookup"><span data-stu-id="e097a-137">In Unreal 4.25.1 and onwards, you can stream your app to a HoloLens 2 device from a packaged Windows executable:</span></span> 

1. <span data-ttu-id="e097a-138">Acesse **Arquivo > Projeto de Pacote > Windows** no menu do editor.</span><span class="sxs-lookup"><span data-stu-id="e097a-138">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="e097a-139">Escolha uma localização para salvar o pacote e **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="e097a-139">Choose a location to save your package and select **Select Folder**.</span></span>

2. <span data-ttu-id="e097a-140">Depois que o pacote terminar de ser compilado, abra o **Holographic Remoting Player** no HoloLens 2 e anote o endereço IP.</span><span class="sxs-lookup"><span data-stu-id="e097a-140">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="e097a-141">Deixe o **Holographic Remoting Player** aberto e use o prompt de linha de comando para:</span><span class="sxs-lookup"><span data-stu-id="e097a-141">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="e097a-142">Executar cd no diretório local em que você salvou o pacote.</span><span class="sxs-lookup"><span data-stu-id="e097a-142">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="e097a-143">Digite o seguinte comando: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span><span class="sxs-lookup"><span data-stu-id="e097a-143">Enter the following command: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span></span>

> [!NOTE]
> <span data-ttu-id="e097a-144">O nome do aplicativo nas configurações do projeto deverá ser usado automaticamente para criar o pacote do Windows.</span><span class="sxs-lookup"><span data-stu-id="e097a-144">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="e097a-145">Se ele for diferente por algum motivo, use o nome do executável do Windows no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e097a-145">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="e097a-146">Pressione ENTER e veja seu aplicativo começar a ser transmitido.</span><span class="sxs-lookup"><span data-stu-id="e097a-146">Hit enter and watch your application start streaming!</span></span>

### <a name="command-line-options"></a><span data-ttu-id="e097a-147">Opções de linha de comando</span><span class="sxs-lookup"><span data-stu-id="e097a-147">Command line options</span></span>

<span data-ttu-id="e097a-148">Outras opções de linha de comando para streaming em cada plataforma no Unreal Engine 4.26+ podem ser encontradas na tabela abaixo.</span><span class="sxs-lookup"><span data-stu-id="e097a-148">Additional command line options for streaming from each platform in Unreal Engine 4.26+ can be found in the table below.</span></span> 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a><span data-ttu-id="e097a-149">Veja também</span><span class="sxs-lookup"><span data-stu-id="e097a-149">See also</span></span>

* [<span data-ttu-id="e097a-150">Histórico de versões do Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="e097a-150">Holographic remoting version history</span></span>](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [<span data-ttu-id="e097a-151">Como escrever um aplicativo personalizado do Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="e097a-151">Writing a custom Holographic Remoting player app</span></span>](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [<span data-ttu-id="e097a-152">Como estabelecer uma conexão segura com o Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="e097a-152">Establishing a secure connection with Holographic Remoting</span></span>](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)