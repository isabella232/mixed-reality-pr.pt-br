---
title: Visualização de malha espacial
description: Saiba mais sobre as diretrizes de design e a compreensão do ambiente físico com a visualização de malha espacial no MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realidade misturada, HoloLens, controles de interface do usuário, interação, interface do usuário, UX, design de UX, interface do usuário espacial, interação espacial, interface do usuário 3D, UX 3D, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: 5e8ffbb90b1143cd4e11bf45a889c11c233232df
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759802"
---
# <a name="spatial-mesh"></a><span data-ttu-id="f4a2f-104">Malha espacial</span><span class="sxs-lookup"><span data-stu-id="f4a2f-104">Spatial mesh</span></span>

![Malha espacial](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="f4a2f-106">Os usuários aprendem como um dispositivo percebe e compreende o ambiente físico por meio da visualização de malha espacial.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="f4a2f-107">A visualização de malha espacial adequada pode criar uma experiência de interessantes e mágico enquanto fornece o contexto espacial.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="f4a2f-108">Diretriz de design</span><span class="sxs-lookup"><span data-stu-id="f4a2f-108">Design guideline</span></span>

<span data-ttu-id="f4a2f-109">É importante permitir que o usuário se concentre e interaja com o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="f4a2f-110">A visualização contínua da malha espacial em segundo plano pode ser uma distração.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="f4a2f-111">É recomendável Visualizar o ambiente com moderação, seja apenas uma vez na inicialização inicial ou quando o usuário mostrar claramente que deseja ver a malha ambiental por direcionamento e espaço de toque.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="f4a2f-112">Você pode observar esse comportamento no portal de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="f4a2f-113">Visualização de malha espacial no MRTK (Kit de ferramentas de realidade mista) para Unity</span><span class="sxs-lookup"><span data-stu-id="f4a2f-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="f4a2f-114">O MRTK fornece vários materiais para a visualização de malha espacial.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="f4a2f-115">**MRTK_Wireframe. esteira, MRTK_Wireframe. passe-partout**: material de malha espacial estática padrão, que mostra os contornos de malha sem animação.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="f4a2f-116">Esse material é útil para fins de depuração, pois mostra as geometrias de malha espacial inteiras.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="f4a2f-117">No entanto, não é recomendável para produção.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="f4a2f-118">**MRTK_SurfaceReconstruction. passe-partout**: esse material oferece um efeito de pulso animado na malha espacial.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="f4a2f-119">Você pode usar esse material para visualizar o ambiente em um momento específico ou na entrada aérea do usuário.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="f4a2f-120">Consulte a cena **PulseShaderExamples. Unity** para ver os exemplos.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="f4a2f-121">Para obter mais informações, consulte [reconhecimento espacial do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md) e [sombreador MRTK-Pulse](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/pulse-shader.md).</span><span class="sxs-lookup"><span data-stu-id="f4a2f-121">For more information, see [MRTK - Spatial Awareness](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md) and [MRTK - Pulse Shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/pulse-shader.md).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="f4a2f-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="f4a2f-122">See also</span></span>

* [<span data-ttu-id="f4a2f-123">Cursores</span><span class="sxs-lookup"><span data-stu-id="f4a2f-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f4a2f-124">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="f4a2f-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="f4a2f-125">Botão</span><span class="sxs-lookup"><span data-stu-id="f4a2f-125">Button</span></span>](button.md)
* [<span data-ttu-id="f4a2f-126">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="f4a2f-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f4a2f-127">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="f4a2f-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f4a2f-128">Manipulação</span><span class="sxs-lookup"><span data-stu-id="f4a2f-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f4a2f-129">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="f4a2f-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="f4a2f-130">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="f4a2f-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="f4a2f-131">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="f4a2f-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="f4a2f-132">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="f4a2f-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="f4a2f-133">Teclado</span><span class="sxs-lookup"><span data-stu-id="f4a2f-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="f4a2f-134">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="f4a2f-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="f4a2f-135">Slate</span><span class="sxs-lookup"><span data-stu-id="f4a2f-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="f4a2f-136">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="f4a2f-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="f4a2f-137">Sombreador</span><span class="sxs-lookup"><span data-stu-id="f4a2f-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="f4a2f-138">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="f4a2f-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="f4a2f-139">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="f4a2f-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="f4a2f-140">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="f4a2f-140">Surface magnetism</span></span>](surface-magnetism.md)
