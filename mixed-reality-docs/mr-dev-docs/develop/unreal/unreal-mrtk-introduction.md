---
title: Introdução ao MRTK para Unreal
description: Comece com tudo o que o Kit de Ferramentas de Realidade Misturada para Unreal tem para oferecer para novos desenvolvedores de realidade misturada.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, teste, Kit de Ferramentas de Realidade Misturada, MRTK versão 2, MRTK, ferramentas, SDK, HoloLens, HoloLens 2, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, multiplataforma
ms.openlocfilehash: 4aa21cbee75c4c362abfd609add922ad9c922682
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584680"
---
# <a name="introducing-mrtk-for-unreal"></a><span data-ttu-id="8da9c-104">Introdução ao MRTK para Unreal</span><span class="sxs-lookup"><span data-stu-id="8da9c-104">Introducing MRTK for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="8da9c-106">O que é o MRTK (Kit de Ferramentas de Realidade Misturada)?</span><span class="sxs-lookup"><span data-stu-id="8da9c-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="8da9c-107">O MRTK é um kit de ferramentas de software livre que existe desde que o HoloLens foi lançado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="8da9c-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="8da9c-108">Ele não seria o que é hoje sem o trabalho árduo da nossa comunidade de desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="8da9c-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> 

<span data-ttu-id="8da9c-109">O MRTK-Unreal (Kit de Ferramentas de Realidade Misturada para Unreal) é um conjunto de componentes, na forma de plug-ins, exemplos e documentação, projetado para ajudar no desenvolvimento de aplicativos de Realidade Misturada usando o Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="8da9c-109">The Mixed Reality Toolkit for Unreal (MRTK-Unreal) is a set of components, in the form of plugins, samples and documentation, designed to help development of Mixed Reality applications using the Unreal Engine.</span></span> <span data-ttu-id="8da9c-110">Atualmente, o kit de ferramentas consiste em:</span><span class="sxs-lookup"><span data-stu-id="8da9c-110">Currently, the toolkit consists of:</span></span>
* <span data-ttu-id="8da9c-111">As [Ferramentas de Experiência do Usuário para Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), que fornecem código, blueprints e exemplos para implementar recursos de UX em aplicativos do Hololens 2.</span><span class="sxs-lookup"><span data-stu-id="8da9c-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), which provides code, blueprints, and examples to implement UX features for Hololens 2 applications.</span></span>
* <span data-ttu-id="8da9c-112">As [Ferramentas de Gráficos para Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), que ajudam a melhorar a fidelidade visual de aplicativos de Realidade Misturada ao mesmo tempo que cumprem os orçamentos de desempenho.</span><span class="sxs-lookup"><span data-stu-id="8da9c-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), which helps improve the visual fidelity of Mixed Reality applications while staying within performance budgets.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="8da9c-113">Confira a [documentação do MRTK no GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) e comece a usar os guias de instalação das [Ferramentas de Experiência do Usuário](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) ou das [Ferramentas de Gráficos](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md).</span><span class="sxs-lookup"><span data-stu-id="8da9c-113">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) and get started with [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) or [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) installation guides.</span></span>

### <a name="modular"></a><span data-ttu-id="8da9c-114">Modular</span><span class="sxs-lookup"><span data-stu-id="8da9c-114">Modular</span></span>

<span data-ttu-id="8da9c-115">Criamos o MRTK Unreal de maneira modular, de modo que não seja necessário inserir todas as partes do kit de ferramentas no projeto.</span><span class="sxs-lookup"><span data-stu-id="8da9c-115">We've built MRTK Unreal in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span> <span data-ttu-id="8da9c-116">Você pode escolher os plug-ins necessários e adicioná-los ou removê-los sempre que quiser.</span><span class="sxs-lookup"><span data-stu-id="8da9c-116">You can pick and choose the plugins you need, and add or remove them whenever you see fit.</span></span> <span data-ttu-id="8da9c-117">Essa abordagem reduz o tamanho do projeto e facilita o gerenciamento dele.</span><span class="sxs-lookup"><span data-stu-id="8da9c-117">This approach keeps your project size smaller and makes it easier to manage.</span></span>  

### <a name="performant"></a><span data-ttu-id="8da9c-118">Alto desempenho</span><span class="sxs-lookup"><span data-stu-id="8da9c-118">Performant</span></span>

<span data-ttu-id="8da9c-119">Trabalhando com plataformas móveis, nós construímos o MRTK Unreal pensando no desempenho.</span><span class="sxs-lookup"><span data-stu-id="8da9c-119">Working with mobile platforms, we constructed MRTK Unreal with performance in mind.</span></span> <span data-ttu-id="8da9c-120">Isso é muito importante e queremos garantir que as ferramentas não trabalharão contra você.</span><span class="sxs-lookup"><span data-stu-id="8da9c-120">This is super important and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="8da9c-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="8da9c-121">See also</span></span>

* [<span data-ttu-id="8da9c-122">Instalar as ferramentas</span><span class="sxs-lookup"><span data-stu-id="8da9c-122">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="8da9c-123">Desenvolvendo com o MRTK para Unreal</span><span class="sxs-lookup"><span data-stu-id="8da9c-123">Developing with MRTK for Unreal</span></span>](unreal-development-overview.md)
* [<span data-ttu-id="8da9c-124">Ferramentas de Experiência do Usuário – Guia de instalação (GitHub)</span><span class="sxs-lookup"><span data-stu-id="8da9c-124">UX Tools - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [<span data-ttu-id="8da9c-125">Ferramentas de Experiência do Usuário – Página inicial da documentação (GitHub)</span><span class="sxs-lookup"><span data-stu-id="8da9c-125">UX Tools- Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [<span data-ttu-id="8da9c-126">Ferramentas de Gráficos – Guia de instalação (GitHub)</span><span class="sxs-lookup"><span data-stu-id="8da9c-126">Graphics Tools - Installation guide (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [<span data-ttu-id="8da9c-127">Ferramentas de Gráficos – Página inicial da documentação (GitHub)</span><span class="sxs-lookup"><span data-stu-id="8da9c-127">Graphics Tools - Documentation home (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)