---
title: Usando o plug-in OpenXR de realidade misturada para o Unity
description: Saiba como habilitar o plug-in OpenXR de realidade misturada para projetos do Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução
ms.openlocfilehash: 61474ecf749b16c8c78352d9f28a6482bfa3334c
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105549916"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="e3464-104">Usando o plug-in OpenXR de realidade misturada para o Unity</span><span class="sxs-lookup"><span data-stu-id="e3464-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="e3464-105">A partir da versão 2020,2 do Unity, o pacote de plugin OpenXR de realidade misturada da Microsoft está disponível usando o UPM (Gerenciador de pacotes do Unity).</span><span class="sxs-lookup"><span data-stu-id="e3464-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e3464-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e3464-106">Prerequisites</span></span>

* <span data-ttu-id="e3464-107">Unity 2020,2 ou posterior</span><span class="sxs-lookup"><span data-stu-id="e3464-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="e3464-108">Plug-in do Unity OpenXR 0.1.4 ou posterior</span><span class="sxs-lookup"><span data-stu-id="e3464-108">Unity OpenXR plugin 0.1.4 or later</span></span>
* <span data-ttu-id="e3464-109">Visual Studio 2019 ou posterior</span><span class="sxs-lookup"><span data-stu-id="e3464-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="e3464-110">Instalar o suporte da plataforma **UWP** no Unity para aplicativos do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e3464-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="e3464-111">Se você estiver criando aplicativos VR no computador Windows, o plug-in OpenXR de realidade misturada não será necessariamente necessário.</span><span class="sxs-lookup"><span data-stu-id="e3464-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="e3464-112">No entanto, você desejará instalar o plug-in se estiver personalizando o mapeamento do controlador para controladores do HP reverbo G2 ou compilando aplicativos que funcionam em headsets de HoloLens 2 e VR.</span><span class="sxs-lookup"><span data-stu-id="e3464-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a><span data-ttu-id="e3464-113">Instalando o OpenXR com a ferramenta de funcionalidade de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="e3464-113">Installing OpenXR with the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="e3464-114">Instale o plug-in OpenXR com o novo aplicativo de ferramenta de recursos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="e3464-114">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="e3464-115">Siga as [instruções de instalação e uso](welcome-to-mr-feature-tool.md) e selecione o pacote de **plug-in OpenXR da realidade mista** na categoria Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="e3464-115">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Janela de pacotes da ferramenta de recurso de realidade mista com plug-in aberto XR realçado](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="e3464-117">Configurando o gerenciamento de plugin XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="e3464-117">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="e3464-118">Para definir OpenXR como o tempo de execução no Unity:</span><span class="sxs-lookup"><span data-stu-id="e3464-118">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="e3464-119">No editor do Unity, navegue até **editar > configurações do projeto**</span><span class="sxs-lookup"><span data-stu-id="e3464-119">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="e3464-120">Na lista de configurações, selecione **Gerenciamento de plugin XR**</span><span class="sxs-lookup"><span data-stu-id="e3464-120">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="e3464-121">Verifique as caixas **inicializar XR nas inicializações** e **OpenXR (visualização)**</span><span class="sxs-lookup"><span data-stu-id="e3464-121">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="e3464-122">Se estiver direcionando para o HoloLens 2, verifique se você está na plataforma UWP e selecione **conjunto de recursos do Microsoft HoloLens**</span><span class="sxs-lookup"><span data-stu-id="e3464-122">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="e3464-124">Se você vir um ícone de aviso vermelho ao lado do **plug-in OpenXR (versão prévia)**, clique no ícone e selecione **corrigir tudo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e3464-124">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="e3464-125">O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="e3464-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de tela da janela de validação do projeto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="e3464-127">Agora você está pronto para começar a desenvolver com o OpenXR no Unity!</span><span class="sxs-lookup"><span data-stu-id="e3464-127">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="e3464-128">Continue na próxima seção para aprender a usar os exemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="e3464-128">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="e3464-129">Optimization</span><span class="sxs-lookup"><span data-stu-id="e3464-129">Optimization</span></span>

<span data-ttu-id="e3464-130">Se você estiver desenvolvendo para o HoloLens 2, navegue até a **realidade misturada> OpenXR > aplicar as configurações de projeto recomendadas para o HoloLens 2** para obter melhor desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3464-130">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Captura de tela do item de menu da realidade misturada abrir com OpenXR selecionado](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="e3464-132">Experimente os bastidores de exemplo do Unity</span><span class="sxs-lookup"><span data-stu-id="e3464-132">Try out the Unity sample scenes</span></span>

