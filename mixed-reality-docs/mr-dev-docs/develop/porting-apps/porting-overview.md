---
title: Visão geral de portabilidade
description: Uma visão geral das várias opções de porta para levar seus aplicativos existentes para Realidade Misturada para HoloLens e VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: portating, unity, middleware, engine, UWP, Win32
ms.openlocfilehash: 167559d69cc4e65f971a8970b56e41e6e3ca8b22
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042267"
---
# <a name="porting-overview"></a><span data-ttu-id="7d216-104">Visão geral de portabilidade</span><span class="sxs-lookup"><span data-stu-id="7d216-104">Porting overview</span></span>

<span data-ttu-id="7d216-105">Quando se trata de portar ou atualizar seus projetos existentes para Realidade Misturada, seu percurso de portação depende se o aplicativo é criado com o Unity ou o Unreal Engine e tem como alvo o HoloLens (1ª geração) ou o HoloLens 2 ou o SteamVR.</span><span class="sxs-lookup"><span data-stu-id="7d216-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="7d216-106">Esta página de visão geral contém nossas recomendações atuais para cada plataforma e dispositivo– verifique novamente, pois esses processos estão sempre mudando.</span><span class="sxs-lookup"><span data-stu-id="7d216-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="7d216-107">Primeiro, configurar o destino do projeto com base em nossas recomendações do [Unity](#unity) e [do Unreal](#unreal) e, em seguida, siga um ou mais dos nossos cenários de portação:</span><span class="sxs-lookup"><span data-stu-id="7d216-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="7d216-108">HoloLens (1ª geração) para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7d216-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="7d216-109">Headsets imersivos de VR</span><span class="sxs-lookup"><span data-stu-id="7d216-109">Immersive VR headsets</span></span>](#immersive-vr-headsets)
- [<span data-ttu-id="7d216-110">Aplicativos UWP 2D</span><span class="sxs-lookup"><span data-stu-id="7d216-110">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="7d216-111">Destinos de projeto recomendados</span><span class="sxs-lookup"><span data-stu-id="7d216-111">Recommended project targets</span></span>

<span data-ttu-id="7d216-112">É importante manter seus projetos atualizados, independentemente de você estar portando um aplicativo para outro dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="7d216-112">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="7d216-113">Consulte os recursos baseados em mecanismo listados abaixo para ver nossas recomendações atuais.</span><span class="sxs-lookup"><span data-stu-id="7d216-113">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="7d216-114">Unity</span><span class="sxs-lookup"><span data-stu-id="7d216-114">Unity</span></span>

<span data-ttu-id="7d216-115">Consulte a [página Escolhendo uma versão do Unity](../unity/choosing-unity-version.md) para obter diretrizes atualizadas sobre as versões recomendadas do Unity e do MRTK.</span><span class="sxs-lookup"><span data-stu-id="7d216-115">See the [Choosing a Unity version](../unity/choosing-unity-version.md) page for up-to-date guidance on the recommended Unity and MRTK versions.</span></span>

### <a name="unreal"></a><span data-ttu-id="7d216-116">Unreal</span><span class="sxs-lookup"><span data-stu-id="7d216-116">Unreal</span></span>

<span data-ttu-id="7d216-117">Consulte a [página Configurando seu projeto do Unreal](../unreal/unreal-project-setup.md) para obter diretrizes atualizadas sobre as versões recomendadas do Unreal e do MRTK.</span><span class="sxs-lookup"><span data-stu-id="7d216-117">See the [Setting up your Unreal project](../unreal/unreal-project-setup.md) page for up-to-date guidance on the recommended Unreal and MRTK versions.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="7d216-118">Cenários de portação</span><span class="sxs-lookup"><span data-stu-id="7d216-118">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="7d216-119">Aplicativos Unity do HoloLens (1ª geração) para o HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7d216-119">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="7d216-120">Se você tiver um aplicativo Unity do HoloLens (1ª geração) existente que gostaria de portar para um HoloLens 2, siga as instruções em nosso artigo de [portabilidade do HoloLens.](./porting-hl1-hl2.md)</span><span class="sxs-lookup"><span data-stu-id="7d216-120">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="immersive-vr-headsets"></a><span data-ttu-id="7d216-121">Headsets imersivos de VR</span><span class="sxs-lookup"><span data-stu-id="7d216-121">Immersive VR headsets</span></span>

<span data-ttu-id="7d216-122">Se você tiver criado conteúdo para outros dispositivos VR, precisará retarget quaisquer SDKs de VR específicos do fornecedor e, potencialmente, APIs de mapeamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="7d216-122">If you've built content for other VR devices, you'll need to retarget any vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="7d216-123">Você pode encontrar informações para cenários de portação do Unity e do Unreal em nosso [guia de portação de aplicativos imersivos.](porting-guides.md)</span><span class="sxs-lookup"><span data-stu-id="7d216-123">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

<span data-ttu-id="7d216-124">Para experiências do SteamVR que você deseja atualizar para headsets Windows Mixed Reality, consulte nosso guia de atualização [do SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)</span><span class="sxs-lookup"><span data-stu-id="7d216-124">For SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="7d216-125">Aplicativos Universais do Windows 2D</span><span class="sxs-lookup"><span data-stu-id="7d216-125">2D Universal Windows applications</span></span>

<span data-ttu-id="7d216-126">Se você tiver um aplicativo UWP 2D existente que gostaria de portar para um headset imersivo Windows Mixed Reality ou HoloLens, siga nossas instruções de portabilidade de aplicativos [UWP 2D](building-2d-apps.md) para Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="7d216-126">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>