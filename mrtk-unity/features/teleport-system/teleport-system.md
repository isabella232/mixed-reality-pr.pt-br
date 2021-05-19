---
title: Visão geral do sistema teleport
description: Visão geral sobre como habilitar e desabilitar o sistema teleport no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, sistema teleport,
ms.openlocfilehash: a44ad1827597dd0b27bc88a9420a3b251f934afd
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144146"
---
# <a name="teleport-system"></a>Sistema de teletransporte

O sistema teleport é um subsistema do MRTK que lida com o transporte do usuário quando o aplicativo está usando uma exibição opaca. Para experiências de AR (como o HoloLens), o sistema de teleportação não está ativo. Para experiências de HMD de imersão (OpenVR, WMR), o sistema teleport pode ser habilitado.

## <a name="enabling-and-disabling"></a>Habilitando e desabilitando

O sistema teleport pode ser habilitado ou desabilitado alternando a caixa de seleção em seu perfil.
Isso pode ser feito selecionando o objeto MixedRealityToolkit na cena, clicando em "teleport" e, em seguida, alternando a caixa de seleção "habilitar o sistema de teleport".

Isso também pode ser feito em tempo de execução:

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

O sistema teleport expõe eventos por meio da [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface para fornecer sinais quando as ações de teleport começam, terminam ou são canceladas.
Consulte a documentação da API vinculada para obter mais detalhes sobre a mecânica dos eventos e sua carga associada.

## <a name="usage"></a>Uso

### <a name="how-to-register-for-teleportation-events"></a>Como registrar-se para eventos de teleportação

O código a seguir mostra como criar um monocomportamento que irá escutar eventos de teleportação. Esse código pressupõe que o sistema teleport está habilitado.

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

## <a name="teleporting-on-mrtk"></a>Teleportamento em MRTK

Para teleport com um controlador em dispositivos MR com configurações padrão, use o Thumbstick. Para teleportr com as mãos articuladas, faça um gesto com seu Palm voltado para cima com o índice e o polegar para cima, concluindo o teleport ao enrolar o dedo do índice. Para teleport com a simulação de entrada, consulte nossa [documentação](../input-simulation/input-simulation-service.md)atualizada do serviço de simulação de entrada.

  ![Gesto de teleport](../images/teleport/handteleport.gif)