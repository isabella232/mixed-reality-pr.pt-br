---
title: Recomendações de material no Unreal
description: Visão geral dos materiais no mecanismo do Unreal.
author: hferrone
ms.author: safarooq
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, desenvolvimento, materiais, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: d5ce702495c95e8ca6d07a0209a4bc7d02f5d4d682415b028d63995e8910a7e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187676"
---
# <a name="material-recommendations-in-unreal"></a>Recomendações de material no Unreal

Os materiais usados podem afetar diretamente o quão bem seus projetos são executados no Unreal Engine. Esta página atua como um início rápido para as configurações básicas que você deve usar para obter o melhor desempenho de seus aplicativos de realidade misturada.

## <a name="using-customizeduvs"></a>Usando CustomedUVs

Se você precisar fornecer blocos UV em seu material, use CustomedUVs em vez de modificar o UV do nó de textura diretamente. Os CustomedUVs permitem manipular UVs nos sombreadores de vértice em vez do sombreador de Pixel.

![Configurações de material no Unreal](images/unreal-materials-img-01c.png)

Você pode encontrar detalhes de material na [documentação do Unreal Engine](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) e exemplos de melhores práticas nas capturas de tela abaixo:

[ ![ Configurações de material ](images/unreal-materials-img-01.png) recomendadas na configuração de ](images/unreal-materials-img-01.png#lightbox) 
 *material recomendado pelo* Unreal

[ ![ Configurações de material ](images/unreal-materials-img-01b.png) não recomendadas na ](images/unreal-materials-img-01b.png#lightbox) 
 *configuração de material não recomendado do* Unreal

## <a name="changing-blend-mode"></a>Alterando o modo blend

É recomendável definir o modo blend como opaco, a menos que haja um motivo forte para fazer o contrário. Materiais mascarados e translúcidos são lentos. Você pode encontrar mais detalhes sobre materiais na [documentação do Unreal Engine](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).

![Alterando o modo de combinação](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>Atualizando a iluminação para dispositivos móveis

A precisão total deve ser desligada. A iluminação de mapa de luz pode ser discada ao girar informações direcionais. Quando desabilitado, a iluminação de mapas de luz será simples, mas mais barata.

![Configurações de material móvel no Unreal](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>Ajustando o sombreamento de avanço

Essas opções melhoram a fidelidade visual às custas do desempenho. Eles devem ser desligados para o desempenho máximo.

![Encaminhar configurações de material de sombreamento no Unreal](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>Definindo a transluência do material

Indica que o material translúcido não deve ser afetado por bloom ou DOF. Como ambos os efeitos são raros no MR, essa configuração deve estar em por padrão.

![Configuração de translência separada móvel no Unreal](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>Configurações opcionais

As configurações a seguir podem melhorar o desempenho, mas observe que elas desabilitam determinados recursos. Use essas configurações somente se tiver certeza de que não precisa dos recursos em questão.

![Configurações de material opcionais no Unreal](images/unreal-materials-img-06.jpg)

Se o material não exigir reflexões ou brilho, definir essa opção poderá fornecer um enorme aumento de desempenho. No teste interno, ele é tão rápido quanto "desllitado" ao fornecer informações de iluminação.

## <a name="best-practices"></a>Práticas recomendadas

As "configurações" a seguir não são as melhores práticas relacionadas aos Materiais.

Ao criar parâmetros, prefira usar "Parâmetros Estáticos" sempre que possível. Comutadores Estáticos podem ser usados para remover um branch inteiro de um material sem custo de runtime. As instâncias podem ter valores diferentes, possibilitando a configuração de um sombreador com modelo sem perda de desempenho. A desvantagem é que várias permutações são criadas que causarão a recomputação do sombreador. Tente minimizar o número de parâmetros estáticos no material e o número de permutações desses parâmetros estáticos usados. Você pode encontrar mais detalhes sobre como renderizar parâmetros de material na [documentação do Unreal Engine](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).

![Práticas recomendadas para configurações de material](images/unreal-materials-img-07.jpg)

Ao criar Instâncias de Material, a preferência deve ser dada à Constante **da Instância de Material sobre** a Instância de Material Dinâmica. **A Constante da Instância** de Material é um Material de instância que calcula apenas uma vez antes do runtime.

A instância de material criada por meio do Navegador de Conteúdo ( clique com o botão **direito do mouse > Criar Instância de Material**) é uma Constante de Instância de Material. A Instância de Material Dinâmica é criada por meio de código. Você pode encontrar mais detalhes sobre instâncias de material na [documentação do Unreal Engine](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).

![Criando instâncias de material no Unreal](images/unreal-materials-img-08.png)

Fique atento à complexidade de seus materiais/sombreadores. Você pode exibir o custo do Material em várias plataformas clicando no ícone Estatísticas da Plataforma. Você também pode encontrar mais detalhes sobre materiais na [documentação do Unreal Engine.](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)

![Criando configurações dinâmicas da instância de material no Unreal](images/unreal-materials-img-09.png)

Você pode ter uma ideia rápida da complexidade relativa do sombreador por meio do modo de Exibição de Complexidade [do Sombreador](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).

* Tecla de atalho do modo de exibição: Alt + 8
* Comando do console: viewmode shadercomplexity

![Complexidade do material no Unreal](images/unreal-materials-img-10.png)

## <a name="see-also"></a>Consulte também
* [Materiais móveis](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [Modos de exibição](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [Instâncias de material](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
