---
ms.openlocfilehash: 639a96785e666cc3f5da3577ec3166f364753ed5
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603700"
---
# <a name="openxr"></a>[<span data-ttu-id="67e3f-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="67e3f-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="67e3f-102">Instale o plug-in OpenXR com o novo aplicativo de ferramenta de recursos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="67e3f-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="67e3f-103">Siga as [instruções de instalação e uso](../../welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR da realidade misturada** na categoria **suporte à plataforma** :</span><span class="sxs-lookup"><span data-stu-id="67e3f-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![Janela de pacotes da ferramenta de recurso de realidade mista com plug-in aberto XR realçado](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="67e3f-105">Configurando seu destino de compilação</span><span class="sxs-lookup"><span data-stu-id="67e3f-105">Setting your build target</span></span>

<span data-ttu-id="67e3f-106">Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="67e3f-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![captura de tela da janela criar Configurações abrir no editor do unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

<span data-ttu-id="67e3f-108">se você estiver direcionando HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="67e3f-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="67e3f-109">selecione **arquivo > Build Configurações...**</span><span class="sxs-lookup"><span data-stu-id="67e3f-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="67e3f-110">selecione **Plataforma Universal do Windows** na lista plataforma e selecione **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="67e3f-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="67e3f-111">Defina **Arquitetura** como **ARM64**</span><span class="sxs-lookup"><span data-stu-id="67e3f-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="67e3f-112">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="67e3f-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="67e3f-113">Defina **Tipo de Build** como **Projeto D3D**</span><span class="sxs-lookup"><span data-stu-id="67e3f-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="67e3f-114">Definir a **versão do SDK de destino** para a **última instalação**</span><span class="sxs-lookup"><span data-stu-id="67e3f-114">Set **Target SDK Version** to **Latest installed**</span></span>

