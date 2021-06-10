---
title: Pesquisa
description: Interação de duração
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Pesquisa, Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647737"
---
# <a name="dwell"></a><span data-ttu-id="02ecb-104">Pesquisa</span><span class="sxs-lookup"><span data-stu-id="02ecb-104">Dwell</span></span>

![Herói de pesquisa](../images/dwell/MRTK_UX_Dwell.png)

<span data-ttu-id="02ecb-106">O Head-olhar e a pesquisa são ótimos em cenários nos quais as mãos de uma pessoa estão ocupadas com outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="02ecb-106">Head-gaze and dwell are great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="02ecb-107">O recurso também é útil quando a voz não é 100% confiável ou está disponível devido a restrições de ambiente ou sociais.</span><span class="sxs-lookup"><span data-stu-id="02ecb-107">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="02ecb-108">Os exemplos de pesquisa de MRTK demonstram tipos diferentes de componentes de interface do usuário com tempo de resposta configurável e comentários visuais.</span><span class="sxs-lookup"><span data-stu-id="02ecb-108">MRTK's dwell examples demonstrate different types of UI components with configurable response time and visual feedback.</span></span>

<span data-ttu-id="02ecb-109">Consulte a página de [diretrizes Head-olhar e de duração](/windows/mixed-reality/design/gaze-and-dwell-head) para obter as recomendações de design.</span><span class="sxs-lookup"><span data-stu-id="02ecb-109">Please see [Head-gaze and dwell guideline](/windows/mixed-reality/design/gaze-and-dwell-head) page for the design recommendations.</span></span>

## <a name="dwell-scripts"></a><span data-ttu-id="02ecb-110">Scripts de duração</span><span class="sxs-lookup"><span data-stu-id="02ecb-110">Dwell scripts</span></span>

- <span data-ttu-id="02ecb-111">**DwellHandler**: adiciona uma modalidade de pesquisa ao destino da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="02ecb-111">**DwellHandler**: Adds a dwell modality to the UI target.</span></span>
- <span data-ttu-id="02ecb-112">**DwellStateType**: os Estados do manipulador de duração.</span><span class="sxs-lookup"><span data-stu-id="02ecb-112">**DwellStateType**: The states of the dwell handler.</span></span>
- <span data-ttu-id="02ecb-113">Evento **DwellUnityEvent**: Unity para um evento de duração de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="02ecb-113">**DwellUnityEvent**: Unity event for a dwell event.</span></span> <span data-ttu-id="02ecb-114">Contém a referência do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="02ecb-114">Contains the pointer reference.</span></span>
- <span data-ttu-id="02ecb-115">**BaseDwellPressableButton. cs** : um script que dispara o evento OnClick () em `Interactable` PressableButtonHoloLens2 pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="02ecb-115">**BaseDwellPressableButton.cs** : A script that triggers OnClick() event in `Interactable` of PressableButtonHoloLens2 prefabs.</span></span>
- <span data-ttu-id="02ecb-116">**ToggleDwellPressableButton. cs** : esse script modifica `_BorderWidth` a propriedade do `dwellVisualImage` que está usando o sombreador padrão do MRTK.</span><span class="sxs-lookup"><span data-stu-id="02ecb-116">**ToggleDwellPressableButton.cs** : This script modifies `_BorderWidth` property of the `dwellVisualImage` which is using MRTK Standard Shader.</span></span>

