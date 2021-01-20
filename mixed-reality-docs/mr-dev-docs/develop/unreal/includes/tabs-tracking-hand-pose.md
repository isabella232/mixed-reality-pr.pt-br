---
ms.openlocfilehash: 21c29b2c8d540378259200cc834f7a36065f8ab3
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581115"
---
# <a name="426"></a>[<span data-ttu-id="10ec6-101">4.26</span><span class="sxs-lookup"><span data-stu-id="10ec6-101">4.26</span></span>](#tab/426)

<span data-ttu-id="10ec6-102">A hierarquia é descrita por `EHandKeypoint` enum:</span><span class="sxs-lookup"><span data-stu-id="10ec6-102">The hierarchy is described by `EHandKeypoint` enum:</span></span>

![Imagem de opções do Bluprint keypoint](../images/hand-keypoint-bp.png)

<span data-ttu-id="10ec6-104">Você pode obter todos esses dados de uma mão do usuário usando a função **obter dados do controlador de movimento** .</span><span class="sxs-lookup"><span data-stu-id="10ec6-104">You can get all this data from a user’s hands using the **Get Motion Controller Data** function.</span></span> <span data-ttu-id="10ec6-105">Essa função retorna uma estrutura **XRMotionControllerData** .</span><span class="sxs-lookup"><span data-stu-id="10ec6-105">That function returns an **XRMotionControllerData** structure.</span></span> <span data-ttu-id="10ec6-106">Veja abaixo um exemplo de script de Blueprint que analisa a estrutura XRMotionControllerData para obter locais conjuntos em conjunto e desenha um sistema de coordenadas de depuração em cada local de cada conjunto.</span><span class="sxs-lookup"><span data-stu-id="10ec6-106">Below is a sample Blueprint script that parses the XRMotionControllerData structure to get hand joint locations and draws a debug coordinate system at each joint’s location.</span></span>

![Plano gráfico da função obter dados olhar conectados ao rastreamento de linha por função de canal](../images/unreal-hand-tracking-img-03.png)

<span data-ttu-id="10ec6-108">É importante verificar se a estrutura é válida e se ela é uma mão.</span><span class="sxs-lookup"><span data-stu-id="10ec6-108">It's important to check if the structure is valid and that it's a hand.</span></span> <span data-ttu-id="10ec6-109">Caso contrário, você pode obter um comportamento indefinido no acesso a posições, rotações e matrizes de raios.</span><span class="sxs-lookup"><span data-stu-id="10ec6-109">Otherwise, you may get undefined behavior in access to positions, rotations, and radii arrays.</span></span>

# <a name="425"></a>[<span data-ttu-id="10ec6-110">4.25</span><span class="sxs-lookup"><span data-stu-id="10ec6-110">4.25</span></span>](#tab/425)

<span data-ttu-id="10ec6-111">A `EWMRHandKeypoint` Enumeração descreve a hierarquia do Bone da mão.</span><span class="sxs-lookup"><span data-stu-id="10ec6-111">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="10ec6-112">Você pode encontrar cada ponto de extremidade à mão listado em seus planos gráficos:</span><span class="sxs-lookup"><span data-stu-id="10ec6-112">You can find each hand keypoint listed in your Blueprints:</span></span>

![Mão keypoint BP](../images/hand-keypoint-bp.png)

<span data-ttu-id="10ec6-114">A enumeração C++ completa está listada abaixo:</span><span class="sxs-lookup"><span data-stu-id="10ec6-114">The full C++ enum is listed below:</span></span>
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

<span data-ttu-id="10ec6-115">Você pode encontrar os valores numéricos para cada caso de enum na tabela [Windows. percepção. People. HandJointKind](/uwp/api/windows.perception.people.handjointkind) .</span><span class="sxs-lookup"><span data-stu-id="10ec6-115">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](/uwp/api/windows.perception.people.handjointkind) table.</span></span>

### <a name="supporting-hand-tracking"></a><span data-ttu-id="10ec6-116">Acompanhamento de suporte à mão</span><span class="sxs-lookup"><span data-stu-id="10ec6-116">Supporting Hand Tracking</span></span>

<span data-ttu-id="10ec6-117">Você pode usar o rastreamento manual em plantas adicionando **suporte ao rastreamento** à mão **> realidade mista do Windows**:</span><span class="sxs-lookup"><span data-stu-id="10ec6-117">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![Controle à mão BP](../images/unreal/hand-tracking-bp.png)

<span data-ttu-id="10ec6-119">Essa função retornará `true` se o controle à mão tiver suporte no dispositivo e `false` se o rastreamento à mão não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="10ec6-119">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![Dá suporte ao controle à mão BP](../images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="10ec6-121">C++:</span><span class="sxs-lookup"><span data-stu-id="10ec6-121">C++:</span></span>

<span data-ttu-id="10ec6-122">Inclua `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span><span class="sxs-lookup"><span data-stu-id="10ec6-122">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="10ec6-123">Obtendo controle à mão</span><span class="sxs-lookup"><span data-stu-id="10ec6-123">Getting Hand Tracking</span></span>

<span data-ttu-id="10ec6-124">Você pode usar **GetHandJointTransform** para retornar dados espaciais da mão.</span><span class="sxs-lookup"><span data-stu-id="10ec6-124">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="10ec6-125">Os dados são atualizados a cada quadro, mas se você estiver dentro de um quadro, os valores retornados serão armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="10ec6-125">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="10ec6-126">Não é recomendável ter muita lógica nessa função por motivos de desempenho.</span><span class="sxs-lookup"><span data-stu-id="10ec6-126">It's not recommended to have heavy logic in this function for performance reasons.</span></span>

![Obter transformação conjunta de entrega](../images/unreal/get-hand-joint-transform.png)

<span data-ttu-id="10ec6-128">C++:</span><span class="sxs-lookup"><span data-stu-id="10ec6-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="10ec6-129">Aqui está uma análise dos parâmetros de função do GetHandJointTransform:</span><span class="sxs-lookup"><span data-stu-id="10ec6-129">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="10ec6-130">A **mão** – pode ser os usuários à esquerda ou à direita.</span><span class="sxs-lookup"><span data-stu-id="10ec6-130">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="10ec6-131">**Ponto de extremidade** – o Bone da mão.</span><span class="sxs-lookup"><span data-stu-id="10ec6-131">**Keypoint** – the bone of the hand.</span></span>
* <span data-ttu-id="10ec6-132">**Transformação** – coordenadas e orientação da base do Bone.</span><span class="sxs-lookup"><span data-stu-id="10ec6-132">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="10ec6-133">Você pode solicitar a base do próximo Bone para obter os dados de transformação para o final de um Bone.</span><span class="sxs-lookup"><span data-stu-id="10ec6-133">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="10ec6-134">Um Bone de dica especial dá ao fim do distal.</span><span class="sxs-lookup"><span data-stu-id="10ec6-134">A special Tip bone gives end of distal.</span></span>
* <span data-ttu-id="10ec6-135">\* \* RADIUS — raio da base do Bone.</span><span class="sxs-lookup"><span data-stu-id="10ec6-135">\*\*Radius—radius of the base of the bone.</span></span>
* <span data-ttu-id="10ec6-136">\* \* Valor de retorno — true se o Bone for rastreado neste quadro, false se o Bone não for acompanhado.</span><span class="sxs-lookup"><span data-stu-id="10ec6-136">\*\*Return Value—true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>