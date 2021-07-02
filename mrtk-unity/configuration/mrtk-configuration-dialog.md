---
title: Caixa de diálogo de configuração do MRTK
description: Configurar o MRTK no Unity Project
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Unity
ms.openlocfilehash: 50a0f40723c05e96f79eefab933942044afb22f1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177332"
---
# <a name="mrtk-configuration-dialog"></a><span data-ttu-id="b20f9-104">Caixa de diálogo de configuração do MRTK</span><span class="sxs-lookup"><span data-stu-id="b20f9-104">MRTK configuration dialog</span></span>

<span data-ttu-id="b20f9-105">A caixa de diálogo configuração do MRTK é exibida quando o Unity carrega um projeto e é determinado que uma ou mais opções de configuração precisam da atenção do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="b20f9-105">The MRTK configuration dialog is displayed when Unity loads a project and it is determined that one or more configuration options needs the attention of the developer.</span></span>

![Aplicar ignorar mais tarde](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

<span data-ttu-id="b20f9-107">Para aplicar as alterações, clique no botão **aplicar** .</span><span class="sxs-lookup"><span data-stu-id="b20f9-107">To apply the changes, click the **Apply** button.</span></span> <span data-ttu-id="b20f9-108">O botão **posterior** adiará as alterações até que o projeto seja recarregado em um momento futuro.</span><span class="sxs-lookup"><span data-stu-id="b20f9-108">The **Later** button will defer the changes until the project is reloaded at a future time.</span></span>

> [!NOTE]
> <span data-ttu-id="b20f9-109">A caixa de diálogo de configuração reaparecerá se uma ou mais das configurações recomendadas forem deixadas desmarcadas.</span><span class="sxs-lookup"><span data-stu-id="b20f9-109">The configuration dialog will reappear if one or more of the recommended settings is left unchecked.</span></span> <span data-ttu-id="b20f9-110">para evitar que isso ocorra, aplique as opções desejadas e reinicie a caixa de diálogo por meio da **realidade misturada Toolkit**  >  **utilitários**  >  **Configure o Unity Project** e clique em **ignorar**.</span><span class="sxs-lookup"><span data-stu-id="b20f9-110">To prevent this from occurring, apply the desired options, then relaunch the dialog via  **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click **Ignore**.</span></span> <span data-ttu-id="b20f9-111">Isso impedirá que a caixa de diálogo de configuração reapareça automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b20f9-111">This will prevent the configuration dialog from reappearing automatically.</span></span>

## <a name="common-settings"></a><span data-ttu-id="b20f9-112">Configurações padrão</span><span class="sxs-lookup"><span data-stu-id="b20f9-112">Common settings</span></span>

<span data-ttu-id="b20f9-113">Todos os destinos de compilação compartilham uma coleção de opções comuns.</span><span class="sxs-lookup"><span data-stu-id="b20f9-113">All build targets share a collection of common options.</span></span>

![Configurações Comuns](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a><span data-ttu-id="b20f9-115">Forçar a serialização de ativos de texto e habilitar os metadados visíveis</span><span class="sxs-lookup"><span data-stu-id="b20f9-115">Force text asset serialization and Enable visible meta files</span></span>

<span data-ttu-id="b20f9-116">Essas configurações ajudam a simplificar o trabalho com projetos do Unity e sistemas de controle do código-fonte (por exemplo: git).</span><span class="sxs-lookup"><span data-stu-id="b20f9-116">These settings help simplify working with Unity projects and source control systems (ex: Git).</span></span>

### <a name="enable-vr-supported"></a><span data-ttu-id="b20f9-117">Habilitar VR com suporte</span><span class="sxs-lookup"><span data-stu-id="b20f9-117">Enable VR supported</span></span>

<span data-ttu-id="b20f9-118">**Unity 2018**</span><span class="sxs-lookup"><span data-stu-id="b20f9-118">**Unity 2018**</span></span>

<span data-ttu-id="b20f9-119">configura a realidade virtual com suporte e as opções do SDK da realidade virtual no **Player Configurações**  >  **XR Configurações**.</span><span class="sxs-lookup"><span data-stu-id="b20f9-119">Configures the Virtual Reality Supported and Virtual Reality SDK options in **Player Settings** > **XR Settings**.</span></span>

### <a name="set-single-pass-instanced-rendering-path"></a><span data-ttu-id="b20f9-120">Definir caminho de renderização da instância única Pass</span><span class="sxs-lookup"><span data-stu-id="b20f9-120">Set Single Pass Instanced rendering path</span></span>

<span data-ttu-id="b20f9-121">configura o modo de renderização estéreo do **Player Configurações**  >  **XR Configurações**  >   para **passagem única em instância**.</span><span class="sxs-lookup"><span data-stu-id="b20f9-121">Configures the **Player Settings** > **XR Settings** > **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>

### <a name="set-default-spatial-awareness-layer"></a><span data-ttu-id="b20f9-122">Definir camada de reconhecimento espacial padrão</span><span class="sxs-lookup"><span data-stu-id="b20f9-122">Set default Spatial Awareness layer</span></span>

<span data-ttu-id="b20f9-123">Registra o reconhecimento espacial como a camada 31 para habilitar a configuração fácil e consistente das opções Raycast e física.</span><span class="sxs-lookup"><span data-stu-id="b20f9-123">Registers Spatial Awareness as layer 31 to enable easy and consistent configuration of raycast and physics options.</span></span>

### <a name="audio-spatializer"></a><span data-ttu-id="b20f9-124">Spatializer de áudio</span><span class="sxs-lookup"><span data-stu-id="b20f9-124">Audio spatializer</span></span>

<span data-ttu-id="b20f9-125">Os spatializers de áudio são os componentes que desbloqueiam o poder do som espacial e do áudio posicional para tornar as experiências de realidade misturadas verdadeiramente imersivas.</span><span class="sxs-lookup"><span data-stu-id="b20f9-125">Audio spatializers are the components that unlock the power of Spatial Sound and positional audio to make mixed reality experiences truly immersive.</span></span>

> [!NOTE]
> <span data-ttu-id="b20f9-126">Definir o áudio spatializer como nenhum desabilitará os recursos de áudio posicional.</span><span class="sxs-lookup"><span data-stu-id="b20f9-126">Setting the audio spatializer to None will disable positional audio features.</span></span>

#### <a name="common-spatializers"></a><span data-ttu-id="b20f9-127">Spatializers comuns</span><span class="sxs-lookup"><span data-stu-id="b20f9-127">Common spatializers</span></span>

- <span data-ttu-id="b20f9-128">Spatializer Microsoft</span><span class="sxs-lookup"><span data-stu-id="b20f9-128">Microsoft Spatializer</span></span>

<span data-ttu-id="b20f9-129">a Microsoft forneceu spatializer que dá suporte à utilização de aceleração de hardware no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b20f9-129">Microsoft provided spatializer that supports utilization of hardware acceleration on HoloLens 2.</span></span>

<span data-ttu-id="b20f9-130">esse spatializer está disponível por meio de [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) e [GitHub](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="b20f9-130">This spatializer is available via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) and [GitHub](https://github.com/microsoft/spatialaudio-unity).</span></span>

<span data-ttu-id="b20f9-131">Mais detalhes sobre o Microsoft Spatializer podem ser encontrados na [documentação de som espacial](/windows/mixed-reality/spatial-sound-in-unity).</span><span class="sxs-lookup"><span data-stu-id="b20f9-131">More details on Microsoft Spatializer can be found in the [Spatial Sound documentation](/windows/mixed-reality/spatial-sound-in-unity).</span></span>

- <span data-ttu-id="b20f9-132">Spatializer MS HRTF</span><span class="sxs-lookup"><span data-stu-id="b20f9-132">MS HRTF Spatializer</span></span>

<span data-ttu-id="b20f9-133">o Microsoft Windows spatializer fornecido pelo Unity como parte dos pacotes de plataforma Windows Mixed Reality e Windows XR.</span><span class="sxs-lookup"><span data-stu-id="b20f9-133">Microsoft Windows spatializer that is provided by Unity as part of the Windows Mixed Reality and Windows XR Platform packages.</span></span>

- <span data-ttu-id="b20f9-134">Áudio Resonance</span><span class="sxs-lookup"><span data-stu-id="b20f9-134">Resonance Audio</span></span>

<span data-ttu-id="b20f9-135">Um spatializer de plataforma cruzada do Google fornecido pelo Unity.</span><span class="sxs-lookup"><span data-stu-id="b20f9-135">A cross platform spatializer from Google that is provided by Unity.</span></span>

<span data-ttu-id="b20f9-136">Mais informações podem ser encontradas no site de [documentação de áudio do resonance](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) .</span><span class="sxs-lookup"><span data-stu-id="b20f9-136">More information can be found on the [Resonance Audio documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) site.</span></span>

## <a name="universal-windows-platform-settings"></a><span data-ttu-id="b20f9-137">configurações de Plataforma Universal do Windows</span><span class="sxs-lookup"><span data-stu-id="b20f9-137">Universal Windows Platform settings</span></span>

![Configurações UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a><span data-ttu-id="b20f9-139">Recursos de UWP</span><span class="sxs-lookup"><span data-stu-id="b20f9-139">UWP Capabilities</span></span>

<span data-ttu-id="b20f9-140">habilita recursos de aplicativo específicos para Plataforma Universal do Windows aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b20f9-140">Enables specific application capabilities for Universal Windows Platform application.</span></span> <span data-ttu-id="b20f9-141">Esses recursos permitem que a plataforma informe e solicite permissão para habilitar a funcionalidade específica.</span><span class="sxs-lookup"><span data-stu-id="b20f9-141">These capabilities enable the platform to inform and request permission to enable specific functionality.</span></span>

- <span data-ttu-id="b20f9-142">Microfone</span><span class="sxs-lookup"><span data-stu-id="b20f9-142">Microphone</span></span>

  <span data-ttu-id="b20f9-143">Habilita a captura de som por meio do microfone.</span><span class="sxs-lookup"><span data-stu-id="b20f9-143">Enables capturing sound via the microphone.</span></span>

- <span data-ttu-id="b20f9-144">Cliente de Internet</span><span class="sxs-lookup"><span data-stu-id="b20f9-144">Internet Client</span></span>

  <span data-ttu-id="b20f9-145">Habilita o suporte para acessar recursos na Internet.</span><span class="sxs-lookup"><span data-stu-id="b20f9-145">Enables support for accessing resources on the internet.</span></span>

- <span data-ttu-id="b20f9-146">Percepção Espacial</span><span class="sxs-lookup"><span data-stu-id="b20f9-146">Spatial Perception</span></span>

  <span data-ttu-id="b20f9-147">Habilita o suporte para o uso do ambiente do mundo real.</span><span class="sxs-lookup"><span data-stu-id="b20f9-147">Enables support for using the real-world environment.</span></span>

- <span data-ttu-id="b20f9-148">Olhar de olho</span><span class="sxs-lookup"><span data-stu-id="b20f9-148">Eye Gaze</span></span>

  <span data-ttu-id="b20f9-149">**Unity 2019,3 e mais recente**</span><span class="sxs-lookup"><span data-stu-id="b20f9-149">**Unity 2019.3 and newer**</span></span>

  <span data-ttu-id="b20f9-150">Habilita o suporte para controlar o olhar de olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="b20f9-150">Enables support for tracking the user's eye gaze.</span></span>

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a><span data-ttu-id="b20f9-151">Evitar falha do Unity ' PlayerSettings. graphicsJob '</span><span class="sxs-lookup"><span data-stu-id="b20f9-151">Avoid Unity 'PlayerSettings.graphicsJob' crash</span></span>

<span data-ttu-id="b20f9-152">**Unity 2019,3 e mais recente**</span><span class="sxs-lookup"><span data-stu-id="b20f9-152">**Unity 2019.3 and newer**</span></span>

<span data-ttu-id="b20f9-153">na versão mais recente do Unity 2019, quando "trabalhos gráficos" estiver habilitado, o aplicativo falhará quando for implantado em um HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b20f9-153">In the latest version of Unity 2019, when "Graphics Jobs" is enabled, the app will crash when deployed to a HoloLens 2.</span></span>
<span data-ttu-id="b20f9-154">essa configuração é habilitada por padrão no Unity-enquanto esse bug existe (consulte o [bug do unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), o configurador usará como padrão a definição de trabalhos gráficos como ' false ' (permitindo assim que os aplicativos implantados no HoloLens 2 não falhem).</span><span class="sxs-lookup"><span data-stu-id="b20f9-154">This setting is enabled by default in Unity - while this bug exists (see [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), the configurator will default to setting Graphics Jobs to 'false' (thus allowing apps deployed to HoloLens 2 not to crash).</span></span>

## <a name="android-settings"></a><span data-ttu-id="b20f9-155">Configurações do Android</span><span class="sxs-lookup"><span data-stu-id="b20f9-155">Android settings</span></span>

<span data-ttu-id="b20f9-156">Definições de configuração para dar suporte a aplicativos AR em dispositivos com Android.</span><span class="sxs-lookup"><span data-stu-id="b20f9-156">Configuration settings to support AR applications on Android powered devices.</span></span>

![Configurações Android](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a><span data-ttu-id="b20f9-158">Desabilitar renderização multi-threaded</span><span class="sxs-lookup"><span data-stu-id="b20f9-158">Disable Multi-Threaded Rendering</span></span>

<span data-ttu-id="b20f9-159">desabilita o **Player Configurações**  >  **outro Configurações**  >  **renderização multi-threaded** , conforme exigido pelo suporte a AR do Android.</span><span class="sxs-lookup"><span data-stu-id="b20f9-159">Disables **Player Settings** > **Other Settings** > **Multithreaded Rendering** as required by Android's AR support.</span></span>

### <a name="set-minimum-api-level"></a><span data-ttu-id="b20f9-160">Definir nível mínimo de API</span><span class="sxs-lookup"><span data-stu-id="b20f9-160">Set Minimum API Level</span></span>

<span data-ttu-id="b20f9-161">define o valor do **Player Configurações**  >  **outro Configurações**  >  **nível de API mínimo** para impor os requisitos do sistema operacional para aplicativos AR.</span><span class="sxs-lookup"><span data-stu-id="b20f9-161">Sets the value of **Player Settings** > **Other Settings** > **Minimum API Level** to enforce operating system requirements for AR applications.</span></span>

## <a name="ios-settings"></a><span data-ttu-id="b20f9-162">Configurações do iOS</span><span class="sxs-lookup"><span data-stu-id="b20f9-162">iOS settings</span></span>

<span data-ttu-id="b20f9-163">Definições de configuração para dar suporte a aplicativos AR em dispositivos com iOS.</span><span class="sxs-lookup"><span data-stu-id="b20f9-163">Configuration settings to support AR applications on iOS powered devices.</span></span>

![Configurações do iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a><span data-ttu-id="b20f9-165">Definir versão do sistema operacional necessária</span><span class="sxs-lookup"><span data-stu-id="b20f9-165">Set Required OS Version</span></span>

<span data-ttu-id="b20f9-166">define o valor do **Player Configurações**  >  **outro Configurações**  >  **versão mínima do iOS de destino** para impor os requisitos do sistema operacional para aplicativos AR.</span><span class="sxs-lookup"><span data-stu-id="b20f9-166">Sets the value of **Player Settings** > **Other Settings** > **Target minimum iOS Version** to enforce operating system requirements for AR applications.</span></span>

### <a name="set-required-architecture"></a><span data-ttu-id="b20f9-167">Definir a arquitetura necessária</span><span class="sxs-lookup"><span data-stu-id="b20f9-167">Set Required Architecture</span></span>

<span data-ttu-id="b20f9-168">define o valor do **Player Configurações**  >  **outra**  >  **arquitetura** de Configurações para impor os requisitos de plataforma para aplicativos AR.</span><span class="sxs-lookup"><span data-stu-id="b20f9-168">Sets the value of **Player Settings** > **Other Settings** > **Architecture** to enforce platform requirements for AR applications.</span></span>

### <a name="set-camera-usage-descriptions"></a><span data-ttu-id="b20f9-169">Definir descrições de uso da câmera</span><span class="sxs-lookup"><span data-stu-id="b20f9-169">Set Camera Usage Descriptions</span></span>

<span data-ttu-id="b20f9-170">define o valor do **Player Configurações**  >  **outro Configurações**  >  **descrição de uso da câmera** usada para solicitar permissão para usar a câmera do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b20f9-170">Sets the value of **Player Settings** > **Other Settings** > **Camera Usage Description** used to request permission to use the device's camera.</span></span>
