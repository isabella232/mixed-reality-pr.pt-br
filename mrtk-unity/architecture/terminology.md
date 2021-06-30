---
title: Terminologia
description: Diferentes termos do sistema de entrada no MRTK.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Entrada,
ms.openlocfilehash: 33f423fba286e9e85e6d0bedac82bff0b7aae81f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121454"
---
# <a name="input-system"></a>Sistema de entrada

O sistema de entrada é um dos maiores sistemas de todos os recursos oferecidos pelo MRTK.
Muitas coisas dentro do kit de ferramentas se baseam nele (ponteiros, foco, pré-requisitos). O código dentro do sistema de entrada é o que permite interações naturais, como pegar e girar entre plataformas.

O sistema de entrada tem algumas de sua própria terminologia que vale a pena definir:

- **Provedores de dados**

    As configurações de entrada no perfil de entrada têm referências a entidades conhecidas como provedores de dados – outra palavra que descreve esses são gerenciadores de dispositivos. Esses são componentes cujo trabalho é estender o sistema de entrada do MRTK intercalando com um sistema subjacente específico. Um exemplo de um provedor é o provedor Windows Mixed Reality, cujo trabalho é conversar com as APIs de Windows Mixed Reality subjacentes e, em seguida, converter os dados dessas APIs em conceitos de entrada específicos do MRTK abaixo. Outro exemplo seria o provedor OpenVR (cujo trabalho é conversar com a versão abstrata do Unity das APIs OpenVR e, em seguida, converter esses dados em conceitos de entrada do MRTK).

- **Controller**

    Uma representação de um controlador físico (seja um controlador de 6 graus de liberdade, uma mão de estilo 1 do HoloLens com suporte a gestos, uma mão totalmente articulada, um controlador de movimento bissexco etc.). Os controladores são gerados por gerenciadores de dispositivos (ou seja, o gerenciador de dispositivos WMR gerará um controlador e gerenciará seu tempo de vida quando vir uma mão articulada entrando em existência).

- **Ponteiro**

    Os controladores usam ponteiros para interagir com objetos de jogo. Por exemplo, o ponteiro de interação próxima é responsável por detectar quando a mão (que é um controlador) está próxima de objetos que se anunciam como dando suporte à "interação próxima". Outros exemplos para ponteiros são ponteiros de longe ou de teletransporte (ou seja, o ponteiro de raio de mão do shell) que usam raios distantes para interagir com o conteúdo com comprimento maior do que o comprimento dos mãos do usuário.

    Os ponteiros são criados pelo gerenciador de dispositivos e anexados a uma fonte de entrada. Para obter todos os ponteiros de um controlador, faça: `controller.InputSource.Pointers`

    Observe que um controlador pode ser associado a muitos ponteiros diferentes ao mesmo tempo. Para garantir que isso não entre em caos, há um mediador de ponteiro que controla quais ponteiros têm permissão para estar ativos (por exemplo, o mediador desabilitará ponteiros de interação distantes quando a interação próxima for detectada).

- **Foco**

    Eventos de ponteiro são enviados para objetos no **foco**. A seleção de foco variará por tipo de ponteiro; um ponteiro de raio de mão usará raycasts, enquanto um ponteiro de ponteiro de ponteiro usará spherecasts. Um objeto deve implementar IMixedRealityFocusHandler para receber o foco. É possível registrar globalmente um objeto para receber eventos de ponteiro não filtrado, mas essa abordagem não é recomendada.

    O componente que atualiza quais objetos estão em foco é [o FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)

- **Cursor**

    Uma entidade associada a um ponteiro que fornece indicações visuais adicionais em torno da interação do ponteiro. Por exemplo, o FingerCursor renderizará um anel ao redor do dedo e poderá girar esse anel quando o dedo estiver próximo de objetos "quase interagindo". Um ponteiro pode ser associado a um único cursor por vez.

- **Interação e manipulação**

    Os objetos podem ser marcados com um script de interação ou manipulação. Isso pode ser por meio de [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) um ou algo como [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

    Por exemplo, NearInteractionGrabbable e NearInteractionTouchable permitem que determinados ponteiros (especialmente ponteiros de interação próxima) saibam em quais objetos podem ser focalizados.

    Interactable e ManipulationHandler são exemplos de componentes que escutam eventos de ponteiro para modificar visuais de interface do usuário ou mover/dimensionar/girar objetos de jogo.

A imagem abaixo captura o build de alto nível (de baixo para cima) da pilha de entrada do MRTK:

![Diagrama do sistema de entrada](../features/images/input/MRTK_InputSystem.png)
