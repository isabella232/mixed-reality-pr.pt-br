---
title: Como controlar a perda no Unity
description: Tratamento da perda de controle em um aplicativo do Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, perda de controle, imagem de perda de rastreamento, sondagem, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual
ms.openlocfilehash: 52b81069e6b9f94a2a6a4fb552be4234cf43d1f0
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678415"
---
# <a name="tracking-loss-in-unity"></a>Como controlar a perda no Unity

Quando o dispositivo não consegue se localizar no mundo, o aplicativo tem "perda de rastreamento". Por padrão, o Unity pausará o loop de atualização e exibirá uma imagem de abertura para o usuário. Quando o rastreamento é retomado, a imagem de abertura desaparece e o loop de atualização continua.

Como alternativa, o usuário pode lidar com essa transição manualmente, recusando a configuração. Todo o conteúdo parecerá ficar bloqueado durante a perda de rastreamento se nada for feito para tratá-lo.

## <a name="default-handling"></a>Manipulação padrão

Por padrão, o loop Update do aplicativo, bem como todas as mensagens e eventos, serão interrompidos durante a perda de rastreamento. Ao mesmo tempo, uma imagem será exibida para o usuário. Você pode personalizar essa imagem acessando configurações de >de edição – >Player, clicando em imagem de abertura e definindo a imagem de perda de rastreamento de Holographic.

## <a name="manual-handling"></a>Manipulação manual

Para tratar manualmente a perda de rastreamento, você precisa ir para **Editar**  >  **configurações de projeto**  >  **Player**  >  **plataforma universal do Windows guia Configurações**  >  **imagem de splash**  >  **Windows Holographic** e desmarcar "durante a perda de controle Pause e show image". Depois, você precisa lidar com as alterações de controle com as APIs especificadas abaixo.

**Namespace:** *UnityEngine. XR. WSA*<br>
**Tipo:** *worldmanager*

* O World Manager expõe um evento para detectar o controle perdido/obtido (*worldmanager. OnPositionalLocatorStateChanged*) e uma propriedade para consultar o estado atual (*worldmanager. State*)
* Quando o estado de acompanhamento não estiver ativo, a câmera não parecerá traduzir no mundo virtual mesmo que o usuário se traduz. Isso significa que os objetos não corresponderão mais a qualquer local físico e todos serão exibidos no corpo bloqueado.

Ao lidar com alterações de controle por conta própria, você precisa sondar a propriedade de estado em cada quadro ou manipular o evento *OnPositionalLocatorStateChanged* .

### <a name="polling"></a>Sondagem

O estado mais importante é *PositionalLocatorState. Active* , o que significa que o controle é totalmente funcional. Qualquer outro Estado resultará em apenas deltas rotacionais para a câmera principal. Por exemplo:

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

Como alternativa e mais conveniente, você também pode assinar o *OnPositionalLocatorStateChanged* para lidar com as transições:

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

## <a name="see-also"></a>Veja também
* [Lidando com a perda de controle no DirectX](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
