---
title: Surfaces
description: As superfícies são um aplicativo de exemplo de software livre dos laboratórios de design de realidade misturada da Microsoft. Ele explora como podemos criar um tactile sensação com Visual, áudio e acompanhamento de mão totalmente articulado.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, mrtk, design, aplicativo de exemplo, controles
ms.openlocfilehash: 1c6cb4579bbd3d6124cf36b21226ffa803f39f00
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573180"
---
# <a name="surfaces"></a><span data-ttu-id="55ed8-105">Surfaces</span><span class="sxs-lookup"><span data-stu-id="55ed8-105">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="55ed8-106">Este artigo discute um exemplo exploratório que criamos nos laboratórios de [design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity), um lugar onde compartilhamos nossas aprendeções e sugestões para o desenvolvimento de aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="55ed8-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="55ed8-107">Nossos artigos e códigos relacionados ao design irão evoluir à medida que fizermos novas descobertas.</span><span class="sxs-lookup"><span data-stu-id="55ed8-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="55ed8-108">As [superfícies](https://github.com/microsoft/MRDL_Unity_Surfaces) são um aplicativo de exemplo de software livre dos laboratórios de design de realidade misturada da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="55ed8-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="55ed8-109">Ele explora como podemos criar um tactile sensação com Visual, áudio e acompanhamento de mão totalmente articulado.</span><span class="sxs-lookup"><span data-stu-id="55ed8-109">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Surfaces](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="55ed8-111">Vídeo de demonstração</span><span class="sxs-lookup"><span data-stu-id="55ed8-111">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="55ed8-112">Registrado com o HoloLens 2 usando a captura de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="55ed8-112">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="55ed8-113">Sobre o aplicativo</span><span class="sxs-lookup"><span data-stu-id="55ed8-113">About the app</span></span>
<span data-ttu-id="55ed8-114">As superfícies demonstram como usar o sistema de entrada do MRTK (Kit de ferramentas de realidade misturada) e os blocos de construção para criar uma experiência de aplicativo para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="55ed8-114">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="55ed8-115">Neste projeto, você pode encontrar os exemplos de:</span><span class="sxs-lookup"><span data-stu-id="55ed8-115">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="55ed8-116">Use o [sistema de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)do MRTK, o acompanhamento de forma específica/conjunta.</span><span class="sxs-lookup"><span data-stu-id="55ed8-116">Use MRTK's [Input System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="55ed8-117">Use o [sombreador padrão](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) do MRTK para gráficos de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="55ed8-117">Use MRTK's [Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) for performant graphics.</span></span>

<span data-ttu-id="55ed8-118">Você pode usar os componentes deste projeto para criar suas próprias experiências de aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="55ed8-118">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="55ed8-119">MR dev dias 2020-aprendizado do aplicativo Sr superfícies</span><span class="sxs-lookup"><span data-stu-id="55ed8-119">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>
[<span data-ttu-id="55ed8-120">Aprendizado do aplicativo Sr superfícies</span><span class="sxs-lookup"><span data-stu-id="55ed8-120">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="55ed8-121">Lars Simkins, designer sênior por trás do aplicativo de superfícies MRDLs fala sobre a história de design do aplicativo e os destaques técnicos.</span><span class="sxs-lookup"><span data-stu-id="55ed8-121">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="55ed8-122">Repositório do projeto no GitHub</span><span class="sxs-lookup"><span data-stu-id="55ed8-122">Project repository on GitHub</span></span>
[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="55ed8-123">Baixar o aplicativo de Microsoft Store no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="55ed8-123">Download app from Microsoft Store in HoloLens 2</span></span>
https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="55ed8-124">(O aplicativo só está disponível no HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="55ed8-124">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="55ed8-125">Sobre o autor</span><span class="sxs-lookup"><span data-stu-id="55ed8-125">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="55ed8-126"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="55ed8-126"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="55ed8-127">Designer de UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="55ed8-127">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="55ed8-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55ed8-128">See also</span></span>

* <span data-ttu-id="55ed8-129">[Hub de Exemplos do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="55ed8-129">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="55ed8-130">[Surfaces](sampleapp-surfaces.md) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="55ed8-130">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="55ed8-131">Tabela periódica dos elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="55ed8-131">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="55ed8-132">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="55ed8-132">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)
