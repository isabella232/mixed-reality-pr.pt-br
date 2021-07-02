---
title: Detectando recursos de plataforma
description: Detalhes de diferentes recursos que o MRTK dá suporte
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, funcionalidades,
ms.openlocfilehash: 70d320e178f4635d74b5be6a1874eb4254801719
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175520"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="24304-104">Detectando recursos de plataforma</span><span class="sxs-lookup"><span data-stu-id="24304-104">Detecting platform capabilities</span></span>

<span data-ttu-id="24304-105">uma pergunta comum feita pelo MRTK envolve saber qual dispositivo específico (ex: Microsoft HoloLens 2) está sendo usado para executar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24304-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="24304-106">Identificar o hardware exato pode ser desafiador em diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="24304-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="24304-107">Em vez disso, o MRTK fornece uma maneira de identificar recursos específicos em tempo de execução, (por exemplo, se o ponto de extremidade do dispositivo atual der suporte a mãos articuladas).</span><span class="sxs-lookup"><span data-stu-id="24304-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="24304-108">Funcionalidades</span><span class="sxs-lookup"><span data-stu-id="24304-108">Capabilities</span></span>

<span data-ttu-id="24304-109">a realidade misturada Toolkit fornece a [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeração, que define um conjunto de recursos para os quais um aplicativo pode consultar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="24304-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="24304-110">Recursos do sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="24304-110">Input system capabilities</span></span>

<span data-ttu-id="24304-111">O sistema de entrada MRTK padrão dá suporte à consulta dos seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="24304-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="24304-112">Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="24304-112">Capability</span></span> | <span data-ttu-id="24304-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="24304-113">Description</span></span> |
|---|---|
| <span data-ttu-id="24304-114">ArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="24304-114">ArticulatedHand</span></span> | <span data-ttu-id="24304-115">Entrada de mão articulada</span><span class="sxs-lookup"><span data-stu-id="24304-115">Articulated hand input</span></span> |
| <span data-ttu-id="24304-116">EyeTracking</span><span class="sxs-lookup"><span data-stu-id="24304-116">EyeTracking</span></span> | <span data-ttu-id="24304-117">Direcionamento olhar de olho</span><span class="sxs-lookup"><span data-stu-id="24304-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="24304-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="24304-118">GGVHand</span></span> | <span data-ttu-id="24304-119">Olhar-gesto-entrada do lado da voz</span><span class="sxs-lookup"><span data-stu-id="24304-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="24304-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="24304-120">MotionController</span></span> | <span data-ttu-id="24304-121">Entrada do controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="24304-121">Motion controller input</span></span> |
| <span data-ttu-id="24304-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="24304-122">VoiceCommand</span></span> | <span data-ttu-id="24304-123">Comandos de voz usando palavras-chave definidas pelo aplicativo</span><span class="sxs-lookup"><span data-stu-id="24304-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="24304-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="24304-124">VoiceDictation</span></span> | <span data-ttu-id="24304-125">Ditado de voz para texto</span><span class="sxs-lookup"><span data-stu-id="24304-125">Voice to text dictation</span></span> |

<span data-ttu-id="24304-126">O código de exemplo abaixo verifica se o sistema de entrada carregou um provedor de dados com suporte para as mãos articuladas.</span><span class="sxs-lookup"><span data-stu-id="24304-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="24304-127">Recursos de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="24304-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="24304-128">O sistema de reconhecimento espacial MRTK padrão dá suporte à consulta dos seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="24304-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="24304-129">Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="24304-129">Capability</span></span> | <span data-ttu-id="24304-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="24304-130">Description</span></span> |
|---|---|
| <span data-ttu-id="24304-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="24304-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="24304-132">Malhas espaciais</span><span class="sxs-lookup"><span data-stu-id="24304-132">Spatial meshes</span></span> |
| <span data-ttu-id="24304-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="24304-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="24304-134">Planos espaciais</span><span class="sxs-lookup"><span data-stu-id="24304-134">Spatial planes</span></span> |
| <span data-ttu-id="24304-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="24304-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="24304-136">Pontos espaciais</span><span class="sxs-lookup"><span data-stu-id="24304-136">Spatial points</span></span> |

<span data-ttu-id="24304-137">Este exemplo verifica se o sistema de conscientização espacial carregou um provedor de dados com suporte para malhas espaciais.</span><span class="sxs-lookup"><span data-stu-id="24304-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="24304-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="24304-138">See also</span></span>

- [<span data-ttu-id="24304-139">Documentação da API do IMixedRealityCapabilityCheck</span><span class="sxs-lookup"><span data-stu-id="24304-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="24304-140">Documentação de enumeração do MixedRealityCapability</span><span class="sxs-lookup"><span data-stu-id="24304-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
