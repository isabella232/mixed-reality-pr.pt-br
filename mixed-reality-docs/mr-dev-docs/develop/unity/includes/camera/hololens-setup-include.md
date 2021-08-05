---
ms.openlocfilehash: 78596197af6c2e7c329e7a7c99281f8debee13b973a212709f5be1ec34e04eea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212194"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

siga este [tutorial](../../tutorials/mr-learning-base-01.md) passo a passo para adicionar e configurar automaticamente Toolkit de realidade misturada em seu projeto do Unity. Também é possível trabalhar diretamente com a classe [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity e definir a escala de **destino** como **mundo**:

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
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

você pode usar o [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) para aplicativos HoloLens, o que funciona melhor com âncoras e ARKit/ARCore.

![Sessão AR na hierarquia](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> A sessão AR e os recursos relacionados precisam do AR Foundation instalado.

Também é possível aplicar as alterações da câmera manualmente sem usar ARSession:

1. Selecione a **câmera principal** no painel **hierarquia**
1. No painel **Inspetor** , localize o componente **transformar** e altere a **posição** para **(X: 0, Y: 0, Z: 0)**

   ![Câmera no painel de Inspetor no Unity](../../images/maincamera-350px.png)  
   *Câmera no painel de Inspetor no Unity*

1. Adicionar um **TrackedPoseDriver** à **câmera principal**

# <a name="legacy-wsa"></a>[WSA herdado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Selecione a **câmera principal** no painel **hierarquia**
1. No painel **Inspetor** , localize o componente **transformar** e altere a **posição** para **(X: 0, Y: 0, Z: 0)**

   ![Câmera no painel de Inspetor no Unity](../../images/maincamera-350px.png)  
   *Câmera no painel de Inspetor no Unity*

1. vá para **outras Configurações** seção do **Player do Windows Store Configurações**
1. escolha **Windows Mixed Reality** como o dispositivo, que pode ser listado como **Windows Holographic** em versões anteriores do Unity
1. Selecione a **realidade virtual com suporte**

Como o objeto da câmera principal é marcado automaticamente como a câmera, o Unity alimenta todo o movimento e a tradução.

>[!NOTE]
>Essas configurações precisam ser aplicadas à câmera em cada cena do seu aplicativo.
>
>Por padrão, quando você cria uma nova cena no Unity, ela conterá uma câmara de jogo principal na hierarquia que inclui o componente da câmera, mas pode não ter as configurações aplicadas corretamente.