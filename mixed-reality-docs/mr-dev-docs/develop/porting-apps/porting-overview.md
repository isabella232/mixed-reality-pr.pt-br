---
title: Visão geral de portabilidade
description: Uma visão geral das várias opções de porta para levar seus aplicativos existentes para Realidade Misturada para HoloLens e VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: portating, unity, middleware, engine, UWP, Win32
ms.openlocfilehash: 9b056bd81a725fea23c1e7f3bfcd9844680086c6
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600495"
---
# <a name="porting-overview"></a><span data-ttu-id="548af-104">Visão geral de portabilidade</span><span class="sxs-lookup"><span data-stu-id="548af-104">Porting overview</span></span>

<span data-ttu-id="548af-105">Quando se trata de portar ou atualizar seus projetos existentes para Realidade Misturada, seu percurso de portação depende se o aplicativo é criado com o Unity ou o Unreal Engine e tem como alvo o HoloLens (1ª geração) ou o HoloLens 2 ou o SteamVR.</span><span class="sxs-lookup"><span data-stu-id="548af-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="548af-106">Esta página de visão geral contém nossas recomendações atuais para cada plataforma e dispositivo– verifique novamente, pois esses processos estão sempre mudando.</span><span class="sxs-lookup"><span data-stu-id="548af-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="548af-107">Primeiro, configurar o destino do projeto com base em nossas recomendações do [Unity](#unity) e [do Unreal](#unreal) e, em seguida, siga um ou mais dos nossos cenários de portação:</span><span class="sxs-lookup"><span data-stu-id="548af-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="548af-108">HoloLens (1ª geração) para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="548af-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="548af-109">Headsets do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="548af-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="548af-110">Aplicativos SteamVR</span><span class="sxs-lookup"><span data-stu-id="548af-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="548af-111">Aplicativos UWP 2D</span><span class="sxs-lookup"><span data-stu-id="548af-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="548af-112">Destinos de projeto recomendados</span><span class="sxs-lookup"><span data-stu-id="548af-112">Recommended project targets</span></span>

<span data-ttu-id="548af-113">É importante manter seus projetos atualizados, independentemente de você estar portando um aplicativo para outro dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="548af-113">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="548af-114">Consulte os recursos baseados em mecanismo listados abaixo para ver nossas recomendações atuais.</span><span class="sxs-lookup"><span data-stu-id="548af-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="548af-115">Unity</span><span class="sxs-lookup"><span data-stu-id="548af-115">Unity</span></span>

<span data-ttu-id="548af-116">Nossa recomendação atual para o desenvolvimento do Unity com Realidade Misturada é **o Unity 2019 LTS usando o pacote XR herdado.**</span><span class="sxs-lookup"><span data-stu-id="548af-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="548af-117">Se seu projeto usar o Kit de Ferramentas de Realidade Misturada, verifique se você está na versão mais recente, que atualmente é **o MRTK-Unity 2.5.**</span><span class="sxs-lookup"><span data-stu-id="548af-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="548af-118">Embora o SDK do XR está disponível com esta versão do Unity, as Âncoras Espaciais do Azure não são compatíveis com essa configuração no momento.</span><span class="sxs-lookup"><span data-stu-id="548af-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="548af-119">Essa recomendação será atualizada com uma versão futura do pacote âncoras espaciais do Azure para Unity.</span><span class="sxs-lookup"><span data-stu-id="548af-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span>
> 
> * <span data-ttu-id="548af-120">Se você não precisar de Âncoras Espaciais do Azure, poderá configurar seu projeto do Unity para [XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) e começar a usar o [MRTK e o SDK do XR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk)</span><span class="sxs-lookup"><span data-stu-id="548af-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk).</span></span>
> 
> * <span data-ttu-id="548af-121">Se você estiver usando o SDK XR em seu projeto e quiser usar Âncoras Espaciais do Azure, desinstale o SDK do XR e reinstale o pacote XR herdado para reverter as configurações do projeto.</span><span class="sxs-lookup"><span data-stu-id="548af-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>

### <a name="unreal"></a><span data-ttu-id="548af-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="548af-122">Unreal</span></span>

<span data-ttu-id="548af-123">Nossa recomendação atual para o desenvolvimento do Unreal com Realidade Misturada é **o Unreal Engine 4.26.**</span><span class="sxs-lookup"><span data-stu-id="548af-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="548af-124">Se seu projeto usar as Ferramentas de UX do Kit de Ferramentas de Realidade Misturada, certifique-se de que você está usando a versão mais recente, que atualmente é **UXT 0.10**.</span><span class="sxs-lookup"><span data-stu-id="548af-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="548af-125">Cenários de portação</span><span class="sxs-lookup"><span data-stu-id="548af-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="548af-126">Aplicativos Unity do HoloLens (1ª geração) para o HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="548af-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="548af-127">Se você tiver um aplicativo Unity do HoloLens (1ª geração) existente que gostaria de portar para um HoloLens 2, siga as instruções em nosso artigo de [portabilidade do HoloLens.](./porting-hl1-hl2.md)</span><span class="sxs-lookup"><span data-stu-id="548af-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="548af-128">Headsets do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="548af-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="548af-129">Se você tiver criado conteúdo para outros dispositivos, como o Oculus Dimensional ou o HP Reverb G2, precisará retarget de SDKs de VR específicos do fornecedor e, potencialmente, APIs de mapeamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="548af-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to retarget vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="548af-130">Você pode encontrar informações para cenários de portação do Unity e do Unreal em nosso [guia de portação de aplicativos imersivos.](porting-guides.md)</span><span class="sxs-lookup"><span data-stu-id="548af-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="548af-131">Aplicativos SteamVR</span><span class="sxs-lookup"><span data-stu-id="548af-131">SteamVR applications</span></span>

<span data-ttu-id="548af-132">Para qualquer experiência do SteamVR que você deseja atualizar para headsets Windows Mixed Reality, consulte nosso guia de atualização [do SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)</span><span class="sxs-lookup"><span data-stu-id="548af-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="548af-133">Aplicativos Universais do Windows 2D</span><span class="sxs-lookup"><span data-stu-id="548af-133">2D Universal Windows applications</span></span>

<span data-ttu-id="548af-134">Se você tiver um aplicativo UWP 2D existente que gostaria de portar para um headset imersivo Windows Mixed Reality ou HoloLens, siga nossas instruções de portabilidade de aplicativos [UWP 2D](building-2d-apps.md) para Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="548af-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>