---
title: Implantando em dispositivos Hololens e WMR
description: Documentação sobre build e implantação de aplicativos em vários dispositivos.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Visual Studio
ms.openlocfilehash: ec66c6ccb8cf1c702fed804230f5cf3ca0526139
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852306"
---
# <a name="building-and-deploying-mrtk-uwp"></a><span data-ttu-id="9aee6-104">Criando e implantando MRTK (UWP)</span><span class="sxs-lookup"><span data-stu-id="9aee6-104">Building and deploying MRTK (UWP)</span></span>

<span data-ttu-id="9aee6-105">Para executar um aplicativo no dispositivo como um aplicativo autônomo (para HoloLens, Android, iOS etc.), a etapa de build e implantação precisa ser executada no projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="9aee6-105">To run an app on device as a standalone app (for HoloLens, Android, iOS, etc.), the build and deploy step needs to be executed in the unity project.</span></span> <span data-ttu-id="9aee6-106">Compilar e implantar um aplicativo que usa o MRTK é como compilar e implantar qualquer outro aplicativo do Unity.</span><span class="sxs-lookup"><span data-stu-id="9aee6-106">Building and deploying an app that uses MRTK is just like building and deploying any other Unity app.</span></span> <span data-ttu-id="9aee6-107">Não há instruções específicas do MRTK.</span><span class="sxs-lookup"><span data-stu-id="9aee6-107">There are no MRTK-specific instructions.</span></span> <span data-ttu-id="9aee6-108">Leia abaixo para obter etapas detalhadas sobre como compilar e implantar um aplicativo do Unity para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9aee6-108">Read below for detailed steps on how to build and deploy a Unity app for HoloLens.</span></span> <span data-ttu-id="9aee6-109">Saiba mais sobre o build para outras plataformas em [Builds de publicação](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span><span class="sxs-lookup"><span data-stu-id="9aee6-109">Learn more about building for other platforms at [Publishing Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="9aee6-110">Criando e implantando MRTK para o HoloLens 1, o HoloLens 2 e o headsets WMR (UWP)</span><span class="sxs-lookup"><span data-stu-id="9aee6-110">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="9aee6-111">As instruções sobre como criar e implantar para o **hololens 1** e o **hololens 2** (UWP) podem ser encontradas em [criando seu aplicativo para o dispositivo](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="9aee6-111">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="9aee6-112">Essas etapas também permitem que você implante em **headsets WMR**.</span><span class="sxs-lookup"><span data-stu-id="9aee6-112">These steps also allow you to deploy to **WMR headsets**.</span></span>

