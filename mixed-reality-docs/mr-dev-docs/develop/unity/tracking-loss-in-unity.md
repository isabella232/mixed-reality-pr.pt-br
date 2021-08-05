---
title: Como controlar a perda no Unity
description: Saiba como lidar com a perda de acompanhamento manual e padrão em um aplicativo de realidade misturada do Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, perda de acompanhamento, imagem de perda de acompanhamento, sondagem, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: fe11c88bec60042901bd7ebb5c55116da97b6e28f0e44e889ef517a03d67245a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211348"
---
# <a name="tracking-loss-in-unity"></a>Como controlar a perda no Unity

Quando o dispositivo não consegue se localizar no mundo, o aplicativo passa por "perda de acompanhamento". Por padrão, o Unity pausa o loop de atualização e exibe uma imagem inicial para o usuário sempre que o controle é perdido. Depois que o acompanhamento for recuperado, a imagem inicial desaparecerá e o loop de atualização continuará.

Como alternativa, o usuário pode lidar manualmente com essa transição, optando por não fazer a configuração. Todo o conteúdo parece se tornará o corpo bloqueado durante a perda de acompanhamento se nada for feito para lidar com isso.

## <a name="default-handling"></a>Tratamento padrão

O loop de atualização e todas as mensagens e eventos serão parados durante o acompanhamento da perda por padrão. Ao mesmo tempo, uma imagem será exibida para o usuário. Você pode personalizar essa imagem indo para Editar->Configurações->Player, clicando em Imagem Inicial e definindo a imagem perda de rastreamento holográfico.

## <a name="manual-handling"></a>Manipulação manual

Para lidar manualmente com a perda de acompanhamento, você precisa ir para Editar configurações do Project Configurações Player Universal Windows Platform na guia Imagem inicial Windows Holográfica e desmarcar "Em Pausa de Perda de Acompanhamento e Mostrar  >    >    >    >    >   Imagem". Depois disso, você precisa lidar com alterações de acompanhamento com as APIs especificadas abaixo.

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldManager*

* O World Manager expõe um evento para detectar o acompanhamento perdido/obtido (*WorldManager.OnPositionalLocatorStateChanged*) e uma propriedade para consultar o estado atual (*WorldManager.state*)
* Quando o estado de acompanhamento não estiver ativo, a câmera não parece será traduzida no mundo virtual, mesmo que o usuário traduza. Os objetos não corresponderão mais a nenhum local físico e todos aparecerão com o corpo bloqueado.

Ao lidar com alterações de acompanhamento por conta própria, você precisa sondar a propriedade de estado de cada quadro ou manipular o *evento OnPositionalLocatorStateChanged.*

### <a name="polling"></a>Sondagem

O estado mais importante é *PositionalLocatorState.Active,* o que significa que o acompanhamento é totalmente funcional. Qualquer outro estado resultará apenas em deltas rotacionais para a câmera principal. Por exemplo:

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Manipulando o evento OnPositionalLocatorStateChanged

Mais convenientemente, você também pode assinar *OnPositionalLocatorStateChanged* para lidar com as transições:

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a>Confira também

* [Manipulando a perda de acompanhamento no DirectX](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
