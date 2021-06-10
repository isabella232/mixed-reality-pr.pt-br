---
title: Como escolher uma versão do Unity e um plug-in de XR
description: Mantenha-se atualizado sobre as recomendações de plug-in do Unity e XR mais recentes para o desenvolvimento de aplicativos holoLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, unity
ms.openlocfilehash: da171db41e508fe556d8645b23f12f6f437446a1
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908228"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="1ae99-104">Como escolher uma versão do Unity e um plug-in de XR</span><span class="sxs-lookup"><span data-stu-id="1ae99-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="1ae99-105">Embora seja recomendável instalar o **Unity 2019.4 LTS** e usar o XR integrado herdado para desenvolvimento de Realidade Misturada, você também pode criar aplicativos com outras configurações do Unity.</span><span class="sxs-lookup"><span data-stu-id="1ae99-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="1ae99-106">Unity 2019.4 LTS (recomendado)</span><span class="sxs-lookup"><span data-stu-id="1ae99-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="1ae99-107">A configuração atual recomendada do Unity da Microsoft para o desenvolvimento do HoloLens 2 e Windows Mixed Reality é **o Unity 2019.4 LTS** usando o suporte herdado a XR.</span><span class="sxs-lookup"><span data-stu-id="1ae99-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="1ae99-108">A melhor maneira de instalar e gerenciar o Unity é por meio <a href="https://unity3d.com/get-unity/download" target="_blank">do [Hub do Unity].</a></span><span class="sxs-lookup"><span data-stu-id="1ae99-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="1ae99-109">Quando ele estiver instalado, abra o Hub do Unity:</span><span class="sxs-lookup"><span data-stu-id="1ae99-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="1ae99-110">Selecione a **guia Instalar e** escolha **ADICIONAR**</span><span class="sxs-lookup"><span data-stu-id="1ae99-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="1ae99-111">Selecione Unity 2019.4 LTS e clique em **Próximo**</span><span class="sxs-lookup"><span data-stu-id="1ae99-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Nova versão instal do hub do Unity](images/unity-hub-img-01.png)

3. <span data-ttu-id="1ae99-113">Verifique os componentes a seguir **em 'Plataformas'**</span><span class="sxs-lookup"><span data-stu-id="1ae99-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="1ae99-114">**Suporte de build da Plataforma Universal do Windows**</span><span class="sxs-lookup"><span data-stu-id="1ae99-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="1ae99-115">**Suporte de build do Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="1ae99-115">**Windows Build Support (IL2CPP)**</span></span>

