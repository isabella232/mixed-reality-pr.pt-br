---
title: Mão do serviço de física
description: documentação para usar o serviço de extensão de física manual no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: af7ea753d52b5e478c54ca19d6d8e391401eea6d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176249"
---
# <a name="hand-physics-service"></a><span data-ttu-id="7ea50-104">Mão do serviço de física</span><span class="sxs-lookup"><span data-stu-id="7ea50-104">Hand physics service</span></span>

![Serviço de extensão de física manual](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="7ea50-106">O serviço de física manual permite eventos de colisão de corpo rígidos e interações com mãos articuladas.</span><span class="sxs-lookup"><span data-stu-id="7ea50-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="7ea50-107">Habilitando a extensão</span><span class="sxs-lookup"><span data-stu-id="7ea50-107">Enabling the extension</span></span>

<span data-ttu-id="7ea50-108">Para habilitar a extensão, abra o perfil do RegisteredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="7ea50-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="7ea50-109">Clique `Register a new Service Provider` para adicionar uma nova configuração.</span><span class="sxs-lookup"><span data-stu-id="7ea50-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="7ea50-110">No campo tipo de componente, selecione HandPhysicsService.</span><span class="sxs-lookup"><span data-stu-id="7ea50-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="7ea50-111">No campo perfil de configuração, selecione o perfil de física de mão padrão incluído com a extensão.</span><span class="sxs-lookup"><span data-stu-id="7ea50-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="7ea50-112">Opções de perfil</span><span class="sxs-lookup"><span data-stu-id="7ea50-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="7ea50-113">Camada física à mão</span><span class="sxs-lookup"><span data-stu-id="7ea50-113">Hand physics layer</span></span>

<span data-ttu-id="7ea50-114">Controla a camada à qual as junções de mão instanciada serão acessadas.</span><span class="sxs-lookup"><span data-stu-id="7ea50-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="7ea50-115">Embora o serviço seja padronizado para a camada "padrão" (0), é recomendável usar uma camada separada para objetos de física de mão.</span><span class="sxs-lookup"><span data-stu-id="7ea50-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="7ea50-116">Caso contrário, pode haver colisões indesejadas e/ou raycasts imprecisas.</span><span class="sxs-lookup"><span data-stu-id="7ea50-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="7ea50-117">Pré-fabricado do corpo cinemática da dica de dedo</span><span class="sxs-lookup"><span data-stu-id="7ea50-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="7ea50-118">Controla qual pré-fabricado é instanciado em mãos.</span><span class="sxs-lookup"><span data-stu-id="7ea50-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="7ea50-119">Para que o serviço funcione conforme o esperado, o pré-fabricado requer:</span><span class="sxs-lookup"><span data-stu-id="7ea50-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="7ea50-120">Um componente rigidbody, com iscinemática habilitada</span><span class="sxs-lookup"><span data-stu-id="7ea50-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="7ea50-121">Um colisor</span><span class="sxs-lookup"><span data-stu-id="7ea50-121">A collider</span></span>
- <span data-ttu-id="7ea50-122">componente `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="7ea50-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="7ea50-123">Usar o corpo do Palm cinemática</span><span class="sxs-lookup"><span data-stu-id="7ea50-123">Use palm kinematic body</span></span>

<span data-ttu-id="7ea50-124">Controla se o serviço tentará criar uma instância de um pré-fabricado no conjunto de Palm.</span><span class="sxs-lookup"><span data-stu-id="7ea50-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="7ea50-125">Pré-fabricado do corpo de Palm cinemática</span><span class="sxs-lookup"><span data-stu-id="7ea50-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="7ea50-126">Quando `UsePalmKinematicBody` está habilitado, esse é o pré-fabricado que ele criará.</span><span class="sxs-lookup"><span data-stu-id="7ea50-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="7ea50-127">Assim como `FingerTipKinematicBodyPrefab` , esse pré-fabricado requer:</span><span class="sxs-lookup"><span data-stu-id="7ea50-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="7ea50-128">Um componente rigidbody, com iscinemática habilitada</span><span class="sxs-lookup"><span data-stu-id="7ea50-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="7ea50-129">Um colisor</span><span class="sxs-lookup"><span data-stu-id="7ea50-129">A collider</span></span>
- <span data-ttu-id="7ea50-130">componente `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="7ea50-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="7ea50-131">Como usar o serviço</span><span class="sxs-lookup"><span data-stu-id="7ea50-131">How to use the service</span></span>

<span data-ttu-id="7ea50-132">Uma vez habilitado, use `IsTrigger` a propriedade do colisor para receber eventos de colisão de todos os 10 dígitos (e Palms, se estiverem habilitados).</span><span class="sxs-lookup"><span data-stu-id="7ea50-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
