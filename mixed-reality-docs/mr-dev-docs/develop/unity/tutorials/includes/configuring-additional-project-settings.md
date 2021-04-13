---
ms.openlocfilehash: 20cfe36028c6fe95cbdc79a1ea8884ed9c3cd5bd
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088596"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="a77bb-101">Unity 2019/2020 + Plug-in do Windows XR</span><span class="sxs-lookup"><span data-stu-id="a77bb-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="a77bb-102">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:</span><span class="sxs-lookup"><span data-stu-id="a77bb-102">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Caminho do menu Configurações de Projeto... do Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="a77bb-104">Na janela Configurações do Projeto, selecione **Gerenciamento de Plug-ins do XR** > **Instalar o Gerenciamento de Plug-ins do XR**, para instalar o Gerenciamento de Plug-ins do XR:</span><span class="sxs-lookup"><span data-stu-id="a77bb-104">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![Configurações de XR do Unity](../images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="a77bb-106">Depois que o Unity terminar de instalar o Gerenciamento de Plug-ins do XR.</span><span class="sxs-lookup"><span data-stu-id="a77bb-106">After Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="a77bb-107">Verifique se você está nas configurações da Plataforma Universal do Windows e marque as opções **Inicializar o XR ao Iniciar** e **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="a77bb-107">Ensure that you are in Universal Windows Platform settings and Check the **Initialize XR on Startup** and **Windows Mixed Reality** checkbox.</span></span>

![Configurações de XR do Unity com a adição do SDK do Windows Mixed Reality](../images/mr-learning-base/base-02-section5-step2-2-1.png)

<span data-ttu-id="a77bb-109">Depois que o Unity terminar de importar o SDK do Windows Mixed Reality, a janela Configurador de Projeto do MRTK deverá aparecer novamente.</span><span class="sxs-lookup"><span data-stu-id="a77bb-109">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="a77bb-110">Se ela não aparecer, use o menu do Unity para abri-la.</span><span class="sxs-lookup"><span data-stu-id="a77bb-110">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="a77bb-111">Na janela Configurador de Projeto do MRTK, use a lista suspensa **Espacializador de áudio** para selecionar o **Espacializador MS HRTF** e clique no botão **Aplicar** para aplicar a configuração:</span><span class="sxs-lookup"><span data-stu-id="a77bb-111">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Configurações de XR do Unity com o SDK do Windows Mixed Reality selecionado](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
><span data-ttu-id="a77bb-113">A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a77bb-113">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="a77bb-114">Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="a77bb-114">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="a77bb-115">Para saber mais sobre este tópico, veja os <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutoriais sobre áudio espacial</a>.</span><span class="sxs-lookup"><span data-stu-id="a77bb-115">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="a77bb-116">Na janela Configurações do Projeto, selecione **Gerenciamento de Plug-ins do XR** > **Windows Mixed Reality** > **Configurações de Runtime** e use a lista suspensa **Formato de Buffer de Profundidade** para selecionar a **profundidade de 16 bits**:</span><span class="sxs-lookup"><span data-stu-id="a77bb-116">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth:**</span></span>

![Configurações de publicação do Unity com o nome do pacote realçado](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> <span data-ttu-id="a77bb-118">A redução do formato de profundidade para 16 bits é opcional, mas ajuda a aprimorar o desempenho gráfico no projeto.</span><span class="sxs-lookup"><span data-stu-id="a77bb-118">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="a77bb-119">Para saber mais sobre este tópico, veja a seção <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank">Desempenho</a> do MRTK.</span><span class="sxs-lookup"><span data-stu-id="a77bb-119">To learn more about this topic, you can refer to the   <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="a77bb-120">Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="a77bb-120">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Configurações de publicação do Unity com o nome do pacote](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="a77bb-122">O 'Nome do pacote' é o identificador exclusivo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a77bb-122">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="a77bb-123">Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a77bb-123">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="a77bb-124">O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a77bb-124">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="a77bb-125">Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.</span><span class="sxs-lookup"><span data-stu-id="a77bb-125">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="a77bb-126">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="a77bb-126">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="a77bb-127">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:</span><span class="sxs-lookup"><span data-stu-id="a77bb-127">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Caminho do menu Configurações de Projeto... do Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="a77bb-129">Na janela Configurações do Projeto, selecione **Gerenciamento de Plug-ins do XR** > **Instalar o Gerenciamento de Plug-ins do XR**, para instalar o Gerenciamento de Plug-ins do XR:</span><span class="sxs-lookup"><span data-stu-id="a77bb-129">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![Configurações de XR do Unity com o gerenciamento de plug-ins de instalação do XR selecionado](../images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="a77bb-131">Depois que o Unity terminar de instalar o Gerenciamento de Plug-ins do XR.</span><span class="sxs-lookup"><span data-stu-id="a77bb-131">After Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="a77bb-132">Verifique se você está nas configurações da Plataforma Universal do Windows e marque as opções **Inicializar o XR ao iniciar**, **OpenXR** e **Conjunto de recursos do Microsoft HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="a77bb-132">Ensure that you are in Universal Windows Platform settings and Check the **Initialize XR on Startup**, **OpenXR** and **Microsoft HoloLens feature set** checkboxes.</span></span>

![Configurações de XR do Unity com a adição do OpenXR e dos recursos do Microsoft HoloLens selecionados](../images/mr-learning-base/base-02-section5-step2-2-1-openxr.png)

<span data-ttu-id="a77bb-134">Na barra de menus na parte superior da tela, navegue até **Realidade Misturada > OpenXR > Aplicar as configurações de projeto recomendadas para o HoloLens 2** para obter melhor desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a77bb-134">In the menu bar at the top of the screen, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Menu da Realidade Misturada com as opções OpenXR e Aplicar as configurações de projeto recomendadas para o HoloLens 2 selecionadas](../images/mr-learning-base/base-02-section5-step2-openxr-2.png)

>[!Important]
><span data-ttu-id="a77bb-136">Se você vir um ícone de aviso vermelho ao lado de Plug-in do OpenXR (Versão Prévia), clique no ícone e selecione Corrigir Tudo antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a77bb-136">If you see a red warning icon next to OpenXR Plugin (Preview), click the icon and select Fix all before continuing.</span></span> <span data-ttu-id="a77bb-137">O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="a77bb-137">The Unity Editor may need to restart itself for the changes to take effect.</span></span>
><span data-ttu-id="a77bb-138">![Menu de validação de projeto do OpenXR com todos os problemas a serem corrigidos selecionados.](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)</span><span class="sxs-lookup"><span data-stu-id="a77bb-138">![OpenXR project validation menu with all issues selected to be fixed.](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)</span></span>

<span data-ttu-id="a77bb-139">Depois que o Unity terminar de importar os arquivos necessários, a janela do Configurador de Projeto do MRTK será exibida novamente.</span><span class="sxs-lookup"><span data-stu-id="a77bb-139">After Unity has finished importing necessary files, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="a77bb-140">Se ela não aparecer, use o menu do Unity para abri-la.</span><span class="sxs-lookup"><span data-stu-id="a77bb-140">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="a77bb-141">Na janela Configurador de Projeto do MRTK, use a lista suspensa **Espacializador de áudio** para selecionar o **Espacializador MS HRTF** e clique no botão **Aplicar** para aplicar a configuração:</span><span class="sxs-lookup"><span data-stu-id="a77bb-141">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Janela de configuração do MRTK com as opções padrão selecionadas](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
><span data-ttu-id="a77bb-143">A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a77bb-143">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="a77bb-144">Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="a77bb-144">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="a77bb-145">Para saber mais sobre este tópico, veja os <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutoriais sobre áudio espacial</a>.</span><span class="sxs-lookup"><span data-stu-id="a77bb-145">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>


<span data-ttu-id="a77bb-146">Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="a77bb-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Configurações de Publicação do Unity](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="a77bb-148">O 'Nome do pacote' é o identificador exclusivo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a77bb-148">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="a77bb-149">Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a77bb-149">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="a77bb-150">O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a77bb-150">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="a77bb-151">Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.</span><span class="sxs-lookup"><span data-stu-id="a77bb-151">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="a77bb-152">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="a77bb-152">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="a77bb-153">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:</span><span class="sxs-lookup"><span data-stu-id="a77bb-153">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="a77bb-154">Na janela Configurações do Projeto, selecione **Player** > **Configurações de XR** e marque a caixa de seleção **Realidade Virtual com Suporte**, clique no ícone **+** e selecione Windows Mixed Reality para adicionar o SDK do Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="a77bb-154">In the Project Settings window, select **Player** > **XR Settings** and check the **Virual Reality Supported** checkbox then click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![Configurações de XR do Unity, adição do SDK do Windows Mixed Reality selecionada](../images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="a77bb-156">Depois que o Unity terminar de importar o SDK do Windows Mixed Reality, a janela Configurador de Projeto do MRTK deverá aparecer novamente.</span><span class="sxs-lookup"><span data-stu-id="a77bb-156">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="a77bb-157">Caso contrário, você pode abri-la manualmente no menu do Unity acessando **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity**</span><span class="sxs-lookup"><span data-stu-id="a77bb-157">If it doesn't, you can manually open it from the Unity menu by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**</span></span>

<span data-ttu-id="a77bb-158">Na janela Configurador de Projeto do MRTK, use a lista suspensa **Espacializador de áudio** para selecionar o **Espacializador MS HRTF** e clique no botão **Aplicar** para aplicar a configuração:</span><span class="sxs-lookup"><span data-stu-id="a77bb-158">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Janela de configuração do MRTK](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="a77bb-160">A definição da propriedade Espacializador de áudio é opcional, mas pode aprimorar a experiência de áudio no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a77bb-160">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="a77bb-161">Se você a definir como Espacializador MS HRTF, esse plug-in do espacializador será usado quando a propriedade AudioSource.spatialize do Unity estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="a77bb-161">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="a77bb-162">Para saber mais sobre este tópico, veja os <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutoriais sobre áudio espacial</a>.</span><span class="sxs-lookup"><span data-stu-id="a77bb-162">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="a77bb-163">Na janela Configurações do Projeto, selecione **Player** > **Configurações de XR** e, em seguida, use a lista suspensa **Formato de Profundidade** para selecionar a **Profundidade de 16 bits**:</span><span class="sxs-lookup"><span data-stu-id="a77bb-163">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Habilitação da profundidade de 16 bits do Unity](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="a77bb-165">A redução do formato de profundidade para 16 bits é opcional, mas ajuda a aprimorar o desempenho gráfico no projeto.</span><span class="sxs-lookup"><span data-stu-id="a77bb-165">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="a77bb-166">Para saber mais sobre este tópico, veja a seção <a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Compartilhamento de buffer de profundidade (HoloLens)</a> na documentação <a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Desempenho</a> do MRTK.</span><span class="sxs-lookup"><span data-stu-id="a77bb-166">To learn more about this topic, you can refer to the   <a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="a77bb-167">Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="a77bb-167">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Configurações de Publicação do Unity.](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="a77bb-170">O 'Nome do pacote' é o identificador exclusivo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a77bb-170">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="a77bb-171">Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a77bb-171">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="a77bb-172">O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a77bb-172">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="a77bb-173">Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.</span><span class="sxs-lookup"><span data-stu-id="a77bb-173">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>