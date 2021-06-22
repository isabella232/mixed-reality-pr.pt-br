---
title: Controle deslizante
description: Visão geral dos controles deslizantes MRTK
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, controles deslizantes,
ms.openlocfilehash: be19806e0202f6cb3ddcea1a80c2c40811aff4f2
ms.sourcegitcommit: e9661d3bab061f9499134226ef3b87751ec56277
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112426872"
---
# <a name="sliders"></a><span data-ttu-id="79cb9-104">Controles deslizantes</span><span class="sxs-lookup"><span data-stu-id="79cb9-104">Sliders</span></span>

![Exemplo de Slider](../images/slider/MRTK_UX_Slider_Main.jpg)

<span data-ttu-id="79cb9-106">Os controles deslizantes são componentes de interface do usuário que permitem que você altere continuamente um valor movendo um controle deslizante em uma faixa. Atualmente, o controle deslizante pinça pode ser movido por meio da captura direta do controle deslizante, seja diretamente ou em uma distância.</span><span class="sxs-lookup"><span data-stu-id="79cb9-106">Sliders are UI components that allow you to continuously change a value by moving a slider on a track. Currently the Pinch Slider can be moved by directly grabbing the slider, either directly or at a distance.</span></span> <span data-ttu-id="79cb9-107">Os controles deslizantes funcionam em AR e VR, usando controladores de movimento, mãos ou gesto + voz.</span><span class="sxs-lookup"><span data-stu-id="79cb9-107">Sliders work on AR and VR, using motion controllers, hands, or Gesture + Voice.</span></span>

## <a name="example-scene"></a><span data-ttu-id="79cb9-108">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="79cb9-108">Example scene</span></span>

