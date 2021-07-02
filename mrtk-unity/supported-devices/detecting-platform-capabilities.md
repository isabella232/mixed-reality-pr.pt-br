---
title: Detectando recursos de plataforma
description: Detalhes de diferentes recursos que o MRTK dá suporte
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, funcionalidades,
ms.openlocfilehash: 70d320e178f4635d74b5be6a1874eb4254801719
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175520"
---
# <a name="detecting-platform-capabilities"></a>Detectando recursos de plataforma

uma pergunta comum feita pelo MRTK envolve saber qual dispositivo específico (ex: Microsoft HoloLens 2) está sendo usado para executar um aplicativo. Identificar o hardware exato pode ser desafiador em diferentes plataformas. Em vez disso, o MRTK fornece uma maneira de identificar recursos específicos em tempo de execução, (por exemplo, se o ponto de extremidade do dispositivo atual der suporte a mãos articuladas).

## <a name="capabilities"></a>Funcionalidades

a realidade misturada Toolkit fornece a [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeração, que define um conjunto de recursos para os quais um aplicativo pode consultar em tempo de execução.

### <a name="input-system-capabilities"></a>Recursos do sistema de entrada

O sistema de entrada MRTK padrão dá suporte à consulta dos seguintes recursos:

| Funcionalidade | Descrição |
|---|---|
| ArticulatedHand | Entrada de mão articulada |
| EyeTracking | Direcionamento olhar de olho |
| GGVHand | Olhar-gesto-entrada do lado da voz |
| MotionController | Entrada do controlador de movimento |
| VoiceCommand | Comandos de voz usando palavras-chave definidas pelo aplicativo |
| VoiceDictation | Ditado de voz para texto |

O código de exemplo abaixo verifica se o sistema de entrada carregou um provedor de dados com suporte para as mãos articuladas.

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a>Recursos de reconhecimento espacial

O sistema de reconhecimento espacial MRTK padrão dá suporte à consulta dos seguintes recursos:

| Funcionalidade | Descrição |
|---|---|
| SpatialAwarenessMesh | Malhas espaciais |
| SpatialAwarenessPlane | Planos espaciais |
| SpatialAwarenessPoint | Pontos espaciais |

Este exemplo verifica se o sistema de conscientização espacial carregou um provedor de dados com suporte para malhas espaciais.

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a>Confira também

- [Documentação da API do IMixedRealityCapabilityCheck](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [Documentação de enumeração do MixedRealityCapability](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
