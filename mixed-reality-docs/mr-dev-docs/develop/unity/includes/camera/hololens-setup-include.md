---
ms.openlocfilehash: 6e751f5376110ddc6ae92c75b4182fba8240a356
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748515"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Siga este [tutorial passo a passo para](../../tutorials/mr-learning-base-01.md) adicionar e configurar automaticamente o Kit de Ferramentas de Realidade Misturada em seu projeto do Unity. Também é possível trabalhar diretamente com a [classe MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) do MRTK para Unity e definir a **Escala** de Destino como **Mundo:**

![Janela de configurações do MRTK](../../images/mrtk-target-scale.png)

O MRTK deve lidar com a posição do playspace e da câmera automaticamente, mas é bom verificar duas vezes:

![Playspace do MRTK](../../images/mrtk-playspace.png)

1. No painel **Hierarquia,** expanda **MixedRealityPlayspace** GameObject e encontre o **objeto filho da Câmera** Principal
2. No painel **Inspetor,** encontre o **componente Transformar** e altere a **Posição** para **(X: 0, Y: 0, Z: 0)**

# <a name="xr-sdk"></a>[SDK do XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

De definir o modo de origem de acompanhamento [no XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Depois de obter o subsistema, chame [TrySetTrackingOriginMode:](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

Você pode usar [ARSession para aplicativos](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) HoloLens, que funciona melhor com âncoras e ARKit/ARCore.

![Sessão AR na hierarquia](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> A Sessão de RA e os recursos relacionados precisam do AR Foundation instalado.

Também é possível aplicar as alterações da câmera manualmente sem usar ARSession:

1. Selecione **Câmera Principal** no painel **Hierarquia**
1. No painel **Inspetor,** encontre o **componente Transformar** e altere a **Posição** para **(X: 0, Y: 0, Z: 0)**

   ![Câmera no painel Inspetor no Unity](../../images/maincamera-350px.png)  
   *Câmera no painel Inspetor no Unity*

1. Adicionar um **TrackedPoseDriver** à **Câmera Principal**

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Selecione **Câmera Principal** no painel **Hierarquia**
1. No painel **Inspetor,** encontre o **componente Transformar** e altere a **Posição** para **(X: 0, Y: 0, Z: 0)**

   ![Câmera no painel Inspetor no Unity](../../images/maincamera-350px.png)  
   *Câmera no painel Inspetor no Unity*

1. Vá para **a seção Outras Configurações** das **Configurações do Player da Windows Store**
1. Escolha **Windows Mixed Reality** como o dispositivo, que pode ser listado como **Windows Holographic** em versões mais antigas do Unity
1. Selecione **Realidade Virtual Com Suporte**

Como o objeto Câmera Principal é marcado automaticamente como a câmera, o Unity acionará toda a movimentação e a tradução.

>[!NOTE]
>Essas configurações precisam ser aplicadas à Câmera em cada cena do seu aplicativo.
>
>Por padrão, quando você cria uma nova cena no Unity, ela conterá um GameObject da Câmera Principal na Hierarquia que inclui o componente Câmera, mas pode não ter as configurações aplicadas corretamente.