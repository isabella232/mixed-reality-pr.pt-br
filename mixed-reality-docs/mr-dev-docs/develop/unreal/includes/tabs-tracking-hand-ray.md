---
ms.openlocfilehash: 23bba22801f61f6b4814991c8b3bde68d2c5f6b7
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002641"
---
# <a name="425"></a>[<span data-ttu-id="a35f4-101">4.25</span><span class="sxs-lookup"><span data-stu-id="a35f4-101">4.25</span></span>](#tab/425)

<span data-ttu-id="a35f4-102">Para usar raios de mão em plantas, pesquise qualquer uma das ações em **HMD de realidade mista do Windows**:</span><span class="sxs-lookup"><span data-stu-id="a35f4-102">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![Raios-mão BP](../images/unreal/hand-rays-bp.png)

<span data-ttu-id="a35f4-104">Para acessá-los em C++, inclua na `WindowsMixedRealityFunctionLibrary.h` parte superior do seu arquivo de código de chamada.</span><span class="sxs-lookup"><span data-stu-id="a35f4-104">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="a35f4-105">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a35f4-105">Enum</span></span>

<span data-ttu-id="a35f4-106">Você também tem acesso a casos de entrada em **EHMDInputControllerButtons**, que podem ser usados em plantas:</span><span class="sxs-lookup"><span data-stu-id="a35f4-106">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![Botões do controlador de entrada](../images/unreal/input-controller-buttons.png)

<span data-ttu-id="a35f4-108">Para acesso em C++, use a `EHMDInputControllerButtons` classe enum:</span><span class="sxs-lookup"><span data-stu-id="a35f4-108">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="a35f4-109">Abaixo está uma análise dos dois casos de enumeração aplicáveis:</span><span class="sxs-lookup"><span data-stu-id="a35f4-109">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="a35f4-110">**Select** -o evento de seleção disparado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="a35f4-110">**Select** - User triggered Select event.</span></span>
    * <span data-ttu-id="a35f4-111">Disparado no HoloLens 2 por Air-TAP, olhar e Commit ou dizendo "Select" com [entrada de voz](../unreal-voice-input.md) habilitada.</span><span class="sxs-lookup"><span data-stu-id="a35f4-111">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](../unreal-voice-input.md) enabled.</span></span>
* <span data-ttu-id="a35f4-112">**Segure** -evento de Segure disparado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="a35f4-112">**Grasp** - User triggered Grasp event.</span></span>
    * <span data-ttu-id="a35f4-113">Disparado no HoloLens 2 fechando os dedos do usuário em um holograma.</span><span class="sxs-lookup"><span data-stu-id="a35f4-113">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span>

<span data-ttu-id="a35f4-114">Você pode acessar o status de acompanhamento da malha do seu lado em C++ por meio da `EHMDTrackingStatus` Enumeração mostrada abaixo:</span><span class="sxs-lookup"><span data-stu-id="a35f4-114">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="a35f4-115">Abaixo está uma análise dos dois casos de enumeração aplicáveis:</span><span class="sxs-lookup"><span data-stu-id="a35f4-115">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="a35f4-116">Não **rastreado** – a mão não está visível</span><span class="sxs-lookup"><span data-stu-id="a35f4-116">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="a35f4-117">**Acompanhado** – a mão é totalmente controlada</span><span class="sxs-lookup"><span data-stu-id="a35f4-117">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="a35f4-118">Estrutura</span><span class="sxs-lookup"><span data-stu-id="a35f4-118">Struct</span></span>

