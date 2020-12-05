---
title: Acompanhamento da mão no Unreal
description: Explica como usar o rastreamento manual em não real
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realidade mista do Windows, acompanhamento manual, inreal, Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade do Windows misturada, headset de realidade virtual
ms.openlocfilehash: 4c66e2353c1e881c05541fd0fe9eafa553ea5c23
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609707"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="7e0c8-104">Acompanhamento da mão no Unreal</span><span class="sxs-lookup"><span data-stu-id="7e0c8-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="7e0c8-105">O sistema de acompanhamento manual usa Palms e dedos de uma pessoa como entrada.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="7e0c8-106">Dados na posição e na rotação de cada dedo, todo o Palm e gestos de mão estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="7e0c8-107">Pose de mão</span><span class="sxs-lookup"><span data-stu-id="7e0c8-107">Hand Pose</span></span>

<span data-ttu-id="7e0c8-108">A pose de mão permite que você acompanhe e use as mãos e os dedos de seus usuários como entrada.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-108">Hand pose lets you track and use the hands and fingers of your users as input.</span></span> <span data-ttu-id="7e0c8-109">Você pode acessar dados de rastreamento em plantas e em C++.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-109">You can access tracking data both in Blueprints and C++.</span></span> <span data-ttu-id="7e0c8-110">Você pode encontrar mais detalhes técnicos na API inreal do [Windows. percepção. People. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) .</span><span class="sxs-lookup"><span data-stu-id="7e0c8-110">You can find more technical details in Unreal's [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API.</span></span> <span data-ttu-id="7e0c8-111">A API inreal envia os dados como um sistema de coordenadas, com tiques sincronizados com o mecanismo inreal.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

### <a name="understanding-the-bone-hierarchy"></a><span data-ttu-id="7e0c8-112">Compreendendo a hierarquia do Bone</span><span class="sxs-lookup"><span data-stu-id="7e0c8-112">Understanding the bone hierarchy</span></span>

<span data-ttu-id="7e0c8-113">A `EWMRHandKeypoint` Enumeração descreve a hierarquia do Bone da mão.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-113">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="7e0c8-114">Você pode encontrar cada ponto de extremidade à mão listado em seus planos gráficos:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-114">You can find each hand keypoint listed in your Blueprints:</span></span>

![Mão keypoint BP](images/hand-keypoint-bp.png)

<span data-ttu-id="7e0c8-116">A enumeração C++ completa está listada abaixo:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-116">The full C++ enum is listed below:</span></span>
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

<span data-ttu-id="7e0c8-117">Você pode encontrar os valores numéricos para cada caso de enum na tabela [Windows. percepção. People. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) .</span><span class="sxs-lookup"><span data-stu-id="7e0c8-117">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span> <span data-ttu-id="7e0c8-118">Todo o layout de pose de mão com casos de enumeração correspondentes é mostrado na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-118">The entire hand pose layout with matching enum cases is shown in the image below:</span></span>

