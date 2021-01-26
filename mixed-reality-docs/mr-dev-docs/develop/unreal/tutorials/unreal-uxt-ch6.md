---
title: 6. Como empacotar e implantar no dispositivo ou emulador
description: Parte 6 de 6 de uma série de tutoriais para criação de um aplicativo de xadrez usando o Unreal Engine 4 e o plug-in Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 7b706cf2a8685954ed916c825c3617ade190f1e0
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583654"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="66d34-104">6. Como empacotar e implantar no dispositivo ou emulador</span><span class="sxs-lookup"><span data-stu-id="66d34-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="66d34-105">No tutorial anterior, você adicionou um botão simples que redefine a peça de xadrez para a posição original dela.</span><span class="sxs-lookup"><span data-stu-id="66d34-105">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="66d34-106">Nesta seção final, você fará com que o aplicativo esteja pronto para ser executado em um HoloLens 2 ou em um emulador.</span><span class="sxs-lookup"><span data-stu-id="66d34-106">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="66d34-107">Se você tem um HoloLens 2, pode transmitir do seu computador ou empacotar o aplicativo para ser executado diretamente no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="66d34-107">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="66d34-108">Se você não tem um dispositivo, você está empacotando o aplicativo para ser executado no emulador.</span><span class="sxs-lookup"><span data-stu-id="66d34-108">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="66d34-109">Ao final desta seção, você terá um aplicativo de realidade misturada implantado que você poderá jogar, completo, com interações e interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="66d34-109">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="66d34-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="66d34-110">Objectives</span></span>

* <span data-ttu-id="66d34-111">[Somente para dispositivo] Transmitir para o HoloLens 2 por meio de comunicação remota holográfica do aplicativo</span><span class="sxs-lookup"><span data-stu-id="66d34-111">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="66d34-112">Empacotar e implantar seu aplicativo em um emulador ou dispositivo do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="66d34-112">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="66d34-113">[Somente para dispositivo] Streaming</span><span class="sxs-lookup"><span data-stu-id="66d34-113">[Device Only] Streaming</span></span>

<span data-ttu-id="66d34-114">[Comunicação remota holográfica](/windows/mixed-reality/add-holographic-remoting) significa transmitir dados de um PC ou um dispositivo UWP autônomo para o HoloLens 2, sem mudar de canal.</span><span class="sxs-lookup"><span data-stu-id="66d34-114">[Holographic Remoting](/windows/mixed-reality/add-holographic-remoting) means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="66d34-115">Um aplicativo host de comunicação remota recebe um fluxo de dados de entrada de um HoloLens, renderiza o conteúdo em uma exibição imersiva virtual e transmite quadros de conteúdo novamente para o HoloLens por Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="66d34-115">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="66d34-116">O streaming permite que você adicione exibições imersivas remotas a um programa de software de PC desktop existente e tenha acesso a mais recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="66d34-116">Streaming lets you add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="66d34-117">Se você estiver seguindo por esse caminho com o aplicativo de xadrez, precisará fazer algumas coisas:</span><span class="sxs-lookup"><span data-stu-id="66d34-117">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="66d34-118">Instale o **Player de Comunicação Remota Holográfica** por meio da Microsoft Store no seu HoloLens 2 e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="66d34-118">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="66d34-119">Anote o endereço IP exibido no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="66d34-119">Note your IP address displayed in the app.</span></span>
    * <span data-ttu-id="66d34-120">Acesse **Editar > Configurações de Projeto** e verifique se o **RHI Padrão** do Windows está definido como **Padrão** ou **D3D11**:</span><span class="sxs-lookup"><span data-stu-id="66d34-120">Go to **Edit > Project Settings** and sure the Windows **Default RHI** is set to **Default** or **D3D11**:</span></span>

![RHI Padrão](../images/unreal/performance-recommendations-img-09.png)

