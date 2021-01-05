---
title: Diretrizes de design do inicializador de aplicativos 3D
description: Um iniciador de aplicativo 3D é um objeto "físico" na casa de realidade misturada do usuário que pode selecionar para iniciar um aplicativo.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, iniciador de aplicativos 3D, headset de imersão, cubo ao vivo, headset de realidade misturada, headset de realidade mista do Windows, Headset virtual realismo, UWP, Win32, iluminação, cor
ms.openlocfilehash: 2edb09e47da5bcbae34a37f004853002f3f65cf3
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757724"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="2cdf6-104">Diretrizes de design do inicializador de aplicativos 3D</span><span class="sxs-lookup"><span data-stu-id="2cdf6-104">3D app launcher design guidance</span></span>

<span data-ttu-id="2cdf6-105">Quando você coloca em um fone de ouvido (VR) de realidade mista do Windows, entra na página inicial do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home.</span></span> <span data-ttu-id="2cdf6-106">A página inicial é visualizada como uma casa em uma Cliff cercada por montanhas e água, mas você pode [escolher outros ambientes e até mesmo criar seus próprios](../design/add-custom-home-environments.md).</span><span class="sxs-lookup"><span data-stu-id="2cdf6-106">The home is visualized as a house on a cliff surrounded by mountains and water, but you can [choose other environments and even create your own](../design/add-custom-home-environments.md)).</span></span> <span data-ttu-id="2cdf6-107">No espaço da Home, um usuário é livre para organizar e organizar os objetos 3D e os aplicativos que eles se preocupam de qualquer forma que desejarem.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-107">Within the home's space, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="2cdf6-108">Um **iniciador de aplicativo 3D** é um objeto "físico" na casa de realidade misturada do usuário que pode selecionar para iniciar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-108">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="2cdf6-109">![Exemplo: inicializador de aplicativo 3D de pássaro flutuante](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-109">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="2cdf6-110">*Exemplo de inicializador de aplicativo 3D de pássaro flutuante (aplicativo fictício)*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-110">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="2cdf6-111">processo de criação do inicializador de aplicativo 3D</span><span class="sxs-lookup"><span data-stu-id="2cdf6-111">3D app launcher creation process</span></span>

<span data-ttu-id="2cdf6-112">Há três etapas para criar um iniciador de aplicativo 3D:</span><span class="sxs-lookup"><span data-stu-id="2cdf6-112">There are 3 steps to creating a 3D app launcher:</span></span>

1. <span data-ttu-id="2cdf6-113">Design e conceito (este artigo)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-113">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="2cdf6-114">Modelagem e exportação</span><span class="sxs-lookup"><span data-stu-id="2cdf6-114">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="2cdf6-115">Integrando-o em seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="2cdf6-115">Integrating it into your application:</span></span>
    * [<span data-ttu-id="2cdf6-116">Aplicativos UWP</span><span class="sxs-lookup"><span data-stu-id="2cdf6-116">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="2cdf6-117">Aplicativos Win32</span><span class="sxs-lookup"><span data-stu-id="2cdf6-117">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="2cdf6-118">Conceitos de design</span><span class="sxs-lookup"><span data-stu-id="2cdf6-118">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="2cdf6-119">Fantástico ainda familiar</span><span class="sxs-lookup"><span data-stu-id="2cdf6-119">Fantastic yet familiar</span></span>

<span data-ttu-id="2cdf6-120">O ambiente de realidade mista do Windows em que seu inicializador de aplicativo reside faz parte familiar, parte fantástica/Sci-Fi.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-120">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="2cdf6-121">Os melhores iniciadores seguem as regras deste mundo.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-121">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="2cdf6-122">Imagine como você pode pegar um objeto familiar e representativo de seu aplicativo, mas dobre algumas das regras da realidade real.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-122">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="2cdf6-123">A mágica será resultado.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-123">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="2cdf6-124">Simples</span><span class="sxs-lookup"><span data-stu-id="2cdf6-124">Intuitive</span></span>

<span data-ttu-id="2cdf6-125">Ao examinar seu iniciador de aplicativo, sua finalidade-para iniciar seu aplicativo-deve ser óbvio e não deve causar qualquer confusão.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-125">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="2cdf6-126">Por exemplo, certifique-se de que o iniciador é um representante óbvio o suficiente do seu aplicativo que não será confundido por uma parte do décor na casa Cliff.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-126">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="2cdf6-127">Seu iniciador de aplicativo deve convidar pessoas para tocar/selecionar.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-127">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="2cdf6-128">![Exemplo: inicializador de aplicativo 3D de anotação atualizada](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-128">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="2cdf6-129">*Observação de novo exemplo de inicializador de aplicativo 3D (aplicativo fictício)*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-129">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="2cdf6-130">Escala inicial</span><span class="sxs-lookup"><span data-stu-id="2cdf6-130">Home scale</span></span>

<span data-ttu-id="2cdf6-131">os iniciadores de aplicativos 3D residem na casa Cliff e seu tamanho padrão deve fazer sentido com os outros objetos "físicos" no espaço.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-131">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="2cdf6-132">Se você colocar seu iniciador ao lado de, digamos, uma planta de casa ou em algumas mobílias, deverá sentir em casa, com tamanho próprio.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-132">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="2cdf6-133">Um bom ponto de partida é ver como ele analisa 30 centímetros cúbicos, mas lembre-se de que os usuários podem escalá-los ou diminuí-los se quiserem.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-133">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="2cdf6-134">Com capacidade própria</span><span class="sxs-lookup"><span data-stu-id="2cdf6-134">Own-able</span></span>

<span data-ttu-id="2cdf6-135">O inicializador de aplicativos deve se parecer com um objeto que uma pessoa estaria empolgando em seu espaço.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-135">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="2cdf6-136">Eles estarão praticamente circundando-se com essas coisas, portanto, o iniciador deve se sentir como algo que o usuário pensava o suficiente para buscar e manter o próximo.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-136">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="2cdf6-137">![Exemplo: inicializador de aplicativo 3D Astro Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-137">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="2cdf6-138">*Exemplo de inicializador de aplicativo 3D Astro Warp (aplicativo fictício)*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-138">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="2cdf6-139">Reconhecível</span><span class="sxs-lookup"><span data-stu-id="2cdf6-139">Recognizable</span></span>

<span data-ttu-id="2cdf6-140">Seu iniciador de aplicativo 3D deve expressar instantaneamente "a marca do aplicativo" para as pessoas que a veem.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-140">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="2cdf6-141">Se você tiver um caractere de estrela ou um objeto especialmente identificável em seu aplicativo, é recomendável usá-lo como uma parte significativa do design.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-141">If you have a star character or an especially identifiable object in your app, we recommend using that as a significant part of your design.</span></span> <span data-ttu-id="2cdf6-142">Em um mundo de realidade misturada, um objeto desenhará mais interesse dos usuários do que apenas um logotipo.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-142">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="2cdf6-143">Os objetos reconhecíveis comunicam a marca de forma rápida e clara.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-143">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="2cdf6-144">Volumétricos</span><span class="sxs-lookup"><span data-stu-id="2cdf6-144">Volumetric</span></span>

<span data-ttu-id="2cdf6-145">Seu aplicativo merece mais do que apenas colocar seu logotipo em um plano plano e chamá-lo por dia.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-145">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="2cdf6-146">Seu iniciador deve parecer um objeto físico empolgante e 3D no espaço do usuário.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-146">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="2cdf6-147">Uma boa abordagem é imaginar que seu aplicativo terá um balão no dia de graças do Macy liderança.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-147">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="2cdf6-148">Pergunte-se, o que realmente seria Wow quando ele chegou à rua?</span><span class="sxs-lookup"><span data-stu-id="2cdf6-148">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="2cdf6-149">O que pareceria muito com todos os ângulos de exibição?</span><span class="sxs-lookup"><span data-stu-id="2cdf6-149">What would look great from all viewing angles?</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="2cdf6-150">![Somente ](images/20171016-140436-mixedreality-640px.jpg) *logotipo* do logotipo</span><span class="sxs-lookup"><span data-stu-id="2cdf6-150">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2cdf6-151">![Mais reconhecível com um caractere ](images/20171016-140557-mixedreality-640px.jpg) *mais reconhecível com um caractere*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-151">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="2cdf6-152">![Abordagem simples, não surpreendentemente, sente-se uma ](images/20171016-155101-mixedreality-640px.jpg) *abordagem simples e simples, não surpreendentemente, parece simples*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-152">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2cdf6-153">![A abordagem de volumétricos melhor apresenta melhor a ](images/20171016-161407-mixedreality-640px.jpg) *abordagem de volumétricos* do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2cdf6-153">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a><span data-ttu-id="2cdf6-154">Dicas para bons modelos 3D</span><span class="sxs-lookup"><span data-stu-id="2cdf6-154">Tips for good 3D models</span></span>

* <span data-ttu-id="2cdf6-155">Ao planejar dimensões para seu inicializador de aplicativo, tenha em seguida um cubo de 30 cm.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-155">When planning dimensions for your app launcher, shoot for roughly a 30-cm cube.</span></span> <span data-ttu-id="2cdf6-156">Portanto, uma proporção de tamanho de 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-156">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="2cdf6-157">Os modelos devem estar abaixo de 10.000 polígonos.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-157">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="2cdf6-158">Saiba mais sobre contagens de triângulos e níveis de detalhes (LODs)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-158">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="2cdf6-159">Teste em um headset de imersão.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-159">Test on an immersive headset.</span></span>
* <span data-ttu-id="2cdf6-160">Crie detalhes na geometria do modelo quando possível – não confie em texturas para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-160">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="2cdf6-161">Crie uma geometria de "água justa" fechada.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-161">Build “water tight” closed geometry.</span></span> <span data-ttu-id="2cdf6-162">Não há buracos que não sejam modelados.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-162">No holes that aren't modeled in.</span></span>
* <span data-ttu-id="2cdf6-163">Use materiais naturais em seu objeto.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-163">Use natural materials in your object.</span></span> <span data-ttu-id="2cdf6-164">Imagine criá-lo no mundo real.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-164">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="2cdf6-165">Certifique-se de que seu modelo Leia bem em diferentes distâncias e tamanhos.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-165">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="2cdf6-166">Quando seu modelo estiver pronto para começar, leia as [diretrizes de exportação de ativos](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span><span class="sxs-lookup"><span data-stu-id="2cdf6-166">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="2cdf6-167">![Modelo com detalhes sutis na textura](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-167">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="2cdf6-168">*Modelo com detalhes sutis na textura*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-168">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="2cdf6-169">O que evitar</span><span class="sxs-lookup"><span data-stu-id="2cdf6-169">What to avoid</span></span>

* <span data-ttu-id="2cdf6-170">Não use detalhes de alto contraste ou padrões e texturas pequenos e ocupados.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-170">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="2cdf6-171">Não use a geometria fina – ela não funciona bem em uma distância e terá alias incorreto.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-171">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="2cdf6-172">Não deixe que partes do seu modelo estendam muito além da proporção de tamanho de 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-172">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="2cdf6-173">Ele criará problemas de dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-173">It will create scaling problems.</span></span>

<span data-ttu-id="2cdf6-174">![Evitar padrões de alto contraste e pequenos ocupados](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-174">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="2cdf6-175">*Evitar padrões de alto contraste, pequenos e ocupados*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-175">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="2cdf6-176">Como tratar o tipo</span><span class="sxs-lookup"><span data-stu-id="2cdf6-176">How to handle type</span></span>

* <span data-ttu-id="2cdf6-177">Recomendamos que seu tipo ocupe cerca de 1/3 de seu iniciador de aplicativo (ou mais).</span><span class="sxs-lookup"><span data-stu-id="2cdf6-177">We recommend your type takes up about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="2cdf6-178">O tipo é o principal coisa que dá às pessoas uma ideia de que seu iniciador é, na verdade, um iniciador, portanto, é bom se for substancial.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-178">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s substantial.</span></span>
* <span data-ttu-id="2cdf6-179">Evite fazer o tipo superlargo – tente mantê-lo dentro dos limites das dimensões principais de iniciadores de aplicativo (mais ou menos).</span><span class="sxs-lookup"><span data-stu-id="2cdf6-179">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="2cdf6-180">O tipo flat pode funcionar, mas pode ser difícil de Exibir de determinados ângulos e em determinados ambientes.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-180">Flat type can work, but it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="2cdf6-181">Você pode considerar colocá-lo em um objeto sólido ou fazer um pano por trás dele para ajudar com isso.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-181">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="2cdf6-182">A adição de dimensão ao seu tipo é agradável em 3D.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-182">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="2cdf6-183">Sombreamento dos lados do tipo uma cor diferente e mais escura pode ajudar na legibilidade.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-183">Shading the sides of the type a different, darker color can help with readability.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="2cdf6-184">![Um tipo simples sem um pano de fundo pode ser difícil de ser exibido a partir de determinados ângulos e, em determinados ambientes, ](images/flattype-640px.png) *o tipo simples sem uma tela de fundo pode ser difícil de Exibir de determinados ângulos e em determinados ambientes*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-184">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2cdf6-185">![O tipo com um pano de fundo interno pode funcionar bem ](images/flattypeandbkg-640px.png) *com um pano de fundo interno que pode funcionar bem*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-185">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2cdf6-186">![O tipo de extrusão pode funcionar bem se você Sombrear os lados ](images/20171016-160221-mixedreality-640px.jpg) *tipo de extrusão pode funcionar bem se você Sombrear os lados*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-186">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="2cdf6-187">**Digitar cores que funcionam**</span><span class="sxs-lookup"><span data-stu-id="2cdf6-187">**Type colors that work**</span></span>

* <span data-ttu-id="2cdf6-188">Branco</span><span class="sxs-lookup"><span data-stu-id="2cdf6-188">White</span></span>
* <span data-ttu-id="2cdf6-189">Preto</span><span class="sxs-lookup"><span data-stu-id="2cdf6-189">Black</span></span>
* <span data-ttu-id="2cdf6-190">Cor semisaturada brilhante</span><span class="sxs-lookup"><span data-stu-id="2cdf6-190">Bright semi-saturated color</span></span>

<span data-ttu-id="2cdf6-191">![Digite as cores que funcionam.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-191">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="2cdf6-192">*Digitar cores que funcionam*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-192">*Type colors that work*</span></span>

### <a name="colors-to-avoid"></a><span data-ttu-id="2cdf6-193">Cores a serem evitadas</span><span class="sxs-lookup"><span data-stu-id="2cdf6-193">Colors to avoid</span></span>

<span data-ttu-id="2cdf6-194">As cores de tipo que causam problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="2cdf6-194">Type colors that cause trouble include:</span></span>

* <span data-ttu-id="2cdf6-195">Tons médios</span><span class="sxs-lookup"><span data-stu-id="2cdf6-195">Mid-tones</span></span>
* <span data-ttu-id="2cdf6-196">Cinza</span><span class="sxs-lookup"><span data-stu-id="2cdf6-196">Gray</span></span>
* <span data-ttu-id="2cdf6-197">Cores sobresaturadas ou cores dessaturadas</span><span class="sxs-lookup"><span data-stu-id="2cdf6-197">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="2cdf6-198">![Digite as cores que causam problemas.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-198">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="2cdf6-199">*Digitar cores que causam problemas*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-199">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="2cdf6-200">Iluminação</span><span class="sxs-lookup"><span data-stu-id="2cdf6-200">Lighting</span></span>

<span data-ttu-id="2cdf6-201">A iluminação para seu inicializador de aplicativos vem do ambiente de casa da Cliff.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-201">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="2cdf6-202">Certifique-se de testar seu iniciador em vários lugares em toda a casa para que ele fique bom na luz e nas sombras.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-202">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="2cdf6-203">A boa notícia é que, se você seguiu as outras diretrizes de design deste documento, o iniciador deve estar em bom formato para a maior parte da luz na casa Cliff.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-203">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="2cdf6-204">Bons lugares para testar como o iniciador analisa as várias luzes no ambiente são o estúdio, a sala de mídia, em qualquer lugar fora e na Patio de fundo (a área concreta com o gramado).</span><span class="sxs-lookup"><span data-stu-id="2cdf6-204">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="2cdf6-205">Outro bom teste é colocá-lo na metade e na metade da sombra e ver como ele se parece.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-205">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="2cdf6-206">![Verifique se o iniciador parece bom tanto na luz quanto nas sombras.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-206">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="2cdf6-207">*Verifique se o iniciador parece bom tanto na luz quanto nas sombras*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-207">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="2cdf6-208">Texturing</span><span class="sxs-lookup"><span data-stu-id="2cdf6-208">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="2cdf6-209">Criando suas texturas</span><span class="sxs-lookup"><span data-stu-id="2cdf6-209">Authoring your textures</span></span>

<span data-ttu-id="2cdf6-210">O formato final do seu iniciador de aplicativo 3D será um arquivo. glb, que é feito usando o pipeline PBR (processamento com base fisicamente).</span><span class="sxs-lookup"><span data-stu-id="2cdf6-210">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="2cdf6-211">Isso pode ser um processo complicado – agora é um bom momento para empregar um artista técnico, caso ainda não tenha feito isso.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-211">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="2cdf6-212">Se você for um corajoso DIY, dedicar o tempo para [Pesquisar e aprender a terminologia do PBR](https://wiki.polycount.com/wiki/PBR) e o que está acontecendo nos bastidores antes de começar irá ajudá-lo a evitar erros comuns.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-212">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="2cdf6-213">![Exemplo: novo aplicativo de observações](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-213">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="2cdf6-214">*Observação de novo exemplo de inicializador de aplicativo 3D (aplicativo fictício)*</span><span class="sxs-lookup"><span data-stu-id="2cdf6-214">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="recommended-authoring-tool"></a><span data-ttu-id="2cdf6-215">Ferramenta de criação recomendada</span><span class="sxs-lookup"><span data-stu-id="2cdf6-215">Recommended authoring tool</span></span>

<span data-ttu-id="2cdf6-216">É recomendável usar a [pincel de substância](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic para criar o arquivo final.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-216">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="2cdf6-217">Se você não estiver familiarizado com a criação de sombreadores de PBR no pintor da substância, aqui está um [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="2cdf6-217">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="2cdf6-218">(Alternativamente [3D-revestimento](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/)ou [Marmoset Toolbag](https://www.marmoset.co/toolbag/) também funcionaria se você estivesse mais familiarizado com um deles.)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-218">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="2cdf6-219">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="2cdf6-219">Best practices</span></span>

* <span data-ttu-id="2cdf6-220">Se o objeto iniciador do aplicativo foi criado para PBR, deve ser simples convertê-lo para o ambiente Cliff House.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-220">If your app launcher object was authored for PBR, it should be straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="2cdf6-221">Nosso sombreador está esperando um fluxo de trabalho de metal/áspero – o sombreador do PBR inreal é um fax próximo.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-221">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="2cdf6-222">Ao exportar suas texturas, mantenha os [tamanhos de textura recomendados](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) em mente.</span><span class="sxs-lookup"><span data-stu-id="2cdf6-222">When exporting your textures, keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="2cdf6-223">Certifique-se de criar seus objetos para iluminação em tempo real – isso significa:</span><span class="sxs-lookup"><span data-stu-id="2cdf6-223">Make sure to build your objects for real-time lighting—this means:</span></span>
  * <span data-ttu-id="2cdf6-224">Evite sombras inclusass – ou sombras pintadas</span><span class="sxs-lookup"><span data-stu-id="2cdf6-224">Avoid baked shadows – or painted shadows</span></span>
  * <span data-ttu-id="2cdf6-225">Evite a iluminação inclusas nas texturas</span><span class="sxs-lookup"><span data-stu-id="2cdf6-225">Avoid baked lighting in the textures</span></span>
  * <span data-ttu-id="2cdf6-226">Use um dos pacotes de criação de material do PBR para obter os mapas corretos gerados para nosso sombreador</span><span class="sxs-lookup"><span data-stu-id="2cdf6-226">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="2cdf6-227">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cdf6-227">See also</span></span>

* [<span data-ttu-id="2cdf6-228">Crie modelos 3D para uso na página inicial misturada de realidade</span><span class="sxs-lookup"><span data-stu-id="2cdf6-228">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="2cdf6-229">Implementar inicializadores de aplicativos 3D (aplicativos UWP)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-229">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="2cdf6-230">Implementar inicializadores de aplicativos 3D (aplicativos Win32)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-230">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
