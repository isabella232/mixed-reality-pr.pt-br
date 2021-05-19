---
title: Teclado de realidade misturada
description: descrição sobre Como usar o teclado de realidade misturada
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 9fa81db9a71f1d0ce32bdd80a123eb072fc26fc5
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143395"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>Classes auxiliares de teclado do HoloLens e realidade misturada

O MRTK fornece vários componentes auxiliares experimentais para ajudar a iniciar e ler texto do [Teclado do Sistema.](../ux-building-blocks/system-keyboard.md)

Observe que o teclado do sistema se comportará de acordo com os recursos da plataforma de destino, por exemplo, o teclado no HoloLens 2 dará suporte a interações diretas à mão, enquanto o teclado no HoloLens (1ª geração) dará suporte ao GGV<sup>[1.](/windows/mixed-reality/gaze)</sup> Além disso, o teclado do sistema não será aparecer ao executar a [Remoting do Unity](../tools/holographic-remoting.md) do editor para um HoloLens.

## <a name="mixedrealitykeyboard"></a>MixedRealityKeyboard

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) é um componente que fornece métodos para iniciar e fechar um teclado do sistema, bem como interagir com o texto inserido pelo teclado.  

### <a name="how-to-use"></a>Como usar

1. Anexe [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) o componente a qualquer objeto.
2. Chame para mostrar e ocultar o teclado e manipular os eventos e para manipular quando o teclado for mostrado, oculto e quando a `Show()` `Hide()` tecla Enter for `OnShowKeyboard` `OnHideKeyboard` `OnCommitText` pressionada.

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>Campos de entrada TMP_KeyboardInputField e UI_KeyboardInputField

As classes e são componentes que podem ser adicionados aos campos de entrada de texto para invocar automaticamente o teclado do sistema quando clicado e atualizar o conteúdo do campo de entrada de texto à medida que o usuário ins dá entrada [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) de texto.

### <a name="how-to-use"></a>Como usar

1. Crie um campo de entrada para UnityUI ou TextMeshPro.
2. Adicione o componente [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) ou correspondente ao objeto do jogo de campo de [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) entrada.

Os pré-requisitos para os campos de entrada do UnityUI e os campos de entrada TextMeshPro (TMPro) estão disponíveis em "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"

Um exemplo de como usar TMP_KeyboardInputField e UI_KeyboardInputField está em "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"