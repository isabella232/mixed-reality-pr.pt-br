---
title: Como usar o Visual Studio para implantação e depuração
description: Saiba como compilar, depurar e implantar aplicativos para o HoloLens e o Windows Mixed Reality usando o Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, realidade misturada, depurar, implantar
ms.openlocfilehash: 2ab89311163a48ee3c14511446a1498ce883a232
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "100496084"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="3d008-104">Como usar o Visual Studio para implantação e depuração</span><span class="sxs-lookup"><span data-stu-id="3d008-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="3d008-105">Se você estiver usando o DirectX ou Unity para desenvolver seu aplicativo de realidade misturada, o Visual Studio é sua ferramenta ideal para depuração e implantação.</span><span class="sxs-lookup"><span data-stu-id="3d008-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="3d008-106">Nesta seção, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="3d008-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="3d008-107">Implantar aplicativos no HoloLens ou no headset imersivo do Windows Mixed Reality por meio do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d008-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="3d008-108">Usar o emulador do HoloLens incorporado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d008-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="3d008-109">Depurar aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="3d008-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3d008-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3d008-110">Prerequisites</span></span>

1. <span data-ttu-id="3d008-111">Confira [Instalar as ferramentas](../../develop/install-the-tools.md#installation-checklist) para obter instruções de instalação.</span><span class="sxs-lookup"><span data-stu-id="3d008-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="3d008-112">Crie um projeto de aplicativo universal do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d008-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="3d008-113">Para o HoloLens (1ª geração), use o Visual Studio 2017 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="3d008-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="3d008-114">Para o HoloLens 2, use o Visual Studio 2019 16.2 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="3d008-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="3d008-115">Há suporte para C# e C++.</span><span class="sxs-lookup"><span data-stu-id="3d008-115">C# and C++ are supported.</span></span> <span data-ttu-id="3d008-116">(Ou siga as instruções para [criar um aplicativo no Unity](../../develop/unity/tutorials/holograms-100.md).)</span><span class="sxs-lookup"><span data-stu-id="3d008-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="3d008-117">Habilitar o modo de desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="3d008-117">Enabling Developer Mode</span></span>

<span data-ttu-id="3d008-118">Comece habilitando o **Modo de Desenvolvedor** no dispositivo, para que o Visual Studio possa se conectar a ele.</span><span class="sxs-lookup"><span data-stu-id="3d008-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="3d008-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="3d008-119">HoloLens</span></span>

1. <span data-ttu-id="3d008-120">Ligue o HoloLens e coloque o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3d008-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="3d008-121">Use o [gesto de início](../../design/system-gesture.md) para iniciar o menu principal.</span><span class="sxs-lookup"><span data-stu-id="3d008-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="3d008-122">Selecione o bloco **Configurações** para iniciar o aplicativo no ambiente.</span><span class="sxs-lookup"><span data-stu-id="3d008-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="3d008-123">Selecione item de menu **Atualização**.</span><span class="sxs-lookup"><span data-stu-id="3d008-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="3d008-124">Selecione o item de menu **Para desenvolvedores**.</span><span class="sxs-lookup"><span data-stu-id="3d008-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="3d008-125">Habilite o **Modo de Desenvolvedor** para implantar aplicativos do Visual Studio em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3d008-125">Enable **Developer Mode** to deploy apps from Visual Studio to your HoloLens.</span></span>
7. <span data-ttu-id="3d008-126">Opcional: Role para baixo e habilite também o **Portal de Dispositivos**, que permite que você se conecte ao [Portal de Dispositivos do Windows](using-the-windows-device-portal.md) no seu HoloLens de um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="3d008-126">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="3d008-127">Computador Windows</span><span class="sxs-lookup"><span data-stu-id="3d008-127">Windows PC</span></span>

<span data-ttu-id="3d008-128">Se você estiver trabalhando com um headset do Windows Mixed Reality conectado ao computador, habilite o **Modo de Desenvolvedor** no computador.</span><span class="sxs-lookup"><span data-stu-id="3d008-128">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="3d008-129">Ir para **Configurações**</span><span class="sxs-lookup"><span data-stu-id="3d008-129">Go to **Settings**</span></span>
2. <span data-ttu-id="3d008-130">Selecione **Atualização e Segurança**</span><span class="sxs-lookup"><span data-stu-id="3d008-130">Select **Update and Security**</span></span>
3. <span data-ttu-id="3d008-131">Selecione **Para desenvolvedores**</span><span class="sxs-lookup"><span data-stu-id="3d008-131">Select **For developers**</span></span>
4. <span data-ttu-id="3d008-132">Habilite o **Modo de Desenvolvedor**, leia o aviso de isenção de responsabilidade da configuração escolhida e, em seguida, selecione Sim para aceitar a alteração.</span><span class="sxs-lookup"><span data-stu-id="3d008-132">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="3d008-133">Como implantar um aplicativo HoloLens via Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="3d008-133">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="3d008-134">Configure seu projeto do Visual Studio com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="3d008-134">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="3d008-135">Selecione suas opções de compilação de aplicativos</span><span class="sxs-lookup"><span data-stu-id="3d008-135">Select your apps compilation options</span></span>
    * <span data-ttu-id="3d008-136">Para projetos do Unity, escolha **Versão** ou **Mestre**</span><span class="sxs-lookup"><span data-stu-id="3d008-136">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="3d008-137">Para todos os outros projetos, escolha **Versão**</span><span class="sxs-lookup"><span data-stu-id="3d008-137">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="3d008-138">Você pode encontrar definições completas para cada opção de compilação em [Como exportar e criar uma solução do Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="3d008-138">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="3d008-139">Selecione a configuração de build com base no seu dispositivo</span><span class="sxs-lookup"><span data-stu-id="3d008-139">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="3d008-140">Selecione **Computador Remoto** no menu suspenso do destino de implantação</span><span class="sxs-lookup"><span data-stu-id="3d008-140">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Destino de implantação de computador remoto no Visual Studio](images/remotemachinesetting_arm64.png)

<span data-ttu-id="3d008-142">Em seguida, você precisa definir sua conexão remota.</span><span class="sxs-lookup"><span data-stu-id="3d008-142">Next, you need to set your remote connection.</span></span> <span data-ttu-id="3d008-143">Para projetos C++ e JavaScript, acesse **Projeto > Propriedades > Propriedades de Configuração > Depuração**.</span><span class="sxs-lookup"><span data-stu-id="3d008-143">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="3d008-144">Se você estiver trabalhando em um projeto C#, uma caixa de diálogo deverá aparecer automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3d008-144">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="3d008-145">Se a caixa de diálogo da conexão remota não aparecer no seu projeto C#, você poderá abri-la manualmente em **Propriedades > Depurar**.</span><span class="sxs-lookup"><span data-stu-id="3d008-145">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="3d008-146">Insira o endereço IP do dispositivo no campo **Endereço** ou **Nome do Computador**.</span><span class="sxs-lookup"><span data-stu-id="3d008-146">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="3d008-147">Você pode encontrar o endereço IP no HoloLens em **Configurações > Rede e Internet > Opções Avançadas**</span><span class="sxs-lookup"><span data-stu-id="3d008-147">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="3d008-148">É sempre recomendável inserir manualmente seu endereço IP em vez de depender do recurso detectado automaticamente</span><span class="sxs-lookup"><span data-stu-id="3d008-148">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="3d008-149">Defina o **Modo de Autenticação** como **Universal (Protocolo não criptografado)**</span><span class="sxs-lookup"><span data-stu-id="3d008-149">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Caixa de diálogo de conexão remota no Visual Studio](images/remotedeploy.png)

3. <span data-ttu-id="3d008-151">Compile, implante e depure o aplicativo com base em suas necessidades</span><span class="sxs-lookup"><span data-stu-id="3d008-151">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="3d008-152">Selecione **Depurar > Iniciar depuração** para implantar o aplicativo e iniciar a depuração</span><span class="sxs-lookup"><span data-stu-id="3d008-152">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="3d008-153">Selecione **Compilar > Implantar** para compilar e implantar sem depurar</span><span class="sxs-lookup"><span data-stu-id="3d008-153">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)