![Esqueleto da mão](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a><span data-ttu-id="7e0c8-120">Acompanhamento de suporte à mão</span><span class="sxs-lookup"><span data-stu-id="7e0c8-120">Supporting Hand Tracking</span></span>

<span data-ttu-id="7e0c8-121">Você pode usar o rastreamento manual em plantas adicionando **suporte ao rastreamento** à mão **> realidade mista do Windows**:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-121">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![Controle à mão BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="7e0c8-123">Essa função retornará `true` se o controle à mão tiver suporte no dispositivo e `false` se o rastreamento à mão não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-123">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![Dá suporte ao controle à mão BP](images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="7e0c8-125">C++:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-125">C++:</span></span> 

<span data-ttu-id="7e0c8-126">Inclua `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-126">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="7e0c8-127">Obtendo controle à mão</span><span class="sxs-lookup"><span data-stu-id="7e0c8-127">Getting Hand Tracking</span></span>

<span data-ttu-id="7e0c8-128">Você pode usar **GetHandJointTransform** para retornar dados espaciais da mão.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-128">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="7e0c8-129">Os dados são atualizados a cada quadro, mas se você estiver dentro de um quadro, os valores retornados serão armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-129">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="7e0c8-130">Não é recomendável ter muita lógica nessa função por motivos de desempenho.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-130">It's not recommended to have heavy logic in this function for performance reasons.</span></span> 

![Obter transformação conjunta de entrega](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="7e0c8-132">C++:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-132">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="7e0c8-133">Aqui está uma análise dos parâmetros de função do GetHandJointTransform:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-133">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="7e0c8-134">A **mão** – pode ser os usuários à esquerda ou à direita.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-134">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="7e0c8-135">**Ponto de extremidade** – o Bone da mão.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-135">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="7e0c8-136">**Transformação** – coordenadas e orientação da base do Bone.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-136">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="7e0c8-137">Você pode solicitar a base do próximo Bone para obter os dados de transformação para o final de um Bone.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-137">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="7e0c8-138">Um Bone de dica especial dá ao fim do distal.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-138">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="7e0c8-139">**RADIUS** — raio da base do Bone.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-139">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="7e0c8-140">**Valor de retorno** — true se o Bone for rastreado neste quadro, false se o Bone não for acompanhado.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-140">**Return Value** — true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="7e0c8-141">Animação do link ao vivo à mão</span><span class="sxs-lookup"><span data-stu-id="7e0c8-141">Hand Live Link Animation</span></span>

<span data-ttu-id="7e0c8-142">As poses de mão são expostas à animação usando o [plug-in de vínculo dinâmico](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span><span class="sxs-lookup"><span data-stu-id="7e0c8-142">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="7e0c8-143">Se a realidade mista do Windows e os plug-ins do Live link estiverem habilitados:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-143">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span> 
1. <span data-ttu-id="7e0c8-144">Selecione **janela > link ao vivo** para abrir a janela do editor de link dinâmico.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-144">Select **Window > Live Link** to open the Live Link editor window.</span></span> 
2. <span data-ttu-id="7e0c8-145">Selecionar **origem** e habilitar a **fonte de acompanhamento do Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="7e0c8-145">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![Origem do link dinâmico](images/unreal/live-link-source.png)
 
<span data-ttu-id="7e0c8-147">Depois de habilitar a origem e abrir um ativo de animação, expanda a seção **animação** na guia **Visualizar cena** também para ver as opções adicionais.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-147">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![Animação de link ao vivo](images/unreal/live-link-animation.png)
 
<span data-ttu-id="7e0c8-149">A hierarquia de animação da mão é a mesma do `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="7e0c8-149">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="7e0c8-150">A animação pode ser redirecionada usando **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-150">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![Animação de link ao vivo 2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="7e0c8-152">Ele também pode ser subclasse no editor:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-152">It can also be subclassed in the editor:</span></span>

![Remapeamento de link dinâmico](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a><span data-ttu-id="7e0c8-154">Acessando dados de malha de mão</span><span class="sxs-lookup"><span data-stu-id="7e0c8-154">Accessing Hand Mesh Data</span></span>

![Malha à mão](images/unreal/hand-mesh.png)

<span data-ttu-id="7e0c8-156">Antes de poder acessar os dados da malha, você precisará:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-156">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="7e0c8-157">Selecione o ativo do **ARSessionConfig** , expanda as configurações do **ar->** configurações de mapeamento do mundo e marque **gerar dados de malha da geometria rastreada**.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-157">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span> 

<span data-ttu-id="7e0c8-158">Abaixo estão os parâmetros de malha padrão:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-158">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="7e0c8-159">Usar dados de malha para oclusão</span><span class="sxs-lookup"><span data-stu-id="7e0c8-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="7e0c8-160">Gerar colisão para dados de malha</span><span class="sxs-lookup"><span data-stu-id="7e0c8-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="7e0c8-161">Gerar malha NAV para dados de malha</span><span class="sxs-lookup"><span data-stu-id="7e0c8-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="7e0c8-162">Renderizar dados de malha em wireframe – parâmetro de depuração que mostra a malha gerada</span><span class="sxs-lookup"><span data-stu-id="7e0c8-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="7e0c8-163">Esses valores de parâmetro são usados como os padrões de malha de mapeamento espacial e malha de mão.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-163">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="7e0c8-164">Você pode alterá-los a qualquer momento em plantas ou código para qualquer malha.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-164">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="7e0c8-165">Referência da API do C++</span><span class="sxs-lookup"><span data-stu-id="7e0c8-165">C++ API Reference</span></span> 
<span data-ttu-id="7e0c8-166">Use `EEARObjectClassification` para localizar valores de malha do lado em todos os objetos rastreáveis.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-166">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

<span data-ttu-id="7e0c8-167">Os delegados a seguir são chamados quando o sistema detecta qualquer objeto rastreável, incluindo uma malha à mão.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-167">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

<span data-ttu-id="7e0c8-168">Verifique se os manipuladores delegados seguem a assinatura de função abaixo:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-168">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="7e0c8-169">Você pode acessar os dados de malha por meio do  `UARTrackedGeometry::GetUnderlyingMesh` :</span><span class="sxs-lookup"><span data-stu-id="7e0c8-169">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a><span data-ttu-id="7e0c8-170">Referência de API de Blueprint</span><span class="sxs-lookup"><span data-stu-id="7e0c8-170">Blueprint API Reference</span></span>

<span data-ttu-id="7e0c8-171">Para trabalhar com malhas à mão em plantas:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-171">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="7e0c8-172">Adicionar um componente **ARTrackableNotify** a um ator do Blueprint</span><span class="sxs-lookup"><span data-stu-id="7e0c8-172">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![ARTrackable notificar](images/unreal/ar-trackable-notify.png)
 
2. <span data-ttu-id="7e0c8-174">Vá para o painel de **detalhes** e expanda a seção **eventos** .</span><span class="sxs-lookup"><span data-stu-id="7e0c8-174">Go to the **Details** panel and expand the **Events** section.</span></span> 

![Notificação ARTrackable 2](images/unreal/ar-trackable-notify2.png)
 
3. <span data-ttu-id="7e0c8-176">Substituir em Adicionar/atualizar/remover geometria rastreada com os seguintes nós em seu grafo de eventos:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-176">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![Na notificação do ARTrackable](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="7e0c8-178">Raios de mão</span><span class="sxs-lookup"><span data-stu-id="7e0c8-178">Hand Rays</span></span>

<span data-ttu-id="7e0c8-179">Você pode usar um raio de mão como um dispositivo apontador em C++ e plantas, que expõem a API [Windows. UI. Input. Spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) .</span><span class="sxs-lookup"><span data-stu-id="7e0c8-179">You can use a hand ray as a pointing device in both C++ and Blueprints, which exposes the [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e0c8-180">Como todos os resultados da função alteram todos os quadros, todos eles se tornaram chamáveis.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-180">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="7e0c8-181">Para obter mais informações sobre funções puras e impuras ou que podem ser chamadas, consulte o GUID do usuário do Blueprint em [funções](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span><span class="sxs-lookup"><span data-stu-id="7e0c8-181">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

<span data-ttu-id="7e0c8-182">Para usar raios de mão em plantas, pesquise qualquer uma das ações em **HMD de realidade mista do Windows**:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-182">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![Raios-mão BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="7e0c8-184">Para acessá-los em C++, inclua na `WindowsMixedRealityFunctionLibrary.h` parte superior do seu arquivo de código de chamada.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-184">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="7e0c8-185">Enumeração</span><span class="sxs-lookup"><span data-stu-id="7e0c8-185">Enum</span></span>

<span data-ttu-id="7e0c8-186">Você também tem acesso a casos de entrada em **EHMDInputControllerButtons**, que podem ser usados em plantas:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-186">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![Botões do controlador de entrada](images/unreal/input-controller-buttons.png)

<span data-ttu-id="7e0c8-188">Para acesso em C++, use a `EHMDInputControllerButtons` classe enum:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-188">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="7e0c8-189">Abaixo está uma análise dos dois casos de enumeração aplicáveis:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-189">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="7e0c8-190">**Select** -o evento de seleção disparado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-190">**Select** - User triggered Select event.</span></span> 
    * <span data-ttu-id="7e0c8-191">Disparado no HoloLens 2 por Air-TAP, olhar e Commit ou dizendo "Select" com [entrada de voz](unreal-voice-input.md) habilitada.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-191">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](unreal-voice-input.md) enabled.</span></span> 
* <span data-ttu-id="7e0c8-192">**Segure** -evento de Segure disparado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-192">**Grasp** - User triggered Grasp event.</span></span> 
    * <span data-ttu-id="7e0c8-193">Disparado no HoloLens 2 fechando os dedos do usuário em um holograma.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-193">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 

<span data-ttu-id="7e0c8-194">Você pode acessar o status de acompanhamento da malha do seu lado em C++ por meio da `EHMDTrackingStatus` Enumeração mostrada abaixo:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-194">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="7e0c8-195">Abaixo está uma análise dos dois casos de enumeração aplicáveis:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-195">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="7e0c8-196">Não **rastreado** – a mão não está visível</span><span class="sxs-lookup"><span data-stu-id="7e0c8-196">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="7e0c8-197">**Acompanhado** – a mão é totalmente controlada</span><span class="sxs-lookup"><span data-stu-id="7e0c8-197">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="7e0c8-198">Estrutura</span><span class="sxs-lookup"><span data-stu-id="7e0c8-198">Struct</span></span>

<span data-ttu-id="7e0c8-199">A estrutura PointerPoseInfo pode fornecer informações sobre os seguintes dados de mão:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-199">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="7e0c8-200">**Origem** – origem da mão</span><span class="sxs-lookup"><span data-stu-id="7e0c8-200">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="7e0c8-201">**Direção** – direção da mão</span><span class="sxs-lookup"><span data-stu-id="7e0c8-201">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="7e0c8-202">**Up** – vetor de cima à mão</span><span class="sxs-lookup"><span data-stu-id="7e0c8-202">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="7e0c8-203">**Orientação** – o quaternion de orientação</span><span class="sxs-lookup"><span data-stu-id="7e0c8-203">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="7e0c8-204">**Status de rastreamento** – status de acompanhamento atual</span><span class="sxs-lookup"><span data-stu-id="7e0c8-204">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="7e0c8-205">Você pode acessar a estrutura PointerPoseInfo por meio de plantas, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-205">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![Ponteiro de pose de informações BP](images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="7e0c8-207">Ou com C++:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-207">Or with C++:</span></span>

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

### <a name="functions"></a><span data-ttu-id="7e0c8-208">Funções</span><span class="sxs-lookup"><span data-stu-id="7e0c8-208">Functions</span></span>

<span data-ttu-id="7e0c8-209">Todas as funções listadas abaixo podem ser chamadas em cada quadro, o que permite o monitoramento contínuo.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-209">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span> 

1. <span data-ttu-id="7e0c8-210">**Obter** informações de pose de ponteiro retorna informações completas sobre a direção de raio da mão no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-210">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span> 

<span data-ttu-id="7e0c8-211">Gráfico</span><span class="sxs-lookup"><span data-stu-id="7e0c8-211">Blueprint:</span></span>

![Obter informações de pose de ponteiro](images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="7e0c8-213">C++:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-213">C++:</span></span> 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="7e0c8-214">**É Segure** retorna true se a mão estiver segurando no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-214">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="7e0c8-215">Gráfico</span><span class="sxs-lookup"><span data-stu-id="7e0c8-215">Blueprint:</span></span>

![BP é compreendida](images/unreal/is-grasped-bp.png)

<span data-ttu-id="7e0c8-217">C++:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-217">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. <span data-ttu-id="7e0c8-218">**Is Select pressionado** retorna true se o usuário disparasse SELECT no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-218">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="7e0c8-219">Gráfico</span><span class="sxs-lookup"><span data-stu-id="7e0c8-219">Blueprint:</span></span>

![É selecione BP pressionado](images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="7e0c8-221">C++:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-221">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="7e0c8-222">O **botão é clicado** retorna true se o evento ou botão for disparado no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-222">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="7e0c8-223">Gráfico</span><span class="sxs-lookup"><span data-stu-id="7e0c8-223">Blueprint:</span></span>

![É um botão clicado em BP](images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="7e0c8-225">C++:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-225">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="7e0c8-226">**Obter status de controle do controlador** retorna o status de acompanhamento no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-226">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="7e0c8-227">Gráfico</span><span class="sxs-lookup"><span data-stu-id="7e0c8-227">Blueprint:</span></span>

![Obter o status de controle do controlador BP](images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="7e0c8-229">C++:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-229">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a><span data-ttu-id="7e0c8-230">Gestos</span><span class="sxs-lookup"><span data-stu-id="7e0c8-230">Gestures</span></span>

<span data-ttu-id="7e0c8-231">O HoloLens 2 rastreia gestos espaciais, o que significa que você pode capturar esses gestos como entrada.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-231">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="7e0c8-232">Você pode encontrar mais detalhes sobre gestos são o documento de [uso básico do HoloLens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .</span><span class="sxs-lookup"><span data-stu-id="7e0c8-232">You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

<span data-ttu-id="7e0c8-233">Você pode encontrar a função Blueprint na **entrada espacial de realidade mista do Windows** e a função C++ adicionando o `WindowsMixedRealitySpatialInputFunctionLibrary.h` arquivo de código de chamada.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-233">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![Gestos de captura](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="7e0c8-235">Enumeração</span><span class="sxs-lookup"><span data-stu-id="7e0c8-235">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="7e0c8-236">Gráfico</span><span class="sxs-lookup"><span data-stu-id="7e0c8-236">Blueprint:</span></span> 

![Tipo de gesto](images/unreal/gesture-type.png)

<span data-ttu-id="7e0c8-238">C++:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-238">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="7e0c8-239">Função</span><span class="sxs-lookup"><span data-stu-id="7e0c8-239">Function</span></span>
<span data-ttu-id="7e0c8-240">Você pode habilitar e desabilitar a captura de gestos com a `CaptureGestures` função.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-240">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="7e0c8-241">Quando um gesto habilitado aciona eventos de entrada, a função retorna `true` se a captura do gesto foi bem-sucedida e, `false` se houver um erro.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-241">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="7e0c8-242">Gráfico</span><span class="sxs-lookup"><span data-stu-id="7e0c8-242">Blueprint:</span></span>

![Gestos de captura BP](images/unreal/capture-gestures-bp.png)

<span data-ttu-id="7e0c8-244">C++:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-244">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

<span data-ttu-id="7e0c8-245">Veja a seguir os principais eventos, que você pode encontrar em plantas e C++: ![ principais eventos](images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="7e0c8-245">The following are key events, which you can find in Blueprints and C++: ![Key Events](images/unreal/key-events.png)</span></span>

![Principais eventos 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a><span data-ttu-id="7e0c8-247">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="7e0c8-247">Next Development Checkpoint</span></span>

<span data-ttu-id="7e0c8-248">Se você estiver seguindo a jornada de desenvolvimento inreal que apresentamos, você está no meio da exploração dos blocos de construção do MRTK Core.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-248">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="7e0c8-249">A partir daqui, você pode continuar para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-249">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="7e0c8-250">Âncoras Espaciais locais</span><span class="sxs-lookup"><span data-stu-id="7e0c8-250">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="7e0c8-251">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="7e0c8-251">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7e0c8-252">Câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="7e0c8-252">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="7e0c8-253">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="7e0c8-253">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>