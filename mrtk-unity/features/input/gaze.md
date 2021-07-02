---
title: Focar
description: Docummentation em tipos de olhar no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, olhar,
ms.openlocfilehash: 95dad85ca8154d35f73906b53019d3a52ced546f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176910"
---
# <a name="gaze"></a><span data-ttu-id="23a35-104">Focar</span><span class="sxs-lookup"><span data-stu-id="23a35-104">Gaze</span></span>

<span data-ttu-id="23a35-105">[Olhar](/windows/mixed-reality/gaze) é uma forma de entrada que interage com o mundo com base em onde o usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="23a35-105">[Gaze](/windows/mixed-reality/gaze) is a form of input that interacts with the world based on where the user is looking.</span></span> <span data-ttu-id="23a35-106">Olhar existe em dois tipos diferentes</span><span class="sxs-lookup"><span data-stu-id="23a35-106">Gaze exists in two different flavors</span></span>

## <a name="head-gaze"></a><span data-ttu-id="23a35-107">Foco da cabeça</span><span class="sxs-lookup"><span data-stu-id="23a35-107">Head gaze</span></span>

<span data-ttu-id="23a35-108">Esse tipo de olhar é baseado na direção em que a cabeça/câmera está olhando.</span><span class="sxs-lookup"><span data-stu-id="23a35-108">This type of gaze is based on the direction that the head/camera is looking at.</span></span> <span data-ttu-id="23a35-109">O Head olhar está ativo em sistemas que não dão suporte a olhar de olho, ou em casos em que o hardware possa dar suporte a olho olhar, mas o conjunto certo de [permissões e configuração](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) não foi realizado.</span><span class="sxs-lookup"><span data-stu-id="23a35-109">Head gaze is active on systems that don't support eye gaze, or in cases where the hardware may support eye gaze, but the right set of [permissions and setup](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) has not been performed.</span></span>

<span data-ttu-id="23a35-110">o olhar de cabeçalho é geralmente associado a interações de estilo HoloLens 1 envolvendo examinar o objeto, colocando-o no centro do quadro Holographic e, em seguida, executando o gesto de toque do ar.</span><span class="sxs-lookup"><span data-stu-id="23a35-110">Head gaze is usually associated with HoloLens 1 style interactions involving looking at object by placing it in the center of the Holographic Frame and then performing the air tap gesture.</span></span>

## <a name="eye-gaze"></a><span data-ttu-id="23a35-111">Foco com o olhar</span><span class="sxs-lookup"><span data-stu-id="23a35-111">Eye gaze</span></span>

<span data-ttu-id="23a35-112">Esse tipo de olhar é baseado em onde os olhos do usuário estão olhando.</span><span class="sxs-lookup"><span data-stu-id="23a35-112">This type of gaze is based on where the user's eyes are looking.</span></span> <span data-ttu-id="23a35-113">O olho olhar está presente apenas em sistemas que dão suporte ao controle de olho.</span><span class="sxs-lookup"><span data-stu-id="23a35-113">Eye gaze is only present on systems that support eye tracking.</span></span> <span data-ttu-id="23a35-114">Consulte a [documentação de acompanhamento de olho](eye-tracking/eye-tracking-main.md) para obter mais detalhes sobre como usar o olho olhar.</span><span class="sxs-lookup"><span data-stu-id="23a35-114">See the [eye tracking documentation](eye-tracking/eye-tracking-main.md) for more details on how to use eye gaze.</span></span>

## <a name="gazeprovider"></a><span data-ttu-id="23a35-115">GazeProvider</span><span class="sxs-lookup"><span data-stu-id="23a35-115">GazeProvider</span></span>

