---
title: Visão geral de portabilidade
description: Uma visão geral das várias opções de portabilidade para trazer os aplicativos existentes para a realidade misturada para o HoloLens e o VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: portabilidade, Unity, middleware, mecanismo, UWP, Win32
ms.openlocfilehash: 693891d67ae26098f0810a539059da8d34f4731c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759107"
---
# <a name="porting-overview"></a><span data-ttu-id="be525-104">Visão geral de portabilidade</span><span class="sxs-lookup"><span data-stu-id="be525-104">Porting overview</span></span>

<span data-ttu-id="be525-105">Quando se trata de portar ou atualizar seus projetos existentes para realidade misturada, sua jornada de portabilidade depende de o seu aplicativo ser criado com o Unity ou o mecanismo inreal e tem como alvo o HoloLens (1º gen) ou o HoloLens 2 ou o SteamVR.</span><span class="sxs-lookup"><span data-stu-id="be525-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="be525-106">Esta página de visão geral contém nossas recomendações atuais para cada plataforma e dispositivo. Verifique novamente, pois esses processos estão sempre mudando.</span><span class="sxs-lookup"><span data-stu-id="be525-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="be525-107">Primeiro, configure o destino do projeto com base em nossas recomendações de [Unity](#unity) e [inreals](#unreal) e siga um ou mais dos nossos cenários de portabilidade:</span><span class="sxs-lookup"><span data-stu-id="be525-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="be525-108">HoloLens (1º gen) para o HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="be525-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="be525-109">Headsets do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="be525-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="be525-110">Aplicativos SteamVR</span><span class="sxs-lookup"><span data-stu-id="be525-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="be525-111">aplicativos UWP 2D</span><span class="sxs-lookup"><span data-stu-id="be525-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="be525-112">Destinos de projeto recomendados</span><span class="sxs-lookup"><span data-stu-id="be525-112">Recommended project targets</span></span>

<span data-ttu-id="be525-113">É importante manter seus projetos atualizados, seja a porta de um aplicativo para outro dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="be525-113">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="be525-114">Consulte os recursos baseados em mecanismo listados abaixo para nossas recomendações atuais.</span><span class="sxs-lookup"><span data-stu-id="be525-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="be525-115">Unity</span><span class="sxs-lookup"><span data-stu-id="be525-115">Unity</span></span>

<span data-ttu-id="be525-116">Nossa recomendação atual para o desenvolvimento do Unity com realidade misturada é **o Unity 2019 LTS usando o pacote XR herdado**.</span><span class="sxs-lookup"><span data-stu-id="be525-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="be525-117">Se o seu projeto usa o kit de ferramentas de realidade misturada, verifique se você está na versão mais recente, que atualmente é **MRTK-Unity 2,5**.</span><span class="sxs-lookup"><span data-stu-id="be525-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="be525-118">Embora o XR SDK esteja disponível com esta versão do Unity, as âncoras espaciais do Azure não são atualmente compatíveis com essa configuração.</span><span class="sxs-lookup"><span data-stu-id="be525-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="be525-119">Essa recomendação será atualizada com uma versão futura do pacote de âncoras espaciais do Azure para o Unity.</span><span class="sxs-lookup"><span data-stu-id="be525-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span> 
> 
> * <span data-ttu-id="be525-120">Se você não precisar de âncoras espaciais do Azure, poderá [configurar seu projeto do Unity para XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) e começar a usar o [MRTK e o XR SDK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/getting-started-with-mrtk-and-xrsdk.md).</span><span class="sxs-lookup"><span data-stu-id="be525-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/getting-started-with-mrtk-and-xrsdk.md).</span></span>
> 
> * <span data-ttu-id="be525-121">Se você estiver usando atualmente o SDK do XR em seu projeto e quiser usar âncoras espaciais do Azure, desinstale o SDK do XR e reinstale o pacote de XR herdado para reverter as configurações do projeto.</span><span class="sxs-lookup"><span data-stu-id="be525-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>


### <a name="unreal"></a><span data-ttu-id="be525-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="be525-122">Unreal</span></span> 

<span data-ttu-id="be525-123">Nossa recomendação atual para desenvolvimento inreal com realidade misturada é o **mecanismo inreal 4,26**.</span><span class="sxs-lookup"><span data-stu-id="be525-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="be525-124">Se seu projeto usa as ferramentas de UX do kit de ferramentas da realidade misturada, verifique se você está usando a versão mais recente, que atualmente é **UXT 0,10**.</span><span class="sxs-lookup"><span data-stu-id="be525-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="be525-125">Cenários de portabilidade</span><span class="sxs-lookup"><span data-stu-id="be525-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="be525-126">Aplicativos do HoloLens (1ª gen) Unity para o HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="be525-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="be525-127">Se você tiver um aplicativo de HoloLens (1ª gen) da Unity existente que você gostaria de portar para um HoloLens 2, siga as instruções em nosso [artigo portador do hololens](./porting-hl1-hl2.md).</span><span class="sxs-lookup"><span data-stu-id="be525-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="be525-128">Headsets do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="be525-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="be525-129">Se você tiver criado conteúdo para outros dispositivos, como o Oculus Rift ou o HP reverbs G2, será necessário redirecionar SDKs de VR específicos do fornecedor e APIs de mapeamento de entrada potencialmente.</span><span class="sxs-lookup"><span data-stu-id="be525-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to retarget vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="be525-130">Você pode encontrar informações para cenários de porta inreal e Unity em nosso [Guia de portabilidade de aplicativos de imersão](porting-guides.md).</span><span class="sxs-lookup"><span data-stu-id="be525-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="be525-131">Aplicativos SteamVR</span><span class="sxs-lookup"><span data-stu-id="be525-131">SteamVR applications</span></span>

<span data-ttu-id="be525-132">Para qualquer experiência de SteamVR que você deseja atualizar para headsets de realidade mista do Windows, consulte nosso [Guia de atualização do SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="be525-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="be525-133">aplicativos universais do Windows 2D</span><span class="sxs-lookup"><span data-stu-id="be525-133">2D Universal Windows applications</span></span>

<span data-ttu-id="be525-134">Se você tiver um aplicativo UWP 2D existente que você gostaria de portar para um headset ou um HoloLens de imersão de realidade do Windows, siga nossas instruções [de portabilidade 2D de aplicativos UWP para Windows Mixed Reality](building-2d-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="be525-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>