---
title: Acompanhamento de mão e olho articulado no Unity
description: Saiba mais sobre as duas principais maneiras de tomar medidas em seu olhar no Unity, gestos de mão e controladores de movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimento, unity, gaze, entrada, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, MRTK, Realidade Misturada Toolkit
ms.openlocfilehash: 005b817574e6d3600b9c43e443432203418b58a2258e2938614cc549ab7539c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223776"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Acompanhamento de mão e olho articulado no Unity

HoloLens 2 introduziu algumas funcionalidades novas e interessantes, como a Mão Articulada e o Acompanhamento Ocular.

A maneira mais fácil de aproveitar a nova funcionalidade no Unity é por meio do MRTK. Também há alguns exemplos de cenas para ajudá-lo a começar.

* [Começar a trabalhar com a mão articulada no MRTK](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
* [Começar a trabalhar com o Acompanhamento Ocular no MRTK](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Blocos de construção que suportam mãos, olhos e outros no MRTK

O MRTK v2 fornece um conjunto de controles de interface do usuário e blocos de construção para ajudá-lo a acelerar o desenvolvimento.

|  [![Botão](images/MRTK_Button_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) [Botão](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) | [ ![ Caixa delimitante caixa](images/MRTK_BoundingBox_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) [delimitada](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) | [ ![ Manipulador de manipulação do](images/MRTK_Manipulation_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) [manipulador de manipulação](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) |
|:--- | :--- | :--- |
| Um controle de botão, que dá suporte a vários métodos de entrada, incluindo a mão articulada do HoloLens2 | Interface do usuário padrão para manipular objetos no espaço 3D | Script para manipular objetos com uma ou duas mãos |
|  [![Ardósia](images/MRTK_Slate_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) [Ardósia](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) | [![Teclado do sistema](images/MRTK_SystemKeyboard_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) [Teclado do sistema](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) | [![Interativo](images/InteractableExamples.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) [Interativo](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) |
| Plano de estilo 2D, que dá suporte à rolagem com entrada de mão articulada | Exemplo de script de uso do teclado do sistema no Unity  | Um script para tornar os objetos interativos com os estados visuais e o suporte a temas |
|  [![Solucionador](images/MRTK_Solver_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) [Solucionador](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) | [![Coleção de objetos](images/MRTK_ObjectCollection_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) [Coleção de objetos](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) | [![Dica de ferramenta](images/MRTK_Tooltip_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) [Dica de ferramenta](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) |
| Vários comportamentos de posicionamento de objeto, como tag-along, bloqueio do corpo, tamanho da exibição constante e surface | Script para estabelecer uma matriz de objetos em uma forma tridimensional | Interface do usuário de anotação com sistema de âncora/pivô flexível, que pode ser usado para rotular controladores de movimento e objeto. |
|  [![Barra de aplicativos](images/MRTK_AppBar_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) [Barra de aplicativos](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) | [![Ponteiros](images/MRTK_Pointer_Main.png)](/windows/mixed-reality/mrtk-unity/features/input/pointers) [Ponteiros](/windows/mixed-reality/mrtk-unity/features/input/pointers) | [![Visualização da ponta do dedo](images/MRTK_FingertipVisualization_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) [Visualização da ponta do dedo](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) |
| Interface do usuário para ativação manual do Bounding Box | Saiba mais sobre os vários tipos de ponteiros | Recursos visuais na ponta do dedo, o que melhora a confiança para a interação direta |
|  [![Acompanhamento ocular: seleção de destino](images/mrtk_et_targetselect.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) [Acompanhamento ocular: seleção de destino](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) | [![Acompanhamento ocular: navegação](images/mrtk_et_navigation.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) [Acompanhamento ocular: navegação](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) |
| Combine os olhos, a voz e a entrada da mão para selecionar hologramas de maneira rápida e sem esforço em sua cena | Saiba como rolar texto automaticamente ou ampliar o conteúdo focado com base no que você está vendo| Exemplos de registro em log, carregamento e visualização do que os usuários estão vendo em seu aplicativo |

## <a name="example-scenes"></a>Cenas de exemplo

Explore os vários tipos de interações e controles de interface do usuário do MRTK nesta [cena de exemplo](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples).

Você pode encontrar outras cenas de exemplo em [Realidade Misturada Toolkit GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity) na pasta **Assets/MixedRealityToolkit.Examples/Demos.**

[![Cena de exemplo](images/MRTK_Examples.png)](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo o percurso de desenvolvimento do Unity que fizemos, você está no meio da exploração dos blocos de construção principais do MRTK. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Mapeamento espacial](spatial-mapping-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Confira também

* [Interação ocular](../../design/eye-gaze-interaction.md)
* [Acompanhamento ocular no HoloLens 2](../../design/eye-tracking.md)
* [Focar e confirmar](../../design/gaze-and-commit.md)
* [Mãos – Manipulação direta](../../design/direct-manipulation.md)
* [Mãos – Gestos](../../design/gaze-and-commit.md#composite-gestures)
* [Mãos – Apontar e confirmar](../../design/point-and-commit.md)
* [Interações instinctuais](../../design/interaction-fundamentals.md)
* [Controladores de movimentos](../../design/motion-controllers.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)