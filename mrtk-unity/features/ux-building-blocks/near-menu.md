---
title: Menu próximo
description: Visão geral ao lado de tipos de menu no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Menu próximo,
ms.openlocfilehash: 15f53ad4e67a0b281750fd1df7f894c49f546531
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175652"
---
# <a name="near-menu"></a><span data-ttu-id="f96e8-104">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="f96e8-104">Near menu</span></span>

![Menu próximo](../images/near-menu/MRTK_UX_NearMenu.png)

<span data-ttu-id="f96e8-106">O menu Near é um controle UX que fornece uma coleção de botões ou outros componentes de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="f96e8-106">Near Menu is a UX control which provides a collection of buttons or other UI components.</span></span> <span data-ttu-id="f96e8-107">Ele está flutuando pelo corpo do usuário e facilmente acessível a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="f96e8-107">It is floating around the user's body and easily accessible anytime.</span></span> <span data-ttu-id="f96e8-108">Como ele está acoplado livremente ao usuário, ele não perturba a interação do usuário com o conteúdo de destino.</span><span class="sxs-lookup"><span data-stu-id="f96e8-108">Since it is loosely coupled with the user, it does not disturb the user's interaction with the target content.</span></span> <span data-ttu-id="f96e8-109">O usuário pode usar o botão ' fixar ' para bloquear/desbloquear o menu do mundo.</span><span class="sxs-lookup"><span data-stu-id="f96e8-109">The user can use the 'Pin' button to world-lock/unlock the menu.</span></span> <span data-ttu-id="f96e8-110">O menu pode ser capturado e colocado em uma posição específica.</span><span class="sxs-lookup"><span data-stu-id="f96e8-110">The menu can be grabbed and placed at a specific position.</span></span>

## <a name="interaction-behavior"></a><span data-ttu-id="f96e8-111">Comportamento de interação</span><span class="sxs-lookup"><span data-stu-id="f96e8-111">Interaction behavior</span></span>

- <span data-ttu-id="f96e8-112">**Marcação**: o menu segue você e permanece dentro do intervalo de 30 60cm do usuário para as interações próximas.</span><span class="sxs-lookup"><span data-stu-id="f96e8-112">**Tag-along**: The menu follows you and stays within 30-60cm range from the user for the near interactions.</span></span>
- <span data-ttu-id="f96e8-113">**PIN**: usando o botão ' fixar ', o menu pode ser bloqueado e liberado pelo mundo.</span><span class="sxs-lookup"><span data-stu-id="f96e8-113">**Pin**: Using the 'Pin' button, the menu can be world-locked and released.</span></span>
- <span data-ttu-id="f96e8-114">**Pegar e mover**: o menu é sempre captado e móvel.</span><span class="sxs-lookup"><span data-stu-id="f96e8-114">**Grab and move**: The menu is always grabbable and movable.</span></span> <span data-ttu-id="f96e8-115">Independentemente do estado anterior, o menu será fixado (bloqueado pelo mundo) quando capturado e liberado.</span><span class="sxs-lookup"><span data-stu-id="f96e8-115">Regardless of the previous state, the menu will be pinned(world-locked) when grabbed and released.</span></span> <span data-ttu-id="f96e8-116">Há indicações visuais para a área de captura.</span><span class="sxs-lookup"><span data-stu-id="f96e8-116">There are visual cues for the grabbable area.</span></span> <span data-ttu-id="f96e8-117">Eles são revelados à proximidade.</span><span class="sxs-lookup"><span data-stu-id="f96e8-117">They are revealed on hand proximity.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a><span data-ttu-id="f96e8-118">Pré-fabricados</span><span class="sxs-lookup"><span data-stu-id="f96e8-118">Prefabs</span></span>

<span data-ttu-id="f96e8-119">O menu Near pré-fabricados foi projetado para demonstrar como usar os vários componentes do MRTK para criar menus para interações próximas.</span><span class="sxs-lookup"><span data-stu-id="f96e8-119">Near Menu prefabs are designed to demonstrate how to use MRTK's various components to build menus for near interactions.</span></span>

- <span data-ttu-id="f96e8-120">**NearMenu2x4. pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="f96e8-120">**NearMenu2x4.prefab**</span></span>
- <span data-ttu-id="f96e8-121">**NearMenu3x1. pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="f96e8-121">**NearMenu3x1.prefab**</span></span>
- <span data-ttu-id="f96e8-122">**NearMenu3x2. pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="f96e8-122">**NearMenu3x2.prefab**</span></span>
- <span data-ttu-id="f96e8-123">**NearMenu3x3. pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="f96e8-123">**NearMenu3x3.prefab**</span></span>
- <span data-ttu-id="f96e8-124">**NearMenu4x1. pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="f96e8-124">**NearMenu4x1.prefab**</span></span>
- <span data-ttu-id="f96e8-125">**NearMenu4x2. pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="f96e8-125">**NearMenu4x2.prefab**</span></span>

## <a name="example-scene"></a><span data-ttu-id="f96e8-126">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="f96e8-126">Example scene</span></span>

<span data-ttu-id="f96e8-127">Você pode encontrar exemplos de pré-fabricados de menu próximo na `NearMenuExamples` cena.</span><span class="sxs-lookup"><span data-stu-id="f96e8-127">You can find examples of Near Menu prefabs in the `NearMenuExamples` scene.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a><span data-ttu-id="f96e8-128">Estrutura</span><span class="sxs-lookup"><span data-stu-id="f96e8-128">Structure</span></span>

<span data-ttu-id="f96e8-129">O menu Near pré-fabricados é feito com os seguintes componentes do MRTK.</span><span class="sxs-lookup"><span data-stu-id="f96e8-129">Near Menu prefabs are made with following MRTK components.</span></span>

