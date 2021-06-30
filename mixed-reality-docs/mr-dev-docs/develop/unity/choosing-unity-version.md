---
title: Como escolher uma versão do Unity e um plug-in de XR
description: Mantenha-se atualizado sobre as recomendações de plug-in do Unity e XR mais recentes para o desenvolvimento de aplicativos holoLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, unity
ms.openlocfilehash: 11f930f014ff579db1f8845d52b7a2d65dd85d6b
ms.sourcegitcommit: 4ea9ba1ca1cde426b016111c4176a4b0a9c17553
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113080693"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="968c9-104">Como escolher uma versão do Unity e um plug-in de XR</span><span class="sxs-lookup"><span data-stu-id="968c9-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="968c9-105">Embora seja recomendável instalar o **Unity 2020.3 LTS** com o plug-in OpenXR de Realidade Misturada mais recente para desenvolvimento de Realidade Misturada, você também pode criar aplicativos com outras configurações do Unity.</span><span class="sxs-lookup"><span data-stu-id="968c9-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="968c9-106">Unity 2020.3 LTS (recomendado)</span><span class="sxs-lookup"><span data-stu-id="968c9-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="968c9-107">A configuração atual recomendada do Unity da Microsoft para o holoLens 2 e Windows Mixed Reality desenvolvimento é **o Unity 2020.3 LTS** com o plug-in OpenXR de Realidade Misturada mais recente.</span><span class="sxs-lookup"><span data-stu-id="968c9-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="968c9-108">Você DEVE usar o patch do Unity versão 2020.3.8f1 ou posterior para evitar problemas de desempenho conhecidos com builds anteriores de 2020.3.</span><span class="sxs-lookup"><span data-stu-id="968c9-108">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="968c9-109">O Unity 2020 não dá suporte ao direcionamento do HoloLens (1ª geração).</span><span class="sxs-lookup"><span data-stu-id="968c9-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="968c9-110">Esses headsets permanecem com suporte no **[Unity 2019 LTS](#unity-20194-lts)** com XR integrado herdado para o ciclo de vida completo do Unity 2019 LTS até meados de 2022.</span><span class="sxs-lookup"><span data-stu-id="968c9-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>
>
> [!NOTE]
> <span data-ttu-id="968c9-111">Azure Remote Rendering ainda não enviou uma versão atualizada com suporte ao Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="968c9-111">Azure Remote Rendering has not yet shipped an updated release supporting Unity 2020.</span></span>
>
> <span data-ttu-id="968c9-112">Se o projeto do Unity usar Azure Remote Rendering, recomendamos manter a atualização do projeto para o Unity 2020 até que um pacote atualizado seja disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="968c9-112">If your Unity project uses Azure Remote Rendering, we recommend holding off on upgrading your project to Unity 2020 until an updated package is available.</span></span>

<span data-ttu-id="968c9-113">A melhor maneira de instalar e gerenciar o Unity é por meio do <a href="https://unity3d.com/get-unity/download" target="_blank">Hub do Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="968c9-113">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="968c9-114">Quando ele estiver instalado, abra o Hub do Unity:</span><span class="sxs-lookup"><span data-stu-id="968c9-114">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="968c9-115">Selecione a **guia Instalar e** escolha **ADICIONAR**</span><span class="sxs-lookup"><span data-stu-id="968c9-115">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="968c9-116">Selecione Unity 2020.3 LTS e clique em **Próximo**</span><span class="sxs-lookup"><span data-stu-id="968c9-116">Select Unity 2020.3 LTS and click **Next**</span></span>

![Nova versão instal do hub do Unity](images/unity-hub-img-01.png)

3. <span data-ttu-id="968c9-118">Verifique os componentes a seguir **em 'Plataformas'**</span><span class="sxs-lookup"><span data-stu-id="968c9-118">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="968c9-119">**Suporte de build da Plataforma Universal do Windows**</span><span class="sxs-lookup"><span data-stu-id="968c9-119">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="968c9-120">**Suporte de build do Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="968c9-120">**Windows Build Support (IL2CPP)**</span></span>

![Opção do Unity de suporte de build da Plataforma Universal do Windows](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="968c9-122">Se você instalou o Unity sem essas opções, poderá adicioná-las por meio do menu **'Adicionar Módulos'** no Hub do Unity:</span><span class="sxs-lookup"><span data-stu-id="968c9-122">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opção do Unity de suporte de build do Windows](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="968c9-124">Usando o plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="968c9-124">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="968c9-125">Embora seja recomendável usar o OpenXR para todos os novos projetos, o Unity 2020.3 LTS também dá suporte ao [plug-in do Windows XR.](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)</span><span class="sxs-lookup"><span data-stu-id="968c9-125">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span></span> <span data-ttu-id="968c9-126">Esse plug-in tem suporte total, embora não receba novos recursos, como o suporte do AR Foundation 4.0.</span><span class="sxs-lookup"><span data-stu-id="968c9-126">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="968c9-127">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="968c9-127">Unity 2019.4 LTS</span></span>

<span data-ttu-id="968c9-128">Se você precisar usar o Unity 2019, poderá usar **o Unity 2019 LTS com xR integrado herdado.**</span><span class="sxs-lookup"><span data-stu-id="968c9-128">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="968c9-129">Para começar a trabalhar com o XR integrado herdados no Unity 2019.4 LTS, clique aqui:</span><span class="sxs-lookup"><span data-stu-id="968c9-129">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="968c9-130">Configurar o XR integrado herddo</span><span class="sxs-lookup"><span data-stu-id="968c9-130">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="968c9-131">O Unity preterido seu suporte de XR integrado herdado a partir do Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="968c9-131">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="968c9-132">Embora o Unity 2019 ofereça uma nova estrutura de plug-in XR, a Microsoft não está recomendando esse caminho no Unity 2019 devido a incompatibilidades das Âncoras Espaciais do Azure com o AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="968c9-132">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="968c9-133">No Unity 2020, as Âncoras Espaciais do Azure são suportadas na estrutura de plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="968c9-133">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="968c9-134">Se você estiver desenvolvendo aplicativos para HoloLens (1ª geração), esses headsets permanecerão com suporte no Unity 2019 LTS com XR integrado herdado para o ciclo de vida completo do Unity 2019 LTS até meados de 2022.</span><span class="sxs-lookup"><span data-stu-id="968c9-134">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="968c9-135">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="968c9-135">Unity 2021.1</span></span>

<span data-ttu-id="968c9-136">Se você estiver tentando criar builds do **Unity 2021.1** no início, vá para o **plug-in OpenXR,** pois o plug-in do Windows XR foi preterido lá.</span><span class="sxs-lookup"><span data-stu-id="968c9-136">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="968c9-137">A partir do Unity 2021.2, o plug-in OpenXR será o único caminho para o desenvolvimento de Realidade Misturada, pois o plug-in do Windows XR não terá mais suporte.</span><span class="sxs-lookup"><span data-stu-id="968c9-137">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="968c9-138">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="968c9-138">Unity 2018.4 LTS</span></span>

<span data-ttu-id="968c9-139">Se você já tiver um projeto usando o Unity 2018.4 LTS, o mecanismo do Unity continuará com suporte por dois anos após seu lançamento.</span><span class="sxs-lookup"><span data-stu-id="968c9-139">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="968c9-140">O Unity 2018 LTS atingirá o fim do serviço na fonte de 2021.</span><span class="sxs-lookup"><span data-stu-id="968c9-140">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
