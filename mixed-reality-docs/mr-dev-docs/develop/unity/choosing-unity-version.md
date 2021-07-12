---
title: Como escolher uma versão do Unity e um plug-in de XR
description: Mantenha-se atualizado sobre as recomendações de plug-in do Unity e XR mais recentes para HoloLens aplicativo.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603677"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="02d1e-104">Como escolher uma versão do Unity e um plug-in de XR</span><span class="sxs-lookup"><span data-stu-id="02d1e-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="02d1e-105">Embora seja recomendável instalar o **Unity 2020.3 LTS** com o plug-in OpenXR de Realidade Misturada mais recente para desenvolvimento de Realidade Misturada, você também pode criar aplicativos com outras configurações do Unity.</span><span class="sxs-lookup"><span data-stu-id="02d1e-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="02d1e-106">Unity 2020.3 LTS (recomendado)</span><span class="sxs-lookup"><span data-stu-id="02d1e-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="02d1e-107">A configuração atual recomendada do Unity da Microsoft para HoloLens 2 e Windows Mixed Reality é **o Unity 2020.3 LTS** com o plug-in OpenXR de Realidade Misturada mais recente.</span><span class="sxs-lookup"><span data-stu-id="02d1e-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="02d1e-108">Você **deve usar** o patch do Unity versão 2020.3.8f1 ou posterior para evitar problemas de desempenho conhecidos com builds anteriores de 2020.3.</span><span class="sxs-lookup"><span data-stu-id="02d1e-108">You **must** use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="02d1e-109">O Unity 2020 não dá suporte ao direcionamento HoloLens (1ª geração).</span><span class="sxs-lookup"><span data-stu-id="02d1e-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="02d1e-110">Esses headsets permanecem com suporte no **[Unity 2019 LTS](#unity-20194-lts)** com XR integrado herdado para o ciclo de vida completo do Unity 2019 LTS até meados de 2022.</span><span class="sxs-lookup"><span data-stu-id="02d1e-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="02d1e-111">A melhor maneira de instalar e gerenciar o Unity é por meio do **Hub do Unity:**</span><span class="sxs-lookup"><span data-stu-id="02d1e-111">The best way to install and manage Unity is through the **Unity Hub**:</span></span>

1. <span data-ttu-id="02d1e-112">Instale <a href="https://unity3d.com/get-unity/download" target="_blank">**o Hub do Unity.**</a></span><span class="sxs-lookup"><span data-stu-id="02d1e-112">Install <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>.</span></span>
2. <span data-ttu-id="02d1e-113">Selecione a **guia Instalar** e escolha **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="02d1e-113">Select the **Installs** tab and choose **Add**.</span></span>
3. <span data-ttu-id="02d1e-114">Selecione **Unity 2020.3 LTS** e clique em **Próximo.**</span><span class="sxs-lookup"><span data-stu-id="02d1e-114">Select **Unity 2020.3 LTS** and click **Next**.</span></span>

![Instalar nova versão do Hub do Unity](images/unity-hub-img-01.png)

4. <span data-ttu-id="02d1e-116">Verifique os seguintes componentes em **'Plataformas':**</span><span class="sxs-lookup"><span data-stu-id="02d1e-116">Check the following components under **'Platforms'**:</span></span>
    * <span data-ttu-id="02d1e-117">**Suporte de build da Plataforma Universal do Windows**</span><span class="sxs-lookup"><span data-stu-id="02d1e-117">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="02d1e-118">**Suporte de build do Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="02d1e-118">**Windows Build Support (IL2CPP)**</span></span>

![Opção do Unity de suporte de build da Plataforma Universal do Windows](../images/Unity_Install_Option_UWP.png)

5. <span data-ttu-id="02d1e-120">Se você instalou o Unity anteriormente sem essas opções, poderá adicioná-las por meio do menu **'Adicionar Módulos'** no Hub do Unity:</span><span class="sxs-lookup"><span data-stu-id="02d1e-120">If you previously installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opção do Unity de suporte de build do Windows](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="02d1e-122">Depois que o Unity 2020.3 estiver instalado, começar a criar um projeto ou atualizar um projeto existente usando o plug-in OpenXR de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="02d1e-122">Once you have Unity 2020.3 installed, get started creating a project or upgrading an existing project using the Mixed Reality OpenXR plugin:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="02d1e-123">Configurar seu projeto com o plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="02d1e-123">Set up your project with the OpenXR plugin</span></span>](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="02d1e-124">Embora seja recomendável usar o OpenXR para todos os novos projetos, o Unity 2020.3 LTS também dá suporte ao [plug-in Windows XR.](xr-project-setup.md?tabs=windowsxr)</span><span class="sxs-lookup"><span data-stu-id="02d1e-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](xr-project-setup.md?tabs=windowsxr).</span></span> <span data-ttu-id="02d1e-125">Esse plug-in tem suporte total, embora não receba novos recursos, como o suporte do AR Foundation 4.0.</span><span class="sxs-lookup"><span data-stu-id="02d1e-125">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="02d1e-126">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="02d1e-126">Unity 2019.4 LTS</span></span>

<span data-ttu-id="02d1e-127">Se você precisar usar o Unity 2019, poderá usar **o Unity 2019 LTS com xR integrado herdado.**</span><span class="sxs-lookup"><span data-stu-id="02d1e-127">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="02d1e-128">Para começar a trabalhar com o XR integrado herdados no Unity 2019.4 LTS, clique aqui:</span><span class="sxs-lookup"><span data-stu-id="02d1e-128">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="02d1e-129">Configurar seu projeto com o XR integrado herddo</span><span class="sxs-lookup"><span data-stu-id="02d1e-129">Set up your project with Legacy Built-in XR</span></span>](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="02d1e-130">O Unity preterido seu suporte de XR integrado herdado a partir do Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="02d1e-130">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="02d1e-131">Embora o Unity 2019 ofereça uma nova estrutura de plug-in XR, a Microsoft não está recomendando esse caminho no Unity 2019 devido a incompatibilidades das Âncoras Espaciais do Azure com o AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="02d1e-131">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="02d1e-132">No Unity 2020, as Âncoras Espaciais do Azure são suportadas na estrutura de plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="02d1e-132">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="02d1e-133">Se você estiver desenvolvendo aplicativos para HoloLens (1ª geração), esses headsets permanecerão com suporte no Unity 2019 LTS com XR integrado herdado para o ciclo de vida completo do Unity 2019 LTS até meados de 2022.</span><span class="sxs-lookup"><span data-stu-id="02d1e-133">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20212"></a><span data-ttu-id="02d1e-134">Unity 2021.2</span><span class="sxs-lookup"><span data-stu-id="02d1e-134">Unity 2021.2</span></span>

<span data-ttu-id="02d1e-135">Se você estiver tentando os primeiros builds do **Unity 2021.2,** vá para o [**plug-in OpenXR**](xr-project-setup.md?tabs=openxr)do Mixed Reality .</span><span class="sxs-lookup"><span data-stu-id="02d1e-135">If you are trying out early **Unity 2021.2** builds, get started with the [**Mixed Reality OpenXR plugin**](xr-project-setup.md?tabs=openxr).</span></span> <span data-ttu-id="02d1e-136">O plug-in OpenXR é o único caminho para o desenvolvimento de realidade misturada no Unity 2021.2 e posterior, pois a versão final do Unity para dar suporte ao plug-in Windows XR era o Unity 2021.1.</span><span class="sxs-lookup"><span data-stu-id="02d1e-136">The OpenXR plugin is the only path for mixed reality development in Unity 2021.2 and later, as the final Unity version to support the Windows XR plugin was Unity 2021.1.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="02d1e-137">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="02d1e-137">Unity 2018.4 LTS</span></span>

<span data-ttu-id="02d1e-138">O Unity 2018.4 LTS atingiu o final da janela de suporte do Long-Term de dois anos do Unity e não está mais recebendo atualizações do Unity, embora seus projetos continuem sendo executados.</span><span class="sxs-lookup"><span data-stu-id="02d1e-138">Unity 2018.4 LTS has reached the end of Unity's two-year Long-Term Support window and is no longer receiving updates from Unity, although your projects will continue to run.</span></span>

<span data-ttu-id="02d1e-139">Se você tiver um projeto do Unity 2018, considere planejar uma migração para o Unity 2020.3 LTS e o plug-in OpenXR de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="02d1e-139">If you have a Unity 2018 project, you should consider planning for a migration forward to Unity 2020.3 LTS and the Mixed Reality OpenXR plugin.</span></span>