![captura de tela da janela criar Configurações abrir no editor do unity com Plataforma Universal do Windows realçado](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="67e3f-116">Configurando o gerenciamento de plugin XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="67e3f-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="67e3f-117">Para definir OpenXR como o tempo de execução no Unity:</span><span class="sxs-lookup"><span data-stu-id="67e3f-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="67e3f-118">no Editor do Unity, navegue até **editar > Project Configurações**</span><span class="sxs-lookup"><span data-stu-id="67e3f-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="67e3f-119">na lista de Configurações, selecione **gerenciamento de Plugin XR** (já deve estar instalado se você instalou o plug-in OpenXR de realidade misturada usando MRFT)</span><span class="sxs-lookup"><span data-stu-id="67e3f-119">In the list of Settings, select **XR Plugin Management** (should already be installed if you installed the Mixed Reality OpenXR plugin using MRFT)</span></span>
3. <span data-ttu-id="67e3f-120">Marque a caixa **inicializar XR na inicialização**</span><span class="sxs-lookup"><span data-stu-id="67e3f-120">Check the **Initialize XR on Startup** box</span></span>
4. <span data-ttu-id="67e3f-121">se for destinado à área de trabalho VR, permaneça na guia autônoma do PC (o monitor) e marque as caixas de **conjunto de recursos** **OpenXR** e Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="67e3f-121">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
5. <span data-ttu-id="67e3f-122">se estiver direcionando HoloLens 2, alterne para a guia Plataforma Universal do Windows (o logotipo Windows) e selecione as caixas **conjunto de recursos** **OpenXR** e Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="67e3f-122">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="67e3f-124">Se você vir um ícone de aviso amarelo ao lado de **plug-in OpenXR**, clique no ícone e selecione **corrigir tudo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="67e3f-124">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="67e3f-125">O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="67e3f-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de tela da janela de validação do projeto OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="67e3f-127">Optimization</span><span class="sxs-lookup"><span data-stu-id="67e3f-127">Optimization</span></span>

<span data-ttu-id="67e3f-128">se você estiver desenvolvendo para o HoloLens 2, selecione a **realidade misturada > Project > aplicar configurações de projeto recomendadas para o item de menu HoloLens 2** para obter melhor desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="67e3f-128">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![Captura de tela do item de menu da realidade misturada abrir com OpenXR selecionado](../../images/openxr-img-08.png)

<span data-ttu-id="67e3f-130">Agora você está pronto para começar a desenvolver com o OpenXR no Unity!</span><span class="sxs-lookup"><span data-stu-id="67e3f-130">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="67e3f-131">Continue na próxima seção para aprender a usar os exemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="67e3f-131">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="67e3f-132">projetos de exemplo do Unity para OpenXR e HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="67e3f-132">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="67e3f-133">confira o [repositório de exemplos de realidade misturada do OpenXR](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para projetos de exemplo do unity mostrando como criar aplicativos do unity para o HoloLens 2 ou headsets de realidade misturada usando o plug-in OpenXR da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="67e3f-133">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="67e3f-134">Ou, se você estiver pronto para começar por conta própria em um projeto em branco, vá para o artigo de [configuração da câmera](../../camera-in-unity.md) .</span><span class="sxs-lookup"><span data-stu-id="67e3f-134">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="67e3f-135">Windows XR</span><span class="sxs-lookup"><span data-stu-id="67e3f-135">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="67e3f-136">o plug-in Windows XR foi preterido no unity 2021,1 e será removido no unity 2021,2.</span><span class="sxs-lookup"><span data-stu-id="67e3f-136">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="67e3f-137">Para o desenvolvimento do Unity 2020, a Microsoft recomenda o plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="67e3f-137">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="67e3f-138">Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="67e3f-138">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![captura de tela da janela criar Configurações abrir no editor do unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

<span data-ttu-id="67e3f-140">se você estiver direcionando HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="67e3f-140">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="67e3f-141">selecione **arquivo > Build Configurações...**</span><span class="sxs-lookup"><span data-stu-id="67e3f-141">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="67e3f-142">selecione **Plataforma Universal do Windows** na lista plataforma e selecione **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="67e3f-142">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="67e3f-143">Defina **Arquitetura** como **ARM64**</span><span class="sxs-lookup"><span data-stu-id="67e3f-143">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="67e3f-144">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="67e3f-144">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="67e3f-145">Defina **Tipo de Build** como **Projeto D3D**</span><span class="sxs-lookup"><span data-stu-id="67e3f-145">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="67e3f-146">Definir a **versão do SDK de destino** para a **última instalação**</span><span class="sxs-lookup"><span data-stu-id="67e3f-146">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="67e3f-147">Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar</span><span class="sxs-lookup"><span data-stu-id="67e3f-147">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![captura de tela da janela criar Configurações abrir no editor do unity com Plataforma Universal do Windows realçado](../../images/wmr-config-img-4.png)

<span data-ttu-id="67e3f-149">Depois de definir sua plataforma, você precisa permitir que o Unity saiba como criar uma [exibição de imersão](../../../../design/app-views.md) em vez de uma exibição 2D quando exportada:</span><span class="sxs-lookup"><span data-stu-id="67e3f-149">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="67e3f-150">no Editor do Unity, navegue até **editar > configurações de Project** e selecione **gerenciamento de Plugin XR**</span><span class="sxs-lookup"><span data-stu-id="67e3f-150">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="67e3f-151">Selecione **instalar o gerenciamento de plugin XR** se ele aparecer</span><span class="sxs-lookup"><span data-stu-id="67e3f-151">Select **Install XR Plugin Management** if it appears</span></span>

![captura de tela da janela Project Configurações aberta no editor do unity com o gerenciamento de Plugin XR realçado](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="67e3f-153">selecione **inicializar XR na inicialização** e **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="67e3f-153">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![captura de tela da janela configurações de Project abrir no editor do unity com o gerenciamento de Plugin XR realçado](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="67e3f-155">selecione a seção Windows Mixed Reality de **gerenciamento de Plug-in do XR**  >   , marque todas as caixas e defina o **formato do buffer** de profundidade para o **Buffer de profundidade 16 bits**</span><span class="sxs-lookup"><span data-stu-id="67e3f-155">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![captura de tela da janela configurações de Project abrir no editor do unity com a seção Windows Mixed Reality realçada](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="67e3f-157">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="67e3f-157">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="67e3f-158">O XR herdado é preterido no Unity 2019 e removido no Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="67e3f-158">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="67e3f-159">Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="67e3f-159">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![captura de tela da janela criar Configurações abrir no editor do unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

<span data-ttu-id="67e3f-161">se você estiver direcionando HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="67e3f-161">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="67e3f-162">selecione **arquivo > Build Configurações...**</span><span class="sxs-lookup"><span data-stu-id="67e3f-162">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="67e3f-163">selecione **Plataforma Universal do Windows** na lista plataforma e selecione **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="67e3f-163">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="67e3f-164">Defina **Arquitetura** como **ARM64**</span><span class="sxs-lookup"><span data-stu-id="67e3f-164">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="67e3f-165">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="67e3f-165">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="67e3f-166">Defina **Tipo de Build** como **Projeto D3D**</span><span class="sxs-lookup"><span data-stu-id="67e3f-166">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="67e3f-167">Definir a **versão do SDK de destino** para a **última instalação**</span><span class="sxs-lookup"><span data-stu-id="67e3f-167">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="67e3f-168">Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar</span><span class="sxs-lookup"><span data-stu-id="67e3f-168">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![captura de tela da janela criar Configurações abrir no editor do unity com Plataforma Universal do Windows realçado](../../images/wmr-config-img-4.png)

<span data-ttu-id="67e3f-170">Depois de definir sua plataforma, você precisa deixar que o Unity saiba criar uma [exibição de imersão](../../../../design/app-views.md) em vez de uma exibição 2D quando exportada.</span><span class="sxs-lookup"><span data-stu-id="67e3f-170">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="67e3f-171">abrir **Player Configurações...** do **Configurações de compilação... janela** e expandir o grupo de **Configurações XR**</span><span class="sxs-lookup"><span data-stu-id="67e3f-171">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="67e3f-172">na seção **Configurações do XR** , selecione **realidade virtual com suporte** para adicionar a lista de dispositivos de realidade virtual</span><span class="sxs-lookup"><span data-stu-id="67e3f-172">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="67e3f-173">Defina o **formato de profundidade** como profundidade de **16 bits** e marque **Habilitar compartilhamento de buffer de profundidade**</span><span class="sxs-lookup"><span data-stu-id="67e3f-173">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="67e3f-174">Defina **Modo de renderização estéreo** como **Instanciado de passagem única**</span><span class="sxs-lookup"><span data-stu-id="67e3f-174">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="67e3f-175">Selecione **WSA Holographic Remoting com suporte** se você quiser usar a comunicação remota do modo de reprodução do Holographic</span><span class="sxs-lookup"><span data-stu-id="67e3f-175">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![captura de tela da janela configurações do Project abrir no editor do unity com a seção configurações do Player realçada](../../images/wmr-config-img-9.png)
