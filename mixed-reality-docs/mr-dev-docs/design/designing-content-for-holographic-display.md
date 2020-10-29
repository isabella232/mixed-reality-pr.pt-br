---
title: Criando conteúdo para exibição do Holographic
description: Diretrizes de design e práticas recomendadas para a exibição do Holographic
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Design de interface do usuário, exibição de Holographic, design de conteúdo, tema escuro, tema claro
ms.openlocfilehash: 627ffdd0a413ad3140c29e9b1c7bb69c9dc249cf
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675597"
---
# <a name="designing-content-for-holographic-display"></a>Criando conteúdo para exibição do Holographic

![Local do ulnar](images/UX_Hero_DarkTheme.jpg)

Ao criar conteúdo para exibições do Holographic, há vários elementos que você precisa considerar para obter a melhor experiência. Listamos algumas das nossas recomendações abaixo e você pode aprender mais sobre as características de exibições do Holographic na página [cor, luz e materiais](color-light-and-materials.md) .

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>Desafios com uma cor brilhante em uma grande superfície 
Com base em nossa pesquisa e teste de usuários sobre vários tipos de experiências de HoloLens, descobrimos que o uso de cores brilhantes em uma grande área da exibição pode causar vários problemas: 

**Fadiga de olho** 

Como a exibição de Holographic é aditiva, a cor brilhante usa mais luz para exibir hologramas. Uma cor sólida e brilhante em uma grande área da exibição pode facilmente causar fadigas de olho para o usuário. 

**Oclusão mão** 

A cor brilhante torna difícil para o usuário ver suas mãos ao interagir diretamente com objetos. Como o usuário não pode ver suas mãos, fica difícil perceber a profundidade/distância entre a mão/dedo para a superfície de destino. O cursor Finger ajuda a compensar esse problema, mas ainda pode ser desafiador em uma superfície branca brilhante. 

![Cor e mão oclusão ](images/color_handocclusion.jpg)
 *dificuldade para ver a mão na placa traseira de conteúdo colorido brilhante*

**Uniformidade de cores**

Devido às características das exibições do Holographic, uma grande área brilhante na exibição pode se tornar blotchy. Usando esquemas de cores escuros, você pode minimizar esse problema. 

## <a name="design-guidelines"></a>Diretrizes de design

**Usar cor escura para o plano de fundo da interface do usuário**

Usando o esquema de cores escuro, você pode minimizar os olhos fadiga e melhorar a confiança em interações diretas. 

![Exemplos de interface do usuário escuro ](images/color_dark_examples.jpg)
 *exemplos de cor escura usada para o plano de fundo do conteúdo*

**Usar seminegrito ou espessura de fonte em negrito**

O HoloLens permite que sua experiência mostre um lindo texto de alta resolução. No entanto, é recomendável que você evite pesos de fontes finas, como luz ou semileve, porque os traços verticais podem se tremular em tamanho de fonte pequeno. 

![Exemplos de interface de usuário escuros ](images/color_font_examples.jpg)
 *, espessura de fonte em negrito ou seminegrito (painel superior) melhora a legibilidade*

**Usar o material de HolographicBackplate do MRTK**

O material HolographicBackplate é aplicado a vários painéis de interface do usuário no Shell do HoloLens. Um de seus recursos é um efeito iridescence que é visível para os usuários à medida que eles alteram sua posição em relação ao painel. A cor da chapa traseira muda sutilmente em um espectro predefinido, criando um efeito visual envolvente e dinâmico sem interferir na legibilidade do conteúdo. Essa mudança sutil na cor também serve para compensar as irregularidades de cores secundárias. 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>Desafios com a placa traseira da interface do usuário Transparent ou translúcida 
![Exemplos de interface do usuário transparente exemplos ](images/color_transparent_examples.jpg)
 *de placa traseira da interface do usuário transparente*

**Complexidade e acessibilidade Visual**

Como os objetos Holographic são mesclados com o ambiente físico, a legibilidade do conteúdo ou da interface do usuário na janela transparente ou translúcida pode ser degradada. Além disso, quando os objetos Holographic transparentes são sobrepostos uns dos outros, pode dificultar o usuário de interagir devido à profundidade confusa.

**Desempenho**

Para que objetos transparentes ou translúcidas sejam renderizados corretamente, eles devem ser classificados e mesclados com todos os objetos existentes em segundo plano. A classificação de objetos transparentes tem um custo modesto de CPU, a mesclagem tem um custo de GPU considerável, pois não permite que a GPU execute a remoção da superfície oculta por meio de uma remoção de z (ou seja, teste de profundidade). Não permitir remoção de superfície oculta aumenta o número de operações que precisam ser computadas para o pixel renderizado final e, portanto, coloca mais pressão nas restrições de taxa de preenchimento.

**Problema de estabilidade de holograma com profundidade LSR tecnologia**

Para melhorar a Reprojeção do Holographic ou a estabilidade do holograma, um aplicativo pode enviar um buffer de profundidade ao sistema para cada quadro renderizado. Ao usar o buffer de profundidade para a Reprojeção, uma regra é que, para cada pixel de cor renderizado, um valor de profundidade correspondente deve ser gravado no buffer de profundidade (e qualquer pixel com um valor de profundidade também deve ter um valor de cor). Se as diretrizes acima não forem seguidas, as áreas da imagem renderizada que não possuam informações de profundidade válidas poderão ser reprojetadas de uma maneira que produza artefatos (geralmente visíveis como uma distorção do tipo Wave).


## <a name="design-guidelines"></a>Diretrizes de design
**Usar plano de fundo opaco da interface do usuário**

Por padrão, os objetos Transparent ou translúcidas não gravam profundidade para permitir a mesclagem adequada. As maneiras de atenuar esse problema incluem, usando objetos opacos, garantindo que os objetos translúcidas pareçam próximos a objetos opacos (como um botão translúcida na frente de uma chapa traseira opaca), forçando os objetos translúcidas a gravar profundidade (não aplicável em todos os cenários) ou renderizando objetos proxy que só contribuem com valores de profundidade no final do quadro

Soluções dentro do MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity  

Usando uma chapa invertida sólida e opaca, podemos proteger a segurança da legibilidade e da interação.

**Minimizar o número de pixels afetados**

Se o seu projeto deve usar objetos transparentes, tente minimizar o número de pixels afetados. Por exemplo, se um objeto só estiver visível em determinadas condições (como um efeito de brilho aditivo), desabilite o objeto quando ele estiver totalmente invisível (em vez de definir a cor aditiva como preta). Para formas 2D simples criadas usando um quad com uma máscara alfa, considere a criação de uma representação de malha da forma com um sombreador opaco em vez disso. 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>Exemplos escuros da interface do usuário em MRTK (Mixed Reality Toolkit) para o Unity
O **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece muitos exemplos de blocos de construção de interface do usuário com base nos esquemas de cores escuros.

* [Menu próximo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [Diálogo](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [Menu do lado](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


<br>

---


## <a name="see-also"></a>Consulte também
* [Cor, luz e materiais](color-light-and-materials.md)
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
