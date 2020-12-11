---
title: 6. Como empacotar e implantar no dispositivo ou emulador
description: Parte 6 de 6 de uma série de tutoriais para criação de um aplicativo de xadrez usando o Unreal Engine 4 e o plug-in Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 4319b1171090b8ca7a320e98867bfb3635bab005
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609487"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="fec35-104">6. Como empacotar e implantar no dispositivo ou emulador</span><span class="sxs-lookup"><span data-stu-id="fec35-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="fec35-105">No tutorial anterior, você adicionou um botão simples que redefine a peça de xadrez para a posição original dela.</span><span class="sxs-lookup"><span data-stu-id="fec35-105">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="fec35-106">Nesta seção final, você fará com que o aplicativo esteja pronto para ser executado em um HoloLens 2 ou em um emulador.</span><span class="sxs-lookup"><span data-stu-id="fec35-106">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="fec35-107">Se você tem um HoloLens 2, pode transmitir do seu computador ou empacotar o aplicativo para ser executado diretamente no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fec35-107">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="fec35-108">Se você não tem um dispositivo, você está empacotando o aplicativo para ser executado no emulador.</span><span class="sxs-lookup"><span data-stu-id="fec35-108">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="fec35-109">Ao final desta seção, você terá um aplicativo de realidade misturada implantado que você poderá jogar, completo, com interações e interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="fec35-109">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="fec35-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="fec35-110">Objectives</span></span>

* <span data-ttu-id="fec35-111">[Somente para dispositivo] Transmitir para o HoloLens 2 por meio de comunicação remota holográfica do aplicativo</span><span class="sxs-lookup"><span data-stu-id="fec35-111">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="fec35-112">Empacotar e implantar seu aplicativo em um emulador ou dispositivo do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fec35-112">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="fec35-113">[Somente para dispositivo] Streaming</span><span class="sxs-lookup"><span data-stu-id="fec35-113">[Device Only] Streaming</span></span>

<span data-ttu-id="fec35-114">[Comunicação remota holográfica](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) significa transmitir dados de um PC ou um dispositivo UWP autônomo para o HoloLens 2, sem mudar de canal.</span><span class="sxs-lookup"><span data-stu-id="fec35-114">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="fec35-115">Um aplicativo host de comunicação remota recebe um fluxo de dados de entrada de um HoloLens, renderiza o conteúdo em uma exibição imersiva virtual e transmite quadros de conteúdo novamente para o HoloLens por Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="fec35-115">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="fec35-116">O streaming permite que você adicione exibições imersivas remotas a um programa de software de PC desktop existente e tenha acesso a mais recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="fec35-116">Streaming lets you add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="fec35-117">Se você estiver seguindo por esse caminho com o aplicativo de xadrez, precisará fazer algumas coisas:</span><span class="sxs-lookup"><span data-stu-id="fec35-117">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="fec35-118">Instale o **Player de Comunicação Remota Holográfica** por meio da Microsoft Store no seu HoloLens 2 e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fec35-118">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="fec35-119">Anote o endereço IP exibido no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fec35-119">Note your IP address displayed in the app.</span></span>

2.  <span data-ttu-id="fec35-120">De volta no editor do Unreal, acesse **Editar > Configurações do Projeto** e marque **Habilitar a Comunicação Remota** na seção **Comunicação Remota Holográfica**.</span><span class="sxs-lookup"><span data-stu-id="fec35-120">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="fec35-121">Reinicie o editor e insira o endereço IP do dispositivo (conforme exibido no aplicativo Player de Comunicação Remota do Holographic) e clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="fec35-121">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="fec35-122">Quando estiver conectado, clique na seta suspensa à direita do botão **Jogar** e selecione a **Visualização de VR**.</span><span class="sxs-lookup"><span data-stu-id="fec35-122">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="fec35-123">O aplicativo será executado na janela de Visualização de VR, que é transmitida para o headset do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fec35-123">The app will run in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="fec35-124">Empacotar e implantar o aplicativo por meio do portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="fec35-124">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="fec35-125">Se esta for a primeira vez que você empacota um aplicativo Unreal para o HoloLens, precisará baixar os arquivos de suporte do Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="fec35-125">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="fec35-126">Vá para **Preferências do Editor > Geral > Código-Fonte > Editor de Código-Fonte** e verifique se o Visual Studio 2019 está selecionado.</span><span class="sxs-lookup"><span data-stu-id="fec35-126">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="fec35-127">Vá para a guia **Biblioteca** no Inicializador da Epic Games, selecione a seta suspensa ao lado de **Iniciar** > e clique em **Opções**.</span><span class="sxs-lookup"><span data-stu-id="fec35-127">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="fec35-128">Em **Plataformas de Destino**, selecione **HoloLens 2** e clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="fec35-128">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="fec35-129">![Alterar a plataforma de destino nas configurações do projeto](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="fec35-129">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="fec35-130">Acesse **Editar > Configurações do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="fec35-130">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="fec35-131">Em **Projeto > Descrição > Sobre > Nome do Projeto**, adicione um nome de projeto.</span><span class="sxs-lookup"><span data-stu-id="fec35-131">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="fec35-132">Adicione **CN=NomeDaSuaEmpresa** em **Projeto > Descrição > Editor > Nome Diferenciado da Empresa**.</span><span class="sxs-lookup"><span data-stu-id="fec35-132">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fec35-133">Se você deixar um desses campos em branco, isso resultará em um erro quando você tentar e gerar um novo certificado na etapa 3.</span><span class="sxs-lookup"><span data-stu-id="fec35-133">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fec35-134">O nome do editor precisa estar no [Formato de Nomes Diferenciados LADPv3](https://www.ietf.org/rfc/rfc2253.txt).</span><span class="sxs-lookup"><span data-stu-id="fec35-134">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="fec35-135">Um nome malformado do editor gera o erro "Chave de assinatura não encontrada.</span><span class="sxs-lookup"><span data-stu-id="fec35-135">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="fec35-136">Não foi possível assinar o aplicativo digitalmente."</span><span class="sxs-lookup"><span data-stu-id="fec35-136">The app could not be digitally signed."</span></span> <span data-ttu-id="fec35-137">durante o empacotamento.</span><span class="sxs-lookup"><span data-stu-id="fec35-137">error upon packaging.</span></span>

