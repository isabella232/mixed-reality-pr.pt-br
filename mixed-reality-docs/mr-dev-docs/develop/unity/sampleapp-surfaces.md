---
title: Surfaces
description: Saiba como criar reações de tactile com visual, áudio e acompanhamento manual articulado no aplicativo de exemplo Surfaces.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality, design, aplicativo de exemplo, controles, MRTK, Kit de Ferramentas de Realidade Misturada, Unity, aplicativos de exemplo, aplicativos de exemplo, open-source, Microsoft Store, HoloLens, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: 28f8bc1e1f30573936067a83b1ad26133c23c5b8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743396"
---
# <a name="surfaces"></a><span data-ttu-id="161fe-104">Surfaces</span><span class="sxs-lookup"><span data-stu-id="161fe-104">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="161fe-105">Este artigo aborda um exemplo exploratório que criamos nos [Laboratórios](https://github.com/Microsoft/MRDesignLabs_Unity)de Design de Realidade Misturada, um local em que compartilhamos nossos aprendizados e sugestões para o desenvolvimento de aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="161fe-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="161fe-106">Nossos artigos e código relacionados ao design evoluirão à medida que fazemos novas descobertas.</span><span class="sxs-lookup"><span data-stu-id="161fe-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="161fe-107">[O Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  é um aplicativo de exemplo de código aberto dos Laboratórios de Design de Realidade Misturada da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="161fe-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="161fe-108">Ele explora como podemos criar uma sensação de tactile com visual, áudio e acompanhamento de mão totalmente articulado.</span><span class="sxs-lookup"><span data-stu-id="161fe-108">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Surfaces](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="161fe-110">Vídeo de demonstração</span><span class="sxs-lookup"><span data-stu-id="161fe-110">Demo video</span></span> 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="161fe-111">Gravado com o HoloLens 2 usando Captura de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="161fe-111">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="161fe-112">Sobre o aplicativo</span><span class="sxs-lookup"><span data-stu-id="161fe-112">About the app</span></span>

<span data-ttu-id="161fe-113">As superfícies demonstram como usar o sistema de entrada e blocos de construção do MRTK (Kit de Ferramentas de Realidade Misturada) para criar uma experiência de aplicativo para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="161fe-113">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="161fe-114">Neste projeto, você pode encontrar os exemplos de:</span><span class="sxs-lookup"><span data-stu-id="161fe-114">In this project, you can find the examples of:</span></span>

- <span data-ttu-id="161fe-115">Use o Sistema de Entrada [do](/windows/mixed-reality/mrtk-unity/features/input/overview)MRTK, especificamente acompanhamento manual/conjunto.</span><span class="sxs-lookup"><span data-stu-id="161fe-115">Use MRTK's [Input System](/windows/mixed-reality/mrtk-unity/features/input/overview), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="161fe-116">Use o Sombreador Padrão [do](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) MRTK para gráficos de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="161fe-116">Use MRTK's [Standard Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) for performant graphics.</span></span>

<span data-ttu-id="161fe-117">Você pode usar os componentes desse projeto para criar suas próprias experiências de aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="161fe-117">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="161fe-118">MR Dev Days 2020 – Aprendizados do aplicativo mr surfaces</span><span class="sxs-lookup"><span data-stu-id="161fe-118">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>

[<span data-ttu-id="161fe-119">Aprendizados do aplicativo Surfaces do MR</span><span class="sxs-lookup"><span data-stu-id="161fe-119">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="161fe-120">Lars Simkins, designer sênior por trás do aplicativo MRDL Surfaces, fala sobre a história de design e os destaques técnicos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="161fe-120">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="161fe-121">Repositório de projetos no GitHub</span><span class="sxs-lookup"><span data-stu-id="161fe-121">Project repository on GitHub</span></span>

[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="161fe-122">Baixar o aplicativo Microsoft Store no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="161fe-122">Download app from Microsoft Store in HoloLens 2</span></span>

https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="161fe-123">(O aplicativo só está disponível no HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="161fe-123">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="161fe-124">Sobre o autor</span><span class="sxs-lookup"><span data-stu-id="161fe-124">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="161fe-125"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="161fe-125"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="161fe-126">Designer de UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="161fe-126">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="161fe-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="161fe-127">See also</span></span>

* <span data-ttu-id="161fe-128">[Hub de Exemplos do MRTK](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="161fe-128">[MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="161fe-129">[Surfaces](sampleapp-surfaces.md) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="161fe-129">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="161fe-130">Tabela periódica dos elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="161fe-130">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="161fe-131">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="161fe-131">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)