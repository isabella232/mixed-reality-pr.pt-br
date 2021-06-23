---
ms.openlocfilehash: c965eb1b4edc91421e0b8b2e96893a04431aef6e
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112536030"
---
# <a name="openxr"></a>[<span data-ttu-id="24fd0-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="24fd0-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="24fd0-102">Instale o plug-in OpenXR com o novo aplicativo Ferramenta de Recursos de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="24fd0-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="24fd0-103">Siga as [instruções de instalação e uso](../../welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR de Realidade Misturada** na categoria **Suporte à** Plataforma:</span><span class="sxs-lookup"><span data-stu-id="24fd0-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![Janela de pacotes da Ferramenta de Recursos de Realidade Misturada com o plug-in xr aberto realçada](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="24fd0-105">Definindo seu destino de build</span><span class="sxs-lookup"><span data-stu-id="24fd0-105">Setting your build target</span></span>

<span data-ttu-id="24fd0-106">Se você estiver direcionando a VR da Área de Trabalho, sugerimos usar a Plataforma Autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="24fd0-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela Configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

<span data-ttu-id="24fd0-108">Se você estiver direcionando o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="24fd0-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="24fd0-109">Selecione **Arquivo > Configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="24fd0-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="24fd0-110">Selecione **Plataforma Universal do Windows** na lista Plataforma e selecione **Alternar Plataforma**</span><span class="sxs-lookup"><span data-stu-id="24fd0-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="24fd0-111">Defina **Arquitetura** como **ARM64**</span><span class="sxs-lookup"><span data-stu-id="24fd0-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="24fd0-112">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="24fd0-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="24fd0-113">Defina **Tipo de Build** como **Projeto D3D**</span><span class="sxs-lookup"><span data-stu-id="24fd0-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="24fd0-114">Definir **a versão do SDK de Destino** como a mais recente **instalada**</span><span class="sxs-lookup"><span data-stu-id="24fd0-114">Set **Target SDK Version** to **Latest installed**</span></span>

