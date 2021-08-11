---
title: Fala
description: configurando a entrada de Fala no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Fala,
ms.openlocfilehash: 00de7854bcb68703fbfd5566b7d502f08ac34efc1ac9434a2c86274f07b6342d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228396"
---
# <a name="speech"></a>Fala

![Menu próximo](../images/input/MRTK_Input_Speech.png)

Os provedores de entrada de fala, como *Windows* entrada de fala, não criam controladores, mas permitem que você defina palavras-chave que gerarão eventos de entrada de fala quando reconhecidos. O **Perfil de Comandos de Fala** no Perfil do Sistema de *Entrada* é o local em que você configura as palavras-chave para reconhecer. Para cada comando, você também pode:

- Selecione uma **ação de entrada** para mapeá-la. Dessa forma, você pode, por exemplo, usar a palavra-chave *Selecionar* para ter o mesmo efeito que um clique do mouse esquerdo, mapeando ambos para a mesma ação.
- **Especifique um código-chave** que produzirá o mesmo evento de fala quando pressionado.
- Adicione uma **chave de localização** que será usada em aplicativos UWP para obter a palavra-chave localizada dos recursos do aplicativo.

<img src="../images/input/SpeechCommandsProfile.png" width="450px" alt="Speech Commands profile">

## <a name="handling-speech-input"></a>Manipulando a entrada de fala

O [**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler) script pode ser adicionado a um GameObject para manipular comandos de fala usando [**UnityEvents**](https://docs.unity3d.com/Manual/UnityEvents.html). Ele mostra automaticamente a lista das palavras-chave definidas do Perfil **de Comandos de Fala**.

<img src="../images/input/SpeechCommands_SpeechInputHandler1.png" width="450px" alt="Speech Input handler">

Atribua **SpeechConfirmationTooltip.prefab** opcional para exibir o rótulo de dica de ferramenta de confirmação animada no reconhecimento.

<img src="../images/input/SpeechCommands_SpeechInputHandler2.png" alt="Sppech input handler 2">

Como alternativa, os desenvolvedores podem implementar [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) a interface em um componente de script personalizado para manipular eventos de entrada de [fala](input-events.md#input-event-interface-example).

## <a name="example-scene"></a>Cena de exemplo

A **cena SpeechInputExample,** em `MRTK/Examples/Demos/Input/Scenes/Speech` , mostra como usar a fala. Você também pode escutar eventos de comando de fala diretamente em seu próprio script implementando [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) (consulte tabela de [manipuladores de eventos](input-events.md)).

<img src="../images/input/SpeechExampleScene.png" width="750px" alt="Speech Example scene">