<span data-ttu-id="e3464-133">Para utilizar um ou mais dos exemplos, instale o [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) do **Gerenciador de pacotes**:</span><span class="sxs-lookup"><span data-stu-id="e3464-133">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![Captura de tela do Gerenciador de pacotes do Unity aberta no editor do Unity com o AR Foundation realçado](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="e3464-135">Exemplos de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e3464-135">HoloLens 2 samples</span></span>

1. <span data-ttu-id="e3464-136">No editor do Unity, navegue até a **janela > Gerenciador de pacotes**</span><span class="sxs-lookup"><span data-stu-id="e3464-136">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="e3464-137">Na lista de pacotes, selecione **OpenXR de realidade misturada plug-in**</span><span class="sxs-lookup"><span data-stu-id="e3464-137">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="e3464-138">Localize o exemplo na lista de **exemplos** e selecione **importar**</span><span class="sxs-lookup"><span data-stu-id="e3464-138">Locate the sample in the **Samples** list and select **Import**</span></span>

![Captura de tela do Gerenciador de pacotes do Unity abrir no editor do Unity com realidade misturada OpenXR plugin selecionado e exemplos de importação do botão realçado](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="e3464-140">Quando um pacote é atualizado, o Unity fornece a opção de atualizar amostras importadas.</span><span class="sxs-lookup"><span data-stu-id="e3464-140">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="e3464-141">A atualização de um exemplo importado substituirá as alterações feitas no exemplo e nos ativos associados.</span><span class="sxs-lookup"><span data-stu-id="e3464-141">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="e3464-142">Usando o MRTK com suporte a OpenXR</span><span class="sxs-lookup"><span data-stu-id="e3464-142">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="e3464-143">MRTK-Unity dá suporte ao plug-in OpenXR de realidade misturada começando pela versão 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="e3464-143">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="e3464-144">Abra a [ferramenta de funcionalidade Mixed Reality](welcome-to-mr-feature-tool.md) novamente para instalar o kit de ferramentas do reality misto, se ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="e3464-144">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="e3464-145">O suporte do OpenXR está no pacote **base** .</span><span class="sxs-lookup"><span data-stu-id="e3464-145">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="e3464-146">Vá para o script de componente do MixedReality Toolkit no Inspetor e alterne para o perfil **DefaultOpenXRConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="e3464-146">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Captura de tela de alternância da configuração MRTK no componente Mixed Reality Toolkit no Inspetor](images/openxr-img-11.png)

    1. <span data-ttu-id="e3464-148">Consulte a documentação do MRTK para obter [informações mais detalhadas sobre como migrar para o OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span><span class="sxs-lookup"><span data-stu-id="e3464-148">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="e3464-149">Ao atualizar de uma versão anterior do MRTK, verifique se a linha a seguir está no arquivo **assets/MixedRealityToolkit. Generated/link.xml** :</span><span class="sxs-lookup"><span data-stu-id="e3464-149">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="e3464-150">Essa linha será adicionada por padrão se você tiver iniciado com MRTK 2.5.4 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="e3464-150">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e3464-151">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e3464-151">Next steps</span></span>

<span data-ttu-id="e3464-152">Agora que você tem o projeto configurado para OpenXR e tem acesso a exemplos, confira quais [recursos](openxr-supported-features.md) têm suporte no momento em nosso plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="e3464-152">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="e3464-153">Tem comentários?</span><span class="sxs-lookup"><span data-stu-id="e3464-153">Have Feedback?</span></span>

<span data-ttu-id="e3464-154">O OpenXR ainda é experimental, portanto, agradecemos os comentários que você pode nos dar para ajudá-lo a melhorá-lo.</span><span class="sxs-lookup"><span data-stu-id="e3464-154">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="e3464-155">Você nos verá nos fóruns do [Unity](https://aka.ms/unityforums) marcando sua postagem no fórum com o **Microsoft**  +  **OpenXR** e o **HoloLens 2** ou a **realidade mista do Windows**.</span><span class="sxs-lookup"><span data-stu-id="e3464-155">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3464-156">Veja também</span><span class="sxs-lookup"><span data-stu-id="e3464-156">See also</span></span>

* [<span data-ttu-id="e3464-157">Como configurar seu projeto sem o MRTK</span><span class="sxs-lookup"><span data-stu-id="e3464-157">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="e3464-158">Configurações recomendadas do Unity</span><span class="sxs-lookup"><span data-stu-id="e3464-158">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="e3464-159">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="e3464-159">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)