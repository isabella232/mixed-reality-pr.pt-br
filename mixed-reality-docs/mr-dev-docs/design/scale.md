---
title: Escala
description: Para exibir conteúdo com aparência realista no formulário holográfico é fundamental imitar, do modo mais próximo possível, as estatísticas visuais do mundo real.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, estilo, design, headset de realidade misturada, headset da realidade mista do Windows, headset da realidade virtual, HoloLens, escala, hologramas
ms.openlocfilehash: 12b1c96146f76274831c9bc3427cef93bb326f70
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583311"
---
# <a name="scale"></a>Escala

A chave para exibir o conteúdo de Holographic realista é imitando as estatísticas visuais do mundo real o mais próximo possível. Incorpore indicações visuais para ajudar os usuários do mundo real a entender onde estão os objetos, qual é o tamanho e o que são feitos. A escala de um objeto é uma das indicações visuais mais importantes porque dá ao visualizador uma ideia do tamanho dos objetos e das indicações para seu local. Além disso, a exibição de objetos em escala real é um dos principais diferenciais de experiência para a realidade misturada em geral – algo que não era possível na exibição anterior baseada em tela.

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Como sugerir a escala de objetos e ambientes

Há várias maneiras de sugerir a escala de um objeto, alguns dos quais têm possíveis efeitos em outros fatores de perceptiva. A chave a é exibir objetos com um tamanho ' real ' e manter esse tamanho realista à medida que os usuários se movem. Os hologramas ocuparão uma quantidade diferente do ângulo visual do usuário de um usuário à medida que eles ficarem mais próximos ou mais distantes, da mesma forma que os objetos reais.

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a>Use a distância dos objetos conforme eles são apresentados ao usuário

Um método comum é usar a distância dos objetos conforme eles são apresentados ao usuário. Por exemplo, considere a visualização de um carro de família grande na frente do usuário. Se o carro estivesse diretamente na frente deles no comprimento do ARM, seria muito grande para caber no campo de exibição do usuário. Fechar objetos exige que o usuário mova a cabeça e o corpo para entender todo o objeto. Se o carro for colocado mais distante (na sala), o usuário poderá estabelecer uma noção de escala ao ver o objeto inteiro em seu campo de exibição. Os usuários podem se mover mais para o objeto para uma inspeção mais detalhada.

:::row:::
    :::column:::
        **[Volvo usou essa técnica para criar uma](https://www.youtube.com/watch?v=DilzwF90vec)** experiência de showroom para um novo carro, usando a escala do carro de Holographic de uma forma que parecia realista e intuitiva ao usuário. A experiência começa com o holograma do carro em uma tabela física, permitindo que o usuário entenda o tamanho total e a forma do modelo. Mais tarde, na experiência, o carro se expande para uma escala além do tamanho do campo de exibição do dispositivo. Como o usuário já adquiriu um quadro de referência do modelo menor, ele pode navegar adequadamente pelos recursos do carro.<br>
        <br>
        *Imagem: experiência de carros Volvo para o HoloLens*
    :::column-end:::
        :::column:::
       ![Experiência de carros Volvo para o HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>Usar hologramas para modificar o espaço real do usuário

Outro método é usar hologramas para modificar o espaço real do usuário, substituindo as paredes ou os tetos existentes por ambientes ou acrescentando ' buracos ' ou ' Windows '. Isso permite que objetos de tamanho maior pareçam "sem interrupções" no espaço físico. Por exemplo, uma árvore grande pode não se ajustar à maioria das salas de vida dos usuários, mas ao colocar um céu virtual em seu teto, o espaço físico se expande para a máquina virtual. Isso permite que o usuário percorra a base da árvore virtual e reúna uma noção de escala e aparência do mundo real. Os usuários podem então consultar para ver se ele se estende muito além do espaço físico da sala.

:::row:::
    :::column:::
        **[Minecraft desenvolveu uma experiência de conceito](https://minecraft.net/)** usando uma técnica semelhante. Ao adicionar uma janela virtual a uma superfície física, os objetos existentes na sala são colocados no contexto de um ambiente amplamente maior, além das limitações de escala física da sala.<br>
        <br>
        *Imagem: experiência de conceito de Minecraft para o HoloLens*
    :::column-end:::
        :::column:::
       ![Experiência de conceito de Minecraft para o HoloLens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>Experimentando a escala

Os designers experimentaram a modificação da escala alterando o tamanho ' real ' exibido do objeto. Ao mesmo tempo, eles mantêm uma única posição de objeto para aproximar um objeto que se move em direção ao visualizador sem qualquer movimento real. Isso foi testado em alguns casos como uma maneira de simular a visualização de itens e, ao mesmo tempo, respeitar possíveis limitações de conforto de exibir conteúdo virtual mais próximo do que a "zona de conforto" sugere.

No entanto, isso pode criar alguns artefatos possíveis na experiência:
* Para objetos virtuais que representam algum objeto com um tamanho "conhecido" para o visualizador, alterar a escala sem alterar a posição leva a indicações visuais conflitantes. Os olhos ainda podem "ver" o objeto em alguma profundidade devido às indicações de Vergence. Para obter mais informações, consulte o artigo [conforto](comfort.md) . O tamanho atua como uma indicação monocular de que o objeto pode estar ficando mais próximo. Essas indicações conflitantes levam a percepções confusas – os visualizadores geralmente veem o objeto como estando em vigor (por causa da indicação de profundidade constante), mas crescendo rapidamente.
* Em alguns casos, a alteração de escala é vista como uma indicação ' surgindo ', em que o objeto pode ou não ser visto para alterar a escala por um visualizador, mas parece estar se movendo diretamente para os olhos do visualizador (o que pode ser um sensação desconfortável).
* Com superfícies de comparação no mundo real, tais alterações de dimensionamento às vezes são vistas como alteração da posição ao longo de vários eixos – os objetos parecem ficar mais baixos em vez de avançar (semelhante em uma projeção 2D do movimento 3D em alguns casos).
* Por fim, para objetos sem um tamanho "Real World" conhecido (por exemplo, formas arbitrárias com tamanhos arbitrários, elementos de interface do usuário e assim por diante), a escala mutável pode funcionar funcionalmente como uma forma de imitar as alterações em distância. Os visualizadores não têm tantas indicações de cima para baixo para entender o tamanho ou o local verdadeiro do objeto, de modo que a escala pode ser processada como uma indicação mais importante.

<br>

---

## <a name="see-also"></a>Confira também
* [Cor, luz e materiais](./color-light-and-materials.md)
* [Tipografia](typography.md)
* [Projeto de som espacial](spatial-sound-design.md)