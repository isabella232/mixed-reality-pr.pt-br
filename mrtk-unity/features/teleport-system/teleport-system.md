---
title: Sistema de teletransporte
description: Visão geral sobre como habilenciar e desabilitar o sistema Dev no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, sistema Dev.
ms.openlocfilehash: c46438ed30880029760b5155efb3e3cd1d571c81a03bfbf764b2010e2e232c53
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197036"
---
# <a name="teleport-system"></a>Sistema de teletransporte

O sistema de teletransporte é um subsistema do MRTK que trata o usuário quando o aplicativo está usando uma exibição opaca. Para experiências de RA (como HoloLens), o sistema de transporte não está ativo. Para experiências de HMD imersivas (OpenVR, WMR), o sistema de teletransporte pode ser habilitado.

## <a name="enabling-and-disabling"></a>Habilitando e desabilitando

O sistema de teletransporte pode ser habilitado ou desabilitado ativando a caixa de seleção em seu perfil.
Isso pode ser feito selecionando o objeto MixedRealityToolkit na cena, clicando em "Transportar" e, em seguida, ativando a caixa de seleção "Habilitar Sistema DeTransportar".

Isso também pode ser feito em runtime:

```c#
void DisableTeleportSystem()
{
    CoreServices.TeleportSystem.Disable();
}

void EnableTeleportSystem()
{
    CoreServices.TeleportSystem.Enable();
}
```

## <a name="events"></a>Eventos

O sistema de teletransporte expõe eventos por meio da interface para fornecer sinais sobre quando as ações [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) de teletransporte começam, terminam ou são canceladas.
Consulte a documentação da API vinculada para obter mais detalhes sobre a mecânica dos eventos e sua carga associada.

## <a name="usage"></a>Uso

### <a name="how-to-register-for-teleportation-events"></a>Como se registrar para eventos de teletransporte

O código a seguir mostra como criar um MonoBehaviour que escutará eventos de teletransportação. Esse código pressuporta que o sistema de transporte está habilitado.

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Teleport;
using UnityEngine;

public class TeleportHandlerExample : MonoBehaviour, IMixedRealityTeleportHandler
{
    public void OnTeleportCanceled(TeleportEventData eventData)
    {
        Debug.Log("Teleport Cancelled");
    }

    public void OnTeleportCompleted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Completed");
    }

    public void OnTeleportRequest(TeleportEventData eventData)
    {
        Debug.Log("Teleport Request");
    }

    public void OnTeleportStarted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Started");
    }

    void OnEnable()
    {
        // This is the critical call that registers this class for events. Without this
        // class's IMixedRealityTeleportHandler interface will not be called.
        CoreServices.TeleportSystem.RegisterHandler<IMixedRealityTeleportHandler>(this);
    }

    void OnDisable()
    {
        // Unregistering when disabled is important, otherwise this class will continue
        // to receive teleportation events.
        CoreServices.TeleportSystem.UnregisterHandler<IMixedRealityTeleportHandler>(this);
    }
}
```

## <a name="teleporting-on-mrtk"></a>Teletransporte no MRTK

Para usar um controlador em dispositivos MR com configurações padrão, use o thumbstick. Para fazer um gesto com as mãos articuladas, faça um gesto com a mão voltada para cima com o índice e o polegar para fora, concluindo o anel ondulando o dedo indicador. Para fazer a simulação de entrada, confira nossa documentação atualizada [do Serviço de Simulação de Entrada](../input-simulation/input-simulation-service.md).

  ![Gesto de Teletransporte](../images/teleport/handteleport.gif)