4. <span data-ttu-id="3d008-155">Na primeira vez que implantar um aplicativo no HoloLens por meio do computador, você deverá fornecer um PIN.</span><span class="sxs-lookup"><span data-stu-id="3d008-155">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="3d008-156">Siga as instruções de **Como emparelhar o dispositivo** abaixo.</span><span class="sxs-lookup"><span data-stu-id="3d008-156">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="3d008-157">Como implantar um aplicativo HoloLens via USB</span><span class="sxs-lookup"><span data-stu-id="3d008-157">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="3d008-158">Selecione suas opções de compilação de aplicativos</span><span class="sxs-lookup"><span data-stu-id="3d008-158">Select your apps compilation options</span></span>
    * <span data-ttu-id="3d008-159">Para projetos do Unity, escolha **Versão** ou **Mestre**</span><span class="sxs-lookup"><span data-stu-id="3d008-159">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="3d008-160">Para todos os outros projetos, escolha **Versão**</span><span class="sxs-lookup"><span data-stu-id="3d008-160">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="3d008-161">Você pode encontrar definições completas para cada opção de compilação em [Como exportar e criar uma solução do Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="3d008-161">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="3d008-162">Selecione a configuração de build com base no seu dispositivo</span><span class="sxs-lookup"><span data-stu-id="3d008-162">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="3d008-163">Selecione **Dispositivo** no menu suspenso do destino de implantação</span><span class="sxs-lookup"><span data-stu-id="3d008-163">Select **Device** in the deployment target drop-down menu</span></span>

![Implantação de dispositivo no Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="3d008-165">Compile, implante e depure o aplicativo com base em suas necessidades</span><span class="sxs-lookup"><span data-stu-id="3d008-165">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="3d008-166">Selecione **Depurar > Iniciar depuração** para implantar o aplicativo e iniciar a depuração</span><span class="sxs-lookup"><span data-stu-id="3d008-166">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="3d008-167">Selecione **Compilar > Implantar** para compilar e implantar sem depurar</span><span class="sxs-lookup"><span data-stu-id="3d008-167">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="3d008-169">Na primeira vez que implantar um aplicativo no HoloLens por meio do computador, você deverá fornecer um PIN.</span><span class="sxs-lookup"><span data-stu-id="3d008-169">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="3d008-170">Siga as instruções de **Como emparelhar o dispositivo** abaixo.</span><span class="sxs-lookup"><span data-stu-id="3d008-170">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="3d008-171">Se você estiver vendo um tempo de latência considerável com a implantação dos aplicativos via USB, recomendamos o uso das [instruções do computador remoto](#deploying-a-hololens-app-over-wi-fi) na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="3d008-171">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="3d008-172">Como implantar um aplicativo no emulador do HoloLens</span><span class="sxs-lookup"><span data-stu-id="3d008-172">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="3d008-173">Verifique se você **[instalou o emulador do HoloLens 2 ou do HoloLens (1ª geração)](../install-the-tools.md#installation-checklist)**</span><span class="sxs-lookup"><span data-stu-id="3d008-173">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="3d008-174">Selecione a configuração de build e o emulador com base no seu dispositivo</span><span class="sxs-lookup"><span data-stu-id="3d008-174">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="3d008-175">Compile, implante e depure o aplicativo com base em suas necessidades</span><span class="sxs-lookup"><span data-stu-id="3d008-175">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="3d008-176">Selecione **Depurar > Iniciar depuração** para implantar o aplicativo e iniciar a depuração</span><span class="sxs-lookup"><span data-stu-id="3d008-176">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="3d008-177">Selecione **Compilar > Implantar** para compilar e implantar sem depurar</span><span class="sxs-lookup"><span data-stu-id="3d008-177">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="3d008-179">Como implantar um aplicativo de VR no seu computador local</span><span class="sxs-lookup"><span data-stu-id="3d008-179">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="3d008-180">Para usar um headset imersivo do Windows Mixed Reality que se conecta ao computador ou o [simulador de realidade misturada](using-the-windows-mixed-reality-simulator.md):</span><span class="sxs-lookup"><span data-stu-id="3d008-180">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="3d008-181">Selecione uma configuração de build **x86** ou **x64** para o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3d008-181">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="3d008-182">Selecione **Computador Local** no menu suspenso do destino de implantação</span><span class="sxs-lookup"><span data-stu-id="3d008-182">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="3d008-183">Compile, implante e depure o aplicativo com base em suas necessidades</span><span class="sxs-lookup"><span data-stu-id="3d008-183">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="3d008-184">Selecione **Depurar > Iniciar depuração** para implantar o aplicativo e iniciar a depuração</span><span class="sxs-lookup"><span data-stu-id="3d008-184">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="3d008-185">Selecione **Compilar > Implantar** para compilar e implantar sem depurar</span><span class="sxs-lookup"><span data-stu-id="3d008-185">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="3d008-186">Como emparelhar o dispositivo</span><span class="sxs-lookup"><span data-stu-id="3d008-186">Pairing your device</span></span>

<span data-ttu-id="3d008-187">Na primeira vez que implantar um aplicativo no HoloLens por meio do Visual Studio, você deverá fornecer um PIN.</span><span class="sxs-lookup"><span data-stu-id="3d008-187">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="3d008-188">No HoloLens, gere um PIN iniciando o aplicativo Configurações, acesse **Atualizar > Para Desenvolvedores** e toque em **Emparelhar**.</span><span class="sxs-lookup"><span data-stu-id="3d008-188">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="3d008-189">Quando o PIN for exibido no seu HoloLens, digite-o no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d008-189">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="3d008-190">Após a conclusão do emparelhamento, toque em **Concluído** no HoloLens para ignorar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="3d008-190">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="3d008-191">Este computador agora está emparelhado com o HoloLens, e você pode implantar aplicativos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3d008-191">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="3d008-192">Repita essas etapas para todos os computadores usados para implantar aplicativos no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3d008-192">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="3d008-193">Para desemparelhar seu HoloLens de todos os computadores emparelhados:</span><span class="sxs-lookup"><span data-stu-id="3d008-193">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="3d008-194">Inicie o aplicativo **Configurações**, acesse **Atualização > Para Desenvolvedores** e toque em **Desmarcar**.</span><span class="sxs-lookup"><span data-stu-id="3d008-194">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="3d008-195">Depurador de Gráficos do HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="3d008-195">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="3d008-196">As ferramentas Diagnóstico de Gráficos do Visual Studio são úteis quando você quer escrever e otimizar um aplicativo holográfico.</span><span class="sxs-lookup"><span data-stu-id="3d008-196">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="3d008-197">Confira [Diagnóstico de Gráficos do Visual Studio no MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) para obter detalhes completos.</span><span class="sxs-lookup"><span data-stu-id="3d008-197">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="3d008-198">**Para iniciar o Depurador de Gráficos**</span><span class="sxs-lookup"><span data-stu-id="3d008-198">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="3d008-199">Siga as instruções acima para definir um dispositivo ou um emulador como destino</span><span class="sxs-lookup"><span data-stu-id="3d008-199">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="3d008-200">Acesse **Depurar > Gráficos > Iniciar Diagnóstico**</span><span class="sxs-lookup"><span data-stu-id="3d008-200">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="3d008-201">Na primeira vez que você iniciar o diagnóstico com um HoloLens, talvez você receba um erro de "acesso negado".</span><span class="sxs-lookup"><span data-stu-id="3d008-201">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="3d008-202">Reinicialize o HoloLens para permitir que as permissões atualizadas entrem em vigor e tente novamente.</span><span class="sxs-lookup"><span data-stu-id="3d008-202">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="3d008-203">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="3d008-203">Profiling</span></span>

<span data-ttu-id="3d008-204">As ferramentas de criação de perfil do Visual Studio permitem que você analise o desempenho e o uso de recursos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3d008-204">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="3d008-205">Isso inclui ferramentas para otimizar a CPU, a memória, os elementos gráficos e o uso da rede.</span><span class="sxs-lookup"><span data-stu-id="3d008-205">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="3d008-206">Confira [Executar ferramentas de diagnóstico sem depuração no MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) para obter detalhes completos.</span><span class="sxs-lookup"><span data-stu-id="3d008-206">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="3d008-207">**Para iniciar as ferramentas de criação de perfil com o HoloLens**</span><span class="sxs-lookup"><span data-stu-id="3d008-207">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="3d008-208">Siga as instruções acima para definir um dispositivo ou um emulador como destino</span><span class="sxs-lookup"><span data-stu-id="3d008-208">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="3d008-209">Acesse **Depurar > Iniciar Ferramentas de Diagnóstico sem Depuração...**</span><span class="sxs-lookup"><span data-stu-id="3d008-209">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="3d008-210">Selecione as ferramentas que deseja usar</span><span class="sxs-lookup"><span data-stu-id="3d008-210">Select the tools you want to use</span></span>
4. <span data-ttu-id="3d008-211">Selecione **Iniciar**</span><span class="sxs-lookup"><span data-stu-id="3d008-211">Select **Start**</span></span>
5. <span data-ttu-id="3d008-212">Na primeira vez que você iniciar o diagnóstico sem fazer a depuração com um HoloLens, talvez você receba um erro de "acesso negado".</span><span class="sxs-lookup"><span data-stu-id="3d008-212">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="3d008-213">Reinicialize o HoloLens para permitir que as permissões atualizadas entrem em vigor e tente novamente.</span><span class="sxs-lookup"><span data-stu-id="3d008-213">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="3d008-214">Como depurar um aplicativo instalado ou em execução</span><span class="sxs-lookup"><span data-stu-id="3d008-214">Debugging an installed or running app</span></span>

<span data-ttu-id="3d008-215">Use o Visual Studio para depurar um aplicativo universal do Windows instalado sem a implantação por meio de um projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d008-215">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="3d008-216">Isso será útil se você quiser depurar um pacote do aplicativo instalado ou um aplicativo que já esteja em execução.</span><span class="sxs-lookup"><span data-stu-id="3d008-216">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="3d008-217">Acesse **Depurar -> Outros Destinos de Depuração-> Depurar Pacote do Aplicativo Instalado**</span><span class="sxs-lookup"><span data-stu-id="3d008-217">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="3d008-218">Selecione o destino **Computador Remoto** para o HoloLens ou **Computador Local** para headsets imersivos.</span><span class="sxs-lookup"><span data-stu-id="3d008-218">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="3d008-219">Insira o endereço IP do **dispositivo**</span><span class="sxs-lookup"><span data-stu-id="3d008-219">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="3d008-220">Escolha o Modo de Autenticação **Universal**</span><span class="sxs-lookup"><span data-stu-id="3d008-220">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="3d008-221">A janela mostrará os aplicativos em execução e inativos.</span><span class="sxs-lookup"><span data-stu-id="3d008-221">The window shows both running and inactive apps.</span></span> <span data-ttu-id="3d008-222">Escolha aquele que deseja depurar.</span><span class="sxs-lookup"><span data-stu-id="3d008-222">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="3d008-223">Escolha o tipo de código para depuração (Gerenciado, Nativo, Misto)</span><span class="sxs-lookup"><span data-stu-id="3d008-223">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="3d008-224">Selecione **Anexar** ou **Iniciar**</span><span class="sxs-lookup"><span data-stu-id="3d008-224">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="3d008-225">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="3d008-225">Next Development Checkpoint</span></span>

<span data-ttu-id="3d008-226">Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unity, você está no meio do estágio de implantação.</span><span class="sxs-lookup"><span data-stu-id="3d008-226">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="3d008-227">Deste ponto, você pode prosseguir para o próximo tópico:</span><span class="sxs-lookup"><span data-stu-id="3d008-227">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3d008-228">Como fazer a implantação no emulador do HoloLens</span><span class="sxs-lookup"><span data-stu-id="3d008-228">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="3d008-229">Ou vá diretamente para a adição de serviços avançados:</span><span class="sxs-lookup"><span data-stu-id="3d008-229">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3d008-230">Serviços avançados</span><span class="sxs-lookup"><span data-stu-id="3d008-230">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="3d008-231">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="3d008-231">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d008-232">Veja também</span><span class="sxs-lookup"><span data-stu-id="3d008-232">See also</span></span>
* [<span data-ttu-id="3d008-233">Instalar as ferramentas</span><span class="sxs-lookup"><span data-stu-id="3d008-233">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="3d008-234">Usando o emulador do HoloLens</span><span class="sxs-lookup"><span data-stu-id="3d008-234">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="3d008-235">Como implantar e depurar aplicativos UWP (Plataforma Universal do Windows)</span><span class="sxs-lookup"><span data-stu-id="3d008-235">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="3d008-236">Habilitar o dispositivo para desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="3d008-236">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)