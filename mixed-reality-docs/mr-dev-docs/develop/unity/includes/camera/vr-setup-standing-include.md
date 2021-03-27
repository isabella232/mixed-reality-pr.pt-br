---
ms.openlocfilehash: 5f990569ae4052377cba717b5526bb8ba51b8016
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636252"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Use a classe [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity e defina a **escala de destino** como **sala** ou **posição**:

![Janela de configurações do MRTK](../../images/mrtk-target-scale.png)

MRTK deve tratar a posição da Playspace e da câmera automaticamente, mas é bom fazer uma verificação dupla:

![MRTK playspace](../../images/mrtk-playspace.png)

1. No painel **hierarquia** , expanda o **MixedRealityPlayspace** gameobject e localize o objeto filho da **câmera principal**
2. No painel **Inspetor** , localize o componente **transformar** e altere a **posição** para **(X: 0, Y: 0, Z: 0)**

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Defina o modo de origem de rastreamento no [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Depois de obter o subsistema, chame [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

E trabalhar com o [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)do Unity.

![Dispositivo XR na hierarquia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Ir para **outra** seção de configurações das **configurações do Windows Store Player**
2. Escolha a **realidade mista do Windows** como o dispositivo, que pode ser listado como **Holographic do Windows** em versões mais antigas do Unity
3. Selecione a **realidade virtual com suporte**

Como o objeto da câmera principal é marcado automaticamente como a câmera, o Unity alimenta todo o movimento e a tradução.

>[!NOTE]
>Essas configurações precisam ser aplicadas à câmera em cada cena do seu aplicativo.
>
>Por padrão, quando você cria uma nova cena no Unity, ela conterá uma câmara de jogo principal na hierarquia que inclui o componente da câmera, mas não tem as configurações abaixo aplicadas corretamente.

**Namespace:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

Para uma experiência **de escala de** colocação ou de escala de **espaço**, você precisará colocar o conteúdo em relação ao andar. Você se deparar com o andar do usuário usando o **[estágio espacial](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, que representa a origem definida do nível de chão do usuário e o limite de sala opcional, configurado durante a primeira execução.

Para garantir que o Unity esteja operando com seu sistema de coordenadas mundiais no nível de piso, você pode definir e testar se o Unity está usando o tipo de espaço de rastreamento RoomScale:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

* Se SetTrackingSpaceType retornar true, o Unity alternará com êxito seu sistema de coordenadas mundiaI para acompanhar o [quadro de referência de estágio](../../../../design/coordinate-systems.md#spatial-coordinate-systems).
* Se SetTrackingSpaceType retornar false, o Unity não poderá alternar para o quadro de referência de estágio, provavelmente porque o usuário não configurou um andar em seu ambiente. Embora um valor falso de retorno não seja comum, isso pode acontecer se o estágio estiver configurado em uma sala diferente e o dispositivo for movido para o espaço atual sem que o usuário configure um novo estágio.

Depois que o aplicativo definir o tipo de espaço de acompanhamento RoomScale com êxito, o conteúdo colocado no plano y = 0 aparecerá no chão. A origem em 0, 0, será o local específico no andar em que o usuário se deparava durante a configuração da sala, com-Z representando a direção de encaminhamento que ele estava enfrentando durante a instalação.