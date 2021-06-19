---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394580"
---
# <a name="openxr"></a>[<span data-ttu-id="5dc22-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="5dc22-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="5dc22-102">Instale o plug-in OpenXR com o novo aplicativo de ferramenta de recursos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="5dc22-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="5dc22-103">Siga as [instruções de instalação e uso](../../welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR da realidade mista** na categoria Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="5dc22-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Janela de pacotes da ferramenta de recurso de realidade mista com plug-in aberto XR realçado](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="5dc22-105">Configurando seu destino de compilação</span><span class="sxs-lookup"><span data-stu-id="5dc22-105">Setting your build target</span></span>

<span data-ttu-id="5dc22-106">Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="5dc22-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

<span data-ttu-id="5dc22-108">Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="5dc22-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="5dc22-109">Selecione **arquivo > configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="5dc22-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="5dc22-110">Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="5dc22-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="5dc22-111">Defina a **Arquitetura** como **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="5dc22-111">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="5dc22-112">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="5dc22-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="5dc22-113">Defina o **Tipo de Build** como **D3D**</span><span class="sxs-lookup"><span data-stu-id="5dc22-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="5dc22-114">Defina o **SDK do UWP** como **Último instalado**</span><span class="sxs-lookup"><span data-stu-id="5dc22-114">Set **UWP SDK** to **Latest installed**</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="5dc22-116">Configurando o gerenciamento de plugin XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="5dc22-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="5dc22-117">Para definir OpenXR como o tempo de execução no Unity:</span><span class="sxs-lookup"><span data-stu-id="5dc22-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="5dc22-118">No editor do Unity, navegue até **editar > configurações do projeto**</span><span class="sxs-lookup"><span data-stu-id="5dc22-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="5dc22-119">Na lista de configurações, selecione **Gerenciamento de plugin XR**</span><span class="sxs-lookup"><span data-stu-id="5dc22-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="5dc22-120">Verifique as caixas **inicializar XR nas Startup** e **OpenXR**</span><span class="sxs-lookup"><span data-stu-id="5dc22-120">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="5dc22-121">Se estiver direcionando para o HoloLens 2, verifique se você está na plataforma UWP e selecione **conjunto de recursos do Microsoft HoloLens**</span><span class="sxs-lookup"><span data-stu-id="5dc22-121">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](../../images/openxr-img-05.png)

### <a name="optimization"></a><span data-ttu-id="5dc22-123">Optimization</span><span class="sxs-lookup"><span data-stu-id="5dc22-123">Optimization</span></span>

<span data-ttu-id="5dc22-124">Se você estiver desenvolvendo para o HoloLens 2, navegue até a **realidade misturada> OpenXR > aplicar as configurações de projeto recomendadas para o HoloLens 2** para obter melhor desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5dc22-124">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Captura de tela do item de menu da realidade misturada abrir com OpenXR selecionado](../../images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="5dc22-126">Se você vir um ícone de aviso amarelo ao lado de **plug-in OpenXR**, clique no ícone e selecione **corrigir tudo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5dc22-126">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="5dc22-127">O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="5dc22-127">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de tela da janela de validação do projeto OpenXR](../../images/openxr-img-06.png)