<span data-ttu-id="a35f4-119">A estrutura PointerPoseInfo pode fornecer informações sobre os seguintes dados de mão:</span><span class="sxs-lookup"><span data-stu-id="a35f4-119">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="a35f4-120">**Origem** – origem da mão</span><span class="sxs-lookup"><span data-stu-id="a35f4-120">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="a35f4-121">**Direção** – direção da mão</span><span class="sxs-lookup"><span data-stu-id="a35f4-121">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="a35f4-122">**Up** – vetor de cima à mão</span><span class="sxs-lookup"><span data-stu-id="a35f4-122">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="a35f4-123">**Orientação** – o quaternion de orientação</span><span class="sxs-lookup"><span data-stu-id="a35f4-123">**Orientation** – orientation quaternion</span></span>
* <span data-ttu-id="a35f4-124">**Status de rastreamento** – status de acompanhamento atual</span><span class="sxs-lookup"><span data-stu-id="a35f4-124">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="a35f4-125">Você pode acessar a estrutura PointerPoseInfo por meio de plantas, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="a35f4-125">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![Ponteiro de pose de informações BP](../images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="a35f4-127">Ou com C++:</span><span class="sxs-lookup"><span data-stu-id="a35f4-127">Or with C++:</span></span>

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

### <a name="functions"></a><span data-ttu-id="a35f4-128">Funções</span><span class="sxs-lookup"><span data-stu-id="a35f4-128">Functions</span></span>

<span data-ttu-id="a35f4-129">Todas as funções listadas abaixo podem ser chamadas em cada quadro, o que permite o monitoramento contínuo.</span><span class="sxs-lookup"><span data-stu-id="a35f4-129">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span>

1. <span data-ttu-id="a35f4-130">**Obter** informações de pose de ponteiro retorna informações completas sobre a direção de raio da mão no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="a35f4-130">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span>

<span data-ttu-id="a35f4-131">Gráfico</span><span class="sxs-lookup"><span data-stu-id="a35f4-131">Blueprint:</span></span>

![Obter informações de pose de ponteiro](../images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="a35f4-133">C++:</span><span class="sxs-lookup"><span data-stu-id="a35f4-133">C++:</span></span>
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="a35f4-134">**É Segure** retorna true se a mão estiver segurando no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="a35f4-134">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="a35f4-135">Gráfico</span><span class="sxs-lookup"><span data-stu-id="a35f4-135">Blueprint:</span></span>

![BP é compreendida](../images/unreal/is-grasped-bp.png)

<span data-ttu-id="a35f4-137">C++:</span><span class="sxs-lookup"><span data-stu-id="a35f4-137">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. <span data-ttu-id="a35f4-138">**Is Select pressionado** retorna true se o usuário disparasse SELECT no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="a35f4-138">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="a35f4-139">Gráfico</span><span class="sxs-lookup"><span data-stu-id="a35f4-139">Blueprint:</span></span>

![É selecione BP pressionado](../images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="a35f4-141">C++:</span><span class="sxs-lookup"><span data-stu-id="a35f4-141">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="a35f4-142">O **botão é clicado** retorna true se o evento ou botão for disparado no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="a35f4-142">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="a35f4-143">Gráfico</span><span class="sxs-lookup"><span data-stu-id="a35f4-143">Blueprint:</span></span>

![É um botão clicado em BP](../images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="a35f4-145">C++:</span><span class="sxs-lookup"><span data-stu-id="a35f4-145">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="a35f4-146">**Obter status de controle do controlador** retorna o status de acompanhamento no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="a35f4-146">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="a35f4-147">Gráfico</span><span class="sxs-lookup"><span data-stu-id="a35f4-147">Blueprint:</span></span>

![Obter o status de controle do controlador BP](../images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="a35f4-149">C++:</span><span class="sxs-lookup"><span data-stu-id="a35f4-149">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
# <a name="426"></a>[<span data-ttu-id="a35f4-150">4.26</span><span class="sxs-lookup"><span data-stu-id="a35f4-150">4.26</span></span>](#tab/426)

<span data-ttu-id="a35f4-151">Para obter os dados para os raios de mão, você deve usar a função obter dados do controlador de movimento da seção anterior.</span><span class="sxs-lookup"><span data-stu-id="a35f4-151">To get the data for the hand rays, you should use the Get Motion Controller Data function from the previous section.</span></span> <span data-ttu-id="a35f4-152">A estrutura retornada contém dois parâmetros que você pode usar para criar uma **posição** de raio e a **rotação** do AIM.</span><span class="sxs-lookup"><span data-stu-id="a35f4-152">The returned structure contains two parameters you can use to create a hand ray – **Aim Position** and **Aim Rotation**.</span></span> <span data-ttu-id="a35f4-153">Esses parâmetros formam um raio direcionado pelo cotovelo.</span><span class="sxs-lookup"><span data-stu-id="a35f4-153">These parameters form a ray directed by your elbow.</span></span> <span data-ttu-id="a35f4-154">Você deve levá-los e encontrar um holograma sendo apontado.</span><span class="sxs-lookup"><span data-stu-id="a35f4-154">You should take them and find a hologram being pointed by.</span></span>

<span data-ttu-id="a35f4-155">Abaixo está um exemplo de como determinar se um raio de lado atinge um widget e como definir um resultado de ocorrência personalizada:</span><span class="sxs-lookup"><span data-stu-id="a35f4-155">Below is an example of determining whether a hand ray hits a Widget and setting a custom hit result:</span></span>

![Plano gráfico da função obter dados do controlador de movimento](../images/unreal-hand-tracking-img-04.png) 