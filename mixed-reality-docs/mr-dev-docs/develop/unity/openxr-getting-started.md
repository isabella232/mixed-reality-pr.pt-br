---
title: Usando o plug-in OpenXR de realidade misturada para o Unity
description: Saiba como habilitar o plug-in OpenXR de realidade misturada para projetos do Unity.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução
ms.openlocfilehash: 05adee2d88bc90dcfb5cf8b780212c7622aff786
ms.sourcegitcommit: ce4975f584bb62075bcb66349237b77081fb982b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97644913"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="45247-104">Usando o plug-in OpenXR de realidade misturada para o Unity</span><span class="sxs-lookup"><span data-stu-id="45247-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="45247-105">A partir da versão 2020,2 do Unity, o pacote de plugin OpenXR de realidade misturada da Microsoft está disponível usando o UPM (Gerenciador de pacotes do Unity).</span><span class="sxs-lookup"><span data-stu-id="45247-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="45247-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="45247-106">Prerequisites</span></span>

*   <span data-ttu-id="45247-107">Unity 2020,2 ou posterior</span><span class="sxs-lookup"><span data-stu-id="45247-107">Unity 2020.2 or later</span></span>
*   <span data-ttu-id="45247-108">Plug-in do Unity OpenXR 0.1.1 ou posterior</span><span class="sxs-lookup"><span data-stu-id="45247-108">Unity OpenXR plugin 0.1.1 or later</span></span>
*   <span data-ttu-id="45247-109">Visual Studio 2019 ou posterior</span><span class="sxs-lookup"><span data-stu-id="45247-109">Visual Studio 2019 or later</span></span>
*   <span data-ttu-id="45247-110">Instalar o suporte da plataforma **UWP** no Unity para aplicativos do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="45247-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="45247-111">Se você estiver criando aplicativos VR no computador Windows, o plug-in OpenXR de realidade misturada não será necessariamente necessário.</span><span class="sxs-lookup"><span data-stu-id="45247-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="45247-112">No entanto, você desejará instalar o plug-in se estiver personalizando o mapeamento do controlador para controladores do HP reverbo G2 ou compilando aplicativos que funcionam em headsets de HoloLens 2 e VR.</span><span class="sxs-lookup"><span data-stu-id="45247-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="45247-113">Instalando o plug-in OpenXR de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="45247-113">Installing the Mixed Reality OpenXR plugin</span></span>

<span data-ttu-id="45247-114">Seu projeto precisa instalar o plug-in **OpenXR** e pacotes de **Gerenciamento de plugin XR** antes de usar o plug-in OpenXR da realidade mista.</span><span class="sxs-lookup"><span data-stu-id="45247-114">Your project needs to install the **OpenXR Plugin** and **XR Plugin Management** packages before using the Mixed Reality OpenXR Plugin.</span></span> <span data-ttu-id="45247-115">Se você já os instalou, ótimo!</span><span class="sxs-lookup"><span data-stu-id="45247-115">If you've already installed them, great!</span></span> <span data-ttu-id="45247-116">Caso contrário, a instalação do plug-in OpenXR de realidade misturada os instalará automaticamente como dependências:</span><span class="sxs-lookup"><span data-stu-id="45247-116">If not, installing the Mixed Reality OpenXR plugin will automatically install them as dependencies:</span></span>

1. <span data-ttu-id="45247-117">No editor do Unity, navegue até **Editar configurações do projeto > > Gerenciador de pacotes**</span><span class="sxs-lookup"><span data-stu-id="45247-117">In the Unity Editor, navigate to **Edit > Project Settings > Package Manager**</span></span>
2. <span data-ttu-id="45247-118">Expanda a seção **registros no escopo** , insira as informações a seguir e selecione **salvar**:</span><span class="sxs-lookup"><span data-stu-id="45247-118">Expand the **Scoped Registries** section, enter the following information, and select **Save**:</span></span>   
    * <span data-ttu-id="45247-119">Definir o **nome** para a **realidade mista da Microsoft**</span><span class="sxs-lookup"><span data-stu-id="45247-119">Set **Name** to **Microsoft Mixed Reality**</span></span>
    * <span data-ttu-id="45247-120">Definir **URL** como **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span><span class="sxs-lookup"><span data-stu-id="45247-120">Set **URL** to **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span></span>
    * <span data-ttu-id="45247-121">Definir **escopo (s)** como **com. Microsoft. mixedreality**</span><span class="sxs-lookup"><span data-stu-id="45247-121">Set **Scope(s)** to **com.microsoft.mixedreality**</span></span>

