---
ms.openlocfilehash: 61fe8754192c1fbd0634fd9d1e1994327599321b
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748483"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Use a [classe MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) do MRTK para Unity e de definir a Escala de **Destino** como **Sala** ou **Em Espera:**

![Janela de configurações do MRTK](../../images/mrtk-target-scale.png)

O MRTK deve lidar com a posição do playspace e da câmera automaticamente, mas é bom verificar duas vezes:

![Playspace do MRTK](../../images/mrtk-playspace.png)

1. No painel **Hierarquia,** expanda **MixedRealityPlayspace** GameObject e encontre o **objeto filho da Câmera** Principal
2. No painel **Inspetor,** encontre o **componente Transformar** e altere a **Posição** para **(X: 0, Y: 0, Z: 0)**

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

De definir o modo de origem de acompanhamento [no XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Depois de obter o subsistema, chame [TrySetTrackingOriginMode:](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

E trabalhe com o [XRRig do](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)Unity.

![Plataforma XR na hierarquia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Vá para **a seção Outras Configurações** das **Configurações do Player da Windows Store**
2. Escolha **Windows Mixed Reality** como o dispositivo, que pode ser listado como **Windows Holographic** em versões mais antigas do Unity
3. Selecione **Realidade Virtual Com Suporte**

Como o objeto Câmera Principal é marcado automaticamente como a câmera, o Unity acionará toda a movimentação e a tradução.

>[!NOTE]
>Essas configurações precisam ser aplicadas à Câmera em cada cena do seu aplicativo.
>
>Por padrão, quando você cria uma nova cena no Unity, ela conterá um GameObject da Câmera Principal na Hierarquia que inclui o componente Câmera, mas não tem as configurações abaixo aplicadas corretamente.

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Para uma **experiência de escala permanente** ou de escala **de** espaço, você precisará colocar o conteúdo em relação ao chão. Você se preocupa com o piso do usuário usando o estágio espacial **[,](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** que representa a origem definida no nível do piso do usuário e o limite de sala opcional, configurada durante a primeira operação.

Para garantir que o Unity está operando com seu sistema de coordenadas mundial no nível do chão, você pode definir e testar se o Unity está usando o tipo de espaço de acompanhamento RoomScale:

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

* Se SetTrackingSpaceType retornar true, o Unity alterna com êxito seu sistema de coordenadas mundial para acompanhar o quadro [de estágio de referência](../../../../design/coordinate-systems.md#spatial-coordinate-systems).
* Se SetTrackingSpaceType retornar false, o Unity não poderá alternar para o quadro de estágio de referência, provavelmente porque o usuário não tiver definido um andar em seu ambiente. Embora um valor de retorno falso não seja comum, isso pode acontecer se o estágio estiver definido em uma sala diferente e o dispositivo for movido para a sala atual sem que o usuário configurar um novo estágio.

Depois que o aplicativo define com êxito o tipo de espaço de acompanhamento RoomScale, o conteúdo colocado no plano y=0 será exibido no chão. A origem em 0, 0, 0 será o local específico no chão em que o usuário se juntou durante a instalação da sala, com -Z representando a direção para frente que ele estava enfrentando durante a instalação.