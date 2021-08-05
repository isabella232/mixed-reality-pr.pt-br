---
title: Terminologia
description: Termos diferentes do sistema de entrada no MRTK.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, entrada,
ms.openlocfilehash: 8046501fdab0a7594800a75ad0306a131adaaa6924ffa870c299571cbd4d8e13
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211148"
---
# <a name="input-system"></a>Sistema de entrada

O sistema de entrada é um dos maiores sistemas de todos os recursos oferecidos pelo MRTK.
Muitas coisas no kit de ferramentas se baseiam nele (ponteiros, foco, pré-fabricados). O código dentro do sistema de entrada é o que permite interações naturais, como pegar e girar entre plataformas.

O sistema de entrada tem uma de suas próprias terminologias que vale a pena definir:

- **Provedores de dados**

    As configurações de entrada no perfil de entrada têm referências a entidades conhecidas como provedores de dados-outra palavra que a descreve é gerenciadores de dispositivos. Esses são os componentes cujo trabalho é estender o sistema de entrada MRTK fazendo a interface com um sistema subjacente específico. um exemplo de provedor é o provedor de Windows Mixed Reality, cujo trabalho é conversar com as apis de Windows Mixed Reality subjacentes e, em seguida, converter os dados dessas APIs em conceitos de entrada específicos do MRTK abaixo. Outro exemplo seria o provedor OpenVR (cujo trabalho é falar com a versão abstrata do Unity das APIs do OpenVR e, em seguida, converter esses dados em conceitos de entrada do MRTK).

- **Controller**

    uma representação de um controlador físico (seja um controlador de 6 graus de liberdade, um HoloLens uma mão com um estilo com suporte a gestos, uma mão totalmente articulada, um controlador de movimento leap, etc.). Os controladores são gerados por gerenciadores de dispositivos (ou seja, o Gerenciador de dispositivos WMR gerará um controlador e gerenciará seu tempo de vida quando vir uma mão articulada chegando à existência).

- **Ponteiro**

    Os controladores usam ponteiros para interagir com objetos de jogo. Por exemplo, o ponteiro de interação próxima é responsável por detectar quando a mão (que é um controlador) está perto dos objetos que se anunciam como suporte a ' interação próxima '. Outros exemplos de ponteiros são Teleportation ou ponteiros distantes (ou seja, o ponteiro do lado do Shell) que usam muito raycasts para se envolver com o conteúdo que tem mais de um comprimento de braços do usuário.

    Os ponteiros são criados pelo Gerenciador de dispositivos e, em seguida, anexados a uma fonte de entrada. Para obter todos os ponteiros para um controlador, faça o: `controller.InputSource.Pointers`

    Observe que um controlador pode ser associado a vários ponteiros diferentes ao mesmo tempo. Para garantir que isso não devolvida o caos, há um ponteiro mediador que controla quais ponteiros podem estar ativos (por exemplo, o mediador desabilitará ponteiros de interação distantes quando uma interação próxima for detectada).

- **Foca**

    Os eventos de ponteiro são enviados aos objetos em **foco**. A seleção de foco variará por tipo de ponteiro; um ponteiro de raio à mão usará raycasts, enquanto um ponteiro de envio usará spherecasts. Um objeto deve implementar IMixedRealityFocusHandler para receber o foco. É possível registrar um objeto globalmente para receber eventos de ponteiro não filtrados, mas essa abordagem não é recomendada.

    O componente que atualiza quais objetos estão em foco é o [focusprovider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)

- **Cursor**

    Uma entidade associada a um ponteiro que fornece indicações visuais adicionais sobre a interação do ponteiro. Por exemplo, o FingerCursor renderizará um toque ao redor do dedo e poderá girar esse anel quando o dedo estiver próximo dos objetos ' Near-interagiveis '. Um ponteiro pode ser associado a um único cursor no momento.

- **Interação e manipulação**

    Os objetos podem ser marcados com um script de interação ou manipulação. Isso pode ser por meio de um [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) , ou algo parecido [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

    Por exemplo, NearInteractionGrabbable e NearInteractionTouchable permitem certos ponteiros (principalmente ponteiros de interação quase próximos) para saber quais objetos podem se concentrar.

    Interagir e ManipulationHandler são exemplos de componentes que escutam eventos de ponteiro para modificar elementos visuais da interface do usuário ou mover/dimensionar/girar objetos de jogo.

A imagem abaixo captura a compilação de alto nível (de baixo para cima) da pilha de entrada MRTK:

![Diagrama do sistema de entrada](../features/images/input/MRTK_InputSystem.png)
