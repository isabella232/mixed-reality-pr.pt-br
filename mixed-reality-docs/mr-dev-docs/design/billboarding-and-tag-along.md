---
title: Mural e tag-along
description: Saiba como usar objetos com mistas, que sempre se orientam para enfrentar o usuário em aplicativos de realidade misturada.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, marcação, marcação, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada
ms.openlocfilehash: 0bd1ac2168284d714240c6775468a61ed3e665b8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600335"
---
# <a name="billboarding-and-tag-along"></a>Mural e tag-along

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>O que é a reação de dados?

A mista é um conceito comportamental que pode ser aplicado a objetos na realidade misturada. Objetos com o uso de objetos sempre se orientam para enfrentar o usuário. Sistemas de texto e menu são casos de uso comuns, em que objetos estáticos colocados no ambiente do usuário (bloqueados pelo mundo) seriam obscurecidos ou ilegíveis quando os usuários se movimentam.

Objetos com a reação de dados habilitada podem girar livremente no ambiente do usuário. Eles também podem ser restritos a um único eixo, dependendo das considerações de design. Lembre-se de que objetos com recodados podem ser repassados ou ocluir a si mesmos quando colocados muito próximos de outros objetos ou, no HoloLens, superfícies examinadas muito próximas. Para evitar isso, pense no volume total que um objeto pode produzir quando girado no eixo habilitado para a rotação.

<br>

---
## <a name="what-is-a-tag-along"></a>O que é um tag-along?

O tag-along é um conceito comportamental que pode ser adicionado aos hologramas. Um objeto de marcação ao longo tenta permanecer em um intervalo que permite que o usuário interaja de maneira confortável.

![O painel de pinos do HoloLens é um ótimo exemplo de como o tag-along se comporta](images/tagalong-1000px.jpg)<br>
*O menu Iniciar HoloLens é um ótimo exemplo de comportamento de tag-along*

Os objetos de marcação têm parâmetros, que podem ajustar a maneira como se comportam. O conteúdo pode estar dentro ou fora da linha de visão do usuário enquanto o usuário se move em torno de seu ambiente. Conforme você se move, o conteúdo tenta permanecer dentro da periférico do usuário deslizando para a borda da exibição. O conteúdo pode estar temporariamente fora de exibição, dependendo da rapidez com que o usuário está se movendo. Quando o usuário se volta para o objeto tag-along, ele fica mais totalmente em exibição. Pense no conteúdo sempre sendo "um relance" para que os usuários nunca se esqueça em qual direção seu conteúdo está.

Parâmetros extras podem fazer com que o objeto de marcação ao longo se sinta anexado à cabeça do usuário por uma faixa de borracha. A aceleração ou a desaceleração mais intensas dão peso ao objeto, fazendo com que ele se sinta fisicamente mais presente. Esse comportamento spring é uma capacidade que ajuda o usuário a criar um modelo mental preciso de como o tag-along funciona. O áudio ajuda a fornecer outras dicas para quando os usuários têm objetos no modo de tag-along. O áudio deve reforçar a velocidade de movimentação; um turno de cabeça rápido deve fornecer um efeito de som mais perceptível, enquanto o trabalho em uma velocidade natural deve ter efeitos de áudio mínimos ou não.

Assim como o conteúdo realmente com a cabeça bloqueada, os objetos de marcação podem se mostrar avassaladores ou desalocar se eles se movem muito ou soltam muito na exibição do usuário. À medida que um usuário procura e, em seguida, para rapidamente, seus sentidoes dizem que ele parou. Seu equilíbrio informa que sua cabeça parou de girar e sua visão vê o mundo parar de girar. No entanto, se o tag-along continuar se movendo quando o usuário tiver parado, isso poderá confundir seus sentidos.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Mistas e marcações no MRTK (Kit de Ferramentas de Realidade Misturada) para Unity
**[O MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts para o comportamento de Marcação e Marcação. Atribua o script Dem.cs a qualquer objeto para adicionar o comportamento de minguação e fazer com que o objeto sempre o despente. Para adicionar o comportamento de tag-along, use o script RadialView.cs. Você pode ajustar várias opções, como tempo de leitura, distância e grau.

* [MRTK – Solucionador de Exibição Radial](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [MRTK – Script de Script de Script do MrTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a>Confira também

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