<span data-ttu-id="79cb9-109">Você pode encontrar exemplos na cena **SliderExample** em `MRTK/Examples/Demos/UX/Slider/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="79cb9-109">You can find examples in the **SliderExample** scene under `MRTK/Examples/Demos/UX/Slider/Scenes/`.</span></span>

## <a name="how-to-use-sliders"></a><span data-ttu-id="79cb9-110">Como usar controles deslizantes</span><span class="sxs-lookup"><span data-stu-id="79cb9-110">How to use sliders</span></span>

<span data-ttu-id="79cb9-111">Arraste e solte o **PinchSlider** pré-fabricado na hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="79cb9-111">Drag and drop the **PinchSlider** prefab into the scene hierarchy.</span></span> <span data-ttu-id="79cb9-112">Se você quiser modificar ou criar seu próprio controle deslizante, lembre-se de fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="79cb9-112">If you want to modify or create your own slider, remember to do the following:</span></span>

- <span data-ttu-id="79cb9-113">Verifique se o seu objeto Thumb tem um colisor nele.</span><span class="sxs-lookup"><span data-stu-id="79cb9-113">Make sure your that your thumb object has a collider on it.</span></span> <span data-ttu-id="79cb9-114">No PinchSlider pré-fabricado, o colisor está ligado `SliderThumb/Button_AnimationContainer/Slider_Button`</span><span class="sxs-lookup"><span data-stu-id="79cb9-114">In the PinchSlider prefab, the collider is on `SliderThumb/Button_AnimationContainer/Slider_Button`</span></span>
- <span data-ttu-id="79cb9-115">Certifique-se de que o objeto que contém o colisor também tenha um componente que pode ser captado pela interação, se você quiser conseguir obter o controle deslizante próximo.</span><span class="sxs-lookup"><span data-stu-id="79cb9-115">Make sure that the object containing the collider also has a Near Interaction Grabbable component on it, if you want to be able to grab the slider near.</span></span>

<span data-ttu-id="79cb9-116">Também é recomendável usar a seguinte hierarquia</span><span class="sxs-lookup"><span data-stu-id="79cb9-116">We also recommend using the following hierarchy</span></span>

- <span data-ttu-id="79cb9-117">PinchSlider-contém o sliderComponent</span><span class="sxs-lookup"><span data-stu-id="79cb9-117">PinchSlider - Contains the sliderComponent</span></span>
  - <span data-ttu-id="79cb9-118">TouchCollider-colisor que contém a área selecionável inteira do controle deslizante.</span><span class="sxs-lookup"><span data-stu-id="79cb9-118">TouchCollider - Collider containing the entire selectable area of the slider.</span></span> <span data-ttu-id="79cb9-119">Habilita o comportamento de ajustar à posição.</span><span class="sxs-lookup"><span data-stu-id="79cb9-119">Enables the Snap To Position behavior.</span></span>
  - <span data-ttu-id="79cb9-120">SliderThumb-contém o Thumb móvel</span><span class="sxs-lookup"><span data-stu-id="79cb9-120">SliderThumb - Contains the movable thumb</span></span>
  - <span data-ttu-id="79cb9-121">TrackVisuals-contendo a faixa e quaisquer outros visuais</span><span class="sxs-lookup"><span data-stu-id="79cb9-121">TrackVisuals - Containing the track and any other visuals</span></span>
  - <span data-ttu-id="79cb9-122">OtherVisuals-contendo quaisquer outros visuais</span><span class="sxs-lookup"><span data-stu-id="79cb9-122">OtherVisuals - Containing any other visuals</span></span>

## <a name="slider-events"></a><span data-ttu-id="79cb9-123">Eventos Slider</span><span class="sxs-lookup"><span data-stu-id="79cb9-123">Slider events</span></span>

<span data-ttu-id="79cb9-124">Os controles deslizantes expõem os seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="79cb9-124">Sliders expose the following events:</span></span>

- <span data-ttu-id="79cb9-125">OnValueUpdated – chamado sempre que o valor do controle deslizante é alterado</span><span class="sxs-lookup"><span data-stu-id="79cb9-125">OnValueUpdated - Called whenever the slider value changes</span></span>
- <span data-ttu-id="79cb9-126">OnInteractionStarted – chamado quando o usuário captura o controle deslizante</span><span class="sxs-lookup"><span data-stu-id="79cb9-126">OnInteractionStarted - Called when the user grabs the slider</span></span>
- <span data-ttu-id="79cb9-127">OnInteractionEnded – chamado quando o usuário libera o controle deslizante</span><span class="sxs-lookup"><span data-stu-id="79cb9-127">OnInteractionEnded - Called when the user releases the slider</span></span>
- <span data-ttu-id="79cb9-128">OnHoverEntered – chamado quando a mão/controlador do usuário passa o mouse sobre o controle deslizante, usando interação próxima ou extrema.</span><span class="sxs-lookup"><span data-stu-id="79cb9-128">OnHoverEntered - Called when the user's hand / controller hovers over the slider, using either near or far interaction.</span></span>
- <span data-ttu-id="79cb9-129">OnHoverExited – chamado quando a mão/controlador do usuário não está mais próximo do controle deslizante.</span><span class="sxs-lookup"><span data-stu-id="79cb9-129">OnHoverExited - Called when the user's hand / controller is no longer near the slider.</span></span>

## <a name="configuring-slider-bound-and-axis"></a><span data-ttu-id="79cb9-130">Configurando eixo e limite do controle deslizante</span><span class="sxs-lookup"><span data-stu-id="79cb9-130">Configuring slider bound and axis</span></span>

<span data-ttu-id="79cb9-131">Você pode mover diretamente os pontos inicial e final do controle deslizante movendo as alças na cena:</span><span class="sxs-lookup"><span data-stu-id="79cb9-131">You can directly move the starting and end points of the slider by moving the handles in the Scene:</span></span>

![Configuração de controles deslizantes](../images/sliders/MRTK_Sliders_Setup.png)

<span data-ttu-id="79cb9-133">Você também pode especificar o eixo (no espaço local) do controle deslizante por meio do campo _eixo do controle deslizante_</span><span class="sxs-lookup"><span data-stu-id="79cb9-133">You can also specify the axis (in local space) of the slider via the _Slider Axis_ field</span></span>

<span data-ttu-id="79cb9-134">Se você não puder usar as alças, poderá especificar os pontos inicial e final do controle deslizante por meio dos campos distância de _início_ do controle deslizante e _distância de término do controle_ deslizante.</span><span class="sxs-lookup"><span data-stu-id="79cb9-134">If you cannot use the handles, you can instead specify the start and end points of the slider via the _Slider Start Distance_ and _Slider End Distance_ fields.</span></span> <span data-ttu-id="79cb9-135">Elas especificam a posição inicial/final do controle deslizante como uma distância do centro do controle deslizante, em coordenadas locais.</span><span class="sxs-lookup"><span data-stu-id="79cb9-135">These specify start / end position of slider as a distance from the slider's center, in local coordinates.</span></span> <span data-ttu-id="79cb9-136">Isso significa que, depois de definir as distâncias de início e término do controle deslizante conforme desejado, você pode dimensionar o controle deslizante para ser menor ou maior sem a necessidade de atualizar as distâncias de início e término.</span><span class="sxs-lookup"><span data-stu-id="79cb9-136">This means that once you set the slider start and end distances as you want them, you can scale the slider to be smaller or larger without needing to update the start and end distances.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="79cb9-137">Propriedades do Inspetor</span><span class="sxs-lookup"><span data-stu-id="79cb9-137">Inspector properties</span></span>

<span data-ttu-id="79cb9-138">**Raiz do polegar** O gameobject que contém a miniatura do slider.</span><span class="sxs-lookup"><span data-stu-id="79cb9-138">**Thumb Root** The gameobject that contains the slider thumb.</span></span>

<span data-ttu-id="79cb9-139">**Ajustar à posição** Se este controle deslizante se ajusta à posição designada no controle deslizante</span><span class="sxs-lookup"><span data-stu-id="79cb9-139">**Snap To Position** Whether or not this slider snaps to the designated position on the slider</span></span>

<span data-ttu-id="79cb9-140">**É tocável** Se esse controle deslizante é controlável por meio de eventos de toque</span><span class="sxs-lookup"><span data-stu-id="79cb9-140">**Is Touchable** Whether or not this slider is controllable via touch events</span></span>

<span data-ttu-id="79cb9-141">**Colisor de polegar** O colisor que controla o controle deslizante Thumb</span><span class="sxs-lookup"><span data-stu-id="79cb9-141">**Thumb Collider** The collider that controls the slider thumb</span></span>

<span data-ttu-id="79cb9-142">**Colisor tocável** A área do controle deslizante que pode ser tocada ou selecionado quando ajustar à posição for verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="79cb9-142">**Touchable Collider** The area of the slider that can be touched or selected when Snap To Position is true.</span></span>

<span data-ttu-id="79cb9-143">**Valor do controle deslizante** O valor do controle deslizante.</span><span class="sxs-lookup"><span data-stu-id="79cb9-143">**Slider Value** The value of the slider.</span></span>

<span data-ttu-id="79cb9-144">**Usar divisões de etapa do controle deslizante** Controla se esse controle deslizante é incrementado em etapas ou continuamente.</span><span class="sxs-lookup"><span data-stu-id="79cb9-144">**Use Slider Step Divisions** Controls whether this slider is increments in steps or continuously.</span></span>

<span data-ttu-id="79cb9-145">**Divisões da etapa do controle deslizante** Número de subdivisãos em que o controle deslizante é dividido quando o uso de divisões de etapa de controle deslizante está habilitado.</span><span class="sxs-lookup"><span data-stu-id="79cb9-145">**Slider Step Divisions** Number of subdivisions the slider is split into when Use Slider Step Divisions is enabled.</span></span>

<span data-ttu-id="79cb9-146">**Acompanhar visuais** O gameobject que contém os visuais de faixa desejados que acompanham o controle deslizante.</span><span class="sxs-lookup"><span data-stu-id="79cb9-146">**Track Visuals** The gameobject that contains the desired track visuals that goes along the slider.</span></span>

<span data-ttu-id="79cb9-147">**Marcas de escala** O gameobject que contém as marcas de escala desejadas que vão ao longo do controle deslizante.</span><span class="sxs-lookup"><span data-stu-id="79cb9-147">**Tick Marks** The gameobject that contains the desired tick marks that goes along the slider.</span></span>

<span data-ttu-id="79cb9-148">**Visuais Thumb** O gameobject que contém o Visual de miniatura desejado que acompanha o controle deslizante.</span><span class="sxs-lookup"><span data-stu-id="79cb9-148">**Thumb Visuals** The gameobject that contains the desired thumb visual that goes along the slider.</span></span>

<span data-ttu-id="79cb9-149">**Eixo do controle deslizante** O eixo no qual o controle deslizante se move.</span><span class="sxs-lookup"><span data-stu-id="79cb9-149">**Slider Axis** The axis the slider moves along.</span></span>

<span data-ttu-id="79cb9-150">**Distância de início do controle deslizante** Em que a faixa do controle deslizante começa, como distância do centro do slider ao longo do eixo, em unidades de espaço local.</span><span class="sxs-lookup"><span data-stu-id="79cb9-150">**Slider Start Distance** Where the slider track starts, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="79cb9-151">**Distância de extremidade do controle deslizante** Em que a faixa do controle deslizante termina, como distância do centro do controle deslizante, em unidades de espaço local.</span><span class="sxs-lookup"><span data-stu-id="79cb9-151">**Slider End Distance** Where the slider track ends, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="79cb9-152">Quando o usuário atualizar o valor do eixo do controle deslizante no editor, então, se rastrear visuais ou visuais de tique forem especificados, a transformação será atualizada.</span><span class="sxs-lookup"><span data-stu-id="79cb9-152">When user updates the slider axis value in editor then if Track Visuals or Tick Visuals are specified then their transform is updated.</span></span>
<span data-ttu-id="79cb9-153">Especificamente, sua posição local é redefinida e sua rotação local é definida para corresponder à orientação do eixo do controle deslizante.</span><span class="sxs-lookup"><span data-stu-id="79cb9-153">Specifically, their local position is reset and their local rotation is set to match the Slider Axis orientation.</span></span>
<span data-ttu-id="79cb9-154">Sua escala não é modificada.</span><span class="sxs-lookup"><span data-stu-id="79cb9-154">Their scale isn't modified.</span></span>
<span data-ttu-id="79cb9-155">Se as marcas de escala tiverem um componente de coleção de objetos de grade, o layout e o CellWidth ou CellHeight serão atualizados adequadamente para corresponder ao eixo do controle deslizante.</span><span class="sxs-lookup"><span data-stu-id="79cb9-155">If Tick Marks have a Grid Object Collection component then the Layout and CellWidth or CellHeight is updated accordingly to match the Slider Axis.</span></span>

## <a name="example-slider-configurations"></a><span data-ttu-id="79cb9-156">Configurações de controle deslizante de exemplo</span><span class="sxs-lookup"><span data-stu-id="79cb9-156">Example Slider Configurations</span></span>

<span data-ttu-id="79cb9-157">Controles deslizantes contínuos com snap para posicionar ![ controles deslizantes contínuos](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span><span class="sxs-lookup"><span data-stu-id="79cb9-157">Continuous Sliders with Snap To Position ![Continuous Sliders](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span></span>

<span data-ttu-id="79cb9-158">Deslizantes de etapa com ajustar à posição</span><span class="sxs-lookup"><span data-stu-id="79cb9-158">Step Sliders with Snap To Position</span></span>

![Deslizantes de etapa](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

<span data-ttu-id="79cb9-160">Controles deslizantes de toque</span><span class="sxs-lookup"><span data-stu-id="79cb9-160">Touch Sliders</span></span>

![Controles deslizantes de toque](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)