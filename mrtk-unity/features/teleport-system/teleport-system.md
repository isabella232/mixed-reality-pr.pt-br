---
title: Sistema teleport
description: Visão geral sobre como habilitar e desabilitar o sistema teleport no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, sistema Teleport,
ms.openlocfilehash: 7a49b1fea36eb1809c57abee4cede1216c07d5bf
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176186"
---
# <a name="teleport-system"></a>Sistema de teletransporte

O sistema teleport é um subsistema do MRTK que lida com o transporte do usuário quando o aplicativo está usando uma exibição opaca. para experiências de AR (como HoloLens), o sistema de teleportação não está ativo. Para experiências de HMD de imersão (OpenVR, WMR), o sistema teleport pode ser habilitado.

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
