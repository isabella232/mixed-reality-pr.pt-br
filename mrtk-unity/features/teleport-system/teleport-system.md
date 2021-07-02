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
# <a name="teleport-system"></a><span data-ttu-id="23894-104">Sistema de teletransporte</span><span class="sxs-lookup"><span data-stu-id="23894-104">Teleport system</span></span>

<span data-ttu-id="23894-105">O sistema teleport é um subsistema do MRTK que lida com o transporte do usuário quando o aplicativo está usando uma exibição opaca.</span><span class="sxs-lookup"><span data-stu-id="23894-105">The teleport system is a sub-system of the MRTK that handles teleporting the user when the application is using an opaque display.</span></span> <span data-ttu-id="23894-106">para experiências de AR (como HoloLens), o sistema de teleportação não está ativo.</span><span class="sxs-lookup"><span data-stu-id="23894-106">For AR experiences (like HoloLens), the teleportation system is not active.</span></span> <span data-ttu-id="23894-107">Para experiências de HMD de imersão (OpenVR, WMR), o sistema teleport pode ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="23894-107">For immersive HMD experiences (OpenVR, WMR) the teleport system can be enabled.</span></span>

## <a name="enabling-and-disabling"></a><span data-ttu-id="23894-108">Habilitando e desabilitando</span><span class="sxs-lookup"><span data-stu-id="23894-108">Enabling and disabling</span></span>

<span data-ttu-id="23894-109">O sistema teleport pode ser habilitado ou desabilitado alternando a caixa de seleção em seu perfil.</span><span class="sxs-lookup"><span data-stu-id="23894-109">The teleport system can be enabled or disabled by toggling the checkbox in its profile.</span></span>
<span data-ttu-id="23894-110">Isso pode ser feito selecionando o objeto MixedRealityToolkit na cena, clicando em "teleport" e, em seguida, alternando a caixa de seleção "habilitar o sistema de teleport".</span><span class="sxs-lookup"><span data-stu-id="23894-110">This can be done by selecting the MixedRealityToolkit object in the scene, clicking "Teleport" and then toggling the "Enable Teleport System" checkbox.</span></span>

<span data-ttu-id="23894-111">Isso também pode ser feito em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="23894-111">This can also be done at runtime:</span></span>

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

## <a name="events"></a><span data-ttu-id="23894-112">Eventos</span><span class="sxs-lookup"><span data-stu-id="23894-112">Events</span></span>

<span data-ttu-id="23894-113">O sistema teleport expõe eventos por meio da [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface para fornecer sinais quando as ações de teleport começam, terminam ou são canceladas.</span><span class="sxs-lookup"><span data-stu-id="23894-113">The teleport system exposes events through the [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface to provide signals on when teleport actions begin, end, or get cancelled.</span></span>
<span data-ttu-id="23894-114">Consulte a documentação da API vinculada para obter mais detalhes sobre a mecânica dos eventos e sua carga associada.</span><span class="sxs-lookup"><span data-stu-id="23894-114">See the linked API documentation for more details on the mechanics of the events and their associated payload.</span></span>

## <a name="usage"></a><span data-ttu-id="23894-115">Uso</span><span class="sxs-lookup"><span data-stu-id="23894-115">Usage</span></span>

### <a name="how-to-register-for-teleportation-events"></a><span data-ttu-id="23894-116">Como registrar-se para eventos de teleportação</span><span class="sxs-lookup"><span data-stu-id="23894-116">How to register for teleportation events</span></span>

<span data-ttu-id="23894-117">O código a seguir mostra como criar um monocomportamento que irá escutar eventos de teleportação.</span><span class="sxs-lookup"><span data-stu-id="23894-117">The code below shows how to create a MonoBehaviour that will listen for teleportation events.</span></span> <span data-ttu-id="23894-118">Esse código pressupõe que o sistema teleport está habilitado.</span><span class="sxs-lookup"><span data-stu-id="23894-118">This code assumes that the teleport system is enabled.</span></span>

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

## <a name="teleporting-on-mrtk"></a><span data-ttu-id="23894-119">Teleportamento em MRTK</span><span class="sxs-lookup"><span data-stu-id="23894-119">Teleporting on MRTK</span></span>

<span data-ttu-id="23894-120">Para teleport com um controlador em dispositivos MR com configurações padrão, use o Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="23894-120">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="23894-121">Para teleportr com as mãos articuladas, faça um gesto com seu Palm voltado para cima com o índice e o polegar para cima, concluindo o teleport ao enrolar o dedo do índice.</span><span class="sxs-lookup"><span data-stu-id="23894-121">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="23894-122">Para teleport com a simulação de entrada, consulte nossa [documentação](../input-simulation/input-simulation-service.md)atualizada do serviço de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="23894-122">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../input-simulation/input-simulation-service.md).</span></span>

  ![Gesto de teleport](../images/teleport/handteleport.gif)
