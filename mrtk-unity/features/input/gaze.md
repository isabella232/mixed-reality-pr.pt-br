---
title: Focar
description: Docummentation em tipos de olhar no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, olhar,
ms.openlocfilehash: 95dad85ca8154d35f73906b53019d3a52ced546f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176910"
---
# <a name="gaze"></a>Focar

[Olhar](/windows/mixed-reality/gaze) é uma forma de entrada que interage com o mundo com base em onde o usuário está olhando. Olhar existe em dois tipos diferentes

## <a name="head-gaze"></a>Foco da cabeça

Esse tipo de olhar é baseado na direção em que a cabeça/câmera está olhando. O Head olhar está ativo em sistemas que não dão suporte a olhar de olho, ou em casos em que o hardware possa dar suporte a olho olhar, mas o conjunto certo de [permissões e configuração](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) não foi realizado.

o olhar de cabeçalho é geralmente associado a interações de estilo HoloLens 1 envolvendo examinar o objeto, colocando-o no centro do quadro Holographic e, em seguida, executando o gesto de toque do ar.

## <a name="eye-gaze"></a>Foco com o olhar

Esse tipo de olhar é baseado em onde os olhos do usuário estão olhando. O olho olhar está presente apenas em sistemas que dão suporte ao controle de olho. Consulte a [documentação de acompanhamento de olho](eye-tracking/eye-tracking-main.md) para obter mais detalhes sobre como usar o olho olhar.

## <a name="gazeprovider"></a>GazeProvider

A funcionalidade olhar (cabeça e olho) é fornecida pelo [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider). Esse provedor pode ser configurado na seção de *ponteiro* do perfil do sistema de entrada:

![Ponto de entrada de configuração do olhar](../images/input/GazeConfigurationEntrypoint.png)

Assim como outras fontes de entrada, o provedor olhar interage com objetos na cena por meio do uso de um ponteiro [(consulte este documento para obter informações sobre ponteiros)](../../architecture/controllers-pointers-and-focus.md).
No caso do provedor olhar, seu ponteiro é implementado por meio do `InternalGazePointer` e não é configurado por meio de um perfil.

É possível substituir o GazeProvider de ações por uma implementação alternativa alterando o *tipo de provedor olhar* para fazer referência a uma classe diferente que implementa [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) e [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).
Geralmente, é recomendável usar o GazeProvider de estoque (e problemas de arquivamento ao localizar bugs), já que a nova implementação do GazeProvider não é trivial.

### <a name="alternative-platform-provided-gaze-poses"></a>Olhar de pose alternativas fornecidas pela plataforma

Por padrão, o MRTK GazeProvider usa o centro do quadro da câmera como a origem olhar. algumas plataformas, como Windows Mixed Reality no HoloLens 2, fornecem uma pose olhar definida como alternativa. Isso é gerenciado por meio da `Use Head Gaze Override` configuração nas configurações de olhar. Quando habilitado, a substituição olhar alternativa será usada. Quando desabilitado, a origem do centro de quadros padrão será usada. especificamente, para o HoloLens 2, o ângulo de olhar será gerado em vários graus para considerar o conforto do usuário no uso de sua cabeça para o direcionamento.

## <a name="usage"></a>Uso

### <a name="how-get-the-current-gaze-target"></a>Como obter o destino de olhar atual

Este exemplo mostra como obter o objeto de jogo atual que é direcionado pelo usuário olhar.

```c#
void LogCurrentGazeTarget()
{
    if (CoreServices.InputSystem.GazeProvider.GazeTarget)
    {
        Debug.Log("User gaze is currently over game object: "
            + CoreServices.InputSystem.GazeProvider.GazeTarget)
    }
}
```

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a>Como obter a origem e a direção do olhar atual

Este exemplo mostra como obter o Vector3 que representa a direção do usuário olhar e a origem (o ponto do qual a direção está indo).

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
