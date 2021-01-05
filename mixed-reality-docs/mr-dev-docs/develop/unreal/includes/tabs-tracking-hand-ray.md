---
ms.openlocfilehash: 18ccbf3e28eaa2f61157bd9585d633c987e9af48
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717422"
---
# <a name="426"></a>[<span data-ttu-id="e0890-101">4.26</span><span class="sxs-lookup"><span data-stu-id="e0890-101">4.26</span></span>](#tab/426)

<span data-ttu-id="e0890-102">Para obter os dados para os raios de mão, você deve usar a função obter dados do controlador de movimento da seção anterior.</span><span class="sxs-lookup"><span data-stu-id="e0890-102">To get the data for the hand rays, you should use the Get Motion Controller Data function from the previous section.</span></span> <span data-ttu-id="e0890-103">A estrutura retornada contém dois parâmetros que você pode usar para criar uma **posição** de raio e a **rotação** do AIM.</span><span class="sxs-lookup"><span data-stu-id="e0890-103">The returned structure contains two parameters you can use to create a hand ray – **Aim Position** and **Aim Rotation**.</span></span> <span data-ttu-id="e0890-104">Esses parâmetros formam um raio direcionado pelo cotovelo.</span><span class="sxs-lookup"><span data-stu-id="e0890-104">These parameters form a ray directed by your elbow.</span></span> <span data-ttu-id="e0890-105">Você deve levá-los e encontrar um holograma sendo apontado.</span><span class="sxs-lookup"><span data-stu-id="e0890-105">You should take them and find a hologram being pointed by.</span></span>

<span data-ttu-id="e0890-106">Abaixo está um exemplo de como determinar se um raio de lado atinge um widget e como definir um resultado de ocorrência personalizada:</span><span class="sxs-lookup"><span data-stu-id="e0890-106">Below is an example of determining whether a hand ray hits a Widget and setting a custom hit result:</span></span>

