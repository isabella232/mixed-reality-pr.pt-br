---
title: Como escolher uma versão do Unity e um plug-in de XR
description: Mantenha-se atualizado sobre as recomendações de plug-in mais recentes do Unity e do XR para o desenvolvimento de aplicativos do HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, Unity
ms.openlocfilehash: febeb46972935a02d9c945e2a0cafabebedd0715
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333378"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="dbfda-104">Como escolher uma versão do Unity e um plug-in de XR</span><span class="sxs-lookup"><span data-stu-id="dbfda-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="dbfda-105">Embora, no momento, **recomendamos a instalação do Unity 2019,4 LTS e o uso da XR interna herdada** para o desenvolvimento de realidade misturada, você também pode criar aplicativos com outras configurações do Unity.</span><span class="sxs-lookup"><span data-stu-id="dbfda-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="dbfda-106">Unity 2019,4 LTS (recomendado)</span><span class="sxs-lookup"><span data-stu-id="dbfda-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="dbfda-107">A configuração atual do Unity recomendada pela Microsoft para o HoloLens 2 e o desenvolvimento de realidade mista do Windows é o **Unity 2019,4 LTS usando o suporte interno a XR herdado** .</span><span class="sxs-lookup"><span data-stu-id="dbfda-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="dbfda-108">A melhor maneira de instalar e gerenciar o Unity é por meio do <a href="https://unity3d.com/get-unity/download" target="_blank">[Hub do Unity]</a>.</span><span class="sxs-lookup"><span data-stu-id="dbfda-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="dbfda-109">Quando ele estiver instalado, abra o Hub do Unity:</span><span class="sxs-lookup"><span data-stu-id="dbfda-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="dbfda-110">Selecione a guia **instalações** e escolha **Adicionar**</span><span class="sxs-lookup"><span data-stu-id="dbfda-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="dbfda-111">Selecione Unity 2019,4 LTS e clique em **Avançar**</span><span class="sxs-lookup"><span data-stu-id="dbfda-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Instalar nova versão do Hub do Unity](images/unity-hub-img-01.png)

3. <span data-ttu-id="dbfda-113">Verifique os seguintes componentes em **' plataformas '**</span><span class="sxs-lookup"><span data-stu-id="dbfda-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="dbfda-114">**Suporte de build da Plataforma Universal do Windows**</span><span class="sxs-lookup"><span data-stu-id="dbfda-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="dbfda-115">**Suporte de build do Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="dbfda-115">**Windows Build Support (IL2CPP)**</span></span>

