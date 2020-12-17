---
title: Configurar seu projeto sem MRTK
description: Instruções sobre como configurar um projeto do Unity para o Windows Mixed Reality
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, realidade mista, desenvolvimento, introdução, novo projeto, realidade do Windows Mixed, UWP, XR, desempenho
ms.openlocfilehash: 1337001e8cc5c280c5789acbc8f10f40bca9b763
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613352"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="b2ca2-104">Configurando seu projeto sem MRTK</span><span class="sxs-lookup"><span data-stu-id="b2ca2-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="b2ca2-105">O Windows Mixed Reality (WMR) é uma plataforma da Microsoft introduzida como parte do sistema operacional Windows 10.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="b2ca2-106">A plataforma WMR permite que você crie aplicativos que processam conteúdo digital em dispositivos de vídeo Holographic e VR.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="b2ca2-107">Embora a Microsoft e a Comunidade tenham criado ferramentas abertas como o [MRTK (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) que configurará automaticamente o ambiente WMR, muitos desenvolvedores desejam criar suas experiências desde o início.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="b2ca2-108">A documentação a seguir demonstrará como configurar corretamente um projeto para o desenvolvimento de realidade misturada se você estiver usando MRTK ou não.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="b2ca2-109">As configurações que você precisa alterar são divididas em duas categorias: configurações por projeto e configurações por cena.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="b2ca2-110">Você sempre pode importar MRTK posteriormente, portanto, não há penalidade para passar a rota manual primeiro.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="b2ca2-111">Se você escolher a configuração manual do WMR, as configurações que você precisa alterar serão divididas em duas categorias: por projeto e por cena.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="b2ca2-112">Configurações por projeto</span><span class="sxs-lookup"><span data-stu-id="b2ca2-112">Per-project settings</span></span>

<span data-ttu-id="b2ca2-113">Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="b2ca2-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

<span data-ttu-id="b2ca2-115">Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="b2ca2-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="b2ca2-116">Selecione **arquivo > configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="b2ca2-117">Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="b2ca2-118">Definir a **arquitetura** para o **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="b2ca2-119">Definir o **dispositivo de destino** para o **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="b2ca2-120">Definir **tipo de compilação** como **D3D**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="b2ca2-121">Definir o **SDK do UWP** para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="b2ca2-122">Definir a **configuração de Build** como **Release** porque há problemas de desempenho conhecidos com a depuração</span><span class="sxs-lookup"><span data-stu-id="b2ca2-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](images/wmr-config-img-4.png)

<span data-ttu-id="b2ca2-124">Depois de definir sua plataforma, você precisa deixar que o Unity saiba criar uma [exibição de imersão](../../design/app-views.md) em vez de uma exibição 2D quando exportada.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="b2ca2-125">Para XRSDK</span><span class="sxs-lookup"><span data-stu-id="b2ca2-125">For XRSDK</span></span> 

1. <span data-ttu-id="b2ca2-126">No editor do Unity, navegue até **editar > configurações do projeto** e selecione **Gerenciamento de plugin XR**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="b2ca2-127">Selecione **instalar o gerenciamento de plugin XR**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-127">Select **Install XR Plugin Management**</span></span>

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](images/wmr-config-img-5.png)

3. <span data-ttu-id="b2ca2-129">Selecione **inicializar XR na inicialização** e **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](images/wmr-config-img-7.png)

4. <span data-ttu-id="b2ca2-131">Expanda a seção **Gerenciamento de plug-ins do XR** e selecione **realidade mista do Windows**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-131">Expand the **XR Plug-in Management** section and select **Windows Mixed Reality**</span></span>
5. <span data-ttu-id="b2ca2-132">Marque todas as caixas e defina o **modo de envio de profundidade** como profundidade de **16 bits**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-132">Check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção realidade mista do Windows realçada](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="b2ca2-134">Para o XR herdado</span><span class="sxs-lookup"><span data-stu-id="b2ca2-134">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="b2ca2-135">O XR herdado é preterido no Unity 2019 e removido no Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-135">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="b2ca2-136">Abra **as configurações do Player...** nas **configurações de compilação... e expandir o grupo de** **configurações XR**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-136">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="b2ca2-137">Na seção **configurações de XR** , selecione **realidade virtual com suporte** para adicionar a lista de dispositivos de realidade virtual</span><span class="sxs-lookup"><span data-stu-id="b2ca2-137">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="b2ca2-138">Definir o **formato de profundidade** como profundidade de **16 bits** e habilitar o **compartilhamento de buffer de profundidade**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-138">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="b2ca2-139">Definir **modo de renderização estéreo** para **instância de passagem única**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-139">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="b2ca2-140">Selecione **WSA Holographic Remoting com suporte** se você quiser usar o Holographic de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="b2ca2-140">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção Configurações do Player realçada](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="b2ca2-142">Atualizando o manifesto</span><span class="sxs-lookup"><span data-stu-id="b2ca2-142">Updating the manifest</span></span>

