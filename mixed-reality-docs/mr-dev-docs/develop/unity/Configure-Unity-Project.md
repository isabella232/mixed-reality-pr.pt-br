---
title: Configurar seu projeto sem MRTK
description: Saiba como configurar um novo projeto do Unity para o Windows Mixed Reality sem o Mixed Reality Toolkit.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, realidade mista, desenvolvimento, introdução, novo projeto, realidade do Windows Mixed, UWP, XR, desempenho
ms.openlocfilehash: c496dc415ff09eea3015b5195e131554c43a98f1
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110254"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="8bdaf-104">Como configurar seu projeto sem o MRTK</span><span class="sxs-lookup"><span data-stu-id="8bdaf-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="8bdaf-105">O Windows Mixed Reality (WMR) é uma plataforma da Microsoft introduzida como parte do sistema operacional Windows 10.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="8bdaf-106">A plataforma WMR permite que você crie aplicativos que processam conteúdo digital em dispositivos de vídeo Holographic e VR.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="8bdaf-107">Embora a Microsoft e a Comunidade tenham criado ferramentas de código aberto, como o [MRTK (Kit de ferramentas de realidade misturada)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) , que configurará automaticamente o ambiente WMR, muitos desenvolvedores desejam criar suas experiências desde o início.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-107">While Microsoft and the community have created open source tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="8bdaf-108">A documentação a seguir demonstrará como configurar corretamente um projeto para o desenvolvimento de realidade misturada se você estiver usando MRTK ou não.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="8bdaf-109">As configurações que você precisa alterar são divididas em duas categorias: configurações por projeto e configurações por cena.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="8bdaf-110">Você sempre pode importar MRTK posteriormente, portanto, não há penalidade para passar a rota manual primeiro.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="8bdaf-111">Se você escolher a configuração manual do WMR, as configurações que você precisa alterar serão divididas em duas categorias: por projeto e por cena.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="8bdaf-112">Configurações por projeto</span><span class="sxs-lookup"><span data-stu-id="8bdaf-112">Per-project settings</span></span>

<span data-ttu-id="8bdaf-113">Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="8bdaf-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

<span data-ttu-id="8bdaf-115">Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="8bdaf-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="8bdaf-116">Selecione **arquivo > configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="8bdaf-117">Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="8bdaf-118">Defina a **Arquitetura** como **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="8bdaf-119">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="8bdaf-120">Defina o **Tipo de Build** como **D3D**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="8bdaf-121">Defina o **SDK do UWP** como **Último instalado**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="8bdaf-122">Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar</span><span class="sxs-lookup"><span data-stu-id="8bdaf-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](images/wmr-config-img-4.png)

<span data-ttu-id="8bdaf-124">Depois de definir sua plataforma, você precisa deixar que o Unity saiba criar uma [exibição de imersão](../../design/app-views.md) em vez de uma exibição 2D quando exportada.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="8bdaf-125">Para XRSDK</span><span class="sxs-lookup"><span data-stu-id="8bdaf-125">For XRSDK</span></span> 

1. <span data-ttu-id="8bdaf-126">No editor do Unity, navegue até **editar > configurações do projeto** e selecione **Gerenciamento de plugin XR**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="8bdaf-127">Selecione **instalar o gerenciamento de plugin XR**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-127">Select **Install XR Plugin Management**</span></span>

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](images/wmr-config-img-5.png)

3. <span data-ttu-id="8bdaf-129">Selecione **inicializar XR na inicialização** e **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](images/wmr-config-img-7.png)