<span data-ttu-id="5dc22-129">Agora você está pronto para começar a desenvolver com o OpenXR no Unity!</span><span class="sxs-lookup"><span data-stu-id="5dc22-129">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="5dc22-130">Continue na próxima seção para aprender a usar os exemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5dc22-130">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="5dc22-131">Projetos de exemplo do Unity para OpenXR e HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5dc22-131">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="5dc22-132">Confira o [repositório de exemplos de realidade misturada OpenXR](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para projetos de exemplo de Unity mostrando como criar aplicativos de Unity para o HoloLens 2 ou headsets de realidade misturada usando o plug-in OpenXR de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="5dc22-132">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="5dc22-133">Windows XR</span><span class="sxs-lookup"><span data-stu-id="5dc22-133">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="5dc22-134">Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="5dc22-134">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

<span data-ttu-id="5dc22-136">Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="5dc22-136">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="5dc22-137">Selecione **arquivo > configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="5dc22-137">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="5dc22-138">Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="5dc22-138">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="5dc22-139">Defina a **Arquitetura** como **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="5dc22-139">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="5dc22-140">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="5dc22-140">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="5dc22-141">Defina o **Tipo de Build** como **D3D**</span><span class="sxs-lookup"><span data-stu-id="5dc22-141">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="5dc22-142">Defina o **SDK do UWP** como **Último instalado**</span><span class="sxs-lookup"><span data-stu-id="5dc22-142">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="5dc22-143">Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar</span><span class="sxs-lookup"><span data-stu-id="5dc22-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](../../images/wmr-config-img-4.png)

<span data-ttu-id="5dc22-145">Depois de definir sua plataforma, você precisa permitir que o Unity saiba como criar uma [exibição de imersão](../../../../design/app-views.md) em vez de uma exibição 2D quando exportada:</span><span class="sxs-lookup"><span data-stu-id="5dc22-145">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="5dc22-146">No editor do Unity, navegue até **editar > configurações do projeto** e selecione **Gerenciamento de plugin XR**</span><span class="sxs-lookup"><span data-stu-id="5dc22-146">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="5dc22-147">Selecione **instalar o gerenciamento de plugin XR**</span><span class="sxs-lookup"><span data-stu-id="5dc22-147">Select **Install XR Plugin Management**</span></span>

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="5dc22-149">Selecione **inicializar XR na inicialização** e **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="5dc22-149">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Captura de tela da janela Configurações do projeto aberta no editor do Unity com o gerenciamento de plugin XR realçado](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="5dc22-151">Expanda a seção **Gerenciamento de plug-ins do XR** e selecione **Universal guia Configurações da plataforma Windows**</span><span class="sxs-lookup"><span data-stu-id="5dc22-151">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="5dc22-152">Se você estiver usando o Unity 2020 ou posterior, verá as opções para verificar a realidade do **OpenXR** ou do **Windows Mixed**.</span><span class="sxs-lookup"><span data-stu-id="5dc22-152">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="5dc22-153">Você pode escolher qualquer tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5dc22-153">You can choose either runtime.</span></span>  <span data-ttu-id="5dc22-154">Se você estiver desenvolvendo especificamente para o HoloLens 2 ou para a HP reverbs G2 e decidir experimentar o **OpenXR**, selecione a caixa OpenXR e examine nosso guia para [usar o plug-in de realidade misturada do OpenXR para](../../openxr-getting-started.md) que o Unity se prepare corretamente para esses dispositivos antes de retornar a este tutorial</span><span class="sxs-lookup"><span data-stu-id="5dc22-154">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](../../openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="5dc22-155">A partir do Unity 2020 LTS, a Microsoft está adotando o desenvolvimento com o OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5dc22-155">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="5dc22-156">À medida que migramos para esse caminho, no Unity 2021,1, o plug-in do Windows XR será preterido e removido em 2021,2, tornando OpenXR o único caminho com suporte.</span><span class="sxs-lookup"><span data-stu-id="5dc22-156">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="5dc22-157">Você pode encontrar mais informações sobre como [usar o plug-in OpenXR de realidade misturada](../../openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="5dc22-157">You can find more information in [Using the Mixed Reality OpenXR plugin](../../openxr-getting-started.md).</span></span>

6. <span data-ttu-id="5dc22-158">Se você decidir escolher o plug-in de **realidade mista do Windows** , marque todas as caixas e defina o **modo de envio de profundidade** como profundidade de **16 bits**</span><span class="sxs-lookup"><span data-stu-id="5dc22-158">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção realidade mista do Windows realçada](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="5dc22-160">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="5dc22-160">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="5dc22-161">Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="5dc22-161">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](../../images/wmr-config-img-3.png)

<span data-ttu-id="5dc22-163">Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="5dc22-163">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="5dc22-164">Selecione **arquivo > configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="5dc22-164">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="5dc22-165">Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="5dc22-165">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="5dc22-166">Defina a **Arquitetura** como **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="5dc22-166">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="5dc22-167">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="5dc22-167">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="5dc22-168">Defina o **Tipo de Build** como **D3D**</span><span class="sxs-lookup"><span data-stu-id="5dc22-168">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="5dc22-169">Defina o **SDK do UWP** como **Último instalado**</span><span class="sxs-lookup"><span data-stu-id="5dc22-169">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="5dc22-170">Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar</span><span class="sxs-lookup"><span data-stu-id="5dc22-170">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](../../images/wmr-config-img-4.png)

<span data-ttu-id="5dc22-172">Depois de definir sua plataforma, você precisa deixar que o Unity saiba criar uma [exibição de imersão](../../../../design/app-views.md) em vez de uma exibição 2D quando exportada.</span><span class="sxs-lookup"><span data-stu-id="5dc22-172">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="5dc22-173">O XR herdado é preterido no Unity 2019 e removido no Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="5dc22-173">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="5dc22-174">Abra **as configurações do Player...** nas **configurações de compilação... e expandir o grupo de** **configurações XR**</span><span class="sxs-lookup"><span data-stu-id="5dc22-174">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="5dc22-175">Na seção **configurações de XR** , selecione **realidade virtual com suporte** para adicionar a lista de dispositivos de realidade virtual</span><span class="sxs-lookup"><span data-stu-id="5dc22-175">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="5dc22-176">Definir o **formato de profundidade** como profundidade de **16 bits** e habilitar o **compartilhamento de buffer de profundidade**</span><span class="sxs-lookup"><span data-stu-id="5dc22-176">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="5dc22-177">Definir **modo de renderização estéreo** para **instância de passagem única**</span><span class="sxs-lookup"><span data-stu-id="5dc22-177">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="5dc22-178">Selecione **WSA Holographic Remoting com suporte** se você quiser usar o Holographic de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="5dc22-178">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Captura de tela da janela Configurações do projeto abrir no editor do Unity com a seção Configurações do Player realçada](../../images/wmr-config-img-9.png)