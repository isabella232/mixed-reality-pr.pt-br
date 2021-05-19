---
title: Provedor de foco de olho de acompanhamento ocular
description: Documentação do provedor de olhar no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, EyeTracking, EyeGaze,
ms.openlocfilehash: ef50a55d52a5dad9f424c8af8139565e02542b6c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144023"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a>Acessando dados de acompanhamento ocular em seu script do Unity

Este artigo pressuila que você tenha compreensão para configurar o acompanhamento ocular em uma cena do MRTK (consulte Configuração básica do [MRTK para usar o acompanhamento ocular).](eye-tracking-basic-setup.md)
Acessar dados de acompanhamento ocular em um script MonoBehaviour é fácil! Basta usar *CoreServices.InputSystem.EyeGazeProvider*.

## <a name="imixedrealityeyegazeprovider"></a>IMixedRealityEyeGazeProvider

A configuração de acompanhamento ocular no MRTK é configurada por meio da [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface . O [uso de CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) fornece a implementação padrão do provedor de gaze registrada no kit de ferramentas em runtime.
As propriedades úteis do `EyeGazeProvider` são descritas abaixo.

- **IsEyeTrackingEnabled:** True se o usuário tiver selecionado usar o acompanhamento ocular para o olhar.

- **IsEyeCalibrationValid:** indica se a calibragem do acompanhamento ocular do usuário é válida ou não.
Ele retornará 'null', se o valor ainda não tiver recebido dados do sistema de acompanhamento ocular.
Pode ser inválido, porque o usuário ignorava a calibragem de acompanhamento ocular.

- **IsEyeTrackingEnabledAndValid:** indica se os dados de acompanhamento ocular atuais estão sendo usados atualmente para o olhar.

- **IsEyeTrackingDataValid:** true se os dados de acompanhamento ocular estão disponíveis.
No entanto, ele pode não estar disponível devido ao tempo limite excedido (deve ser robusto para o usuário piscar) ou à falta de hardware ou permissões de acompanhamento.
Confira nosso exemplo [de notificação de calibragem](eye-tracking-is-user-calibrated.md) ocular ausente que explica como detectar se um usuário está calibrado com o olhar e para mostrar uma notificação apropriada.

- **GazeOrigin:** origem do raio do olhar.
Observe que isso retornará a *origem do* olhar de cabeça se 'IsEyeGazeValid' for false.

- **GazeDirection**: direção do olhar Ray.
Isso retornará a direção da olhar de *cabeçalho* se ' IsEyeGazeValid ' for false.

- **HitInfo**, **HitPosition**, **HitNormal**, etc.: informações sobre o gazed no momento no destino.
Novamente, se `IsEyeGazeValid` for false, isso será baseado no olhar da *cabeça* do usuário.

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a>Exemplos de uso de CoreServices. InputSystem. EyeGazeProvider

Aqui está um exemplo do [FollowEyeGaze. cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):

- Obtenha o ponto de um holograma que o usuário está vendo:

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- Mostrando um ativo visual a uma distância fixa de onde o usuário está atualmente procurando:

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a>Confira também

- [Visão geral do acompanhamento de olho do MRTK](eye-tracking-main.md)
- [Configuração de acompanhamento de olho do MRTK](eye-tracking-basic-setup.md)
- [Calibragem de controle ocular MRTK](eye-tracking-is-user-calibrated.md)
- [Documentação de acompanhamento de olho do HoloLens 2](/windows/mixed-reality/eye-tracking)