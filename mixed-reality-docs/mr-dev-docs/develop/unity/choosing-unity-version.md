---
title: Como escolher uma versão do Unity e um plug-in de XR
description: Mantenha-se atualizado sobre as recomendações de plug-in mais recentes do Unity e do XR para o desenvolvimento de aplicativos do HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 05/27/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, Unity
ms.openlocfilehash: 1f658c0e69091ce0aaeb37b7f427e57f060c3fb2
ms.sourcegitcommit: 62e5909b837c9c7ecedd040164f2308868db4723
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2021
ms.locfileid: "111741918"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="7f768-104">Como escolher uma versão do Unity e um plug-in de XR</span><span class="sxs-lookup"><span data-stu-id="7f768-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="7f768-105">Embora, no momento, **recomendamos a instalação do Unity 2020,3 LTS com o plug-in OpenXR da realidade mista mais recente** para o desenvolvimento de realidade misturada, você também pode criar aplicativos com outras configurações do Unity.</span><span class="sxs-lookup"><span data-stu-id="7f768-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="7f768-106">Unity 2020,3 LTS (recomendado)</span><span class="sxs-lookup"><span data-stu-id="7f768-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="7f768-107">A configuração atual recomendada do Unity da Microsoft para o HoloLens 2 e o desenvolvimento de realidade mista do Windows é **o Unity 2020,3 LTS com o plug-in OpenXR da realidade mista mais recente**.</span><span class="sxs-lookup"><span data-stu-id="7f768-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7f768-108">O Unity 2020 não dá suporte ao direcionamento de HoloLens (1ª gen).</span><span class="sxs-lookup"><span data-stu-id="7f768-108">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="7f768-109">Esses headsets permanecem com suporte no **[unity 2019 LTS](#unity-20194-lts)** com a XR interna herdada para o ciclo de vida completo do Unity 2019 LTS até o mid-2022.</span><span class="sxs-lookup"><span data-stu-id="7f768-109">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="7f768-110">O plug-in Mixed Reality OpenXR dá suporte total ao AR Foundation 4,0, fornecendo implementações ARPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="7f768-110">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="7f768-111">Isso permite que você escreva um código de teste de clique uma vez que se estenda a telefones 2 e ARCore/ARKit celulares e tablets.</span><span class="sxs-lookup"><span data-stu-id="7f768-111">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

<span data-ttu-id="7f768-112">A melhor maneira de instalar e gerenciar o Unity é por meio do <a href="https://unity3d.com/get-unity/download" target="_blank">Hub do Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="7f768-112">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="7f768-113">Quando ele estiver instalado, abra o Hub do Unity:</span><span class="sxs-lookup"><span data-stu-id="7f768-113">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="7f768-114">Selecione a guia **instalações** e escolha **Adicionar**</span><span class="sxs-lookup"><span data-stu-id="7f768-114">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="7f768-115">Selecione Unity 2020,3 LTS e clique em **Avançar**</span><span class="sxs-lookup"><span data-stu-id="7f768-115">Select Unity 2020.3 LTS and click **Next**</span></span>

![Instalar nova versão do Hub do Unity](images/unity-hub-img-01.png)

3. <span data-ttu-id="7f768-117">Verifique os seguintes componentes em **' plataformas '**</span><span class="sxs-lookup"><span data-stu-id="7f768-117">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="7f768-118">**Suporte de build da Plataforma Universal do Windows**</span><span class="sxs-lookup"><span data-stu-id="7f768-118">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="7f768-119">**Suporte de build do Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="7f768-119">**Windows Build Support (IL2CPP)**</span></span>

![Opção do Unity de suporte de build da Plataforma Universal do Windows](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="7f768-121">Se você instalou o Unity sem essas opções, poderá adicioná-los por meio do menu **' Adicionar módulos '** no Hub do Unity:</span><span class="sxs-lookup"><span data-stu-id="7f768-121">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opção do Unity de suporte de build do Windows](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="7f768-123">Usando o plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="7f768-123">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="7f768-124">Embora seja recomendável usar OpenXR para todos os novos projetos, o Unity 2020,3 LTS também dá suporte ao **[plug-in do Windows XR](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)**.</span><span class="sxs-lookup"><span data-stu-id="7f768-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the **[Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)**.</span></span> <span data-ttu-id="7f768-125">Os problemas conhecidos que afetam a estabilidade do holograma e outros recursos no HoloLens 2 incluem:</span><span class="sxs-lookup"><span data-stu-id="7f768-125">Known issues that affect hologram stability and other features on HoloLens 2 include:</span></span>
>
> * <span data-ttu-id="7f768-126">Os aplicativos de comunicação remota do aplicativo Holographic usando o destino de compilação Plataforma Universal do Windows não estão funcionando.</span><span class="sxs-lookup"><span data-stu-id="7f768-126">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
> * <span data-ttu-id="7f768-127">O sistema de trabalhos gráficos do Unity é padronizado, embora não seja compatível com projetos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7f768-127">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="7f768-128">Unity 2019,4 LTS</span><span class="sxs-lookup"><span data-stu-id="7f768-128">Unity 2019.4 LTS</span></span>

<span data-ttu-id="7f768-129">Se você precisar usar o Unity 2019, poderá usar o **unity 2019 LTS com o XR interno do Legacy**.</span><span class="sxs-lookup"><span data-stu-id="7f768-129">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="7f768-130">Para começar a usar a XR interna herdada no Unity 2019,4 LTS, clique aqui:</span><span class="sxs-lookup"><span data-stu-id="7f768-130">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7f768-131">Configurar a XR interna herdada</span><span class="sxs-lookup"><span data-stu-id="7f768-131">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="7f768-132">O Unity preteriu seu suporte interno de XR herdado a partir do Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="7f768-132">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="7f768-133">Embora o Unity 2019 ofereça uma nova estrutura de plug-ins XR, a Microsoft não recomenda esse caminho no Unity 2019 devido a incompatibilidades de âncoras espaciais do Azure com o AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="7f768-133">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="7f768-134">No Unity 2020, há suporte para âncoras espaciais do Azure na estrutura de plug-ins do XR.</span><span class="sxs-lookup"><span data-stu-id="7f768-134">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="7f768-135">Se você estiver desenvolvendo aplicativos para o HoloLens (1º gen), esses headsets permanecerão com suporte no Unity 2019 LTS com a XR interna herdada para o ciclo de vida completo do Unity 2019 LTS até o Mid-2022.</span><span class="sxs-lookup"><span data-stu-id="7f768-135">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="7f768-136">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="7f768-136">Unity 2021.1</span></span>

<span data-ttu-id="7f768-137">Se você estiver experimentando compilações iniciais do **Unity 2021,1** , deverá avançar para o **plug-in do OpenXR**, pois o plug-in do Windows XR foi preterido lá.</span><span class="sxs-lookup"><span data-stu-id="7f768-137">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="7f768-138">A partir do Unity 2021,2, o plug-in OpenXR será o único caminho para o desenvolvimento de realidade misturada, pois o plug-in do Windows XR não terá mais suporte.</span><span class="sxs-lookup"><span data-stu-id="7f768-138">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="7f768-139">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="7f768-139">Unity 2018.4 LTS</span></span>

<span data-ttu-id="7f768-140">Se você já tiver um projeto usando o Unity 2018,4 LTS, o seu mecanismo do Unity continuará a ter suporte por dois anos após seu lançamento.</span><span class="sxs-lookup"><span data-stu-id="7f768-140">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="7f768-141">O Unity 2018 LTS atingirá o fim do serviço no Spring de 2021.</span><span class="sxs-lookup"><span data-stu-id="7f768-141">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
