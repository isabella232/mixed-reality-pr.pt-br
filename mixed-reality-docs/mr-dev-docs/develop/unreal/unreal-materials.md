---
title: Recomendações de material no Unreal
description: Visão geral dos materiais no mecanismo inreal.
author: hferrone
ms.author: safarooq
ms.date: 09/18/2020
ms.topic: article
keywords: Inreal, Engine 4, UE4, HoloLens, HoloLens 2, desenvolvimento, materiais, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: bfe70e730c5fbd6e5d103737b03e76bfd0ab65f6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580789"
---
# <a name="material-recommendations-in-unreal"></a>Recomendações de material no Unreal

Os materiais que você usa podem afetar diretamente o quão bem seus projetos são executados em um mecanismo inreal. Esta página atua como um início rápido para as configurações básicas que você deve usar para obter o melhor desempenho de seus aplicativos de realidade misturada.

## <a name="using-customizeduvs"></a>Usando CustomizedUVs

Se você precisar fornecer uma disposição UV em seu material, use CustomizedUVs em vez de modificar a UV do nó de textura diretamente. CustomizedUVs permitem que você manipule UVs nos sombreadores de vértice em vez do sombreador de pixel.

![Configurações de material em inreal](images/unreal-materials-img-01c.png)

Você pode encontrar detalhes materiais na [documentação do mecanismo inreal](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) e nos exemplos de práticas recomendadas nas capturas de tela abaixo:

[ ![ Configurações de material recomendadas em ](images/unreal-materials-img-01.png) configuração de ](images/unreal-materials-img-01.png#lightbox) 
 *material recomendado* inreal

[ ![ Configurações de material não recomendadas em ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox) 
 *configuração de material não recomendável não recomendada*

## <a name="changing-blend-mode"></a>Alterando o modo de mesclagem

É recomendável definir o modo de mesclagem como opaco, a menos que haja um motivo forte para fazer o contrário. Os materiais mascarados e translúcidas são lentos. Você pode encontrar mais detalhes sobre materiais na [documentação do mecanismo inreal](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).

![Alterando o modo de mesclagem](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>Atualizando a iluminação para dispositivos móveis

A precisão total deve ser desativada. A iluminação lightmap pode ser discada por meio da ativação de informações direcionais. Quando desabilitada, a iluminação de lightmaps será simples, mas mais barata.

![Configurações de material móvel em não real](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>Ajustando o sombreamento de encaminhamento

Essas opções melhoram a fidelidade visual ao custo do desempenho. Eles devem ser desativados para o desempenho máximo.

![Encaminhe as configurações de material de sombreamento em um espaço inreal](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>Configurando material Translucency

Indica que o material translúcida não deve ser afetado por flor ou DOF. Como ambos os efeitos são raros no Sr, essa configuração deve estar ativada por padrão.

![Configuração de Translucency separada para dispositivos móveis em não real](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>Configurações opcionais

As configurações a seguir podem melhorar o desempenho, mas observe que elas desabilitam determinados recursos. Use essas configurações somente se tiver certeza de que não precisa dos recursos em questão.

![Configurações de material opcionais em inreal](images/unreal-materials-img-06.jpg)

Se seu material não exigir reflexo ou brilho, a definição dessa opção pode fornecer um enorme aumento de desempenho. No teste interno, é tão rápido quanto "unlit" ao fornecer informações de iluminação.

## <a name="best-practices"></a>Práticas recomendadas

As seguintes não são "configurações", assim como as práticas recomendadas relacionadas aos materiais.

Ao criar parâmetros, prefira usar "parâmetros estáticos" sempre que possível. Opções estáticas podem ser usadas para remover uma ramificação inteira de um material sem custo de tempo de execução. As instâncias podem ter valores diferentes, tornando possível ter um sombreado modelo configurado sem perda de desempenho. A desvantagem é que várias permutações são criadas e causarão a recompilação do sombreador. Tente minimizar o número de parâmetros estáticos no material e o número de permutações desses parâmetros estáticos que são usados. Você pode encontrar mais detalhes sobre como renderizar os parâmetros de material na [documentação do mecanismo inreal](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).

![Práticas recomendadas para configurações de material](images/unreal-materials-img-07.jpg)

Ao criar instâncias de material, a preferência deve ser dada à **constante da instância material** sobre a instância de material dinâmica. **Constante de instância de material** é um material de instância que calcula apenas uma vez antes do tempo de execução.

A instância de material criada por meio do navegador de conteúdo (**clique com o botão direito do mouse > criar instância de material**) é uma constante de instância de material. A instância de material dinâmica é criada por meio de código. Você pode encontrar mais detalhes sobre as instâncias de material na [documentação do mecanismo inreal](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).

![Criando instâncias de material em um não real](images/unreal-materials-img-08.png)

Fique atento à complexidade dos seus materiais/sombreadores. Você pode exibir o custo de seu material em várias plataformas clicando no ícone de estatísticas de plataforma. Você também pode encontrar mais detalhes sobre materiais na [documentação do mecanismo inreal](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).

![Criando configurações dinâmicas da instância de material em um inreal](images/unreal-materials-img-09.png)

Você pode obter uma ideia rápida da complexidade relativa do seu sombreador por meio do [modo de exibição](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)de complexidade do sombreador.

* Tecla de atalho do modo de exibição: Alt + 8
* Comando de console: ViewMode shadercomplexity

![Complexidade de material em não real](images/unreal-materials-img-10.png)

## <a name="see-also"></a>Confira também
* [Materiais móveis](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [Modos de exibição](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [Instâncias de material](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