2.  <span data-ttu-id="66d34-122">De volta no editor do Unreal, acesse **Editar > Configurações do Projeto** e marque **Habilitar a Comunicação Remota** na seção **Comunicação Remota Holográfica**.</span><span class="sxs-lookup"><span data-stu-id="66d34-122">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="66d34-123">Reinicie o editor e insira o endereço IP do dispositivo (conforme exibido no aplicativo Player de Comunicação Remota do Holographic) e clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="66d34-123">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="66d34-124">Quando estiver conectado, clique na seta suspensa à direita do botão **Jogar** e selecione a **Visualização de VR**.</span><span class="sxs-lookup"><span data-stu-id="66d34-124">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="66d34-125">O aplicativo será executado na janela de Visualização de VR, que é transmitida para o headset do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="66d34-125">The app will run in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="66d34-126">Empacotar e implantar o aplicativo por meio do portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="66d34-126">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="66d34-127">Se esta for a primeira vez que você empacota um aplicativo Unreal para o HoloLens, precisará baixar os arquivos de suporte do Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="66d34-127">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="66d34-128">Vá para **Preferências do Editor > Geral > Código-Fonte > Editor de Código-Fonte** e verifique se o Visual Studio 2019 está selecionado.</span><span class="sxs-lookup"><span data-stu-id="66d34-128">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="66d34-129">Vá para a guia **Biblioteca** no Inicializador da Epic Games, selecione a seta suspensa ao lado de **Iniciar** > e clique em **Opções**.</span><span class="sxs-lookup"><span data-stu-id="66d34-129">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="66d34-130">Em **Plataformas de Destino**, selecione **HoloLens 2** e clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="66d34-130">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="66d34-131">![Alterar a plataforma de destino nas configurações do projeto](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="66d34-131">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="66d34-132">Acesse **Editar > Configurações do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="66d34-132">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="66d34-133">Em **Projeto > Descrição > Sobre > Nome do Projeto**, adicione um nome de projeto.</span><span class="sxs-lookup"><span data-stu-id="66d34-133">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="66d34-134">Adicione **CN=NomeDaSuaEmpresa** em **Projeto > Descrição > Editor > Nome Diferenciado da Empresa**.</span><span class="sxs-lookup"><span data-stu-id="66d34-134">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>
    * <span data-ttu-id="66d34-135">Selecione **Iniciar em VR** em **Projeto > Descrição > Configurações**.</span><span class="sxs-lookup"><span data-stu-id="66d34-135">Select **Start in VR** under **Project > Description > Settings**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66d34-136">Se você deixar um desses campos em branco, isso resultará em um erro quando você tentar e gerar um novo certificado na etapa 3.</span><span class="sxs-lookup"><span data-stu-id="66d34-136">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66d34-137">O nome do editor precisa estar no [Formato de Nomes Diferenciados LADPv3](https://www.ietf.org/rfc/rfc2253.txt).</span><span class="sxs-lookup"><span data-stu-id="66d34-137">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="66d34-138">Um nome malformado do editor gera o erro "Chave de assinatura não encontrada.</span><span class="sxs-lookup"><span data-stu-id="66d34-138">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="66d34-139">Não foi possível assinar o aplicativo digitalmente."</span><span class="sxs-lookup"><span data-stu-id="66d34-139">The app could not be digitally signed."</span></span> <span data-ttu-id="66d34-140">durante o empacotamento.</span><span class="sxs-lookup"><span data-stu-id="66d34-140">error upon packaging.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66d34-141">Se você não selecionar "Iniciar em VR", o aplicativo tentará iniciar em um slate</span><span class="sxs-lookup"><span data-stu-id="66d34-141">Not selecting "Start in VR" will lead your application trying to start in a slate</span></span>

![Configurações do projeto – descrição](images/unreal-uxt/6-cn-new.PNG)

2.  <span data-ttu-id="66d34-143">Habilite **Compilar para Emulação no HoloLens** e/ou **Compilar para Dispositivo do HoloLens** em **Plataformas > HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="66d34-143">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="66d34-144">Clique em **Gerar novo** na seção **Empacotamento** (ao lado de **Certificado de Autenticação**).</span><span class="sxs-lookup"><span data-stu-id="66d34-144">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66d34-145">Se você está usando um certificado que já foi gerado, o nome do editor do certificado precisa ser igual ao nome do editor do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="66d34-145">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="66d34-146">Caso contrário, isso gera o erro "Chave de assinatura não encontrada.</span><span class="sxs-lookup"><span data-stu-id="66d34-146">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="66d34-147">Não foi possível assinar o aplicativo digitalmente."</span><span class="sxs-lookup"><span data-stu-id="66d34-147">The app could not be digitally signed."</span></span> <span data-ttu-id="66d34-148">erro.</span><span class="sxs-lookup"><span data-stu-id="66d34-148">error.</span></span>

![Configurações do projeto – Plataformas – HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="66d34-150">Clique em **Nenhum** para fins de teste quando precisar criar uma senha da chave privada.</span><span class="sxs-lookup"><span data-stu-id="66d34-150">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![Como gerar um novo certificado](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="66d34-152">Acesse **Arquivo > Empacotar Projeto** e selecione **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="66d34-152">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="66d34-153">Crie uma pasta para salvar o pacote e clique em **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="66d34-153">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="66d34-154">Depois que o aplicativo tiver sido empacotado, abra o [Portal de Dispositivos do Windows](/windows/mixed-reality/using-the-windows-device-portal), acesse **Exibições > Aplicativos** e localize a seção **Implantar aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="66d34-154">Open the [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="66d34-155">Clique em **Procurar...** , encontre o arquivo **ChessApp.appxbundle** e clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="66d34-155">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="66d34-156">Marque a caixa ao lado de **Permitir que eu selecione pacotes de estrutura** se você está instalando o aplicativo no seu dispositivo pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="66d34-156">Check the box next to **Allow me to select framework packages** if you're installing the app on your device for the first time.</span></span>
    * <span data-ttu-id="66d34-157">Na próxima caixa de diálogo, inclua os arquivos **VCLibs** e **appx** apropriados: **arm64** para dispositivo e **x64** para emulador.</span><span class="sxs-lookup"><span data-stu-id="66d34-157">In the next dialogue, include the appropriate **VCLibs** and **appx** files, **arm64** for device and **x64** for emulator.</span></span> <span data-ttu-id="66d34-158">Encontre os arquivos no **HoloLens**, dentro da pasta em que você salvou o pacote.</span><span class="sxs-lookup"><span data-stu-id="66d34-158">You can find the files under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="66d34-159">Clique em **Instalar**</span><span class="sxs-lookup"><span data-stu-id="66d34-159">Click **Install**</span></span>
    * <span data-ttu-id="66d34-160">Agora você pode acessar **Todos os Aplicativos** e tocar no aplicativo recém-instalado para executá-lo ou iniciar o aplicativo diretamente do **Portal de Dispositivos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="66d34-160">You can now go to **All Apps** and tap the newly installed app to run it, or start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="66d34-161">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="66d34-161">Congratulations!</span></span> <span data-ttu-id="66d34-162">Seu aplicativo de realidade misturada do HoloLens está concluído e pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="66d34-162">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="66d34-163">No entanto, esse não é o final da estrada.</span><span class="sxs-lookup"><span data-stu-id="66d34-163">However, you're not at the end of the road.</span></span> <span data-ttu-id="66d34-164">O MRTK tem muitos recursos autônomos que você pode adicionar aos seus projetos, incluindo entrada por foco e voz, mapeamento espacial e até mesmo códigos QR.</span><span class="sxs-lookup"><span data-stu-id="66d34-164">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="66d34-165">Mais informações sobre esses recursos podem ser encontradas na [Visão geral do desenvolvimento com o Unreal](/windows/mixed-reality/unreal-development-overview).</span><span class="sxs-lookup"><span data-stu-id="66d34-165">More information on these features can be found in the [Unreal development overview](/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="66d34-166">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="66d34-166">Next Development Checkpoint</span></span>

<span data-ttu-id="66d34-167">Se está seguindo o percurso de desenvolvimento do Unreal que estabelecemos, você está no meio da exploração dos principais blocos de construção do MRTK.</span><span class="sxs-lookup"><span data-stu-id="66d34-167">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="66d34-168">Deste ponto, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="66d34-168">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66d34-169">Entrada por foco</span><span class="sxs-lookup"><span data-stu-id="66d34-169">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="66d34-170">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="66d34-170">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66d34-171">Câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="66d34-171">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="66d34-172">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](../unreal-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="66d34-172">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>