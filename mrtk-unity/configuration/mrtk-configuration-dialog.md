---
title: Caixa de diálogo de configuração do MRTK
description: Configurar o MRTK no projeto do Unity
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Unity
ms.openlocfilehash: fd05f7f3b579522a1225e11b0411b255a43e1e3f
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345089"
---
# <a name="mrtk-project-configuration-dialog"></a><span data-ttu-id="a241d-104">Caixa de diálogo configuração do projeto MRTK</span><span class="sxs-lookup"><span data-stu-id="a241d-104">MRTK project configuration dialog</span></span>

<span data-ttu-id="a241d-105">A caixa de diálogo configuração do MRTK é exibida quando o Unity carrega um projeto e é determinado que uma ou mais opções de configuração precisam da atenção do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="a241d-105">The MRTK configuration dialog is displayed when Unity loads a project and it is determined that one or more configuration options needs the attention of the developer.</span></span>

![Aplicar ignorar mais tarde](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

<span data-ttu-id="a241d-107">Para aplicar as alterações, clique no botão **aplicar** .</span><span class="sxs-lookup"><span data-stu-id="a241d-107">To apply the changes, click the **Apply** button.</span></span> <span data-ttu-id="a241d-108">O botão **posterior** adiará as alterações até que o projeto seja recarregado em um momento futuro.</span><span class="sxs-lookup"><span data-stu-id="a241d-108">The **Later** button will defer the changes until the project is reloaded at a future time.</span></span>

> [!NOTE]
> <span data-ttu-id="a241d-109">A caixa de diálogo de configuração reaparecerá se uma ou mais das configurações recomendadas forem deixadas desmarcadas.</span><span class="sxs-lookup"><span data-stu-id="a241d-109">The configuration dialog will reappear if one or more of the recommended settings is left unchecked.</span></span> <span data-ttu-id="a241d-110">Para evitar que isso ocorra, aplique as opções desejadas e reinicie a caixa de diálogo por meio de utilitários do **Kit de ferramentas da realidade misturados**  >    >  **Configurar o projeto do Unity** e clique em **ignorar**.</span><span class="sxs-lookup"><span data-stu-id="a241d-110">To prevent this from occurring, apply the desired options, then relaunch the dialog via  **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click **Ignore**.</span></span> <span data-ttu-id="a241d-111">Isso impedirá que a caixa de diálogo de configuração reapareça automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a241d-111">This will prevent the configuration dialog from reappearing automatically.</span></span>

## <a name="common-settings"></a><span data-ttu-id="a241d-112">Configurações padrão</span><span class="sxs-lookup"><span data-stu-id="a241d-112">Common settings</span></span>

<span data-ttu-id="a241d-113">Todos os destinos de compilação compartilham uma coleção de opções comuns.</span><span class="sxs-lookup"><span data-stu-id="a241d-113">All build targets share a collection of common options.</span></span>

![Configurações Comuns](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a><span data-ttu-id="a241d-115">Forçar a serialização de ativos de texto e habilitar os metadados visíveis</span><span class="sxs-lookup"><span data-stu-id="a241d-115">Force text asset serialization and Enable visible meta files</span></span>

<span data-ttu-id="a241d-116">Essas configurações ajudam a simplificar o trabalho com projetos do Unity e sistemas de controle do código-fonte (por exemplo: git).</span><span class="sxs-lookup"><span data-stu-id="a241d-116">These settings help simplify working with Unity projects and source control systems (ex: Git).</span></span>

### <a name="enable-vr-supported"></a><span data-ttu-id="a241d-117">Habilitar VR com suporte</span><span class="sxs-lookup"><span data-stu-id="a241d-117">Enable VR supported</span></span>

<span data-ttu-id="a241d-118">**Unity 2018**</span><span class="sxs-lookup"><span data-stu-id="a241d-118">**Unity 2018**</span></span>

<span data-ttu-id="a241d-119">Configura a realidade virtual com suporte e as opções do SDK da realidade virtual nas **configurações do Player**  >  **XR Settings**.</span><span class="sxs-lookup"><span data-stu-id="a241d-119">Configures the Virtual Reality Supported and Virtual Reality SDK options in **Player Settings** > **XR Settings**.</span></span>

### <a name="set-single-pass-instanced-rendering-path"></a><span data-ttu-id="a241d-120">Definir caminho de renderização da instância única Pass</span><span class="sxs-lookup"><span data-stu-id="a241d-120">Set Single Pass Instanced rendering path</span></span>

<span data-ttu-id="a241d-121">Define as configurações do **Player**  >  **XR Settings**  >  **modo de renderização estéreo** para **passagem única instância**.</span><span class="sxs-lookup"><span data-stu-id="a241d-121">Configures the **Player Settings** > **XR Settings** > **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>

### <a name="set-default-spatial-awareness-layer"></a><span data-ttu-id="a241d-122">Definir camada de reconhecimento espacial padrão</span><span class="sxs-lookup"><span data-stu-id="a241d-122">Set default Spatial Awareness layer</span></span>

<span data-ttu-id="a241d-123">Registra o reconhecimento espacial como a camada 31 para habilitar a configuração fácil e consistente das opções Raycast e física.</span><span class="sxs-lookup"><span data-stu-id="a241d-123">Registers Spatial Awareness as layer 31 to enable easy and consistent configuration of raycast and physics options.</span></span>

### <a name="audio-spatializer"></a><span data-ttu-id="a241d-124">Spatializer de áudio</span><span class="sxs-lookup"><span data-stu-id="a241d-124">Audio spatializer</span></span>

<span data-ttu-id="a241d-125">Os spatializers de áudio são os componentes que desbloqueiam o poder do som espacial e do áudio posicional para tornar as experiências de realidade misturadas verdadeiramente imersivas.</span><span class="sxs-lookup"><span data-stu-id="a241d-125">Audio spatializers are the components that unlock the power of Spatial Sound and positional audio to make mixed reality experiences truly immersive.</span></span>

> [!NOTE]
> <span data-ttu-id="a241d-126">Definir o áudio spatializer como nenhum desabilitará os recursos de áudio posicional.</span><span class="sxs-lookup"><span data-stu-id="a241d-126">Setting the audio spatializer to None will disable positional audio features.</span></span>

#### <a name="common-spatializers"></a><span data-ttu-id="a241d-127">Spatializers comuns</span><span class="sxs-lookup"><span data-stu-id="a241d-127">Common spatializers</span></span>

- <span data-ttu-id="a241d-128">Spatializer Microsoft</span><span class="sxs-lookup"><span data-stu-id="a241d-128">Microsoft Spatializer</span></span>

<span data-ttu-id="a241d-129">A Microsoft forneceu spatializer que dá suporte à utilização de aceleração de hardware no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a241d-129">Microsoft provided spatializer that supports utilization of hardware acceleration on HoloLens 2.</span></span>

<span data-ttu-id="a241d-130">Esse spatializer está disponível por meio do [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) e do [GitHub](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="a241d-130">This spatializer is available via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) and [GitHub](https://github.com/microsoft/spatialaudio-unity).</span></span>

<span data-ttu-id="a241d-131">Mais detalhes sobre o Microsoft Spatializer podem ser encontrados na [documentação de som espacial](/windows/mixed-reality/spatial-sound-in-unity).</span><span class="sxs-lookup"><span data-stu-id="a241d-131">More details on Microsoft Spatializer can be found in the [Spatial Sound documentation](/windows/mixed-reality/spatial-sound-in-unity).</span></span>

- <span data-ttu-id="a241d-132">Spatializer MS HRTF</span><span class="sxs-lookup"><span data-stu-id="a241d-132">MS HRTF Spatializer</span></span>

<span data-ttu-id="a241d-133">Microsoft Windows spatializer que é fornecido pelo Unity como parte dos pacotes da plataforma Windows Mixed e da realidade do Windows XR.</span><span class="sxs-lookup"><span data-stu-id="a241d-133">Microsoft Windows spatializer that is provided by Unity as part of the Windows Mixed Reality and Windows XR Platform packages.</span></span>

- <span data-ttu-id="a241d-134">Áudio Resonance</span><span class="sxs-lookup"><span data-stu-id="a241d-134">Resonance Audio</span></span>

<span data-ttu-id="a241d-135">Um spatializer de plataforma cruzada do Google fornecido pelo Unity.</span><span class="sxs-lookup"><span data-stu-id="a241d-135">A cross platform spatializer from Google that is provided by Unity.</span></span>

<span data-ttu-id="a241d-136">Mais informações podem ser encontradas no site de [documentação de áudio do resonance](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) .</span><span class="sxs-lookup"><span data-stu-id="a241d-136">More information can be found on the [Resonance Audio documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) site.</span></span>

## <a name="universal-windows-platform-settings"></a><span data-ttu-id="a241d-137">Configurações de Plataforma Universal do Windows</span><span class="sxs-lookup"><span data-stu-id="a241d-137">Universal Windows Platform settings</span></span>

![Configurações de UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a><span data-ttu-id="a241d-139">Recursos de UWP</span><span class="sxs-lookup"><span data-stu-id="a241d-139">UWP Capabilities</span></span>

<span data-ttu-id="a241d-140">Habilita recursos de aplicativo específicos para Plataforma Universal do Windows aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a241d-140">Enables specific application capabilities for Universal Windows Platform application.</span></span> <span data-ttu-id="a241d-141">Esses recursos permitem que a plataforma informe e solicite permissão para habilitar a funcionalidade específica.</span><span class="sxs-lookup"><span data-stu-id="a241d-141">These capabilities enable the platform to inform and request permission to enable specific functionality.</span></span>

- <span data-ttu-id="a241d-142">Microfone</span><span class="sxs-lookup"><span data-stu-id="a241d-142">Microphone</span></span>

  <span data-ttu-id="a241d-143">Habilita a captura de som por meio do microfone.</span><span class="sxs-lookup"><span data-stu-id="a241d-143">Enables capturing sound via the microphone.</span></span>

- <span data-ttu-id="a241d-144">Cliente de Internet</span><span class="sxs-lookup"><span data-stu-id="a241d-144">Internet Client</span></span>

  <span data-ttu-id="a241d-145">Habilita o suporte para acessar recursos na Internet.</span><span class="sxs-lookup"><span data-stu-id="a241d-145">Enables support for accessing resources on the internet.</span></span>

- <span data-ttu-id="a241d-146">Percepção Espacial</span><span class="sxs-lookup"><span data-stu-id="a241d-146">Spatial Perception</span></span>

  <span data-ttu-id="a241d-147">Habilita o suporte para o uso do ambiente do mundo real.</span><span class="sxs-lookup"><span data-stu-id="a241d-147">Enables support for using the real-world environment.</span></span>

- <span data-ttu-id="a241d-148">Olhar de olho</span><span class="sxs-lookup"><span data-stu-id="a241d-148">Eye Gaze</span></span>

  <span data-ttu-id="a241d-149">**Unity 2019,3 e mais recente**</span><span class="sxs-lookup"><span data-stu-id="a241d-149">**Unity 2019.3 and newer**</span></span>

  <span data-ttu-id="a241d-150">Habilita o suporte para controlar o olhar de olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="a241d-150">Enables support for tracking the user's eye gaze.</span></span>

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a><span data-ttu-id="a241d-151">Evitar falha do Unity ' PlayerSettings. graphicsJob '</span><span class="sxs-lookup"><span data-stu-id="a241d-151">Avoid Unity 'PlayerSettings.graphicsJob' crash</span></span>

<span data-ttu-id="a241d-152">**Unity 2019,3 e mais recente**</span><span class="sxs-lookup"><span data-stu-id="a241d-152">**Unity 2019.3 and newer**</span></span>

<span data-ttu-id="a241d-153">Na versão mais recente do Unity 2019, quando "trabalhos gráficos" estiver habilitado, o aplicativo falhará quando for implantado em um HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a241d-153">In the latest version of Unity 2019, when "Graphics Jobs" is enabled, the app will crash when deployed to a HoloLens 2.</span></span>
<span data-ttu-id="a241d-154">Essa configuração é habilitada por padrão no Unity-enquanto esse bug existe (consulte o [bug do Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), o configurador usará como padrão a definição de trabalhos gráficos como ' false ' (permitindo que os aplicativos implantados no HoloLens 2 não falhem).</span><span class="sxs-lookup"><span data-stu-id="a241d-154">This setting is enabled by default in Unity - while this bug exists (see [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), the configurator will default to setting Graphics Jobs to 'false' (thus allowing apps deployed to HoloLens 2 not to crash).</span></span>

## <a name="android-settings"></a><span data-ttu-id="a241d-155">Configurações do Android</span><span class="sxs-lookup"><span data-stu-id="a241d-155">Android settings</span></span>

<span data-ttu-id="a241d-156">Definições de configuração para dar suporte a aplicativos AR em dispositivos com Android.</span><span class="sxs-lookup"><span data-stu-id="a241d-156">Configuration settings to support AR applications on Android powered devices.</span></span>

![Configurações do Android](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a><span data-ttu-id="a241d-158">Desabilitar renderização multi-threaded</span><span class="sxs-lookup"><span data-stu-id="a241d-158">Disable Multi-Threaded Rendering</span></span>

<span data-ttu-id="a241d-159">Desabilita **as configurações do Player**  >  **outras configurações**  >  **renderização multi-threaded** conforme exigido pelo suporte a ar do Android.</span><span class="sxs-lookup"><span data-stu-id="a241d-159">Disables **Player Settings** > **Other Settings** > **Multithreaded Rendering** as required by Android's AR support.</span></span>

### <a name="set-minimum-api-level"></a><span data-ttu-id="a241d-160">Definir nível mínimo de API</span><span class="sxs-lookup"><span data-stu-id="a241d-160">Set Minimum API Level</span></span>

<span data-ttu-id="a241d-161">Define o valor das **configurações do Player**  >  **outras configurações**  >  **nível mínimo de API** para impor os requisitos do sistema operacional para aplicativos ar.</span><span class="sxs-lookup"><span data-stu-id="a241d-161">Sets the value of **Player Settings** > **Other Settings** > **Minimum API Level** to enforce operating system requirements for AR applications.</span></span>

## <a name="ios-settings"></a><span data-ttu-id="a241d-162">Configurações do iOS</span><span class="sxs-lookup"><span data-stu-id="a241d-162">iOS settings</span></span>

<span data-ttu-id="a241d-163">Definições de configuração para dar suporte a aplicativos AR em dispositivos com iOS.</span><span class="sxs-lookup"><span data-stu-id="a241d-163">Configuration settings to support AR applications on iOS powered devices.</span></span>

![Configurações do iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a><span data-ttu-id="a241d-165">Definir versão do sistema operacional necessária</span><span class="sxs-lookup"><span data-stu-id="a241d-165">Set Required OS Version</span></span>

<span data-ttu-id="a241d-166">Define o valor das **configurações do Player**  >  **outras configurações** de  >  **destino versão mínima do IOS** para impor os requisitos do sistema operacional para aplicativos ar.</span><span class="sxs-lookup"><span data-stu-id="a241d-166">Sets the value of **Player Settings** > **Other Settings** > **Target minimum iOS Version** to enforce operating system requirements for AR applications.</span></span>

### <a name="set-required-architecture"></a><span data-ttu-id="a241d-167">Definir a arquitetura necessária</span><span class="sxs-lookup"><span data-stu-id="a241d-167">Set Required Architecture</span></span>

<span data-ttu-id="a241d-168">Define o valor das **configurações do Player**  >  **outra**  >  **arquitetura** de configurações para impor os requisitos de plataforma para aplicativos ar.</span><span class="sxs-lookup"><span data-stu-id="a241d-168">Sets the value of **Player Settings** > **Other Settings** > **Architecture** to enforce platform requirements for AR applications.</span></span>

### <a name="set-camera-usage-descriptions"></a><span data-ttu-id="a241d-169">Definir descrições de uso da câmera</span><span class="sxs-lookup"><span data-stu-id="a241d-169">Set Camera Usage Descriptions</span></span>

<span data-ttu-id="a241d-170">Define o valor das **configurações do Player**  >  **outras configurações**  >  **Descrição uso da câmera** usada para solicitar permissão para usar a câmera do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a241d-170">Sets the value of **Player Settings** > **Other Settings** > **Camera Usage Description** used to request permission to use the device's camera.</span></span>