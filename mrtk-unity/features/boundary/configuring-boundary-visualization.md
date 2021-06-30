---
title: Configurando a visualização de limite
description: Detalhes para configurar o sistema de limites no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Sistema de Limites,
ms.openlocfilehash: 0f1a9edd9f9a31e7ba20f630406b299909a4864c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121244"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="df02c-104">Configurando a visualização de limite</span><span class="sxs-lookup"><span data-stu-id="df02c-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="df02c-105">O *Perfil de Visualização de* Limite fornece opções para configurar a linguagem visual e outros parâmetros relacionados para o sistema de limites.</span><span class="sxs-lookup"><span data-stu-id="df02c-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="df02c-106">As visualizações de limite são anexadas ao objeto do Playspace de Realidade Misturada na cena e são conectadas ao usuário.</span><span class="sxs-lookup"><span data-stu-id="df02c-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="df02c-107">Configurações gerais</span><span class="sxs-lookup"><span data-stu-id="df02c-107">General settings</span></span>

![Configurações gerais de visualização de limite](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="df02c-109">Altura do limite</span><span class="sxs-lookup"><span data-stu-id="df02c-109">Boundary height</span></span>

<span data-ttu-id="df02c-110">A altura do limite indica a distância acima do plano de piso no qual o limite deve ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="df02c-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="df02c-111">O valor padrão é 3 metros.</span><span class="sxs-lookup"><span data-stu-id="df02c-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="df02c-112">Configurações de piso</span><span class="sxs-lookup"><span data-stu-id="df02c-112">Floor settings</span></span>

![Configurações de piso de visualização de limite](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="df02c-114">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="df02c-114">**Show**</span></span>

<span data-ttu-id="df02c-115">Indica se um plano de piso deve ou não ser criado e adicionado à cena.</span><span class="sxs-lookup"><span data-stu-id="df02c-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="df02c-116">O valor padrão é true.</span><span class="sxs-lookup"><span data-stu-id="df02c-116">The default value is true.</span></span>

<span data-ttu-id="df02c-117">**Material**</span><span class="sxs-lookup"><span data-stu-id="df02c-117">**Material**</span></span>

<span data-ttu-id="df02c-118">Indica o material que deve ser usado ao criar o plano de piso.</span><span class="sxs-lookup"><span data-stu-id="df02c-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="df02c-119">**Escala**</span><span class="sxs-lookup"><span data-stu-id="df02c-119">**Scale**</span></span>

<span data-ttu-id="df02c-120">Indica o tamanho, em metros, do plano de piso a ser criado.</span><span class="sxs-lookup"><span data-stu-id="df02c-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="df02c-121">A escala padrão é um quadrado de 3 metros x 3 metros.</span><span class="sxs-lookup"><span data-stu-id="df02c-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="df02c-122">**Camada física**</span><span class="sxs-lookup"><span data-stu-id="df02c-122">**Physics Layer**</span></span>

<span data-ttu-id="df02c-123">A camada na qual o plano de piso deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="df02c-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="df02c-124">O valor padrão é a *camada* Padrão.</span><span class="sxs-lookup"><span data-stu-id="df02c-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="df02c-125">Configurações da área de reprodução</span><span class="sxs-lookup"><span data-stu-id="df02c-125">Play area settings</span></span>

![Configurações de área de reprodução de visualização de limite](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="df02c-127">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="df02c-127">**Show**</span></span>

<span data-ttu-id="df02c-128">Indica se um retângulo de área de reprodução é criado e adicionado à cena.</span><span class="sxs-lookup"><span data-stu-id="df02c-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="df02c-129">O valor padrão é true.</span><span class="sxs-lookup"><span data-stu-id="df02c-129">The default value is true.</span></span>

<span data-ttu-id="df02c-130">**Material**</span><span class="sxs-lookup"><span data-stu-id="df02c-130">**Material**</span></span>

<span data-ttu-id="df02c-131">Indica o material que deve ser usado ao criar o objeto de área de reprodução.</span><span class="sxs-lookup"><span data-stu-id="df02c-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="df02c-132">**Camada física**</span><span class="sxs-lookup"><span data-stu-id="df02c-132">**Physics Layer**</span></span>

<span data-ttu-id="df02c-133">A camada na qual a área de reprodução deve ser definida.</span><span class="sxs-lookup"><span data-stu-id="df02c-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="df02c-134">O valor padrão é a *camada Ignorar Raycast.*</span><span class="sxs-lookup"><span data-stu-id="df02c-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="df02c-135">Configurações de área rastreada</span><span class="sxs-lookup"><span data-stu-id="df02c-135">Tracked area settings</span></span>

![Configurações de área rastreada de visualização de limite](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="df02c-137">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="df02c-137">**Show**</span></span>

<span data-ttu-id="df02c-138">Indica se o contorno da área rastreada é criado ou não e adicionado à cena.</span><span class="sxs-lookup"><span data-stu-id="df02c-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="df02c-139">O valor padrão é true.</span><span class="sxs-lookup"><span data-stu-id="df02c-139">The default value is true.</span></span>

<span data-ttu-id="df02c-140">**Material**</span><span class="sxs-lookup"><span data-stu-id="df02c-140">**Material**</span></span>

<span data-ttu-id="df02c-141">Indica o material que deve ser usado ao criar o contorno da área rastreada.</span><span class="sxs-lookup"><span data-stu-id="df02c-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="df02c-142">**Camada física**</span><span class="sxs-lookup"><span data-stu-id="df02c-142">**Physics Layer**</span></span>

<span data-ttu-id="df02c-143">A camada na qual a área rastreada deve ser configurada.</span><span class="sxs-lookup"><span data-stu-id="df02c-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="df02c-144">O valor padrão é a *camada Ignorar Raycast.*</span><span class="sxs-lookup"><span data-stu-id="df02c-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="df02c-145">Configurações de parede de limite</span><span class="sxs-lookup"><span data-stu-id="df02c-145">Boundary wall settings</span></span>

![Configurações de parede de limite de visualização de limite](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="df02c-147">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="df02c-147">**Show**</span></span>

<span data-ttu-id="df02c-148">Indica se planos de parede de limite devem ou não ser criados e adicionados à cena.</span><span class="sxs-lookup"><span data-stu-id="df02c-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="df02c-149">O valor padrão é false.</span><span class="sxs-lookup"><span data-stu-id="df02c-149">The default value is false.</span></span>

<span data-ttu-id="df02c-150">**Material**</span><span class="sxs-lookup"><span data-stu-id="df02c-150">**Material**</span></span>

<span data-ttu-id="df02c-151">Indica o material que deve ser usado ao criar os planos de parede de limite.</span><span class="sxs-lookup"><span data-stu-id="df02c-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="df02c-152">**Camada física**</span><span class="sxs-lookup"><span data-stu-id="df02c-152">**Physics Layer**</span></span>

<span data-ttu-id="df02c-153">A camada na qual as paredes de limite devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="df02c-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="df02c-154">O valor padrão é a *camada Ignorar Raycast.*</span><span class="sxs-lookup"><span data-stu-id="df02c-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="df02c-155">Definir o componente de parede de limite como uma camada física diferente de *Ignorar Raycast* pode impedir que os usuários interajam com objetos dentro da cena.</span><span class="sxs-lookup"><span data-stu-id="df02c-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="df02c-156">Configurações de limite de limite</span><span class="sxs-lookup"><span data-stu-id="df02c-156">Boundary ceiling settings</span></span>

![Configurações de limite de limite de visualização de limite](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="df02c-158">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="df02c-158">**Show**</span></span>

<span data-ttu-id="df02c-159">Indica se um plano de limite deve ou não ser criado e adicionado à cena.</span><span class="sxs-lookup"><span data-stu-id="df02c-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="df02c-160">O valor padrão é false.</span><span class="sxs-lookup"><span data-stu-id="df02c-160">The default value is false.</span></span>

<span data-ttu-id="df02c-161">**Material**</span><span class="sxs-lookup"><span data-stu-id="df02c-161">**Material**</span></span>

<span data-ttu-id="df02c-162">Indica o material que deve ser usado ao criar o plano de limite de limite.</span><span class="sxs-lookup"><span data-stu-id="df02c-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="df02c-163">**Camada física**</span><span class="sxs-lookup"><span data-stu-id="df02c-163">**Physics Layer**</span></span>

<span data-ttu-id="df02c-164">A camada na qual as paredes de limite devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="df02c-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="df02c-165">O valor padrão é a *camada Ignorar Raycast.*</span><span class="sxs-lookup"><span data-stu-id="df02c-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="df02c-166">Definir o componente de limite de limite para uma camada física diferente de *Ignorar Raycast* pode impedir que os usuários interajam com objetos dentro da cena.</span><span class="sxs-lookup"><span data-stu-id="df02c-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="df02c-167">Confira também</span><span class="sxs-lookup"><span data-stu-id="df02c-167">See also</span></span>

- [<span data-ttu-id="df02c-168">Documentação da API de limite</span><span class="sxs-lookup"><span data-stu-id="df02c-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="df02c-169">Sistema de limite</span><span class="sxs-lookup"><span data-stu-id="df02c-169">Boundary System</span></span>](boundary-system-getting-started.md)
