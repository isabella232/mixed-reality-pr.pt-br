---
title: Como instalar o PIX para o HoloLens 2
description: Saiba como instalar o PIX para dispositivos do HoloLens 2.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, captura, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 598a6b891798be7059eae2eff578c6bbbae442f6
ms.sourcegitcommit: 9d79aaa313f003dd42d5610d458031890776ee8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/30/2020
ms.locfileid: "97822919"
---
# <a name="installing-pix-for-hololens-2"></a><span data-ttu-id="3280c-104">Como instalar o PIX para o HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3280c-104">Installing PIX for HoloLens 2</span></span>

<span data-ttu-id="3280c-105">O [PIX](https://devblogs.microsoft.com/pix) é uma ferramenta de ajuste e depuração de desempenho para aplicativos DirectX 12 no Windows.</span><span class="sxs-lookup"><span data-stu-id="3280c-105">[PIX](https://devblogs.microsoft.com/pix) is a performance tuning and debugging tool for DirectX 12 applications on Windows.</span></span> 

## <a name="setup"></a><span data-ttu-id="3280c-106">Instalação</span><span class="sxs-lookup"><span data-stu-id="3280c-106">Setup</span></span>

1. <span data-ttu-id="3280c-107">Obtenha a [versão]( https://devblogs.microsoft.com/pix/download) mais recente do PIX do seu PC host e conecte o seu HoloLens 2 ao seu PC por meio de um cabo USB.</span><span class="sxs-lookup"><span data-stu-id="3280c-107">Grab the latest PIX [release]( https://devblogs.microsoft.com/pix/download) from your host PC and connect your HoloLens 2 to your PC via a USB cable.</span></span>

2. <span data-ttu-id="3280c-108">Se o seu HoloLens 2 estiver em um [Build do Windows Insider](https://insider.windows.com) ou tiver uma configuração que interrompa o PIX,  [repisque seu dispositivo](https://docs.microsoft.com/hololens/hololens-recovery) para apagar todos os dados.</span><span class="sxs-lookup"><span data-stu-id="3280c-108">If your HoloLens 2 is on a [Windows Insider build](https://insider.windows.com) or has a configuration that breaks PIX,  [reflash your device](https://docs.microsoft.com/hololens/hololens-recovery) to erase all data.</span></span>

3. <span data-ttu-id="3280c-109">Habilitar o **modo de desenvolvedor** e o portal do **dispositivo**:</span><span class="sxs-lookup"><span data-stu-id="3280c-109">Enable **Developer Mode** and **Device Portal**:</span></span>

* <span data-ttu-id="3280c-110">Abra **as configurações** do início da realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="3280c-110">Open **Settings** from Mixed Reality Home:</span></span>

![Captura de tela do menu do HoloLens com o botão Configurações realçado](images/pix-img-01.jpg)

* <span data-ttu-id="3280c-112">Selecione **Atualizar segurança &**:</span><span class="sxs-lookup"><span data-stu-id="3280c-112">Select **Update & Security**:</span></span>

![Captura de tela da janela de configurações aberta no HoloLens com o botão de atualização e segurança realçado](images/pix-img-02.jpg)

* <span data-ttu-id="3280c-114">Selecione **para desenvolvedores**:</span><span class="sxs-lookup"><span data-stu-id="3280c-114">Select **For Developers**:</span></span>

![Captura de tela da janela segurança e atualizações abrir com o botão desenvolvedores realçado](images/pix-img-03.jpg)

* <span data-ttu-id="3280c-116">Ativar o **uso de recursos de desenvolvedor** e **habilitar o portal do dispositivo**</span><span class="sxs-lookup"><span data-stu-id="3280c-116">Turn on **Use Developer Features** and **Enable Device Portal**</span></span>

![Captura de tela da janela para desenvolvedores abrir em configurações com o botão habilitar portal do dispositivo realçado](images/pix-img-04.jpg)

![Captura de tela da janela para desenvolvedores abrir em configurações com a opção usar desenvolver recursos alternar realçada](images/pix-img-05.jpg)

* <span data-ttu-id="3280c-119">Com o dispositivo ainda conectado, ativo e com o usuário conectado, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3280c-119">With the device still connected, awake, and with the user logged in, launch Visual Studio.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3280c-120">Verifique se o dispositivo não está no modo de espera ou em suspensão.</span><span class="sxs-lookup"><span data-stu-id="3280c-120">Make sure your device isn't in standby mode or asleep.</span></span> <span data-ttu-id="3280c-121">Se você estiver tendo problemas com essa etapa, consulte as [instruções do portal de dispositivo do Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span><span class="sxs-lookup"><span data-stu-id="3280c-121">If you're having trouble with this step, refer to the [Windows Device Portal instructions](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span></span>

## <a name="preparing-for-deployment"></a><span data-ttu-id="3280c-122">Preparando para implantação</span><span class="sxs-lookup"><span data-stu-id="3280c-122">Preparing for deployment</span></span>

1. <span data-ttu-id="3280c-123">No Visual Studio, defina **ARM64** como a plataforma e o **dispositivo** como o dispositivo:</span><span class="sxs-lookup"><span data-stu-id="3280c-123">In Visual Studio, set **ARM64** as the platform and **Device** as the device:</span></span>

![Captura de tela da solução Visual estúdios com as configurações de plataforma e dispositivo realçadas](images/pix-img-06.png)

2. <span data-ttu-id="3280c-125">Quando o Visual Studio solicitar um **PIN** do dispositivo:</span><span class="sxs-lookup"><span data-stu-id="3280c-125">When Visual Studio prompts you for a **PIN** from the device:</span></span>

![Captura de tela do pop-up do Visual Studio solicitando PIN](images/pix-img-07.png)

* <span data-ttu-id="3280c-127">Selecione **as configurações** do Shell</span><span class="sxs-lookup"><span data-stu-id="3280c-127">Select **Settings** from Shell</span></span>
* <span data-ttu-id="3280c-128">Selecione **Atualizar segurança &**</span><span class="sxs-lookup"><span data-stu-id="3280c-128">Select **Update & Security**</span></span>
* <span data-ttu-id="3280c-129">Selecione **para desenvolvedores** e pressione o par em **descoberta de dispositivo**</span><span class="sxs-lookup"><span data-stu-id="3280c-129">Select **For Developers** and press Pair under **Device Discovery**</span></span> 

![Captura de tela da janela para desenvolvedores abrir em configurações com descoberta de dispositivo realçada](images/pix-img-08.jpg)

![Captura de tela do pop-up do dispositivo pago com o código de registro realçado](images/pix-img-09.jpg)

* <span data-ttu-id="3280c-132">Insira o número de PIN gerado no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3280c-132">Enter the generated PIN number in Visual Studio</span></span>

3. <span data-ttu-id="3280c-133">O Visual Studio implantará o aplicativo no HoloLens 2 conectado, o que pode levar alguns minutos, dependendo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3280c-133">Visual Studio will deploy the app to the connected HoloLens 2, which may take a few minutes depending on the app.</span></span>

## <a name="launching-pix"></a><span data-ttu-id="3280c-134">Iniciando o PIX</span><span class="sxs-lookup"><span data-stu-id="3280c-134">Launching PIX</span></span>

<span data-ttu-id="3280c-135">Primeiro, use o portal do dispositivo para verificar se o aplicativo não está em execução no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3280c-135">First, use Device Portal to verify the app isn't running on the HoloLens 2.</span></span> <span data-ttu-id="3280c-136">Em seguida, inicie o PIX, conecte-se ao seu dispositivo e selecione **início**:</span><span class="sxs-lookup"><span data-stu-id="3280c-136">Then, launch PIX, connect to your device, and select **Home**:</span></span>

![Captura de tela da página inicial do aplicativo PIX](images/pix-img-10.png)

* <span data-ttu-id="3280c-138">Selecione **conectar** no menu do lado esquerdo:</span><span class="sxs-lookup"><span data-stu-id="3280c-138">Select **Connect** from the left-side menu:</span></span>

![Captura de tela do menu do lado esquerdo do aplicativo PIX com o botão conectar realçado](images/pix-img-11.png)

2. <span data-ttu-id="3280c-140">Na guia **computador** , selecione **Adicionar** e insira as seguintes credenciais:</span><span class="sxs-lookup"><span data-stu-id="3280c-140">From the **Computer** tab, select **Add**, and enter the following credentials:</span></span>
    * <span data-ttu-id="3280c-141">Alias: até o critério do usuário</span><span class="sxs-lookup"><span data-stu-id="3280c-141">Alias: Up to user’s discretion</span></span>
    * <span data-ttu-id="3280c-142">Nome do host ou endereço IP: 127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="3280c-142">Host Name or IP Address: 127.0.0.1</span></span>

3. <span data-ttu-id="3280c-143">Selecione **conectar** no canto inferior direito da guia **computador** :</span><span class="sxs-lookup"><span data-stu-id="3280c-143">Select **Connect** in the lower right of the **Computer** tab:</span></span>

![Captura de tela da janela de conexão de aplicativo do PIX com alias, nome do host, endereço IP e botão Adicionar realçado](images/pix-img-12.png)

> [!NOTE]
> <span data-ttu-id="3280c-145">A primeira conexão é sempre mais lenta porque os binários estão sendo copiados.</span><span class="sxs-lookup"><span data-stu-id="3280c-145">The first connection is always slower because binaries are being copied.</span></span>

4. <span data-ttu-id="3280c-146">Quando o PIX tiver se conectado ao HoloLens 2, localize seu aplicativo na seção **selecionar processo de destino** na guia Iniciar UWP e selecione **Iniciar**:</span><span class="sxs-lookup"><span data-stu-id="3280c-146">When PIX has connected to the HoloLens 2, find your app in the **Select Target Process** section in the Launch UWP tab, and select **Launch**:</span></span>

![Captura de tela do aplicativo PIX com a janela Selecionar processo de destino e o botão iniciar realçado](images/pix-img-13.png)

## <a name="gpu-captured"></a><span data-ttu-id="3280c-148">GPU capturada</span><span class="sxs-lookup"><span data-stu-id="3280c-148">GPU captured</span></span>

1. <span data-ttu-id="3280c-149">Inicie a captura de GPU clicando em **foto** na seção de **captura de GPU** :</span><span class="sxs-lookup"><span data-stu-id="3280c-149">Start the GPU capture by clicking **Photo** in the **GPU Capture** section:</span></span>

![Captura de tela do aplicativo PIX com o painel de conexão do PC aberto com a captura de GPU realçada](images/pix-img-14.png)

2. <span data-ttu-id="3280c-151">Abra a captura para análise clicando na captura de tela gerada no painel de **captura de GPU** :</span><span class="sxs-lookup"><span data-stu-id="3280c-151">Open the capture for analysis by clicking on the generated screenshot in the **GPU Capture** panel:</span></span>

![Captura de tela do aplicativo PIX com a seção de captura de GPU aberta com o painel de captura de GPU realçado](images/pix-img-15.png)

3. <span data-ttu-id="3280c-153">Pressione **Iniciar** para iniciar a análise:</span><span class="sxs-lookup"><span data-stu-id="3280c-153">Press **Start** to begin the analysis:</span></span>

![Captura de tela do aplicativo PIX o botão iniciar realçado](images/pix-img-16.png)

> [!IMPORTANT]
> <span data-ttu-id="3280c-155">Se você coletar dados de tempo depois de fazer uma captura de GPU, será necessário reinicializar o headset.</span><span class="sxs-lookup"><span data-stu-id="3280c-155">If you collect timing data after taking a GPU capture, you'll be required to reboot the headset.</span></span> <span data-ttu-id="3280c-156">Este é um reinício único do dispositivo e é necessário para a coleta de dados de tempo.</span><span class="sxs-lookup"><span data-stu-id="3280c-156">This is a one-time restart of the device and is required for timing data collection.</span></span>

<span data-ttu-id="3280c-157">O PIX agora está pronto para uso!</span><span class="sxs-lookup"><span data-stu-id="3280c-157">PIX is now ready for use!</span></span>

## <a name="see-also"></a><span data-ttu-id="3280c-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3280c-158">See also</span></span>
* [<span data-ttu-id="3280c-159">Home Page do PIX</span><span class="sxs-lookup"><span data-stu-id="3280c-159">PIX homepage</span></span>](https://devblogs.microsoft.com/pix)