4. <span data-ttu-id="8bdaf-131">Expanda a seção **Gerenciamento de plug-ins do XR** e selecione **Universal guia Configurações da plataforma Windows**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-131">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="8bdaf-132">Se você estiver usando o Unity 2020 ou posterior, verá as opções para verificar a realidade do **OpenXR** ou do **Windows Mixed**.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-132">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="8bdaf-133">Você pode escolher qualquer tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-133">You can choose either runtime.</span></span>  <span data-ttu-id="8bdaf-134">Se você estiver desenvolvendo especificamente para o HoloLens 2 ou para a HP reverbs G2 e decidir experimentar o **OpenXR**, selecione a caixa OpenXR e examine nosso guia para [usar o plug-in de realidade misturada do OpenXR para](openxr-getting-started.md) que o Unity se prepare corretamente para esses dispositivos antes de retornar a este tutorial</span><span class="sxs-lookup"><span data-stu-id="8bdaf-134">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="8bdaf-135">A partir do Unity 2020 LTS, a Microsoft está adotando o desenvolvimento com o OpenXR.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-135">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="8bdaf-136">À medida que migramos para esse caminho, no Unity 2021,1, o plug-in do Windows XR será preterido e removido em 2021,2, tornando OpenXR o único caminho com suporte.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-136">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="8bdaf-137">Você pode encontrar mais informações sobre como [usar o plug-in OpenXR de realidade misturada](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="8bdaf-137">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="8bdaf-138">Se você decidir escolher o plug-in de **realidade mista do Windows** , marque todas as caixas e defina o **modo de envio de profundidade** como profundidade de **16 bits**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-138">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção realidade mista do Windows realçada](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="8bdaf-140">Para o XR herdado</span><span class="sxs-lookup"><span data-stu-id="8bdaf-140">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="8bdaf-141">O XR herdado é preterido no Unity 2019 e removido no Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-141">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="8bdaf-142">Abra **as configurações do Player...** nas **configurações de compilação... e expandir o grupo de** **configurações XR**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-142">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="8bdaf-143">Na seção **configurações de XR** , selecione **realidade virtual com suporte** para adicionar a lista de dispositivos de realidade virtual</span><span class="sxs-lookup"><span data-stu-id="8bdaf-143">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="8bdaf-144">Definir o **formato de profundidade** como profundidade de **16 bits** e habilitar o **compartilhamento de buffer de profundidade**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-144">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="8bdaf-145">Definir **modo de renderização estéreo** para **instância de passagem única**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-145">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="8bdaf-146">Selecione **WSA Holographic Remoting com suporte** se você quiser usar o Holographic de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="8bdaf-146">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção Configurações do Player realçada](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="8bdaf-148">Atualizando o manifesto</span><span class="sxs-lookup"><span data-stu-id="8bdaf-148">Updating the manifest</span></span>

<span data-ttu-id="8bdaf-149">Seu aplicativo agora pode manipular a renderização Holographic e a entrada espacial.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-149">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="8bdaf-150">No entanto, seu aplicativo precisa declarar os recursos apropriados em seu manifesto para aproveitar determinadas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-150">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="8bdaf-151">Você pode encontrar os recursos de seus projetos acessando **configurações do Player > configurações para Plataforma Universal do Windows > configurações de publicação > recursos**.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-151">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="8bdaf-152">É recomendável que você faça as declarações de manifesto no Unity para incluí-las em todos os projetos futuros que você exportar.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-152">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="8bdaf-153">Os recursos aplicáveis para habilitar as APIs do Unity comumente usadas para realidade misturada são:</span><span class="sxs-lookup"><span data-stu-id="8bdaf-153">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="8bdaf-154">Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="8bdaf-154">Capability</span></span>  |  <span data-ttu-id="8bdaf-155">APIs que exigem capacidade</span><span class="sxs-lookup"><span data-stu-id="8bdaf-155">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="8bdaf-156">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="8bdaf-156">SpatialPerception</span></span>  |  <span data-ttu-id="8bdaf-157">SurfaceObserver (acesso a malhas de [mapeamento espacial](../../design/spatial-mapping.md) no HoloLens) &mdash; *nenhum recurso necessário para acompanhamento espacial geral do headset*</span><span class="sxs-lookup"><span data-stu-id="8bdaf-157">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="8bdaf-158">Integrada</span><span class="sxs-lookup"><span data-stu-id="8bdaf-158">WebCam</span></span>  |  <span data-ttu-id="8bdaf-159">VideoCapture e fotocaptura</span><span class="sxs-lookup"><span data-stu-id="8bdaf-159">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="8bdaf-160">PicturesLibrary / VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="8bdaf-160">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="8bdaf-161">VideoCapture, respectivamente (ao armazenar o conteúdo capturado)</span><span class="sxs-lookup"><span data-stu-id="8bdaf-161">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="8bdaf-162">Microfone</span><span class="sxs-lookup"><span data-stu-id="8bdaf-162">Microphone</span></span>  |  <span data-ttu-id="8bdaf-163">VideoCapture (ao capturar áudio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="8bdaf-163">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="8bdaf-164">InternetClient</span><span class="sxs-lookup"><span data-stu-id="8bdaf-164">InternetClient</span></span>  |  <span data-ttu-id="8bdaf-165">DictationRecognizer (e para usar o criador de perfil do Unity)</span><span class="sxs-lookup"><span data-stu-id="8bdaf-165">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="8bdaf-166">Configurações de qualidade</span><span class="sxs-lookup"><span data-stu-id="8bdaf-166">Quality settings</span></span>

<span data-ttu-id="8bdaf-167">O HoloLens tem uma GPU de classe móvel.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-167">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="8bdaf-168">Se seu aplicativo estiver direcionando para o HoloLens, você desejará começar com as configurações de qualidade em seu aplicativo ajustadas para um desempenho mais rápido, a fim de garantir que ela mantenha a taxa completa de quadros.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-168">If your app is targeting HoloLens, you'll want to start off with the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate.</span></span>  <span data-ttu-id="8bdaf-169">Depois que você tiver as suas próximas em seu desenvolvimento, poderá considerar upping as configurações de qualidade para encontrar o equilíbrio certo de qualidade e desempenho:</span><span class="sxs-lookup"><span data-stu-id="8bdaf-169">Once you have your are further along in your development you may consider upping the quality settings to find the right balance of quality and performance:</span></span> 

1. <span data-ttu-id="8bdaf-170">Selecione **Editar configurações do projeto > > qualidade**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-170">Select **Edit > Project Settings > Quality**</span></span> 
2. <span data-ttu-id="8bdaf-171">Selecione o **menu suspenso** sob o logotipo da  **Windows Store**   e selecione  **muito baixo**.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-171">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="8bdaf-172">Você saberá que a configuração foi aplicada corretamente quando a caixa na coluna da Windows Store e a linha muito baixa estiverem verdes</span><span class="sxs-lookup"><span data-stu-id="8bdaf-172">You'll know the setting is applied correctly when the box in the Windows Store column and Very Low row is green</span></span> 
3. <span data-ttu-id="8bdaf-173">Na seção **sombras**   , selecione **desabilitar sombras**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-173">In the **Shadows** section, select **Disable Shadows**</span></span> 

<span data-ttu-id="8bdaf-174">![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção Configurações de qualidade realçada](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="8bdaf-174">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="8bdaf-175">*Configurações de qualidade do Unity*</span><span class="sxs-lookup"><span data-stu-id="8bdaf-175">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="8bdaf-176">Configurações por cena</span><span class="sxs-lookup"><span data-stu-id="8bdaf-176">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="8bdaf-177">Configurações da câmera do Unity</span><span class="sxs-lookup"><span data-stu-id="8bdaf-177">Unity camera settings</span></span>

<span data-ttu-id="8bdaf-178">Com a **realidade virtual suportada** marcada, o componente da [câmera do Unity](camera-in-unity.md) lida com o [controle de cabeçalho e a renderização de estereoscópico](../platform-capabilities-and-apis/rendering.md).</span><span class="sxs-lookup"><span data-stu-id="8bdaf-178">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="8bdaf-179">Isso significa que não há necessidade de substituir o objeto da câmera principal por uma câmera personalizada.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-179">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="8bdaf-180">Se seu aplicativo estiver direcionando para o HoloLens especificamente, você precisará alterar algumas configurações para otimizar para as exibições transparentes do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-180">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="8bdaf-181">Essas configurações permitem que o conteúdo do Holographic seja mostrado ao mundo físico:</span><span class="sxs-lookup"><span data-stu-id="8bdaf-181">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="8bdaf-182">Na **hierarquia**, selecione a **câmera principal**</span><span class="sxs-lookup"><span data-stu-id="8bdaf-182">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="8bdaf-183">No painel de **inspetores** , defina a **posição** de transformação como **0, 0,** portanto, o local da cabeça do usuário começa na origem do Unity World.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-183">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="8bdaf-184">Alterar **sinalizadores claros** para **cor sólida**.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-184">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="8bdaf-185">Altere a cor do **plano de fundo** para **RGBA 0, 0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-185">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="8bdaf-186">O preto é renderizado como transparente no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-186">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="8bdaf-187">Alterar os **planos de recorte-próximo** ao [HoloLens recomendado](camera-in-unity.md#using-clipping-planes) 0,85 (metros).</span><span class="sxs-lookup"><span data-stu-id="8bdaf-187">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#using-clipping-planes) 0.85 (meters).</span></span>

<span data-ttu-id="8bdaf-188">![Captura de tela da guia Inspetor aberta no editor do Unity](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="8bdaf-188">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="8bdaf-189">*Configurações da câmera do Unity*</span><span class="sxs-lookup"><span data-stu-id="8bdaf-189">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bdaf-190">Se você excluir e criar uma nova câmera, verifique se a nova câmera está marcada como **MainCamera**.</span><span class="sxs-lookup"><span data-stu-id="8bdaf-190">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8bdaf-191">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="8bdaf-191">Next steps</span></span>

<span data-ttu-id="8bdaf-192">Agora que seu projeto está pronto, você pode começar a desenvolver sua experiência de realidade mista:</span><span class="sxs-lookup"><span data-stu-id="8bdaf-192">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="8bdaf-193">Adicionar [blocos de construção principais](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="8bdaf-193">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="8bdaf-194">Confira as [APIs e os recursos de plataforma](unity-development-overview.md#3-advanced-features) disponíveis</span><span class="sxs-lookup"><span data-stu-id="8bdaf-194">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="8bdaf-195">Saiba como [implantar seu aplicativo](../platform-capabilities-and-apis/using-visual-studio.md#)</span><span class="sxs-lookup"><span data-stu-id="8bdaf-195">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="8bdaf-196">Usar o [simulador de realidade misturada](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="8bdaf-196">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="8bdaf-197">Veja também</span><span class="sxs-lookup"><span data-stu-id="8bdaf-197">See also</span></span>
* [<span data-ttu-id="8bdaf-198">Instalar as ferramentas</span><span class="sxs-lookup"><span data-stu-id="8bdaf-198">Install the tools</span></span>](../install-the-tools.md)