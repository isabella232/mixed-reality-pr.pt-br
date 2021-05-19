---
title: Sistema elástico
description: documentação relacionada à simulação de elásticos no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, ElasticsSystem,
ms.openlocfilehash: 01a4c4a337593252e0955c03e883e35e1329fc45
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145182"
---
# <a name="elastic-system-experimental"></a>Sistema elástico (experimental)

![Sistema elástico](../images/elastics/Elastics_Main1.gif)

O MRTK vem com um sistema de simulação elástica que inclui uma ampla variedade de subclasses extensível e flexíveis, oferecendo associações para molas de quaternions bidimensionais, molas de volume tridimensionais e sistemas Spring lineares simples.

Atualmente, os seguintes componentes do MRTK que dão suporte ao [Gerenciador de elásticos](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) podem aproveitar a funcionalidade de elásticos:

- [Controle de limites](../ux-building-blocks/bounds-control.md)
- [Manipulador de objeto](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a>Gerenciador de elásticos

![System2 elástico](../images/elastics/Elastics_Main.gif)

Os processos do elásticos Manager passaram pelas transformações e as alimentam no sistema elástico.

A habilitação de elásticos para componentes personalizados pode ser obtida por duas etapas:

1. Chamar o método Initialize no início da manipulação, atualizar o sistema com a transformação do host atual.
1. Consultando ApplyHostTransform sempre que um cálculo de elásticos deve ser executado na transformação de destino atualizada.

Observe que os elásticos continuarão simulando após o término da manipulação (por meio do loop de atualização do elásticos Manager). Para bloquear o comportamento, a atualização automática de elásticos [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) pode ser definida como false.

Por padrão, o componente do elásticos Manager, quando adicionado a um objeto de jogo, não tem elásticos habilitados para qualquer tipo de transformações.
O campo `Manipulation types using elastic feedback` precisa ser habilitado para tipos de transformação específicos para criar a configuração de elásticos e extensões para o tipo selecionado.

### <a name="elastics-configurations"></a>Configurações de elásticos

Semelhante às [configurações de controle de limites](../ux-building-blocks/bounds-control.md#configuration-objects), o Gerenciador elástico vem com um conjunto de objetos de configuração que podem ser armazenados como objetos programáveis e compartilhados entre diferentes instâncias ou pré-fabricados. As configurações podem ser compartilhadas e vinculadas como arquivos de ativo programáveis por script ou ativos de script aninhados individuais dentro do pré-fabricados. Outras configurações também podem ser definidas diretamente na instância sem vincular a um ativo externo ou aninhado que pode ser script.

O inspetor do gerenciador de elásticos indicará se uma configuração é compartilhada ou emlinada como parte da instância atual mostrando uma mensagem no inspetor de propriedade. Além disso, as instâncias compartilhadas não serão editáveis diretamente na própria janela de propriedades do gerenciador de elásticos, mas, em vez disso, o ativo ao que está vinculando precisa ser diretamente modfiado para evitar alterações acidentais em configurações compartilhadas.

O Elastics Manager oferece opções de objetos de configuração para os seguintes tipos de transformação, cada um deles representado por [um objeto de configuração elástica](#elastic-configuration-object):

- Tradução elástica
- Rotação elástica
- Dimensionar Elástico

#### <a name="elastic-configuration-object"></a>Objeto de configuração elástica

Uma configuração elástica define as propriedades de um sistema diferencial de oscilador insuceso escuros.
As propriedades a seguir podem ser ajustadas, mas já vêm com um conjunto de padrões no MRTK:

- **Massa:** massa do elemento de oscilador simulado.
- **HandK:** constante de spring da mão.
- **EndK:** constante spring end cap.
- **SnapK:** constante spring do ponto de encaixe.
- **Arraste**: fator de arrastar/damper, proporcional à velocidade.

### <a name="elastics-extents"></a>Extensão elástica

As configurações de extensão elástica variam dependendo do tipo de manipulação. A tradução e a escala são representadas por extensão [elástica de volume](#volume-elastic-extent) e a rotação é representada por uma [extensão elástica de quatternion](#quaternion-elastic-extent).

#### <a name="volume-elastic-extent"></a>Extensão elástica do volume

As extensão de volume definem um espaço tridimensional no qual o oscilador harmônico sem gravidade está livre para se mover.

![Limites de ampliação do volume elástico](../images/elastics/Elastics_Volume_Bounds.gif)

- **StretchBounds**: representa os limites inferiores do espaço elástico.
- **UseBounds**: se os limites de ampliação devem ser respeitados pelo sistema. Se for true, quando a iteração atual da posição de destino estiver fora dos limites de ampliação, a força final será aplicada.
- **SnapPoints**: aponta para dentro do espaço no qual o sistema será ajustado.
- **RepeatSnapPoints**: repete os pontos de ajuste para infinito. Os pontos de ajuste existentes servirão como um módulo em que os pontos de ajuste reais são mapeados para os múltiplos inteiros mais próximos de cada ponto de ajuste.
- **SnapRadius**: distância em que os pontos de encaixe começam a forçar a mola.

![Grade de ajuste de volume elástico](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a>Extensão elástica do Quaternion

Extensões de Quaternion definem um espaço de rotação dimensional em que o Oscillator harmônica úmido é livre para girar.

![Exemplo de rotação elástica](../images/elastics/Elastics_Rotation.gif)

- **SnapPoints**: ângulos de Euler para os quais o sistema será ajustado.
- **RepeatSnapPoints**: repete os pontos de ajuste. Os pontos de ajuste existentes servirão como um módulo em que os pontos de ajuste reais são mapeados para os múltiplos inteiros mais próximos de cada ponto de ajuste.
- **SnapRadius**: arco-ângulo no qual os pontos de encaixe começam a forçar a mola em graus de Euler.

## <a name="elastics-example-scene"></a>Exemplo de cena de elásticos

Você pode encontrar exemplos de configurações de elásticos na `ElasticSystemExample` cena.

![Exemplo de cena de elásticos](../images/elastics/Elastics_Example_Scene.png)
