---
title: Mural e tag-along
description: Os objetos com o mural sempre se orientam para enfrentar o usuário.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, mensagem de contorno, marca, com a realidade misturada Headset, headset da realidade mista do Windows, headset da realidade virtual, HoloLens, MRTK, kit de ferramentas da realidade misturada
ms.openlocfilehash: 44f2678fe2f8e4be071086f46037749d1df61ae4
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848035"
---
# <a name="billboarding-and-tag-along"></a>Mural e tag-along

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>O que é o mural?

A mensagem é um conceito comportamental que pode ser aplicado a objetos em realidade misturada. Os objetos com o mural sempre se orientam para enfrentar o usuário. Os sistemas de texto e de menus são casos de uso comuns, em que os objetos estáticos colocados no ambiente do usuário (bloqueado pelo mundo) seriam obscuros ou ilegíveis quando os usuários perfrentem.

Os objetos com o mural habilitado podem girar livremente no ambiente do usuário. Eles também podem ser restritos a um único eixo, dependendo das considerações de design. Tenha em mente que os objetos convelados podem recortar ou se occluder quando colocados muito próximos de outros objetos, ou no HoloLens, fecham as superfícies digitalizadas. Para evitar isso, pense na superfície total que um objeto pode produzir quando girado no eixo habilitado para a mensagem.

<br>

---
## <a name="what-is-a-tag-along"></a>O que é uma marca?

A marcação é um conceito comportamental que pode ser adicionado a hologramas. Um objeto de marca ao longo das tentativas de permanecer em um intervalo que permite que o usuário interaja confortavelmente.

![O painel Pins do HoloLens é um ótimo exemplo de como a tag se comporta](images/tagalong-1000px.jpg)<br>
*O menu Iniciar do HoloLens é um ótimo exemplo de comportamento de marcação*

Os objetos de marca têm parâmetros, que podem ajustar a forma com que se comportam. O conteúdo pode estar dentro ou fora da linha de visão do usuário, enquanto o usuário se move em torno de seu ambiente. À medida que você se move, o conteúdo tenta permanecer dentro do periferia do usuário, deslizando para a borda da exibição. O conteúdo pode estar temporariamente fora de exibição, dependendo da rapidez com que o usuário está se movendo. Quando o usuário gazes em direção ao objeto de marca, ele é mais totalmente na exibição. Imagine que o conteúdo esteja sempre sendo "um relance" para que os usuários nunca se esqueçam em que direção seu conteúdo está.

Os parâmetros extras podem fazer com que a marca de objeto fique anexada à cabeça do usuário por uma faixa de borracha. A aceleração ou a desaceleração proporciona peso ao objeto, fazendo com que ele fique mais fisicamente presente. Esse comportamento de mola é uma forma que ajuda o usuário a criar um modelo mental preciso de como o Tag-by funciona. O áudio ajuda a fornecer outras indicações para quando os usuários têm objetos no modo de marca. O áudio deve reforçar a velocidade de movimento; uma rodada de cabeça rápida deve fornecer um efeito de som mais perceptível, ao passo que a movimentação em uma velocidade natural deve ter um mínimo ou sem efeitos de áudio.

Assim como o conteúdo realmente bloqueado, os objetos de marca podem se comprovar de forma exagerada ou nauseating se se moverem intensamente ou se acabarem muito na exibição do usuário. À medida que um usuário é examinado e, em seguida, pára rapidamente, seus sentidos dizem que eles foram interrompidos. Seu saldo informa que sua cabeça parou de ser ativada e sua visão vê o mundo parar de ligar. No entanto, se a marca ainda mantiver a movimentação quando o usuário for interrompido, ele poderá confundir seus sentidos.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Contorno e marcação em MRTK (Kit de ferramentas de realidade misturada) para o Unity
O **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts para o comportamento de etiqueta e de contorno. Atribua o script Billboard.cs a qualquer objeto para adicionar o comportamento de mensagem e fazer com que o objeto sempre fique à frente. Para adicionar o comportamento de marca, use o script RadialView.cs. Você pode ajustar várias opções, como lerping time, Distance e diploma.

* [MRTK-solucionador de exibição radial](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [MRTK-script do mural](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a>Consulte também

* [Cursores](cursors.md)
* [Raio de mão](point-and-commit.md)
* [Botão](button.md)
* [Objeto interativo](interactable-object.md)
* [Caixa delimitadora e barra de aplicativos](app-bar-and-bounding-box.md)
* [Manipulação](direct-manipulation.md)
* [Menu lateral](hand-menu.md)
* [Menu próximo](near-menu.md)
* [Coleção de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Dica de ferramenta](tooltip.md)
* [Slate](slate.md)
* [Controle deslizante](slider.md)
* [Sombreador](shader.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
* [Exibindo o progresso](progress.md)
* [Magnetismo de superfície](surface-magnetism.md)
