---
title: Entrada do teclado no Unity
description: O Unity fornece a classe TouchScreenKeyboard para aceitar a entrada de teclado quando não há nenhum teclado físico disponível.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: teclado, entrada, Unity, touchscreenkeyboard, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, HoloLens, HoloLens 2
ms.openlocfilehash: 398a7c57dc701fc848fe9091949b45b2c1796987
ms.sourcegitcommit: e5bd72d8b92976a6590e0f59706a88e66374934c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098268"
---
# <a name="keyboard-input-in-unity"></a>Entrada do teclado no Unity

**Namespace:** *UnityEngine*<br>
 **Tipo**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Embora o HoloLens dê suporte a muitas formas de entrada, incluindo teclados Bluetooth, a maioria dos aplicativos não pode pressupor que todos os usuários terão uma Keyboard física disponível. Se seu aplicativo requer entrada de texto, alguma forma de teclado na tela deve ser fornecida.

O Unity fornece a classe *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* para aceitar a entrada de teclado quando não há nenhum teclado físico disponível.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Comportamento do teclado do sistema do HoloLens no Unity

No HoloLens, o *TouchScreenKeyboard* aproveita o teclado na tela do sistema e se sobrepõe diretamente à exibição do volumétricos do seu aplicativo Mr. A experiência é semelhante ao uso do teclado nos aplicativos internos do HoloLens. Observe que o teclado do sistema se comportará de acordo com os recursos da plataforma de destino, por exemplo, o teclado no HoloLens 2 dará suporte a interações diretas, enquanto o teclado no HoloLens (1º gen) dará suporte a GGV (olhar, gesto e voz). Além disso, o teclado do sistema não aparecerá ao executar a comunicação remota do Unity do editor para um HoloLens.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Usando o teclado do sistema em seu aplicativo do Unity

### <a name="declare-the-keyboard"></a>Declarar o teclado

Na classe, declare uma variável para armazenar o *TouchScreenKeyboard* e uma variável para conter a cadeia de caracteres que o teclado retorna.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Invocar o teclado

Quando ocorrer um evento solicitando entrada de teclado, use o seguinte para mostrar o teclado.

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

Você pode usar parâmetros adicionais passados para a `TouchScreenKeyboard.Open` função para controlar o comportamento do teclado (por exemplo, definir o texto do espaço reservado ou dar suporte à correção automática). Para obter a lista completa de parâmetros, consulte a [documentação do Unity](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).

### <a name="retrieve-typed-contents"></a>Recuperar conteúdo digitado

O conteúdo pode simplesmente ser recuperado chamando `keyboard.text` . Talvez você queira recuperar o conteúdo por quadro ou apenas quando o teclado for fechado.

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a>Opções de teclado alternativas

Além de usar a classe *TouchScreenKeyboard* diretamente, você também pode obter a entrada do usuário usando o campo de entrada da *interface do usuário* do Unity ou o *campo de entrada TextMeshPro*. Além disso, há uma implementação baseada em *TouchScreenKeyboard* na [cena HandInteractionExamples](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) de [MRTK](/windows/mixed-reality/mrtk-unity) (há um exemplo de interação de teclado no lado esquerdo).

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos recursos e APIs da plataforma de realidade misturada. A partir daqui, você pode continuar com qualquer [tópico](unity-development-overview.md#3-advanced-features) ou ir diretamente para a implantação de seu aplicativo em um dispositivo ou emulador.

> [!div class="nextstepaction"]
> [Implantar no HoloLens ou em headsets de imersão de realidade mista do Windows](../platform-capabilities-and-apis/using-visual-studio.md)
