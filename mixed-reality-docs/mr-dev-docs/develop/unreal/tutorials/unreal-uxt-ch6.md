---
title: 6. Como empacotar e implantar no dispositivo ou emulador
description: Parte 6 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 6e1f19810a97480ab324846e8d674bb4edf5da52
ms.sourcegitcommit: 8e91ff47ef70e80a41137f80aa1093e711d27bf7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957806"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="07422-104">6. Como empacotar e implantar no dispositivo ou emulador</span><span class="sxs-lookup"><span data-stu-id="07422-104">6. Packaging & deploying to device or emulator</span></span>

## <a name="overview"></a><span data-ttu-id="07422-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="07422-105">Overview</span></span>

<span data-ttu-id="07422-106">No tutorial anterior, você adicionou um botão simples que redefine a peça de xadrez para a posição original dela.</span><span class="sxs-lookup"><span data-stu-id="07422-106">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="07422-107">Nesta seção final, você fará com que o aplicativo esteja pronto para ser executado em um HoloLens 2 ou em um emulador.</span><span class="sxs-lookup"><span data-stu-id="07422-107">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="07422-108">Se você tem um HoloLens 2, pode transmitir do seu computador ou empacotar o aplicativo para ser executado diretamente no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="07422-108">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="07422-109">Se você não tem um dispositivo, você está empacotando o aplicativo para ser executado no emulador.</span><span class="sxs-lookup"><span data-stu-id="07422-109">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="07422-110">Ao final desta seção, você terá um aplicativo de realidade misturada implantado que você poderá jogar, completo, com interações e interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="07422-110">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="07422-111">Objetivos</span><span class="sxs-lookup"><span data-stu-id="07422-111">Objectives</span></span>

* <span data-ttu-id="07422-112">[Somente para dispositivo] Transmitir para o HoloLens 2 por meio de comunicação remota holográfica do aplicativo</span><span class="sxs-lookup"><span data-stu-id="07422-112">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="07422-113">Empacotar e implantar seu aplicativo em um emulador ou dispositivo do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="07422-113">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="07422-114">[Somente para dispositivo] Streaming</span><span class="sxs-lookup"><span data-stu-id="07422-114">[Device Only] Streaming</span></span>
<span data-ttu-id="07422-115">A [comunicação remota holográfica](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting), nesse caso, significa transmitir dados de um computador ou dispositivo UWP autônomo para o HoloLens 2, sem mudar de canal.</span><span class="sxs-lookup"><span data-stu-id="07422-115">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) in this case means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="07422-116">Isso funciona com um aplicativo host de comunicação remota que recebe um fluxo de dados de entrada de um HoloLens, renderiza o conteúdo em uma exibição imersiva virtual e transmite quadros de conteúdo de volta para o HoloLens por Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="07422-116">The way this works is a remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="07422-117">O streaming permite que você adicione exibições imersivas remotas a software de PC desktop existente e tenha acesso a mais recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="07422-117">Streaming allows you to add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="07422-118">Se você estiver seguindo por esse caminho com o aplicativo de xadrez, precisará fazer algumas coisas:</span><span class="sxs-lookup"><span data-stu-id="07422-118">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="07422-119">Instale o **Player de Comunicação Remota Holográfica** por meio da Microsoft Store no seu HoloLens 2 e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07422-119">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="07422-120">Anote o endereço IP exibido no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07422-120">Note your IP address displayed in the app.</span></span>

2.  <span data-ttu-id="07422-121">De volta no editor do Unreal, acesse **Editar > Configurações do Projeto** e marque **Habilitar a Comunicação Remota** na seção **Comunicação Remota Holográfica**.</span><span class="sxs-lookup"><span data-stu-id="07422-121">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="07422-122">Reinicie o editor e insira o endereço IP do dispositivo (conforme exibido no aplicativo Player de Comunicação Remota do Holographic) e clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="07422-122">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="07422-123">Quando estiver conectado, clique na seta suspensa à direita do botão **Jogar** e selecione a **Visualização de VR**.</span><span class="sxs-lookup"><span data-stu-id="07422-123">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="07422-124">Isso executará o aplicativo na janela de Visualização de VR, que é transmitida para o headset do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="07422-124">This will run the app in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="07422-125">Empacotar e implantar o aplicativo por meio do portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="07422-125">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="07422-126">Se esta for a primeira vez que você empacota um aplicativo Unreal para o HoloLens, precisará baixar os arquivos de suporte do Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="07422-126">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="07422-127">Vá para **Preferências do Editor > Geral > Código-Fonte > Editor de Código-Fonte** e verifique se o Visual Studio 2019 está selecionado.</span><span class="sxs-lookup"><span data-stu-id="07422-127">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="07422-128">Vá para a guia **Biblioteca** no Inicializador da Epic Games, selecione a seta suspensa ao lado de **Iniciar** > e clique em **Opções**.</span><span class="sxs-lookup"><span data-stu-id="07422-128">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="07422-129">Em **Plataformas de Destino**, selecione **HoloLens 2** e clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="07422-129">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="07422-130">![Alterar a plataforma de destino nas configurações do projeto](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="07422-130">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="07422-131">Acesse **Editar > Configurações do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="07422-131">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="07422-132">Em **Projeto > Descrição > Sobre > Nome do Projeto**, adicione um nome de projeto.</span><span class="sxs-lookup"><span data-stu-id="07422-132">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="07422-133">Adicione **CN=NomeDaSuaEmpresa** em **Projeto > Descrição > Editor > Nome Diferenciado da Empresa**.</span><span class="sxs-lookup"><span data-stu-id="07422-133">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07422-134">Se você deixar um desses campos em branco, isso resultará em um erro quando você tentar e gerar um novo certificado na etapa 3.</span><span class="sxs-lookup"><span data-stu-id="07422-134">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07422-135">O nome do editor precisa estar no [Formato de Nomes Diferenciados LADPv3](https://www.ietf.org/rfc/rfc2253.txt).</span><span class="sxs-lookup"><span data-stu-id="07422-135">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="07422-136">Um nome malformado do editor gera o erro "Chave de assinatura não encontrada.</span><span class="sxs-lookup"><span data-stu-id="07422-136">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="07422-137">Não foi possível assinar o aplicativo digitalmente."</span><span class="sxs-lookup"><span data-stu-id="07422-137">The app could not be digitally signed."</span></span> <span data-ttu-id="07422-138">durante o empacotamento.</span><span class="sxs-lookup"><span data-stu-id="07422-138">error upon packaging.</span></span>

![Configurações do projeto – descrição](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="07422-140">Habilite **Compilar para Emulação no HoloLens** e/ou **Compilar para Dispositivo do HoloLens** em **Plataformas > HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="07422-140">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="07422-141">Clique em **Gerar novo** na seção **Empacotamento** (ao lado de **Certificado de Autenticação**).</span><span class="sxs-lookup"><span data-stu-id="07422-141">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07422-142">Se você está usando um certificado que já foi gerado, o nome do editor do certificado precisa ser igual ao nome do editor do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07422-142">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="07422-143">Caso contrário, isso gera o erro "Chave de assinatura não encontrada.</span><span class="sxs-lookup"><span data-stu-id="07422-143">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="07422-144">Não foi possível assinar o aplicativo digitalmente."</span><span class="sxs-lookup"><span data-stu-id="07422-144">The app could not be digitally signed."</span></span> <span data-ttu-id="07422-145">erro.</span><span class="sxs-lookup"><span data-stu-id="07422-145">error.</span></span>

![Configurações do projeto – Plataformas – HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="07422-147">Clique em **Nenhum** para fins de teste quando precisar criar uma senha da chave privada.</span><span class="sxs-lookup"><span data-stu-id="07422-147">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![Como gerar um novo certificado](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="07422-149">Acesse **Arquivo > Empacotar Projeto** e selecione **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="07422-149">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="07422-150">Crie uma pasta para salvar o pacote e clique em **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="07422-150">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="07422-151">Depois que o aplicativo tiver sido empacotado, abra o [Portal de Dispositivos do Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal), acesse **Exibições > Aplicativos** e localize a seção **Implantar aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="07422-151">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="07422-152">Clique em **Procurar...** , encontre o arquivo **ChessApp.appxbundle** e clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="07422-152">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="07422-153">Se esta é a primeira vez que você está instalando o aplicativo em seu dispositivo, marque a caixa ao lado de **Permitir que eu selecione pacotes de estrutura**.</span><span class="sxs-lookup"><span data-stu-id="07422-153">Check the box next to **Allow me to select framework packages** if this is the first time you're installing the app on your device.</span></span>
    * <span data-ttu-id="07422-154">Na próxima caixa de diálogo, inclua os arquivos **VCLibs** e **appx** apropriados (arm64 para dispositivo, x64 para emulador).</span><span class="sxs-lookup"><span data-stu-id="07422-154">In the next dialogue, include the appropriate **VCLibs** and **appx** files (arm64 for device, x64 for emulator).</span></span> <span data-ttu-id="07422-155">Você pode encontrá-los em **HoloLens**, dentro da pasta em que você salvou o pacote.</span><span class="sxs-lookup"><span data-stu-id="07422-155">You can find these under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="07422-156">Clique em **Instalar**</span><span class="sxs-lookup"><span data-stu-id="07422-156">Click **Install**</span></span>
    * <span data-ttu-id="07422-157">Agora você pode acessar **Todos os Aplicativos** e tocar no aplicativo recém-instalado para executá-lo ou pode iniciar o aplicativo diretamente do **Portal de Dispositivos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="07422-157">You can now go to **All Apps** and tap the newly installed app to run it, or you can start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="07422-158">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="07422-158">Congratulations!</span></span> <span data-ttu-id="07422-159">Seu aplicativo de realidade misturada do HoloLens está concluído e pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="07422-159">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="07422-160">No entanto, esse não é o fim da jornada.</span><span class="sxs-lookup"><span data-stu-id="07422-160">However, this isn't the end of the road.</span></span> <span data-ttu-id="07422-161">O MRTK tem muitos recursos autônomos que você pode adicionar aos seus projetos, incluindo entrada por foco e voz, mapeamento espacial e até mesmo códigos QR.</span><span class="sxs-lookup"><span data-stu-id="07422-161">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="07422-162">Mais informações sobre esses recursos podem ser encontradas na [Visão geral do desenvolvimento com o Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span><span class="sxs-lookup"><span data-stu-id="07422-162">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="07422-163">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="07422-163">Next Development Checkpoint</span></span>

<span data-ttu-id="07422-164">Se você está seguindo o percurso de pontos de verificação de desenvolvimento do Unreal, está no meio da exploração dos principais blocos de construção do MRTK.</span><span class="sxs-lookup"><span data-stu-id="07422-164">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="07422-165">A partir daí, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="07422-165">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07422-166">Entrada por foco</span><span class="sxs-lookup"><span data-stu-id="07422-166">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="07422-167">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="07422-167">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07422-168">Câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="07422-168">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="07422-169">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](../unreal-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="07422-169">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