<span data-ttu-id="23a35-116">A funcionalidade olhar (cabeça e olho) é fornecida pelo [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span><span class="sxs-lookup"><span data-stu-id="23a35-116">Gaze functionality (both head and eye) is provided by the [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span></span> <span data-ttu-id="23a35-117">Esse provedor pode ser configurado na seção de *ponteiro* do perfil do sistema de entrada:</span><span class="sxs-lookup"><span data-stu-id="23a35-117">This provider can be configured in the *Pointer* section of the input system profile:</span></span>

![Ponto de entrada de configuração do olhar](../images/input/GazeConfigurationEntrypoint.png)

<span data-ttu-id="23a35-119">Assim como outras fontes de entrada, o provedor olhar interage com objetos na cena por meio do uso de um ponteiro [(consulte este documento para obter informações sobre ponteiros)](../../architecture/controllers-pointers-and-focus.md).</span><span class="sxs-lookup"><span data-stu-id="23a35-119">Like other sources of input, the gaze provider interacts with objects in the scene through use of a pointer [(see this document for information on pointers)](../../architecture/controllers-pointers-and-focus.md).</span></span>
<span data-ttu-id="23a35-120">No caso do provedor olhar, seu ponteiro é implementado por meio do `InternalGazePointer` e não é configurado por meio de um perfil.</span><span class="sxs-lookup"><span data-stu-id="23a35-120">In the case of the gaze provider, its pointer is implemented via `InternalGazePointer` and is not configured through a profile.</span></span>

<span data-ttu-id="23a35-121">É possível substituir o GazeProvider de ações por uma implementação alternativa alterando o *tipo de provedor olhar* para fazer referência a uma classe diferente que implementa [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) e [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span><span class="sxs-lookup"><span data-stu-id="23a35-121">It is possible to replace the stock GazeProvider with an alternate implementation by changing *Gaze Provider Type* to reference a different class that implements [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) and [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span></span>
<span data-ttu-id="23a35-122">Geralmente, é recomendável usar o GazeProvider de estoque (e problemas de arquivamento ao localizar bugs), já que a nova implementação do GazeProvider não é trivial.</span><span class="sxs-lookup"><span data-stu-id="23a35-122">It's generally recommended to use the stock GazeProvider (and filing issues in when finding bugs) as re-implementing the GazeProvider is non-trivial.</span></span>

### <a name="alternative-platform-provided-gaze-poses"></a><span data-ttu-id="23a35-123">Olhar de pose alternativas fornecidas pela plataforma</span><span class="sxs-lookup"><span data-stu-id="23a35-123">Alternative platform-provided gaze poses</span></span>

<span data-ttu-id="23a35-124">Por padrão, o MRTK GazeProvider usa o centro do quadro da câmera como a origem olhar.</span><span class="sxs-lookup"><span data-stu-id="23a35-124">By default, the MRTK GazeProvider uses the center of the camera's frame as the gaze origin.</span></span> <span data-ttu-id="23a35-125">algumas plataformas, como Windows Mixed Reality no HoloLens 2, fornecem uma pose olhar definida como alternativa.</span><span class="sxs-lookup"><span data-stu-id="23a35-125">Some platforms, like Windows Mixed Reality on HoloLens 2, provide an alternatively defined gaze pose.</span></span> <span data-ttu-id="23a35-126">Isso é gerenciado por meio da `Use Head Gaze Override` configuração nas configurações de olhar.</span><span class="sxs-lookup"><span data-stu-id="23a35-126">This is managed via the `Use Head Gaze Override` setting in the gaze settings.</span></span> <span data-ttu-id="23a35-127">Quando habilitado, a substituição olhar alternativa será usada.</span><span class="sxs-lookup"><span data-stu-id="23a35-127">When enabled, the alternative gaze override will be used.</span></span> <span data-ttu-id="23a35-128">Quando desabilitado, a origem do centro de quadros padrão será usada.</span><span class="sxs-lookup"><span data-stu-id="23a35-128">When disabled, the default frame center origin will be used.</span></span> <span data-ttu-id="23a35-129">especificamente, para o HoloLens 2, o ângulo de olhar será gerado em vários graus para considerar o conforto do usuário no uso de sua cabeça para o direcionamento.</span><span class="sxs-lookup"><span data-stu-id="23a35-129">Specifically, for HoloLens 2, the gaze angle will be raised several degrees to account for user comfort in using their head for targeting.</span></span>

## <a name="usage"></a><span data-ttu-id="23a35-130">Uso</span><span class="sxs-lookup"><span data-stu-id="23a35-130">Usage</span></span>

### <a name="how-get-the-current-gaze-target"></a><span data-ttu-id="23a35-131">Como obter o destino de olhar atual</span><span class="sxs-lookup"><span data-stu-id="23a35-131">How get the current gaze target</span></span>

<span data-ttu-id="23a35-132">Este exemplo mostra como obter o objeto de jogo atual que é direcionado pelo usuário olhar.</span><span class="sxs-lookup"><span data-stu-id="23a35-132">This sample shows how to get the current game object that is targeted by the user gaze.</span></span>

```c#
void LogCurrentGazeTarget()
{
    if (CoreServices.InputSystem.GazeProvider.GazeTarget)
    {
        Debug.Log("User gaze is currently over game object: "
            + CoreServices.InputSystem.GazeProvider.GazeTarget)
    }
}
```

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a><span data-ttu-id="23a35-133">Como obter a origem e a direção do olhar atual</span><span class="sxs-lookup"><span data-stu-id="23a35-133">How to get the current gaze direction and origin</span></span>

<span data-ttu-id="23a35-134">Este exemplo mostra como obter o Vector3 que representa a direção do usuário olhar e a origem (o ponto do qual a direção está indo).</span><span class="sxs-lookup"><span data-stu-id="23a35-134">This sample shows how to get the Vector3 representing the direction of the user gaze and the origin (the point from which the direction is going).</span></span>

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
