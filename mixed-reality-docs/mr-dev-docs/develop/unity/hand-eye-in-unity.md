---
title: Controle de mão e de olho articulado no Unity
description: Saiba mais sobre as duas maneiras principais de agir em seu olhar no Unity, gestos de mão e controladores de movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimento, Unity, olhar, entrada, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: ac122a0353bc5a35202c9aeba0d27c489b72fd68
ms.sourcegitcommit: 6ae047bf0d78819ee68681f7d9450961efbc8595
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103022868"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Controle de mão e de olho articulado no Unity

O HoloLens 2 introduziu alguns recursos novos e empolgantes, como controle de mão e de olho articulado.

A maneira mais fácil de aproveitar o novo recurso no Unity é por meio de MRTK. Também há alguns exemplos de cenas para ajudá-lo a começar.

* [Introdução à mão articulada no MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/hand-tracking.md)
* [Introdução ao acompanhamento de olho no MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-main.md)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Blocos de construção com suporte a mãos, olhos e outros no MRTK 

O MRTK v2 fornece um conjunto de controles de interface do usuário e blocos de construção para ajudá-lo a acelerar seu desenvolvimento.

|  [![Botão](images/MRTK_Button_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button.md) [Botão](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button.md) | [Caixa](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box.md) delimitadora de [ ![ caixa delimitada](images/MRTK_BoundingBox_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box.md) | [Manipulador de manipulação](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler.md) do [ ![ manipulador de manipulação](images/MRTK_Manipulation_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler.md) |
|:--- | :--- | :--- |
| Um controle de botão, que dá suporte a vários métodos de entrada, incluindo a mão HoloLens2's articulada | Interface do usuário padrão para manipular objetos no espaço 3D | Script para manipular objetos com uma ou duas mãos |
|  [![Ardósia](images/MRTK_Slate_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate.md) [Ardósia](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate.md) | [![Teclado do sistema](images/MRTK_SystemKeyboard_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard.md) [Teclado do sistema](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard.md) | [![Interativo](images/InteractableExamples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable.md) [Interativo](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable.md) |
| plano de estilo 2D, que dá suporte à rolagem com entrada de mão articulada | Exemplo de script de uso do teclado do sistema no Unity  | Um script para tornar os objetos interativos com os estados visuais e o suporte a temas |
|  [![Solucionador](images/MRTK_Solver_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver.md) [Solucionador](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver.md) | [![Coleção de objetos](images/MRTK_ObjectCollection_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection.md) [Coleção de objetos](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection.md) | [![Dica de ferramenta](images/MRTK_Tooltip_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip.md) [Dica de ferramenta](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip.md) |
| Vários comportamentos de posicionamento de objeto, como marca, bloqueio de corpo, tamanho de exibição constante e Magnetism de superfície | Script para dispor uma matriz de objetos em uma forma tridimensional | A interface do usuário de anotações com sistema flexível âncora/dinâmico, que pode ser usada para rotular os controladores de movimento e o objeto. |
|  [![Barra de aplicativos](images/MRTK_AppBar_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar.md) [Barra de aplicativos](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar.md) | [![Ponteiros](images/MRTK_Pointer_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/pointers.md) [Ponteiros](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/pointers.md) | [![Visualização da ponta do dedo](images/MRTK_FingertipVisualization_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization.md) [Visualização da ponta do dedo](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization.md) |
| Interface do usuário para ativação manual da caixa delimitadora | Saiba mais sobre os vários tipos de ponteiros | A unificação Visual está na ponta, o que melhora a confiança para a interação direta |
|  [![Acompanhamento ocular: seleção de destino](images/mrtk_et_targetselect.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-target-selection.md) [Acompanhamento ocular: seleção de destino](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-target-selection.md) | [![Acompanhamento ocular: navegação](images/mrtk_et_navigation.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-navigation.md) [Acompanhamento ocular: navegação](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-navigation.md) | [![Acompanhamento ocular: mapa de calor](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) [Acompanhamento ocular: mapa de calor](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Combine a entrada de olhos, voz e mão para selecionar com rapidez e facilidade os hologramas em sua cena | Saiba como rolar automaticamente o texto ou ampliar o conteúdo focado com base no que você está vendo| Exemplos de registro em log, carregamento e visualização do que os usuários estão olhando em seu aplicativo |

## <a name="example-scenes"></a>Cenas de exemplo

Explore os vários tipos de interações e controles de interface do usuário do MRTK nesta [cena de exemplo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html).

Você pode encontrar outros exemplos de cenas no [GitHub do kit de ferramentas da realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity) em **assets/MixedRealityToolkit. examples/demos** Folder.

[![Cena de exemplo](images/MRTK_Examples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples.md)

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos blocos de construção do MRTK Core. Deste ponto, você pode prosseguir para o próximo bloco de construção:

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
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
