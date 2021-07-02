---
title: Acompanhamento da mão
description: Documentação sobre como usar o HandTracking no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, acompanhamento à mão,
ms.openlocfilehash: 68e936cb4121027008f37aae72496fe59445b636
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176893"
---
# <a name="hand-tracking"></a><span data-ttu-id="f429a-104">Acompanhamento da mão</span><span class="sxs-lookup"><span data-stu-id="f429a-104">Hand tracking</span></span>

## <a name="hand-tracking-profile"></a><span data-ttu-id="f429a-105">Perfil de acompanhamento à mão</span><span class="sxs-lookup"><span data-stu-id="f429a-105">Hand tracking profile</span></span>

<span data-ttu-id="f429a-106">O _perfil de rastreamento de mão_ é encontrado no _perfil do sistema de entrada_.</span><span class="sxs-lookup"><span data-stu-id="f429a-106">The _Hand Tracking profile_ is found under the _Input System profile_.</span></span> <span data-ttu-id="f429a-107">Ele contém configurações para personalizar a representação manual.</span><span class="sxs-lookup"><span data-stu-id="f429a-107">It contains settings for customizing hand representation.</span></span>

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a><span data-ttu-id="f429a-108">Pré-fabricados conjunta</span><span class="sxs-lookup"><span data-stu-id="f429a-108">Joint prefabs</span></span>

<span data-ttu-id="f429a-109">As pré-fabricados conjuntas são visualizadas usando pré-fabricados simples.</span><span class="sxs-lookup"><span data-stu-id="f429a-109">Joint prefabs are visualized using simple prefabs.</span></span> <span data-ttu-id="f429a-110">As junções de _palmeira_ e de _índice_ são de importância especial e têm seu próprio pré-fabricado, enquanto todas as outras junções compartilham o mesmo pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="f429a-110">The _Palm_ and _Index Finger_ joints are of special importance and have their own prefab, while all other joints share the same prefab.</span></span>

