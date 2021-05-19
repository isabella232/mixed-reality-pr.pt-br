---
title: Visão geral do serviço de física
description: documentação para usar o serviço de extensão de física manual no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 751aec148d3a40da4728d2fdd60a60402b59a4de
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145087"
---
# <a name="hand-physics-extension-service"></a><span data-ttu-id="423f5-104">Serviço de extensão de física manual</span><span class="sxs-lookup"><span data-stu-id="423f5-104">Hand physics extension service</span></span>

![Serviço de extensão de física manual](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="423f5-106">O serviço de física manual permite eventos de colisão de corpo rígidos e interações com mãos articuladas.</span><span class="sxs-lookup"><span data-stu-id="423f5-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="423f5-107">Habilitando a extensão</span><span class="sxs-lookup"><span data-stu-id="423f5-107">Enabling the extension</span></span>

<span data-ttu-id="423f5-108">Para habilitar a extensão, abra o perfil do RegisteredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="423f5-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="423f5-109">Clique `Register a new Service Provider` para adicionar uma nova configuração.</span><span class="sxs-lookup"><span data-stu-id="423f5-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="423f5-110">No campo tipo de componente, selecione HandPhysicsService.</span><span class="sxs-lookup"><span data-stu-id="423f5-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="423f5-111">No campo perfil de configuração, selecione o perfil de física de mão padrão incluído com a extensão.</span><span class="sxs-lookup"><span data-stu-id="423f5-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="423f5-112">Opções de perfil</span><span class="sxs-lookup"><span data-stu-id="423f5-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="423f5-113">Camada física à mão</span><span class="sxs-lookup"><span data-stu-id="423f5-113">Hand physics layer</span></span>

<span data-ttu-id="423f5-114">Controla a camada à qual as junções de mão instanciada serão acessadas.</span><span class="sxs-lookup"><span data-stu-id="423f5-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="423f5-115">Embora o serviço seja padronizado para a camada "padrão" (0), é recomendável usar uma camada separada para objetos de física de mão.</span><span class="sxs-lookup"><span data-stu-id="423f5-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="423f5-116">Caso contrário, pode haver colisões indesejadas e/ou raycasts imprecisas.</span><span class="sxs-lookup"><span data-stu-id="423f5-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="423f5-117">Pré-fabricado do corpo cinemática da dica de dedo</span><span class="sxs-lookup"><span data-stu-id="423f5-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="423f5-118">Controla qual pré-fabricado é instanciado em mãos.</span><span class="sxs-lookup"><span data-stu-id="423f5-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="423f5-119">Para que o serviço funcione conforme o esperado, o pré-fabricado requer:</span><span class="sxs-lookup"><span data-stu-id="423f5-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="423f5-120">Um componente rigidbody, com iscinemática habilitada</span><span class="sxs-lookup"><span data-stu-id="423f5-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="423f5-121">Um colisor</span><span class="sxs-lookup"><span data-stu-id="423f5-121">A collider</span></span>
- <span data-ttu-id="423f5-122">componente `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="423f5-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="423f5-123">Usar o corpo kinematic da mão</span><span class="sxs-lookup"><span data-stu-id="423f5-123">Use palm kinematic body</span></span>

<span data-ttu-id="423f5-124">Controla se o serviço tentará insinuar um pré-fab na junção da mão.</span><span class="sxs-lookup"><span data-stu-id="423f5-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="423f5-125">Pré-fab de corpo kinematic da mão</span><span class="sxs-lookup"><span data-stu-id="423f5-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="423f5-126">Quando `UsePalmKinematicBody` está habilitado, esse é o pré-fab que ele insinuou.</span><span class="sxs-lookup"><span data-stu-id="423f5-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="423f5-127">Assim como `FingerTipKinematicBodyPrefab` , esse pré-fab requer:</span><span class="sxs-lookup"><span data-stu-id="423f5-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="423f5-128">Um componente rigidbody, com isKinematic habilitado</span><span class="sxs-lookup"><span data-stu-id="423f5-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="423f5-129">Um colisor</span><span class="sxs-lookup"><span data-stu-id="423f5-129">A collider</span></span>
- <span data-ttu-id="423f5-130">componente `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="423f5-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="423f5-131">Como usar o serviço</span><span class="sxs-lookup"><span data-stu-id="423f5-131">How to use the service</span></span>

<span data-ttu-id="423f5-132">Uma vez habilitado, use a propriedade de qualquer colisor para receber eventos de colisão de todos os 10 dígitos (e as mãos, se eles `IsTrigger` estão habilitados).</span><span class="sxs-lookup"><span data-stu-id="423f5-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
