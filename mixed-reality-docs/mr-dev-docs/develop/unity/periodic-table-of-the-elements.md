---
title: Tabela periódica dos elementos
description: A tabela periódica dos elementos é um aplicativo de exemplo de código-fonte aberto dos laboratórios de design de realidade misturada da Microsoft. Saiba como criar uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma coleção de objetos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, aplicativo de exemplo, controles, MRTK, kit de ferramentas de realidade misturada, Unity, aplicativos de exemplo, aplicativos de exemplo, software livre, Microsoft Store, HoloLens, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual
ms.openlocfilehash: a4099c889fee886e63d3a8b773398a250621f26e
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010177"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="e25a2-105">Tabela periódica dos elementos</span><span class="sxs-lookup"><span data-stu-id="e25a2-105">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="e25a2-106">Este artigo discute um exemplo exploratório que criamos nos laboratórios de [design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity), um lugar onde compartilhamos nossas aprendeções e sugestões para o desenvolvimento de aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="e25a2-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="e25a2-107">Nossos artigos e códigos relacionados ao design irão evoluir à medida que fizermos novas descobertas.</span><span class="sxs-lookup"><span data-stu-id="e25a2-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="e25a2-108">[A tabela periódica dos elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) é um aplicativo de exemplo de código-fonte aberto dos laboratórios de design de realidade misturada da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e25a2-108">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="e25a2-109">Saiba como dispor uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma **[coleção de objetos](../../design/object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="e25a2-109">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="e25a2-110">Saiba também como criar objetos que respondam às entradas padrão do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e25a2-110">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="e25a2-111">Você pode usar os componentes deste projeto para criar sua própria experiência de aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="e25a2-111">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabela de período do aplicativo de elementos](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="e25a2-113">Vídeo de demonstração</span><span class="sxs-lookup"><span data-stu-id="e25a2-113">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="e25a2-114">Registrado com o HoloLens 2 usando a captura de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="e25a2-114">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="e25a2-115">Sobre o aplicativo</span><span class="sxs-lookup"><span data-stu-id="e25a2-115">About the app</span></span>

<span data-ttu-id="e25a2-116">A tabela periódica dos elementos visualiza os elementos químicos e cada uma de suas propriedades em um espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="e25a2-116">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="e25a2-117">Ele incorpora as interações básicas de HoloLens, como olhar e toque de ar.</span><span class="sxs-lookup"><span data-stu-id="e25a2-117">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="e25a2-118">Os usuários podem aprender sobre os elementos com modelos 3D animados.</span><span class="sxs-lookup"><span data-stu-id="e25a2-118">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="e25a2-119">Eles podem entender visualmente o Shell de um dos elementos do seu núcleo, que é composto de protoneladas e neutrons.</span><span class="sxs-lookup"><span data-stu-id="e25a2-119">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="e25a2-120">Segundo plano</span><span class="sxs-lookup"><span data-stu-id="e25a2-120">Background</span></span>

<span data-ttu-id="e25a2-121">Depois de ter experimentado o HoloLens pela primeira vez, sabia que queria experimentar um aplicativo de tabela periódico em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="e25a2-121">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="e25a2-122">Como cada elemento tem muitos pontos de dados que são exibidos com texto, pensei que seria um ótimo assunto para explorar a composição tipográfica em um espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="e25a2-122">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="e25a2-123">Dar aos usuários a chance de visualizar o modelo de sem interspersão do elemento era outra parte interessante deste projeto.</span><span class="sxs-lookup"><span data-stu-id="e25a2-123">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="e25a2-124">Design</span><span class="sxs-lookup"><span data-stu-id="e25a2-124">Design</span></span>

<span data-ttu-id="e25a2-125">Para a exibição padrão da tabela periódica, Imaginai caixas tridimensionais que conteriam o modelo de todos os elementos.</span><span class="sxs-lookup"><span data-stu-id="e25a2-125">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="e25a2-126">A superfície de cada caixa seria translúcida para que o usuário pudesse obter uma ideia aproximada do volume do elemento.</span><span class="sxs-lookup"><span data-stu-id="e25a2-126">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="e25a2-127">Com o olhar e o toque do Air, o usuário pode abrir uma exibição detalhada de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="e25a2-127">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="e25a2-128">Para fazer com que a transição entre a exibição de tabela e a exibição de detalhes seja suave e natural, eu o fiz de forma semelhante à interação física de uma abertura de caixa na vida real.</span><span class="sxs-lookup"><span data-stu-id="e25a2-128">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="e25a2-129">![Esboço de design](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="e25a2-129">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="e25a2-130">*Esboços de design*</span><span class="sxs-lookup"><span data-stu-id="e25a2-130">*Design sketches*</span></span>

<span data-ttu-id="e25a2-131">No modo de exibição de detalhes, eu queria visualizar as informações de cada elemento com o texto renderizado linda em espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="e25a2-131">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="e25a2-132">O modelo de rede 3D animada é exibido na área central e pode ser exibido a partir de diferentes ângulos.</span><span class="sxs-lookup"><span data-stu-id="e25a2-132">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interação](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="e25a2-134">![Protótipos](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="e25a2-134">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="e25a2-135">*Protótipos de interação*</span><span class="sxs-lookup"><span data-stu-id="e25a2-135">*Interaction prototypes*</span></span>

<span data-ttu-id="e25a2-136">O usuário pode alterar o tipo de superfície por ar tocando nos botões na parte inferior da tabela-eles podem alternar entre plano, cilindro, esfera e dispersão.</span><span class="sxs-lookup"><span data-stu-id="e25a2-136">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="e25a2-137">Controles e padrões comuns usados neste aplicativo</span><span class="sxs-lookup"><span data-stu-id="e25a2-137">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="e25a2-138">Objeto interagir (botão)</span><span class="sxs-lookup"><span data-stu-id="e25a2-138">Interactable object (button)</span></span>

<span data-ttu-id="e25a2-139">O [objeto de interação](../../design/interactable-object.md) é um objeto, que pode responder às entradas básicas do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e25a2-139">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="e25a2-140">Ele é fornecido como um pré-fabricado/script, que você pode aplicar facilmente a qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="e25a2-140">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="e25a2-141">Por exemplo, você pode fazer com que uma xícara de café em sua cena interaja e responda a entradas como olhar, toque de ar, navegação e gestos de manipulação.</span><span class="sxs-lookup"><span data-stu-id="e25a2-141">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="e25a2-142">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="e25a2-142">Learn more</span></span>](../../design/interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="e25a2-144">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="e25a2-144">Object collection</span></span>

<span data-ttu-id="e25a2-145">A [coleção de objetos](../../design/object-collection.md) é um objeto, que ajuda você a dispor vários objetos em várias formas.</span><span class="sxs-lookup"><span data-stu-id="e25a2-145">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="e25a2-146">Ele dá suporte a plano, cilindro, esfera e dispersão.</span><span class="sxs-lookup"><span data-stu-id="e25a2-146">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="e25a2-147">Você pode configurar propriedades adicionais, como RADIUS, número de linhas e espaçamento.</span><span class="sxs-lookup"><span data-stu-id="e25a2-147">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="e25a2-148">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="e25a2-148">Learn more</span></span>](../../design/object-collection.md)

![Coleção de objetos](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="e25a2-150">Detalhes técnicos</span><span class="sxs-lookup"><span data-stu-id="e25a2-150">Technical details</span></span>

<span data-ttu-id="e25a2-151">Você pode encontrar scripts e pré-fabricados para a tabela periódica do aplicativo de elementos no [GitHub de laboratórios de design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="e25a2-151">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="e25a2-152">A história do portador para o HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e25a2-152">Porting story for HoloLens 2</span></span>

<span data-ttu-id="e25a2-153">Leia a história sobre como a tabela periódica do aplicativo de elementos foi atualizada com as interações de instinctual do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e25a2-153">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="e25a2-154">Tabela periódica dos elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="e25a2-154">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="e25a2-155">Sobre o autor</span><span class="sxs-lookup"><span data-stu-id="e25a2-155">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="e25a2-156"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="e25a2-156"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="e25a2-157">Designer de UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="e25a2-157">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="e25a2-158">Confira também</span><span class="sxs-lookup"><span data-stu-id="e25a2-158">See also</span></span>

* <span data-ttu-id="e25a2-159">[Hub de Exemplos do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="e25a2-159">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="e25a2-160">[Surfaces](sampleapp-surfaces.md) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="e25a2-160">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="e25a2-161">Tabela periódica dos elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="e25a2-161">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="e25a2-162">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="e25a2-162">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)