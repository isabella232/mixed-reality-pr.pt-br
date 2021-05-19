---
title: Acompanhamento da mão
description: Documentação sobre como usar o HandTracking no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Acompanhamento de Mão,
ms.openlocfilehash: 6cd55bc76d9fba42640954bcbf50e62f66454a94
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143351"
---
# <a name="hand-tracking"></a>Acompanhamento da mão

## <a name="hand-tracking-profile"></a>Perfil de acompanhamento de mão

O _perfil de Acompanhamento de Mão_ é encontrado no perfil sistema de _entrada_. Ele contém configurações para personalizar a representação da mão.

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a>Pré-requisitos conjuntos

Os pré-fabs conjuntos são visualizados usando pré-fabs simples. As _junções de_ dedo indicador e de mão indicador são de importância especial e têm seu próprio pré-fab, enquanto todas as outras junções compartilham o mesmo pré-fab. 

Por padrão, os pré-padrões de junção de mão são primitivos geométricos simples. Eles podem ser substituídos, se desejado. Se nenhum pré-fab for especificado, [gameObjects vazios](https://docs.unity3d.com/ScriptReference/GameObject.html) serão criados.

> [!WARNING]
> Evite usar scripts complexos ou renderização cara em pré-requisitos conjuntos, pois os objetos comuns são transformados em cada quadro e podem ter um custo de desempenho significativo!

Representação conjunta de mão padrão |  Rótulos conjuntos
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a>Pré-fab de malha de mão

A malha manual será usada se os dados de malha totalmente definidos são fornecidos pelo dispositivo de acompanhamento de mão. A malha renderizável no pré-teste é substituída pelos dados do dispositivo, portanto, uma malha fiada, como um cubo, é suficiente. O material do pré-fab é usado para a malha manual.

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

A exibição da malha manual pode ter um impacto perceptível no desempenho, por esse motivo, ela pode ser desabilitada inteiramente desmarcando a opção Habilitar Visualização **de Malha manual.**

## <a name="hand-visualization-settings"></a>Configurações de visualização de mão

A malha de mão e as visualizações conjuntas podem ser desativadas ou ativadas por meio da configuração dos *modos de visualização de malha à* mão e *modos de visualização conjunta* , respectivamente. Essas configurações são específicas do modo de aplicativo, o que significa que é possível ativar alguns recursos enquanto estiver no editor (para ver as junções com a simulação no editor, por exemplo) enquanto têm os mesmos recursos desativados quando implantados no dispositivo (em builds de Player).

Observe que, em geral, é recomendável ter a visualização conjunta configurada no editor (para que a simulação do editor mostre onde estão as junções de mão) e ter a visualização conjunta e a visualização de malha à mão desativada no Player (porque elas incorrem em um impacto no desempenho).

## <a name="scripting"></a>Scripting

A posição e a rotação podem ser solicitadas no sistema de entrada para cada conjunto individual de cada mão como um [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

Como alternativa, o sistema permite o acesso ao [Gameobjects](https://docs.unity3d.com/ScriptReference/GameObject.html) que segue as junções. Isso pode ser útil se outro gameobject deve acompanhar um conjunto continuamente.

As junções disponíveis são listadas na [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enumeração.

> [!NOTE]
> O objeto conjunta é destruído quando o rastreamento à mão é perdido! Certifique-se de que todos os scripts que usam o objeto conjunta manipulem o `null` caso normalmente para evitar erros!

### <a name="accessing-a-given-hand-controller"></a>Acessando um determinado controlador

Um controlador de mão específico geralmente está disponível, por exemplo, ao manipular eventos de entrada. Nesse caso, os dados conjuntas podem ser solicitados diretamente do dispositivo, usando a [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.

#### <a name="polling-joint-pose-from-controller"></a>Sondagem conjunta de pose do controlador

A [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) função retornará `false` se a junção solicitada não estiver disponível por algum motivo. Nesse caso, a pose resultante será [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .

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

#### <a name="joint-transform-from-hand-visualizer"></a>Transformação conjunta do Visualizador de mão

Objetos conjuntas podem ser solicitados no [Visualizador do controlador](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).

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

### <a name="simplified-joint-data-access"></a>Acesso a dados em conjunto simplificado

Se nenhum controlador específico for fornecido, as classes utilitárias serão fornecidas para acesso conveniente aos dados conjuntas. Essas funções solicitam dados conjuntas do primeiro dispositivo disponível atualmente controlado.

#### <a name="polling-joint-pose-from-handjointutils"></a>Pose conjunta de sondagem de HandJointUtils

[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) é uma classe estática que consulta o primeiro dispositivo de mão ativo.

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a>Transformação conjunta do serviço conjunto de mão

[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) mantém um conjunto persistente de [GameObjects para](https://docs.unity3d.com/ScriptReference/GameObject.html) controlar junções.

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a>Eventos de acompanhamento de mão

O sistema de entrada também fornece eventos, se a sondagem de dados de controladores diretamente não for desejável.

#### <a name="joint-events"></a>Eventos conjuntos

[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) lida com atualizações de posições conjuntas.

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

#### <a name="mesh-events"></a>Eventos de malha

[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) trata as alterações da malha de mão articulada.

Observe que as malhas de mão não estão habilitadas por padrão.

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

## <a name="known-issues"></a>Problemas conhecidos

### <a name="net-native"></a>.NET Nativo

Atualmente, há um problema conhecido com builds Mestre usando o back-end do .NET. No .NET Native, `IInspectable` ponteiros não podem ser marshalados de código nativo para gerenciado usando `Marshal.GetObjectForIUnknown` . O MRTK usa isso para obter o para receber dados de mãos e olhos `SpatialCoordinateSystem` da plataforma.

Fornecemos a origem da DLL como uma solução alternativa para esse problema, no repo nativo do Kit de Ferramentas [de Realidade Misturada](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround). Siga as instruções no LEIAME e copie os binários resultantes em uma pasta Plug-ins em seus ativos do Unity. Depois disso, o script WindowsMixedRealityUtilities fornecido no MRTK resolverá a solução alternativa para você.

Se você quiser criar sua própria DLL ou incluir essa solução alternativa em uma existente, o núcleo da solução alternativa será:

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

E seu uso em seu código do Unity em C#:

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
