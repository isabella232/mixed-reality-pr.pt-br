---
title: Estudo de caso - Como olhar através dos buracos na sua realidade
description: Este estudo de caso explica a implementação do efeito "janela mágica" HoloLens, permitindo que o usuário veja atrás de paredes, abaixo do chão e em aberturas virtuais.
author: ericrehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, janela mágica, paralax
ms.openlocfilehash: 0769d8a7bd2b5bdf1ef1fe50f1bbcd2f284b8503bf66b8fdb09b2206b716ea65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228162"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>Estudo de caso - Como olhar através dos buracos na sua realidade

Quando as pessoas pensam sobre a realidade misturada e o que podem fazer com Microsoft HoloLens, elas geralmente se aterão a perguntas como "Quais objetos posso adicionar ao meu quarto?" ou "O que posso camada sobre o meu espaço?" Gostaria de destacar outra área que você pode considerar, essencialmente um truque mágico, usando a mesma tecnologia para analisar ou por meio de objetos físicos reais ao seu redor.

## <a name="the-tech"></a>A tecnologia

Se você já tiver feito isso enquanto eles atravessam suas paredes **[](case-study-creating-an-immersive-experience-in-fragments.md)** no **[RoboRaid,](https://www.youtube.com/watch?v=Hf9qkURqtbM)** desbloqueou um cofre de parede em Fragmentos ou teve a sorte suficiente para ver o infinity UNSC na experiência halo 5 no E3 em **[2015,](https://www.youtube.com/watch?v=QDw5QjDtFy8)** você viu o que estou falando. Dependendo da sua criatividade, esse truque visual pode ser usado para colocar os orifícios temporários em sua drywall ou para ocultar mundos em um piso solto.

![O RoboRaid adiciona pipes tridimensionais e outra estrutura atrás de suas paredes, visíveis somente por meio de orifícios criados à medida que os invasores se atravessam.](../develop/unity/images/roboraid-640px.png)

O RoboRaid adiciona pipes tridimensionais e outra estrutura atrás de suas paredes, visíveis somente por meio de orifícios criados à medida que os invasores se atravessam.

Usando um desses hologramas exclusivos no HoloLens, um aplicativo pode fornecer a ilusão de conteúdo por trás de suas paredes ou por meio de seu piso da mesma maneira que a realidade se apresenta por meio de uma janela real. Mova-se para a esquerda e você poderá ver o que está no lado direito. Fique mais próximo e você poderá ver um pouco mais de tudo. A principal diferença é que os orifícios reais permitem que você passe, enquanto seu chão não permitirá que você passe por esse conteúdo holográfico mágico. (Adicionarei uma tarefa à pendência.)

## <a name="behind-the-scenes"></a>Nos bastidores

Esse truque é uma combinação de dois efeitos. Primeiro, o conteúdo holográfico é fixado ao mundo usando "âncoras espaciais". O uso de âncoras para tornar esse conteúdo "bloqueado pelo mundo" significa que o que você está vendo não se desmapeia visualmente dos objetos físicos perto dele, mesmo quando você se move ou o sistema de mapeamento espacial subjacente atualiza seu modelo 3D de sua sala.

Em segundo lugar, esse conteúdo holográfico é visualmente limitado a um espaço muito específico, portanto, você só pode ver por meio do orifício em sua realidade. Essa oclusão é necessária para exigir a análise de um orifício lógico, uma janela ou uma porta, que vende o truque. Sem algo bloqueando a maior parte da exibição, uma quebra no espaço para uma dimensão secreta Defássico pode se parecer apenas com um dinossauro mal posicionado.

![Essa não é uma captura de tela real, mas uma ilustração de como o segredo do MR Basics 101 se parece com HoloLens. O compartimento preto não aparece, mas você pode ver o conteúdo por meio de um espaço virtual. (Ao olhar por um dispositivo real, o chão pareceria desaparecer ainda mais porque seus olhos se concentram em uma distância maior, como se ele não estivesse lá.)](images/origamiholecomposited-640px.png)

Essa não é uma captura de tela real, mas uma ilustração de como o segredo do [MR Basics 101](../develop/unity/tutorials/holograms-101.md) se parece com HoloLens. O compartimento preto não aparece, mas você pode ver o conteúdo por meio de um espaço virtual. (Ao olhar por um dispositivo real, o chão pareceria desaparecer ainda mais porque seus olhos se concentram em uma distância maior, como se ele não estivesse lá.)

### <a name="world-locking-holographic-content"></a>Conteúdo holográfico de bloqueio mundial

No Unity, fazer com que o conteúdo holográfico permaneça bloqueado no mundo é tão fácil quanto adicionar um componente WorldAnchor:

```
myObject.AddComponent<WorldAnchor>();
```

O componente WorldAnchor ajustará constantemente a posição e a rotação de seu GameObject (e, portanto, qualquer outra coisa sob esse objeto na hierarquia) para mantê-lo estável em relação a objetos físicos próximos. Ao criar seu conteúdo, crie-o de forma que o pivô raiz do objeto seja centralizado nesse vazio virtual. (Se o pivô do objeto estiver profundo na parede, seus pequenos ajustes na posição e na rotação serão muito mais perceptíveis e o orifício poderá não parecer muito estável.)

### <a name="occluding-everything-but-the-virtual-hole"></a>Oclusão de tudo, menos o vazio virtual

Há várias maneiras de bloquear seletivamente a exibição para o que está oculto em suas paredes. A mais simples aproveita o fato de que o HoloLens usa uma exibição aditiva, o que significa que objetos totalmente pretos parecem invisíveis. Você pode fazer isso no Unity sem fazer nenhum sombreador especial ou truques de material– basta criar um material preto e atribuí-lo a um objeto que faz a caixa em seu conteúdo. Se você não quiser fazer a modelagem 3D, use apenas alguns objetos Quad padrão e sobreponha-os ligeiramente. Há várias desvantagens nessa abordagem, mas é a maneira mais rápida de fazer algo funcionar e obter uma prova de conceito de baixa fidelidade funcionando é excelente, mesmo se você suspeitar que talvez queira refactorá-lo mais tarde.

Uma grande desvantagem para a abordagem de "caixa preta" acima é que ela não é uma boa fotografia. Embora seu efeito possa parecer perfeito durante a exibição de HoloLens, todas as capturas de tela que você tirar mostrarão um objeto preto grande em vez do que resta de sua parede ou piso. O motivo para isso é que o hardware físico e as capturas de tela dos hologramas compostos e da realidade são diferentes. Vamos fazer um desvio por um momento em algumas matemáticas falsas...

*Alerta de matemática falso! Esses números e fórmulas devem ilustrar um ponto, não para ser qualquer tipo de métrica precisa!*

O que você vê por meio HoloLens:

```
( Reality * darkening_amount ) + Holograms
```

O que você vê em capturas de tela e vídeo:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

Em inglês: o que você vê por meio HoloLens é uma combinação simples de realidade escura (como por meio de óculos de sol) e quaisquer hologramas que o aplicativo deseja mostrar. Mas quando você faz uma captura de tela, a imagem da câmera é combinada com os hologramas do aplicativo de acordo com o valor de transparência por pixel.

Uma maneira de resolver isso é alterar o material de "caixa preta" para gravar apenas no buffer de profundidade e classificar com todos os outros materiais opacos. Para ver um exemplo disso, confira o [arquivo WindowOcclusion.shader no MixedRealityToolkit no GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader). As linhas relevantes são copiadas aqui:

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

(Observe que a linha "Deslocamento 50, 100" é para lidar com problemas não relacionados, portanto, provavelmente faria sentido deixar isso de fora.)

Implementar um material de oclusão invisível como esse permitirá que seu aplicativo desenhe uma caixa que parece correta na exibição e em capturas de tela de realidade misturada. Para pontos de bônus, você pode tentar melhorar ainda mais o desempenho dessa caixa fazendo coisas inteligentes para desenhar ainda menos pixels invisíveis, mas isso pode realmente chegar às weeds e geralmente não será necessário.

![Aqui está o segredo do MR Basics 101 à medida que o Unity o desenha, exceto para as partes externas da caixa de oclusão. Observe que o pivô para o chão está no centro da caixa, o que ajuda a manter o orifício o mais estável possível em relação ao seu piso real.](images/underworld-occluded-640px.png)

Aqui está o segredo do [MR Basics 101](../develop/unity/tutorials/holograms-101.md) à medida que o Unity o desenha, exceto para as partes externas da caixa de oclusão. Observe que o pivô para o chão está no centro da caixa, o que ajuda a manter o orifício o mais estável possível em relação ao seu piso real.

## <a name="do-it-yourself"></a>Faça você mesmo

Tem um HoloLens e deseja experimentar o efeito por você mesmo? A coisa mais fácil que você pode fazer (sem a necessidade de codificação) é instalar o aplicativo Visualizador 3D gratuito e, em seguida, carregar o [arquivo .fbx](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) fornecido no GitHub para exibir um modelo de flores em seu quarto. Carregue-o HoloLens e você poderá ver a ilusão no trabalho. Quando você estiver na frente do modelo, só poderá ver no pequeno espaço – todo o resto fica invisível. Veja o modelo de qualquer outro lado e ele desaparece completamente. Use os controles de movimentação, rotação e escala do Visualizador 3D para posicionar o orifício virtual em qualquer superfície vertical que você possa pensar para gerar algumas ideias!

![A exibição desse modelo no editor do Unity mostrará uma caixa preta grande em torno do depósito de flores. No HoloLens, a caixa desaparece, dando lugar a um efeito de janela mágica.](images/magicwindowflowerpotineditor.png)

A exibição desse modelo no editor do Unity mostrará uma caixa preta grande em torno do depósito de flores. No HoloLens, a caixa desaparece, dando lugar a um efeito de janela mágica.

Se você quiser criar um aplicativo que usa essa técnica, confira o tutorial do [MR Basics 101](../develop/unity/tutorials/holograms-101.md) nos [tutoriais de Realidade Misturada.](../develop/unity/tutorials.md) O capítulo 7 termina com uma explosão em seu chão que revela um segredo oculto (conforme figura acima). Who que os tutoriais tinham que ser entediantes?

Aqui estão algumas ideias sobre onde você pode usar essa ideia a seguir:
* Pense em maneiras de tornar o conteúdo dentro do espaço virtual interativo. Permitir que os usuários tenham algum impacto além de suas paredes pode realmente melhorar a sensação de surpresa que esse truque pode fornecer.
* Pense em maneiras de ver os objetos de volta para áreas conhecidas. Por exemplo, como você pode colocar um espaço holográfico em sua tabela de café e ver o chão abaixo dele?

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Reh ltda</b><br>Engenheiro de Software Sênior @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Confira também
* [Noções básicas do MR 101: projeto completo com dispositivo](../develop/unity/tutorials/holograms-101.md)
* [Sistemas de coordenadas](../design/coordinate-systems.md)
* [Âncoras espaciais](../design/spatial-anchors.md)
* [Mapeamento espacial](../design/spatial-mapping.md)
