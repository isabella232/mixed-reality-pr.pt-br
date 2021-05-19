---
title: Provedor de foco de olho de acompanhamento ocular
description: Documentação do provedor de olhar no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, EyeTracking, EyeGaze,
ms.openlocfilehash: ef50a55d52a5dad9f424c8af8139565e02542b6c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144023"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a><span data-ttu-id="64b78-104">Acessando dados de acompanhamento ocular em seu script do Unity</span><span class="sxs-lookup"><span data-stu-id="64b78-104">Accessing eye tracking data in your Unity script</span></span>

<span data-ttu-id="64b78-105">Este artigo pressuila que você tenha compreensão para configurar o acompanhamento ocular em uma cena do MRTK (consulte Configuração básica do [MRTK para usar o acompanhamento ocular).](eye-tracking-basic-setup.md)</span><span class="sxs-lookup"><span data-stu-id="64b78-105">This article assumes one has understanding for setting up eye tracking in an MRTK scene (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)).</span></span>
<span data-ttu-id="64b78-106">Acessar dados de acompanhamento ocular em um script MonoBehaviour é fácil!</span><span class="sxs-lookup"><span data-stu-id="64b78-106">Accessing eye tracking data in a MonoBehaviour script is easy!</span></span> <span data-ttu-id="64b78-107">Basta usar *CoreServices.InputSystem.EyeGazeProvider*.</span><span class="sxs-lookup"><span data-stu-id="64b78-107">Simply use *CoreServices.InputSystem.EyeGazeProvider*.</span></span>

## <a name="imixedrealityeyegazeprovider"></a><span data-ttu-id="64b78-108">IMixedRealityEyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="64b78-108">IMixedRealityEyeGazeProvider</span></span>

