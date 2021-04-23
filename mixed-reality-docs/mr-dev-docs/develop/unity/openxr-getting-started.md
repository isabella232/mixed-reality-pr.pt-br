---
title: Usando o plug-in OpenXR de realidade misturada para o Unity
description: Saiba como habilitar o plug-in OpenXR de realidade misturada para projetos do Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução
ms.openlocfilehash: 97169507e2b61110d2d16580ba957feff3755258
ms.sourcegitcommit: aca5fddb98fbbd9aa22bdf8174d7fdcdb9d4c08a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2021
ms.locfileid: "107894006"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="a276d-104">Usando o plug-in OpenXR de realidade misturada para o Unity</span><span class="sxs-lookup"><span data-stu-id="a276d-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="a276d-105">A partir da versão 2020,2 do Unity, o pacote de plugin OpenXR de realidade misturada da Microsoft está disponível usando o UPM (Gerenciador de pacotes do Unity).</span><span class="sxs-lookup"><span data-stu-id="a276d-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a276d-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a276d-106">Prerequisites</span></span>

* <span data-ttu-id="a276d-107">Unity 2020,3 LTS ou posterior</span><span class="sxs-lookup"><span data-stu-id="a276d-107">Unity 2020.3 LTS or later</span></span>
* <span data-ttu-id="a276d-108">Plug-in do Unity OpenXR 1.1.1 ou posterior</span><span class="sxs-lookup"><span data-stu-id="a276d-108">Unity OpenXR plugin 1.1.1 or later</span></span>
* <span data-ttu-id="a276d-109">Visual Studio 2019 ou posterior</span><span class="sxs-lookup"><span data-stu-id="a276d-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="a276d-110">Instalar o suporte da plataforma **UWP** no Unity para aplicativos do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a276d-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="a276d-111">Se você estiver criando aplicativos VR no computador Windows, o plug-in OpenXR de realidade misturada não será necessariamente necessário.</span><span class="sxs-lookup"><span data-stu-id="a276d-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="a276d-112">No entanto, você desejará instalar o plug-in se estiver personalizando o mapeamento do controlador para controladores do HP reverbo G2 ou compilando aplicativos que funcionam em headsets de HoloLens 2 e VR.</span><span class="sxs-lookup"><span data-stu-id="a276d-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="a276d-113">Configurando seu projeto com o MRTK</span><span class="sxs-lookup"><span data-stu-id="a276d-113">Setting up your project with MRTK</span></span>

<span data-ttu-id="a276d-114">O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais.</span><span class="sxs-lookup"><span data-stu-id="a276d-114">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="a276d-115">A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="a276d-115">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="a276d-116">O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.</span><span class="sxs-lookup"><span data-stu-id="a276d-116">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a276d-117">Configurar seu projeto usando o MRTK</span><span class="sxs-lookup"><span data-stu-id="a276d-117">Set up your project using MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="a276d-118">Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.</span><span class="sxs-lookup"><span data-stu-id="a276d-118">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="a276d-119">Configuração manual sem MRTK</span><span class="sxs-lookup"><span data-stu-id="a276d-119">Manual setup without MRTK</span></span>

<span data-ttu-id="a276d-120">Instale o plug-in OpenXR com o novo aplicativo de ferramenta de recursos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="a276d-120">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="a276d-121">Siga as [instruções de instalação e uso](welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR da realidade mista** na categoria Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="a276d-121">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Janela de pacotes da ferramenta de recurso de realidade mista com plug-in aberto XR realçado](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="a276d-123">Configurando seu destino de compilação</span><span class="sxs-lookup"><span data-stu-id="a276d-123">Setting your build target</span></span>

<span data-ttu-id="a276d-124">Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="a276d-124">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

<span data-ttu-id="a276d-126">Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="a276d-126">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="a276d-127">Selecione **arquivo > configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="a276d-127">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="a276d-128">Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="a276d-128">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="a276d-129">Defina a **Arquitetura** como **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="a276d-129">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="a276d-130">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="a276d-130">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="a276d-131">Defina o **Tipo de Build** como **D3D**</span><span class="sxs-lookup"><span data-stu-id="a276d-131">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="a276d-132">Defina o **SDK do UWP** como **Último instalado**</span><span class="sxs-lookup"><span data-stu-id="a276d-132">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="a276d-133">Defina a **Configuração de Build** como **Lançamento** porque há problemas de desempenho conhecidos com a opção Depurar</span><span class="sxs-lookup"><span data-stu-id="a276d-133">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](images/wmr-config-img-4.png)

<span data-ttu-id="a276d-135">Depois de definir sua plataforma, você precisa deixar que o Unity saiba criar uma [exibição de imersão](../../design/app-views.md) em vez de uma exibição 2D quando exportada.</span><span class="sxs-lookup"><span data-stu-id="a276d-135">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="a276d-136">Configurando o gerenciamento de plugin XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="a276d-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="a276d-137">Para definir OpenXR como o tempo de execução no Unity:</span><span class="sxs-lookup"><span data-stu-id="a276d-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="a276d-138">No editor do Unity, navegue até **editar > configurações do projeto**</span><span class="sxs-lookup"><span data-stu-id="a276d-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="a276d-139">Na lista de configurações, selecione **Gerenciamento de plugin XR**</span><span class="sxs-lookup"><span data-stu-id="a276d-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="a276d-140">Verifique as caixas **inicializar XR nas Startup** e **OpenXR**</span><span class="sxs-lookup"><span data-stu-id="a276d-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="a276d-141">Se estiver direcionando para o HoloLens 2, verifique se você está na plataforma UWP e selecione **conjunto de recursos do Microsoft HoloLens**</span><span class="sxs-lookup"><span data-stu-id="a276d-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="a276d-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="a276d-143">Optimization</span></span>

