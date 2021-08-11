---
title: Teclado de realidade misturada
description: descrição sobre como usar o teclado de realidade misturada
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 068d88483eff8db5466c6b5ff0d2ca8bbc0b5dddee549bb3d87c82fa740bc8fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197003"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>Classes auxiliares de HoloLens de realidade misturada e do teclado

O MRTK fornece vários componentes auxiliares experimentais para auxiliar na inicialização e leitura de texto do [teclado do sistema](../ux-building-blocks/system-keyboard.md).

observe que o teclado do sistema se comportará de acordo com os recursos da plataforma de destino, por exemplo, o teclado no HoloLens 2 dará suporte a interações diretas, enquanto o teclado no HoloLens (1º gen) dará suporte a GGV<sup>[1](/windows/mixed-reality/gaze)</sup>. Além disso, o teclado do sistema não aparecerá ao executar a [comunicação remota do Unity](../tools/holographic-remoting.md) do editor para um HoloLens.

## <a name="mixedrealitykeyboard"></a>MixedRealityKeyboard

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) é um componente que fornece métodos para iniciar e fechar um teclado do sistema, bem como interagir com texto inserido pelo teclado.  

### <a name="how-to-use"></a>Como usar

1. Anexe o [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) componente a qualquer objeto.
2. Chame `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` para mostrar e ocultar o teclado, e manipule os `OnShowKeyboard` `OnHideKeyboard` eventos e `OnCommitText` para manipular quando o teclado é mostrado, oculto e quando a tecla Enter é pressionada.

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>Campos de entrada TMP_KeyboardInputField e UI_KeyboardInputField

As [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes e são componentes que podem ser adicionados aos campos de entrada de texto para invocar automaticamente o teclado do sistema quando clicado e atualizar o conteúdo do campo de entrada de texto conforme o usuário digita o texto.

### <a name="how-to-use"></a>Como usar

1. Crie um campo de entrada para UnityUI ou TextMeshPro.
2. Adicione o [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) componente correspondente ou [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) ao objeto de jogo campo de entrada.

Pré-fabricados para os campos de entrada UnityUI e TextMeshPro (TMPro) estão disponíveis em "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"

Um exemplo de como o para usar TMP_KeyboardInputField e UI_KeyboardInputField está em "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"