## <a name="dwell-profiles"></a><span data-ttu-id="02ecb-117">Perfis de duração</span><span class="sxs-lookup"><span data-stu-id="02ecb-117">Dwell profiles</span></span>
<span data-ttu-id="02ecb-118">Os perfis de duração são usados pelo **manipulador de duração** para configurar os vários limites.</span><span class="sxs-lookup"><span data-stu-id="02ecb-118">Dwell profiles are used by the **Dwell Handler** to configure the various thresholds.</span></span>
- <span data-ttu-id="02ecb-119">**ButtonDwellProfile. Asset**</span><span class="sxs-lookup"><span data-stu-id="02ecb-119">**ButtonDwellProfile.asset**</span></span>
- <span data-ttu-id="02ecb-120">**InstandDwellProfile. Asset**</span><span class="sxs-lookup"><span data-stu-id="02ecb-120">**InstandDwellProfile.asset**</span></span>
- <span data-ttu-id="02ecb-121">**DwellProfileWithDecay. Asset**</span><span class="sxs-lookup"><span data-stu-id="02ecb-121">**DwellProfileWithDecay.asset**</span></span>

## <a name="prefabs"></a><span data-ttu-id="02ecb-122">Pré-fabricados</span><span class="sxs-lookup"><span data-stu-id="02ecb-122">Prefabs</span></span>

<span data-ttu-id="02ecb-123">Esses pré-fabricados são variantes do pré-fabricados de botão pressionável de estilo do HoloLens 2 que têm componentes adicionais para dar suporte a interações de duração de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="02ecb-123">These prefabs are variants of the HoloLens 2 style pressable button prefabs that have additional components to support dwell interactions.</span></span>

- <span data-ttu-id="02ecb-124">**PressableButtonHoloLens2_Dwell. pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="02ecb-124">**PressableButtonHoloLens2_Dwell.prefab**</span></span>
- <span data-ttu-id="02ecb-125">**PressableButtonHoloLens2_32x96_Dwell. pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="02ecb-125">**PressableButtonHoloLens2_32x96_Dwell.prefab**</span></span>
- <span data-ttu-id="02ecb-126">**PressableButtonHoloLens2ToggleDwell. pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="02ecb-126">**PressableButtonHoloLens2ToggleDwell.prefab**</span></span>
- <span data-ttu-id="02ecb-127">**PressableButtonHoloLens2Toggle_32x96_Dwell. pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="02ecb-127">**PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**</span></span>

<span data-ttu-id="02ecb-128">Esses pré-fabricados têm um componente de placa traseira adicional **QuadDwellVisual** para visualizar o estado de entrada de duração.</span><span class="sxs-lookup"><span data-stu-id="02ecb-128">These prefabs have an additional backplate component **QuadDwellVisual** to visualize the dwell input state.</span></span> <span data-ttu-id="02ecb-129">Ele tem o material **HolographicBackPlateDwellVisual. enquadrable** atribuído.</span><span class="sxs-lookup"><span data-stu-id="02ecb-129">It has **HolographicBackPlateDwellVisual.mat** material assigned.</span></span> <span data-ttu-id="02ecb-130">**ToggleDwellPressableButton. cs** atualiza a propriedade **_BorderWidth** do sombreador padrão MRTK para visualizar a entrada de duração da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="02ecb-130">**ToggleDwellPressableButton.cs** updates the **_BorderWidth** property of MRTK Standard shader to visualize the dwell input.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a><span data-ttu-id="02ecb-131">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="02ecb-131">Example scene</span></span>

<span data-ttu-id="02ecb-132">Você pode encontrar exemplos na `DwellExample` cena.</span><span class="sxs-lookup"><span data-stu-id="02ecb-132">You can find examples in the `DwellExample` scene.</span></span> <span data-ttu-id="02ecb-133">A cena de exemplo mostra os exemplos de interface do usuário do volumétricos e exemplos da interface do usuário do Unity</span><span class="sxs-lookup"><span data-stu-id="02ecb-133">The example scene shows both volumetric UI examples and Unity UI examples.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a><span data-ttu-id="02ecb-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="02ecb-134">See also</span></span>

- [<span data-ttu-id="02ecb-135">**Botões**</span><span class="sxs-lookup"><span data-stu-id="02ecb-135">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="02ecb-136">**Interativo**</span><span class="sxs-lookup"><span data-stu-id="02ecb-136">**Interactable**</span></span>](interactable.md)