- <span data-ttu-id="f96e8-130">[**PressableButtonHoloLens2**](button.md) pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="f96e8-130">[**PressableButtonHoloLens2**](button.md) prefab</span></span>
- <span data-ttu-id="f96e8-131">[**Coleção de objetos de grade**](object-collection.md): layout de vários botões na grade</span><span class="sxs-lookup"><span data-stu-id="f96e8-131">[**Grid Object Collection**](object-collection.md): Multiple button layout in grid</span></span>
- <span data-ttu-id="f96e8-132">[**Manipulador de manipulação**](manipulation-handler.md): Pegue e mova o menu</span><span class="sxs-lookup"><span data-stu-id="f96e8-132">[**Manipulation Handler**](manipulation-handler.md): Grab and move the menu</span></span>
- <span data-ttu-id="f96e8-133">[**RadialView Solver**](solvers/solver.md): Siga o comportamento (marcação)</span><span class="sxs-lookup"><span data-stu-id="f96e8-133">[**RadialView Solver**](solvers/solver.md): Follow Me(tag-along) behavior</span></span>

![Menu Near pré-fabricado](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a><span data-ttu-id="f96e8-135">Como personalizar</span><span class="sxs-lookup"><span data-stu-id="f96e8-135">How to customize</span></span>

<span data-ttu-id="f96e8-136">**1. Adicionar/remover botões**</span><span class="sxs-lookup"><span data-stu-id="f96e8-136">**1. Add/Remove Buttons**</span></span>

<span data-ttu-id="f96e8-137">Em `ButtonCollection` objeto, adicione ou remova botões.</span><span class="sxs-lookup"><span data-stu-id="f96e8-137">Under `ButtonCollection` object, add or remove buttons.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

<span data-ttu-id="f96e8-138">**2. atualizar a coleção de objetos de grade**</span><span class="sxs-lookup"><span data-stu-id="f96e8-138">**2. Update the Grid Object Collection**</span></span>

<span data-ttu-id="f96e8-139">Clique `Update Collection` no botão no Inspetor do `ButtonCollection` objeto.</span><span class="sxs-lookup"><span data-stu-id="f96e8-139">Click `Update Collection` button in the Inspector of the `ButtonCollection` object.</span></span> <span data-ttu-id="f96e8-140">O layout da grade será atualizado.</span><span class="sxs-lookup"><span data-stu-id="f96e8-140">It will update the grid layout.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

<span data-ttu-id="f96e8-141">Você pode configurar o número de linhas usando `Rows` a propriedade da coleção de objetos de grade.</span><span class="sxs-lookup"><span data-stu-id="f96e8-141">You can configure the number of rows using `Rows` property of the Grid Object Collection.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

<span data-ttu-id="f96e8-142">**3. ajustar o tamanho da placa de cima**</span><span class="sxs-lookup"><span data-stu-id="f96e8-142">**3. Adjust the backplate size**</span></span>

<span data-ttu-id="f96e8-143">Ajuste o tamanho do `Quad` objeto em `Backplate` .</span><span class="sxs-lookup"><span data-stu-id="f96e8-143">Adjust the size of the `Quad` under `Backplate` object.</span></span> <span data-ttu-id="f96e8-144">A largura e a altura da chapa de backdevem ser `0.032 * [Number of the buttons + 1]` .</span><span class="sxs-lookup"><span data-stu-id="f96e8-144">The width and height of the backplate should be `0.032 * [Number of the buttons + 1]`.</span></span> <span data-ttu-id="f96e8-145">Por exemplo, se você tiver três botões x 2, a largura da chapa de backfica `0.032 * 4` e a altura será `0.032 * 3` .</span><span class="sxs-lookup"><span data-stu-id="f96e8-145">For example, if you have 3 x 2 buttons, the width of the backplate is `0.032 * 4` and the height is `0.032 * 3`.</span></span> <span data-ttu-id="f96e8-146">Você pode colocar essa expressão diretamente no campo do Unity.</span><span class="sxs-lookup"><span data-stu-id="f96e8-146">You can directly put this expression into the Unity's field.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- <span data-ttu-id="f96e8-147">o tamanho padrão do botão HoloLens 2 é 3,2 x 3.2 cm (0.032 m)</span><span class="sxs-lookup"><span data-stu-id="f96e8-147">Default size of the HoloLens 2 button is 3.2x3.2 cm (0.032m)</span></span>

## <a name="see-also"></a><span data-ttu-id="f96e8-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="f96e8-148">See also</span></span>

- [<span data-ttu-id="f96e8-149">**Botões**</span><span class="sxs-lookup"><span data-stu-id="f96e8-149">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="f96e8-150">**Controle de limites**</span><span class="sxs-lookup"><span data-stu-id="f96e8-150">**Bounds Control**</span></span>](bounds-control.md)
- [<span data-ttu-id="f96e8-151">**Controle deslizante**</span><span class="sxs-lookup"><span data-stu-id="f96e8-151">**Slider**</span></span>](sliders.md)
- [<span data-ttu-id="f96e8-152">**Coleção de objetos de grade**</span><span class="sxs-lookup"><span data-stu-id="f96e8-152">**Grid Object Collection**</span></span>](object-collection.md)
- [<span data-ttu-id="f96e8-153">**Manipulador de manipulação**</span><span class="sxs-lookup"><span data-stu-id="f96e8-153">**Manipulation Handler**</span></span>](manipulation-handler.md)
- [<span data-ttu-id="f96e8-154">**Solucionador de RadialView**</span><span class="sxs-lookup"><span data-stu-id="f96e8-154">**RadialView Solver**</span></span>](solvers/solver.md)
