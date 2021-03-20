---
title: Acompanhamento da mão no Unreal
description: Saiba como usar a entrada de rastreamento manual, a pose, as malhas à mão e as animações de link ao vivo em aplicativos inreais de realidade misturada.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realidade mista do Windows, acompanhamento manual, inreal, Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade do Windows misturada, headset de realidade virtual
ms.openlocfilehash: 415a0773586ab232e925fd0f18a3a8e6f8217e88
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695793"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="0b815-104">Acompanhamento da mão no Unreal</span><span class="sxs-lookup"><span data-stu-id="0b815-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="0b815-105">O sistema de acompanhamento manual usa Palms e dedos de uma pessoa como entrada.</span><span class="sxs-lookup"><span data-stu-id="0b815-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="0b815-106">Dados na posição e na rotação de cada dedo, todo o Palm e gestos de mão estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0b815-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> <span data-ttu-id="0b815-107">A partir do inreal 4,26, o rastreamento manual é baseado no plug-in HeadMountedDisplay inreal e usa uma API comum em todas as plataformas e dispositivos XR.</span><span class="sxs-lookup"><span data-stu-id="0b815-107">Starting in Unreal 4.26, hand tracking is based on the Unreal HeadMountedDisplay plugin and uses a common API across all XR platforms and devices.</span></span> <span data-ttu-id="0b815-108">A funcionalidade é a mesma para sistemas OpenXR e realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="0b815-108">Functionality is the same for both Windows Mixed Reality and OpenXR systems.</span></span>

## <a name="hand-pose"></a><span data-ttu-id="0b815-109">Pose de mão</span><span class="sxs-lookup"><span data-stu-id="0b815-109">Hand pose</span></span>

<span data-ttu-id="0b815-110">A pose de mão permite que você controle e use as mãos e os dedos de seus usuários como entrada, que podem ser acessados em planos gráficos e em C++.</span><span class="sxs-lookup"><span data-stu-id="0b815-110">Hand pose lets you track and use the hands and fingers of your users as input, which can be accessed in both Blueprints and C++.</span></span> <span data-ttu-id="0b815-111">A API inreal envia os dados como um sistema de coordenadas, com tiques sincronizados com o mecanismo inreal.</span><span class="sxs-lookup"><span data-stu-id="0b815-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

<span data-ttu-id="0b815-112">![Imagem do esqueleto da mão com esqueleto da sobreposição de junções ](images/hand-tracking-img-02.png)
 ![](images/hand-tracking-skeleton-update.png)</span><span class="sxs-lookup"><span data-stu-id="0b815-112">![Hand skeleton image with joints overlay](images/hand-tracking-img-02.png)
![Hand Skeleton](images/hand-tracking-skeleton-update.png)</span></span>

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a><span data-ttu-id="0b815-113">Animação do link ao vivo à mão</span><span class="sxs-lookup"><span data-stu-id="0b815-113">Hand Live Link Animation</span></span>

