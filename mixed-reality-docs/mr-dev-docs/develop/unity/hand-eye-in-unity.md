---
title: Controle de mão e de olho articulado no Unity
description: Saiba mais sobre as duas maneiras principais de agir em seu olhar no Unity, gestos de mão e controladores de movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimento, Unity, olhar, entrada, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: 2daa02a0681fe4f3da24fa32379e10877750af7e
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110230"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Controle de mão e de olho articulado no Unity

O HoloLens 2 introduziu alguns recursos novos e empolgantes, como controle de mão e de olho articulado.

A maneira mais fácil de aproveitar o novo recurso no Unity é por meio de MRTK. Também há alguns exemplos de cenas para ajudá-lo a começar.

* [Introdução à mão articulada no MRTK](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
* [Introdução ao acompanhamento de olho no MRTK](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Blocos de construção com suporte a mãos, olhos e outros no MRTK

O MRTK v2 fornece um conjunto de controles de interface do usuário e blocos de construção para ajudá-lo a acelerar seu desenvolvimento.

|  [![Botão](images/MRTK_Button_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) [Botão](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) | [Caixa](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) delimitadora de [ ![ caixa delimitada](images/MRTK_BoundingBox_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) | [Manipulador de manipulação](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) do [ ![ manipulador de manipulação](images/MRTK_Manipulation_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) |
|:--- | :--- | :--- |
| Um controle de botão, que dá suporte a vários métodos de entrada, incluindo a mão HoloLens2's articulada | Interface do usuário padrão para manipular objetos no espaço 3D | Script para manipular objetos com uma ou duas mãos |
|  [![Ardósia](images/MRTK_Slate_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) [Ardósia](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) | [![Teclado do sistema](images/MRTK_SystemKeyboard_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) [Teclado do sistema](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) | [![Interativo](images/InteractableExamples.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) [Interativo](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) |
| plano de estilo 2D, que dá suporte à rolagem com entrada de mão articulada | Exemplo de script de uso do teclado do sistema no Unity  | Um script para tornar os objetos interativos com os estados visuais e o suporte a temas |
|  [![Solucionador](images/MRTK_Solver_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) [Solucionador](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) | [![Coleção de objetos](images/MRTK_ObjectCollection_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) [Coleção de objetos](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) | [![Dica de ferramenta](images/MRTK_Tooltip_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) [Dica de ferramenta](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) |
| Vários comportamentos de posicionamento de objeto, como marca, bloqueio de corpo, tamanho de exibição constante e Magnetism de superfície | Script para dispor uma matriz de objetos em uma forma tridimensional | A interface do usuário de anotações com sistema flexível âncora/dinâmico, que pode ser usada para rotular os controladores de movimento e o objeto. |
|  [![Barra de aplicativos](images/MRTK_AppBar_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) [Barra de aplicativos](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) | [![Ponteiros](images/MRTK_Pointer_Main.png)](/windows/mixed-reality/mrtk-unity/features/input/pointers) [Ponteiros](/windows/mixed-reality/mrtk-unity/features/input/pointers) | [![Visualização da ponta do dedo](images/MRTK_FingertipVisualization_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) [Visualização da ponta do dedo](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) |
| Interface do usuário para ativação manual da caixa delimitadora | Saiba mais sobre os vários tipos de ponteiros | A unificação Visual está na ponta, o que melhora a confiança para a interação direta |
|  [![Acompanhamento ocular: seleção de destino](images/mrtk_et_targetselect.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) [Acompanhamento ocular: seleção de destino](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) | [![Acompanhamento ocular: navegação](images/mrtk_et_navigation.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) [Acompanhamento ocular: navegação](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) |
| Combine a entrada de olhos, voz e mão para selecionar com rapidez e facilidade os hologramas em sua cena | Saiba como rolar automaticamente o texto ou ampliar o conteúdo focado com base no que você está vendo| Exemplos de registro em log, carregamento e visualização do que os usuários estão olhando em seu aplicativo |

## <a name="example-scenes"></a>Cenas de exemplo

Explore os vários tipos de interações e controles de interface do usuário do MRTK nesta [cena de exemplo](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples).

Você pode encontrar outros exemplos de cenas no [GitHub do kit de ferramentas da realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity) em **assets/MixedRealityToolkit. examples/demos** Folder.

[![Cena de exemplo](images/MRTK_Examples.png)](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

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