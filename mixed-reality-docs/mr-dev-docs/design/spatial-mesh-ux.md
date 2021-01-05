---
title: Visualização de malha espacial
description: Saiba mais sobre como os dispositivos entendem ambientes físicos usando malhas espaciais.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realidade misturada, HoloLens, controles de interface do usuário, interação, interface do usuário, UX, design de UX, interface do usuário espacial, interação espacial, interface do usuário 3D, UX 3D, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: ffa13da6762b803ba2a3f370308ac2af65164ecf
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848193"
---
# <a name="spatial-mesh"></a><span data-ttu-id="2a0f9-104">Malha espacial</span><span class="sxs-lookup"><span data-stu-id="2a0f9-104">Spatial mesh</span></span>

![Malha espacial](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="2a0f9-106">Os usuários aprendem como um dispositivo percebe e compreende o ambiente físico por meio da visualização de malha espacial.</span><span class="sxs-lookup"><span data-stu-id="2a0f9-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="2a0f9-107">A visualização de malha espacial adequada pode criar uma experiência de interessantes e mágico enquanto fornece o contexto espacial.</span><span class="sxs-lookup"><span data-stu-id="2a0f9-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="2a0f9-108">Diretriz de design</span><span class="sxs-lookup"><span data-stu-id="2a0f9-108">Design guideline</span></span>

<span data-ttu-id="2a0f9-109">É importante permitir que o usuário se concentre e interaja com o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2a0f9-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="2a0f9-110">A visualização contínua da malha espacial em segundo plano pode ser uma distração.</span><span class="sxs-lookup"><span data-stu-id="2a0f9-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="2a0f9-111">É recomendável Visualizar o ambiente com moderação, seja apenas uma vez na inicialização inicial ou quando o usuário mostrar claramente que deseja ver a malha ambiental por direcionamento e espaço de toque.</span><span class="sxs-lookup"><span data-stu-id="2a0f9-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="2a0f9-112">Você pode observar esse comportamento no portal de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="2a0f9-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="2a0f9-113">Visualização de malha espacial no MRTK (Kit de ferramentas de realidade mista) para Unity</span><span class="sxs-lookup"><span data-stu-id="2a0f9-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="2a0f9-114">O MRTK fornece vários materiais para a visualização de malha espacial.</span><span class="sxs-lookup"><span data-stu-id="2a0f9-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="2a0f9-115">**MRTK_Wireframe. esteira, MRTK_Wireframe. passe-partout**: material de malha espacial estática padrão, que mostra os contornos de malha sem animação.</span><span class="sxs-lookup"><span data-stu-id="2a0f9-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="2a0f9-116">Esse material é útil para fins de depuração, pois mostra as geometrias de malha espacial inteiras.</span><span class="sxs-lookup"><span data-stu-id="2a0f9-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="2a0f9-117">No entanto, não é recomendável para produção.</span><span class="sxs-lookup"><span data-stu-id="2a0f9-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="2a0f9-118">**MRTK_SurfaceReconstruction. passe-partout**: esse material oferece um efeito de pulso animado na malha espacial.</span><span class="sxs-lookup"><span data-stu-id="2a0f9-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="2a0f9-119">Você pode usar esse material para visualizar o ambiente em um momento específico ou na entrada aérea do usuário.</span><span class="sxs-lookup"><span data-stu-id="2a0f9-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="2a0f9-120">Consulte a cena **PulseShaderExamples. Unity** para ver os exemplos.</span><span class="sxs-lookup"><span data-stu-id="2a0f9-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="2a0f9-121">Para obter mais informações, consulte [reconhecimento espacial do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) e [sombreador MRTK-Pulse](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).</span><span class="sxs-lookup"><span data-stu-id="2a0f9-121">For more information, see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="2a0f9-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a0f9-122">See also</span></span>

* [<span data-ttu-id="2a0f9-123">Cursores</span><span class="sxs-lookup"><span data-stu-id="2a0f9-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="2a0f9-124">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="2a0f9-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="2a0f9-125">Botão</span><span class="sxs-lookup"><span data-stu-id="2a0f9-125">Button</span></span>](button.md)
* [<span data-ttu-id="2a0f9-126">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="2a0f9-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="2a0f9-127">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="2a0f9-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="2a0f9-128">Manipulação</span><span class="sxs-lookup"><span data-stu-id="2a0f9-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="2a0f9-129">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="2a0f9-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="2a0f9-130">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="2a0f9-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="2a0f9-131">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="2a0f9-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="2a0f9-132">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="2a0f9-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="2a0f9-133">Teclado</span><span class="sxs-lookup"><span data-stu-id="2a0f9-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="2a0f9-134">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="2a0f9-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="2a0f9-135">Slate</span><span class="sxs-lookup"><span data-stu-id="2a0f9-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="2a0f9-136">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="2a0f9-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="2a0f9-137">Sombreador</span><span class="sxs-lookup"><span data-stu-id="2a0f9-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="2a0f9-138">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="2a0f9-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="2a0f9-139">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="2a0f9-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="2a0f9-140">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="2a0f9-140">Surface magnetism</span></span>](surface-magnetism.md)
