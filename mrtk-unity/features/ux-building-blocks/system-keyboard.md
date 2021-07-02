---
title: Teclado do sistema
description: Visão geral do System Key Board no MRTK
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Teclado do Sistema,
ms.openlocfilehash: 9b1db512a1a4e27a2c41e8e8b5752200c461ee6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176496"
---
# <a name="system-keyboard"></a>Teclado do sistema

![Teclado do sistema](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

Um aplicativo unity pode invocar o teclado do sistema a qualquer momento. Observe que o teclado do sistema se comportará de acordo com as funcionalidades da plataforma de destino, por exemplo, o teclado no HoloLens 2 dará suporte a interações diretas à mão, enquanto o teclado no HoloLens (1ª geração) dará suporte ao GGV (Gaze, Gesto e Voz)<sup>[1](/windows/mixed-reality/gaze)</sup>. Além disso, o teclado do sistema não será aparecer ao executar a [Remoting do Unity](../tools/holographic-remoting.md) do editor para um HoloLens.

## <a name="how-to-invoke-the-system-keyboard"></a>Como invocar o teclado do sistema

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a>Como ler a entrada

```c#
public TouchScreenKeyboard keyboard;

...

private void Update()
{
    if (keyboard != null)
    {
        keyboardText = keyboard.text;
        // Do stuff with keyboardText
    }
}
```

## <a name="system-keyboard-example"></a>Exemplo de teclado do sistema

Você pode ver um exemplo simples de como abrir o teclado do sistema `MixedRealityKeyboard.cs` em (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)

## <a name="see-also"></a>Consulte Também

- [Classes auxiliares de teclado de realidade misturada](../experimental/mixed-reality-keyboard.md)