<span data-ttu-id="0b815-114">As poses de mão são expostas à animação usando o [plug-in de vínculo dinâmico](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span><span class="sxs-lookup"><span data-stu-id="0b815-114">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="0b815-115">Se a realidade mista do Windows e os plug-ins do Live link estiverem habilitados:</span><span class="sxs-lookup"><span data-stu-id="0b815-115">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span>
1. <span data-ttu-id="0b815-116">Selecione **janela > link ao vivo** para abrir a janela do editor de link dinâmico.</span><span class="sxs-lookup"><span data-stu-id="0b815-116">Select **Window > Live Link** to open the Live Link editor window.</span></span>
2. <span data-ttu-id="0b815-117">Selecionar **origem** e habilitar a **fonte de acompanhamento do Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="0b815-117">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![Origem do link dinâmico](images/unreal/live-link-source.png)

<span data-ttu-id="0b815-119">Depois de habilitar a origem e abrir um ativo de animação, expanda a seção **animação** na guia **Visualizar cena** também para ver as opções adicionais.</span><span class="sxs-lookup"><span data-stu-id="0b815-119">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![Animação de link ao vivo](images/unreal/live-link-animation.png)

<span data-ttu-id="0b815-121">A hierarquia de animação da mão é a mesma do `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="0b815-121">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="0b815-122">A animação pode ser redirecionada usando **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span><span class="sxs-lookup"><span data-stu-id="0b815-122">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![Animação de link ao vivo 2](images/unreal/live-link-animation2.png)

<span data-ttu-id="0b815-124">Ele também pode ser subclasse no editor:</span><span class="sxs-lookup"><span data-stu-id="0b815-124">It can also be subclassed in the editor:</span></span>

![Remapeamento de link dinâmico](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a><span data-ttu-id="0b815-126">Malha à mão</span><span class="sxs-lookup"><span data-stu-id="0b815-126">Hand Mesh</span></span>

### <a name="hand-mesh-as-a-tracked-geometry"></a><span data-ttu-id="0b815-127">Malha à mão como uma geometria rastreada</span><span class="sxs-lookup"><span data-stu-id="0b815-127">Hand Mesh as a Tracked Geometry</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b815-128">A obtenção de malhas à mão como uma geometria rastreada no OpenXR exige que você chame **definir a malha de uso** com a geometria de **acompanhamento habilitada**.</span><span class="sxs-lookup"><span data-stu-id="0b815-128">Getting hand meshes as a tracked geometry in OpenXR requires you to call **Set Use Hand Mesh** with **Enabled Tracking Geometry**.</span></span>

<span data-ttu-id="0b815-129">Para habilitar esse modo, você deve chamar **set use mesh** com a **geometria de acompanhamento habilitada**:</span><span class="sxs-lookup"><span data-stu-id="0b815-129">To enable that mode you should call **Set Use Hand Mesh** with **Enabled Tracking Geometry**:</span></span>

![Plano gráfico de início de evento de execução conectado para definir a função de malha manual de uso com o modo de geometria de rastreamento habilitado](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> <span data-ttu-id="0b815-131">Não é possível habilitar ambos os modos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="0b815-131">It’s not possible for both modes to be enabled at the same time.</span></span> <span data-ttu-id="0b815-132">Se você habilitar um, o outro será desabilitado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="0b815-132">If you enable one, the other is automatically disabled.</span></span>

### <a name="accessing-hand-mesh-data"></a><span data-ttu-id="0b815-133">Acessando dados de malha de mão</span><span class="sxs-lookup"><span data-stu-id="0b815-133">Accessing Hand Mesh Data</span></span>

![Malha à mão](images/unreal/hand-mesh.png)

<span data-ttu-id="0b815-135">Antes de poder acessar os dados da malha, você precisará:</span><span class="sxs-lookup"><span data-stu-id="0b815-135">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="0b815-136">Selecione o ativo do **ARSessionConfig** , expanda as configurações do **ar->** configurações de mapeamento do mundo e marque **gerar dados de malha da geometria rastreada**.</span><span class="sxs-lookup"><span data-stu-id="0b815-136">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span>

<span data-ttu-id="0b815-137">Abaixo estão os parâmetros de malha padrão:</span><span class="sxs-lookup"><span data-stu-id="0b815-137">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="0b815-138">Usar dados de malha para oclusão</span><span class="sxs-lookup"><span data-stu-id="0b815-138">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="0b815-139">Gerar colisão para dados de malha</span><span class="sxs-lookup"><span data-stu-id="0b815-139">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="0b815-140">Gerar malha NAV para dados de malha</span><span class="sxs-lookup"><span data-stu-id="0b815-140">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="0b815-141">Renderizar dados de malha em wireframe – parâmetro de depuração que mostra a malha gerada</span><span class="sxs-lookup"><span data-stu-id="0b815-141">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="0b815-142">Esses valores de parâmetro são usados como os padrões de malha de mapeamento espacial e malha de mão.</span><span class="sxs-lookup"><span data-stu-id="0b815-142">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="0b815-143">Você pode alterá-los a qualquer momento em plantas ou código para qualquer malha.</span><span class="sxs-lookup"><span data-stu-id="0b815-143">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="0b815-144">Referência da API do C++</span><span class="sxs-lookup"><span data-stu-id="0b815-144">C++ API Reference</span></span>
<span data-ttu-id="0b815-145">Use `EEARObjectClassification` para localizar valores de malha do lado em todos os objetos rastreáveis.</span><span class="sxs-lookup"><span data-stu-id="0b815-145">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

<span data-ttu-id="0b815-146">Os delegados a seguir são chamados quando o sistema detecta qualquer objeto rastreável, incluindo uma malha à mão.</span><span class="sxs-lookup"><span data-stu-id="0b815-146">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span>

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

<span data-ttu-id="0b815-147">Verifique se os manipuladores delegados seguem a assinatura de função abaixo:</span><span class="sxs-lookup"><span data-stu-id="0b815-147">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="0b815-148">Você pode acessar os dados de malha por meio do  `UARTrackedGeometry::GetUnderlyingMesh` :</span><span class="sxs-lookup"><span data-stu-id="0b815-148">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a><span data-ttu-id="0b815-149">Referência de API de Blueprint</span><span class="sxs-lookup"><span data-stu-id="0b815-149">Blueprint API Reference</span></span>

<span data-ttu-id="0b815-150">Para trabalhar com malhas à mão em plantas:</span><span class="sxs-lookup"><span data-stu-id="0b815-150">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="0b815-151">Adicionar um componente **ARTrackableNotify** a um ator do Blueprint</span><span class="sxs-lookup"><span data-stu-id="0b815-151">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![ARTrackable notificar](images/unreal/ar-trackable-notify.png)

2. <span data-ttu-id="0b815-153">Vá para o painel de **detalhes** e expanda a seção **eventos** .</span><span class="sxs-lookup"><span data-stu-id="0b815-153">Go to the **Details** panel and expand the **Events** section.</span></span>

![Notificação ARTrackable 2](images/unreal/ar-trackable-notify2.png)

3. <span data-ttu-id="0b815-155">Substituir em Adicionar/atualizar/remover geometria rastreada com os seguintes nós em seu grafo de eventos:</span><span class="sxs-lookup"><span data-stu-id="0b815-155">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![Na notificação do ARTrackable](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a><span data-ttu-id="0b815-157">Visualização de malha à mão em OpenXR</span><span class="sxs-lookup"><span data-stu-id="0b815-157">Hand Mesh visualization in OpenXR</span></span>

<span data-ttu-id="0b815-158">A maneira recomendada de visualizar a malha à mão é usar o plug-in XRVisualization do Epic junto com o [plug-in OpenXR da Microsoft](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="0b815-158">The recommended way to visualize hand mesh is to use Epic’s XRVisualization plugin together with the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span> 

<span data-ttu-id="0b815-159">Em seguida, no editor do Blueprint, você deve usar a função de **malha de uso manual** do [plug-in Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal) com o **XRVisualization habilitado** como um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="0b815-159">Then in the blueprint editor, you should use **Set Use Hand Mesh** function from the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) with **Enabled XRVisualization** as a parameter:</span></span>

![Plano gráfico do evento de início de execução conectado para definir a função de malha manual de uso com o modo xrvisualization habilitado](images/unreal-hand-tracking-img-05.png)

<span data-ttu-id="0b815-161">Para gerenciar o processo de renderização, você deve usar o **controlador de movimento de renderização** de XRVisualization:</span><span class="sxs-lookup"><span data-stu-id="0b815-161">To manage the rendering process, you should use **Render Motion Controller** from XRVisualization:</span></span>

![Plano gráfico da função obter dados do controlador de movimento conectado à função renderizar o controlador de movimento](images/unreal-hand-tracking-img-06.png)

<span data-ttu-id="0b815-163">O resultado :</span><span class="sxs-lookup"><span data-stu-id="0b815-163">The result:</span></span>

![Imagem da mão digital sobreposta em uma mão humana real](images/unreal-hand-tracking-img-07.png) 

<span data-ttu-id="0b815-165">Se precisar de algo mais complicado, como desenhar uma malha à mão com um sombreador personalizado, você precisará obter as malhas como uma geometria rastreada.</span><span class="sxs-lookup"><span data-stu-id="0b815-165">If you need anything more complicated, such as drawing a hand mesh with a custom shader, you need to get the meshes as a tracked geometry.</span></span> 

## <a name="hand-rays"></a><span data-ttu-id="0b815-166">Raios de mão</span><span class="sxs-lookup"><span data-stu-id="0b815-166">Hand rays</span></span>

<span data-ttu-id="0b815-167">A obtenção de entrega manual funciona para as interações próximas, como a captura de objetos ou o pressionamento de botões.</span><span class="sxs-lookup"><span data-stu-id="0b815-167">Getting hand pose works for close interactions like grabbing objects or pressing buttons.</span></span> <span data-ttu-id="0b815-168">No entanto, às vezes você precisa trabalhar com hologramas que estão longe de seus usuários.</span><span class="sxs-lookup"><span data-stu-id="0b815-168">However, sometimes you need to work with holograms that are far away from your users.</span></span> <span data-ttu-id="0b815-169">Isso pode ser feito com raios de mão, que podem ser usados como dispositivos apontadores em C++ e em planos gráficos.</span><span class="sxs-lookup"><span data-stu-id="0b815-169">This can be accomplished with hand rays, which can be used as pointing devices in both C++ and Blueprints.</span></span> <span data-ttu-id="0b815-170">Você pode desenhar um raio a partir de sua mão até um ponto distante e, com alguma ajuda de rastreamento de Ray não real, selecionar um holograma que, de outra forma, estaria fora do alcance.</span><span class="sxs-lookup"><span data-stu-id="0b815-170">You can draw a ray from your hand to a far point and, with some help from Unreal ray tracing, select a hologram that would otherwise be out of reach.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="0b815-171">Como todos os resultados da função alteram todos os quadros, todos eles se tornaram chamáveis.</span><span class="sxs-lookup"><span data-stu-id="0b815-171">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="0b815-172">Para obter mais informações sobre funções puras e impuras ou que podem ser chamadas, consulte o GUID do usuário do Blueprint em [funções](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span><span class="sxs-lookup"><span data-stu-id="0b815-172">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a><span data-ttu-id="0b815-173">Gestos</span><span class="sxs-lookup"><span data-stu-id="0b815-173">Gestures</span></span>

<span data-ttu-id="0b815-174">O HoloLens 2 rastreia gestos espaciais, o que significa que você pode capturar esses gestos como entrada.</span><span class="sxs-lookup"><span data-stu-id="0b815-174">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="0b815-175">O rastreamento de gestos é baseado em um modelo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="0b815-175">Gesture tracking is based on a subscription model.</span></span> <span data-ttu-id="0b815-176">Você deve usar a função "configurar gestos" para informar ao dispositivo quais gestos você deseja rastrear.  Você pode encontrar mais detalhes sobre gestos são o documento de [uso básico do HoloLens 2](/hololens/hololens2-basic-usage) .</span><span class="sxs-lookup"><span data-stu-id="0b815-176">You should use the “Configure Gestures” function to tell the device which gestures you want to track.  You can find more details about gestures are the [HoloLens 2 Basic Usage](/hololens/hololens2-basic-usage) document.</span></span>

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="0b815-177">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="0b815-177">Next Development Checkpoint</span></span>

<span data-ttu-id="0b815-178">Se está seguindo o percurso de desenvolvimento do Unreal que estabelecemos, você está no meio da exploração dos principais blocos de construção do MRTK.</span><span class="sxs-lookup"><span data-stu-id="0b815-178">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="0b815-179">Deste ponto, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="0b815-179">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b815-180">Âncoras Espaciais locais</span><span class="sxs-lookup"><span data-stu-id="0b815-180">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="0b815-181">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="0b815-181">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b815-182">Câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="0b815-182">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="0b815-183">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="0b815-183">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>