<span data-ttu-id="b2ca2-143">Seu aplicativo agora pode manipular a renderização Holographic e a entrada espacial.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-143">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="b2ca2-144">No entanto, seu aplicativo precisa declarar os recursos apropriados em seu manifesto para aproveitar determinadas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-144">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="b2ca2-145">Você pode encontrar os recursos de seus projetos acessando **configurações do Player > configurações para Plataforma Universal do Windows > configurações de publicação > recursos**.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-145">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="b2ca2-146">É recomendável que você faça as declarações de manifesto no Unity para incluí-las em todos os projetos futuros que você exportar.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-146">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="b2ca2-147">Os recursos aplicáveis para habilitar as APIs do Unity comumente usadas para realidade misturada são:</span><span class="sxs-lookup"><span data-stu-id="b2ca2-147">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="b2ca2-148">Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="b2ca2-148">Capability</span></span>  |  <span data-ttu-id="b2ca2-149">APIs que exigem capacidade</span><span class="sxs-lookup"><span data-stu-id="b2ca2-149">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="b2ca2-150">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="b2ca2-150">SpatialPerception</span></span>  |  <span data-ttu-id="b2ca2-151">SurfaceObserver (acesso a malhas de [mapeamento espacial](../../design/spatial-mapping.md) no HoloLens) &mdash; *nenhum recurso necessário para acompanhamento espacial geral do headset*</span><span class="sxs-lookup"><span data-stu-id="b2ca2-151">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="b2ca2-152">Integrada</span><span class="sxs-lookup"><span data-stu-id="b2ca2-152">WebCam</span></span>  |  <span data-ttu-id="b2ca2-153">VideoCapture e fotocaptura</span><span class="sxs-lookup"><span data-stu-id="b2ca2-153">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="b2ca2-154">PicturesLibrary / VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="b2ca2-154">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="b2ca2-155">VideoCapture, respectivamente (ao armazenar o conteúdo capturado)</span><span class="sxs-lookup"><span data-stu-id="b2ca2-155">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="b2ca2-156">Microfone</span><span class="sxs-lookup"><span data-stu-id="b2ca2-156">Microphone</span></span>  |  <span data-ttu-id="b2ca2-157">VideoCapture (ao capturar áudio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="b2ca2-157">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="b2ca2-158">InternetClient</span><span class="sxs-lookup"><span data-stu-id="b2ca2-158">InternetClient</span></span>  |  <span data-ttu-id="b2ca2-159">DictationRecognizer (e para usar o criador de perfil do Unity)</span><span class="sxs-lookup"><span data-stu-id="b2ca2-159">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="b2ca2-160">Configurações de qualidade</span><span class="sxs-lookup"><span data-stu-id="b2ca2-160">Quality settings</span></span>

<span data-ttu-id="b2ca2-161">O HoloLens tem uma GPU de classe móvel.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-161">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="b2ca2-162">Se seu aplicativo estiver direcionando para o HoloLens, você desejará que as configurações de qualidade em seu aplicativo sejam ajustadas para um desempenho mais rápido, a fim de garantir que ela mantenha a taxa completa de quadros:</span><span class="sxs-lookup"><span data-stu-id="b2ca2-162">If your app is targeting HoloLens, you'll want the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate:</span></span>

1. <span data-ttu-id="b2ca2-163">Selecione **Editar configurações do projeto > > qualidade**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-163">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="b2ca2-164">Selecione o **menu suspenso** sob o logotipo da **Windows Store** e selecione **muito baixo**.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-164">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="b2ca2-165">Você saberá que a configuração foi aplicada corretamente quando a caixa na coluna da Windows Store e a linha **muito baixa** estiverem verdes</span><span class="sxs-lookup"><span data-stu-id="b2ca2-165">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green</span></span>
3. <span data-ttu-id="b2ca2-166">Na seção **sombras** , selecione **desabilitar sombras**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-166">In the **Shadows** section, select **Disable Shadows**</span></span>

<span data-ttu-id="b2ca2-167">![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção Configurações de qualidade realçada](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="b2ca2-167">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="b2ca2-168">*Configurações de qualidade do Unity*</span><span class="sxs-lookup"><span data-stu-id="b2ca2-168">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="b2ca2-169">Configurações por cena</span><span class="sxs-lookup"><span data-stu-id="b2ca2-169">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="b2ca2-170">Configurações da câmera do Unity</span><span class="sxs-lookup"><span data-stu-id="b2ca2-170">Unity camera settings</span></span>

<span data-ttu-id="b2ca2-171">Com a **realidade virtual suportada** marcada, o componente da [câmera do Unity](camera-in-unity.md) lida com o [controle de cabeçalho e a renderização de estereoscópico](../platform-capabilities-and-apis/rendering.md).</span><span class="sxs-lookup"><span data-stu-id="b2ca2-171">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="b2ca2-172">Isso significa que não há necessidade de substituir o objeto da câmera principal por uma câmera personalizada.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-172">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="b2ca2-173">Se seu aplicativo estiver direcionando para o HoloLens especificamente, você precisará alterar algumas configurações para otimizar para as exibições transparentes do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-173">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="b2ca2-174">Essas configurações permitem que o conteúdo do Holographic seja mostrado ao mundo físico:</span><span class="sxs-lookup"><span data-stu-id="b2ca2-174">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="b2ca2-175">Na **hierarquia**, selecione a **câmera principal**</span><span class="sxs-lookup"><span data-stu-id="b2ca2-175">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="b2ca2-176">No painel de **inspetores** , defina a **posição** de transformação como **0, 0,** portanto, o local da cabeça do usuário começa na origem do Unity World.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-176">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="b2ca2-177">Alterar **sinalizadores claros** para **cor sólida**.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-177">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="b2ca2-178">Altere a cor do **plano de fundo** para **RGBA 0, 0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-178">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="b2ca2-179">O preto é renderizado como transparente no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-179">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="b2ca2-180">Alterar os **planos de recorte-próximo** ao [HoloLens recomendado](camera-in-unity.md#clip-planes) 0,85 (metros).</span><span class="sxs-lookup"><span data-stu-id="b2ca2-180">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="b2ca2-181">![Captura de tela da guia Inspetor aberta no editor do Unity](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="b2ca2-181">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="b2ca2-182">*Configurações da câmera do Unity*</span><span class="sxs-lookup"><span data-stu-id="b2ca2-182">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b2ca2-183">Se você excluir e criar uma nova câmera, verifique se a nova câmera está marcada como **MainCamera**.</span><span class="sxs-lookup"><span data-stu-id="b2ca2-183">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b2ca2-184">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b2ca2-184">Next steps</span></span>

<span data-ttu-id="b2ca2-185">Agora que seu projeto está pronto, você pode começar a desenvolver sua experiência de realidade mista:</span><span class="sxs-lookup"><span data-stu-id="b2ca2-185">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="b2ca2-186">Adicionar [blocos de construção principais](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="b2ca2-186">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="b2ca2-187">Confira as [APIs e os recursos de plataforma](unity-development-overview.md#3-platform-capabilities-and-apis) disponíveis</span><span class="sxs-lookup"><span data-stu-id="b2ca2-187">Check out available [platform capabilities and APIs](unity-development-overview.md#3-platform-capabilities-and-apis)</span></span>
* <span data-ttu-id="b2ca2-188">Saiba como [implantar seu aplicativo](../platform-capabilities-and-apis/using-visual-studio.md#deploying-an-app-to-your-local-pc---immersive-headset)</span><span class="sxs-lookup"><span data-stu-id="b2ca2-188">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#deploying-an-app-to-your-local-pc---immersive-headset)</span></span>
* <span data-ttu-id="b2ca2-189">Usar o [simulador de realidade misturada](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="b2ca2-189">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="b2ca2-190">Veja também</span><span class="sxs-lookup"><span data-stu-id="b2ca2-190">See also</span></span>
* [<span data-ttu-id="b2ca2-191">Instalar as ferramentas</span><span class="sxs-lookup"><span data-stu-id="b2ca2-191">Install the tools</span></span>](../install-the-tools.md)