<span data-ttu-id="64b78-109">A configuração de acompanhamento ocular no MRTK é configurada por meio da [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface .</span><span class="sxs-lookup"><span data-stu-id="64b78-109">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span> <span data-ttu-id="64b78-110">O [uso de CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) fornece a implementação padrão do provedor de gaze registrada no kit de ferramentas em runtime.</span><span class="sxs-lookup"><span data-stu-id="64b78-110">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span>
<span data-ttu-id="64b78-111">As propriedades úteis do `EyeGazeProvider` são descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="64b78-111">Useful properties of the `EyeGazeProvider` is outlined below.</span></span>

- <span data-ttu-id="64b78-112">**IsEyeTrackingEnabled:** True se o usuário tiver selecionado usar o acompanhamento ocular para o olhar.</span><span class="sxs-lookup"><span data-stu-id="64b78-112">**IsEyeTrackingEnabled**: True if user has selected to use eye tracking for gaze.</span></span>

- <span data-ttu-id="64b78-113">**IsEyeCalibrationValid:** indica se a calibragem do acompanhamento ocular do usuário é válida ou não.</span><span class="sxs-lookup"><span data-stu-id="64b78-113">**IsEyeCalibrationValid**: Indicates whether the user's eye tracking calibration is valid or not.</span></span>
<span data-ttu-id="64b78-114">Ele retornará 'null', se o valor ainda não tiver recebido dados do sistema de acompanhamento ocular.</span><span class="sxs-lookup"><span data-stu-id="64b78-114">It returns 'null', if the value has not yet received data from the eye tracking system.</span></span>
<span data-ttu-id="64b78-115">Pode ser inválido, porque o usuário ignorava a calibragem de acompanhamento ocular.</span><span class="sxs-lookup"><span data-stu-id="64b78-115">It may be invalid, because the user skipped the eye tracking calibration.</span></span>

- <span data-ttu-id="64b78-116">**IsEyeTrackingEnabledAndValid:** indica se os dados de acompanhamento ocular atuais estão sendo usados atualmente para o olhar.</span><span class="sxs-lookup"><span data-stu-id="64b78-116">**IsEyeTrackingEnabledAndValid**: Indicates whether the current eye tracking data is currently been used for gaze.</span></span>

- <span data-ttu-id="64b78-117">**IsEyeTrackingDataValid:** true se os dados de acompanhamento ocular estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="64b78-117">**IsEyeTrackingDataValid**: True if eye tracking data is available.</span></span>
<span data-ttu-id="64b78-118">No entanto, ele pode não estar disponível devido ao tempo limite excedido (deve ser robusto para o usuário piscar) ou à falta de hardware ou permissões de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="64b78-118">It may be unavailable due to exceeded timeout (should be robust to the user blinking though) or lack of tracking hardware or permissions.</span></span>
<span data-ttu-id="64b78-119">Confira nosso exemplo [de notificação de calibragem](eye-tracking-is-user-calibrated.md) ocular ausente que explica como detectar se um usuário está calibrado com o olhar e para mostrar uma notificação apropriada.</span><span class="sxs-lookup"><span data-stu-id="64b78-119">Check out our [Missing eye calibration notification sample](eye-tracking-is-user-calibrated.md) that explains how to detect whether a user is eye calibrated and to show an appropriate notification.</span></span>

- <span data-ttu-id="64b78-120">**GazeOrigin:** origem do raio do olhar.</span><span class="sxs-lookup"><span data-stu-id="64b78-120">**GazeOrigin**: Origin of the gaze ray.</span></span>
<span data-ttu-id="64b78-121">Observe que isso retornará a *origem do* olhar de cabeça se 'IsEyeGazeValid' for false.</span><span class="sxs-lookup"><span data-stu-id="64b78-121">Please note that this will return the *head* gaze origin if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="64b78-122">**GazeDirection**: direção do olhar Ray.</span><span class="sxs-lookup"><span data-stu-id="64b78-122">**GazeDirection**: Direction of the gaze ray.</span></span>
<span data-ttu-id="64b78-123">Isso retornará a direção da olhar de *cabeçalho* se ' IsEyeGazeValid ' for false.</span><span class="sxs-lookup"><span data-stu-id="64b78-123">This will return the *head* gaze direction if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="64b78-124">**HitInfo**, **HitPosition**, **HitNormal**, etc.: informações sobre o gazed no momento no destino.</span><span class="sxs-lookup"><span data-stu-id="64b78-124">**HitInfo**, **HitPosition**, **HitNormal**, etc.: Information about the currently gazed at target.</span></span>
<span data-ttu-id="64b78-125">Novamente, se `IsEyeGazeValid` for false, isso será baseado no olhar da *cabeça* do usuário.</span><span class="sxs-lookup"><span data-stu-id="64b78-125">Again, if `IsEyeGazeValid` is false, this will be based on the user's *head* gaze.</span></span>

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a><span data-ttu-id="64b78-126">Exemplos de uso de CoreServices. InputSystem. EyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="64b78-126">Examples for using CoreServices.InputSystem.EyeGazeProvider</span></span>

<span data-ttu-id="64b78-127">Aqui está um exemplo do [FollowEyeGaze. cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span><span class="sxs-lookup"><span data-stu-id="64b78-127">Here is an example from the [FollowEyeGaze.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span></span>

- <span data-ttu-id="64b78-128">Obtenha o ponto de um holograma que o usuário está vendo:</span><span class="sxs-lookup"><span data-stu-id="64b78-128">Get the point of a hologram that the user is looking at:</span></span>

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- <span data-ttu-id="64b78-129">Mostrando um ativo visual a uma distância fixa de onde o usuário está atualmente procurando:</span><span class="sxs-lookup"><span data-stu-id="64b78-129">Showing a visual asset at a fixed distance from where the user is currently looking:</span></span>

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a><span data-ttu-id="64b78-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="64b78-130">See also</span></span>

- [<span data-ttu-id="64b78-131">Visão geral do acompanhamento de olho do MRTK</span><span class="sxs-lookup"><span data-stu-id="64b78-131">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="64b78-132">Configuração de acompanhamento de olho do MRTK</span><span class="sxs-lookup"><span data-stu-id="64b78-132">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="64b78-133">Calibragem de controle ocular MRTK</span><span class="sxs-lookup"><span data-stu-id="64b78-133">MRTK Eye Tracking Calibration</span></span>](eye-tracking-is-user-calibrated.md)
- [<span data-ttu-id="64b78-134">Documentação de acompanhamento de olho do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="64b78-134">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)