![Captura de tela da janela Configurações de Build aberta no editor do Unity Plataforma Universal do Windows realçada](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="24fd0-116">Configurando o gerenciamento de plug-in XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="24fd0-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="24fd0-117">Para definir o OpenXR como o runtime no Unity:</span><span class="sxs-lookup"><span data-stu-id="24fd0-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="24fd0-118">No Editor do Unity, navegue até **Editar configurações > projeto**</span><span class="sxs-lookup"><span data-stu-id="24fd0-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="24fd0-119">Na lista de Configurações, selecione Gerenciamento **de Plug-in XR**</span><span class="sxs-lookup"><span data-stu-id="24fd0-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="24fd0-120">Selecione **Instalar o Gerenciamento de Plug-in XR** se aparecer Captura de tela da janela Configurações do Projeto aberta no editor do Unity com o gerenciamento de plug-in ![ XR realçada](../../images/wmr-config-img-5.png)</span><span class="sxs-lookup"><span data-stu-id="24fd0-120">Select **Install XR Plugin Management** if it appears ![Screenshot of Project Settings window open in unity editor with XR Plugin management highlighted](../../images/wmr-config-img-5.png)</span></span>
4. <span data-ttu-id="24fd0-121">Marque a **caixa Inicializar XR na inicialização**</span><span class="sxs-lookup"><span data-stu-id="24fd0-121">Check the **Initialize XR on Startup** box</span></span>
5. <span data-ttu-id="24fd0-122">Se estiver direcionando a VR da Área de Trabalho, permaneça na guia COMPUTADOR Autônomo (o monitor) e marque as caixas de conjunto de recursos **OpenXR** **e Windows Mixed Reality aplicativo**</span><span class="sxs-lookup"><span data-stu-id="24fd0-122">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
6. <span data-ttu-id="24fd0-123">Se estiver direcionando o HoloLens 2, alternar para a guia Plataforma Universal do Windows  (o logotipo do Windows) e selecione as caixas de conjunto de Microsoft HoloLens **OpenXR** e</span><span class="sxs-lookup"><span data-stu-id="24fd0-123">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![Captura de tela do painel de configurações do projeto aberto no editor do Unity com o gerenciamento de plug-in XR realçada](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="24fd0-125">Se você vir um ícone de aviso amarelo ao lado de **Plug-in OpenXR,** clique no ícone e selecione **Corrigir Tudo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="24fd0-125">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="24fd0-126">O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="24fd0-126">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de tela da janela de validação do projeto OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="24fd0-128">Optimization</span><span class="sxs-lookup"><span data-stu-id="24fd0-128">Optimization</span></span>

<span data-ttu-id="24fd0-129">Se você estiver desenvolvendo para o HoloLens 2, selecione o item de menu > Projeto > Realidade Misturada > Aplicar configurações de projeto recomendadas para **o HoloLens 2** para obter um melhor desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24fd0-129">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![Captura de tela do item de menu de realidade misturada aberto com OpenXR selecionado](../../images/openxr-img-08.png)

<span data-ttu-id="24fd0-131">Agora você está pronto para começar a desenvolver com o OpenXR no Unity!</span><span class="sxs-lookup"><span data-stu-id="24fd0-131">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="24fd0-132">Continue na próxima seção para saber como usar os exemplos do OpenXR.</span><span class="sxs-lookup"><span data-stu-id="24fd0-132">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="24fd0-133">Projetos de exemplo do Unity para OpenXR e HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="24fd0-133">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="24fd0-134">Confira o repo de exemplos do [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para projetos de exemplo do Unity mostrando como criar aplicativos unity para headsets do HoloLens 2 ou realidade misturada usando o plug-in OpenXR de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="24fd0-134">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="24fd0-135">Ou, se você estiver pronto para começar por conta própria de um projeto em branco, vá para o [artigo Configuração da](../../camera-in-unity.md) câmera.</span><span class="sxs-lookup"><span data-stu-id="24fd0-135">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="24fd0-136">Windows XR</span><span class="sxs-lookup"><span data-stu-id="24fd0-136">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="24fd0-137">O plug-in do Windows XR foi preterido no Unity 2021.1 e será removido no Unity 2021.2.</span><span class="sxs-lookup"><span data-stu-id="24fd0-137">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="24fd0-138">Para o desenvolvimento do Unity 2020, a Microsoft recomenda o plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="24fd0-138">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="24fd0-139">Se você estiver direcionando a VR da Área de Trabalho, sugerimos usar a Plataforma Autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="24fd0-139">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela Configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

<span data-ttu-id="24fd0-141">Se você estiver direcionando o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="24fd0-141">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="24fd0-142">Selecione **Arquivo > Configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="24fd0-142">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="24fd0-143">Selecione **Plataforma Universal do Windows** na lista Plataforma e selecione **Alternar Plataforma**</span><span class="sxs-lookup"><span data-stu-id="24fd0-143">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="24fd0-144">Defina **Arquitetura** como **ARM64**</span><span class="sxs-lookup"><span data-stu-id="24fd0-144">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="24fd0-145">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="24fd0-145">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="24fd0-146">Defina **Tipo de Build** como **Projeto D3D**</span><span class="sxs-lookup"><span data-stu-id="24fd0-146">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="24fd0-147">Definir **a versão do SDK de Destino** como a mais recente **instalada**</span><span class="sxs-lookup"><span data-stu-id="24fd0-147">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="24fd0-148">Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar</span><span class="sxs-lookup"><span data-stu-id="24fd0-148">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de tela da janela Configurações de Build aberta no editor do Unity Plataforma Universal do Windows realçada](../../images/wmr-config-img-4.png)

<span data-ttu-id="24fd0-150">Depois de configurar sua plataforma, você precisa [](../../../../design/app-views.md) permitir que o Unity saiba para criar uma exibição imersiva em vez de uma exibição 2D quando exportada:</span><span class="sxs-lookup"><span data-stu-id="24fd0-150">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="24fd0-151">No Editor do Unity, navegue até **Editar > Do projeto** e selecione Gerenciamento de **Plug-in XR**</span><span class="sxs-lookup"><span data-stu-id="24fd0-151">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="24fd0-152">Selecione **Instalar o Gerenciamento de Plug-in XR** se ele aparecer</span><span class="sxs-lookup"><span data-stu-id="24fd0-152">Select **Install XR Plugin Management** if it appears</span></span>

![Captura de tela da janela Configurações do Projeto aberta no editor do Unity com o gerenciamento de plug-in XR realçada](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="24fd0-154">Selecione **Inicializar XR na Inicialização** **e Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="24fd0-154">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in XR realçada](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="24fd0-156">Selecione a seção Gerenciamento de **Plug-inS XR** Windows Mixed Reality, marque todas as caixas e de conjunto Formato do Buffer de Profundidade como  >   Buffer de **Profundidade 16 Bits** </span><span class="sxs-lookup"><span data-stu-id="24fd0-156">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![Captura de tela da janela Configurações do projeto aberta no editor do Unity Windows Mixed Reality seção realçada](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="24fd0-158">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="24fd0-158">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="24fd0-159">O XR herdado foi preterido no Unity 2019 e removido no Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="24fd0-159">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="24fd0-160">Se você estiver direcionando a VR da Área de Trabalho, sugerimos usar a Plataforma Autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="24fd0-160">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela Configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

<span data-ttu-id="24fd0-162">Se você estiver direcionando o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="24fd0-162">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="24fd0-163">Selecione **Arquivo > Configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="24fd0-163">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="24fd0-164">Selecione **Plataforma Universal do Windows** na lista Plataforma e selecione **Alternar Plataforma**</span><span class="sxs-lookup"><span data-stu-id="24fd0-164">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="24fd0-165">Defina **Arquitetura** como **ARM64**</span><span class="sxs-lookup"><span data-stu-id="24fd0-165">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="24fd0-166">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="24fd0-166">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="24fd0-167">Defina **Tipo de Build** como **Projeto D3D**</span><span class="sxs-lookup"><span data-stu-id="24fd0-167">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="24fd0-168">Definir **a versão do SDK de Destino** como a mais recente **instalada**</span><span class="sxs-lookup"><span data-stu-id="24fd0-168">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="24fd0-169">Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar</span><span class="sxs-lookup"><span data-stu-id="24fd0-169">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de tela da janela Configurações de Build aberta no editor do Unity Plataforma Universal do Windows realçada](../../images/wmr-config-img-4.png)

<span data-ttu-id="24fd0-171">Depois de configurar sua plataforma, você precisa permitir que o Unity saiba para criar uma [exibição](../../../../design/app-views.md) imersiva em vez de uma exibição 2D quando exportada.</span><span class="sxs-lookup"><span data-stu-id="24fd0-171">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="24fd0-172">Abra **Configurações do Player...** nas **Configurações de Build... janela** e expanda o **grupo Configurações XR**</span><span class="sxs-lookup"><span data-stu-id="24fd0-172">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="24fd0-173">Na seção **Configurações do XR,** selecione **Realidade Virtual Com** Suporte para adicionar a lista Dispositivos de Realidade Virtual</span><span class="sxs-lookup"><span data-stu-id="24fd0-173">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="24fd0-174">Definir **formato de profundidade** como profundidade de **16 bits e marque** Habilitar **Compartilhamento de Buffer de Profundidade**</span><span class="sxs-lookup"><span data-stu-id="24fd0-174">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="24fd0-175">Defina **Modo de renderização estéreo** como **Instanciado de passagem única**</span><span class="sxs-lookup"><span data-stu-id="24fd0-175">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="24fd0-176">Selecione **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span><span class="sxs-lookup"><span data-stu-id="24fd0-176">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com a seção Configurações do player realçada](../../images/wmr-config-img-9.png)
