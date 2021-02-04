---
title: Introdução ao MRTK para Unity
description: Comece com tudo o que o Kit de Ferramentas de Realidade Misturada multiplataforma tem para oferecer para novos desenvolvedores de realidade misturada.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, teste, Kit de Ferramentas de Realidade Misturada, MRTK versão 2, MRTK, ferramentas, SDK, HoloLens, HoloLens 2, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, multiplataforma
ms.openlocfilehash: 54ad49bbf4da577a398a0bfb12fbdc84cdff34d9
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99238122"
---
# <a name="introducing-mrtk-for-unity"></a><span data-ttu-id="31070-104">Introdução ao MRTK para Unity</span><span class="sxs-lookup"><span data-stu-id="31070-104">Introducing MRTK for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="31070-106">O que é o MRTK (Kit de Ferramentas de Realidade Misturada)?</span><span class="sxs-lookup"><span data-stu-id="31070-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="31070-107">O MRTK é um kit de ferramentas de software livre que existe desde que o HoloLens foi lançado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="31070-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="31070-108">Ele não seria o que é hoje sem o trabalho árduo da nossa comunidade de desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="31070-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> <span data-ttu-id="31070-109">Nos últimos três anos, ouvimos os comentários da comunidade de desenvolvedores e criamos o MRTK v2 para abordas as principais preocupações.</span><span class="sxs-lookup"><span data-stu-id="31070-109">Over the past three years, we've listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="31070-110">O MRTK para Unity é um kit de desenvolvimento de software livre multiplataforma para aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="31070-110">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="31070-111">A maneira mais fácil de instalar o kit de ferramentas é com o nosso novo aplicativo Ferramenta de Recursos de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="31070-111">The easiest way to install the toolkit is with our new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="31070-112">Siga as [instruções de instalação e uso](welcome-to-mr-feature-tool.md) e selecione o pacote **Mixed Reality Toolkit Foundation** na categoria Kit de Ferramentas de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="31070-112">Follow our [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality Toolkit Foundation** package in the Mixed Reality Toolkit category.</span></span> 

<span data-ttu-id="31070-113">O MRTK para Unity fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais.</span><span class="sxs-lookup"><span data-stu-id="31070-113">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="31070-114">A versão 2 do MRTK tem o objetivo de acelerar o desenvolvimento de aplicativos para o Microsoft HoloLens, os headsets imersivos (VR) do Windows Mixed Reality e a plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="31070-114">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="31070-115">O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.</span><span class="sxs-lookup"><span data-stu-id="31070-115">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="31070-116">Dê uma olhada na [documentação do MRTK no GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) para obter mais detalhes sobre os recursos.</span><span class="sxs-lookup"><span data-stu-id="31070-116">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) for more feature details.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="31070-117">Novidades com o MRTK v2</span><span class="sxs-lookup"><span data-stu-id="31070-117">New with MRTK v2</span></span>

<span data-ttu-id="31070-118">Queremos enfatizar nosso compromisso com estas ferramentas de plataforma.</span><span class="sxs-lookup"><span data-stu-id="31070-118">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="31070-119">Na verdade, aproveitamos o MRTK versão 2 para desenvolver nossas experiências de caixa de entrada, como a OOBE (configuração inicial pelo usuário) e nosso aplicativo Dicas sobre Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="31070-119">In fact, we used MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="31070-120">Você também pode esperar ver as novas funcionalidades do HoloLens 2 apresentadas pela primeira vez por meio do MRTK, pois acreditamos que é a melhor maneira de realizar o desenvolvimento em nossa plataforma.</span><span class="sxs-lookup"><span data-stu-id="31070-120">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="31070-121">Modular</span><span class="sxs-lookup"><span data-stu-id="31070-121">Modular</span></span>

<span data-ttu-id="31070-122">O MRTK foi criado de maneira modular, de modo que não seja necessário inserir todas as partes do kit de ferramentas no projeto.</span><span class="sxs-lookup"><span data-stu-id="31070-122">We have built it in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="31070-123">Na verdade, há alguns benefícios nessa abordagem.</span><span class="sxs-lookup"><span data-stu-id="31070-123">There are actually a few benefits to this.</span></span>  <span data-ttu-id="31070-124">Ela reduz o tamanho do projeto e facilita o gerenciamento dele.</span><span class="sxs-lookup"><span data-stu-id="31070-124">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="31070-125">Além disso, como o kit foi criado com objetos programáveis e é orientado por interface, também é possível substituir os componentes incluídos pelos seus próprios, a fim de dar suporte a outros serviços, sistemas e plataformas.</span><span class="sxs-lookup"><span data-stu-id="31070-125">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="31070-126">Plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="31070-126">Cross-platform</span></span>

<span data-ttu-id="31070-127">Falando em outras plataformas, ele tem suporte multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="31070-127">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="31070-128">Embora isso não signifique que todas as plataformas são compatíveis, garantimos que nenhum código do kit de ferramentas será desfeito quando você mudar o destino de build para outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="31070-128">And while this doesn’t mean every single platform is supported, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="31070-129">A robustez e a extensibilidade do design modular compatibilizam seus aplicativos com diversas plataformas, como ARCore, ARKit e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="31070-129">The robustness and extensibility of the modular design sets your apps up to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="31070-130">Alto desempenho</span><span class="sxs-lookup"><span data-stu-id="31070-130">Performant</span></span>

<span data-ttu-id="31070-131">Trabalhando com plataformas móveis, nós o construímos com o desempenho em mente.</span><span class="sxs-lookup"><span data-stu-id="31070-131">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="31070-132">Isso é muito importante, e queremos garantir que as ferramentas não trabalharão contra você.</span><span class="sxs-lookup"><span data-stu-id="31070-132">This is super important, and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="31070-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="31070-133">See also</span></span>

* [<span data-ttu-id="31070-134">Instalar as ferramentas</span><span class="sxs-lookup"><span data-stu-id="31070-134">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="31070-135">Ferramenta de Recursos de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="31070-135">Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
* [<span data-ttu-id="31070-136">Desenvolvimento com o MRTK para Unity</span><span class="sxs-lookup"><span data-stu-id="31070-136">Developing with MRTK for Unity</span></span>](unity-development-overview.md)
* [<span data-ttu-id="31070-137">MRTK – Página inicial da documentação (GitHub)</span><span class="sxs-lookup"><span data-stu-id="31070-137">MRTK - Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="31070-138">Portabilidade do HoloToolkit/MRTK para o MRTK versão 2 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="31070-138">Porting from HoloToolkit/MRTK to MRTK version 2 (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
