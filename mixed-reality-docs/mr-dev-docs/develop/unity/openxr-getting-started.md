---
title: Como usar o plug-in OpenXR de Realidade Misturada
description: Saiba como habilitar o plug-in OpenXR de realidade misturada para projetos do Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução
ms.openlocfilehash: 65b79aadeb52db6be61edcc90a5d4a44c12384a1
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547069"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="14a0f-104">Como usar o plug-in OpenXR de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="14a0f-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="14a0f-105">Para os desenvolvedores que visam o Unity 2020 criarem aplicativos de realidade 2 ou misturados, o plug-in OpenXR pode ser usado em vez do plug-in WindowsXR para melhorar as compatibilidades entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="14a0f-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="14a0f-106">O plug-in OpenXR de realidade misturada também funciona bem com o mais recente [Kit de ferramentas de realidade mista 2,7](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="14a0f-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Toolkit 2.7](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="14a0f-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="14a0f-107">Prerequisites</span></span>

* <span data-ttu-id="14a0f-108">LTS do Unity 2020,3 mais recente, (recomendamos o 2020.3.8 F1 ou superior)</span><span class="sxs-lookup"><span data-stu-id="14a0f-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>
* <span data-ttu-id="14a0f-109">Plug-in mais recente do Unity OpenXR (Recomendamos 1,2 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="14a0f-109">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="14a0f-110">Ferramentas mais recentes [para o desenvolvimento do HoloLens 2](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="14a0f-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="14a0f-111">MRTK mais recente (opcional), (recomendamos a versão 2,7 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="14a0f-111">Latest MRTK (optional), (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="14a0f-112">Plugin OpenXR de realidade mista mais recente, (recomendamos a versão 1.0.0-Preview. 1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="14a0f-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0-preview.1 or later)</span></span>

![Captura de tela da amostra do Open XR Unity básico em execução em um HoloLens](images/openxr-example.png)

> [!NOTE]
> <span data-ttu-id="14a0f-114">Se você estiver criando aplicativos VR no computador Windows, o plug-in OpenXR de realidade misturada não será necessariamente necessário.</span><span class="sxs-lookup"><span data-stu-id="14a0f-114">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="14a0f-115">No entanto, você desejará instalar o plug-in se estiver personalizando o mapeamento do controlador para controladores do HP reverbo G2 ou compilando aplicativos que funcionam em headsets de HoloLens 2 e VR.</span><span class="sxs-lookup"><span data-stu-id="14a0f-115">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="14a0f-116">Configurando seu projeto com o MRTK</span><span class="sxs-lookup"><span data-stu-id="14a0f-116">Setting up your project with MRTK</span></span>

<span data-ttu-id="14a0f-117">O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais.</span><span class="sxs-lookup"><span data-stu-id="14a0f-117">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="14a0f-118">A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="14a0f-118">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="14a0f-119">O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.</span><span class="sxs-lookup"><span data-stu-id="14a0f-119">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="14a0f-120">Configurar seu projeto usando o MRTK</span><span class="sxs-lookup"><span data-stu-id="14a0f-120">Set up your project using MRTK</span></span>](./tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="14a0f-121">Dê uma olhada na [documentação do MRTK](/windows/mixed-reality/mrtk-unity) para obter mais detalhes sobre os recursos.</span><span class="sxs-lookup"><span data-stu-id="14a0f-121">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="14a0f-122">Configuração manual sem MRTK</span><span class="sxs-lookup"><span data-stu-id="14a0f-122">Manual setup without MRTK</span></span>

<span data-ttu-id="14a0f-123">Instale o plug-in OpenXR com o novo aplicativo de ferramenta de recursos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="14a0f-123">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="14a0f-124">Siga as [instruções de instalação e uso](welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR da realidade mista** na categoria Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="14a0f-124">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Janela de pacotes da ferramenta de recurso de realidade mista com plug-in aberto XR realçado](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="14a0f-126">Configurando seu destino de compilação</span><span class="sxs-lookup"><span data-stu-id="14a0f-126">Setting your build target</span></span>

<span data-ttu-id="14a0f-127">Se você estiver destinando à área de trabalho VR, sugerimos usar a plataforma autônoma do PC selecionada por padrão em um novo projeto do Unity:</span><span class="sxs-lookup"><span data-stu-id="14a0f-127">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com PC, Mac & plataforma autônoma realçada](images/wmr-config-img-3.png)

<span data-ttu-id="14a0f-129">Se você estiver direcionando para o HoloLens 2, precisará alternar para o Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="14a0f-129">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="14a0f-130">Selecione **arquivo > configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="14a0f-130">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="14a0f-131">Selecione **plataforma universal do Windows** na lista plataforma e selecione **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="14a0f-131">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="14a0f-132">Defina a **Arquitetura** como **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="14a0f-132">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="14a0f-133">Defina o **Dispositivo de destino** como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="14a0f-133">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="14a0f-134">Defina o **Tipo de Build** como **D3D**</span><span class="sxs-lookup"><span data-stu-id="14a0f-134">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="14a0f-135">Defina o **SDK do UWP** como **Último instalado**</span><span class="sxs-lookup"><span data-stu-id="14a0f-135">Set **UWP SDK** to **Latest installed**</span></span>

![Captura de tela da janela de configurações de Build aberta no editor do Unity com Plataforma Universal do Windows realçado](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="14a0f-137">Configurando o gerenciamento de plugin XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="14a0f-137">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="14a0f-138">Para definir OpenXR como o tempo de execução no Unity:</span><span class="sxs-lookup"><span data-stu-id="14a0f-138">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="14a0f-139">No editor do Unity, navegue até **editar > configurações do projeto**</span><span class="sxs-lookup"><span data-stu-id="14a0f-139">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="14a0f-140">Na lista de configurações, selecione **Gerenciamento de plugin XR**</span><span class="sxs-lookup"><span data-stu-id="14a0f-140">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="14a0f-141">Verifique as caixas **inicializar XR nas Startup** e **OpenXR**</span><span class="sxs-lookup"><span data-stu-id="14a0f-141">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="14a0f-142">Se estiver direcionando para o HoloLens 2, verifique se você está na plataforma UWP e selecione **conjunto de recursos do Microsoft HoloLens**</span><span class="sxs-lookup"><span data-stu-id="14a0f-142">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="14a0f-144">Optimization</span><span class="sxs-lookup"><span data-stu-id="14a0f-144">Optimization</span></span>

<span data-ttu-id="14a0f-145">Se você estiver desenvolvendo para o HoloLens 2, navegue até a **realidade misturada> OpenXR > aplicar as configurações de projeto recomendadas para o HoloLens 2** para obter melhor desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="14a0f-145">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Captura de tela do item de menu da realidade misturada abrir com OpenXR selecionado](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="14a0f-147">Se você vir um ícone de aviso vermelho ao lado de **plug-in OpenXR**, clique no ícone e selecione **corrigir tudo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="14a0f-147">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="14a0f-148">O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="14a0f-148">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de tela da janela de validação do projeto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="14a0f-150">Agora você está pronto para começar a desenvolver com o OpenXR no Unity!</span><span class="sxs-lookup"><span data-stu-id="14a0f-150">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="14a0f-151">Continue na próxima seção para aprender a usar os exemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="14a0f-151">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="14a0f-152">Projetos de exemplo do Unity para OpenXR e HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="14a0f-152">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="14a0f-153">Confira o [repositório de exemplos de realidade misturada OpenXR](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para projetos de exemplo de Unity mostrando como criar aplicativos de Unity para o HoloLens 2 ou headsets de realidade misturada usando o plug-in OpenXR de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="14a0f-153">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="14a0f-154">Usando o MRTK com suporte a OpenXR</span><span class="sxs-lookup"><span data-stu-id="14a0f-154">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="14a0f-155">O MRTK para a versão 2,7 do Unity agora dá suporte oficialmente ao plug-in OpenXR da realidade mista.</span><span class="sxs-lookup"><span data-stu-id="14a0f-155">MRTK for Unity version 2.7 now officially supports the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="14a0f-156">Abra a [ferramenta de funcionalidade Mixed Reality](welcome-to-mr-feature-tool.md) novamente para instalar o kit de ferramentas do reality misto, se ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="14a0f-156">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="14a0f-157">O suporte do OpenXR está no pacote **base** .</span><span class="sxs-lookup"><span data-stu-id="14a0f-157">OpenXR support is in the **Foundation** package.</span></span>

![Ferramenta de recursos da realidade misturada descobrir janela de características com ativos padrão realçados](images/mrft-install-openxr.png)

> [!NOTE]
> <span data-ttu-id="14a0f-159">Ao atualizar de uma versão anterior do MRTK, verifique se a linha a seguir está no arquivo **assets/MixedRealityToolkit. Generated/link.xml** :</span><span class="sxs-lookup"><span data-stu-id="14a0f-159">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="14a0f-160">Essa linha será adicionada por padrão se você tiver iniciado com MRTK 2.5.4 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="14a0f-160">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="14a0f-161">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="14a0f-161">Next steps</span></span>

<span data-ttu-id="14a0f-162">Agora que você tem o projeto configurado para OpenXR e tem acesso a exemplos, confira quais [recursos](openxr-supported-features.md) têm suporte no momento em nosso plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="14a0f-162">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="14a0f-163">Tem comentários?</span><span class="sxs-lookup"><span data-stu-id="14a0f-163">Have Feedback?</span></span>

<span data-ttu-id="14a0f-164">O OpenXR ainda é experimental, portanto, agradecemos os comentários que você pode nos dar para ajudá-lo a melhorá-lo.</span><span class="sxs-lookup"><span data-stu-id="14a0f-164">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="14a0f-165">Você nos verá nos fóruns do [Unity](https://aka.ms/unityforums) marcando sua postagem no fórum com o **Microsoft**  +  **OpenXR** e o **HoloLens 2** ou a **realidade mista do Windows**.</span><span class="sxs-lookup"><span data-stu-id="14a0f-165">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="14a0f-166">Confira também</span><span class="sxs-lookup"><span data-stu-id="14a0f-166">See also</span></span>

* [<span data-ttu-id="14a0f-167">Como configurar seu projeto sem o MRTK</span><span class="sxs-lookup"><span data-stu-id="14a0f-167">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="14a0f-168">Configurações recomendadas do Unity</span><span class="sxs-lookup"><span data-stu-id="14a0f-168">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="14a0f-169">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="14a0f-169">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