3. <span data-ttu-id="45247-122">Em **Configurações avançadas**, selecione **habilitar pacotes de visualização**</span><span class="sxs-lookup"><span data-stu-id="45247-122">Under **Advanced Settings**, select **Enable Preview Packages**</span></span>

![Captura de tela da janela do Gerenciador de pacotes do Unity aberta nas configurações do projeto](images/openxr-img-01.png)

<span data-ttu-id="45247-124">O Gerenciador de pacotes do Unity usa um arquivo de manifesto chamado *manifest.jsno* para determinar quais pacotes instalar e os registros dos quais eles podem ser instalados.</span><span class="sxs-lookup"><span data-stu-id="45247-124">The Unity Package Manager uses a manifest file named *manifest.json* to determine which packages to install and the registries they can be installed from.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45247-125">O OpenXR ainda é experimental no Unity e esse processo pode mudar ao longo do tempo enquanto trabalhamos para otimizar a experiência do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="45247-125">OpenXR is still experimental in Unity and this process may change over time as we work to optimize the developer experience.</span></span>

### <a name="registering-the-mixed-reality-dependency"></a><span data-ttu-id="45247-126">Registrando a dependência da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="45247-126">Registering the Mixed Reality dependency</span></span>

<span data-ttu-id="45247-127">Depois que o registro com escopo do Microsoft Mixed Reality tiver sido adicionado ao manifesto, o pacote OpenXR poderá ser especificado.</span><span class="sxs-lookup"><span data-stu-id="45247-127">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the OpenXR package can be specified.</span></span>

<span data-ttu-id="45247-128">Para adicionar o pacote OpenXR:</span><span class="sxs-lookup"><span data-stu-id="45247-128">To add the OpenXR package:</span></span>

1. <span data-ttu-id="45247-129">Abra **<projectRoot> /Packages/manifest.jsem** um editor de texto como Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="45247-129">Open **<projectRoot>/Packages/manifest.json** in a text editor like Visual Studio Code</span></span>
2. <span data-ttu-id="45247-130">Modifique a seção dependências dos *pacotes/manifest.jsno* arquivo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="45247-130">Modify the dependencies section of the *Packages/manifest.json* file as follows:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45247-131">Pode haver mais dependências no arquivo de manifesto do que mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="45247-131">There may be more dependencies in your manifest file than shown here.</span></span> <span data-ttu-id="45247-132">Não exclua nenhum deles, basta adicionar a dependência OpenXR à lista.</span><span class="sxs-lookup"><span data-stu-id="45247-132">Don't delete any of them, just add the OpenXR dependency to the list.</span></span>

```
  "dependencies": {
    "com.microsoft.mixedreality.openxr": "0.1.0",
  }
```

3. <span data-ttu-id="45247-133">Salve o arquivo, volte para o editor do Unity e abra o **Gerenciador de pacotes** para confirmar se o plug-in está instalado:</span><span class="sxs-lookup"><span data-stu-id="45247-133">Save the file, switch back to the Unity Editor, and open the **Package Manager** to confirm the plugin is installed:</span></span> 

![Captura de tela do Gerenciador de pacotes do Unity aberta no editor do Unity com realidade misturada OpenXR plugin realçado](images/openxr-img-03.png)

> [!Note] 
> <span data-ttu-id="45247-135">Se o pacote OpenXR for removido usando o Gerenciador de pacotes do Unity, você precisará adicioná-lo novamente usando as etapas descritas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="45247-135">If the OpenXR package is removed using the Unity Package Manager, you'll have to re-add it using the previously described steps.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="45247-136">Configurando o gerenciamento de plugin XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="45247-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="45247-137">Para definir OpenXR como o tempo de execução no Unity:</span><span class="sxs-lookup"><span data-stu-id="45247-137">To set OpenXR as the the runtime in Unity:</span></span> 

