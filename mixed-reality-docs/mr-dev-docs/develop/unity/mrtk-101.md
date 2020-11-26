---
title: MRTK 101 – Como usar o Kit de Ferramentas de Realidade Misturada do Unity para interações espaciais comuns (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
description: Como usar a o Mixed Reality Toolkit Unity para interações básicas (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada, Windows Mixed Reality, design, aplicativo de exemplo, controles, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.localizationpriority: high
ms.openlocfilehash: 95d8f8c52b226eda7ea1601feffc1464c2ea91c5
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677526"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a>MRTK 101: Como usar o Kit de Ferramentas de Realidade Misturada do Unity para interações espaciais
![MRTK](images/MRTK101/MRTK101Cover.png)

Saiba mais sobre como usar o MRTK para obter alguns dos padrões comuns de interação mais amplamente usados em realidade misturada.

- Como simular as interações de entrada no editor do Unity?
- Como pegar e mover um objeto?
- Como redimensionar um objeto?
- Como mover ou girar um objeto com precisão?
- Como fazer um objeto responder a eventos de entrada?
- Como adicionar comentários visuais?
- Como adicionar comentários de áudio?
- Como usar pré-fabricados do botão no estilo HoloLens 2?
- Como fazer um objeto seguir você?
- Como fazer um objeto olhar para você?

> [!NOTE]
> Este artigo foi atualizado para refletir as alterações na [versão do MRTK v2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)

Todo o conteúdo desta página pode ser testado no editor do Unity com a simulação de entrada do MRTK. Caso ainda não tenha feito isso, siga o [Guia de Instalação do MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) para instalar a última versão do MRTK.

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a>Como simular as interações de entrada no editor do Unity?
O MRTK é compatível com a simulação de entrada no editor. Basta executar sua cena clicando no botão reproduzir do Unity. Use essas chaves para simular a entrada.
Pressione as teclas W, A, S, D para mover a câmera.
Mantenha o botão direito do mouse pressionado e mova o mouse para examinar.
Para exibir as mãos simuladas, pressione a barra de Espaço (à direita) ou a tecla Shift esquerda (à esquerda) para manter as mãos simuladas na exibição, pressione a tecla T ou Y para girar as mãos simuladas, pressione Q ou E (horizontal)/R ou F (vertical)

- [Saiba mais sobre a Simulação de Entrada na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-an-object"></a>Como pegar e mover um objeto?
Para tornar um objeto captável, atribua estes dois scripts: **ObjectManipulator.cs** e **NearInteractionGrabbable.cs** (para captura direta com entrada de acompanhamento de mão articulada): ObjectManipulator dá suporte a interações próximas e distantes. Você pode pegar e mover um objeto com a entrada de acompanhamento de mão articulada do HoloLens 2 (próximo), raio da mão (distante), feixe do controlador de movimento (distante), cursor de olhar do HoloLens e toque no ar (distante).

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a>Como redimensionar um objeto?
**ObjectManipulator.cs** dá suporte à escala/rotação de duas mãos. Isso funciona com vários tipos de entrada, como entrada de mão articulada do HoloLens 2, entrada de olhar + gesto do HoloLens 1 e entrada do controlador de movimento do headset imersivo do Windows Mixed Reality.

- [Saiba mais sobre o Object Manipulator na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>Como mover ou girar um objeto com precisão?
Atribua **BoundsControl.cs** a um objeto para usar a Caixa Delimitadora que é a interface para dimensionar e girar um objeto. Por padrão, ele mostra as alças e os fios azuis no estilo HoloLens 1. Para usar as alças animadas com base em proximidades no estilo HoloLens 2, você precisa atribuir pré-fabricados e materiais. 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [Saiba mais sobre o Controle de Limites na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a>Como fazer um objeto responder a eventos de entrada?
Atribua **PointerHandler.cs** a um objeto. No inspetor, você poderá usar os eventos OnPointerDown(), OnPointerUp(), OnPointerClicked() e OnPointerDragged(). Para usar esses eventos em um script, implemente **IMixedRealityPointerHandler**.

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [Saiba mais sobre o Sistema de Entrada na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>Como adicionar comentários visuais?
Atribua **Interactable.cs** a um objeto. No inspetor, adicione um objeto de destino e crie um tema. Usando perfis de tema de interação, você pode adicionar facilmente comentários visuais a todos os estados de interação de entrada disponíveis.

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


O item passível de interação fornece vários tipos de temas, incluindo o tema do sombreador, que permite controlar as propriedades do sombreador por estado de interação.

- [Saiba mais sobre o item passível de interação na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Outro bloco de construção importante para comentários visuais é o **Sombreador Padrão do MRTK**. Com o sombreador Padrão MRTK, você pode adicionar facilmente efeitos de comentários visuais, como luz de foco e luz de proximidade. Como o sombreador Padrão MRTK executa significativamente menos cálculos do que o sombreador Padrão Unity, você pode criar uma experiência de alto desempenho.

Crie um material e selecione o sombreador "Mixed Reality Toolkit > Padrão". Ou você pode escolher um dos materiais existentes que usam o Sombreador Padrão MRTK.

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Saiba mais sobre o Sombreador Padrão MRTK na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>Como adicionar comentários de áudio?
Adicione **AudioSource** a um objeto. Em seguida, nos scripts que expõem eventos de entrada (por exemplo, Interactable.cs ou PointerHandler.cs), atribua o objeto com AudioSource ao evento e selecione **AudioSource.PlayOneShot()** . Você pode usar seus clipes de áudio ou escolher um dos ativos de áudio do MRTK.

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a>Como usar pré-fabricados do botão no estilo HoloLens 2?
O MRTK fornece vários tipos de botões no estilo shell (sistema operacional) do HoloLens 2. Ele fornece comentários visuais sofisticados, como luz de proximidade, caixa de compactação e um efeito de ondulação na superfície do botão para aprimorar a confiança do usuário.

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

Basta arrastar e soltar um dos **pré-fabricados de botão pressionável de estilo HoloLens 2** na sua cena. O pré-fabricado usa Interactable.cs, que é apresentado acima. Você pode usar eventos expostos, como OnClick(), em ações de gatilho de interação.

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Saiba mais sobre os pré-fabricados de Botão na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a>Como fazer um objeto seguir você?
Atribua o script **RadialView.cs** ou **Follow.cs** a um objeto. Ele faz parte da série de scripts do Solucionador que permite alcançar vários tipos de posicionamento de objeto no espaço 3D. O **SolverHandler.cs** será adicionado automaticamente.
Veja abaixo um exemplo de configuração do RadialView para obter a marca "acompanhamento lento" ao longo do comportamento, assim como o menu Iniciar no shell do HoloLens. Você pode especificar a distância mínima/máxima e os graus de exibição mínimo/máximo. O exemplo a seguir mostra o posicionamento do objeto entre o intervalo de 0,4 m e 0,8 m dentro de 15°. Ajuste os valores de Tempo de Lerp para tornar a atualização posicional mais rápida ou mais lenta.

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [Saiba mais sobre Solucionadores na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a>Como fazer um objeto olhar para você?
Atribua o script **Billboard.cs** a um objeto. Ele sempre vai olhar para você, independentemente da sua posição. Você pode especificar a opção de eixo dinâmico.

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


Pronto para criar experiências incríveis para realidade misturada? Visite as páginas abaixo e saiba mais sobre MRTK e realidade misturada.

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Designer de UX @Microsoft</td>
</tr>
</table>

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unity, você está no meio da exploração dos principais blocos de construção do MRTK. De lá, você pode prosseguir para o próximo bloco de construção: 

> [!div class="nextstepaction"]
> [Câmera](camera-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Confira também
* [Guia de Instalação do MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [Mixed Reality Toolkit-Unity (MRTK) – GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Portal de documentação do MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Diretrizes de portabilidade do HoloToolkit para o MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
