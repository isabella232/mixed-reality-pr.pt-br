---
title: Visão geral do sistema de teletransporte
description: Visão geral sobre como habilitar e desabilitar o sistema de teletransporte no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, sistema de teletransporte,
ms.openlocfilehash: ee56f62d6e0206249db62d8e7e93cf97cdf8bcc40c35ec0284ebae319870f8ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197636"
---
# <a name="teleport-system"></a>Sistema de teletransporte

O sistema de teletransporte é um subsistema do MRTK que lida com o teletransporte do usuário quando o aplicativo está usando uma exibição opaca. Em experiências de RA (como o HoloLens), o sistema de teletransporte não está ativo. Em experiências imersivas de HMD (OpenVR e WMR), o sistema de teletransporte pode ser habilitado.

## <a name="enabling-and-disabling"></a>Como habilitar e desabilitar o sistema

O sistema de teletransporte pode ser habilitado ou desabilitado marcando/desmarcando a caixa de seleção no respectivo perfil.
É possível executar isso selecionando o objeto MixedRealityToolkit na cena, clicando em "Teletransportar" e marcando/desmarcando a caixa de seleção "Habilitar Sistema de Teletransporte".

Também é possível executar isso no runtime:

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

O sistema de teletransporte expõe eventos por meio da interface [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) para fornecer sinais quando as ações de teletransporte começam, terminam ou são canceladas.
Confira a documentação da API vinculada para obter mais detalhes sobre a mecânica dos eventos e o conteúdo associado.

## <a name="usage"></a>Uso

### <a name="how-to-register-for-teleportation-events"></a>Como se registrar em eventos de teletransporte

O código a seguir mostrará de que modo criar um MonoBehaviour que vai escutar eventos de teletransporte. Esse código pressupõe que o sistema de teletransporte está habilitado.

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
