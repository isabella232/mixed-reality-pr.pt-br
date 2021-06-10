---
title: Tabela periódica dos elementos
description: Saiba como estabelecer uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma coleção object com a Tabela Periódica do aplicativo de exemplo Elements.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, aplicativo de exemplo, controles, MRTK, Kit de Ferramentas de Realidade Misturada, Unity, aplicativos de exemplo, aplicativos de exemplo, open-source, Microsoft Store, HoloLens, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: ed8c35fc6467322c25b92924b134f176fa4a9b47
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743415"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="0aa0a-104">Tabela periódica dos elementos</span><span class="sxs-lookup"><span data-stu-id="0aa0a-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="0aa0a-105">Este artigo aborda um exemplo exploratório que criamos nos [Laboratórios](https://github.com/Microsoft/MRDesignLabs_Unity)de Design de Realidade Misturada, um local em que compartilhamos nossos aprendizados e sugestões para o desenvolvimento de aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="0aa0a-106">Nossos artigos e código relacionados ao design evoluirão à medida que fazemos novas descobertas.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="0aa0a-107">[A Tabela Periódica dos Elementos é](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) um aplicativo de exemplo de código aberto dos Laboratórios de Design de Realidade Misturada da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="0aa0a-108">Saiba como estabelecer uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma **[Coleção de objetos](../../design/object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-108">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="0aa0a-109">Saiba também como criar objetos interagidos que respondem a entradas padrão do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="0aa0a-110">Você pode usar os componentes desse projeto para criar sua própria experiência de aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabela de período do aplicativo Elements](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="0aa0a-112">Vídeo de demonstração</span><span class="sxs-lookup"><span data-stu-id="0aa0a-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="0aa0a-113">Gravado com o HoloLens 2 usando Captura de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="0aa0a-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="0aa0a-114">Sobre o aplicativo</span><span class="sxs-lookup"><span data-stu-id="0aa0a-114">About the app</span></span>

<span data-ttu-id="0aa0a-115">A Tabela Periódica dos Elementos visualiza os elementos quimicos e cada uma de suas propriedades em um espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="0aa0a-116">Ele incorpora as interações básicas do HoloLens, como o olhar e o toque de ar.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="0aa0a-117">Os usuários podem aprender sobre os elementos com modelos 3D animados.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="0aa0a-118">Eles podem entender visualmente o shell de electron de um elemento e seus anões , que é composto de protons e anões.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="0aa0a-119">Segundo plano</span><span class="sxs-lookup"><span data-stu-id="0aa0a-119">Background</span></span>

<span data-ttu-id="0aa0a-120">Depois de experimentar o HoloLens pela primeira vez, eu sabia que queria experimentar um aplicativo de tabela periódico em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-120">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="0aa0a-121">Como cada elemento tem muitos pontos de dados exibidos com texto, eu acho que seria um ótimo assunto explorar a composição tipográfica em um espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="0aa0a-122">Dar aos usuários a oportunidade de visualizar o modelo de electron do elemento era outra parte interessante desse projeto.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-122">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="0aa0a-123">Design</span><span class="sxs-lookup"><span data-stu-id="0aa0a-123">Design</span></span>

<span data-ttu-id="0aa0a-124">Para a exibição padrão da tabela periódica, eu vi caixas tridimensionais que contêm o modelo de electron de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="0aa0a-125">A superfície de cada caixa seria translúcida para que o usuário pudesse ter uma ideia aproximada do volume do elemento.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="0aa0a-126">Com o olhar e o toque de ar, o usuário pode abrir uma exibição detalhada de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="0aa0a-127">Para tornar a transição entre a exibição de tabela e a exibição de detalhes suave e natural, eu a torna semelhante à interação física de uma caixa abrindo na vida real.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="0aa0a-128">![Esboço de design](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="0aa0a-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="0aa0a-129">*Esboçar esboços*</span><span class="sxs-lookup"><span data-stu-id="0aa0a-129">*Design sketches*</span></span>

<span data-ttu-id="0aa0a-130">Na exibição detalhada, eu queria visualizar as informações de cada elemento com texto renderizado perfeitamente no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="0aa0a-131">O modelo de electron 3D animado é exibido na área central e pode ser exibido de diferentes ângulos.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interação](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="0aa0a-133">![Protótipos](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="0aa0a-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="0aa0a-134">*Protótipos de interação*</span><span class="sxs-lookup"><span data-stu-id="0aa0a-134">*Interaction prototypes*</span></span>

<span data-ttu-id="0aa0a-135">O usuário pode alterar o tipo de superfície tocando ar nos botões na parte inferior da tabela– ele pode alternar entre plano, cilindro, esfera e dispersão.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="0aa0a-136">Controles e padrões comuns usados neste aplicativo</span><span class="sxs-lookup"><span data-stu-id="0aa0a-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="0aa0a-137">Objeto interajante (botão)</span><span class="sxs-lookup"><span data-stu-id="0aa0a-137">Interactable object (button)</span></span>

<span data-ttu-id="0aa0a-138">[O objeto interagente](../../design/interactable-object.md) é um objeto que pode responder a entradas básicas do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-138">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="0aa0a-139">Ele é fornecido como um pré-bb/script, que você pode aplicar facilmente a qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-139">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="0aa0a-140">Por exemplo, você pode tornar uma cafeteira em sua cena interagente e responder a entradas como olhar, toque de ar, navegação e gestos de manipulação.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="0aa0a-141">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="0aa0a-141">Learn more</span></span>](../../design/interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="0aa0a-143">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="0aa0a-143">Object collection</span></span>

<span data-ttu-id="0aa0a-144">[A coleção de](../../design/object-collection.md) objetos é um objeto , que ajuda você a estabelecer vários objetos em várias formas.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-144">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="0aa0a-145">Ele dá suporte a plano, cilindro, esfera e dispersão.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-145">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="0aa0a-146">Você pode configurar propriedades adicionais, como radius, número de linhas e espaçamento.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="0aa0a-147">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="0aa0a-147">Learn more</span></span>](../../design/object-collection.md)

![Coleção de objetos](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="0aa0a-149">Detalhes técnicos</span><span class="sxs-lookup"><span data-stu-id="0aa0a-149">Technical details</span></span>

<span data-ttu-id="0aa0a-150">Você pode encontrar scripts e pré-fabs para a Tabela Periódica do aplicativo Elements no [GitHub do Mixed Reality Design Labs.](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)</span><span class="sxs-lookup"><span data-stu-id="0aa0a-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="0aa0a-151">História de porta para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="0aa0a-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="0aa0a-152">Leia a história sobre como a Tabela Periódica do aplicativo Elements foi atualizada com as interações instintivas do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0aa0a-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="0aa0a-153">Tabela periódica dos elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="0aa0a-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="0aa0a-154">Sobre o autor</span><span class="sxs-lookup"><span data-stu-id="0aa0a-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="0aa0a-155"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="0aa0a-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="0aa0a-156">Designer de UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="0aa0a-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="0aa0a-157">Confira também</span><span class="sxs-lookup"><span data-stu-id="0aa0a-157">See also</span></span>

* <span data-ttu-id="0aa0a-158">[Hub de Exemplos do MRTK](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="0aa0a-158">[MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="0aa0a-159">[Surfaces](sampleapp-surfaces.md) - [(download da Microsoft Store no HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="0aa0a-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="0aa0a-160">Tabela periódica dos elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="0aa0a-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="0aa0a-161">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="0aa0a-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)