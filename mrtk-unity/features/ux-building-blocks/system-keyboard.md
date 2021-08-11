---
title: Teclado do sistema
description: Visão geral do painel de chave do sistema no MRTK
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, teclado do sistema,
ms.openlocfilehash: 4fc7023f6f39d9794011a09810e078f2ebbfc1c01c22e7003d5a3742e4c85921
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224732"
---
# <a name="system-keyboard"></a>Teclado do sistema

![Teclado do sistema](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

Um aplicativo do Unity pode invocar o teclado do sistema a qualquer momento. observe que o teclado do sistema se comportará de acordo com os recursos da plataforma de destino, por exemplo, o teclado no HoloLens 2 dará suporte a interações diretas, enquanto o teclado no HoloLens (1º gen) dará suporte a GGV (olhar, gesto e voz)<sup>[1](/windows/mixed-reality/gaze)</sup>. Além disso, o teclado do sistema não aparecerá ao executar a [comunicação remota do Unity](../tools/holographic-remoting.md) do editor para um HoloLens.

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

Você pode ver um exemplo simples de como abrir o teclado do sistema no `MixedRealityKeyboard.cs` (assets/MRTK/SDK/experimental/Features/UX/MixedRealityKeyboard. cs)

## <a name="see-also"></a>Consulte Também

- [Classes do auxiliar de teclado de realidade misturada](../experimental/mixed-reality-keyboard.md)
