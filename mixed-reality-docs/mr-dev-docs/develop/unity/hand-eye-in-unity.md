---
title: Controle de mão e de olho articulado no Unity
description: Há duas maneiras principais de agir em seu olhar no Unity, gestos de mão e controladores de movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimento, Unity, olhar, entrada, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: de8ea7968c36722f3690c5515e4f69e576898524
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97011546"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Controle de mão e de olho articulado no Unity

O HoloLens 2 introduziu alguns recursos novos e empolgantes, como controle de mão e de olho articulado.

A maneira mais fácil de aproveitar o novo recurso no Unity é por meio de MRTK. Também há alguns exemplos de cenas para ajudá-lo a começar.

* [Introdução à mão articulada no MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/HandTracking.html)
* [Introdução ao acompanhamento de olho no MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Blocos de construção com suporte a mãos, olhos e outros no MRTK 

O MRTK v2 fornece um conjunto de controles de interface do usuário e blocos de construção para ajudá-lo a acelerar seu desenvolvimento.

|  [Botão](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) de [ ![ botão](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | [Caixa](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) delimitadora de [ ![ caixa delimitada](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) | [Manipulador de manipulação](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) do [ ![ manipulador de manipulação](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| Um controle de botão, que dá suporte a vários métodos de entrada, incluindo a mão HoloLens2's articulada | Interface do usuário padrão para manipular objetos no espaço 3D | Script para manipular objetos com uma ou duas mãos |
|  [Ardósia](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) - [ ![ ardósia](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | [Teclado do sistema](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) de [ ![ teclado do sistema](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | [ ![ Interagir](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) interagindo [](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| plano de estilo 2D, que dá suporte à rolagem com entrada de mão articulada | Exemplo de script de uso do teclado do sistema no Unity  | Um script para tornar os objetos interagirem com os Estados visuais e o suporte a temas |
|  [Solucionador](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) de [ ![ resolução](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [Coleção de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) da [ ![ coleção de objetos](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | [Dica de ferramenta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) [ ![ ToolTip](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| Vários comportamentos de posicionamento de objeto, como marca, bloqueio de corpo, tamanho de exibição constante e Magnetism de superfície | Script para dispor uma matriz de objetos em uma forma tridimensional | A interface do usuário de anotações com sistema flexível âncora/dinâmico, que pode ser usada para rotular os controladores de movimento e o objeto. |
|  [Barra de aplicativos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) da [ ![ barra de aplicativos](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [Ponteiros](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) de [ ![ ponteiros](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) | [Visualização](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) da [ ![ disposição da visualização](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) |
| Interface do usuário para ativação manual da caixa delimitadora | Saiba mais sobre os vários tipos de ponteiros | A unificação Visual está na ponta, o que melhora a confiança para a interação direta |
|  [ ![ Acompanhamento de olho:](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) acompanhamento de olho de seleção de destino [: seleção de destino](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [ ![ Acompanhamento de olho:](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) acompanhamento de olho de navegação [: navegação](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [ ![ Acompanhamento de olho:](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) acompanhamento de olho do mapa de calor [: mapa de calor](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Combine a entrada de olhos, voz e mão para selecionar com rapidez e facilidade os hologramas em sua cena | Saiba como rolar automaticamente o texto ou ampliar o conteúdo focado com base no que você está vendo| Exemplos de registro em log, carregamento e visualização do que os usuários estão olhando em seu aplicativo |

## <a name="example-scenes"></a>Cenas de exemplo

Explore os vários tipos de interações e controles de interface do usuário do MRTK nesta [cena de exemplo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html).

Você pode encontrar outros exemplos de cenas no [GitHub do kit de ferramentas da realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity) em **assets/MixedRealityToolkit. examples/demos** Folder.

[![Cena de exemplo](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos blocos de construção do MRTK Core. A partir daqui, você pode continuar para o próximo bloco de construção:

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
