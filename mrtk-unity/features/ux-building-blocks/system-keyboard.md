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
# <a name="system-keyboard"></a><span data-ttu-id="6c687-104">Teclado do sistema</span><span class="sxs-lookup"><span data-stu-id="6c687-104">System keyboard</span></span>

![Teclado do sistema](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

<span data-ttu-id="6c687-106">Um aplicativo unity pode invocar o teclado do sistema a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="6c687-106">A Unity application can invoke the system keyboard at any time.</span></span> <span data-ttu-id="6c687-107">Observe que o teclado do sistema se comportará de acordo com as funcionalidades da plataforma de destino, por exemplo, o teclado no HoloLens 2 dará suporte a interações diretas à mão, enquanto o teclado no HoloLens (1ª geração) dará suporte ao GGV (Gaze, Gesto e Voz)<sup>[1](/windows/mixed-reality/gaze)</sup>.</span><span class="sxs-lookup"><span data-stu-id="6c687-107">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice)<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="6c687-108">Além disso, o teclado do sistema não será aparecer ao executar a [Remoting do Unity](../tools/holographic-remoting.md) do editor para um HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6c687-108">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="how-to-invoke-the-system-keyboard"></a><span data-ttu-id="6c687-109">Como invocar o teclado do sistema</span><span class="sxs-lookup"><span data-stu-id="6c687-109">How to invoke the system keyboard</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a><span data-ttu-id="6c687-110">Como ler a entrada</span><span class="sxs-lookup"><span data-stu-id="6c687-110">How to read the input</span></span>

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

## <a name="system-keyboard-example"></a><span data-ttu-id="6c687-111">Exemplo de teclado do sistema</span><span class="sxs-lookup"><span data-stu-id="6c687-111">System keyboard example</span></span>

<span data-ttu-id="6c687-112">Você pode ver um exemplo simples de como abrir o teclado do sistema `MixedRealityKeyboard.cs` em (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span><span class="sxs-lookup"><span data-stu-id="6c687-112">You can see a simple example of how to bring up system keyboard in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span></span>

## <a name="see-also"></a><span data-ttu-id="6c687-113">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="6c687-113">See Also</span></span>

- [<span data-ttu-id="6c687-114">Classes auxiliares de teclado de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="6c687-114">Mixed Reality Keyboard Helper Classes</span></span>](../experimental/mixed-reality-keyboard.md)