<span data-ttu-id="f429a-111">Por padrão, as pré-fabricados conjuntas de mão são primitivos geométricos simples.</span><span class="sxs-lookup"><span data-stu-id="f429a-111">By default the hand joint prefabs are simple geometric primitives.</span></span> <span data-ttu-id="f429a-112">Eles podem ser substituídos, se desejado.</span><span class="sxs-lookup"><span data-stu-id="f429a-112">These can be replaced if desired.</span></span> <span data-ttu-id="f429a-113">Se nenhum pré-fabricado for especificado, os [Gameobjects](https://docs.unity3d.com/ScriptReference/GameObject.html) vazios serão criados em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f429a-113">If no prefab is specified at all, empty [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) are created instead.</span></span>

> [!WARNING]
> <span data-ttu-id="f429a-114">Evite usar scripts complexos ou processamentos caros em pré-fabricados conjuntas, pois os objetos conjuntas são transformados em todos os quadros e podem ter um custo de desempenho significativo!</span><span class="sxs-lookup"><span data-stu-id="f429a-114">Avoid using complex scripts or expensive rendering in joint prefabs, since joint objects are transformed on every frame and can have significant performance cost!</span></span>

<span data-ttu-id="f429a-115">Representação conjunta padrão</span><span class="sxs-lookup"><span data-stu-id="f429a-115">Default Hand Joint Representation</span></span> |  <span data-ttu-id="f429a-116">Rótulos conjuntas</span><span class="sxs-lookup"><span data-stu-id="f429a-116">Joint Labels</span></span>
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a><span data-ttu-id="f429a-117">Pré-fabricado de malha à mão</span><span class="sxs-lookup"><span data-stu-id="f429a-117">Hand mesh prefab</span></span>

<span data-ttu-id="f429a-118">A malha à mão será usada se os dados de malha totalmente definidos forem fornecidos pelo dispositivo de rastreamento manual.</span><span class="sxs-lookup"><span data-stu-id="f429a-118">The hand mesh is used if fully defined mesh data is provided by the hand tracking device.</span></span> <span data-ttu-id="f429a-119">A malha renderizada no pré-fabricado é substituída pelos dados do dispositivo, portanto, uma malha fictícia, como um cubo, é suficiente.</span><span class="sxs-lookup"><span data-stu-id="f429a-119">The mesh renderable in the prefab is replaced by data from the device, so a dummy mesh such as a cube is sufficient.</span></span> <span data-ttu-id="f429a-120">O material do pré-fabricado é usado para a malha de mão.</span><span class="sxs-lookup"><span data-stu-id="f429a-120">The material of the prefab is used for the hand mesh.</span></span>

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

<span data-ttu-id="f429a-121">A exibição de malha à mão pode ter um impacto perceptível no desempenho, por esse motivo, ela pode ser totalmente desativada desmarcando a opção **habilitar visualização de malha à mão** .</span><span class="sxs-lookup"><span data-stu-id="f429a-121">Hand mesh display can have a noticeable performance impact, for this reason it can be disabled entirely by unchecking **Enable Hand Mesh Visualization** option.</span></span>

## <a name="hand-visualization-settings"></a><span data-ttu-id="f429a-122">Configurações de visualização da mão</span><span class="sxs-lookup"><span data-stu-id="f429a-122">Hand visualization settings</span></span>

<span data-ttu-id="f429a-123">A malha de mão e as visualizações conjuntas podem ser desativadas ou ativadas por meio da configuração dos *modos de visualização de malha à* mão e *modos de visualização conjunta* , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f429a-123">The hand mesh and hand joint visualizations can be turned off or on via the *Hand Mesh Visualization Modes* setting and *Hand Joint Visualization Modes* respectively.</span></span> <span data-ttu-id="f429a-124">Essas configurações são específicas do modo de aplicativo, o que significa que é possível ativar alguns recursos enquanto estiver no editor (para ver as junções com a simulação no editor, por exemplo) enquanto têm os mesmos recursos desativados quando implantados no dispositivo (em builds de Player).</span><span class="sxs-lookup"><span data-stu-id="f429a-124">These settings are application-mode specific, meaning it is possible to turn on some features while in editor (to see joints with in-editor simulation, for example) while having the same features turned off when deployed to device (in player builds).</span></span>

<span data-ttu-id="f429a-125">Observe que, em geral, é recomendável ter a visualização conjunta configurada no editor (para que a simulação do editor mostre onde estão as junções de mão) e ter a visualização conjunta e a visualização de malha à mão desativada no Player (porque elas incorrem em um impacto no desempenho).</span><span class="sxs-lookup"><span data-stu-id="f429a-125">Note that it's generally recommended to have hand joint visualization turned on in editor (so that in-editor simulation will show where the hand joints are), and to have both hand joint visualization and hand mesh visualization turned off in player (because they incur a performance hit).</span></span>

## <a name="scripting"></a><span data-ttu-id="f429a-126">Scripting</span><span class="sxs-lookup"><span data-stu-id="f429a-126">Scripting</span></span>

<span data-ttu-id="f429a-127">A posição e a rotação podem ser solicitadas no sistema de entrada para cada conjunto individual de cada mão como um [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .</span><span class="sxs-lookup"><span data-stu-id="f429a-127">Position and rotation can be requested from the input system for each individual hand joint as a [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="f429a-128">Como alternativa, o sistema permite o acesso ao [Gameobjects](https://docs.unity3d.com/ScriptReference/GameObject.html) que segue as junções.</span><span class="sxs-lookup"><span data-stu-id="f429a-128">Alternatively the system allows access to [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) that follow the joints.</span></span> <span data-ttu-id="f429a-129">Isso pode ser útil se outro gameobject deve acompanhar um conjunto continuamente.</span><span class="sxs-lookup"><span data-stu-id="f429a-129">This can be useful if another GameObject should track a joint continuously.</span></span>

<span data-ttu-id="f429a-130">As junções disponíveis são listadas na [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enumeração.</span><span class="sxs-lookup"><span data-stu-id="f429a-130">Available joints are listed in the [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enum.</span></span>

> [!NOTE]
> <span data-ttu-id="f429a-131">O objeto conjunta é destruído quando o rastreamento à mão é perdido!</span><span class="sxs-lookup"><span data-stu-id="f429a-131">Joint object are destroyed when hand tracking is lost!</span></span> <span data-ttu-id="f429a-132">Certifique-se de que todos os scripts que usam o objeto conjunta manipulem o `null` caso normalmente para evitar erros!</span><span class="sxs-lookup"><span data-stu-id="f429a-132">Make sure that any scripts using the joint object handle the `null` case gracefully to avoid errors!</span></span>

### <a name="accessing-a-given-hand-controller"></a><span data-ttu-id="f429a-133">Acessando um determinado controlador</span><span class="sxs-lookup"><span data-stu-id="f429a-133">Accessing a given hand controller</span></span>

<span data-ttu-id="f429a-134">Um controlador de mão específico geralmente está disponível, por exemplo, ao manipular eventos de entrada.</span><span class="sxs-lookup"><span data-stu-id="f429a-134">A specific hand controller is often available, e.g. when handling input events.</span></span> <span data-ttu-id="f429a-135">Nesse caso, os dados conjuntas podem ser solicitados diretamente do dispositivo, usando a [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.</span><span class="sxs-lookup"><span data-stu-id="f429a-135">In this case the joint data can be requested directly from the device, using the [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.</span></span>

#### <a name="polling-joint-pose-from-controller"></a><span data-ttu-id="f429a-136">Sondagem conjunta de pose do controlador</span><span class="sxs-lookup"><span data-stu-id="f429a-136">Polling joint pose from controller</span></span>

<span data-ttu-id="f429a-137">A [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) função retornará `false` se a junção solicitada não estiver disponível por algum motivo.</span><span class="sxs-lookup"><span data-stu-id="f429a-137">The [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) function returns `false` if the requested joint is not available for some reason.</span></span> <span data-ttu-id="f429a-138">Nesse caso, a pose resultante será [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .</span><span class="sxs-lookup"><span data-stu-id="f429a-138">In that case the resulting pose will be [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var hand = eventData.Controller as IMixedRealityHand;
  if (hand != null)
  {
    if (hand.TryGetJoint(TrackedHandJoint.IndexTip, out MixedRealityPose jointPose)
    {
      // ...
    }
  }
}
```

#### <a name="joint-transform-from-hand-visualizer"></a><span data-ttu-id="f429a-139">Transformação conjunta do Visualizador de mão</span><span class="sxs-lookup"><span data-stu-id="f429a-139">Joint transform from hand visualizer</span></span>

<span data-ttu-id="f429a-140">Objetos conjuntas podem ser solicitados no [Visualizador do controlador](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span><span class="sxs-lookup"><span data-stu-id="f429a-140">Joint objects can be requested from the [controller visualizer](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var handVisualizer = eventData.Controller.Visualizer as IMixedRealityHandVisualizer;
  if (handVisualizer != null)
  {
    if (handVisualizer.TryGetJointTransform(TrackedHandJoint.IndexTip, out Transform jointTransform)
    {
      // ...
    }
  }
}
```

### <a name="simplified-joint-data-access"></a><span data-ttu-id="f429a-141">Acesso a dados em conjunto simplificado</span><span class="sxs-lookup"><span data-stu-id="f429a-141">Simplified joint data access</span></span>

<span data-ttu-id="f429a-142">Se nenhum controlador específico for fornecido, as classes utilitárias serão fornecidas para acesso conveniente aos dados conjuntas.</span><span class="sxs-lookup"><span data-stu-id="f429a-142">If no specific controller is given then utility classes are provided for convenient access to hand joint data.</span></span> <span data-ttu-id="f429a-143">Essas funções solicitam dados conjuntas do primeiro dispositivo disponível atualmente controlado.</span><span class="sxs-lookup"><span data-stu-id="f429a-143">These functions request joint data from the first available hand device currently tracked.</span></span>

#### <a name="polling-joint-pose-from-handjointutils"></a><span data-ttu-id="f429a-144">Sondagem em conjunto de HandJointUtils</span><span class="sxs-lookup"><span data-stu-id="f429a-144">Polling joint pose from HandJointUtils</span></span>

<span data-ttu-id="f429a-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) é uma classe estática que consulta o primeiro dispositivo ativo de mão.</span><span class="sxs-lookup"><span data-stu-id="f429a-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) is a static class that queries the first active hand device.</span></span>

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a><span data-ttu-id="f429a-146">Transformação conjunta do serviço de conjunto de mão</span><span class="sxs-lookup"><span data-stu-id="f429a-146">Joint transform from hand joint service</span></span>

<span data-ttu-id="f429a-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) mantém um conjunto persistente de [Gameobjects](https://docs.unity3d.com/ScriptReference/GameObject.html) para acompanhamento de junções.</span><span class="sxs-lookup"><span data-stu-id="f429a-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) keeps a persistent set of [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) for tracking joints.</span></span>

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a><span data-ttu-id="f429a-148">Eventos de acompanhamento de mão</span><span class="sxs-lookup"><span data-stu-id="f429a-148">Hand tracking events</span></span>

<span data-ttu-id="f429a-149">O sistema de entrada também fornece eventos, se a sondagem de dados de controladores diretamente não for desejável.</span><span class="sxs-lookup"><span data-stu-id="f429a-149">The input system provides events as well, if polling data from controllers directly is not desirable.</span></span>

#### <a name="joint-events"></a><span data-ttu-id="f429a-150">Eventos conjuntas</span><span class="sxs-lookup"><span data-stu-id="f429a-150">Joint events</span></span>

<span data-ttu-id="f429a-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) lida com atualizações de posições conjuntas.</span><span class="sxs-lookup"><span data-stu-id="f429a-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) handles updates of joint positions.</span></span>

```c#
public class MyHandJointEventHandler : IMixedRealityHandJointHandler
{
    public Handedness myHandedness;

    void IMixedRealityHandJointHandler.OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            if (eventData.InputData.TryGetValue(TrackedHandJoint.IndexTip, out MixedRealityPose pose))
            {
                // ...
            }
        }
    }
}
```

#### <a name="mesh-events"></a><span data-ttu-id="f429a-152">Eventos de malha</span><span class="sxs-lookup"><span data-stu-id="f429a-152">Mesh events</span></span>

<span data-ttu-id="f429a-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) lida com alterações da malha lado articulada.</span><span class="sxs-lookup"><span data-stu-id="f429a-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) handles changes of the articulated hand mesh.</span></span>

<span data-ttu-id="f429a-154">Observe que as malhas à mão não estão habilitadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="f429a-154">Note that hand meshes are not enabled by default.</span></span>

```c#
public class MyHandMeshEventHandler : IMixedRealityHandMeshHandler
{
    public Handedness myHandedness;
    public Mesh myMesh;

    public void OnHandMeshUpdated(InputEventData<HandMeshInfo> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            myMesh.vertices = eventData.InputData.vertices;
            myMesh.normals = eventData.InputData.normals;
            myMesh.triangles = eventData.InputData.triangles;

            if (eventData.InputData.uvs != null && eventData.InputData.uvs.Length > 0)
            {
                myMesh.uv = eventData.InputData.uvs;
            }

            // ...
        }
    }
}
```

## <a name="known-issues"></a><span data-ttu-id="f429a-155">Problemas conhecidos</span><span class="sxs-lookup"><span data-stu-id="f429a-155">Known issues</span></span>

### <a name="net-native"></a><span data-ttu-id="f429a-156">.NET Nativo</span><span class="sxs-lookup"><span data-stu-id="f429a-156">.NET Native</span></span>

<span data-ttu-id="f429a-157">Atualmente, há um problema conhecido com compilações mestras usando o back-end do .NET.</span><span class="sxs-lookup"><span data-stu-id="f429a-157">There is currently a known issue with Master builds using the .NET backend.</span></span> <span data-ttu-id="f429a-158">no .NET Native, os `IInspectable` ponteiros não podem ser empacotados do código nativo para o gerenciado usando `Marshal.GetObjectForIUnknown` .</span><span class="sxs-lookup"><span data-stu-id="f429a-158">In .NET Native, `IInspectable` pointers cannot be marshaled from native to managed code using `Marshal.GetObjectForIUnknown`.</span></span> <span data-ttu-id="f429a-159">O MRTK usa isso para obter o a `SpatialCoordinateSystem` fim de receber dados de olho e de mão da plataforma.</span><span class="sxs-lookup"><span data-stu-id="f429a-159">The MRTK uses this to obtain the `SpatialCoordinateSystem` in order to receive hand and eye data from the platform.</span></span>

<span data-ttu-id="f429a-160">fornecemos a origem da DLL como uma solução alternativa para esse problema, na [realidade misturada nativa Toolkit repositório](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span><span class="sxs-lookup"><span data-stu-id="f429a-160">We've provided DLL source as a workaround for this issue, in [the native Mixed Reality Toolkit repo](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span></span> <span data-ttu-id="f429a-161">Siga as instruções no arquivo LEIAme e copie os binários resultantes em uma pasta plugins em seus ativos de Unity.</span><span class="sxs-lookup"><span data-stu-id="f429a-161">Please follow the instructions in the README there and copy the resulting binaries into a Plugins folder in your Unity assets.</span></span> <span data-ttu-id="f429a-162">Depois disso, o script WindowsMixedRealityUtilities fornecido no MRTK resolverá a solução alternativa para você.</span><span class="sxs-lookup"><span data-stu-id="f429a-162">After that, the WindowsMixedRealityUtilities script provided in the MRTK will resolve the workaround for you.</span></span>

<span data-ttu-id="f429a-163">Se você quiser criar sua própria DLL ou incluir essa solução alternativa em uma existente, o núcleo da solução alternativa será:</span><span class="sxs-lookup"><span data-stu-id="f429a-163">If you want to create your own DLL or include this workaround in an existing one, the core of the workaround is:</span></span>

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

<span data-ttu-id="f429a-164">E seu uso em seu código da Unity em C#:</span><span class="sxs-lookup"><span data-stu-id="f429a-164">And its use in your C# Unity code:</span></span>

```c#
[DllImport("DotNetNativeWorkaround.dll", EntryPoint = "MarshalIInspectable")]
private static extern void GetSpatialCoordinateSystem(IntPtr nativePtr, out SpatialCoordinateSystem coordinateSystem);

private static SpatialCoordinateSystem GetSpatialCoordinateSystem(IntPtr nativePtr)
{
    try
    {
        GetSpatialCoordinateSystem(nativePtr, out SpatialCoordinateSystem coordinateSystem);
        return coordinateSystem;
    }
    catch
    {
        UnityEngine.Debug.LogError("Call to the DotNetNativeWorkaround plug-in failed. The plug-in is required for correct behavior when using .NET Native compilation");
        return Marshal.GetObjectForIUnknown(nativePtr) as SpatialCoordinateSystem;
    }
}
```
