---
title: Tabela periódica dos elementos
description: A tabela periódica dos elementos é um aplicativo de exemplo de software livre dos laboratórios de design da realidade misturada da Microsoft, em que você pode aprender a criar uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma coleção de objetos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, aplicativo de exemplo, controles
ms.openlocfilehash: 82ffa19b27c1d2687b67df659cb3bb50544748fc
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573260"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="3cd68-104">Tabela periódica dos elementos</span><span class="sxs-lookup"><span data-stu-id="3cd68-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="3cd68-105">Este artigo discute um exemplo exploratório que criamos nos laboratórios de [design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity), um lugar onde compartilhamos nossas aprendeções e sugestões para o desenvolvimento de aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="3cd68-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="3cd68-106">Nossos artigos e códigos relacionados ao design irão evoluir à medida que fizermos novas descobertas.</span><span class="sxs-lookup"><span data-stu-id="3cd68-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="3cd68-107">[A tabela periódica dos elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) é um aplicativo de exemplo de código-fonte aberto dos laboratórios de design de realidade misturada da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3cd68-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="3cd68-108">Com esse projeto, você pode aprender a formatar uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma **[coleção de objetos](../../design/object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="3cd68-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="3cd68-109">Saiba também como criar objetos que respondam às entradas padrão do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3cd68-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="3cd68-110">Você pode usar os componentes deste projeto para criar sua própria experiência de aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="3cd68-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabela de período do aplicativo de elementos](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="3cd68-112">Vídeo de demonstração</span><span class="sxs-lookup"><span data-stu-id="3cd68-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="3cd68-113">Registrado com o HoloLens 2 usando a captura de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="3cd68-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="3cd68-114">Sobre o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3cd68-114">About the app</span></span>

<span data-ttu-id="3cd68-115">A tabela periódica dos elementos visualiza os elementos químicos e cada uma de suas propriedades em um espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="3cd68-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="3cd68-116">Ele incorpora as interações básicas de HoloLens, como olhar e toque de ar.</span><span class="sxs-lookup"><span data-stu-id="3cd68-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="3cd68-117">Os usuários podem aprender sobre os elementos com modelos 3D animados.</span><span class="sxs-lookup"><span data-stu-id="3cd68-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="3cd68-118">Eles podem entender visualmente o Shell de um dos elementos do seu núcleo, que é composto de protoneladas e neutrons.</span><span class="sxs-lookup"><span data-stu-id="3cd68-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="3cd68-119">Tela de fundo</span><span class="sxs-lookup"><span data-stu-id="3cd68-119">Background</span></span>

<span data-ttu-id="3cd68-120">Depois de ter experimentado o HoloLens pela primeira vez, um aplicativo de tabela periódico foi uma ideia que eu sabia que queria experimentar em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="3cd68-120">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="3cd68-121">Como cada elemento tem muitos pontos de dados que são exibidos com texto, pensei que seria um ótimo assunto para explorar a composição tipográfica em um espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="3cd68-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="3cd68-122">Ser capaz de visualizar o modelo de sem interesse do elemento foi outra parte interessante deste projeto.</span><span class="sxs-lookup"><span data-stu-id="3cd68-122">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="3cd68-123">Design</span><span class="sxs-lookup"><span data-stu-id="3cd68-123">Design</span></span>

<span data-ttu-id="3cd68-124">Para a exibição padrão da tabela periódica, Imaginai caixas tridimensionais que conteriam o modelo de todos os elementos.</span><span class="sxs-lookup"><span data-stu-id="3cd68-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="3cd68-125">A superfície de cada caixa seria translúcida para que o usuário pudesse obter uma ideia aproximada do volume do elemento.</span><span class="sxs-lookup"><span data-stu-id="3cd68-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="3cd68-126">Com o olhar e o toque do Air, o usuário pode abrir uma exibição detalhada de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="3cd68-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="3cd68-127">Para fazer com que a transição entre a exibição de tabela e a exibição de detalhes seja suave e natural, eu o fiz de forma semelhante à interação física de uma abertura de caixa na vida real.</span><span class="sxs-lookup"><span data-stu-id="3cd68-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="3cd68-128">![Esboço de design](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="3cd68-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="3cd68-129">*Esboços de design*</span><span class="sxs-lookup"><span data-stu-id="3cd68-129">*Design sketches*</span></span>

<span data-ttu-id="3cd68-130">No modo de exibição de detalhes, eu queria visualizar as informações de cada elemento com o texto renderizado linda em espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="3cd68-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="3cd68-131">O modelo de rede 3D animada é exibido na área central e pode ser exibido a partir de diferentes ângulos.</span><span class="sxs-lookup"><span data-stu-id="3cd68-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interação](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="3cd68-133">![Protótipos](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="3cd68-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="3cd68-134">*Protótipos de interação*</span><span class="sxs-lookup"><span data-stu-id="3cd68-134">*Interaction prototypes*</span></span>

<span data-ttu-id="3cd68-135">O usuário pode alterar o tipo de superfície por ar tocando nos botões na parte inferior da tabela-eles podem alternar entre plano, cilindro, esfera e dispersão.</span><span class="sxs-lookup"><span data-stu-id="3cd68-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="3cd68-136">Controles e padrões comuns usados neste aplicativo</span><span class="sxs-lookup"><span data-stu-id="3cd68-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="3cd68-137">Objeto interagir (botão)</span><span class="sxs-lookup"><span data-stu-id="3cd68-137">Interactable object (button)</span></span>

<span data-ttu-id="3cd68-138">O [objeto de interação](../../design/interactable-object.md) é um objeto que pode responder às entradas básicas do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3cd68-138">[Interactable object](../../design/interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="3cd68-139">Ele é fornecido como um pré-fabricado/script que você pode aplicar facilmente a qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="3cd68-139">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="3cd68-140">Por exemplo, você pode fazer com que uma xícara de café em sua cena interaja e responda a entradas como olhar, toque de ar, navegação e gestos de manipulação.</span><span class="sxs-lookup"><span data-stu-id="3cd68-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="3cd68-141">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="3cd68-141">Learn more</span></span>](../../design/interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="3cd68-143">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="3cd68-143">Object collection</span></span>

<span data-ttu-id="3cd68-144">A [coleção de objetos](../../design/object-collection.md) é um objeto que ajuda você a dispor vários objetos em várias formas.</span><span class="sxs-lookup"><span data-stu-id="3cd68-144">[Object collection](../../design/object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="3cd68-145">Ele dá suporte a plano, cilindro, esfera e dispersão.</span><span class="sxs-lookup"><span data-stu-id="3cd68-145">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="3cd68-146">Você pode configurar propriedades adicionais, como RADIUS, número de linhas e espaçamento.</span><span class="sxs-lookup"><span data-stu-id="3cd68-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="3cd68-147">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="3cd68-147">Learn more</span></span>](../../design/object-collection.md)

![Coleção de objetos](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="3cd68-149">Detalhes técnicos</span><span class="sxs-lookup"><span data-stu-id="3cd68-149">Technical details</span></span>

<span data-ttu-id="3cd68-150">Você pode encontrar scripts e pré-fabricados para a tabela periódica do aplicativo de elementos no [GitHub de laboratórios de design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="3cd68-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="3cd68-151">A história do portador para o HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3cd68-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="3cd68-152">Leia a história sobre como a tabela periódica do aplicativo de elementos foi atualizada com as interações de instinctual do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3cd68-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="3cd68-153">Tabela periódica dos elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="3cd68-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="3cd68-154">Sobre o autor</span><span class="sxs-lookup"><span data-stu-id="3cd68-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="3cd68-155"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="3cd68-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="3cd68-156">Designer de UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="3cd68-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="3cd68-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cd68-157">See also</span></span>

* <span data-ttu-id="3cd68-158">[Hub de Exemplos do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="3cd68-158">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="3cd68-159">[Surfaces](sampleapp-surfaces.md) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="3cd68-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="3cd68-160">Tabela periódica dos elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="3cd68-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="3cd68-161">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="3cd68-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)