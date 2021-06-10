---
title: Criar conteúdo para exibição holográfica
description: Saiba mais sobre as diretrizes de design e as práticas recomendadas para a exibição do Holographic em dispositivos HoloLens.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Design de interface do usuário, exibição de Holographic, design de conteúdo, tema escuro, tema claro, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada, design, pixels
ms.openlocfilehash: 2c68acb5478bfbd438c8bbb9dd2f8d9686bcefc5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600315"
---
# <a name="designing-content-for-holographic-display"></a>Criar conteúdo para exibição holográfica

![Local do ulnar](images/UX_Hero_DarkTheme.jpg)

Ao criar conteúdo para exibições do Holographic, há vários elementos que você precisa considerar para obter a melhor experiência. Listamos algumas das nossas recomendações abaixo e você pode aprender mais sobre as características de exibições do Holographic na página [cor, luz e materiais](color-light-and-materials.md) .

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>Desafios com uma cor brilhante em uma grande superfície 

Com base em nossa pesquisa e teste de experiência de HoloLens, descobrimos que o uso de cores brilhantes em uma grande área da exibição pode causar vários problemas: 

**Fadiga de olho** 

Como a exibição de Holographic é aditiva, os hologramas com cores brilhantes usam mais luz. Uma cor sólida e brilhante em uma grande área da exibição pode facilmente causar fadigas de olho para o usuário. 

**Oclusão mão** 

A cor brilhante torna difícil para o usuário ver suas mãos ao interagir diretamente com objetos. Como o usuário não consegue ver suas mãos, fica difícil perceber a profundidade/distância entre a mão/dedo para a superfície de destino. O cursor Finger ajuda a compensar esse problema, mas ainda pode ser desafiador em uma superfície branca brilhante. 

![Cor e mão oclusão ](images/color_handocclusion.jpg)
 *dificuldade para ver a mão na placa traseira de conteúdo colorido brilhante*

**Uniformidade de cores**

Devido às características das exibições do Holographic, uma grande área brilhante na exibição pode se tornar blotchy. Usando esquemas de cores escuros, você pode minimizar esse problema. 

## <a name="design-guidelines-for-color-choices"></a>Diretrizes de design para opções de cores

**Usar cor escura para o plano de fundo da interface do usuário**

Usando o esquema de cores escuro, você pode minimizar os olhos fadiga e melhorar a confiança em interações diretas. 

![Exemplos de cores escuras usadas para os exemplos de conteúdo em segundo plano ](images/color_dark_examples.jpg)
 *da cor escura usada para o plano de fundo do conteúdo*

**Usar seminegrito ou espessura de fonte em negrito**

O HoloLens permite que sua experiência mostre um lindo texto de alta resolução. No entanto, é recomendável que você evite pesos de fontes finas, como luz ou semileve, porque os traços verticais podem se tremular em tamanho de fonte pequeno. 

![A espessura da fonte em negrito ou seminegrito (painel superior) melhora a ](images/color_font_examples.jpg)
 *espessura da fonte de negrito ou seminegrito (painel superior) melhora a legibilidade*

**Usar o material de HolographicBackplate do MRTK**

O material HolographicBackplate é aplicado a vários painéis de interface do usuário no Shell do HoloLens. Um de seus recursos é um efeito iridescence que é visível para os usuários à medida que eles alternam sua posição com base no painel. A cor da chapa traseira muda sutilmente em um espectro predefinido, criando um efeito visual envolvente e dinâmico sem interferir na legibilidade do conteúdo. Essa mudança sutil na cor também serve para compensar as irregularidades de cores secundárias. 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>Desafios com a placa traseira da interface do usuário Transparent ou translúcida 

![Exemplos de interface do usuário transparente exemplos ](images/color_transparent_examples.jpg)
 *de placa traseira da interface do usuário transparente*

**Complexidade e acessibilidade Visual**

Como o Holographic Objects Blend com o ambiente físico, o conteúdo ou a interface do usuário legível em janelas transparentes ou translúcidas pode ser degradado. Além disso, quando os objetos Holographic transparentes são sobrepostos uns dos outros, pode dificultar o usuário de interagir devido à profundidade confusa.

**Desempenho**

Para que objetos transparentes ou translúcidas sejam renderizados corretamente, eles devem ser classificados e mesclados com todos os objetos, que existem em segundo plano. A classificação de objetos transparentes tem um custo modesto de CPU, a mesclagem tem um custo de GPU considerável porque não permite que a GPU Faça a remoção da superfície oculta por meio de seleção de z (ou seja, teste de profundidade). Não permitir remoção de superfície oculta aumenta o número de operações necessárias para o pixel renderizado final. Isso coloca mais restrições de taxa de preenchimento de pressão.

**Problema de estabilidade de holograma com profundidade LSR tecnologia**

Para melhorar a Reprojeção do Holographic ou a estabilidade do holograma, um aplicativo pode enviar um buffer de profundidade ao sistema para cada quadro renderizado. Ao usar o buffer de profundidade para a Reprojeção, você precisa escrever um buffer de profundidade para cada cor renderizada em pixel como uma profundidade correspondente. Qualquer pixel com um valor de profundidade também deve ter um valor de cor. Se as diretrizes acima não forem seguidas, as áreas da imagem renderizada que não possuam informações de profundidade válidas poderão ser reprojetadas de uma forma que produza artefatos, que geralmente são visíveis como uma distorção do tipo Wave.


## <a name="design-guidelines-for-transparent-elements"></a>Diretrizes de design para elementos transparentes

**Usar plano de fundo opaco da interface do usuário**

Por padrão, os objetos Transparent ou translúcidas não gravam profundidade para permitir a mistura adequada. Maneiras de atenuar esse problema incluem, usando objetos opacos, garantindo que objetos translúcidas pareçam próximos a objetos opacos (como um botão translúcida na frente de uma chapa traseira opaca), forçando os objetos translúcidas a gravar profundidade (não aplicável em todos os cenários) ou renderizando objetos proxy, que só contribuem com valores de profundidade no final do quadro.

Soluções em MRTK-Unity:/Windows/Mixed-Reality/mrtk-Unity/performance/Hologram-Stabilization # Depth-buffer-Sharing-in-Unity  

Usando uma chapa invertida sólida e opaca, podemos proteger a segurança da legibilidade e da interação.

**Minimizar o número de pixels afetados**

Se o seu projeto deve usar objetos transparentes, tente minimizar o número de pixels afetados. Por exemplo, se um objeto só estiver visível em determinadas condições (como um efeito de brilho aditivo), desabilite o objeto quando ele estiver totalmente invisível (em vez de definir a cor aditiva como preto). Para formas 2D simples criadas usando um quad com uma máscara alfa, considere a criação de uma representação de malha da forma com um sombreador opaco em vez disso. 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>Exemplos escuros da interface do usuário em MRTK (Mixed Reality Toolkit) para o Unity

O **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece muitos exemplos de blocos de construção de interface do usuário com base nos esquemas de cores escuros.

* [Menu próximo](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
* [Diálogo](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)
* [Menu do lado](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="see-also"></a>Confira também

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