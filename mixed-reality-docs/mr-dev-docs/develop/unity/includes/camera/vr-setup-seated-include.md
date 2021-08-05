---
ms.openlocfilehash: f55de39af8c9bc59bb23136203bfc093a4e29f1ea9ddc5ccd147f8c81d6f0020
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212198"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Use a classe [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity e defina a **escala de destino** como **encaixada**:

![Janela de configurações do MRTK](../../images/mrtk-target-scale.png)

MRTK deve tratar a posição da Playspace e da câmera automaticamente, mas é bom fazer uma verificação dupla:

![MRTK playspace](../../images/mrtk-playspace.png)

1. No painel **hierarquia** , expanda o **MixedRealityPlayspace** gameobject e localize o objeto filho da **câmera principal**
2. No painel **Inspetor** , localize o componente **transformar** e altere a **posição** para **(X: 0, Y: 0, Z: 0)**

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Defina o modo de origem de rastreamento no [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Depois de obter o subsistema, chame [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

E trabalhar com o [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)do Unity.

![Dispositivo XR na hierarquia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. vá para **outras Configurações** seção do **Player do Windows Store Configurações**
2. escolha **Windows Mixed Reality** como o dispositivo, que pode ser listado como **Windows Holographic** em versões anteriores do Unity
3. Selecione a **realidade virtual com suporte**

Como o objeto da câmera principal é marcado automaticamente como a câmera, o Unity alimenta todo o movimento e a tradução.

>[!NOTE]
>Essas configurações precisam ser aplicadas à câmera em cada cena do seu aplicativo.
>
>Por padrão, quando você cria uma nova cena no Unity, ela conterá uma câmara de jogo principal na hierarquia que inclui o componente da câmera, mas não tem as configurações abaixo aplicadas corretamente.

**Namespace:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

Para criar uma experiência **somente de orientação** ou **de escala assentada**, você precisa definir o Unity para o tipo de espaço de rastreamento estacionário. O espaço de acompanhamento fixo define o sistema de coordenadas mundiais do Unity para acompanhar o [quadro de referência](../../../../design/coordinate-systems.md#spatial-coordinate-systems). No modo de rastreamento estacionário, o conteúdo colocado no editor apenas na frente do local padrão da câmera (Forward is-Z) aparecerá na frente do usuário quando o aplicativo for iniciado.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Namespace:** *UnityEngine. XR*<br>
**Tipo:** *InputTracking*

Para uma **experiência pura somente de orientação** , como um visualizador de vídeo de 360 graus (em que as atualizações de cabeça posicional poderiam arruinar a ilusão), você pode então definir a [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) para true:

```cs
InputTracking.disablePositionalTracking = true;
```

Para uma **experiência em escala**, para permitir que o usuário recentralize a origem encaixada novamente, você pode chamar a [XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :

```cs
InputTracking.Recenter();
```

Se você estiver criando uma [experiência de escala](../../../../design/coordinate-systems.md)em posição, poderá recentralizar a origem mundial da unidade na posição de cabeçalho atual do usuário chamando o **[XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .