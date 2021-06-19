---
title: Como usar o plug-in OpenXR de Realidade Misturada
description: Saiba como habilitar o plug-in OpenXR de Realidade Misturada para projetos do Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realidade misturada, MRTK, Kit de Ferramentas de Realidade Misturada, realidade aumentada, realidade virtual, headsets de realidade misturada, learn, tutorial, introdução
ms.openlocfilehash: ffec0cbe2ea9fd87cbb5f38010dad2d64e2e82ee
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392674"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="95ef9-104">Como usar o plug-in OpenXR de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="95ef9-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="95ef9-105">Para desenvolvedores que direcionam o Unity 2020 para criar aplicativos holoLens 2 ou Realidade Misturada, o plug-in OpenXR pode ser usado em vez do plug-in windowsXR para melhor compatibilidade entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="95ef9-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="95ef9-106">O plug-in OpenXR de Realidade Misturada também funciona bem com a Ferramenta de Recursos de [Realidade Misturada mais recente.](welcome-to-mr-feature-tool.md)</span><span class="sxs-lookup"><span data-stu-id="95ef9-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="95ef9-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="95ef9-107">Prerequisites</span></span>

* <span data-ttu-id="95ef9-108">Unity 2020.3 LTS mais recente, recomendamos 2020.3.6f1 ou superior.</span><span class="sxs-lookup"><span data-stu-id="95ef9-108">Latest Unity 2020.3 LTS, recommend 2020.3.6f1 or above.</span></span>
* <span data-ttu-id="95ef9-109">Plug-in do Unity OpenXR mais recente, recomendamos 1.2 ou posterior</span><span class="sxs-lookup"><span data-stu-id="95ef9-109">Latest Unity OpenXR plugin, recommend 1.2 or later</span></span>
* <span data-ttu-id="95ef9-110">Ferramentas [mais recentes para desenvolvimento do HoloLens 2](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="95ef9-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="95ef9-111">MRTK mais recente (opcional), recomenda a versão 2.6 ou posterior</span><span class="sxs-lookup"><span data-stu-id="95ef9-111">Latest MRTK (optional), recommend version 2.6 or later</span></span>
* <span data-ttu-id="95ef9-112">Plug-in OpenXR de Realidade Misturada mais recente, recomendamos a versão 0.9.5 ou posterior</span><span class="sxs-lookup"><span data-stu-id="95ef9-112">Latest Mixed Reality OpenXR Plugin, recommend version 0.9.5 or later</span></span>

> [!NOTE]
> <span data-ttu-id="95ef9-113">Se você estiver criando aplicativos de VR no computador Windows, o plug-in OpenXR de Realidade Misturada não será necessariamente necessário.</span><span class="sxs-lookup"><span data-stu-id="95ef9-113">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="95ef9-114">No entanto, você deseja instalar o plug-in se estiver personalização do mapeamento do controlador para controladores HP Reverb G2 ou criação de aplicativos que funcionam em headsets HoloLens 2 e VR.</span><span class="sxs-lookup"><span data-stu-id="95ef9-114">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="95ef9-115">Configurando seu projeto com o MRTK</span><span class="sxs-lookup"><span data-stu-id="95ef9-115">Setting up your project with MRTK</span></span>

<span data-ttu-id="95ef9-116">O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais.</span><span class="sxs-lookup"><span data-stu-id="95ef9-116">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="95ef9-117">A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="95ef9-117">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="95ef9-118">O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.</span><span class="sxs-lookup"><span data-stu-id="95ef9-118">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="95ef9-119">Configurar seu projeto usando o MRTK</span><span class="sxs-lookup"><span data-stu-id="95ef9-119">Set up your project using MRTK</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="95ef9-120">Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.</span><span class="sxs-lookup"><span data-stu-id="95ef9-120">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="95ef9-121">Configuração manual sem MRTK</span><span class="sxs-lookup"><span data-stu-id="95ef9-121">Manual setup without MRTK</span></span>

<span data-ttu-id="95ef9-122">Instale o plug-in OpenXR com o novo aplicativo Ferramenta de Recursos de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="95ef9-122">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="95ef9-123">Siga as [instruções de instalação e uso](welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR de** Realidade Misturada na categoria Kit de Ferramentas de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="95ef9-123">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Janela de pacotes da Ferramenta de Recursos de Realidade Misturada com o plug-in xr aberto realçada](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="95ef9-125">Definindo seu destino de build</span><span class="sxs-lookup"><span data-stu-id="95ef9-125">Setting your build target</span></span>

<span data-ttu-id="95ef9-126">Se você estiver direcionando a VR da Área de Trabalho, sugerimos usar a Plataforma Autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="95ef9-126">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela Configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

<span data-ttu-id="95ef9-128">Se você estiver direcionando o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="95ef9-128">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="95ef9-129">Selecione **Arquivo > Configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="95ef9-129">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="95ef9-130">Selecione **Plataforma Universal do Windows** na lista Plataforma e selecione **Alternar Plataforma**</span><span class="sxs-lookup"><span data-stu-id="95ef9-130">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="95ef9-131">Defina a **Arquitetura** como **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="95ef9-131">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="95ef9-132">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="95ef9-132">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="95ef9-133">Defina o **Tipo de Build** como **D3D**</span><span class="sxs-lookup"><span data-stu-id="95ef9-133">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="95ef9-134">Defina o **SDK do UWP** como **Último instalado**</span><span class="sxs-lookup"><span data-stu-id="95ef9-134">Set **UWP SDK** to **Latest installed**</span></span>

![Captura de tela da janela Configurações de Build aberta no editor do Unity Plataforma Universal do Windows realçada](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="95ef9-136">Configurando o gerenciamento de plug-in XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="95ef9-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="95ef9-137">Para definir o OpenXR como o runtime no Unity:</span><span class="sxs-lookup"><span data-stu-id="95ef9-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="95ef9-138">No Editor do Unity, navegue até **Editar configurações > projeto**</span><span class="sxs-lookup"><span data-stu-id="95ef9-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="95ef9-139">Na lista de Configurações, selecione Gerenciamento **de Plug-in XR**</span><span class="sxs-lookup"><span data-stu-id="95ef9-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="95ef9-140">Marque as **caixas Inicializar XR na Inicialização** **e OpenXR**</span><span class="sxs-lookup"><span data-stu-id="95ef9-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="95ef9-141">Se estiver direcionando o HoloLens 2, certifique-se de que você está na plataforma UWP e selecione **Microsoft HoloLens conjunto de recursos**</span><span class="sxs-lookup"><span data-stu-id="95ef9-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Captura de tela do painel de configurações do projeto aberto no editor do Unity com o gerenciamento de plug-in XR realçada](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="95ef9-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="95ef9-143">Optimization</span></span>

<span data-ttu-id="95ef9-144">Se você estiver desenvolvendo para o HoloLens 2, navegue até Realidade **Misturada> OpenXR > Aplicar** as configurações de projeto recomendadas para o HoloLens 2 para obter um melhor desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95ef9-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Captura de tela do item de menu de realidade misturada aberto com OpenXR selecionado](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="95ef9-146">Se você vir um ícone de aviso vermelho ao lado do **Plug-in OpenXR,** clique no ícone e selecione **Corrigir tudo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="95ef9-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="95ef9-147">O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="95ef9-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de tela da janela de validação do projeto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="95ef9-149">Agora você está pronto para começar a desenvolver com o OpenXR no Unity!</span><span class="sxs-lookup"><span data-stu-id="95ef9-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="95ef9-150">Continue na próxima seção para saber como usar os exemplos do OpenXR.</span><span class="sxs-lookup"><span data-stu-id="95ef9-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="95ef9-151">Projetos de exemplo do Unity para OpenXR e HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="95ef9-151">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="95ef9-152">Confira o repo de exemplos do [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para projetos de exemplo do Unity mostrando como criar aplicativos unity para headsets do HoloLens 2 ou realidade misturada usando o plug-in OpenXR de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="95ef9-152">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="95ef9-153">Usando o MRTK com suporte a OpenXR</span><span class="sxs-lookup"><span data-stu-id="95ef9-153">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="95ef9-154">MRTK-Unity dá suporte ao plug-in OpenXR de Realidade Misturada a partir da versão 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="95ef9-154">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="95ef9-155">Abra a [Ferramenta de Recursos de Realidade](welcome-to-mr-feature-tool.md) Misturada novamente para instalar o Kit de Ferramentas de Realidade Misturada, caso ainda não tenha feito isso.</span><span class="sxs-lookup"><span data-stu-id="95ef9-155">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="95ef9-156">O suporte a OpenXR está no **pacote Foundation.**</span><span class="sxs-lookup"><span data-stu-id="95ef9-156">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="95ef9-157">Vá para o script do componente MixedReality Toolkit no Inspetor e alternar para o **perfil DefaultOpenXRConfigurationProfile:**</span><span class="sxs-lookup"><span data-stu-id="95ef9-157">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Captura de tela da alternação da configuração do MRTK no componente Kit de Ferramentas de Realidade Misturada no inspetor](images/openxr-img-11.png)

    1. <span data-ttu-id="95ef9-159">Consulte a documentação do MRTK [para obter informações mais detalhadas sobre como migrar para o OpenXR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)</span><span class="sxs-lookup"><span data-stu-id="95ef9-159">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="95ef9-160">Ao atualizar de uma versão anterior do MRTK, verifique se a seguinte linha está no arquivo **Assets/MixedRealityToolkit.Generated/link.xml:**</span><span class="sxs-lookup"><span data-stu-id="95ef9-160">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="95ef9-161">Essa linha será adicionada por padrão se você tiver iniciado com o MRTK 2.5.4 ou mais novo.</span><span class="sxs-lookup"><span data-stu-id="95ef9-161">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="95ef9-162">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="95ef9-162">Next steps</span></span>

<span data-ttu-id="95ef9-163">Agora que seu projeto está configurado para OpenXR e tem [](openxr-supported-features.md) acesso a exemplos, confira quais recursos têm suporte no momento em nosso plug-in openXR.</span><span class="sxs-lookup"><span data-stu-id="95ef9-163">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="95ef9-164">Tem comentários?</span><span class="sxs-lookup"><span data-stu-id="95ef9-164">Have Feedback?</span></span>

<span data-ttu-id="95ef9-165">O OpenXR ainda é experimental, portanto, agradecemos qualquer comentário que você possa nos dar para ajudar a melhorá-lo.</span><span class="sxs-lookup"><span data-stu-id="95ef9-165">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="95ef9-166">Você nos encontrará nos Fóruns do [Unity](https://aka.ms/unityforums) marcando sua postagem do fórum com **o Microsoft** OpenXR e o  +   **HoloLens 2** **ou Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="95ef9-166">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="95ef9-167">Confira também</span><span class="sxs-lookup"><span data-stu-id="95ef9-167">See also</span></span>

* [<span data-ttu-id="95ef9-168">Como configurar seu projeto sem o MRTK</span><span class="sxs-lookup"><span data-stu-id="95ef9-168">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="95ef9-169">Configurações recomendadas do Unity</span><span class="sxs-lookup"><span data-stu-id="95ef9-169">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="95ef9-170">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="95ef9-170">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)