1. <span data-ttu-id="45247-138">No editor do Unity, navegue até **editar > configurações do projeto**</span><span class="sxs-lookup"><span data-stu-id="45247-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="45247-139">Na lista de configurações, selecione **Gerenciamento de plugin XR**</span><span class="sxs-lookup"><span data-stu-id="45247-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="45247-140">Verifique as caixas **inicializar XR nas inicializações** e **OpenXR (visualização)**</span><span class="sxs-lookup"><span data-stu-id="45247-140">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="45247-141">Se estiver direcionando para o HoloLens 2, verifique se você está na plataforma UWP e selecione **conjunto de recursos do Microsoft HoloLens**</span><span class="sxs-lookup"><span data-stu-id="45247-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="45247-143">Se você vir um ícone de aviso vermelho ao lado do **plug-in OpenXR (versão prévia)**, clique no ícone e selecione **corrigir tudo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="45247-143">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="45247-144">O editor do Unity pode precisar ser reiniciado para que as alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="45247-144">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de tela da janela de validação do projeto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="45247-146">Agora você está pronto para começar a desenvolver com o OpenXR no Unity!</span><span class="sxs-lookup"><span data-stu-id="45247-146">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="45247-147">Continue na próxima seção para aprender a usar os exemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="45247-147">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="45247-148">Optimization</span><span class="sxs-lookup"><span data-stu-id="45247-148">Optimization</span></span>

<span data-ttu-id="45247-149">Se você estiver desenvolvendo para o HoloLens 2, navegue até a **realidade misturada> OpenXR > aplicar as configurações de projeto recomendadas para o HoloLens 2** para obter melhor desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="45247-149">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Captura de tela do item de menu da realidade misturada abrir com OpenXR selecionado](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="45247-151">Experimente os bastidores de exemplo do Unity</span><span class="sxs-lookup"><span data-stu-id="45247-151">Try out the Unity sample scenes</span></span>

<span data-ttu-id="45247-152">Para utilizar um ou mais dos exemplos, instale o [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) do **pacote Manager**:</span><span class="sxs-lookup"><span data-stu-id="45247-152">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Pacakage Manager**:</span></span>

![Captura de tela do Gerenciador de pacotes do Unity aberta no editor do Unity com o AR Foundation realçado](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="45247-154">Exemplos de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="45247-154">HoloLens 2 samples</span></span>

1. <span data-ttu-id="45247-155">No editor do Unity, navegue até a **janela > Gerenciador de pacotes**</span><span class="sxs-lookup"><span data-stu-id="45247-155">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="45247-156">Na lista de pacotes, selecione **OpenXR de realidade misturada plug-in**</span><span class="sxs-lookup"><span data-stu-id="45247-156">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="45247-157">Localize o exemplo na lista de **exemplos** e selecione **importar**</span><span class="sxs-lookup"><span data-stu-id="45247-157">Locate the sample in the **Samples** list and select **Import**</span></span>

![Captura de tela do Gerenciador de pacotes do Unity abrir no editor do Unity com realidade misturada OpenXR plugin selecionado e exemplos de importação do botão realçado](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
>  <span data-ttu-id="45247-159">Quando um pacote é atualizado, o Unity fornece a opção de atualizar amostras importadas.</span><span class="sxs-lookup"><span data-stu-id="45247-159">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="45247-160">A atualização de um exemplo importado substituirá as alterações feitas no exemplo e nos ativos associados.</span><span class="sxs-lookup"><span data-stu-id="45247-160">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="next-steps"></a><span data-ttu-id="45247-161">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="45247-161">Next steps</span></span> 

<span data-ttu-id="45247-162">Agora que você tem o projeto configurado para OpenXR e tem acesso a exemplos, confira quais [recursos](openxr-supported-features.md) têm suporte no momento em nosso plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="45247-162">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="see-also"></a><span data-ttu-id="45247-163">Confira também</span><span class="sxs-lookup"><span data-stu-id="45247-163">See also</span></span>
* [<span data-ttu-id="45247-164">Configurando seu projeto sem MRTK</span><span class="sxs-lookup"><span data-stu-id="45247-164">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="45247-165">Configurações recomendadas do Unity</span><span class="sxs-lookup"><span data-stu-id="45247-165">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="45247-166">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="45247-166">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)