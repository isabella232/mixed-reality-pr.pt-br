---
title: Como detectar funcionalidades de plataforma
description: Detalhes de diferentes recursos que o MRTK dá suporte
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, recursos,
ms.openlocfilehash: e6f5a70120b2634a4c8c75cdca3d8b369967c4b0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143864"
---
# <a name="detecting-platform-capabilities"></a>Detectando recursos de plataforma

Uma pergunta comum feita pelo MRTK envolve saber qual dispositivo específico (ex: Microsoft HoloLens 2) está sendo usado para executar um aplicativo. Identificar o hardware exato pode ser desafiador em diferentes plataformas. Em vez disso, o MRTK fornece uma maneira de identificar recursos específicos em tempo de execução, (por exemplo, se o ponto de extremidade do dispositivo atual der suporte a mãos articuladas).

## <a name="capabilities"></a>Funcionalidades

O kit de ferramentas de realidade misturada fornece a [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeração, que define um conjunto de recursos para os quais um aplicativo pode consultar em tempo de execução.

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
