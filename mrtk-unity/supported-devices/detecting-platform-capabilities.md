---
title: Detectar funcionalidades de plataforma
description: Detalhes de diferentes funcionalidades compatíveis com o MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, funcionalidades,
ms.openlocfilehash: 0a3ad248e418e10ad1a7105ca5f9ece3e02c62bd7679cfd22d9c4396016d09a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207604"
---
# <a name="detecting-platform-capabilities"></a>Detectar funcionalidades de plataforma

Uma pergunta comum do MRTK envolve saber qual dispositivo específico (por exemplo, Microsoft HoloLens 2) está sendo usado para executar um aplicativo. Identificar o hardware exato pode ser um desafio em diferentes plataformas. Em vez disso, o MRTK fornece uma maneira de identificar recursos específicos em runtime(por exemplo, se o ponto de extremidade do dispositivo atual dá suporte a mãos articuladas).

## <a name="capabilities"></a>Funcionalidades

A Toolkit de Realidade Misturada fornece a enumeração , que define um conjunto de recursos para os quais um aplicativo pode [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) consultar em runtime.

### <a name="input-system-capabilities"></a>Funcionalidades do sistema de entrada

O sistema de entrada padrão do MRTK dá suporte à consulta dos seguintes recursos:

| Funcionalidade | Descrição |
|---|---|
| ArticuladoHand | Entrada de mão articulada |
| EyeTracking | Direcionamento para o olhar |
| GGVHand | Entrada de mão de gesto de olhar/voz |
| MotionController | Entrada do controlador de movimento |
| VoiceCommand | Comandos de voz usando palavras-chave definidas pelo aplicativo |
| VoiceDictation | Ditado de voz para texto |

O código de exemplo abaixo verifica se o sistema de entrada carregou um provedor de dados com suporte para mãos articuladas.

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a>Funcionalidades de reconhecimento espacial

O sistema padrão de Reconhecimento Espacial do MRTK dá suporte à consulta dos seguintes recursos:

| Funcionalidade | Descrição |
|---|---|
| SpatialAwarenessMesh | Malhas espaciais |
| SpatialAwarenessPlane | Planos espaciais |
| SpatialAwarenessPoint | Pontos espaciais |

Este exemplo verifica se o sistema de reconhecimento espacial carregou um provedor de dados com suporte para malhas espaciais.

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a>Confira também

- [Documentação da API IMixedRealityCapabilityCheck](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [Documentação de enum mixedRealityCapability](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