![Opção do Unity de suporte de build da Plataforma Universal do Windows](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="1ae99-117">Se você instalou o Unity sem essas opções, poderá adicioná-las por meio do menu **'Adicionar Módulos'** no Hub do Unity:</span><span class="sxs-lookup"><span data-stu-id="1ae99-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opção do Unity de suporte de build do Windows](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="1ae99-119">Para começar a trabalhar com o XR integrado herdados no Unity 2019.4 LTS, clique aqui:</span><span class="sxs-lookup"><span data-stu-id="1ae99-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1ae99-120">Configurar o XR integrado herddo</span><span class="sxs-lookup"><span data-stu-id="1ae99-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="1ae99-121">O Unity preterido seu suporte de XR integrado herdado a partir do Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="1ae99-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="1ae99-122">Embora o Unity 2019 ofereça uma nova estrutura de plug-in XR, a Microsoft não está recomendando esse caminho no Unity 2019 devido a incompatibilidades das Âncoras Espaciais do Azure com o AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="1ae99-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="1ae99-123">No Unity 2020, as Âncoras Espaciais do Azure são suportadas na estrutura de plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="1ae99-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="1ae99-124">Se você estiver desenvolvendo aplicativos para HoloLens (1ª geração), esses headsets permanecerão com suporte no Unity 2019 LTS com XR integrado herdado para o ciclo de vida completo do Unity 2019 LTS até meados de 2022.</span><span class="sxs-lookup"><span data-stu-id="1ae99-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="1ae99-125">Unity 2020.3 LTS</span><span class="sxs-lookup"><span data-stu-id="1ae99-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="1ae99-126">Se você estiver usando **o Unity 2020.3 LTS,** poderá usar o **plug-in do Windows XR** para desenvolver o HoloLens 2 e Windows Mixed Reality aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1ae99-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="1ae99-127">No entanto, há problemas conhecidos que afetam a estabilidade do holograma e outros recursos no HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="1ae99-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="1ae99-128">Aplicativos de comunicação de comunicação Plataforma Universal do Windows aplicativo holográfico usando Plataforma Universal do Windows de build não estão funcionando.</span><span class="sxs-lookup"><span data-stu-id="1ae99-128">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="1ae99-129">O sistema de trabalhos gráficos do Unity é padrão, embora não seja compatível com projetos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1ae99-129">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="1ae99-130">Se você optar por iniciar um novo projeto no Unity 2020 hoje, certifique-se de acompanhar nos próximos meses para builds atualizados do Unity e builds de plug-in do Windows XR antes de enviar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ae99-130">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming months for updated Unity builds and Windows XR plugin builds before shipping your app.</span></span>  <span data-ttu-id="1ae99-131">Isso garantirá que os usuários experimentem a estabilidade adequada do holograma.</span><span class="sxs-lookup"><span data-stu-id="1ae99-131">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1ae99-132">Como usar o plug-in de XR do Windows</span><span class="sxs-lookup"><span data-stu-id="1ae99-132">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="1ae99-133">Usando OpenXR</span><span class="sxs-lookup"><span data-stu-id="1ae99-133">Using OpenXR</span></span>

<span data-ttu-id="1ae99-134">O Unity 2020.3 LTS também dá suporte a uma visualização pública do plug-in **OpenXR de Realidade Misturada.**</span><span class="sxs-lookup"><span data-stu-id="1ae99-134">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="1ae99-135">O plug-in OpenXR de Realidade Misturada dá suporte total ao AR Foundation 4.0, fornecendo implementações ARPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="1ae99-135">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="1ae99-136">Isso permite que você escreva um código de teste de clique uma vez que abrange os telefones e tablets holoLens 2 e ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="1ae99-136">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="1ae99-137">Posteriormente neste ano, **o Unity 2020.3 LTS** com o plug-in OpenXR se tornará a configuração recomendada do Unity e os futuros recursos do HoloLens 2 no Unity serão expostos somente por meio desse plug-in.</span><span class="sxs-lookup"><span data-stu-id="1ae99-137">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1ae99-138">Usando o plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="1ae99-138">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="1ae99-139">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="1ae99-139">Unity 2021.1</span></span>

<span data-ttu-id="1ae99-140">Se você estiver tentando criar builds do **Unity 2021.1** no início, vá para o **plug-in OpenXR,** pois o plug-in do Windows XR foi preterido lá.</span><span class="sxs-lookup"><span data-stu-id="1ae99-140">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="1ae99-141">A partir do Unity 2021.2, o plug-in OpenXR será o único caminho para o desenvolvimento de Realidade Misturada, pois o plug-in do Windows XR não terá mais suporte.</span><span class="sxs-lookup"><span data-stu-id="1ae99-141">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="1ae99-142">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="1ae99-142">Unity 2018.4 LTS</span></span>

<span data-ttu-id="1ae99-143">Se você já tiver um projeto usando o Unity 2018.4 LTS, o mecanismo do Unity continuará com suporte por dois anos após seu lançamento.</span><span class="sxs-lookup"><span data-stu-id="1ae99-143">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="1ae99-144">O Unity 2018 LTS atingirá o fim do serviço na fonte de 2021.</span><span class="sxs-lookup"><span data-stu-id="1ae99-144">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>