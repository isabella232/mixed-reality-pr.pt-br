---
title: Sistema elástico
description: Documentação relacionada à simulação de elástico no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, ElasticsSystem,
ms.openlocfilehash: 1f90864ee6d3b6756b863de600ade8423a44cacc
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121234"
---
# <a name="elastic-system-experimental"></a>Sistema elástico (experimental)

![Sistema elástico](../images/elastics/Elastics_Main1.gif)

O MRTK vem com um sistema de simulação elástica que inclui uma ampla variedade de subclasses extensíveis e flexíveis, oferecendo vinculações para o quaternão 4dimensional, o 3º volume e sistemas simples de fonte linear.

Atualmente, os seguintes componentes do MRTK que suportam [o gerenciador de elásticos](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) podem aproveitar a funcionalidade de elástico:

- [Controle de limites](../ux-building-blocks/bounds-control.md)
- [Manipulador de objetos](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a>Gerenciador de elásticos

![Sistema Elástico2](../images/elastics/Elastics_Main.gif)

Os processos do gerenciador de elásticos passados são transformadas e os alimenta no sistema elástico.

A habilitação de elásticos para componentes personalizados pode ser alcançada por duas etapas:

1. Chamando o método Initialize no início da manipulação, atualizando o sistema com a transformação de host atual.
1. Consultando ApplyHostTransform sempre que um cálculo elástico deve ser executado na transformação de destino atualizada.

Observe que os elásticos continuarão a simular depois que a manipulação terminar (por meio do loop de atualização do gerenciador elástico). Para bloquear o comportamento, a atualização automática de elástico [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) pode ser definida como false.

Por padrão, o componente do gerenciador de elásticos, quando adicionado a um objeto de jogo, não terá elásticos habilitados para nenhum tipo de transformação.
O campo precisa ser habilitado para tipos de transformação específicos para criar a configuração e as extensão de `Manipulation types using elastic feedback` elásticos para o tipo selecionado.

### <a name="elastics-configurations"></a>Configurações do Elastics

Semelhante às configurações de controle de limites, o gerenciador elástico vem com um conjunto de objetos de configuração que podem ser armazenados como objetos que podem ser scripts e [compartilhados](../ux-building-blocks/bounds-control.md#configuration-objects)entre diferentes instâncias ou pré-fabs. As configurações podem ser compartilhadas e vinculadas como arquivos de ativos individuais com script ou ativos aninhados que podem ser script dentro de pré-requisitos. Outras configurações também podem ser definidas diretamente na instância sem vincular a um ativo externo ou aninhado que pode ser script.

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

![Limites de alongamento de volume elástico](../images/elastics/Elastics_Volume_Bounds.gif)

- **StretchBounds**: representa os limites inferiores do espaço elástico.
- **UseBounds:** se os limites de stretch devem ser respeitados pelo sistema. Se true, quando a iteração atual da posição de destino estiver fora dos limites de stretch, a força final será aplicada.
- **SnapPoints:** pontos dentro do espaço ao qual o sistema será encaixado.
- **RepeatSnapPoints:** repete os pontos de snap para infinito. Os pontos de snap existentes servirão como um módulo em que os pontos de snap reais são mapeados para os múltiplos inteiros mais próximos de cada ponto de snap.
- **SnapRadius:** distância na qual os pontos de snap começam a forçar a fonte.

![Grade de Snap Grid de Volume Elástico](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a>Extensão elástica do Quatternion

As extensão quaternion definem um espaço de rotação quatrodimensional no qual o oscilador ínteco sem gravidade está livre para girar.

![Exemplo de rotação elástica](../images/elastics/Elastics_Rotation.gif)

- **SnapPoints:** ângulos de euler aos quais o sistema será encaixado.
- **RepeatSnapPoints:** repete os pontos de snap. Os pontos de snap existentes servirão como um módulo em que os pontos de snap reais são mapeados para os múltiplos inteiros mais próximos de cada ponto de snap.
- **SnapRadius:** arco angular no qual os pontos de ajuste começam a forçar a fonte em graus euler.

## <a name="elastics-example-scene"></a>Cena de exemplo do Elastics

Você pode encontrar exemplos de configurações de elásticos na `ElasticSystemExample` cena.

![Cena de exemplo do Elastics](../images/elastics/Elastics_Example_Scene.png)