<span data-ttu-id="a276d-144">Se você estiver desenvolvendo para o HoloLens 2, navegue até a **realidade misturada> OpenXR > aplicar as configurações de projeto recomendadas para o HoloLens 2** para obter melhor desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a276d-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Captura de tela do item de menu da realidade misturada abrir com OpenXR selecionado](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="a276d-146">Se você vir um ícone de aviso vermelho ao lado de **plug-in OpenXR**, clique no ícone e selecione **corrigir tudo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a276d-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="a276d-147">O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="a276d-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de tela da janela de validação do projeto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="a276d-149">Agora você está pronto para começar a desenvolver com o OpenXR no Unity!</span><span class="sxs-lookup"><span data-stu-id="a276d-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="a276d-150">Continue na próxima seção para aprender a usar os exemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="a276d-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="a276d-151">Experimente os bastidores de exemplo do Unity</span><span class="sxs-lookup"><span data-stu-id="a276d-151">Try out the Unity sample scenes</span></span>

### <a name="hololens-2-samples"></a><span data-ttu-id="a276d-152">Exemplos de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a276d-152">HoloLens 2 samples</span></span>

1. <span data-ttu-id="a276d-153">No editor do Unity, navegue até a **janela > Gerenciador de pacotes**</span><span class="sxs-lookup"><span data-stu-id="a276d-153">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="a276d-154">Na lista de pacotes, selecione **OpenXR de realidade misturada plug-in**</span><span class="sxs-lookup"><span data-stu-id="a276d-154">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="a276d-155">Localize o exemplo na lista de **exemplos** e selecione **importar**</span><span class="sxs-lookup"><span data-stu-id="a276d-155">Locate the sample in the **Samples** list and select **Import**</span></span>

![Captura de tela do Gerenciador de pacotes do Unity abrir no editor do Unity com realidade misturada OpenXR plugin selecionado e exemplos de importação do botão realçado](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="a276d-157">Quando um pacote é atualizado, o Unity fornece a opção de atualizar amostras importadas.</span><span class="sxs-lookup"><span data-stu-id="a276d-157">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="a276d-158">A atualização de um exemplo importado substituirá as alterações feitas no exemplo e nos ativos associados.</span><span class="sxs-lookup"><span data-stu-id="a276d-158">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="a276d-159">Usando o MRTK com suporte a OpenXR</span><span class="sxs-lookup"><span data-stu-id="a276d-159">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="a276d-160">MRTK-Unity dá suporte ao plug-in OpenXR de realidade misturada começando pela versão 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="a276d-160">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="a276d-161">Abra a [ferramenta de funcionalidade Mixed Reality](welcome-to-mr-feature-tool.md) novamente para instalar o kit de ferramentas do reality misto, se ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="a276d-161">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="a276d-162">O suporte do OpenXR está no pacote **base** .</span><span class="sxs-lookup"><span data-stu-id="a276d-162">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="a276d-163">Vá para o script de componente do MixedReality Toolkit no Inspetor e alterne para o perfil **DefaultOpenXRConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="a276d-163">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Captura de tela de alternância da configuração MRTK no componente Mixed Reality Toolkit no Inspetor](images/openxr-img-11.png)

    1. <span data-ttu-id="a276d-165">Consulte a documentação do MRTK para obter [informações mais detalhadas sobre como migrar para o OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span><span class="sxs-lookup"><span data-stu-id="a276d-165">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="a276d-166">Ao atualizar de uma versão anterior do MRTK, verifique se a linha a seguir está no arquivo **assets/MixedRealityToolkit. Generated/link.xml** :</span><span class="sxs-lookup"><span data-stu-id="a276d-166">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="a276d-167">Essa linha será adicionada por padrão se você tiver iniciado com MRTK 2.5.4 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="a276d-167">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a276d-168">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a276d-168">Next steps</span></span>

<span data-ttu-id="a276d-169">Agora que você tem o projeto configurado para OpenXR e tem acesso a exemplos, confira quais [recursos](openxr-supported-features.md) têm suporte no momento em nosso plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="a276d-169">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="a276d-170">Tem comentários?</span><span class="sxs-lookup"><span data-stu-id="a276d-170">Have Feedback?</span></span>

<span data-ttu-id="a276d-171">O OpenXR ainda é experimental, portanto, agradecemos os comentários que você pode nos dar para ajudá-lo a melhorá-lo.</span><span class="sxs-lookup"><span data-stu-id="a276d-171">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="a276d-172">Você nos verá nos fóruns do [Unity](https://aka.ms/unityforums) marcando sua postagem no fórum com o **Microsoft**  +  **OpenXR** e o **HoloLens 2** ou a **realidade mista do Windows**.</span><span class="sxs-lookup"><span data-stu-id="a276d-172">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a276d-173">Confira também</span><span class="sxs-lookup"><span data-stu-id="a276d-173">See also</span></span>

* [<span data-ttu-id="a276d-174">Como configurar seu projeto sem o MRTK</span><span class="sxs-lookup"><span data-stu-id="a276d-174">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="a276d-175">Configurações recomendadas do Unity</span><span class="sxs-lookup"><span data-stu-id="a276d-175">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="a276d-176">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="a276d-176">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
