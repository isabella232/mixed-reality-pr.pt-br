---
title: Escala
description: Para exibir conteúdo com aparência realista no formulário holográfico é fundamental imitar, do modo mais próximo possível, as estatísticas visuais do mundo real.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Estilo, design, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, escala, hologramas
ms.openlocfilehash: 0b643b7f4b53795afa6bac9b54e55565233ac1d96a6a58d5389a8a4b7db8d7cc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222994"
---
# <a name="scale"></a>Escala

A chave para exibir conteúdo holográfico realista é imitar as estatísticas visuais do mundo real o mais próximo possível. Incorpore dicas visuais para ajudar os usuários do mundo real a entender onde estão os objetos, o tamanho deles e do que são feitos. A escala de um objeto é uma das responsabilidades visuais mais importantes, pois dá ao visualizador uma noção do tamanho dos objetos e sinais de sua localização. Além disso, a exibição de objetos em escala real é um dos principais diferenciais de experiência para a realidade misturada em geral– algo que não foi possível na exibição anterior baseada em tela.

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Como sugerir a escala de objetos e ambientes

Há muitas maneiras de sugerir a escala de um objeto, algumas das quais têm efeitos possíveis em outros fatores percepcionais. A chave é exibir objetos em um tamanho "real" e manter esse tamanho realista conforme os usuários se movem. Hologramas assumirá uma quantidade diferente do ângulo visual de um usuário à medida que eles se aproximarem ou se aproximarem, da mesma maneira que os objetos reais.

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a>Use a distância dos objetos conforme eles são apresentados ao usuário

Um método comum é usar a distância dos objetos conforme eles são apresentados ao usuário. Por exemplo, considere visualizar um carro de família grande na frente do usuário. Se o carro estivesse diretamente na frente dele dentro do tamanho do arm, ele seria muito grande para caber no campo de exibição do usuário. Objetos close exigem que o usuário mova a cabeça e o corpo para entender a totalidade do objeto. Se o carro for colocado mais distante (em toda a sala), o usuário poderá estabelecer uma noção de escala vendo todo o objeto em seu campo de exibição. Em seguida, os usuários podem se mover para mais perto do objeto para uma inspeção mais detalhada.

:::row:::
    :::column:::
        **[Ela usou essa técnica para](https://www.youtube.com/watch?v=DilzwF90vec)** criar uma experiência de showroom para um novo carro, usando a escala do carro holográfico de uma maneira realista e intuitiva para o usuário. A experiência começa com o holograma do carro em uma tabela física, permitindo que o usuário entenda o tamanho total e a forma do modelo. Posteriormente na experiência, o carro se expande para uma escala além do tamanho do campo de exibição do dispositivo. Como o usuário já adquiriu um quadro de referência do modelo menor, ele pode navegar adequadamente pelos recursos do carro.<br>
        <br>
        *Imagem: Experiência de Carros de HoloLens*
    :::column-end:::
        :::column:::
       ![Experiência do Cars Cars para HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>Usar hologramas para modificar o espaço real do usuário

Outro método é usar hologramas para modificar o espaço real do usuário, substituindo as paredes ou os limites existentes por ambientes ou 'orifícios' ou 'janelas'. Isso permite que objetos de tamanhos acima do tamanho aparentemente 'quebrem' o espaço físico. Por exemplo, uma árvore grande pode não caber nas salas de estar da maioria dos usuários, mas colocando um céu virtual em seu limite, o espaço físico se expande para o virtual. Isso permite que o usuário ande pela base da árvore virtual e reúna uma noção de escala e aparência do mundo real. Em seguida, os usuários podem procurar para vê-lo se estender muito além do espaço físico da sala.

:::row:::
    :::column:::
        **[Minecraft desenvolveu experiências de conceito usando](https://minecraft.net/)** uma técnica semelhante. Ao adicionar uma janela virtual a uma superfície física, os objetos existentes na sala são colocados no contexto de um ambiente muito maior, além das limitações de escala física da sala.<br>
        <br>
        *Imagem: Minecraft experiência de conceito para HoloLens*
    :::column-end:::
        :::column:::
       ![Minecraft experiência de conceito para HoloLens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>Experimentando com escala

Os designers experimentaram modificar a escala alterando o tamanho 'real' exibido do objeto. Ao mesmo tempo, eles mantêm uma única posição de objeto para aproximar um objeto que se move para o visualizador sem nenhum movimento real. Isso foi testado em alguns casos como uma maneira de simular a exibição de itens de perto, respeitando as possíveis limitações de conforto da exibição do conteúdo virtual mais próximo do que a "zona de conforto" sugeriria.

No entanto, isso pode criar alguns artefatos possíveis na experiência:
* Para objetos virtuais que representam algum objeto com um tamanho 'conhecido' para o visualizador, alterar a escala sem alterar a posição leva a responsabilidades visuais conflitantes. Os olhos ainda podem 'ver' o objeto em alguma profundidade devido a sinais de cadência. Para obter mais informações, consulte o [artigo Conforto.](comfort.md) O tamanho atua como uma indicação monocular de que o objeto pode estar se aproximando. Essas dicas conflitantes levam a percepções confusas – os visualizadores geralmente veem o objeto como permanecendo no lugar (devido à indicação de profundidade constante), mas crescendo rapidamente.
* Em alguns casos, a alteração da escala é vista como uma indicação de "nging", em que o objeto pode ou não ser visto para alterar a escala por um visualizador, mas parece estar se movendo diretamente em direção aos olhos do visualizador (o que pode ser um sentimento estranho).
* Com as superfícies de comparação no mundo real, essas alterações de dimensionamento às vezes são vistas como alteração de posição ao longo de vários eixos – os objetos parecem cair mais em vez de se aproximarem (semelhante em uma projeção 2D de movimento 3D em alguns casos).
* Por fim, para objetos sem um tamanho conhecido do 'mundo real' (por exemplo, formas arbitrárias com tamanhos arbitrários, elementos de interface do usuário e assim por diante), alterar a escala pode atuar funcionalmente como uma maneira de imitar alterações na distância. Os visualizadores não têm tantos sinais de top-down pré-existentes para entender o tamanho real ou o local do objeto, portanto, a escala pode ser processada como uma indicação mais importante.

<br>

---

## <a name="see-also"></a>Confira também
* [Cor, luz e materiais](./color-light-and-materials.md)
* [Tipografia](typography.md)
* [Projeto de som espacial](spatial-sound-design.md)