![Configurações do projeto – descrição](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="fec35-139">Habilite **Compilar para Emulação no HoloLens** e/ou **Compilar para Dispositivo do HoloLens** em **Plataformas > HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="fec35-139">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="fec35-140">Clique em **Gerar novo** na seção **Empacotamento** (ao lado de **Certificado de Autenticação**).</span><span class="sxs-lookup"><span data-stu-id="fec35-140">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fec35-141">Se você está usando um certificado que já foi gerado, o nome do editor do certificado precisa ser igual ao nome do editor do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fec35-141">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="fec35-142">Caso contrário, isso gera o erro "Chave de assinatura não encontrada.</span><span class="sxs-lookup"><span data-stu-id="fec35-142">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="fec35-143">Não foi possível assinar o aplicativo digitalmente."</span><span class="sxs-lookup"><span data-stu-id="fec35-143">The app could not be digitally signed."</span></span> <span data-ttu-id="fec35-144">erro.</span><span class="sxs-lookup"><span data-stu-id="fec35-144">error.</span></span>

![Configurações do projeto – Plataformas – HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="fec35-146">Clique em **Nenhum** para fins de teste quando precisar criar uma senha da chave privada.</span><span class="sxs-lookup"><span data-stu-id="fec35-146">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![Como gerar um novo certificado](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="fec35-148">Acesse **Arquivo > Empacotar Projeto** e selecione **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="fec35-148">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="fec35-149">Crie uma pasta para salvar o pacote e clique em **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="fec35-149">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="fec35-150">Depois que o aplicativo tiver sido empacotado, abra o [Portal de Dispositivos do Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal), acesse **Exibições > Aplicativos** e localize a seção **Implantar aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="fec35-150">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="fec35-151">Clique em **Procurar...** , encontre o arquivo **ChessApp.appxbundle** e clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="fec35-151">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="fec35-152">Marque a caixa ao lado de **Permitir que eu selecione pacotes de estrutura** se você está instalando o aplicativo no seu dispositivo pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="fec35-152">Check the box next to **Allow me to select framework packages** if you're installing the app on your device for the first time.</span></span>
    * <span data-ttu-id="fec35-153">Na próxima caixa de diálogo, inclua os arquivos **VCLibs** e **appx** apropriados: **arm64** para dispositivo e **x64** para emulador.</span><span class="sxs-lookup"><span data-stu-id="fec35-153">In the next dialogue, include the appropriate **VCLibs** and **appx** files, **arm64** for device and **x64** for emulator.</span></span> <span data-ttu-id="fec35-154">Encontre os arquivos no **HoloLens**, dentro da pasta em que você salvou o pacote.</span><span class="sxs-lookup"><span data-stu-id="fec35-154">You can find the files under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="fec35-155">Clique em **Instalar**</span><span class="sxs-lookup"><span data-stu-id="fec35-155">Click **Install**</span></span>
    * <span data-ttu-id="fec35-156">Agora você pode acessar **Todos os Aplicativos** e tocar no aplicativo recém-instalado para executá-lo ou iniciar o aplicativo diretamente do **Portal de Dispositivos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="fec35-156">You can now go to **All Apps** and tap the newly installed app to run it, or start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="fec35-157">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="fec35-157">Congratulations!</span></span> <span data-ttu-id="fec35-158">Seu aplicativo de realidade misturada do HoloLens está concluído e pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="fec35-158">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="fec35-159">No entanto, esse não é o final da estrada.</span><span class="sxs-lookup"><span data-stu-id="fec35-159">However, you're not at the end of the road.</span></span> <span data-ttu-id="fec35-160">O MRTK tem muitos recursos autônomos que você pode adicionar aos seus projetos, incluindo entrada por foco e voz, mapeamento espacial e até mesmo códigos QR.</span><span class="sxs-lookup"><span data-stu-id="fec35-160">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="fec35-161">Mais informações sobre esses recursos podem ser encontradas na [Visão geral do desenvolvimento com o Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span><span class="sxs-lookup"><span data-stu-id="fec35-161">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="fec35-162">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="fec35-162">Next Development Checkpoint</span></span>

<span data-ttu-id="fec35-163">Se está seguindo o percurso de desenvolvimento do Unreal que estabelecemos, você está no meio da exploração dos principais blocos de construção do MRTK.</span><span class="sxs-lookup"><span data-stu-id="fec35-163">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="fec35-164">Deste ponto, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="fec35-164">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fec35-165">Entrada por foco</span><span class="sxs-lookup"><span data-stu-id="fec35-165">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="fec35-166">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="fec35-166">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fec35-167">Câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="fec35-167">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="fec35-168">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](../unreal-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="fec35-168">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
