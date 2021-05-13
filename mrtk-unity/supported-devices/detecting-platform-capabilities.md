---
title: DetectingPlatformCapabilities
description: Detalhes de diferentes funcionalidades compatíveis com o MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, funcionalidades,
ms.openlocfilehash: 62e03c6d47deb079d3460759b5c694dd258a7767
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852305"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="a22ed-104">Detectando funcionalidades da plataforma</span><span class="sxs-lookup"><span data-stu-id="a22ed-104">Detecting platform capabilities</span></span>

<span data-ttu-id="a22ed-105">Uma pergunta comum do MRTK envolve saber qual dispositivo específico (por exemplo, Microsoft HoloLens 2) está sendo usado para executar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a22ed-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="a22ed-106">Identificar o hardware exato pode ser um desafio em diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="a22ed-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="a22ed-107">Em vez disso, o MRTK fornece uma maneira de identificar recursos específicos em runtime(por exemplo, se o ponto de extremidade do dispositivo atual dá suporte a mãos articuladas).</span><span class="sxs-lookup"><span data-stu-id="a22ed-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="a22ed-108">Funcionalidades</span><span class="sxs-lookup"><span data-stu-id="a22ed-108">Capabilities</span></span>

<span data-ttu-id="a22ed-109">O Kit de Ferramentas de Realidade Misturada fornece a enumeração , que define um conjunto de recursos para os quais um aplicativo pode [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) consultar em runtime.</span><span class="sxs-lookup"><span data-stu-id="a22ed-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="a22ed-110">Funcionalidades do sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="a22ed-110">Input system capabilities</span></span>

<span data-ttu-id="a22ed-111">O sistema de entrada padrão do MRTK dá suporte à consulta dos seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="a22ed-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="a22ed-112">Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="a22ed-112">Capability</span></span> | <span data-ttu-id="a22ed-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a22ed-113">Description</span></span> |
|---|---|
| <span data-ttu-id="a22ed-114">ArticuladoHand</span><span class="sxs-lookup"><span data-stu-id="a22ed-114">ArticulatedHand</span></span> | <span data-ttu-id="a22ed-115">Entrada de mão articulada</span><span class="sxs-lookup"><span data-stu-id="a22ed-115">Articulated hand input</span></span> |
| <span data-ttu-id="a22ed-116">EyeTracking</span><span class="sxs-lookup"><span data-stu-id="a22ed-116">EyeTracking</span></span> | <span data-ttu-id="a22ed-117">Direcionamento para o olhar</span><span class="sxs-lookup"><span data-stu-id="a22ed-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="a22ed-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="a22ed-118">GGVHand</span></span> | <span data-ttu-id="a22ed-119">Entrada de mão de gesto de olhar/voz</span><span class="sxs-lookup"><span data-stu-id="a22ed-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="a22ed-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="a22ed-120">MotionController</span></span> | <span data-ttu-id="a22ed-121">Entrada do controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="a22ed-121">Motion controller input</span></span> |
| <span data-ttu-id="a22ed-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="a22ed-122">VoiceCommand</span></span> | <span data-ttu-id="a22ed-123">Comandos de voz usando palavras-chave definidas pelo aplicativo</span><span class="sxs-lookup"><span data-stu-id="a22ed-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="a22ed-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="a22ed-124">VoiceDictation</span></span> | <span data-ttu-id="a22ed-125">Ditado de voz para texto</span><span class="sxs-lookup"><span data-stu-id="a22ed-125">Voice to text dictation</span></span> |

<span data-ttu-id="a22ed-126">O código de exemplo abaixo verifica se o sistema de entrada carregou um provedor de dados com suporte para as mãos articuladas.</span><span class="sxs-lookup"><span data-stu-id="a22ed-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="a22ed-127">Recursos de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="a22ed-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="a22ed-128">O sistema de reconhecimento espacial MRTK padrão dá suporte à consulta dos seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="a22ed-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="a22ed-129">Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="a22ed-129">Capability</span></span> | <span data-ttu-id="a22ed-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="a22ed-130">Description</span></span> |
|---|---|
| <span data-ttu-id="a22ed-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="a22ed-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="a22ed-132">Malhas espaciais</span><span class="sxs-lookup"><span data-stu-id="a22ed-132">Spatial meshes</span></span> |
| <span data-ttu-id="a22ed-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="a22ed-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="a22ed-134">Planos espaciais</span><span class="sxs-lookup"><span data-stu-id="a22ed-134">Spatial planes</span></span> |
| <span data-ttu-id="a22ed-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="a22ed-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="a22ed-136">Pontos espaciais</span><span class="sxs-lookup"><span data-stu-id="a22ed-136">Spatial points</span></span> |

<span data-ttu-id="a22ed-137">Este exemplo verifica se o sistema de conscientização espacial carregou um provedor de dados com suporte para malhas espaciais.</span><span class="sxs-lookup"><span data-stu-id="a22ed-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="a22ed-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="a22ed-138">See also</span></span>

- [<span data-ttu-id="a22ed-139">Documentação da API do IMixedRealityCapabilityCheck</span><span class="sxs-lookup"><span data-stu-id="a22ed-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="a22ed-140">Documentação de enumeração do MixedRealityCapability</span><span class="sxs-lookup"><span data-stu-id="a22ed-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
