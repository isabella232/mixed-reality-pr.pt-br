---
title: Configurar a visualização de limite
description: Detalhes para configurar o sistema de limites no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Sistema de Limites,
ms.openlocfilehash: 36717493107b129a7200dd3f912bcbdc3337b9a1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144496"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="8b626-104">Configurando a visualização de limite</span><span class="sxs-lookup"><span data-stu-id="8b626-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="8b626-105">O *Perfil de Visualização de* Limite fornece opções para configurar a linguagem visual e outros parâmetros relacionados para o sistema de limites.</span><span class="sxs-lookup"><span data-stu-id="8b626-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="8b626-106">As visualizações de limite são anexadas ao objeto do Playspace de Realidade Misturada na cena e são conectadas ao usuário.</span><span class="sxs-lookup"><span data-stu-id="8b626-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="8b626-107">Configurações gerais</span><span class="sxs-lookup"><span data-stu-id="8b626-107">General settings</span></span>

![Configurações gerais de visualização de limite](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="8b626-109">Altura do limite</span><span class="sxs-lookup"><span data-stu-id="8b626-109">Boundary height</span></span>

<span data-ttu-id="8b626-110">A altura do limite indica a distância acima do plano de piso no qual o limite deve ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="8b626-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="8b626-111">O valor padrão é 3 metros.</span><span class="sxs-lookup"><span data-stu-id="8b626-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="8b626-112">Configurações de piso</span><span class="sxs-lookup"><span data-stu-id="8b626-112">Floor settings</span></span>

![Configurações de piso de visualização de limite](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="8b626-114">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="8b626-114">**Show**</span></span>

<span data-ttu-id="8b626-115">Indica se um plano de piso deve ou não ser criado e adicionado à cena.</span><span class="sxs-lookup"><span data-stu-id="8b626-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="8b626-116">O valor padrão é true.</span><span class="sxs-lookup"><span data-stu-id="8b626-116">The default value is true.</span></span>

<span data-ttu-id="8b626-117">**Material**</span><span class="sxs-lookup"><span data-stu-id="8b626-117">**Material**</span></span>

<span data-ttu-id="8b626-118">Indica o material que deve ser usado ao criar o plano de piso.</span><span class="sxs-lookup"><span data-stu-id="8b626-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="8b626-119">**Escala**</span><span class="sxs-lookup"><span data-stu-id="8b626-119">**Scale**</span></span>

<span data-ttu-id="8b626-120">Indica o tamanho, em metros, do plano de piso a ser criado.</span><span class="sxs-lookup"><span data-stu-id="8b626-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="8b626-121">A escala padrão é um quadrado de 3 metros x 3 metros.</span><span class="sxs-lookup"><span data-stu-id="8b626-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="8b626-122">**Camada física**</span><span class="sxs-lookup"><span data-stu-id="8b626-122">**Physics Layer**</span></span>

<span data-ttu-id="8b626-123">A camada na qual o plano de piso deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="8b626-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="8b626-124">O valor padrão é a *camada* Padrão.</span><span class="sxs-lookup"><span data-stu-id="8b626-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="8b626-125">Configurações da área de reprodução</span><span class="sxs-lookup"><span data-stu-id="8b626-125">Play area settings</span></span>

![Configurações de área de reprodução de visualização de limite](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="8b626-127">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="8b626-127">**Show**</span></span>

<span data-ttu-id="8b626-128">Indica se um retângulo de área de reprodução é ou não criado e adicionado à cena.</span><span class="sxs-lookup"><span data-stu-id="8b626-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="8b626-129">O valor padrão é true.</span><span class="sxs-lookup"><span data-stu-id="8b626-129">The default value is true.</span></span>

<span data-ttu-id="8b626-130">**Material**</span><span class="sxs-lookup"><span data-stu-id="8b626-130">**Material**</span></span>

<span data-ttu-id="8b626-131">Indica o material que deve ser usado ao criar o objeto da área de reprodução.</span><span class="sxs-lookup"><span data-stu-id="8b626-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="8b626-132">**Camada física**</span><span class="sxs-lookup"><span data-stu-id="8b626-132">**Physics Layer**</span></span>

<span data-ttu-id="8b626-133">A camada na qual a área de reprodução deve ser definida.</span><span class="sxs-lookup"><span data-stu-id="8b626-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="8b626-134">O valor padrão é a camada *ignorar Raycast* .</span><span class="sxs-lookup"><span data-stu-id="8b626-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="8b626-135">Configurações da área rastreada</span><span class="sxs-lookup"><span data-stu-id="8b626-135">Tracked area settings</span></span>

![Configurações de área rastreada de visualização de limite](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="8b626-137">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="8b626-137">**Show**</span></span>

<span data-ttu-id="8b626-138">Indica se o contorno da área rastreada é criado e adicionado à cena.</span><span class="sxs-lookup"><span data-stu-id="8b626-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="8b626-139">O valor padrão é true.</span><span class="sxs-lookup"><span data-stu-id="8b626-139">The default value is true.</span></span>

<span data-ttu-id="8b626-140">**Material**</span><span class="sxs-lookup"><span data-stu-id="8b626-140">**Material**</span></span>

<span data-ttu-id="8b626-141">Indica o material que deve ser usado ao criar a estrutura de tópicos da área rastreada.</span><span class="sxs-lookup"><span data-stu-id="8b626-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="8b626-142">**Camada física**</span><span class="sxs-lookup"><span data-stu-id="8b626-142">**Physics Layer**</span></span>

<span data-ttu-id="8b626-143">A camada na qual a área rastreada deve ser definida.</span><span class="sxs-lookup"><span data-stu-id="8b626-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="8b626-144">O valor padrão é a camada *ignorar Raycast* .</span><span class="sxs-lookup"><span data-stu-id="8b626-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="8b626-145">Configurações de parede de limite</span><span class="sxs-lookup"><span data-stu-id="8b626-145">Boundary wall settings</span></span>

![Configurações de parede de limite de visualização de limite](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="8b626-147">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="8b626-147">**Show**</span></span>

<span data-ttu-id="8b626-148">Indica se os planos de parede de limite devem ser criados e adicionados à cena.</span><span class="sxs-lookup"><span data-stu-id="8b626-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="8b626-149">O valor padrão é false.</span><span class="sxs-lookup"><span data-stu-id="8b626-149">The default value is false.</span></span>

<span data-ttu-id="8b626-150">**Material**</span><span class="sxs-lookup"><span data-stu-id="8b626-150">**Material**</span></span>

<span data-ttu-id="8b626-151">Indica o material que deve ser usado ao criar os planos de parede de limite.</span><span class="sxs-lookup"><span data-stu-id="8b626-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="8b626-152">**Camada física**</span><span class="sxs-lookup"><span data-stu-id="8b626-152">**Physics Layer**</span></span>

<span data-ttu-id="8b626-153">A camada na qual as paredes de limite devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="8b626-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="8b626-154">O valor padrão é a camada *ignorar Raycast* .</span><span class="sxs-lookup"><span data-stu-id="8b626-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="8b626-155">Definir o componente de borda de limite como uma camada física diferente de *ignorar Raycast* pode impedir que os usuários interajam com objetos dentro da cena.</span><span class="sxs-lookup"><span data-stu-id="8b626-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="8b626-156">Configurações de limite de limite</span><span class="sxs-lookup"><span data-stu-id="8b626-156">Boundary ceiling settings</span></span>

![Configurações de limite de limite de visualização de limite](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="8b626-158">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="8b626-158">**Show**</span></span>

<span data-ttu-id="8b626-159">Indica se um plano de limite deve ou não ser criado e adicionado à cena.</span><span class="sxs-lookup"><span data-stu-id="8b626-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="8b626-160">O valor padrão é false.</span><span class="sxs-lookup"><span data-stu-id="8b626-160">The default value is false.</span></span>

<span data-ttu-id="8b626-161">**Material**</span><span class="sxs-lookup"><span data-stu-id="8b626-161">**Material**</span></span>

<span data-ttu-id="8b626-162">Indica o material que deve ser usado ao criar o plano de limite de limite.</span><span class="sxs-lookup"><span data-stu-id="8b626-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="8b626-163">**Camada física**</span><span class="sxs-lookup"><span data-stu-id="8b626-163">**Physics Layer**</span></span>

<span data-ttu-id="8b626-164">A camada na qual as paredes de limite devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="8b626-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="8b626-165">O valor padrão é a *camada Ignorar Raycast.*</span><span class="sxs-lookup"><span data-stu-id="8b626-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="8b626-166">Definir o componente de limite de limite para uma camada física diferente de *Ignorar Raycast* pode impedir que os usuários interajam com objetos dentro da cena.</span><span class="sxs-lookup"><span data-stu-id="8b626-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b626-167">Confira também</span><span class="sxs-lookup"><span data-stu-id="8b626-167">See also</span></span>

- [<span data-ttu-id="8b626-168">Documentação da API de limite</span><span class="sxs-lookup"><span data-stu-id="8b626-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="8b626-169">Sistema de limite</span><span class="sxs-lookup"><span data-stu-id="8b626-169">Boundary System</span></span>](boundary-system-getting-started.md)