![Opção do Unity de suporte de build da Plataforma Universal do Windows](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="dbfda-117">Se você instalou o Unity sem essas opções, poderá adicioná-los por meio do menu **' Adicionar módulos '** no Hub do Unity:</span><span class="sxs-lookup"><span data-stu-id="dbfda-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opção do Unity de suporte de build do Windows](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="dbfda-119">Para começar a usar a XR interna herdada no Unity 2019,4 LTS, clique aqui:</span><span class="sxs-lookup"><span data-stu-id="dbfda-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dbfda-120">Configurar a XR interna herdada</span><span class="sxs-lookup"><span data-stu-id="dbfda-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="dbfda-121">O Unity preteriu seu suporte interno de XR herdado a partir do Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="dbfda-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="dbfda-122">Embora o Unity 2019 ofereça uma nova estrutura de plug-ins XR, a Microsoft não recomenda esse caminho no Unity 2019 devido a incompatibilidades de âncoras espaciais do Azure com o AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="dbfda-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="dbfda-123">No Unity 2020, há suporte para âncoras espaciais do Azure na estrutura de plug-ins do XR.</span><span class="sxs-lookup"><span data-stu-id="dbfda-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="dbfda-124">Se você estiver desenvolvendo aplicativos para o HoloLens (1º gen), esses headsets permanecerão com suporte no Unity 2019 LTS com a XR interna herdada para o ciclo de vida completo do Unity 2019 LTS até o Mid-2022.</span><span class="sxs-lookup"><span data-stu-id="dbfda-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="dbfda-125">Unity 2020,3 LTS</span><span class="sxs-lookup"><span data-stu-id="dbfda-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="dbfda-126">Se você estiver usando o **Unity 2020,3 LTS**, poderá usar o **plug-in do Windows XR** para desenvolver aplicativos do HoloLens 2 e do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="dbfda-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="dbfda-127">No entanto, há problemas conhecidos que afetam a estabilidade do holograma e outros recursos no HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="dbfda-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="dbfda-128">Os aplicativos de comunicação remota do aplicativo Holographic usando o destino de compilação Plataforma Universal do Windows não estão funcionando.</span><span class="sxs-lookup"><span data-stu-id="dbfda-128">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="dbfda-129">O sistema de trabalhos gráficos do Unity é padronizado, embora não seja compatível com projetos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="dbfda-129">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="dbfda-130">Se você optar por usar o Unity 2020, certifique-se de atualizar para o Unity 2020.3.6 F1 ou versões posteriores para garantir que sua experiência do usuário seja adequada para a estabilidade do holograma.</span><span class="sxs-lookup"><span data-stu-id="dbfda-130">If you choose to use Unity 2020, be sure to upgrade to Unity 2020.3.6f1 or later versions to ensure your user experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dbfda-131">Como usar o plug-in de XR do Windows</span><span class="sxs-lookup"><span data-stu-id="dbfda-131">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="dbfda-132">Usando OpenXR</span><span class="sxs-lookup"><span data-stu-id="dbfda-132">Using OpenXR</span></span>

<span data-ttu-id="dbfda-133">O Unity 2020,3 LTS também dá suporte a uma visualização pública do plug-in **OpenXR da realidade mista** .</span><span class="sxs-lookup"><span data-stu-id="dbfda-133">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="dbfda-134">O plug-in Mixed Reality OpenXR dá suporte total ao AR Foundation 4,0, fornecendo implementações ARPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="dbfda-134">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="dbfda-135">Isso permite que você escreva um código de teste de clique uma vez que se estenda a telefones 2 e ARCore/ARKit celulares e tablets.</span><span class="sxs-lookup"><span data-stu-id="dbfda-135">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="dbfda-136">Posteriormente neste ano, o **unity 2020,3 LTS com o plug-in OpenXR** se tornará a configuração de Unity recomendada e futuros recursos do HoloLens 2 no Unity serão expostos somente por meio desse plug-in.</span><span class="sxs-lookup"><span data-stu-id="dbfda-136">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dbfda-137">Usando o plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="dbfda-137">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="dbfda-138">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="dbfda-138">Unity 2021.1</span></span>

<span data-ttu-id="dbfda-139">Se você estiver experimentando compilações iniciais do **Unity 2021,1** , deverá avançar para o **plug-in do OpenXR**, pois o plug-in do Windows XR foi preterido lá.</span><span class="sxs-lookup"><span data-stu-id="dbfda-139">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="dbfda-140">A partir do Unity 2021,2, o plug-in OpenXR será o único caminho para o desenvolvimento de realidade misturada, pois o plug-in do Windows XR não terá mais suporte.</span><span class="sxs-lookup"><span data-stu-id="dbfda-140">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="dbfda-141">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="dbfda-141">Unity 2018.4 LTS</span></span>

<span data-ttu-id="dbfda-142">Se você já tiver um projeto usando o Unity 2018,4 LTS, o seu mecanismo do Unity continuará a ter suporte por dois anos após seu lançamento.</span><span class="sxs-lookup"><span data-stu-id="dbfda-142">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="dbfda-143">O Unity 2018 LTS atingirá o fim do serviço no Spring de 2021.</span><span class="sxs-lookup"><span data-stu-id="dbfda-143">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
