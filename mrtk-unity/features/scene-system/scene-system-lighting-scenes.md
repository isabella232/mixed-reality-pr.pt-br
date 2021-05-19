---
title: Cenas de iluminação do sistema de cena
description: Documentação sobre iluminação na cena.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: fa7442bc968710a31ce3ca379c7fd73928e6e324
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144411"
---
# <a name="lighting-scene-operations"></a><span data-ttu-id="40080-104">Operações de cena de iluminação</span><span class="sxs-lookup"><span data-stu-id="40080-104">Lighting scene operations</span></span>

<span data-ttu-id="40080-105">A cena de iluminação padrão definida em seu perfil é carregada na inicialização.</span><span class="sxs-lookup"><span data-stu-id="40080-105">The default lighting scene defined in your profile is loaded on startup.</span></span> <span data-ttu-id="40080-106">Essa cena de iluminação permanece carregada até que `SetLightingScene` seja chamada.</span><span class="sxs-lookup"><span data-stu-id="40080-106">That lighting scene remains loaded until `SetLightingScene` is called.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a><span data-ttu-id="40080-107">Transições de configuração de iluminação</span><span class="sxs-lookup"><span data-stu-id="40080-107">Lighting setting transitions</span></span>

<span data-ttu-id="40080-108">`transitionType` controla o estilo da transição para a nova cena de iluminação.</span><span class="sxs-lookup"><span data-stu-id="40080-108">`transitionType` controls the style of the transition to new lighting scene.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

<span data-ttu-id="40080-109">Os estilos disponíveis são:</span><span class="sxs-lookup"><span data-stu-id="40080-109">The available styles are:</span></span>

<span data-ttu-id="40080-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="40080-110">Type</span></span> | <span data-ttu-id="40080-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="40080-111">Description</span></span> | <span data-ttu-id="40080-112">Duration</span><span class="sxs-lookup"><span data-stu-id="40080-112">Duration</span></span>
--- | --- | ---
<span data-ttu-id="40080-113">Nenhum</span><span class="sxs-lookup"><span data-stu-id="40080-113">None</span></span> | <span data-ttu-id="40080-114">A cena de iluminação anterior está descarregada, a nova cena de iluminação é carregada.</span><span class="sxs-lookup"><span data-stu-id="40080-114">Previous lighting scene is unloaded, new lighting scene is loaded.</span></span> <span data-ttu-id="40080-115">Sem transição.</span><span class="sxs-lookup"><span data-stu-id="40080-115">No transition.</span></span> | <span data-ttu-id="40080-116">Ignored</span><span class="sxs-lookup"><span data-stu-id="40080-116">Ignored</span></span>
<span data-ttu-id="40080-117">FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="40080-117">FadeToBlack</span></span> | <span data-ttu-id="40080-118">A cena de iluminação anterior esmaece para preto.</span><span class="sxs-lookup"><span data-stu-id="40080-118">Previous lighting scene fades out to black.</span></span> <span data-ttu-id="40080-119">A nova cena de iluminação é carregada e, em seguida, esmaecida de preto.</span><span class="sxs-lookup"><span data-stu-id="40080-119">New lighting scene is loaded, then faded up from black.</span></span> <span data-ttu-id="40080-120">Útil para transições suaves entre locais.</span><span class="sxs-lookup"><span data-stu-id="40080-120">Useful for smooth transitions between locations.</span></span> | <span data-ttu-id="40080-121">Usado</span><span class="sxs-lookup"><span data-stu-id="40080-121">Used</span></span>
<span data-ttu-id="40080-122">Fading cruzado</span><span class="sxs-lookup"><span data-stu-id="40080-122">CrossFade</span></span> | <span data-ttu-id="40080-123">A cena de iluminação anterior desaparece conforme a nova cena de iluminação esmaece.</span><span class="sxs-lookup"><span data-stu-id="40080-123">Previous lighting scene fades out as new lighting scene fades in.</span></span> <span data-ttu-id="40080-124">Útil para transições suaves entre as configurações de iluminação no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="40080-124">Useful for smooth transitions between lighting setups in the same location.</span></span> | <span data-ttu-id="40080-125">Usado</span><span class="sxs-lookup"><span data-stu-id="40080-125">Used</span></span>

<span data-ttu-id="40080-126">Observe que algumas configurações de iluminação não podem ser interpoladas durante as transições.</span><span class="sxs-lookup"><span data-stu-id="40080-126">Note that some lighting settings cannot be interpolated during transitions.</span></span> <span data-ttu-id="40080-127">Se você quiser uma transição Visual suave, essas configurações precisarão permanecer consistentes entre as cenas de iluminação.</span><span class="sxs-lookup"><span data-stu-id="40080-127">If you want a smooth visual transition these settings will have to remain consistent between lighting scenes.</span></span>

<span data-ttu-id="40080-128">Configuração</span><span class="sxs-lookup"><span data-stu-id="40080-128">Setting</span></span> | <span data-ttu-id="40080-129">Transição do Smooth FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="40080-129">Smooth FadeToBlack Transition</span></span> | <span data-ttu-id="40080-130">Transição de fading cruzado suave</span><span class="sxs-lookup"><span data-stu-id="40080-130">Smooth CrossFade Transition</span></span>
--- | --- | ---
<span data-ttu-id="40080-131">Skybox</span><span class="sxs-lookup"><span data-stu-id="40080-131">Skybox</span></span> | <span data-ttu-id="40080-132">Não</span><span class="sxs-lookup"><span data-stu-id="40080-132">No</span></span> | <span data-ttu-id="40080-133">Não</span><span class="sxs-lookup"><span data-stu-id="40080-133">No</span></span>
<span data-ttu-id="40080-134">Reflexões personalizadas</span><span class="sxs-lookup"><span data-stu-id="40080-134">Custom Reflections</span></span> | <span data-ttu-id="40080-135">Não</span><span class="sxs-lookup"><span data-stu-id="40080-135">No</span></span> | <span data-ttu-id="40080-136">Não</span><span class="sxs-lookup"><span data-stu-id="40080-136">No</span></span>
<span data-ttu-id="40080-137">Sombras em tempo real de luz solar</span><span class="sxs-lookup"><span data-stu-id="40080-137">Sun light realtime shadows</span></span> | <span data-ttu-id="40080-138">Sim</span><span class="sxs-lookup"><span data-stu-id="40080-138">Yes</span></span> | <span data-ttu-id="40080-139">Não</span><span class="sxs-lookup"><span data-stu-id="40080-139">No</span></span>