![Plano gráfico da função obter dados do controlador de movimento](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[<span data-ttu-id="e0890-108">4.25</span><span class="sxs-lookup"><span data-stu-id="e0890-108">4.25</span></span>](#tab/425)

<span data-ttu-id="e0890-109">Para usar raios de mão em plantas, pesquise qualquer uma das ações em **HMD de realidade mista do Windows**:</span><span class="sxs-lookup"><span data-stu-id="e0890-109">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![Raios-mão BP](../images/unreal/hand-rays-bp.png)

<span data-ttu-id="e0890-111">Para acessá-los em C++, inclua na `WindowsMixedRealityFunctionLibrary.h` parte superior do seu arquivo de código de chamada.</span><span class="sxs-lookup"><span data-stu-id="e0890-111">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="e0890-112">Enumeração</span><span class="sxs-lookup"><span data-stu-id="e0890-112">Enum</span></span>

<span data-ttu-id="e0890-113">Você também tem acesso a casos de entrada em **EHMDInputControllerButtons**, que podem ser usados em plantas:</span><span class="sxs-lookup"><span data-stu-id="e0890-113">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![Botões do controlador de entrada](../images/unreal/input-controller-buttons.png)

<span data-ttu-id="e0890-115">Para acesso em C++, use a `EHMDInputControllerButtons` classe enum:</span><span class="sxs-lookup"><span data-stu-id="e0890-115">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="e0890-116">Abaixo está uma análise dos dois casos de enumeração aplicáveis:</span><span class="sxs-lookup"><span data-stu-id="e0890-116">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="e0890-117">**Select** -o evento de seleção disparado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e0890-117">**Select** - User triggered Select event.</span></span>
    * <span data-ttu-id="e0890-118">Disparado no HoloLens 2 por Air-TAP, olhar e Commit ou dizendo "Select" com [entrada de voz](../unreal-voice-input.md) habilitada.</span><span class="sxs-lookup"><span data-stu-id="e0890-118">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](../unreal-voice-input.md) enabled.</span></span>
* <span data-ttu-id="e0890-119">**Segure** -evento de Segure disparado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e0890-119">**Grasp** - User triggered Grasp event.</span></span>
    * <span data-ttu-id="e0890-120">Disparado no HoloLens 2 fechando os dedos do usuário em um holograma.</span><span class="sxs-lookup"><span data-stu-id="e0890-120">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span>

<span data-ttu-id="e0890-121">Você pode acessar o status de acompanhamento da malha do seu lado em C++ por meio da `EHMDTrackingStatus` Enumeração mostrada abaixo:</span><span class="sxs-lookup"><span data-stu-id="e0890-121">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="e0890-122">Abaixo está uma análise dos dois casos de enumeração aplicáveis:</span><span class="sxs-lookup"><span data-stu-id="e0890-122">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="e0890-123">Não **rastreado** – a mão não está visível</span><span class="sxs-lookup"><span data-stu-id="e0890-123">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="e0890-124">**Acompanhado** – a mão é totalmente controlada</span><span class="sxs-lookup"><span data-stu-id="e0890-124">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="e0890-125">Estrutura</span><span class="sxs-lookup"><span data-stu-id="e0890-125">Struct</span></span>

<span data-ttu-id="e0890-126">A estrutura PointerPoseInfo pode fornecer informações sobre os seguintes dados de mão:</span><span class="sxs-lookup"><span data-stu-id="e0890-126">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="e0890-127">**Origem** – origem da mão</span><span class="sxs-lookup"><span data-stu-id="e0890-127">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="e0890-128">**Direção** – direção da mão</span><span class="sxs-lookup"><span data-stu-id="e0890-128">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="e0890-129">**Up** – vetor de cima à mão</span><span class="sxs-lookup"><span data-stu-id="e0890-129">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="e0890-130">**Orientação** – o quaternion de orientação</span><span class="sxs-lookup"><span data-stu-id="e0890-130">**Orientation** – orientation quaternion</span></span>
* <span data-ttu-id="e0890-131">**Status de rastreamento** – status de acompanhamento atual</span><span class="sxs-lookup"><span data-stu-id="e0890-131">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="e0890-132">Você pode acessar a estrutura PointerPoseInfo por meio de plantas, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="e0890-132">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![Ponteiro de pose de informações BP](../images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="e0890-134">Ou com C++:</span><span class="sxs-lookup"><span data-stu-id="e0890-134">Or with C++:</span></span>

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a><span data-ttu-id="e0890-135">Funções</span><span class="sxs-lookup"><span data-stu-id="e0890-135">Functions</span></span>

<span data-ttu-id="e0890-136">Todas as funções listadas abaixo podem ser chamadas em cada quadro, o que permite o monitoramento contínuo.</span><span class="sxs-lookup"><span data-stu-id="e0890-136">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span>

1. <span data-ttu-id="e0890-137">**Obter** informações de pose de ponteiro retorna informações completas sobre a direção de raio da mão no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="e0890-137">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span>

<span data-ttu-id="e0890-138">Gráfico</span><span class="sxs-lookup"><span data-stu-id="e0890-138">Blueprint:</span></span>

![Obter informações de pose de ponteiro](../images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="e0890-140">C++:</span><span class="sxs-lookup"><span data-stu-id="e0890-140">C++:</span></span>
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="e0890-141">**É Segure** retorna true se a mão estiver segurando no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="e0890-141">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="e0890-142">Gráfico</span><span class="sxs-lookup"><span data-stu-id="e0890-142">Blueprint:</span></span>

![BP é compreendida](../images/unreal/is-grasped-bp.png)

<span data-ttu-id="e0890-144">C++:</span><span class="sxs-lookup"><span data-stu-id="e0890-144">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. <span data-ttu-id="e0890-145">**Is Select pressionado** retorna true se o usuário disparasse SELECT no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="e0890-145">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="e0890-146">Gráfico</span><span class="sxs-lookup"><span data-stu-id="e0890-146">Blueprint:</span></span>

![É selecione BP pressionado](../images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="e0890-148">C++:</span><span class="sxs-lookup"><span data-stu-id="e0890-148">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="e0890-149">O **botão é clicado** retorna true se o evento ou botão for disparado no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="e0890-149">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="e0890-150">Gráfico</span><span class="sxs-lookup"><span data-stu-id="e0890-150">Blueprint:</span></span>

![É um botão clicado em BP](../images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="e0890-152">C++:</span><span class="sxs-lookup"><span data-stu-id="e0890-152">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="e0890-153">**Obter status de controle do controlador** retorna o status de acompanhamento no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="e0890-153">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="e0890-154">Gráfico</span><span class="sxs-lookup"><span data-stu-id="e0890-154">Blueprint:</span></span>

![Obter o status de controle do controlador BP](../images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="e0890-156">C++:</span><span class="sxs-lookup"><span data-stu-id="e0890-156">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```