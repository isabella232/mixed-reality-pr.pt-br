---
title: implantando em fones de ouvido HoloLens e WMR
description: Documentação sobre build e implantação de aplicativos em vários dispositivos.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Visual Studio
ms.openlocfilehash: 137e1b699e9a0cda1e8a454a6c3219b581fa71b4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176368"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a><span data-ttu-id="95810-104">implantando em fones de ouvido HoloLens e WMR</span><span class="sxs-lookup"><span data-stu-id="95810-104">Deploying to HoloLens and WMR headsets</span></span>

<span data-ttu-id="95810-105">há duas maneiras de implantar aplicativos criados com o MRTK em seu dispositivo windows, a UWP (universal Windows platform) e a plataforma autônoma.</span><span class="sxs-lookup"><span data-stu-id="95810-105">There are two ways to deploy applications built with MRTK to your windows device, the Univeral Windows Platform (UWP) and the Standalone Platform.</span></span> <span data-ttu-id="95810-106">os aplicativos criados para HoloLens 1 ou HoloLens 2 devem ter como alvo o uwp, enquanto os aplicativos criados para fones de ouvido WMR podem se concentrar em uwp ou autônomos.</span><span class="sxs-lookup"><span data-stu-id="95810-106">Applications built for HoloLens 1 or HoloLens 2 must target UWP, while applications built for WMR headsets may target either UWP or Standalone.</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="95810-107">criando e implantando MRTK para HoloLens 1, HoloLens 2 e WMR headsets (UWP)</span><span class="sxs-lookup"><span data-stu-id="95810-107">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="95810-108">as instruções sobre como criar e implantar para o **HoloLens 1** e o **HoloLens 2** (UWP) podem ser encontradas em [criando seu aplicativo para o dispositivo](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="95810-108">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="95810-109">Essas etapas também permitem que você implante em **headsets WMR**.</span><span class="sxs-lookup"><span data-stu-id="95810-109">These steps also allow you to deploy to **WMR headsets**.</span></span>

> [!NOTE]
> <span data-ttu-id="95810-110">ao implantar seu aplicativo em seu dispositivo no Visual Studio, você precisa configurar Visual Studio um pouco diferente dependendo do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="95810-110">When deploying your application to your device in Visual Studio, you need to configure Visual Studio slightly differently depending on the device.</span></span> <span data-ttu-id="95810-111">As configurações são as seguintes</span><span class="sxs-lookup"><span data-stu-id="95810-111">The configurations are as follows</span></span>
>
>| <span data-ttu-id="95810-112">Plataforma</span><span class="sxs-lookup"><span data-stu-id="95810-112">Platform</span></span> | <span data-ttu-id="95810-113">Configuração</span><span class="sxs-lookup"><span data-stu-id="95810-113">Configuration</span></span> | <span data-ttu-id="95810-114">Arquitetura</span><span class="sxs-lookup"><span data-stu-id="95810-114">Architecture</span></span> | <span data-ttu-id="95810-115">Destino</span><span class="sxs-lookup"><span data-stu-id="95810-115">Target</span></span> |
|---|---|---|---|
| <span data-ttu-id="95810-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="95810-116">HoloLens 2</span></span> | <span data-ttu-id="95810-117">Lançamento ou mestre</span><span class="sxs-lookup"><span data-stu-id="95810-117">Release or Master</span></span> | <span data-ttu-id="95810-118">ARM64</span><span class="sxs-lookup"><span data-stu-id="95810-118">ARM64</span></span> | <span data-ttu-id="95810-119">Dispositivo</span><span class="sxs-lookup"><span data-stu-id="95810-119">Device</span></span> |
| <span data-ttu-id="95810-120">HoloLens 1</span><span class="sxs-lookup"><span data-stu-id="95810-120">HoloLens 1</span></span> | <span data-ttu-id="95810-121">Lançamento ou mestre</span><span class="sxs-lookup"><span data-stu-id="95810-121">Release or Master</span></span> | <span data-ttu-id="95810-122">x86</span><span class="sxs-lookup"><span data-stu-id="95810-122">x86</span></span> | <span data-ttu-id="95810-123">Dispositivo</span><span class="sxs-lookup"><span data-stu-id="95810-123">Device</span></span> |
| <span data-ttu-id="95810-124">Headsets WMR</span><span class="sxs-lookup"><span data-stu-id="95810-124">WMR Headsets</span></span> | <span data-ttu-id="95810-125">Lançamento ou mestre</span><span class="sxs-lookup"><span data-stu-id="95810-125">Release or Master</span></span> | <span data-ttu-id="95810-126">x64</span><span class="sxs-lookup"><span data-stu-id="95810-126">x64</span></span> | <span data-ttu-id="95810-127">Computador Local</span><span class="sxs-lookup"><span data-stu-id="95810-127">Local Machine</span></span> |

<span data-ttu-id="95810-128">**Dica:** ao compilar para HoloLens 1, HoloLens 2 ou WMR, é recomendável que as configurações de compilação "versão do SDK de destino" e "versão mínima da plataforma" tenham a seguinte aparência na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="95810-128">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Janela de build](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="95810-130">As outras configurações podem ser diferentes (por exemplo, Configuração de Build/Arquitetura/Tipo de Build e outras sempre podem ser alteradas na solução do Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="95810-130">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="95810-131">Verifique se a lista suspensa "Versão do SDK de Destino" inclui a opção "10.0.18362.0". Se isso estiver ausente, [o último SDK do Windows](https://developer.microsoft.com/windows/downloads/windows-10-sdk) precisará ser instalado.</span><span class="sxs-lookup"><span data-stu-id="95810-131">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20192020-and-hololens"></a><span data-ttu-id="95810-132">Unity 2019/2020 e HoloLens</span><span class="sxs-lookup"><span data-stu-id="95810-132">Unity 2019/2020 and HoloLens</span></span>

<span data-ttu-id="95810-133">se um aplicativo HoloLens aparecer como um painel 2d no dispositivo, verifique se as configurações a seguir foram configuradas no Unity antes de implantar seu aplicativo UWP:</span><span class="sxs-lookup"><span data-stu-id="95810-133">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity before deploying your UWP app:</span></span>

<span data-ttu-id="95810-134">Se estiver usando o suporte interno do XR herdado (somente Unity 2019):</span><span class="sxs-lookup"><span data-stu-id="95810-134">If using the legacy built-in XR support (Unity 2019 only):</span></span>

1. <span data-ttu-id="95810-135">Acesse Editar > Configurações do Projeto, Player</span><span class="sxs-lookup"><span data-stu-id="95810-135">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="95810-136">Em **Configurações de XR** na guia UWP, verifique se a opção **Realidade Virtual Compatível** está habilitada e se o SDK do **Windows Mixed Reality** foi adicionado aos SDKs.</span><span class="sxs-lookup"><span data-stu-id="95810-136">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="95810-137">Build e implantação no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="95810-137">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="95810-138">se estiver usando os plug-ins OpenXR ou Windows XR:</span><span class="sxs-lookup"><span data-stu-id="95810-138">If using the OpenXR or Windows XR plugins:</span></span>

1. <span data-ttu-id="95810-139">Siga as etapas encontradas em [Introdução ao XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span><span class="sxs-lookup"><span data-stu-id="95810-139">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="95810-140">Verifique se o perfil de configuração é o **DefaultXRSDKConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="95810-140">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="95810-141">Acesse **Editar > Configurações de Projeto, Gerenciamento do Plug-in de XR** e verifique se o **Windows Mixed Reality** está habilitado.</span><span class="sxs-lookup"><span data-stu-id="95810-141">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="95810-142">Build e implantação no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="95810-142">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="95810-143">Se você estiver usando o Unity 2019.3.x, selecione **ARM64** e não **ARM** como a arquitetura de build no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="95810-143">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="95810-144">Com as configurações padrão do Unity no Unity 2019.3.x, um aplicativo do Unity não será implantado em um HoloLens se o ARM for selecionado devido a um bug do Unity.</span><span class="sxs-lookup"><span data-stu-id="95810-144">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span>
>
> <span data-ttu-id="95810-145">Se a arquitetura do ARM for necessária, acesse **Editar > Configurações de Projeto, Player** e, no menu **Outras Configurações**, desabilite **Trabalhos Gráficos**.</span><span class="sxs-lookup"><span data-stu-id="95810-145">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="95810-146">A desabilitação de **Trabalhos Gráficos** permitirá que o aplicativo seja implantado com a arquitetura de build do ARM para o Unity 2019.3.x, mas o ARM64 é recomendado.</span><span class="sxs-lookup"><span data-stu-id="95810-146">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>
>
> <span data-ttu-id="95810-147">Esse problema foi corrigido no Unity 2019,4 e no Unity 2020,3.</span><span class="sxs-lookup"><span data-stu-id="95810-147">This issue was fixed in Unity 2019.4 and Unity 2020.3.</span></span>

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a><span data-ttu-id="95810-148">Criando e implantando MRTK em headsets WMR (autônomos)</span><span class="sxs-lookup"><span data-stu-id="95810-148">Building and deploying MRTK to WMR Headsets (Standalone)</span></span>

<span data-ttu-id="95810-149">Compilações autônomas de MRTK podem ser usadas em headsets WMR.</span><span class="sxs-lookup"><span data-stu-id="95810-149">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="95810-150">Um build autônomo para um headset do WMR exige as seguintes etapas extras:</span><span class="sxs-lookup"><span data-stu-id="95810-150">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="95810-151">O SDK de XR do Unity também dá suporte ao WMR nativo em builds autônomos, mas não exige o plug-in do SteamVR ou do WMR.</span><span class="sxs-lookup"><span data-stu-id="95810-151">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="95810-152">Essas etapas são necessárias para o XR herdado do Unity.</span><span class="sxs-lookup"><span data-stu-id="95810-152">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="95810-153">Instale o [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="95810-153">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="95810-154">Instale o [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="95810-154">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="95810-155">Instale o [Plug-in do WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="95810-155">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="95810-156">Como usar o plug-in do WMR</span><span class="sxs-lookup"><span data-stu-id="95810-156">How to use WMR plugin</span></span>

1. <span data-ttu-id="95810-157">Abra o Steam e procure o Plug-in do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="95810-157">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="95810-158">Verifique se o SteamVR está fechado antes de iniciar o Plug-in do WMR.</span><span class="sxs-lookup"><span data-stu-id="95810-158">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="95810-159">A inicialização do plug-in do WMR também inicia o SteamVR.</span><span class="sxs-lookup"><span data-stu-id="95810-159">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="95810-160">Verifique se o headset do WMR está conectado.</span><span class="sxs-lookup"><span data-stu-id="95810-160">Make sure the WMR headset is plugged in.</span></span>

    ![Pesquisa de plug-in do WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="95810-162">Selecione **Iniciar** no Plug-in do Windows Mixed Reality para SteamVR.</span><span class="sxs-lookup"><span data-stu-id="95810-162">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![Plug-in do WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="95810-164">O SteamVR e o plug-in do WMR serão iniciados e uma nova janela de status de acompanhamento do headset do WMR será exibida.</span><span class="sxs-lookup"><span data-stu-id="95810-164">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="95810-165">Para obter mais informações, acesse a [documentação do Windows Mixed Reality para Steam](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="95810-165">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Aparência da inicialização do WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="95810-167">No Unity, com a cena do MRTK aberta, acesse **Arquivo > Configurações de Build**</span><span class="sxs-lookup"><span data-stu-id="95810-167">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="95810-168">Compilar a cena</span><span class="sxs-lookup"><span data-stu-id="95810-168">Build the scene</span></span>
    - <span data-ttu-id="95810-169">Selecione **Adicionar Cena Aberta**</span><span class="sxs-lookup"><span data-stu-id="95810-169">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="95810-170">Verifique se a Plataforma é **Autônomo**</span><span class="sxs-lookup"><span data-stu-id="95810-170">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="95810-171">Selecione **Compilar**</span><span class="sxs-lookup"><span data-stu-id="95810-171">Select **Build**</span></span>
    - <span data-ttu-id="95810-172">Escolha a localização do novo build no Explorador de Arquivos</span><span class="sxs-lookup"><span data-stu-id="95810-172">Choose the location for the new build in File Explorer</span></span>

    ![Configurações de Build para Autônomo](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="95810-174">Um executável do Unity será criado. Para iniciar seu aplicativo, selecione o executável do Unity no Explorador de Arquivos.</span><span class="sxs-lookup"><span data-stu-id="95810-174">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Unity no Explorador de Arquivos](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="95810-176">Confira também</span><span class="sxs-lookup"><span data-stu-id="95810-176">See also</span></span>

- [<span data-ttu-id="95810-177">Suporte para Android e iOS</span><span class="sxs-lookup"><span data-stu-id="95810-177">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="95810-178">Suporte para Leap Motion</span><span class="sxs-lookup"><span data-stu-id="95810-178">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="95810-179">Como detectar funcionalidades de plataforma</span><span class="sxs-lookup"><span data-stu-id="95810-179">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)