<span data-ttu-id="9aee6-113">**Dica:** Ao compilar para o HoloLens 1, o HoloLens 2 ou o WMR, é recomendável que as configurações de compilação "versão do SDK de destino" e "versão mínima da plataforma" tenham a seguinte aparência na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="9aee6-113">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Janela de build](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="9aee6-115">As outras configurações podem ser diferentes (por exemplo, Configuração de Build/Arquitetura/Tipo de Build e outras sempre podem ser alteradas na solução do Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="9aee6-115">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="9aee6-116">Verifique se a lista suspensa "Versão do SDK de Destino" inclui a opção "10.0.18362.0". Se isso estiver ausente, [o último SDK do Windows](https://developer.microsoft.com/windows/downloads/windows-10-sdk) precisará ser instalado.</span><span class="sxs-lookup"><span data-stu-id="9aee6-116">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="9aee6-117">Unity 2019.3 e HoloLens</span><span class="sxs-lookup"><span data-stu-id="9aee6-117">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="9aee6-118">Se um aplicativo do HoloLens aparecer como um painel 2D no dispositivo, verifique se as seguintes configurações foram definidas no Unity 2019.3.x antes de implantar seu aplicativo UWP:</span><span class="sxs-lookup"><span data-stu-id="9aee6-118">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="9aee6-119">Se você estiver usando o XR herdado:</span><span class="sxs-lookup"><span data-stu-id="9aee6-119">If using the legacy XR:</span></span>

1. <span data-ttu-id="9aee6-120">Acesse Editar > Configurações do Projeto, Player</span><span class="sxs-lookup"><span data-stu-id="9aee6-120">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="9aee6-121">Em **Configurações de XR** na guia UWP, verifique se a opção **Realidade Virtual Compatível** está habilitada e se o SDK do **Windows Mixed Reality** foi adicionado aos SDKs.</span><span class="sxs-lookup"><span data-stu-id="9aee6-121">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="9aee6-122">Build e implantação no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9aee6-122">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="9aee6-123">Se você estiver usando o Plug-in de XR:</span><span class="sxs-lookup"><span data-stu-id="9aee6-123">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="9aee6-124">Siga as etapas encontradas em [Introdução ao XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span><span class="sxs-lookup"><span data-stu-id="9aee6-124">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="9aee6-125">Verifique se o perfil de configuração é o **DefaultXRSDKConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="9aee6-125">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="9aee6-126">Acesse **Editar > Configurações de Projeto, Gerenciamento do Plug-in de XR** e verifique se o **Windows Mixed Reality** está habilitado.</span><span class="sxs-lookup"><span data-stu-id="9aee6-126">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="9aee6-127">Build e implantação no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9aee6-127">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="9aee6-128">Se você estiver usando o Unity 2019.3.x, selecione **ARM64** e não **ARM** como a arquitetura de build no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9aee6-128">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="9aee6-129">Com as configurações padrão do Unity no Unity 2019.3.x, um aplicativo do Unity não será implantado em um HoloLens se o ARM for selecionado devido a um bug do Unity.</span><span class="sxs-lookup"><span data-stu-id="9aee6-129">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="9aee6-130">Acompanhe isso no [rastreador de problemas do Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="9aee6-130">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="9aee6-131">Se a arquitetura do ARM for necessária, acesse **Editar > Configurações de Projeto, Player** e, no menu **Outras Configurações**, desabilite **Trabalhos Gráficos**.</span><span class="sxs-lookup"><span data-stu-id="9aee6-131">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="9aee6-132">A desabilitação de **Trabalhos Gráficos** permitirá que o aplicativo seja implantado com a arquitetura de build do ARM para o Unity 2019.3.x, mas o ARM64 é recomendado.</span><span class="sxs-lookup"><span data-stu-id="9aee6-132">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-standalone"></a><span data-ttu-id="9aee6-133">Criando e implantando MRTK (autônomo)</span><span class="sxs-lookup"><span data-stu-id="9aee6-133">Building and deploying MRTK (Standalone)</span></span>

<span data-ttu-id="9aee6-134">Compilações autônomas de MRTK podem ser usadas em headsets WMR.</span><span class="sxs-lookup"><span data-stu-id="9aee6-134">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="9aee6-135">Um build autônomo para um headset do WMR exige as seguintes etapas extras:</span><span class="sxs-lookup"><span data-stu-id="9aee6-135">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="9aee6-136">O SDK de XR do Unity também dá suporte ao WMR nativo em builds autônomos, mas não exige o plug-in do SteamVR ou do WMR.</span><span class="sxs-lookup"><span data-stu-id="9aee6-136">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="9aee6-137">Essas etapas são necessárias para o XR herdado do Unity.</span><span class="sxs-lookup"><span data-stu-id="9aee6-137">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="9aee6-138">Instale o [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="9aee6-138">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="9aee6-139">Instale o [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="9aee6-139">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="9aee6-140">Instale o [Plug-in do WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="9aee6-140">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="9aee6-141">Como usar o plug-in do WMR</span><span class="sxs-lookup"><span data-stu-id="9aee6-141">How to use WMR plugin</span></span>

1. <span data-ttu-id="9aee6-142">Abra o Steam e procure o Plug-in do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="9aee6-142">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="9aee6-143">Verifique se o SteamVR está fechado antes de iniciar o Plug-in do WMR.</span><span class="sxs-lookup"><span data-stu-id="9aee6-143">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="9aee6-144">A inicialização do plug-in do WMR também inicia o SteamVR.</span><span class="sxs-lookup"><span data-stu-id="9aee6-144">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="9aee6-145">Verifique se o headset do WMR está conectado.</span><span class="sxs-lookup"><span data-stu-id="9aee6-145">Make sure the WMR headset is plugged in.</span></span>

    ![Pesquisa de plug-in do WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="9aee6-147">Selecione **Iniciar** no Plug-in do Windows Mixed Reality para SteamVR.</span><span class="sxs-lookup"><span data-stu-id="9aee6-147">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![Plug-in do WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="9aee6-149">O SteamVR e o plug-in do WMR serão iniciados e uma nova janela de status de acompanhamento do headset do WMR será exibida.</span><span class="sxs-lookup"><span data-stu-id="9aee6-149">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="9aee6-150">Para obter mais informações, acesse a [documentação do Windows Mixed Reality para Steam](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="9aee6-150">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Aparência da inicialização do WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="9aee6-152">No Unity, com a cena do MRTK aberta, acesse **Arquivo > Configurações de Build**</span><span class="sxs-lookup"><span data-stu-id="9aee6-152">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="9aee6-153">Compilar a cena</span><span class="sxs-lookup"><span data-stu-id="9aee6-153">Build the scene</span></span>
    - <span data-ttu-id="9aee6-154">Selecione **Adicionar Cena Aberta**</span><span class="sxs-lookup"><span data-stu-id="9aee6-154">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="9aee6-155">Verifique se a Plataforma é **Autônomo**</span><span class="sxs-lookup"><span data-stu-id="9aee6-155">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="9aee6-156">Selecione **Compilar**</span><span class="sxs-lookup"><span data-stu-id="9aee6-156">Select **Build**</span></span>
    - <span data-ttu-id="9aee6-157">Escolha a localização do novo build no Explorador de Arquivos</span><span class="sxs-lookup"><span data-stu-id="9aee6-157">Choose the location for the new build in File Explorer</span></span>

    ![Configurações de Build para Autônomo](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="9aee6-159">Um executável do Unity será criado. Para iniciar seu aplicativo, selecione o executável do Unity no Explorador de Arquivos.</span><span class="sxs-lookup"><span data-stu-id="9aee6-159">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Unity no Explorador de Arquivos](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="9aee6-161">Confira também</span><span class="sxs-lookup"><span data-stu-id="9aee6-161">See also</span></span>

- [<span data-ttu-id="9aee6-162">Suporte para Android e iOS</span><span class="sxs-lookup"><span data-stu-id="9aee6-162">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="9aee6-163">Suporte para Leap Motion</span><span class="sxs-lookup"><span data-stu-id="9aee6-163">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="9aee6-164">Como detectar funcionalidades de plataforma</span><span class="sxs-lookup"><span data-stu-id="9aee6-164">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)